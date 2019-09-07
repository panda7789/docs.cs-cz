---
title: <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: ea2d4bb285047939992e9b191abc2dc896bdaa6a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398278"
---
# <a name="allowedaudienceuris"></a><span data-ttu-id="fdf52-101">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="fdf52-101">\<allowedAudienceUris></span></span>
<span data-ttu-id="fdf52-102">Představuje kolekci cílových identifikátorů URI, pro které <xref:System.IdentityModel.Tokens.SamlSecurityToken> může být token zabezpečení zaměřen na to, aby mohl být považován za platný <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> v instanci.</span><span class="sxs-lookup"><span data-stu-id="fdf52-102">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
<span data-ttu-id="fdf52-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fdf52-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fdf52-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="fdf52-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="fdf52-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fdf52-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="fdf52-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fdf52-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="fdf52-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fdf52-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="fdf52-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="fdf52-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="fdf52-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedTokenAuthentication >** ](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="fdf52-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)</span></span>\
<span data-ttu-id="fdf52-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<allowedAudienceUris >**</span><span class="sxs-lookup"><span data-stu-id="fdf52-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowedAudienceUris>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdf52-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fdf52-111">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fdf52-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fdf52-112">Attributes and Elements</span></span>  
 <span data-ttu-id="fdf52-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fdf52-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fdf52-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="fdf52-114">Attributes</span></span>  
 <span data-ttu-id="fdf52-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="fdf52-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fdf52-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fdf52-116">Child Elements</span></span>  
  
|<span data-ttu-id="fdf52-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="fdf52-117">Element</span></span>|<span data-ttu-id="fdf52-118">Popis</span><span class="sxs-lookup"><span data-stu-id="fdf52-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fdf52-119">\<add></span><span class="sxs-lookup"><span data-stu-id="fdf52-119">\<add></span></span>](add-of-allowedaudienceuris.md)|<span data-ttu-id="fdf52-120">Přidá cílový identifikátor URI, pro který <xref:System.IdentityModel.Tokens.SamlSecurityToken> se pro token zabezpečení dá cílit, aby se dalo považovat za platný <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> v instanci.</span><span class="sxs-lookup"><span data-stu-id="fdf52-120">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fdf52-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fdf52-121">Parent Elements</span></span>  
  
|<span data-ttu-id="fdf52-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="fdf52-122">Element</span></span>|<span data-ttu-id="fdf52-123">Popis</span><span class="sxs-lookup"><span data-stu-id="fdf52-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fdf52-124">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="fdf52-124">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="fdf52-125">Určuje token vydaný jako pověření služby.</span><span class="sxs-lookup"><span data-stu-id="fdf52-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdf52-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fdf52-126">Remarks</span></span>  
 <span data-ttu-id="fdf52-127">Tuto kolekci byste měli použít ve federované aplikaci, která využívá službu tokenů zabezpečení (STS), která vydává <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="fdf52-127">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="fdf52-128">Pokud služba STS vydá token zabezpečení, může zadat identifikátor URI webových služeb, pro které je token zabezpečení určen přidáním <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> do tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="fdf52-128">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="fdf52-129">To umožňuje <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> , aby webová služba příjemce ověřila, že vydaný token zabezpečení je určený pro tuto webovou službu, a to tak, že určí, že tato kontrola proběhne takto:</span><span class="sxs-lookup"><span data-stu-id="fdf52-129">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="fdf52-130">`audienceUriMode` Nastavte atribut<xref:System.IdentityModel.Selectors.AudienceUriMode.Always> na nebo .<xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly> `<issuedTokenAuthentication>`</span><span class="sxs-lookup"><span data-stu-id="fdf52-130">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="fdf52-131">Zadejte sadu platných identifikátorů URI přidáním identifikátorů URI do této kolekce.</span><span class="sxs-lookup"><span data-stu-id="fdf52-131">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="fdf52-132">Další informace naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="fdf52-132">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="fdf52-133">Další informace o použití tohoto konfiguračního prvku naleznete v tématu [How to: Konfigurace přihlašovacích údajů na](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)služba FS (Federation Service).</span><span class="sxs-lookup"><span data-stu-id="fdf52-133">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdf52-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fdf52-134">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="fdf52-135">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="fdf52-135">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="fdf52-136">\<add></span><span class="sxs-lookup"><span data-stu-id="fdf52-136">\<add></span></span>](add-of-allowedaudienceuris.md)
- [<span data-ttu-id="fdf52-137">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="fdf52-137">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="fdf52-138">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="fdf52-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="fdf52-139">Postupy: Konfigurace přihlašovacích údajů na služba FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="fdf52-139">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
