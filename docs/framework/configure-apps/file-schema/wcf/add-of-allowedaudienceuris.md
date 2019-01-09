---
title: '&lt;add&gt; – &lt;allowedAudienceUris&gt;'
ms.date: 03/30/2017
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
ms.openlocfilehash: 5428b41cadebbb38716789fa0e275c244fe74311
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146226"
---
# <a name="ltaddgt-of-ltallowedaudienceurisgt"></a><span data-ttu-id="fe52d-102">&lt;add&gt; – &lt;allowedAudienceUris&gt;</span><span class="sxs-lookup"><span data-stu-id="fe52d-102">&lt;add&gt; of &lt;allowedAudienceUris&gt;</span></span>
<span data-ttu-id="fe52d-103">Přidá cílový identifikátor Uri pro kterou <xref:System.IdentityModel.Tokens.SamlSecurityToken> token zabezpečení může služba je určená pro aby mohl být uznán platnou podle <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span><span class="sxs-lookup"><span data-stu-id="fe52d-103">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="fe52d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fe52d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fe52d-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="fe52d-105">\<behaviors></span></span>  
<span data-ttu-id="fe52d-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="fe52d-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="fe52d-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="fe52d-107">\<behavior></span></span>  
<span data-ttu-id="fe52d-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="fe52d-108">\<serviceCredentials></span></span>  
<span data-ttu-id="fe52d-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="fe52d-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="fe52d-110">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="fe52d-110">\<allowedAudienceUris></span></span>  
<span data-ttu-id="fe52d-111">\<Přidat > – element pro \<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="fe52d-111">\<add> element for \<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe52d-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe52d-112">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe52d-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fe52d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="fe52d-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fe52d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe52d-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="fe52d-115">Attributes</span></span>  
  
|<span data-ttu-id="fe52d-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="fe52d-116">Attribute</span></span>|<span data-ttu-id="fe52d-117">Popis</span><span class="sxs-lookup"><span data-stu-id="fe52d-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fe52d-118">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="fe52d-118">allowedAudienceUri</span></span>|<span data-ttu-id="fe52d-119">Řetězec, který obsahuje cílový identifikátor Uri pro kterou <xref:System.IdentityModel.Tokens.SamlSecurityToken> token zabezpečení může služba je určená pro aby mohl být uznán platnou podle <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span><span class="sxs-lookup"><span data-stu-id="fe52d-119">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe52d-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fe52d-120">Child Elements</span></span>  
 <span data-ttu-id="fe52d-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="fe52d-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fe52d-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fe52d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="fe52d-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="fe52d-123">Element</span></span>|<span data-ttu-id="fe52d-124">Popis</span><span class="sxs-lookup"><span data-stu-id="fe52d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe52d-125">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="fe52d-125">\<allowedAudienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)|<span data-ttu-id="fe52d-126">Představuje sadu cílových identifikátorů URI, pro kterou <xref:System.IdentityModel.Tokens.SamlSecurityToken> token zabezpečení může služba je určená pro aby mohl být uznán platnou podle <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span><span class="sxs-lookup"><span data-stu-id="fe52d-126">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe52d-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe52d-127">Remarks</span></span>  
 <span data-ttu-id="fe52d-128">Tato kolekce měli použít ve federované aplikaci, která využívá služby tokenů zabezpečení (STS), která vydává <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="fe52d-128">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="fe52d-129">Když služba tokenů zabezpečení vydá token zabezpečení, můžete určit identifikátor URI webové služby, pro které je určen token zabezpečení tak, že přidáte <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> do tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="fe52d-129">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="fe52d-130">Umožňuje <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> pro příjemce webovou službu, chcete-li ověřit, že token vydaný zabezpečení je určený pro tuto webovou službu tak, že určíte, že tato kontrola se stane při následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="fe52d-130">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
-   <span data-ttu-id="fe52d-131">Nastavte `audienceUriMode` atribut `<issuedTokenAuthentication>` k <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> nebo <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="fe52d-131">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
-   <span data-ttu-id="fe52d-132">Zadejte sadu platné identifikátory URI, tak, že přidáte identifikátory URI do této kolekce.</span><span class="sxs-lookup"><span data-stu-id="fe52d-132">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="fe52d-133">Další informace naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="fe52d-133">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="fe52d-134">Další informace o použití tento prvek konfigurace, najdete v části [jak: Konfigurace pověření ve službě Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="fe52d-134">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe52d-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe52d-135">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>  
 [<span data-ttu-id="fe52d-136">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="fe52d-136">\<allowedAudienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)  
 [<span data-ttu-id="fe52d-137">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="fe52d-137">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [<span data-ttu-id="fe52d-138">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="fe52d-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="fe52d-139">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="fe52d-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="fe52d-140">Postupy: Konfigurace pověření ve službě Federation Service</span><span class="sxs-lookup"><span data-stu-id="fe52d-140">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
