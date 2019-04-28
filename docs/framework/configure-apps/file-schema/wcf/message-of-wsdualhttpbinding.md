---
title: <message> z <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 75101744-eed8-4d61-91f4-5fc4473a21f2
ms.openlocfilehash: 03a1ae9c220b6d7f84b501f26c5fe408fc702528
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768937"
---
# <a name="message-of-wsdualhttpbinding"></a>\<Zpráva > z \<wsDualHttpBinding >
Definuje zabezpečení na úrovni zprávy [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).  
  
 \<system.ServiceModel>  
\<vazby >  
\<wsDualHttpBinding>  
\<Vytvoření vazby >  
\<security>  
\<Zpráva >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
         negotiateServiceCredential="Boolean"
         algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
</message>
```  
  
## <a name="type"></a>Type  
 <xref:System.ServiceModel.MessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|algorithmSuite|Volitelné. Nastaví zprávu algoritmy šifrování a klíč zalamování řádků. Algoritmy a velikosti klíče jsou určeny <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> třídy. Tyto algoritmy namapovat na uvedené ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).<br /><br /> Možné hodnoty najdete níže. Výchozí hodnota je `Basic256`.|  
|clientCredentialType|Volitelné. Určuje typ přihlašovacích údajů se použije při použití režimu zabezpečení rozhraní provádí ověření klienta `Message`. Možné hodnoty najdete níže. Výchozí hodnota je `Windows`.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType>.|  
|negotiateServiceCredential|Volitelné. Logická hodnota, která určuje, zda přihlašovací údaje služby je zřízený v klientovi mimo pásmo nebo se získá od služby ke klientovi procesem vyjednávání. Takové vyjednávání je předpokladem k výměně zpráv obvyklé.<br /><br /> Pokud `clientCredentialType` atributu rovná na hodnotu None, uživatelské jméno nebo certifikát, nastavení tohoto atributu na `false` znamená, že certifikát služby je k dispozici na klientovi mimo IP síť a že klient musí a určete certifikát služby (pomocí [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) v [ \<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) služeb chování. Tento režim se vzájemná spolupráce s zásobníky SOAP, které implementují WS-Trust a WS-SecureConversation.<br /><br /> Pokud `ClientCredentialType` atribut je nastaven na `Windows`, nastavení tohoto atributu na `false` Určuje ověřování na základě protokolu Kerberos. To znamená, že klient a služba musí být součástí stejné domény pomocí protokolu Kerberos. Tento režim se vzájemná spolupráce s zásobníky SOAP, které implementují profilu token protokolu Kerberos (jak jsou definovány v OASIS WSS TC) a WS-Trust a WS-SecureConversation. Pokud tento atribut je `true`, dojde k vygenerování vyjednávání protokolu SOAP .NET, které tunelových propojení SPNego exchange přes zprávy protokolu SOAP.<br /><br /> Výchozí hodnota je `true`.|  
  
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
|Žádný|To umožňuje službě komunikovat s anonymní klienty. Na straně služeb to znamená, že služba nevyžaduje žádné pověření klienta. Na straně klienta to znamená, že klient neposkytuje žádné pověření klienta.|  
|Windows|Umožňuje výměnu SOAP být pod správou ověřený kontext přihlašovacích údajů Windows. Pokud `negotiateServiceCredential` atribut je nastaven na `true`, buď provede vyjednávání SSPI nebo aplikace pomocí protokolu Kerberos (interoperabilní standard).|  
|UserName|Umožňuje službě tak, aby vyžadovala, ověření klienta pomocí přihlašovacích údajů uživatelského jména. WCF nepodporuje odesílání hodnotou hash hesla nebo odvození klíče pomocí hesla a pomocí těchto klíčů pro zabezpečení zpráv. V důsledku toho WCF vynutí, že při použití pověření uživatelských jmen je zabezpečený přenos. Výsledkem interoperabilní exchange nebo -interoperabilní vyjednávání na základě tohoto režimu přihlašovacích údajů `negotiateServiceCredential` atribut.|  
|Certifikát|Umožňuje službě tak, aby vyžadovala, ověření klienta pomocí certifikátu. Pokud se používá režim zabezpečených zpráv a `negotiateServiceCredential` atribut je nastaven na `false`, klient musí být zřízená s certifikátem služby.|  
|Třídy IssuedToken|Určuje vlastní token, obvykle vydávají služby tokenů zabezpečení.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsdualhttpbinding.md)|Definuje možnosti zabezpečení [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSDualHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>
- <xref:System.ServiceModel.MessageSecurityOverHttp>
- [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
