---
title: <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: 03888600a89d72f5216c8c8cac21c9da96879ba8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919966"
---
# <a name="allowedaudienceuris"></a><span data-ttu-id="227cd-101">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="227cd-101">\<allowedAudienceUris></span></span>
<span data-ttu-id="227cd-102">Představuje kolekci cílových identifikátorů URI, pro které <xref:System.IdentityModel.Tokens.SamlSecurityToken> může být token zabezpečení zaměřen na to, aby mohl být považován za platný <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> v instanci.</span><span class="sxs-lookup"><span data-stu-id="227cd-102">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="227cd-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="227cd-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="227cd-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="227cd-104">\<behaviors></span></span>  
<span data-ttu-id="227cd-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="227cd-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="227cd-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="227cd-106">\<behavior></span></span>  
<span data-ttu-id="227cd-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="227cd-107">\<serviceCredentials></span></span>  
<span data-ttu-id="227cd-108">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="227cd-108">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="227cd-109">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="227cd-109">\<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="227cd-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="227cd-110">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="227cd-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="227cd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="227cd-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="227cd-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="227cd-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="227cd-113">Attributes</span></span>  
 <span data-ttu-id="227cd-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="227cd-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="227cd-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="227cd-115">Child Elements</span></span>  
  
|<span data-ttu-id="227cd-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="227cd-116">Element</span></span>|<span data-ttu-id="227cd-117">Popis</span><span class="sxs-lookup"><span data-stu-id="227cd-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="227cd-118">\<add></span><span class="sxs-lookup"><span data-stu-id="227cd-118">\<add></span></span>](add-of-allowedaudienceuris.md)|<span data-ttu-id="227cd-119">Přidá cílový identifikátor URI, pro který <xref:System.IdentityModel.Tokens.SamlSecurityToken> se pro token zabezpečení dá cílit, aby se dalo považovat za platný <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> v instanci.</span><span class="sxs-lookup"><span data-stu-id="227cd-119">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="227cd-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="227cd-120">Parent Elements</span></span>  
  
|<span data-ttu-id="227cd-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="227cd-121">Element</span></span>|<span data-ttu-id="227cd-122">Popis</span><span class="sxs-lookup"><span data-stu-id="227cd-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="227cd-123">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="227cd-123">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="227cd-124">Určuje token vydaný jako pověření služby.</span><span class="sxs-lookup"><span data-stu-id="227cd-124">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="227cd-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="227cd-125">Remarks</span></span>  
 <span data-ttu-id="227cd-126">Tuto kolekci byste měli použít ve federované aplikaci, která využívá službu tokenů zabezpečení (STS), která vydává <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="227cd-126">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="227cd-127">Pokud služba STS vydá token zabezpečení, může zadat identifikátor URI webových služeb, pro které je token zabezpečení určen přidáním <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> do tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="227cd-127">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="227cd-128">To umožňuje <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> , aby webová služba příjemce ověřila, že vydaný token zabezpečení je určený pro tuto webovou službu, a to tak, že určí, že tato kontrola proběhne takto:</span><span class="sxs-lookup"><span data-stu-id="227cd-128">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="227cd-129">`audienceUriMode` Nastavte atribut<xref:System.IdentityModel.Selectors.AudienceUriMode.Always> na nebo .<xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly> `<issuedTokenAuthentication>`</span><span class="sxs-lookup"><span data-stu-id="227cd-129">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="227cd-130">Zadejte sadu platných identifikátorů URI přidáním identifikátorů URI do této kolekce.</span><span class="sxs-lookup"><span data-stu-id="227cd-130">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="227cd-131">Další informace naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="227cd-131">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="227cd-132">Další informace o použití tohoto konfiguračního prvku naleznete v tématu [How to: Konfigurace přihlašovacích údajů na](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)služba FS (Federation Service).</span><span class="sxs-lookup"><span data-stu-id="227cd-132">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="227cd-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="227cd-133">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="227cd-134">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="227cd-134">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="227cd-135">\<add></span><span class="sxs-lookup"><span data-stu-id="227cd-135">\<add></span></span>](add-of-allowedaudienceuris.md)
- [<span data-ttu-id="227cd-136">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="227cd-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="227cd-137">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="227cd-137">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="227cd-138">Postupy: Konfigurace přihlašovacích údajů na služba FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="227cd-138">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
