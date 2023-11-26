# Hacking-Active-Directory
Hacking Active Directory  notes based on https://www.youtube.com/watch?v=VXxH4n684HE&amp;t=11955s video


## IPV6 DNS ATTACK + ldap relay using ntlmrelayx and mitm6 :

https://medium.com/@n3tworkn1nja/ipv6-dns-take-over-attack-fd8db1cd25f3

## ntlm relay

https://www.digitalwhisper.co.il/files/Zines/0x6D/DW109-1-reNTLMRelay.pdf

## smb relay :

https://tcm-sec.com/smb-relay-attacks-and-how-to-prevent-them/

## LLMNR POISENING :

https://systemweakness.com/what-is-llmnr-poisoning-attack-and-how-to-secure-against-it-417f3b415e51


## LM, NTLM, Net-NTLMv2 hashes explained:

https://medium.com/@petergombos/lm-ntlm-net-ntlmv2-oh-my-a9b235c58ed4


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



pass the hash explanation: https://en.wikipedia.org/wiki/Pass_the_hash





