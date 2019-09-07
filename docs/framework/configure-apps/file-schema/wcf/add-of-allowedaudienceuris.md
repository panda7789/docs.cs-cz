---
title: <add> z <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
ms.openlocfilehash: e15cb2d3e525d39a321bbe9760ddb8d72b02fffa
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398358"
---
# <a name="add-of-allowedaudienceuris"></a><span data-ttu-id="e157b-102">\<add> of \<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="e157b-102">\<add> of \<allowedAudienceUris></span></span>
<span data-ttu-id="e157b-103">Přidá cílový identifikátor URI, pro který <xref:System.IdentityModel.Tokens.SamlSecurityToken> se pro token zabezpečení dá cílit, aby se dalo považovat za platný <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> v instanci.</span><span class="sxs-lookup"><span data-stu-id="e157b-103">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
<span data-ttu-id="e157b-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e157b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e157b-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e157b-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e157b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e157b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="e157b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e157b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="e157b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e157b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="e157b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="e157b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="e157b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedTokenAuthentication >** ](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="e157b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)</span></span>\
<span data-ttu-id="e157b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<allowedAudienceUris >** ](allowedaudienceuris.md)</span><span class="sxs-lookup"><span data-stu-id="e157b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowedAudienceUris>**](allowedaudienceuris.md)</span></span>\
<span data-ttu-id="e157b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="e157b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e157b-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e157b-113">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e157b-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e157b-114">Attributes and Elements</span></span>  
 <span data-ttu-id="e157b-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e157b-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e157b-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="e157b-116">Attributes</span></span>  
  
|<span data-ttu-id="e157b-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="e157b-117">Attribute</span></span>|<span data-ttu-id="e157b-118">Popis</span><span class="sxs-lookup"><span data-stu-id="e157b-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e157b-119">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="e157b-119">allowedAudienceUri</span></span>|<span data-ttu-id="e157b-120">Řetězec, který obsahuje cílový identifikátor URI, pro který <xref:System.IdentityModel.Tokens.SamlSecurityToken> je možné cílit na token zabezpečení, aby mohl být považován za platný <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> v instanci.</span><span class="sxs-lookup"><span data-stu-id="e157b-120">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e157b-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e157b-121">Child Elements</span></span>  
 <span data-ttu-id="e157b-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="e157b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e157b-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e157b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e157b-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="e157b-124">Element</span></span>|<span data-ttu-id="e157b-125">Popis</span><span class="sxs-lookup"><span data-stu-id="e157b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e157b-126">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="e157b-126">\<allowedAudienceUris></span></span>](allowedaudienceuris.md)|<span data-ttu-id="e157b-127">Představuje kolekci cílových identifikátorů URI, pro které <xref:System.IdentityModel.Tokens.SamlSecurityToken> může být token zabezpečení zaměřen na to, aby mohl být považován za platný <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> v instanci.</span><span class="sxs-lookup"><span data-stu-id="e157b-127">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e157b-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e157b-128">Remarks</span></span>  
 <span data-ttu-id="e157b-129">Tuto kolekci byste měli použít ve federované aplikaci, která využívá službu tokenů zabezpečení (STS), která vydává <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e157b-129">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="e157b-130">Pokud služba STS vydá token zabezpečení, může zadat identifikátor URI webových služeb, pro které je token zabezpečení určen přidáním <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> do tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e157b-130">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="e157b-131">To umožňuje <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> , aby webová služba příjemce ověřila, že vydaný token zabezpečení je určený pro tuto webovou službu, a to tak, že určí, že tato kontrola proběhne takto:</span><span class="sxs-lookup"><span data-stu-id="e157b-131">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="e157b-132">`audienceUriMode` Nastavte atribut<xref:System.IdentityModel.Selectors.AudienceUriMode.Always> na nebo .<xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly> `<issuedTokenAuthentication>`</span><span class="sxs-lookup"><span data-stu-id="e157b-132">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="e157b-133">Zadejte sadu platných identifikátorů URI přidáním identifikátorů URI do této kolekce.</span><span class="sxs-lookup"><span data-stu-id="e157b-133">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="e157b-134">Další informace naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="e157b-134">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="e157b-135">Další informace o použití tohoto konfiguračního prvku naleznete v tématu [How to: Konfigurace přihlašovacích údajů na](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)služba FS (Federation Service).</span><span class="sxs-lookup"><span data-stu-id="e157b-135">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e157b-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e157b-136">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="e157b-137">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="e157b-137">\<allowedAudienceUris></span></span>](allowedaudienceuris.md)
- [<span data-ttu-id="e157b-138">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="e157b-138">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="e157b-139">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e157b-139">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="e157b-140">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="e157b-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e157b-141">Postupy: Konfigurace přihlašovacích údajů na služba FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="e157b-141">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
