---
title: <message> z <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 621abbde-590b-454d-90ac-68dc3c69c720
ms.openlocfilehash: 5a4d7bb41a57ca25397f585a2d5684ca6abdfa33
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738972"
---
# <a name="message-of-wshttpbinding"></a>\<> zprávy \<wsHttpBinding >
Definuje nastavení pro zabezpečení [\<wsHttpBinding >](wshttpbinding.md)na úrovni zprávy.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsHttpBinding >** ](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpečení >** ](security-of-wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zpráva >**  
  
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
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|algorithmSuite|Nastaví šifrování zpráv a algoritmy pro zabalení klíčů. Algoritmy a velikosti klíčů jsou určeny třídou <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>. Tyto algoritmy jsou mapovány na ty, které jsou zadány ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).<br /><br /> Výchozí hodnota je `Basic256`.|  
|clientCredentialType|Volitelné. Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů pomocí režimu zabezpečení `Message` nebo `TransportWithMessageCredentials`. Podívejte se na následující výčtové hodnoty. Výchozí hodnota je `Windows`.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType>.|  
|establishSecurityContext|Logická hodnota určující, zda kanál zabezpečení vytváří zabezpečenou relaci. Zabezpečená relace vytvoří token kontextu zabezpečení (SCT) před výměnou zpráv aplikace. Po navázání SCT kanál zabezpečení nabízí rozhraní <xref:System.ServiceModel.Channels.ISession> k horním kanálům. Další informace o použití zabezpečených relací najdete v tématu [Postupy: Vytvoření zabezpečené relace](../../../wcf/feature-details/how-to-create-a-secure-session.md).<br /><br /> Výchozí hodnota je `true`.|  
|negotiateServiceCredential|Volitelné. Logická hodnota, která určuje, zda je pověření služby zřízené na vzdáleném klientovi nebo získáno ze služby klientovi prostřednictvím procesu vyjednávání. Toto vyjednávání je prekurzorem pro běžný výměnu zpráv.<br /><br /> Pokud se atribut `clientCredentialType` rovná žádnému, uživatelskému jménu nebo certifikátu, nastavení tohoto atributu na hodnotu `false` znamená, že je certifikát služby dostupný v klientovi mimo IP síť a že klient potřebuje zadat certifikát služby (pomocí [\<serviceCertificate >](servicecertificate-of-servicecredentials.md)) v chování služby [\<ServiceCredentials >](servicecredentials.md) . Tento režim je interoperabilní pomocí zásobníků SOAP, které implementují WS-Trust a WS-SecureConversation.<br /><br /> Pokud je atribut `ClientCredentialType` nastaven na hodnotu `Windows`, nastavení tohoto atributu na `false` Určuje ověřování na základě protokolu Kerberos. To znamená, že klient a služba musí být součástí stejné domény Kerberos. Tento režim se vzájemně spolupracuje se zásobníky SOAP, které implementují profil tokenu Kerberos (jak je definováno v OASIS WSS TC) a také WS-Trust a WS-SecureConversation.<br /><br /> Pokud je tento atribut `true`, způsobí vyjednávání .NET SOAP, které tunely SPNego Exchange prostřednictvím zpráv SOAP.<br /><br /> Výchozí hodnota je `true`.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite – atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Basic128|Pro zabalení klíče použijte šifrování Basic128, SHA1 pro Digest zpráv a RSA-výplně OAEP-mgf1p.|  
|Basic192|Pro zabalení klíče použijte šifrování Basic192, SHA1 pro Digest zpráv, RSA-výplně OAEP-mgf1p.|  
|Basic256|Pro zabalení klíče použijte šifrování Basic256, SHA1 pro Digest zpráv, RSA-výplně OAEP-mgf1p.|  
|Basic256Rsa15|Použijte Basic256 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.|  
|Basic192Rsa15|Použijte Basic192 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.|  
|TripleDes|Pro zabalení klíče použijte šifrování TripleDes, SHA1 pro Digest zprávy, RSA-výplně OAEP-mgf1p.|  
|Basic128Rsa15|Použijte Basic128 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.|  
|TripleDesRsa15|Pro zabalení klíče použijte šifrování TripleDes, SHA1 pro Message Digest a Rsa15.|  
|Basic128Sha256|Pro zabalení klíče použijte Basic256 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.|  
|Basic192Sha256|Pro zabalení klíče použijte Basic192 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.|  
|Basic256Sha256|Pro zabalení klíče použijte Basic256 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.|  
|TripleDesSha256|Pro zabalení klíče použijte TripleDes pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.|  
|Basic128Sha256Rsa15|Použijte Basic128 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.|  
|Basic192Sha256Rsa15|Použijte Basic192 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.|  
|Basic256Sha256Rsa15|Použijte Basic256 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.|  
|TripleDesSha256Rsa15|Pro zabalení zprávy použijte TripleDes pro šifrování zpráv, SHA256 pro Message Digest a Rsa15.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType – atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádné|Díky tomu může služba spolupracovat s anonymními klienty. Na straně služby to znamená, že služba nevyžaduje žádné přihlašovací údaje klienta. V klientovi to znamená, že klient neposkytuje žádné přihlašovací údaje klienta.|  
|Certifikát|Umožňuje službě, aby vyžadovala ověření klienta pomocí certifikátu. Pokud je použit režim zabezpečení zprávy a atribut `negotiateServiceCredential` je nastaven na hodnotu `false`, musí být klient zřízen s certifikátem služby.|  
|Třídy IssuedToken|Určuje vlastní token, který je obvykle vydaný službou tokenu zabezpečení.|  
|UserName|Umožňuje službě, aby vyžadovala ověření klienta pomocí přihlašovacích údajů uživatelského jména. WCF nepodporuje odeslání Digest hesla ani odvození klíčů pomocí hesla a použití takových klíčů pro zabezpečení zpráv. Technologie WCF proto vynutila, že při použití přihlašovacích údajů uživatelského jména je přenos zabezpečený. Tento režim přihlašovacích údajů má za následek vzájemně ovladatelné nebo neinteroperabilní vyjednávání založené na atributu `negotiateServiceCredential`.|  
|Windows|Povoluje, aby Exchange SOAP byly pod ověřeným kontextem pověření systému Windows. Pokud je atribut `negotiateServiceCredential` nastaven na hodnotu `true`, provede se buď vyjednávání SSPI, nebo Kerberos (interoperabilní Standard).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[> zabezpečení \<](security-of-wshttpbinding.md)|Definuje nastavení zabezpečení pro [\<wsHttpBinding >](wshttpbinding.md).|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.NonDualMessageSecurityOverHttpElement>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [vazba \<](bindings.md)
