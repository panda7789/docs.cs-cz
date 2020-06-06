---
title: <message> z <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 9ffd8db6-84a8-4b38-a9fe-2cb1a87a1c97
ms.openlocfilehash: 3396f74f76d790759f4c32de2907607486701b1a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738942"
---
# <a name="message-of-ws2007httpbinding"></a>\<message> z \<ws2007HttpBinding>
Definuje nastavení pro zabezpečení na úrovni zprávy [\<ws2007HttpBinding>](ws2007httpbinding.md) elementu.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
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
  
## <a name="type"></a>Typ  
 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`algorithmSuite`|Nastaví šifrování zpráv a algoritmy pro zabalení klíčů. Algoritmy a velikosti klíčů jsou určeny <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> třídou. Tyto algoritmy jsou mapovány na ty, které jsou zadány ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).<br /><br /> Výchozí hodnota je Basic256.|  
|`clientCredentialType`|Nepovinný parametr. Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů pomocí režimu zabezpečení `Message` nebo `TransportWithMessageCredentials` . Podívejte se na hodnoty výčtu v následující tabulce. Výchozí hodnota je Windows.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType> .|  
|`establishSecurityContext`|Hodnota, která určuje, zda kanál zabezpečení vytváří zabezpečenou relaci. Zabezpečená relace vytvoří token kontextu zabezpečení (SCT) před výměnou zpráv aplikace. Po navázání SCT kanál zabezpečení nabízí <xref:System.ServiceModel.Channels.ISession> rozhraní pro horní kanály. Další informace o použití zabezpečených relací najdete v tématu [Postupy: Vytvoření zabezpečené relace](../../../wcf/feature-details/how-to-create-a-secure-session.md).<br /><br /> Výchozí hodnota je `true`.|  
|`negotiateServiceCredential`|Nepovinný parametr. Hodnota, která určuje, zda je pověření služby zřízené na vzdáleném klientovi nebo získáno ze služby klientovi prostřednictvím procesu vyjednávání. Toto vyjednávání je prekurzorem pro běžný výměnu zpráv.<br /><br /> Pokud se `clientCredentialType` atribut rovná None, username nebo Certificate, nastavení tohoto atributu `false` znamená, že je certifikát služby k dispozici na klientovi mimo IP síť a že klient musí ve svém chování služby zadat certifikát služby (pomocí [\<serviceCertificate>](servicecertificate-of-servicecredentials.md) ) [\<serviceCredentials>](servicecredentials.md) . Tento režim je interoperabilní pomocí zásobníků SOAP, které implementují WS-Trust a WS-SecureConversation.<br /><br /> Pokud `ClientCredentialType` je atribut nastaven na hodnotu `Windows` , nastavením tohoto atributu `false` určíte ověřování založené na protokolu Kerberos. To znamená, že klient a služba musí být součástí stejné domény Kerberos. Tento režim je interoperabilní pomocí zásobníků SOAP, které implementují profil tokenu Kerberos (jak je definováno ve OASIS WSS TC) a také WS-Trust a WS-SecureConversation.<br /><br /> Pokud je tento atribut `true` , způsobí vyjednávání rozhraní .NET SOAP, které provádí tunelové <xref:System.ServiceModel.Security.Tokens.ServiceModelSecurityTokenTypes.Spnego%2A> výměnu přes zprávy SOAP.<br /><br /> Výchozí formát je `true`.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite – atribut  
  
|Hodnota|Description|  
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
  
|Hodnota|Description|  
|-----------|-----------------|  
|`None`|Díky tomu může služba spolupracovat s anonymními klienty. Ve službě to znamená, že služba nevyžaduje žádná pověření klienta. V klientovi to znamená, že klient neposkytuje žádné přihlašovací údaje klienta.|  
|`Certificate`|Umožňuje službě, aby vyžadovala ověření klienta pomocí certifikátu. Pokud `message` je použit režim zabezpečení a `negotiateServiceCredential` atribut je nastaven na hodnotu `false` , musí být klient zřízen s certifikátem služby.|  
|`IssuedToken`|Určuje vlastní token, který je obvykle vydaný službou tokenu zabezpečení (STS).|  
|`UserName`|Umožňuje službě, aby vyžadovala ověření klienta pomocí `UserName` pověření. WCF nepodporuje odeslání Digest hesla ani odvození klíčů pomocí hesla a použití takových klíčů pro zabezpečení zpráv. Technologie WCF proto vynutila, že při použití přihlašovacích údajů je přenos zabezpečený `UserName` . Tento režim přihlašovacích údajů má za následek vzájemně ovladatelné nebo neinteroperabilní vyjednávání založené na `negotiateServiceCredential` atributu.|  
|`Windows`|Povoluje, aby Exchange SOAP byly pod ověřeným kontextem `Windows` přihlašovacích údajů. Pokud `negotiateServiceCredential` je atribut nastavený na `true` , provede se buď vyjednávání SSPI, nebo Kerberos (interoperabilní Standard).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<security>](security-of-ws2007httpbinding.md)|Definuje nastavení zabezpečení pro [\<ws2007HttpBinding>](ws2007httpbinding.md) .|  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.NonDualMessageSecurityOverHttpElement>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
