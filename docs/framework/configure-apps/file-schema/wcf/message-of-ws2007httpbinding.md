---
title: <message> z <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 9ffd8db6-84a8-4b38-a9fe-2cb1a87a1c97
ms.openlocfilehash: 987c51f65f5c36a70724fd62fecaf737943c2d9a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398037"
---
# <a name="message-of-ws2007httpbinding"></a>\<> zpráv > \<WS2007HttpBinding
Definuje nastavení pro zabezpečení na [ \<](ws2007httpbinding.md) úrovni zprávy prvku WS2007HttpBinding >.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007HttpBinding >** ](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-of-ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zprávy**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<ws2007HttpBinding>
  <binding>
    <security>
      <message clientCredentialType="None/Windows/UserName/Certificate/IssuedToken"
               establishSecurityContext="Boolean"
               negotiateServiceCredential="Boolean"
               algorithmSuite="Enumeration. See algorithmSuite Attribute below."
               defaultProtectionLevel="None/Sign/EncryptionAndSign" />
    </security>
  </binding>
</ws2007HttpBinding>
```  
  
## <a name="type"></a>type  
 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`algorithmSuite`|Nastaví šifrování zpráv a algoritmy pro zabalení klíčů. Algoritmy a velikosti klíčů jsou určeny <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> třídou. Tyto algoritmy jsou mapovány na ty, které jsou zadány ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).<br /><br /> Výchozí hodnota je Basic256.|  
|`clientCredentialType`|Volitelný parametr. Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů pomocí režimu `Message` zabezpečení nebo. `TransportWithMessageCredentials` Podívejte se na hodnoty výčtu v následující tabulce. Výchozí hodnota je Windows.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType>.|  
|`establishSecurityContext`|Hodnota, která určuje, zda kanál zabezpečení vytváří zabezpečenou relaci. Zabezpečená relace vytvoří token kontextu zabezpečení (SCT) před výměnou zpráv aplikace. Po navázání SCT kanál zabezpečení nabízí <xref:System.ServiceModel.Channels.ISession> rozhraní pro horní kanály. Další informace o používání zabezpečených relací najdete v [tématu How to: Vytvořte zabezpečenou relaci](../../../wcf/feature-details/how-to-create-a-secure-session.md).<br /><br /> Výchozí hodnota je `true`.|  
|`negotiateServiceCredential`|Volitelný parametr. Hodnota, která určuje, zda je pověření služby zřízené na vzdáleném klientovi nebo získáno ze služby klientovi prostřednictvím procesu vyjednávání. Toto vyjednávání je prekurzorem pro běžný výměnu zpráv.<br /><br /> Pokud se `clientCredentialType` atribut rovná None, username nebo Certificate, nastavením tohoto `false` atributu znamená, že je certifikát služby dostupný v klientovi mimo IP síť a že klient musí zadat certifikát služby (pomocí [ serviceCertificate\<>](servicecertificate-of-servicecredentials.md)) v chování služby [ ServiceCredentials>.\<](servicecredentials.md) Tento režim je interoperabilní pomocí zásobníků SOAP, které implementují WS-Trust a WS-SecureConversation.<br /><br /> Pokud je `Windows`atribut nastaven na hodnotu `false` , nastavením tohoto atributu určíte ověřování založené na protokolu Kerberos. `ClientCredentialType` To znamená, že klient a služba musí být součástí stejné domény Kerberos. Tento režim je interoperabilní pomocí zásobníků SOAP, které implementují profil tokenu Kerberos (jak je definováno ve OASIS WSS TC) a také WS-Trust a WS-SecureConversation.<br /><br /> Pokud je `true`tento atribut, způsobí vyjednávání rozhraní .NET SOAP, které provádí <xref:System.ServiceModel.Security.Tokens.ServiceModelSecurityTokenTypes.Spnego%2A> tunelové výměnu přes zprávy SOAP.<br /><br /> Výchozí hodnota je `true`.|  
  
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
|`None`|Díky tomu může služba spolupracovat s anonymními klienty. Ve službě to znamená, že služba nevyžaduje žádná pověření klienta. V klientovi to znamená, že klient neposkytuje žádné přihlašovací údaje klienta.|  
|`Certificate`|Umožňuje službě, aby vyžadovala ověření klienta pomocí certifikátu. Pokud `message` je použit režim zabezpečení `negotiateServiceCredential` a atribut je nastaven na `false`hodnotu, musí být klient zřízen s certifikátem služby.|  
|`IssuedToken`|Určuje vlastní token, který je obvykle vydaný službou tokenu zabezpečení (STS).|  
|`UserName`|Umožňuje službě, aby vyžadovala ověření klienta pomocí `UserName` pověření. WCF nepodporuje odeslání Digest hesla ani odvození klíčů pomocí hesla a použití takových klíčů pro zabezpečení zpráv. Technologie WCF proto vynutila, že při použití `UserName` přihlašovacích údajů je přenos zabezpečený. Tento režim přihlašovacích údajů má za následek vzájemně ovladatelné nebo neinteroperabilní vyjednávání založené na `negotiateServiceCredential` atributu.|  
|`Windows`|Povoluje, aby Exchange SOAP byly pod ověřeným kontextem `Windows` přihlašovacích údajů. `true`Pokud je `negotiateServiceCredential` atribut nastavený na, provede se buď vyjednávání SSPI, nebo Kerberos (interoperabilní Standard).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> zabezpečení](security-of-ws2007httpbinding.md)|Definuje nastavení zabezpečení pro [ \<WS2007HttpBinding >](ws2007httpbinding.md).|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.NonDualMessageSecurityOverHttpElement>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<> vazby](../../../misc/binding.md)
