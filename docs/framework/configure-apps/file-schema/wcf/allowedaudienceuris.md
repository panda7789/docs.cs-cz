---
title: <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: ea2d4bb285047939992e9b191abc2dc896bdaa6a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398278"
---
# \<allowedAudienceUris>
<span data-ttu-id="c6845-101">Představuje kolekci cílových identifikátorů URI, pro které <xref:System.IdentityModel.Tokens.SamlSecurityToken> může být token zabezpečení zaměřen na to, aby mohl být považován za platný v <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instanci.</span><span class="sxs-lookup"><span data-stu-id="c6845-101">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowedAudienceUris>**  
  
## <a name="syntax"></a><span data-ttu-id="c6845-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6845-102">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6845-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c6845-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c6845-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c6845-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6845-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="c6845-105">Attributes</span></span>  
 <span data-ttu-id="c6845-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="c6845-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c6845-107">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c6845-107">Child Elements</span></span>  
  
|<span data-ttu-id="c6845-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="c6845-108">Element</span></span>|<span data-ttu-id="c6845-109">Description</span><span class="sxs-lookup"><span data-stu-id="c6845-109">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-allowedaudienceuris.md)|<span data-ttu-id="c6845-110">Přidá cílový identifikátor URI, pro který se pro <xref:System.IdentityModel.Tokens.SamlSecurityToken> token zabezpečení dá cílit, aby se dalo považovat za platný v <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instanci.</span><span class="sxs-lookup"><span data-stu-id="c6845-110">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c6845-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c6845-111">Parent Elements</span></span>  
  
|<span data-ttu-id="c6845-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="c6845-112">Element</span></span>|<span data-ttu-id="c6845-113">Description</span><span class="sxs-lookup"><span data-stu-id="c6845-113">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="c6845-114">Určuje token vydaný jako pověření služby.</span><span class="sxs-lookup"><span data-stu-id="c6845-114">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6845-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6845-115">Remarks</span></span>  
 <span data-ttu-id="c6845-116">Tuto kolekci byste měli použít ve federované aplikaci, která využívá službu tokenů zabezpečení (STS), která vydává <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c6845-116">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="c6845-117">Pokud služba STS vydá token zabezpečení, může zadat identifikátor URI webových služeb, pro které je token zabezpečení určen přidáním <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> do tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c6845-117">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="c6845-118">To umožňuje, aby <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> Webová služba příjemce ověřila, že vydaný token zabezpečení je určený pro tuto webovou službu, a to tak, že určí, že tato kontrola proběhne takto:</span><span class="sxs-lookup"><span data-stu-id="c6845-118">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="c6845-119">Nastavte `audienceUriMode` atribut `<issuedTokenAuthentication>` na <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> nebo <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly> .</span><span class="sxs-lookup"><span data-stu-id="c6845-119">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="c6845-120">Zadejte sadu platných identifikátorů URI přidáním identifikátorů URI do této kolekce.</span><span class="sxs-lookup"><span data-stu-id="c6845-120">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="c6845-121">Další informace naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="c6845-121">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="c6845-122">Další informace o použití tohoto konfiguračního prvku naleznete v tématu [How to: Configure a Credentials on a služba FS (Federation Service)](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="c6845-122">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6845-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6845-123">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)
- [\<add>](add-of-allowedaudienceuris.md)
- [<span data-ttu-id="c6845-124">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c6845-124">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="c6845-125">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="c6845-125">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c6845-126">Postupy: Konfigurace pověření ve službě Federation Service</span><span class="sxs-lookup"><span data-stu-id="c6845-126">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
