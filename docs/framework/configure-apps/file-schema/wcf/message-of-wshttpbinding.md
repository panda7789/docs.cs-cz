---
title: '&lt;message&gt; – &lt;wsHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 621abbde-590b-454d-90ac-68dc3c69c720
ms.openlocfilehash: 28ea1cad77b5a35fa16c98b816c1c82de71bd7cb
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147769"
---
# <a name="ltmessagegt-of-ltwshttpbindinggt"></a>&lt;message&gt; – &lt;wsHttpBinding&gt;
Definuje nastavení pro zabezpečení na úrovni zprávy z [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 \<system.ServiceModel>  
\<vazby >  
\<wsHttpBinding>  
\<Vytvoření vazby >  
\<zabezpečení >  
\<Zpráva >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
         establishSecurityContext="Boolean"
         negotiateServiceCredential="Boolean" />
```  
  
## <a name="type"></a>Typ  
 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|algorithmSuite|Nastaví zprávu algoritmy šifrování a klíč zalamování řádků. Algoritmy a velikosti klíče jsou určeny <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> třídy. Tyto algoritmy namapovat na uvedené ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).<br /><br /> Výchozí hodnota je `Basic256`.|  
|Typ clientCredentialType|Volitelné. Určuje typ přihlašovacích údajů se použije při použití režimu zabezpečení rozhraní provádí ověření klienta `Message` nebo `TransportWithMessageCredentials`. Podívejte se níže uvedené hodnoty výčtu. Výchozí hodnota je `Windows`.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType>.|  
|establishSecurityContext|Logická hodnota, která určuje, zda kanálu zabezpečení vytváří zabezpečenou relaci. Zabezpečené relace vytváří bezpečnostní kontext Token (SCT) před výměnou zprávy aplikace. Po vytvoření SCT nabízí zabezpečený kanál <xref:System.ServiceModel.Channels.ISession> rozhraní do horní kanálů. Další informace o použití zabezpečených relací najdete v tématu [jak: Vytvoření zabezpečené relace](../../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md).<br /><br /> Výchozí hodnota je `true`.|  
|negotiateServiceCredential|Volitelné. Logická hodnota, která určuje, zda přihlašovací údaje služby je zřízený v klientovi mimo pásmo nebo se získá od služby ke klientovi procesem vyjednávání. Takové vyjednávání je předpokladem k výměně zpráv obvyklé.<br /><br /> Pokud `clientCredentialType` atributu rovná na hodnotu None, uživatelské jméno nebo certifikát, nastavení tohoto atributu na `false` znamená, že certifikát služby je k dispozici na klientovi mimo IP síť a že klient musí a určete certifikát služby (pomocí [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) v [ \<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) služeb chování. Tento režim se vzájemná spolupráce s zásobníky SOAP, které implementují WS-Trust a WS-SecureConversation.<br /><br /> Pokud `ClientCredentialType` atribut je nastaven na `Windows`, nastavení tohoto atributu na `false` Určuje ověřování na základě protokolu Kerberos. To znamená, že klient a služba musí být součástí stejné domény pomocí protokolu Kerberos. Tento režim se vzájemná spolupráce s zásobníky SOAP, které implementují profilu token protokolu Kerberos (jak jsou definovány v OASIS WSS TC) a WS-Trust a WS-SecureConversation.<br /><br /> Pokud tento atribut je `true`, dojde k vygenerování vyjednávání protokolu SOAP .NET, které tunelových propojení SPNego exchange přes zprávy protokolu SOAP.<br /><br /> Výchozí hodnota je `true`.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Basic128|Zabalení klíče použijte Basic128 šifrování, algoritmus pro hash Sha1 a Rsa. oaep mgf1p.|  
|Basic192|Použijte šifrování Basic192, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256|Použijte šifrování Basic256, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256Rsa15|Použití Basic256 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.|  
|Basic192Rsa15|Použití Basic192 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.|  
|TripleDes|Použití šifrování TripleDes, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic128Rsa15|Použití Basic128 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.|  
|TripleDesRsa15|Použití šifrování TripleDes, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.|  
|Basic128Sha256|Použití Basic256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic192Sha256|Použití Basic192 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256Sha256|Použití Basic256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|TripleDesSha256|TripleDes použijte pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic128Sha256Rsa15|Použití Basic128 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|Basic192Sha256Rsa15|Použití Basic192 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|Basic256Sha256Rsa15|Použití Basic256 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|TripleDesSha256Rsa15|TripleDes použijte pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
  
## <a name="clientcredentialtype-attribute"></a>Typ clientCredentialType atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádná|To umožňuje službě komunikovat s anonymní klienty. Na straně služeb to znamená, že služba nevyžaduje žádné pověření klienta. Na straně klienta to znamená, že klient neposkytuje žádné pověření klienta.|  
|Certifikát|Umožňuje službě tak, aby vyžadovala, ověření klienta pomocí certifikátu. Pokud se používá režim zabezpečených zpráv a `negotiateServiceCredential` atribut je nastaven na `false`, klient musí být zřízená s certifikátem služby.|  
|Třídy IssuedToken|Určuje vlastní token, obvykle vydávají služby tokenů zabezpečení.|  
|UserName|Umožňuje službě tak, aby vyžadovala, ověření klienta pomocí přihlašovacích údajů uživatelského jména. WCF nepodporuje odesílání hodnotou hash hesla nebo odvození klíče pomocí hesla a pomocí těchto klíčů pro zabezpečení zpráv. V důsledku toho WCF vynutí, že při použití pověření uživatelských jmen je zabezpečený přenos. Výsledkem interoperabilní exchange nebo -interoperabilní vyjednávání na základě tohoto režimu přihlašovacích údajů `negotiateServiceCredential` atribut.|  
|Windows|Umožňuje výměnu SOAP být pod správou ověřený kontext přihlašovacích údajů Windows. Pokud `negotiateServiceCredential` atribut je nastaven na `true`, buď provede vyjednávání SSPI nebo aplikace pomocí protokolu Kerberos (interoperabilní standard).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádná  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|Definuje nastavení zabezpečení [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.NonDualMessageSecurityOverHttpElement>  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služeb a klientů](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
