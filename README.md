#### Scripts-and-guides-to-register-RHEL-systems-via-subscription-manager
Go to settings of Redhat system
Registration server- Redhat
Registration type-Redhat Account
Registration Details-
Fill the username,password,organization.(This is for the system which is SCA enabled by the organization)
For no cost use Red Hat Developer No-Cost Subscription which is free for individual developers.

#### Fixing "This system is not registered with an entitlement server. You can use subscription-manager to register." issue
$ yum install git
This system is not registered with an entitlement server. You can use subscription-manager to register.
Error: There are no enabled repos.
#### Follow this steps to register on Redhat server and to use no cost subscription
## Red Hat Developer No-Cost Subscription Setup
- [Sign Up for a Free Red Hat Developer Account](https://sso.redhat.com/auth/realms/redhat-external/protocol/openid-connect/registrations?client_id=rhd-web&redirect_uri=https%3A%2F%2Fdevelopers.redhat.com&state=33005da4-0288-48f1-afe7-1c45a4a8e772&response_mode=fragment&response_type=code&scope=openid%20api.dxp_portals.developers&nonce=06cb6193-59f1-4f42-8c45-edcedee2d4bb&code_challenge=qD5uxGFZnYhvTEwiwGXIaAih4Tcpmwk6neOpw57kerM&code_challenge_method=S256)
- Create an account using your email and password
## 1 Register Your System
Use subscription-manager to register your system:
subscription-manager register
## 2 Attach a subscription
subscription-manager attach --auto
or (to atatch manually)
subscription-manager list --available (copy the pool id)
subscription-manager attach --pool=<POOL_ID> (paste here)
## 3 Verify subscription
subscription-manager list --consumed
## 4 Test Installation
Try installing a package to verify access.
yum install git
## If fails to access
Run below commands to enable essential repos
subscription-manager repos --enable=rhel-8-baseos-rpms
subscription-manager repos --enable=rhel-8-appstream-rpms
,
[Download RHEL ISO from developer redhat portal](https://developers.redhat.com/)
Ataach to cloud or virtual machines and run the above mentioned commands(1-4) again.


##### Fixing 'No Enabled Repositories' in /etc/yum/repos.d and /etc/distro/repos.d in SCA enabled on system.

SCA Is Provided by the Organization (Red Hat Customer Account)
When you’re working in a corporate or enterprise environment, Simple Content Access (SCA) is typically enabled or managed by your organization’s Red Hat account administrator.
How to Check If Your Organization Has SCA Enabled-
Ask Red hat account administrator or IT team.
or
[login to](https://access.redhat.com/)
- Go to Subscriptions > Simple Content Access
- Check if it’s Enabled for your organization
##  Enable Repositories
If you're using RHSM (Red Hat Subscription Manager):
subscription-manager repos --enable=rhel-8-baseos-rpms
subscription-manager repos --enable=rhel-8-appstream-rpms
## Test installation
yum install git
## If still getting error,unregister your system and again register.
subscription-manager unregister
subscription-manager remove --all
subscription-manager clean
subscription-manager register
subscription-manager status
subscription-manager attach --auto









