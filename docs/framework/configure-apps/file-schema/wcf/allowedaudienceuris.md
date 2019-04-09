---
title: <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: f758fc8e0934f56f9593246497d8aba5084c4a79
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143348"
---
# <a name="allowedaudienceuris"></a><span data-ttu-id="31010-101">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="31010-101">\<allowedAudienceUris></span></span>
<span data-ttu-id="31010-102">Představuje sadu cílových identifikátorů URI, pro kterou <xref:System.IdentityModel.Tokens.SamlSecurityToken> token zabezpečení může služba je určená pro aby mohl být uznán platnou podle <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span><span class="sxs-lookup"><span data-stu-id="31010-102">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="31010-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="31010-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="31010-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="31010-104">\<behaviors></span></span>  
<span data-ttu-id="31010-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="31010-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="31010-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="31010-106">\<behavior></span></span>  
<span data-ttu-id="31010-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="31010-107">\<serviceCredentials></span></span>  
<span data-ttu-id="31010-108">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="31010-108">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="31010-109">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="31010-109">\<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31010-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31010-110">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31010-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="31010-111">Attributes and Elements</span></span>  
 <span data-ttu-id="31010-112">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="31010-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31010-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="31010-113">Attributes</span></span>  
 <span data-ttu-id="31010-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="31010-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="31010-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="31010-115">Child Elements</span></span>  
  
|<span data-ttu-id="31010-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="31010-116">Element</span></span>|<span data-ttu-id="31010-117">Popis</span><span class="sxs-lookup"><span data-stu-id="31010-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31010-118">\<add></span><span class="sxs-lookup"><span data-stu-id="31010-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)|<span data-ttu-id="31010-119">Přidá cílový identifikátor Uri pro kterou <xref:System.IdentityModel.Tokens.SamlSecurityToken> token zabezpečení může služba je určená pro aby mohl být uznán platnou podle <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span><span class="sxs-lookup"><span data-stu-id="31010-119">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="31010-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="31010-120">Parent Elements</span></span>  
  
|<span data-ttu-id="31010-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="31010-121">Element</span></span>|<span data-ttu-id="31010-122">Popis</span><span class="sxs-lookup"><span data-stu-id="31010-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31010-123">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="31010-123">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="31010-124">Určuje token vydaný jako pověření služby.</span><span class="sxs-lookup"><span data-stu-id="31010-124">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31010-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="31010-125">Remarks</span></span>  
 <span data-ttu-id="31010-126">Tato kolekce měli použít ve federované aplikaci, která využívá služby tokenů zabezpečení (STS), která vydává <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="31010-126">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="31010-127">Když služba tokenů zabezpečení vydá token zabezpečení, můžete určit identifikátor URI webové služby, pro které je určen token zabezpečení tak, že přidáte <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> do tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="31010-127">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="31010-128">Umožňuje <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> pro příjemce webovou službu, chcete-li ověřit, že token vydaný zabezpečení je určený pro tuto webovou službu tak, že určíte, že tato kontrola se stane při následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="31010-128">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
-   <span data-ttu-id="31010-129">Nastavte `audienceUriMode` atribut `<issuedTokenAuthentication>` k <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> nebo <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="31010-129">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
-   <span data-ttu-id="31010-130">Zadejte sadu platné identifikátory URI, tak, že přidáte identifikátory URI do této kolekce.</span><span class="sxs-lookup"><span data-stu-id="31010-130">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="31010-131">Další informace naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="31010-131">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="31010-132">Další informace o použití tento prvek konfigurace, najdete v části [jak: Konfigurace pověření ve službě Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="31010-132">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31010-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="31010-133">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="31010-134">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="31010-134">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="31010-135">\<add></span><span class="sxs-lookup"><span data-stu-id="31010-135">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)
- [<span data-ttu-id="31010-136">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="31010-136">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="31010-137">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="31010-137">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="31010-138">Postupy: Konfigurace pověření ve službě Federation Service</span><span class="sxs-lookup"><span data-stu-id="31010-138">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
