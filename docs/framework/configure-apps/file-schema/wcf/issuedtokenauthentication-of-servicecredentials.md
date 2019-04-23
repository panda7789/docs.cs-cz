---
title: <issuedTokenAuthentication> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: d093b45269b230b4ff074d07a66290ab09592f60
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178565"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a>\<issuedTokenAuthentication> of \<serviceCredentials>
Určuje vlastní token vydaný jako pověření služby.  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors>  
\<chování >  
\<serviceCredentials>  
\<issuedTokenAuthentication>  
  
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
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`allowedAudienceUris`|Získá sadu cílových identifikátorů URI pro kterou <xref:System.IdentityModel.Tokens.SamlSecurityToken> token zabezpečení může služba je určená pro aby mohl být uznán platnou podle <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance. Další informace o použití tohoto atributu naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.|  
|`allowUntrustedRsaIssuers`|Logická hodnota, která určuje, jestli jsou povolená nedůvěryhodní Vystavitelé certifikátů RSA.<br /><br /> Certifikáty jsou podepsány certifikačními autoritami (CA) k ověření pravosti. Nedůvěryhodné Vystavitel je certifikační Autorita, která není zadána jako důvěryhodného k podepisování certifikátů.|  
|`audienceUriMode`|Získá hodnotu, která určuje, zda <xref:System.IdentityModel.Tokens.SamlSecurityToken> token zabezpečení <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> by měl být ověřen. Tato hodnota je typu <xref:System.IdentityModel.Selectors.AudienceUriMode>. Další informace o použití tohoto atributu naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.|  
|`certificateValidationMode`|Nastaví režim ověřování certifikátu. Jednu z platných hodnot z <xref:System.ServiceModel.Security.X509CertificateValidationMode>. Pokud hodnotu `Custom`, o `customCertificateValidator` musí být rovněž dodán. Výchozí hodnota je `ChainTrust`.|  
|`customCertificateValidatorType`|Volitelný řetězec. Typ a sestavení používané pro ověření vlastního typu. Tento atribut musí být nastaven při `certificateValidationMode` je nastavena na `Custom`.|  
|`revocationMode`|Nastaví režim odvolání určující, zda dochází ke kontrolám odvolání a pokud se provádí online nebo offline. Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.|  
|`samlSerializer`|Volitelný řetězec atribut, který určuje typ SamlSerializer, který se používá pro přihlašovací údaje služby. Výchozí hodnota je prázdný řetězec.|  
|`trustedStoreLocation`|Volitelný výčet. Jeden z umístění dvou systémových úložišť: `LocalMachine` nebo `CurrentUser`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`knownCertificates`|Určuje kolekci <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> prvky, které určuje důvěryhodných vystavitelů pro přihlašovací údaje služby.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Určuje přihlašovací údaje pro ověřování služby a nastavení vztahující se k ověření přihlašovacích údajů klienta.|  
  
## <a name="remarks"></a>Poznámky  
 Vydaný token scénář má tři fáze. V první fázi se klient pokouší o přístup ke službě označuje *služby tokenů zabezpečení*. Služba tokenů zabezpečení pak ověří klienta a následně vydá klienta token, obvykle token zabezpečení kontrolní výrazy SAML (Markup Language). Klient pak vrátí ke službě s tokenem. Služba zkontroluje token pro data, která umožňuje službě ověření tokenu a proto klienta. K ověření tokenu, certifikát používá služba tokenů zabezpečení musí být známo ke službě.  
  
 Tento element má úložiště pro tyto certifikáty služba tokenů zabezpečení. Chcete-li přidat certifikáty použít [ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). Vložit [ \<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) pro každý certifikát, jak je znázorněno v následujícím příkladu.  
  
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
  
 Ve výchozím nastavení certifikáty musí pocházet od Služba tokenů zabezpečení. Tyto certifikáty, ujistěte se, že, který klientům pouze bezpečných "známé" můžete přístup ke službě.  
  
 Další informace o použití tento prvek konfigurace, najdete v části [jak: Konfigurace pověření ve službě Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Postupy: Konfigurace pověření ve službě Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
