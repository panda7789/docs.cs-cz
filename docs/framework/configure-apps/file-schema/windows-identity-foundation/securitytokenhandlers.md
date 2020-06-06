---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: 017309436660991c69da569e9cc4219e842ecaa3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251877"
---
# \<securityTokenHandlers>
<span data-ttu-id="dc2d4-101">Určuje kolekci obslužných rutin tokenů zabezpečení, které jsou registrovány u koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="dc2d4-101">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlers>**  
  
## <a name="syntax"></a><span data-ttu-id="dc2d4-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc2d4-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc2d4-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dc2d4-103">Attributes and Elements</span></span>  
 <span data-ttu-id="dc2d4-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dc2d4-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc2d4-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="dc2d4-105">Attributes</span></span>  
  
|<span data-ttu-id="dc2d4-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="dc2d4-106">Attribute</span></span>|<span data-ttu-id="dc2d4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="dc2d4-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dc2d4-108">name</span><span class="sxs-lookup"><span data-stu-id="dc2d4-108">name</span></span>|<span data-ttu-id="dc2d4-109">Určuje název kolekce obslužných rutin tokenu.</span><span class="sxs-lookup"><span data-stu-id="dc2d4-109">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="dc2d4-110">Pouze hodnoty rozpoznané rozhraním jsou "ActAs" a "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="dc2d4-110">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="dc2d4-111">Pokud jsou kolekce obslužných rutin tokenů zadány s některým z těchto názvů, kolekce bude použita při zpracování tokenů ActAs nebo OnBehalfOf.</span><span class="sxs-lookup"><span data-stu-id="dc2d4-111">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc2d4-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dc2d4-112">Child Elements</span></span>  
  
|<span data-ttu-id="dc2d4-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="dc2d4-113">Element</span></span>|<span data-ttu-id="dc2d4-114">Description</span><span class="sxs-lookup"><span data-stu-id="dc2d4-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="dc2d4-115">Přidá obslužnou rutinu tokenu zabezpečení do kolekce obslužných rutin tokenů.</span><span class="sxs-lookup"><span data-stu-id="dc2d4-115">Adds a security token handler to the token handler collection.</span></span>|  
|[\<clear>](clear.md)|<span data-ttu-id="dc2d4-116">Vymaže všechny obslužné rutiny tokenů zabezpečení z kolekce obslužných rutin tokenů.</span><span class="sxs-lookup"><span data-stu-id="dc2d4-116">Clears all security token handlers from the token handler collection.</span></span>|  
|[\<remove>](remove.md)|<span data-ttu-id="dc2d4-117">Odebere obslužnou rutinu tokenu zabezpečení z kolekce obslužných rutin tokenu.</span><span class="sxs-lookup"><span data-stu-id="dc2d4-117">Removes a security token handler from the token handler collection.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="dc2d4-118">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů.</span><span class="sxs-lookup"><span data-stu-id="dc2d4-118">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dc2d4-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dc2d4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="dc2d4-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="dc2d4-120">Element</span></span>|<span data-ttu-id="dc2d4-121">Description</span><span class="sxs-lookup"><span data-stu-id="dc2d4-121">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="dc2d4-122">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="dc2d4-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc2d4-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dc2d4-123">Remarks</span></span>  
 <span data-ttu-id="dc2d4-124">V konfiguraci služby můžete zadat jednu nebo více pojmenovaných obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="dc2d4-124">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="dc2d4-125">Název kolekce můžete zadat pomocí `name` atributu.</span><span class="sxs-lookup"><span data-stu-id="dc2d4-125">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="dc2d4-126">Jedinými názvy, které rozhraní zpracovává, jsou "ActAs" a "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="dc2d4-126">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="dc2d4-127">Pokud obslužné rutiny existují v těchto kolekcích, používají se pro službu tokenů zabezpečení (STS) místo výchozích obslužných rutin při zpracování `ActAs` `OnBehalfOf` tokenů.</span><span class="sxs-lookup"><span data-stu-id="dc2d4-127">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="dc2d4-128">Ve výchozím nastavení je kolekce naplněna následujícími typy obslužných rutin: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> a <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="dc2d4-128">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="dc2d4-129">Kolekci lze upravit pomocí `<add>` prvků, a `<remove>` `<clear>` .</span><span class="sxs-lookup"><span data-stu-id="dc2d4-129">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="dc2d4-130">Je nutné zajistit, aby v kolekci existovala pouze jedna obslužná rutina libovolného konkrétního typu.</span><span class="sxs-lookup"><span data-stu-id="dc2d4-130">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="dc2d4-131">Například pokud odvozujete obslužnou rutinu z <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídy, buď obslužnou rutinu, nebo <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> může být konfigurována v jedné kolekci, ale ne v obou.</span><span class="sxs-lookup"><span data-stu-id="dc2d4-131">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="dc2d4-132">Použijte `<securityTokenHandlerConfiguration>` element k určení nastavení konfigurace obslužných rutin v kolekci.</span><span class="sxs-lookup"><span data-stu-id="dc2d4-132">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="dc2d4-133">Nastavení zadaná prostřednictvím tohoto elementu přepíší hodnoty zadané ve službě prostřednictvím [\<identityConfiguration>](identityconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="dc2d4-133">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="dc2d4-134">Některé obslužné rutiny (včetně několika vestavěných typů obslužných rutin) mohou podporovat další konfiguraci prostřednictvím podřízeného prvku `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="dc2d4-134">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="dc2d4-135">Nastavení zadané u obslužné rutiny přepište ekvivalentní nastavení zadané v kolekci nebo službě.</span><span class="sxs-lookup"><span data-stu-id="dc2d4-135">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>
