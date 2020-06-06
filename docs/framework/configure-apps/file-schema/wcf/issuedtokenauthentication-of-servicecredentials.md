---
title: <issuedTokenAuthentication> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: 6d468a27ee05fb4dd8cf087d10e5d170783d3454
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400360"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a>\<issuedTokenAuthentication> z \<serviceCredentials>
Určuje vlastní token vydaný jako pověření služby.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenAuthentication>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<issuedTokenAuthentication allowUntrustedRsaIssuers="Boolean"
                           audienceUriMode="Always/BearerKeyOnly/Never"
                           customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                           certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                           revocationMode="NoCheck/Online/Offline"
                           samlSerializer="String"
                           trustedStoreLocation="CurrentUser/LocalMachine">
  <allowedAudienceUris>
    <add allowedAudienceUri="String" />
  </allowedAudienceUris>
  <knownCertificates>
    <add findValue="String"
         storeLocation="CurrentUser/LocalMachine"
         storeName=" CurrentUser/LocalMachine"
         x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`allowedAudienceUris`|Získá sadu cílových identifikátorů URI, pro které <xref:System.IdentityModel.Tokens.SamlSecurityToken> může být token zabezpečení cílen, aby mohl být považován za platný v <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instanci. Další informace o použití tohoto atributu naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A> .|  
|`allowUntrustedRsaIssuers`|Logická hodnota určující, zda jsou povoleny nedůvěryhodné vystavitele certifikátů RSA.<br /><br /> Certifikáty jsou podepsané certifikačními autoritami (CAs) k ověření pravosti. Nedůvěryhodný Vydavatel je certifikační autorita, která nemá být důvěryhodná pro podepisování certifikátů.|  
|`audienceUriMode`|Načte hodnotu, která určuje, jestli se <xref:System.IdentityModel.Tokens.SamlSecurityToken> <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> má ověřit token zabezpečení. Tato hodnota je typu <xref:System.IdentityModel.Selectors.AudienceUriMode>. Další informace o použití tohoto atributu naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A> .|  
|`certificateValidationMode`|Nastaví režim ověřování certifikátu. Jedna z platných hodnot <xref:System.ServiceModel.Security.X509CertificateValidationMode> . Je-li nastaveno na hodnotu `Custom` , `customCertificateValidator` musí být zadána také. Výchozí formát je `ChainTrust`.|  
|`customCertificateValidatorType`|Volitelný řetězec. Typ a sestavení, které slouží k ověření vlastního typu. Tento atribut musí být nastaven `certificateValidationMode` , je-li nastavena na hodnotu `Custom` .|  
|`revocationMode`|Nastaví režim odvolání určující, zda dojde k provedení kontroly odvolání a zda je proveden online nebo offline. Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> .|  
|`samlSerializer`|Volitelný atribut řetězce, který určuje typ SamlSerializer, který se používá pro pověření služby. Výchozí hodnota je prázdný řetězec.|  
|`trustedStoreLocation`|Volitelný výčet. Jedno ze dvou umístění úložiště systému: `LocalMachine` nebo `CurrentUser` .|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|`knownCertificates`|Určuje kolekci <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> prvků, které určují důvěryhodné vystavitele pro pověření služby.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřením přihlašovacích údajů klienta.|  
  
## <a name="remarks"></a>Poznámky  
 Scénář vydaného tokenu má tři fáze. V první fázi se klientovi, který se pokouší o přístup ke službě, říká *služba tokenů zabezpečení*. Služba tokenů zabezpečení potom ověří klienta a následně vydá token klienta, obvykle token SAML (Security Assert Markup Language). Klient se pak vrátí ke službě s tokenem. Služba prověřuje token pro data, která umožňují službě ověřit token, a tedy klienta. Chcete-li ověřit token, je nutné, aby služba používala certifikát, který používá služba tokenů zabezpečení.  
  
 Tento prvek je úložištěm těchto certifikátů služby tokenu zabezpečení. Chcete-li přidat certifikáty, použijte [\<knownCertificates>](knowncertificates.md) . Vložte [\<add>](add-of-knowncertificates.md) pro každý certifikát, jak je znázorněno v následujícím příkladu.  
  
```xml  
<issuedTokenAuthentication>
  <knownCertificates>
    <add findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="My"
         X509FindType="FindBySubjectName" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
 Ve výchozím nastavení se certifikáty musí získat ze služby zabezpečeného tokenu. Tyto "známé" certifikáty zajistí, že ke službě budou mít přístup jenom legitimní klienti.  
  
 Další informace o použití tohoto konfiguračního prvku naleznete v tématu [How to: Configure a Credentials on a služba FS (Federation Service)](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Postupy: Konfigurace pověření ve službě Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
