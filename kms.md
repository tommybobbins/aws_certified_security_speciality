# KMS

- Create and Manage symmetrics and asymmetrics encryption keys
- KMS keys are protected by AWS HSM (not always customer HSM).
- Customer Managed Keys
- AWS Managed Keys (e.g. aws/ebs). Cannot manage, rotate or change them.
- Developer created keys are CMK.
- KMS by default creates the key material for a KMS key, can import yourself if required.
- KMS key can encrypt data up to 4KB.
- KMS key can generate, encrypt and decrypt Data Encryption keys (DEKs) if you need to encrypt large amounts of data.

# Alternative Key Stores

## External Key Store 

- Keys can be stored outside of AWS to meet regulatory requirements.
- You can create a KMS key in an external Key Store (XKS).
- All keys are generated and stored in an external key manager.
- When using an XKS, key material never leaves your HSM.

## Custom Key Store

- You can create KMS keys in an AWS CloudHSM custom key store.
- All keys are generated and stored in a CloudHSM cluster that you own and manage.
- Crypto operations are performed only in the CloudHSM cluster. 
- Custom key stores are not available for asymmetric KMS keys.

## Data Encrpytion Keys

 - Large amounts of data.
 - KMS keys generate, encrypt and decrypt data keys.
 - KMS does not store, manage or track your data keys or perform crypto with data keys.
 - Use and Manage Data keys outside of KMS.


 ## KMS Key rotation

 |Type of KMS Key|Customer Managed|AWS Managed|AWS Owned|
 |---|---|---|---|
 |Can View|Yes|Yes|No|
 |Can Manage|Yes|No|No|
 |Used only for my account|Yes|Yes|No|
 |Automatic rotation|Optional. Every 365 Days|Required. Every 365 days|Varies|

 - Cannot Enable or Disable Key rotation for AWS owned keys
 - Automatic key rotation is supported only on symmetric encryption KMS keys with Key material that AWS KMS generates (Origin = AWS_KMS).
 - Rotation changes the key material not the Key ID, ARN, region, policies or permissions.
 - After you enable key rotation, KMS rotates the KMS key automatically every year.
 - Automatic rotation is not supported for Asymmetric KMS keys, HMAC KMS keys, KMS keys in custom key stores.  
 - Can do manual key rotation, which changes the key_id. You can use an Alias to refer to the key.

 ## KMS Key Policies

- Need to allow the correct KMS actions to allow a user to use a key
- Multiple policy statements can be combined to specify user and admin permissions.
- Grants are useful for temporary permissions as they can be used without modifying key policies or IAM policies. 

## KMS Key Material Origin

Identifies the source of the key material in the KMS Key and cannot be changed after creation.

- *KMS (AWS_KMS)* - default. AWS KMS creates and manages the key material in its own key store.
- *External (EXTERNAL)*. You import the key material into the KMS key and you are responsible for securing and managing the key material outside of AWS.
- *Custom Keystore (AWS_CLOUDHSM)* - create the key material within CloudHSM.

## Exam Tips

- To share snapshots with another account, you must specify ````Decrypt```` and ````CreateGrant```` permissions.
- The kms:ViaService condition key can be used to limit key usage to specific AWS services (EC2, RDS).
- Cryptographic erasure means removing the ability to decrypt data and can be achieved when using imported key material and deleting it. 
- You must use DeleteImportedKeyMaterial API to remove the key material.
- InvalidKeyId exception when using SSM Parameter Store means the KMS key is not enabled.


## KMS Multi-Region

- Same Key material and same key ID in both regions.
- Encrypt in one region and decrypt in other regions.
- Multi-Region keys have the same key id, key material, automatic rotation etc.
- KMS Multi-Region are not global (Primary + Replicas).

Use Cases: Global client-side encryption, encryption on Global DynamoDB, Global Aurora.

## KMS and Envelope encryption

KMS Encrypt API has a limit of 4KB. If you want to encrypt more than 4KB, then use envelope encryption.
API Used will be GenerateDataKey API == Envelope encryption.

Data Key Caching - reuse data keys instead of creating one each time.

## KMS Symmetric

- *Encrypt* - encrypt up to 4KB of data through KMS.
- *GenerateDataKey* - generates a unique symmetric data key. Returns a plaintext copy of the data key and a copy that is encrypted under the CMK that you specify.
- *GenerateDataKeyWithoutPlaintext* - Generate a DEK to use at some point (not immediately). DEK that is encrypted under the CMK that specify. Must decrypt it before you can use it.
- *Decrypt* - decrypt up to 4KB of data.
- *GenerateRandom* - returns a random byte string.

## KMS Key Deletion - CloudWatch Alarm

- Use CloudTrail, CloudWatch Logs, CloudWatch Alarms and SNS to be notified when someone tries to use a CMK that's pending deletion in a cryptographic operation (Encrypt, Decrypt).
- To be notified of keys being deleted or disabled, use cloudtrail and eventbridge.

````
User-> *DisableKey* or *ScheduleKeyDeletion* API calls -> AWS KMS -> event -> Eventbridge -> trigger -> SNS -> SendEmail -> Admin
                                                                                          -> initiate --------->SSM
                                                            <------- AWSConfigRemediation-CancelKeyOperation<--<SSM
````


## KMS Grants 

- Allow you to grant access to specific AWS KMS keys to other AWS accounts and IAM Users/Roles within your AWS Account.
- Often used for temporary permissions.
- Can be used for all operations including encrypt, decrypt, sign and verify as well as creating more grants.
- Grants are for one KMS key only and one or more IAM Principals.
- Once granted, a principal can perform any operation as specified in the Grant.
- Grants do not expire automatically, you must delete them manually.
- You don't need to change KMS Key Policy or IAM Policy.

## Condition Keys

- *kms:ViaService* - limits the use of a KMS key to requests from specified AWS Services.
- Condition->StringEquals->kms:ViaService->rds.us-west-2.amazonaws.com
- Can be used with aws/ebs aws/rds - you will find this in the policies.
- *kms:CallerAccount* - kms:CallerAccount
- Condition->StringEquals->kms:CallerAccount->"0123456789"
