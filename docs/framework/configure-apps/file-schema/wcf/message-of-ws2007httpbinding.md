---
title: <message> of <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 9ffd8db6-84a8-4b38-a9fe-2cb1a87a1c97
ms.openlocfilehash: bf0ed2de73505d5634d6c7d26881f9800a0bf1f2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166735"
---
# <a name="message-of-ws2007httpbinding"></a>\<Zpráva > z \<ws2007HttpBinding >
Definuje nastavení pro zabezpečení na úrovni zprávy z [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) elementu.  
  
 \<system.ServiceModel>  
\<vazby >  
\<ws2007HttpBinding>  
\<Vytvoření vazby >  
\<security>  
\<Zpráva >  
  
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
  
## <a name="type"></a>Type  
 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`algorithmSuite`|Nastaví zprávu algoritmy šifrování a klíč zalamování řádků. Algoritmy a velikosti klíče jsou určeny <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> třídy. Tyto algoritmy namapovat na uvedené ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).<br /><br /> Výchozí hodnota je Basic256.|  
|`clientCredentialType`|Volitelné. Určuje typ přihlašovacích údajů pro použití při ověřování klientů pomocí režimu zabezpečení rozhraní `Message` nebo `TransportWithMessageCredentials`. Zobrazit hodnoty výčtu v následující tabulce. Výchozí hodnota je Windows.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType>.|  
|`establishSecurityContext`|Hodnota, která určuje, zda kanálu zabezpečení vytváří zabezpečenou relaci. Zabezpečené relace vytvoří token kontextu zabezpečení (SCT) před výměnou zprávy aplikace. Po vytvoření SCT nabízí zabezpečený kanál <xref:System.ServiceModel.Channels.ISession> rozhraní do horní kanálů. Další informace o použití zabezpečených relací najdete v tématu [jak: Vytvoření zabezpečené relace](../../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md).<br /><br /> Výchozí hodnota je `true`.|  
|`negotiateServiceCredential`|Volitelné. Hodnota, která určuje, zda přihlašovací údaje služby je zřízený v klientovi mimo pásmo nebo se získá od služby ke klientovi procesem vyjednávání. Takové vyjednávání je předpokladem k výměně zpráv obvyklé.<br /><br /> Pokud `clientCredentialType` atributu rovná na hodnotu None, uživatelské jméno nebo certifikát, nastavení tohoto atributu na `false` znamená, že je k dispozici na klientovi mimo pásmo certifikát služby a že klient musí určete certifikát služby (pomocí [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) v [ \<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) služeb chování. Tento režim se vzájemná spolupráce s zásobníky SOAP, které implementují WS-Trust a WS-SecureConversation.<br /><br /> Pokud `ClientCredentialType` atribut je nastaven na `Windows`, nastavení tohoto atributu na `false` Určuje ověřování na základě protokolu Kerberos. To znamená, že klient a služba musí být součástí stejné domény pomocí protokolu Kerberos. Tento režim se vzájemná spolupráce s SOAP balíčcích, které implementují profilu token protokolu Kerberos (jak jsou definovány v OASIS WSS TC) a WS-Trust a WS-SecureConversation.<br /><br /> Pokud tento atribut je `true`, dojde k vygenerování vyjednávání protokolu SOAP .NET, které tunelových propojení <xref:System.ServiceModel.Security.Tokens.ServiceModelSecurityTokenTypes.Spnego%2A> exchange přes zprávy protokolu SOAP.<br /><br /> Výchozí hodnota je `true`.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Basic128|Zabalení klíče použijte Aes128 šifrování, algoritmus pro hash Sha1 a Rsa. oaep mgf1p.|  
|Basic192|Použijte šifrování Aes192, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256|Použijte šifrování pomocí Aes256, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256Rsa15|Pomocí Aes256 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.|  
|Basic192Rsa15|Použití Aes192 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.|  
|TripleDes|Použití šifrování TripleDes, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic128Rsa15|Použití Aes128 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.|  
|TripleDesRsa15|Použití šifrování TripleDes, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.|  
|Basic128Sha256|Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic192Sha256|Použití Aes192 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256Sha256|Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|TripleDesSha256|TripleDes použijte pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic128Sha256Rsa15|Použití Aes128 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|Basic192Sha256Rsa15|Použití Aes192 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|Basic256Sha256Rsa15|Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|TripleDesSha256Rsa15|TripleDes použijte pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType Attribute  
  
|Value|Popis|  
|-----------|-----------------|  
|`None`|To umožňuje službě komunikovat s anonymní klienty. Ve službě to znamená, že služba nevyžaduje žádné pověření klienta. Na straně klienta to znamená, že klient neposkytuje žádné pověření klienta.|  
|`Certificate`|Umožňuje službě tak, aby vyžadovala, ověření klienta pomocí certifikátu. Pokud `message` režimu zabezpečení se používá a `negotiateServiceCredential` atribut je nastaven na `false`, klient musí být poskytnut certifikát služby.|  
|`IssuedToken`|Určuje vlastní token, obvykle vydané službou tokenu služby zabezpečení (STS).|  
|`UserName`|Umožňuje službě tak, aby vyžadovala, ověření klienta pomocí `UserName` přihlašovacích údajů. WCF nepodporuje odesílání hodnotou hash hesla nebo odvození klíče pomocí hesla a pomocí těchto klíčů pro zabezpečení zpráv. V důsledku toho se vynutí, že při použití je zabezpečený přenos WCF `UserName` přihlašovací údaje. Výsledkem interoperabilní exchange nebo -interoperabilní vyjednávání na základě tohoto režimu přihlašovacích údajů `negotiateServiceCredential` atribut.|  
|`Windows`|Umožňuje výměnu SOAP bude v kontextu ověření `Windows` přihlašovacích údajů. Pokud `negotiateServiceCredential` atribut je nastaven na `true`, buď provede vyjednávání SSPI nebo aplikace pomocí protokolu Kerberos (interoperabilní standard).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|Definuje nastavení zabezpečení [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md).|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.NonDualMessageSecurityOverHttpElement>
- [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
