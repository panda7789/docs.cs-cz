---
title: <message> z <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 75101744-eed8-4d61-91f4-5fc4473a21f2
ms.openlocfilehash: aef03634ed6156d3a7e052ccdbde35fdfda99cc3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736723"
---
# <a name="message-of-wsdualhttpbinding"></a>\<> zprávy \<wsDualHttpBinding >
Definuje zabezpečení na úrovni zprávy pro [\<wsDualHttpBinding >](wsdualhttpbinding.md).  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsDualHttpBinding >** ](wsdualhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpečení >** ](security-of-wsdualhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zpráva >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
         negotiateServiceCredential="Boolean"
         algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
</message>
```  
  
## <a name="type"></a>Typ  
 <xref:System.ServiceModel.MessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|algorithmSuite|Volitelné. Nastaví šifrování zpráv a algoritmy pro zabalení klíčů. Algoritmy a velikosti klíčů jsou určeny třídou <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. Tyto algoritmy jsou mapovány na ty, které jsou zadány ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).<br /><br /> Možné hodnoty viz níže. Výchozí hodnota je `Basic256`.|  
|clientCredentialType|Volitelné. Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů pomocí režimu zabezpečení `Message`. Možné hodnoty viz níže. Výchozí hodnota je `Windows`.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType>.|  
|negotiateServiceCredential|Volitelné. Logická hodnota určující, zda je pověření služby zřízené na vzdáleném klientovi nebo získáno ze služby klientovi prostřednictvím procesu vyjednávání. Toto vyjednávání je prekurzorem pro běžný výměnu zpráv.<br /><br /> Pokud se atribut `clientCredentialType` rovná žádnému, uživatelskému jménu nebo certifikátu, nastavení tohoto atributu na hodnotu `false` znamená, že je certifikát služby dostupný v klientovi mimo IP síť a že klient potřebuje zadat certifikát služby (pomocí [\<serviceCertificate >](servicecertificate-of-servicecredentials.md)) v chování služby [\<ServiceCredentials >](servicecredentials.md) . Tento režim je interoperabilní pomocí zásobníků SOAP, které implementují WS-Trust a WS-SecureConversation.<br /><br /> Pokud je atribut `ClientCredentialType` nastaven na hodnotu `Windows`, nastavení tohoto atributu na `false` Určuje ověřování na základě protokolu Kerberos. To znamená, že klient a služba musí být součástí stejné domény Kerberos. Tento režim se vzájemně spolupracuje se zásobníky SOAP, které implementují profil tokenu Kerberos (jak je definováno v OASIS WSS TC) a také WS-Trust a WS-SecureConversation. Pokud je tento atribut `true`, způsobí vyjednávání .NET SOAP, které tunely SPNego Exchange prostřednictvím zpráv SOAP.<br /><br /> Výchozí hodnota je `true`.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite – atribut  
  
|Hodnota|Popis|  
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
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádné|Díky tomu může služba spolupracovat s anonymními klienty. Na straně služby to znamená, že služba nevyžaduje žádné přihlašovací údaje klienta. V klientovi to znamená, že klient neposkytuje žádné přihlašovací údaje klienta.|  
|Windows|Povoluje, aby Exchange SOAP byly pod ověřeným kontextem pověření systému Windows. Pokud je atribut `negotiateServiceCredential` nastaven na hodnotu `true`, provede se buď vyjednávání SSPI, nebo Kerberos (interoperabilní Standard).|  
|UserName|Umožňuje službě, aby vyžadovala ověření klienta pomocí přihlašovacích údajů uživatelského jména. WCF nepodporuje odeslání Digest hesla ani odvození klíčů pomocí hesla a použití takových klíčů pro zabezpečení zpráv. Technologie WCF proto vynutila, že při použití přihlašovacích údajů uživatelského jména je přenos zabezpečený. Tento režim přihlašovacích údajů má za následek vzájemně ovladatelné nebo neinteroperabilní vyjednávání založené na atributu `negotiateServiceCredential`.|  
|Certifikát|Umožňuje službě, aby vyžadovala ověření klienta pomocí certifikátu. Pokud je použit režim zabezpečení zprávy a atribut `negotiateServiceCredential` je nastaven na hodnotu `false`, musí být klient zřízen s certifikátem služby.|  
|Třídy IssuedToken|Určuje vlastní token, který je obvykle vydaný službou tokenu zabezpečení.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[> zabezpečení \<](security-of-wsdualhttpbinding.md)|Definuje možnosti zabezpečení [\<wsDualHttpBinding >](wsdualhttpbinding.md).|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSDualHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>
- <xref:System.ServiceModel.MessageSecurityOverHttp>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [vazba \<](bindings.md)
