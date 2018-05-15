---
title: '&lt;allowedAudienceUris&gt;'
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: b7a4ae230e9b8788d9ac23147a3fcf21637dadaf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltallowedaudienceurisgt"></a><span data-ttu-id="7c51f-102">&lt;allowedAudienceUris&gt;</span><span class="sxs-lookup"><span data-stu-id="7c51f-102">&lt;allowedAudienceUris&gt;</span></span>
<span data-ttu-id="7c51f-103">Představuje kolekci cíle identifikátory URI, pro kterou <xref:System.IdentityModel.Tokens.SamlSecurityToken> token zabezpečení je možné cílit pro Chcete-li být považován za platný podle <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span><span class="sxs-lookup"><span data-stu-id="7c51f-103">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="7c51f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7c51f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7c51f-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="7c51f-105">\<behaviors></span></span>  
<span data-ttu-id="7c51f-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7c51f-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7c51f-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="7c51f-107">\<behavior></span></span>  
<span data-ttu-id="7c51f-108">\<– serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="7c51f-108">\<serviceCredentials></span></span>  
<span data-ttu-id="7c51f-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="7c51f-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="7c51f-110">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="7c51f-110">\<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c51f-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c51f-111">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>  
      <add allowedAudienceUri="String"/>  
</allowedAudienceUris>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c51f-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7c51f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7c51f-113">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7c51f-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c51f-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="7c51f-114">Attributes</span></span>  
 <span data-ttu-id="7c51f-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="7c51f-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7c51f-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7c51f-116">Child Elements</span></span>  
  
|<span data-ttu-id="7c51f-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="7c51f-117">Element</span></span>|<span data-ttu-id="7c51f-118">Popis</span><span class="sxs-lookup"><span data-stu-id="7c51f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c51f-119">\<add></span><span class="sxs-lookup"><span data-stu-id="7c51f-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)|<span data-ttu-id="7c51f-120">Přidá cílový identifikátor Uri pro kterou <xref:System.IdentityModel.Tokens.SamlSecurityToken> token zabezpečení je možné cílit pro Chcete-li být považován za platný podle <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span><span class="sxs-lookup"><span data-stu-id="7c51f-120">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7c51f-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7c51f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7c51f-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="7c51f-122">Element</span></span>|<span data-ttu-id="7c51f-123">Popis</span><span class="sxs-lookup"><span data-stu-id="7c51f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c51f-124">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="7c51f-124">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="7c51f-125">Určuje tokenem vydaným jako přihlašovací údaje služby.</span><span class="sxs-lookup"><span data-stu-id="7c51f-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c51f-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7c51f-126">Remarks</span></span>  
 <span data-ttu-id="7c51f-127">Ve federovaných aplikací, který využívá službu tokenů zabezpečení (STS), vydá byste měli používat tuto kolekci <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7c51f-127">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="7c51f-128">Když služba tokenů zabezpečení vydá token zabezpečení, může však určovat identifikátor URI webové služby, pro které je určen přidáním token zabezpečení <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> do tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7c51f-128">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="7c51f-129">Umožňuje <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> pro příjemce webovou službu k ověření, že token zabezpečení vydané slouží k této webové služby tak, že zadáte, aby tato kontrola má proběhnout provedením následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="7c51f-129">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
-   <span data-ttu-id="7c51f-130">Nastavte `audienceUriMode` atribut `<issuedTokenAuthentication>` k <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> nebo <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="7c51f-130">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
-   <span data-ttu-id="7c51f-131">Zadejte sadu platné identifikátory URI přidáním identifikátory URI k této kolekci.</span><span class="sxs-lookup"><span data-stu-id="7c51f-131">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="7c51f-132">Další informace naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="7c51f-132">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="7c51f-133">Další informace o použití tohoto elementu konfigurace najdete v tématu [postupy: Konfigurace pověření ve službě Federation](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="7c51f-133">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c51f-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c51f-134">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>  
 [<span data-ttu-id="7c51f-135">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="7c51f-135">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [<span data-ttu-id="7c51f-136">\<add></span><span class="sxs-lookup"><span data-stu-id="7c51f-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)  
 [<span data-ttu-id="7c51f-137">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7c51f-137">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="7c51f-138">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="7c51f-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="7c51f-139">Postupy: Konfigurace přihlašovacích údajů ve službě Federation Service</span><span class="sxs-lookup"><span data-stu-id="7c51f-139">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
