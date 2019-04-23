---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 5c20baecf3e9fe83385c986e3fb58f0c03eeeb47
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224192"
---
# <a name="knowncertificates"></a>\<knownCertificates>
Představuje kolekci certifikátů X.509, které jsou k dispozici k ověřování pověření zabezpečení vydané z tokenu služby zabezpečení (STS).  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors>  
\<chování >  
\<serviceCredentials>  
\<issuedTokenAuthentication>  
\<knownCertificates>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)|Přidá certifikát X.509 do kolekce.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|Určuje token vydaný jako pověření služby.|  
  
## <a name="remarks"></a>Poznámky  
 Vydaný token scénář má tři fáze. V první fázi se klient pokouší o přístup ke službě označuje *služby tokenů zabezpečení*. Služba tokenů zabezpečení pak ověří klienta a následně vydá klienta token, obvykle token zabezpečení kontrolní výrazy SAML (Markup Language). Klient pak vrátí ke službě s tokenem. Služba zkontroluje token pro data, která umožňuje službě ověření tokenu a proto klienta. K ověření tokenu, certifikát používá služba tokenů zabezpečení musí být známo ke službě.  
  
 [ \<IssuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element je úložiště pro tyto certifikáty služba tokenů zabezpečení. Chcete-li přidat certifikáty použít [ \<knownCertificates > element](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). Vložit [ \<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) pro každý certifikát, jak je znázorněno v následujícím příkladu.  
  
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
  
 Podmínky pro klienta ověřit federované služby, jakož i další informace o použití tento prvek konfigurace najdete v tématu [jak: Konfigurace pověření ve službě Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md). Další informace o federovaných scénářích najdete v tématu [federace a vydané tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Příklad, který ukazuje, jak k naplnění kolekce v konfiguraci, najdete v části [ \<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)
- [\<issuedTokenAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)
- [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Postupy: Konfigurace pověření ve službě Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)
- [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
