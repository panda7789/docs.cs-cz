---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: 678e5c705181c55257b1ddb853690ada60ecd17a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942463"
---
# <a name="securitytokenhandlers"></a><span data-ttu-id="4aba9-101">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="4aba9-101">\<securityTokenHandlers></span></span>
<span data-ttu-id="4aba9-102">Určuje kolekci obslužných rutin tokenů zabezpečení, které jsou registrovány u koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="4aba9-102">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
 <span data-ttu-id="4aba9-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="4aba9-103">\<system.identityModel></span></span>  
<span data-ttu-id="4aba9-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="4aba9-104">\<identityConfiguration></span></span>  
<span data-ttu-id="4aba9-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="4aba9-105">\<securityTokenHandlers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aba9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4aba9-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4aba9-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4aba9-107">Attributes and Elements</span></span>  
 <span data-ttu-id="4aba9-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4aba9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4aba9-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="4aba9-109">Attributes</span></span>  
  
|<span data-ttu-id="4aba9-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="4aba9-110">Attribute</span></span>|<span data-ttu-id="4aba9-111">Popis</span><span class="sxs-lookup"><span data-stu-id="4aba9-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4aba9-112">name</span><span class="sxs-lookup"><span data-stu-id="4aba9-112">name</span></span>|<span data-ttu-id="4aba9-113">Určuje název kolekce obslužných rutin tokenu.</span><span class="sxs-lookup"><span data-stu-id="4aba9-113">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="4aba9-114">Pouze hodnoty rozpoznané rozhraním jsou "ActAs" a "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="4aba9-114">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="4aba9-115">Pokud jsou kolekce obslužných rutin tokenů zadány s některým z těchto názvů, kolekce bude použita při zpracování tokenů ActAs nebo OnBehalfOf.</span><span class="sxs-lookup"><span data-stu-id="4aba9-115">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4aba9-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4aba9-116">Child Elements</span></span>  
  
|<span data-ttu-id="4aba9-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="4aba9-117">Element</span></span>|<span data-ttu-id="4aba9-118">Popis</span><span class="sxs-lookup"><span data-stu-id="4aba9-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4aba9-119">\<add></span><span class="sxs-lookup"><span data-stu-id="4aba9-119">\<add></span></span>](add.md)|<span data-ttu-id="4aba9-120">Přidá obslužnou rutinu tokenu zabezpečení do kolekce obslužných rutin tokenů.</span><span class="sxs-lookup"><span data-stu-id="4aba9-120">Adds a security token handler to the token handler collection.</span></span>|  
|[<span data-ttu-id="4aba9-121">\<clear></span><span class="sxs-lookup"><span data-stu-id="4aba9-121">\<clear></span></span>](clear.md)|<span data-ttu-id="4aba9-122">Vymaže všechny obslužné rutiny tokenů zabezpečení z kolekce obslužných rutin tokenů.</span><span class="sxs-lookup"><span data-stu-id="4aba9-122">Clears all security token handlers from the token handler collection.</span></span>|  
|[<span data-ttu-id="4aba9-123">\<remove></span><span class="sxs-lookup"><span data-stu-id="4aba9-123">\<remove></span></span>](remove.md)|<span data-ttu-id="4aba9-124">Odebere obslužnou rutinu tokenu zabezpečení z kolekce obslužných rutin tokenu.</span><span class="sxs-lookup"><span data-stu-id="4aba9-124">Removes a security token handler from the token handler collection.</span></span>|  
|[<span data-ttu-id="4aba9-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="4aba9-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="4aba9-126">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů.</span><span class="sxs-lookup"><span data-stu-id="4aba9-126">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4aba9-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4aba9-127">Parent Elements</span></span>  
  
|<span data-ttu-id="4aba9-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="4aba9-128">Element</span></span>|<span data-ttu-id="4aba9-129">Popis</span><span class="sxs-lookup"><span data-stu-id="4aba9-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4aba9-130">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="4aba9-130">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="4aba9-131">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="4aba9-131">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4aba9-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4aba9-132">Remarks</span></span>  
 <span data-ttu-id="4aba9-133">V konfiguraci služby můžete zadat jednu nebo více pojmenovaných obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4aba9-133">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="4aba9-134">Název kolekce můžete zadat pomocí `name` atributu.</span><span class="sxs-lookup"><span data-stu-id="4aba9-134">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="4aba9-135">Jedinými názvy, které rozhraní zpracovává, jsou "ActAs" a "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="4aba9-135">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="4aba9-136">Pokud obslužné rutiny existují v těchto kolekcích, používají se pro službu tokenů zabezpečení (STS) místo výchozích obslužných rutin `ActAs` při `OnBehalfOf` zpracování tokenů.</span><span class="sxs-lookup"><span data-stu-id="4aba9-136">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="4aba9-137">Ve výchozím nastavení je kolekce naplněna následujícími typy obslužných rutin <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>: <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, a <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="4aba9-137">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="4aba9-138">Kolekci lze upravit pomocí `<add>` `<clear>` prvků, `<remove>`a.</span><span class="sxs-lookup"><span data-stu-id="4aba9-138">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="4aba9-139">Je nutné zajistit, aby v kolekci existovala pouze jedna obslužná rutina libovolného konkrétního typu.</span><span class="sxs-lookup"><span data-stu-id="4aba9-139">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="4aba9-140">Například pokud odvozujete obslužnou rutinu z <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídy, buď obslužnou rutinu, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> nebo může být konfigurována v jedné kolekci, ale ne v obou.</span><span class="sxs-lookup"><span data-stu-id="4aba9-140">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="4aba9-141">`<securityTokenHandlerConfiguration>` Použijte element k určení nastavení konfigurace obslužných rutin v kolekci.</span><span class="sxs-lookup"><span data-stu-id="4aba9-141">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="4aba9-142">Nastavení zadaná prostřednictvím tohoto elementu přepíší ty zadané ve službě prostřednictvím [ \<elementu IdentityConfiguration >](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="4aba9-142">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="4aba9-143">Některé obslužné rutiny (včetně několika vestavěných typů obslužných rutin) mohou podporovat další konfiguraci prostřednictvím podřízeného prvku `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="4aba9-143">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="4aba9-144">Nastavení zadané u obslužné rutiny přepište ekvivalentní nastavení zadané v kolekci nebo službě.</span><span class="sxs-lookup"><span data-stu-id="4aba9-144">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>
