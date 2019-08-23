---
title: <message> z <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 75101744-eed8-4d61-91f4-5fc4473a21f2
ms.openlocfilehash: 796c6bf5df541e525624a609fcfba255eda673cd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931478"
---
# <a name="message-of-wsdualhttpbinding"></a>\<> zpráv > \<WSDualHttpBinding
Definuje zabezpečení na [ \<](wsdualhttpbinding.md)úrovni zprávy pro WSDualHttpBinding >.  
  
 \<system.ServiceModel>  
\<> vazeb  
\<wsDualHttpBinding>  
\<> vazby  
\<> zabezpečení  
\<> zprávy  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
         negotiateServiceCredential="Boolean"
         algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
</message>
```  
  
## <a name="type"></a>type  
 <xref:System.ServiceModel.MessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|algorithmSuite|Volitelný parametr. Nastaví šifrování zpráv a algoritmy pro zabalení klíčů. Algoritmy a velikosti klíčů jsou určeny <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> třídou. Tyto algoritmy jsou mapovány na ty, které jsou zadány ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).<br /><br /> Možné hodnoty viz níže. Výchozí hodnota je `Basic256`.|  
|clientCredentialType|Volitelný parametr. Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů pomocí režimu `Message`zabezpečení. Možné hodnoty viz níže. Výchozí hodnota je `Windows`.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType>.|  
|negotiateServiceCredential|Volitelný parametr. Logická hodnota určující, zda je pověření služby zřízené na vzdáleném klientovi nebo získáno ze služby klientovi prostřednictvím procesu vyjednávání. Toto vyjednávání je prekurzorem pro běžný výměnu zpráv.<br /><br /> Pokud se `clientCredentialType` atribut rovná None, username nebo Certificate, nastavením tohoto `false` atributu znamená, že je certifikát služby k dispozici na klientovi mimo IP síť a že klient potřebuje zadat certifikát služby (pomocí serviceCertificate >) v [ \<chování služby ServiceCredentials >](servicecredentials.md) . [ \<](servicecertificate-of-servicecredentials.md) Tento režim je interoperabilní pomocí zásobníků SOAP, které implementují WS-Trust a WS-SecureConversation.<br /><br /> Pokud je `Windows`atribut nastaven na hodnotu `false` , nastavením tohoto atributu určíte ověřování založené na protokolu Kerberos. `ClientCredentialType` To znamená, že klient a služba musí být součástí stejné domény Kerberos. Tento režim se vzájemně spolupracuje se zásobníky SOAP, které implementují profil tokenu Kerberos (jak je definováno v OASIS WSS TC) a také WS-Trust a WS-SecureConversation. Pokud je `true`tento atribut, způsobí vyjednávání .NET SOAP, které tunely SPNEGO Exchange prostřednictvím zpráv SOAP.<br /><br /> Výchozí hodnota je `true`.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Basic128|Pro zabalení klíče použijte šifrování Aes128, SHA1 pro Digest zpráv a RSA-výplně OAEP-mgf1p.|  
|Basic192|Pro zabalení klíče použijte šifrování Aes192, SHA1 pro Digest zpráv, RSA-výplně OAEP-mgf1p.|  
|Basic256|Pro zabalení klíče použijte šifrování AES256, SHA1 pro Digest zpráv, RSA-výplně OAEP-mgf1p.|  
|Basic256Rsa15|Použijte AES256 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.|  
|Basic192Rsa15|Použijte Aes192 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.|  
|TripleDes|Pro zabalení klíče použijte šifrování TripleDes, SHA1 pro Digest zprávy, RSA-výplně OAEP-mgf1p.|  
|Basic128Rsa15|Použijte Aes128 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.|  
|TripleDesRsa15|Pro zabalení klíče použijte šifrování TripleDes, SHA1 pro Message Digest a Rsa15.|  
|Basic128Sha256|Pro zabalení klíče použijte AES256 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.|  
|Basic192Sha256|Pro zabalení klíče použijte Aes192 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.|  
|Basic256Sha256|Pro zabalení klíče použijte AES256 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.|  
|TripleDesSha256|Pro zabalení klíče použijte TripleDes pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.|  
|Basic128Sha256Rsa15|Použijte Aes128 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.|  
|Basic192Sha256Rsa15|Použijte Aes192 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.|  
|Basic256Sha256Rsa15|Použijte AES256 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.|  
|TripleDesSha256Rsa15|Pro zabalení zprávy použijte TripleDes pro šifrování zpráv, SHA256 pro Message Digest a Rsa15.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Žádné|Díky tomu může služba spolupracovat s anonymními klienty. Na straně služby to znamená, že služba nevyžaduje žádné přihlašovací údaje klienta. V klientovi to znamená, že klient neposkytuje žádné přihlašovací údaje klienta.|  
|Windows|Povoluje, aby Exchange SOAP byly pod ověřeným kontextem pověření systému Windows. `true`Pokud je `negotiateServiceCredential` atribut nastavený na, provede se buď vyjednávání SSPI, nebo Kerberos (interoperabilní Standard).|  
|UserName|Umožňuje službě, aby vyžadovala ověření klienta pomocí přihlašovacích údajů uživatelského jména. WCF nepodporuje odeslání Digest hesla ani odvození klíčů pomocí hesla a použití takových klíčů pro zabezpečení zpráv. Technologie WCF proto vynutila, že při použití přihlašovacích údajů uživatelského jména je přenos zabezpečený. Tento režim přihlašovacích údajů má za následek vzájemně ovladatelné nebo neinteroperabilní vyjednávání založené na `negotiateServiceCredential` atributu.|  
|Certifikát|Umožňuje službě, aby vyžadovala ověření klienta pomocí certifikátu. Pokud je použit režim zabezpečení zprávy a `negotiateServiceCredential` atribut je nastaven na `false`hodnotu, musí být klient zřízen s certifikátem služby.|  
|Třídy IssuedToken|Určuje vlastní token, který je obvykle vydaný službou tokenu zabezpečení.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> zabezpečení](security-of-wsdualhttpbinding.md)|Definuje možnosti [ \<zabezpečení WSDualHttpBinding >](wsdualhttpbinding.md).|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSDualHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>
- <xref:System.ServiceModel.MessageSecurityOverHttp>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<> vazby](../../../misc/binding.md)
