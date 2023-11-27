# Hacking-Active-Directory
Hacking Active Directory  notes based on https://www.youtube.com/watch?v=VXxH4n684HE&amp;t=11955s video


## IPV6 DNS ATTACK + ldap relay using ntlmrelayx and mitm6 :

- https://medium.com/@n3tworkn1nja/ipv6-dns-take-over-attack-fd8db1cd25f3

## ntlm relay
- https://infosecwriteups.com/abusing-ntlm-relay-and-pass-the-hash-for-admin-d24d0f12bea0
- https://www.digitalwhisper.co.il/files/Zines/0x6D/DW109-1-reNTLMRelay.pdf
## smb relay :

- https://tcm-sec.com/smb-relay-attacks-and-how-to-prevent-them/

## LLMNR POISENING :

- https://systemweakness.com/what-is-llmnr-poisoning-attack-and-how-to-secure-against-it-417f3b415e51


## LM, NTLM, Net-NTLMv2 hashes explained:
- https://medium.com/@petergombos/lm-ntlm-net-ntlmv2-oh-my-a9b235c58ed4
- https://systemweakness.com/difference-between-nt-lm-ntlm-net-ntlmv1-v2-ntlmv1-v2-hashes-c6df0afde008

## Post Compromise Enumeration tools : powerview , bloodhound :


## Post Compromise Attacks AD (pass the hass , Pass the Password ):

- tools and examples :

1. secretsdump.py marval/fcastle:Ari123a123@192.168.59.130
 ![image](https://github.com/ArielElb/Hacking-Active-Directory/assets/94087682/1bc081fe-0c05-4e48-8697-381e2e784916)

2. dumping the hashes in the SAM file when we got a user
crackmapexec smb 192.168.59.0/24 -u fcastle -d marval.local -p Ari123a123 --sam

- good resource : https://www.hackingarticles.in/credential-dumping-sam/

![image](https://github.com/ArielElb/Hacking-Active-Directory/assets/94087682/d82819ee-059e-4f47-8a42-ef9df98192f2)

3. trying to pass the ntlm hash:
![image](https://github.com/ArielElb/Hacking-Active-Directory/assets/94087682/04c932f7-3749-4896-99ee-134effbf2b83)

4. amazinng resource : - https://www.giac.org/paper/gcih/34273/pass-the-hash-windows-10/174913
pass the hash explanation:: -https://en.wikipedia.org/wiki/Pass_the_hash

## Domain Escalation with Token Impersonation:

- https://medium.com/r3d-buck3t/domain-escalation-with-token-impersonation-bc577db55a0f

## kerberoasting attack:

- https://medium.com/@Shorty420/kerberoasting-9108477279cc

" Kerberoast: 
The goal of Kerberoasting is to harvest TGS tickets for services that run on behalf of user accounts in the AD, not computer accounts. Thus, part of these TGS tickets are encrypted with keys derived from user passwords. As a consequence, their credentials could be cracked offline.
You can know that a user account is being used as a service because the property "ServicePrincipalName" is not null.
Therefore, to perform Kerberoasting, only a domain account that can request for TGSs is necessary, which is anyone since no special privileges are required.
You need valid credentials inside the domain. "
- (https://book.hacktricks.xyz/windows-hardening/active-directory-methodology/kerberoast)

 1. get the TGS hash that encrypted with the service owner hash :
  ![image](https://github.com/ArielElb/Hacking-Active-Directory/assets/94087682/98bbb258-cc32-4674-9ded-514a7f723642)
 2. use hashcat with a list of common passwords or a list generated by mentalist tool after enumerating the network:
    ![image](https://github.com/ArielElb/Hacking-Active-Directory/assets/94087682/43e346c5-f627-4728-8ba9-6e5e1ce2cde6)
    ![image](https://github.com/ArielElb/Hacking-Active-Directory/assets/94087682/b157daa9-2d4f-4c27-89d4-6d0ec7d8226b)

 * we got the SQL service domain password that was misconfigoured and is a domain admin *

