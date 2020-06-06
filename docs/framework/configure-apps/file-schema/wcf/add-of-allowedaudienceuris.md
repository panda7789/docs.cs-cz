---
title: <add> z <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
ms.openlocfilehash: e15cb2d3e525d39a321bbe9760ddb8d72b02fffa
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398358"
---
# <a name="add-of-allowedaudienceuris"></a><span data-ttu-id="8d5d8-102">\<add> z \<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="8d5d8-102">\<add> of \<allowedAudienceUris></span></span>
<span data-ttu-id="8d5d8-103">Přidá cílový identifikátor URI, pro který se pro <xref:System.IdentityModel.Tokens.SamlSecurityToken> token zabezpečení dá cílit, aby se dalo považovat za platný v <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instanci.</span><span class="sxs-lookup"><span data-stu-id="8d5d8-103">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowedAudienceUris>**](allowedaudienceuris.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="8d5d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d5d8-104">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d5d8-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8d5d8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8d5d8-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8d5d8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d5d8-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="8d5d8-107">Attributes</span></span>  
  
|<span data-ttu-id="8d5d8-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="8d5d8-108">Attribute</span></span>|<span data-ttu-id="8d5d8-109">Popis</span><span class="sxs-lookup"><span data-stu-id="8d5d8-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8d5d8-110">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="8d5d8-110">allowedAudienceUri</span></span>|<span data-ttu-id="8d5d8-111">Řetězec, který obsahuje cílový identifikátor URI, pro který je <xref:System.IdentityModel.Tokens.SamlSecurityToken> možné cílit na token zabezpečení, aby mohl být považován za platný v <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instanci.</span><span class="sxs-lookup"><span data-stu-id="8d5d8-111">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d5d8-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8d5d8-112">Child Elements</span></span>  
 <span data-ttu-id="8d5d8-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="8d5d8-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8d5d8-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8d5d8-114">Parent Elements</span></span>  
  
|<span data-ttu-id="8d5d8-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="8d5d8-115">Element</span></span>|<span data-ttu-id="8d5d8-116">Description</span><span class="sxs-lookup"><span data-stu-id="8d5d8-116">Description</span></span>|  
|-------------|-----------------|  
|[\<allowedAudienceUris>](allowedaudienceuris.md)|<span data-ttu-id="8d5d8-117">Představuje kolekci cílových identifikátorů URI, pro které <xref:System.IdentityModel.Tokens.SamlSecurityToken> může být token zabezpečení zaměřen na to, aby mohl být považován za platný v <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instanci.</span><span class="sxs-lookup"><span data-stu-id="8d5d8-117">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d5d8-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d5d8-118">Remarks</span></span>  
 <span data-ttu-id="8d5d8-119">Tuto kolekci byste měli použít ve federované aplikaci, která využívá službu tokenů zabezpečení (STS), která vydává <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8d5d8-119">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="8d5d8-120">Pokud služba STS vydá token zabezpečení, může zadat identifikátor URI webových služeb, pro které je token zabezpečení určen přidáním <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> do tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8d5d8-120">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="8d5d8-121">To umožňuje, aby <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> Webová služba příjemce ověřila, že vydaný token zabezpečení je určený pro tuto webovou službu, a to tak, že určí, že tato kontrola proběhne takto:</span><span class="sxs-lookup"><span data-stu-id="8d5d8-121">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="8d5d8-122">Nastavte `audienceUriMode` atribut `<issuedTokenAuthentication>` na <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> nebo <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly> .</span><span class="sxs-lookup"><span data-stu-id="8d5d8-122">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="8d5d8-123">Zadejte sadu platných identifikátorů URI přidáním identifikátorů URI do této kolekce.</span><span class="sxs-lookup"><span data-stu-id="8d5d8-123">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="8d5d8-124">Další informace naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="8d5d8-124">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="8d5d8-125">Další informace o použití tohoto konfiguračního prvku naleznete v tématu [How to: Configure a Credentials on a služba FS (Federation Service)](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="8d5d8-125">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d5d8-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d5d8-126">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [\<allowedAudienceUris>](allowedaudienceuris.md)
- [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="8d5d8-127">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="8d5d8-127">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="8d5d8-128">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="8d5d8-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8d5d8-129">Postupy: Konfigurace pověření ve službě Federation Service</span><span class="sxs-lookup"><span data-stu-id="8d5d8-129">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
