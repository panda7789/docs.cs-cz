---
title: '&lt;add&gt; – &lt;allowedAudienceUris&gt;'
ms.date: 03/30/2017
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
ms.openlocfilehash: cfd18d6af5248e680b9520069fb34c412ee12b3f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746625"
---
# <a name="ltaddgt-of-ltallowedaudienceurisgt"></a>&lt;add&gt; – &lt;allowedAudienceUris&gt;
Přidá cílový identifikátor Uri pro kterou <xref:System.IdentityModel.Tokens.SamlSecurityToken> token zabezpečení je možné cílit pro Chcete-li být považován za platný podle <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors >  
\<chování >  
\<– serviceCredentials >  
\<issuedTokenAuthentication >  
\<allowedAudienceUris >  
\<Přidat > elementu pro \<allowedAudienceUris >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<allowedAudienceUris>   
   <add allowedAudienceUri="String"/>  
</allowedAudienceUris>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|allowedAudienceUri|Řetězec, který obsahuje cílový identifikátor Uri pro kterou <xref:System.IdentityModel.Tokens.SamlSecurityToken> token zabezpečení je možné cílit pro Chcete-li být považován za platný podle <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<allowedAudienceUris >](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)|Představuje kolekci cíle identifikátory URI, pro kterou <xref:System.IdentityModel.Tokens.SamlSecurityToken> token zabezpečení je možné cílit pro Chcete-li být považován za platný podle <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.|  
  
## <a name="remarks"></a>Poznámky  
 Ve federovaných aplikací, který využívá službu tokenů zabezpečení (STS), vydá byste měli používat tuto kolekci <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokeny zabezpečení. Když služba tokenů zabezpečení vydá token zabezpečení, může však určovat identifikátor URI webové služby, pro které je určen přidáním token zabezpečení <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> do tokenu zabezpečení. Umožňuje <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> pro příjemce webovou službu k ověření, že token zabezpečení vydané slouží k této webové služby tak, že zadáte, aby tato kontrola má proběhnout provedením následujících akcí:  
  
-   Nastavte `audienceUriMode` atribut `<issuedTokenAuthentication>` k <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> nebo <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.  
  
-   Zadejte sadu platné identifikátory URI přidáním identifikátory URI k této kolekci.  
  
 Další informace naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Další informace o použití tohoto elementu konfigurace najdete v tématu [postupy: Konfigurace pověření ve službě Federation](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>  
 [\<allowedAudienceUris >](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)  
 [\<issuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Postupy: Konfigurace přihlašovacích údajů ve službě Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
