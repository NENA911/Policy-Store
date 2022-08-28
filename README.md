# Policy-Store
NENA-STA-010: The Policy Store web service stores and retrieves policies (rulesets) for i3-based systems. The Policy Store accepts a policy document from a policy owner (an agency) or an agency authorized to store policies on behalf of the owner. Policies are identified by the policy type, the identity of the agency whose owns the policy and for Policy Routing Rules, a policyQueueName or an Id. Policy Types come from the Policy Type Registry 10.33 and consist of service names (which are policies that describe the access rights for the service), and policyTypes specified by this document or other NENA standards. The Policy Store provides the policy on request to a policy retriever. The Policy Store does not alter the policy document in any way; it stores it as an octet stream, without performing line-ending conversion, JSON or XML normalization, reformatting, or any other alteration. This allows the policy signature to be verified more efficiently, by avoiding the need to re-canonicalize the JSON.

A policy is represented by a JWS which contains a Policy Object. The Policy Object consists of:

|      Name                         |      Condition                                                                                                          |      Description                                                                                             |
|-----------------------------------|-------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
|     policyOwner                   |     MANDATORY                                                                                                           |     ID of the   agency or service whose policy is requested. MUST be a FQDN or URI that   contains a FQDN    |
|     policyType                    |     MANDATORY                                                                                                           |     Type of the   policy. Restricted to the values in the Policy Types registry                              |
|     policyId                      |     CONDITIONAL, MUST NOT be specified unless policyType is “OtherRoutePolicy”                                          |     For   “OtherRoutePolicy”, this is an arbitrary identifier for the policy                                 |
|     policyQueueName               |     CONDITIONAL, MUST NOT be specified unless policyType is “OriginationRoutePolicy”   or “NormalNextHopRoutePolicy”    |     For   “OriginationRoutePolicy” or “NormalNextHopRoutePolicy”, this is the policyQueueName                |
|     policyExpirationTime          |     OPTIONAL                                                                                                            |     Policy is not   valid after this time                                                                    |
|     policyRules                   |     MANDATORY                                                                                                           |     Array of Rules                                                                                           |
|     policyLastModificationTime    |     CONDITIONAL, MUST be provided on retrieval, ignored on store                                                        |     Date/Time   policy was last modified                                                                     |
|     description                   |     OPTIONAL                                                                                                            |     Text   description of policy                                                                             |

## Owner

The owner of this repository approves all changes to the repository. 

This repository is owned by the NENA Core Services Committee, i3 Architecture working group.

#### Rules:

Specification Required. 

#### Contact:

[https://www.nena.org/page/911CoreSvcs](https://www.nena.org/page/911CoreSvcs) 

## Version History

### Policy Store v 1.0

An OpenAPI schema for the Policy Store was originally defined in NENA-STA-010.3.2021. See https://www.nena.org/page/i3_Stage
