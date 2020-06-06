---
title: <message>prvek elementu<netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 1d71edd9-c085-4c2e-b6d3-980c313366f9
ms.openlocfilehash: 76c4a0a30b637bc168855b091029a959b858401e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739008"
---
# <a name="message-element-of-nettcpbinding"></a>\<message>prvek elementu\<netTcpBinding>
Definuje typ požadavků zabezpečení na úrovni zprávy pro koncový bod nakonfigurovaný pomocí [\<netTcpBinding>](nettcpbinding.md) .  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<message algorithmSuite="System.Servicemodel.Security.SecurityAlgorithmsuite"
         clientCredentialType="None/Windows/UserName/Certificate/IssuedToken" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`algorithmSuite`|Nastaví šifrování zpráv a algoritmy pro zabalení klíčů. Algoritmy a velikosti klíčů jsou určeny <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> třídou. Tyto algoritmy jsou mapovány na ty, které jsou zadány ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).<br /><br /> Možné hodnoty jsou uvedeny v následující tabulce. Výchozí hodnota je `Basic256`.<br /><br /> Pokud vazba služby určuje `algorithmSuite` hodnotu, která není shodná s výchozí hodnotou, a vygenerujete konfigurační soubor pomocí Svcutil. exe, není generována správně a je nutné ručně upravit konfigurační soubor pro nastavení tohoto atributu na požadovanou hodnotu.|  
|`clientCredentialType`|Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů pomocí zabezpečení založeného na zprávách. Možné hodnoty jsou uvedeny v následující tabulce. Výchozí hodnota je `UserName`. Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType> .|  
  
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
|Žádné|Díky tomu může služba spolupracovat s anonymními klienty. Ve službě to znamená, že služba nevyžaduje žádná pověření klienta. V klientovi to znamená, že klient neposkytuje žádné přihlašovací údaje klienta.|  
|Windows|Povoluje, aby Exchange SOAP byly pod ověřeným kontextem pověření systému Windows.|  
|UserName|Umožňuje službě, aby vyžadovala ověření klienta pomocí přihlašovacích údajů uživatelského jména. WCF nepodporuje odeslání Digest hesla ani odvození klíčů pomocí hesla a použití takových klíčů pro zabezpečení zpráv. Technologie WCF proto vynutila, že při použití přihlašovacích údajů uživatelského jména je přenos zabezpečený. Tento režim přihlašovacích údajů má za následek vzájemně ovladatelné nebo neinteroperabilní vyjednávání založené na `negotiateServiceCredential` atributu.|  
|Certifikát|Umožňuje službě, aby vyžadovala ověření klienta pomocí certifikátu. Pokud je použit režim zabezpečení zprávy a `negotiateServiceCredential` atribut je nastaven na hodnotu `false` , musí být klient zřízen s certifikátem služby.|  
|Třídy IssuedToken|Určuje vlastní token, který je obvykle vydaný službou tokenu zabezpečení (STS).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|Definuje možnosti zabezpečení pro <xref:System.ServiceModel.Configuration.NetTcpBindingElement> .|  
  
## <a name="remarks"></a>Poznámky  
 Zpráva používá zabezpečení na úrovni zprávy pro integritu a důvěrnost zprávy SOAP a pro vzájemné ověřování partnerských partnerů. Pokud je tento režim zabezpečení vybraný u vazby, nakonfiguruje se zásobník kanálů s prvky vazby zabezpečení zprávy a zprávy protokolu SOAP se zabezpečují v souladu s normami WS-Security *.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.MessageSecurityOverTcp>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
