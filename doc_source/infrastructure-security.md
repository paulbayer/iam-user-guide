# Infrastructure security in AWS Identity and Access Management<a name="infrastructure-security"></a>

As a managed service, AWS Identity and Access Management is protected by the AWS global network security\. For information about AWS security services and how AWS protects infrastructure, see [AWS Cloud Security](http://aws.amazon.com/security/)\. To design your AWS environment using the best practices for infrastructure security, see [Infrastructure Protection](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/infrastructure-protection.html) in *Security Pillar AWS Well‐Architected Framework*\.

You use AWS published API calls to access IAM through the network\. Clients must support the following:
+ Transport Layer Security \(TLS\) 1\.0 or later\. We recommend TLS 1\.2 or later\.
+ Cipher suites with perfect forward secrecy \(PFS\) such as DHE \(Ephemeral Diffie\-Hellman\) or ECDHE \(Elliptic Curve Ephemeral Diffie\-Hellman\)\. Most modern systems such as Java 7 and later support these modes\.

Additionally, requests must be signed by using an access key ID and a secret access key that is associated with an IAM principal\. Or you can use the [AWS Security Token Service](https://docs.aws.amazon.com/STS/latest/APIReference/Welcome.html) \(AWS STS\) to generate temporary security credentials to sign requests\.

IAM can be accessed programmatically by using the IAM HTTPS API, which lets you issue HTTPS requests directly to the service\. The Query API returns sensitive information, including security credentials\. Therefore, you must use HTTPS with all API requests\. When you use the HTTPS API, you must include code to digitally sign requests using your credentials\.

You can call these API operations from any network location, but IAM does support resource\-based access policies, which can include restrictions based on the source IP address\. You can also use IAM policies to control access from specific Amazon Virtual Private Cloud \(Amazon VPC\) endpoints or specific VPCs\. Effectively, this isolates network access to a given IAM resource from only the specific VPC within the AWS network\.