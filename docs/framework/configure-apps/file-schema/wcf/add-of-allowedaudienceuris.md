---
title: <add> z <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
ms.openlocfilehash: 64f0dd5c97ddfcd2fffd8ff4820d02af8c1ced54
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926882"
---
# <a name="add-of-allowedaudienceuris"></a><span data-ttu-id="7e11c-102">\<add> of \<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="7e11c-102">\<add> of \<allowedAudienceUris></span></span>
<span data-ttu-id="7e11c-103">Přidá cílový identifikátor URI, pro který <xref:System.IdentityModel.Tokens.SamlSecurityToken> se pro token zabezpečení dá cílit, aby se dalo považovat za platný <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> v instanci.</span><span class="sxs-lookup"><span data-stu-id="7e11c-103">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="7e11c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7e11c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7e11c-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="7e11c-105">\<behaviors></span></span>  
<span data-ttu-id="7e11c-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="7e11c-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7e11c-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="7e11c-107">\<behavior></span></span>  
<span data-ttu-id="7e11c-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="7e11c-108">\<serviceCredentials></span></span>  
<span data-ttu-id="7e11c-109">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="7e11c-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="7e11c-110">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="7e11c-110">\<allowedAudienceUris></span></span>  
<span data-ttu-id="7e11c-111">\<Přidat > element pro \<> AllowedAudienceUris</span><span class="sxs-lookup"><span data-stu-id="7e11c-111">\<add> element for \<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e11c-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e11c-112">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e11c-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7e11c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="7e11c-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7e11c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e11c-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="7e11c-115">Attributes</span></span>  
  
|<span data-ttu-id="7e11c-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="7e11c-116">Attribute</span></span>|<span data-ttu-id="7e11c-117">Popis</span><span class="sxs-lookup"><span data-stu-id="7e11c-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e11c-118">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="7e11c-118">allowedAudienceUri</span></span>|<span data-ttu-id="7e11c-119">Řetězec, který obsahuje cílový identifikátor URI, pro který <xref:System.IdentityModel.Tokens.SamlSecurityToken> je možné cílit na token zabezpečení, aby mohl být považován za platný <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> v instanci.</span><span class="sxs-lookup"><span data-stu-id="7e11c-119">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e11c-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7e11c-120">Child Elements</span></span>  
 <span data-ttu-id="7e11c-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="7e11c-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7e11c-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7e11c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7e11c-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="7e11c-123">Element</span></span>|<span data-ttu-id="7e11c-124">Popis</span><span class="sxs-lookup"><span data-stu-id="7e11c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e11c-125">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="7e11c-125">\<allowedAudienceUris></span></span>](allowedaudienceuris.md)|<span data-ttu-id="7e11c-126">Představuje kolekci cílových identifikátorů URI, pro které <xref:System.IdentityModel.Tokens.SamlSecurityToken> může být token zabezpečení zaměřen na to, aby mohl být považován za platný <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> v instanci.</span><span class="sxs-lookup"><span data-stu-id="7e11c-126">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e11c-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e11c-127">Remarks</span></span>  
 <span data-ttu-id="7e11c-128">Tuto kolekci byste měli použít ve federované aplikaci, která využívá službu tokenů zabezpečení (STS), která vydává <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7e11c-128">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="7e11c-129">Pokud služba STS vydá token zabezpečení, může zadat identifikátor URI webových služeb, pro které je token zabezpečení určen přidáním <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> do tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7e11c-129">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="7e11c-130">To umožňuje <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> , aby webová služba příjemce ověřila, že vydaný token zabezpečení je určený pro tuto webovou službu, a to tak, že určí, že tato kontrola proběhne takto:</span><span class="sxs-lookup"><span data-stu-id="7e11c-130">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="7e11c-131">`audienceUriMode` Nastavte atribut<xref:System.IdentityModel.Selectors.AudienceUriMode.Always> na nebo .<xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly> `<issuedTokenAuthentication>`</span><span class="sxs-lookup"><span data-stu-id="7e11c-131">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="7e11c-132">Zadejte sadu platných identifikátorů URI přidáním identifikátorů URI do této kolekce.</span><span class="sxs-lookup"><span data-stu-id="7e11c-132">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="7e11c-133">Další informace naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="7e11c-133">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="7e11c-134">Další informace o použití tohoto konfiguračního prvku naleznete v tématu [How to: Konfigurace přihlašovacích údajů na](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)služba FS (Federation Service).</span><span class="sxs-lookup"><span data-stu-id="7e11c-134">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e11c-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e11c-135">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="7e11c-136">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="7e11c-136">\<allowedAudienceUris></span></span>](allowedaudienceuris.md)
- [<span data-ttu-id="7e11c-137">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="7e11c-137">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="7e11c-138">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7e11c-138">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="7e11c-139">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="7e11c-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7e11c-140">Postupy: Konfigurace přihlašovacích údajů na služba FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="7e11c-140">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
