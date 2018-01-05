---
title: "&lt;message&gt; – &lt;ws2007HttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ffd8db6-84a8-4b38-a9fe-2cb1a87a1c97
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5048bc2980d7eb51efc1707cfc143f3a81ddf81d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltmessagegt-of-ltws2007httpbindinggt"></a>&lt;message&gt; – &lt;ws2007HttpBinding&gt;
Definuje nastavení pro zprávy úroveň zabezpečení [ \<– ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.  
  
 \<systém. ServiceModel >  
\<vazby >  
\<– ws2007HttpBinding >  
\<Vazba >  
\<zabezpečení >  
\<Zpráva >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<ws2007HttpBinding>  
 <binding >  
  <security>  
   <message clientCredentialType =  
    "None/Windows/UserName/Certificate/IssuedToken"  
    establishSecurityContext="Boolean"  
    negotiateServiceCredential="Boolean"  
    algorithmSuite= Enumeration. See algorithmSuite Attribute below.  
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
|`algorithmSuite`|Nastaví zprávu algoritmy šifrování a klíč wrap. Algoritmy a velikosti klíče jsou určeny <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> třídy. Tyto algoritmy mapovat platformám zadaným v specifikace jazyka zásady zabezpečení (WS-SecurityPolicy).<br /><br /> Výchozí hodnota je Basic256.|  
|`clientCredentialType`|Volitelné. Určuje typ pověření, který se má použít při ověřování klienta pomocí režim zabezpečení `Message` nebo `TransportWithMessageCredentials`. Zobrazit výčet hodnoty v následující tabulce. Výchozí hodnota je Windows.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType>.|  
|`establishSecurityContext`|Hodnota, která určuje, zda kanál zabezpečení vytvoří zabezpečené relaci. Zabezpečené relace vytváří tokenu kontextu zabezpečení (SCT) před výměna zpráv aplikace. Po vytvoření SCT nabízí zabezpečený kanál <xref:System.ServiceModel.Channels.ISession> rozhraní pro horní kanály. Další informace o použití zabezpečených relací najdete v tématu [postupy: vytvoření zabezpečené relace](../../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md).<br /><br /> Výchozí hodnota je `true`.|  
|`negotiateServiceCredential`|Volitelné. Hodnota, která určuje, zda je zřízený na straně klienta vzdálené správy přihlašovací údaje služby, nebo je klientovi procesem vyjednávání získat ze služby. Takové vyjednávání je předchůdcem služby exchange obvykle zprávy.<br /><br /> Pokud `clientCredentialType` rovná atributu na hodnotu None, uživatelské jméno nebo certifikát, nastavení tohoto atributu na `false` znamená, že certifikát služby je k dispozici na straně klienta vzdálené správy a že klient musíte zadat certifikát služby (s použitím [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) v [ \<– serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) služby chování. Tento režim je vzájemná spolupráce s zásobníky SOAP, které implementují WS-Trust a WS-SecureConversation.<br /><br /> Pokud `ClientCredentialType` je atribut nastaven na `Windows`, nastavení tohoto atributu na `false` Určuje ověřování pomocí protokolu Kerberos. To znamená, že klient a služba musí být součástí stejné domény protokolu Kerberos. Tento režim je vzájemná spolupráce s zásobníky SOAP, které implementují tokenu profil protokolu Kerberos (podle definice v OASIS WSS TC) a WS-Trust a WS-SecureConversation.<br /><br /> Když tento atribut je `true`, způsobí, že vyjednávání protokolu SOAP .NET, která tunelových propojení <xref:System.ServiceModel.Security.Tokens.ServiceModelSecurityTokenTypes.Spnego%2A> exchange v protokolu SOAP zprávy.<br /><br /> Výchozí hodnota je `true`.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Basic128|Použijte šifrování pomocí algoritmu aes128 za pomoci, Sha1 pro hodnota hash a šifrování Rsa. oaep mgf1p pro zabalení klíče.|  
|Basic192|Použijte šifrování pomocí Aes192, Sha1 pro hodnotu hash zpráv, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256|Použijte šifrování pomocí Aes256, Sha1 pro hodnotu hash zpráv, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256Rsa15|Pomocí Aes256 pro šifrování zpráv, Sha1 pro hodnota hash a Rsa15 pro zabalení klíče.|  
|Basic192Rsa15|Použijte Aes192 pro šifrování zpráv, Sha1 pro hodnota hash a Rsa15 pro zabalení klíče.|  
|TripleDes|Použití šifrování TripleDes, Sha1 pro hodnotu hash zpráv, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic128Rsa15|Pomocí algoritmu aes128 za pomoci pro šifrování zpráv, Sha1 pro hodnota hash a Rsa15 pro zabalení klíče.|  
|TripleDesRsa15|Použití šifrování TripleDes, Sha1 pro hodnota hash a Rsa15 pro zabalení klíče.|  
|Basic128Sha256|Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic192Sha256|Použijte Aes192 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256Sha256|Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|TripleDesSha256|Použití šifrování TripleDes pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic128Sha256Rsa15|Pomocí algoritmu aes128 za pomoci pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|Basic192Sha256Rsa15|Použijte Aes192 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|Basic256Sha256Rsa15|Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|TripleDesSha256Rsa15|Použití šifrování TripleDes pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`None`|To umožňuje službu k interakci s anonymní klienty. Ve službě to znamená, že služba nevyžaduje žádné pověření klienta. Na klientovi to znamená, že klient nenabízí žádné pověření klienta.|  
|`Certificate`|Umožňuje službě vyžadují, ověření klienta pomocí certifikátu. Pokud `message` režimu zabezpečení se používá a `negotiateServiceCredential` je atribut nastaven na `false`, klient musí být zřízená s certifikát služby.|  
|`IssuedToken`|Určuje vlastní token, obvykle vystavené pomocí zabezpečení tokenu služby (STS).|  
|`UserName`|Umožňuje službě vyžadují, ověření klienta pomocí `UserName` přihlašovacích údajů. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]nepodporuje odesílání hodnotu hash hesla nebo odvozování klíče pomocí hesla a použití tyto klíče pro zabezpečení zpráv. Jako takový [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] vynutí, že při použití zabezpečené přenos `UserName` přihlašovací údaje. Tento režim pověření výsledkem umožňuje vzájemnou spolupráci exchange nebo jiný umožňuje vzájemnou spolupráci vyjednávání na základě `negotiateServiceCredential` atribut.|  
|`Windows`|Umožňuje výměnu SOAP být v kontextu ověřený `Windows` přihlašovacích údajů. Pokud `negotiateServiceCredential` je atribut nastaven na `true`, buď provede vyjednávání SSPI nebo protokolu Kerberos (umožňuje vzájemnou spolupráci standard).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|Definuje nastavení zabezpečení pro [ \<– ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md).|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.NonDualMessageSecurityOverHttpElement>  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)
