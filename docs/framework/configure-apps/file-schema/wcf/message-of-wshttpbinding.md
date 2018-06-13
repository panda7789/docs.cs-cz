---
title: '&lt;message&gt; – &lt;wsHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 621abbde-590b-454d-90ac-68dc3c69c720
ms.openlocfilehash: 29cef7aa215b29ac5c7a986b456e5e5e06ba135f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364622"
---
# <a name="ltmessagegt-of-ltwshttpbindinggt"></a>&lt;message&gt; – &lt;wsHttpBinding&gt;
Definuje nastavení pro zprávy úroveň zabezpečení [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 \<system.ServiceModel>  
\<vazby >  
\<wsHttpBinding>  
\<Vazba >  
\<zabezpečení >  
\<Zpráva >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<message   
   algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
   clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
   establishSecurityContext="Boolean"  
   negotiateServiceCredential="Boolean" />  
```  
  
## <a name="type"></a>Typ  
 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|algorithmSuite|Nastaví zprávu algoritmy šifrování a klíč wrap. Algoritmy a velikosti klíče jsou určeny <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> třídy. Tyto algoritmy mapovat platformám zadaným v specifikace jazyka zásady zabezpečení (WS-SecurityPolicy).<br /><br /> Výchozí hodnota je `Basic256`.|  
|clientCredentialType|Volitelné. Určuje typ pověření, které se používají při provádění ověřování klientů pomocí režim zabezpečení je `Message` nebo `TransportWithMessageCredentials`. Najdete v níže uvedené hodnoty výčtu. Výchozí hodnota je `Windows`.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType>.|  
|establishSecurityContext|Logická hodnota, která určuje, zda kanál zabezpečení vytvoří zabezpečené relaci. Zabezpečené relace vytváří zabezpečení kontextu tokenu (SCT) před výměna zpráv aplikace. Po vytvoření SCT nabízí zabezpečený kanál <xref:System.ServiceModel.Channels.ISession> rozhraní pro horní kanály. Další informace o použití zabezpečených relací najdete v tématu [postupy: vytvoření zabezpečené relace](../../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md).<br /><br /> Výchozí hodnota je `true`.|  
|negotiateServiceCredential|Volitelné. Logická hodnota, která určuje, zda je zřízený na straně klienta vzdálené správy přihlašovací údaje služby, nebo je klientovi procesem vyjednávání získat ze služby. Takové vyjednávání je předchůdcem služby exchange obvykle zprávy.<br /><br /> Pokud `clientCredentialType` rovná atributu na hodnotu None, uživatelské jméno nebo certifikát, nastavení tohoto atributu na `false` znamená, že certifikát služby je k dispozici na straně klienta vzdálené správy a že klient musí určit certifikát služby (pomocí [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) v [ \<– serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) služby chování. Tento režim je vzájemná spolupráce s zásobníky SOAP, které implementují třídu WS-Trust a WS-SecureConversation.<br /><br /> Pokud `ClientCredentialType` je atribut nastaven na `Windows`, nastavení tohoto atributu na `false` Určuje ověřování pomocí protokolu Kerberos. To znamená, že klient a služba musí být součástí stejné domény protokolu Kerberos. Tento režim je vzájemná spolupráce s zásobníky SOAP, které implementují třídu tokenu profil protokolu Kerberos (podle definice v OASIS WSS TC) a WS-Trust a WS-SecureConversation.<br /><br /> Když tento atribut je `true`, způsobí, že vyjednávání protokolu SOAP rozhraní .NET, která tunelových propojení SPNego exchange prostřednictvím protokolu SOAP zprávy.<br /><br /> Výchozí hodnota je `true`.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Basic128|Použijte šifrování Basic128, Sha1 pro hodnota hash a šifrování Rsa. oaep mgf1p zabalení klíče.|  
|Basic192|Použijte šifrování pomocí Basic192, Sha1 pro hodnotu hash zpráv, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256|Použijte šifrování pomocí Basic256, Sha1 pro hodnotu hash zpráv, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256Rsa15|Použijte Basic256 pro šifrování zpráv, Sha1 pro hodnota hash a Rsa15 pro zabalení klíče.|  
|Basic192Rsa15|Použijte Basic192 pro šifrování zpráv, Sha1 pro hodnota hash a Rsa15 pro zabalení klíče.|  
|TripleDes|Použití šifrování TripleDes, Sha1 pro hodnotu hash zpráv, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic128Rsa15|Použijte Basic128 pro šifrování zpráv, Sha1 pro hodnota hash a Rsa15 pro zabalení klíče.|  
|TripleDesRsa15|Použití šifrování TripleDes, Sha1 pro hodnota hash a Rsa15 pro zabalení klíče.|  
|Basic128Sha256|Použijte Basic256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic192Sha256|Použijte Basic192 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256Sha256|Použijte Basic256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|TripleDesSha256|Použití šifrování TripleDes pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic128Sha256Rsa15|Použijte Basic128 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|Basic192Sha256Rsa15|Použijte Basic192 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|Basic256Sha256Rsa15|Použijte Basic256 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|TripleDesSha256Rsa15|Použití šifrování TripleDes pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádné|To umožňuje službu k interakci s anonymní klienty. Na straně služby to znamená, že služba nevyžaduje žádné pověření klienta. Na klientovi to znamená, že klient nenabízí žádné pověření klienta.|  
|certifikát|Umožňuje službě vyžadují, ověření klienta pomocí certifikátu. Pokud se používá režim zabezpečení zprávy a `negotiateServiceCredential` je atribut nastaven na `false`, klient musí být opatřena certifikát služby.|  
|IssuedToken|Určuje vlastní token, obvykle vydávají služby tokenů zabezpečení.|  
|UserName|Umožňuje službě vyžadují, ověření klienta pomocí pověření uživatelského jména. WCF nepodporuje odesílání hodnotu hash hesla nebo odvozování klíče pomocí hesla a použití tyto klíče pro zabezpečení zpráv. Jako takový WCF vynutí, že při použití uživatelské jméno pověření zabezpečené přenosu. Tento režim pověření výsledkem umožňuje vzájemnou spolupráci exchange nebo jiný umožňuje vzájemnou spolupráci vyjednávání na základě `negotiateServiceCredential` atribut.|  
|Windows|Umožňuje výměnu SOAP pod pro ověřený kontext pověření systému Windows. Pokud `negotiateServiceCredential` je atribut nastaven na `true`, buď provede vyjednávání SSPI nebo protokolu Kerberos (umožňuje vzájemnou spolupráci standard).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|Definuje nastavení zabezpečení pro [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.NonDualMessageSecurityOverHttpElement>  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)
