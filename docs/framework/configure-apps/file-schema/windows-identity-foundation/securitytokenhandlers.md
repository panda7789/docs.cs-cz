---
title: '&lt;securityTokenHandlers&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: de19fffdeae801163ec991ecf08d00b1286781d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritytokenhandlersgt"></a><span data-ttu-id="fdd24-102">&lt;securityTokenHandlers&gt;</span><span class="sxs-lookup"><span data-stu-id="fdd24-102">&lt;securityTokenHandlers&gt;</span></span>
<span data-ttu-id="fdd24-103">Určuje kolekci zabezpečení tokenu rutin, které jsou registrovány koncový bod.</span><span class="sxs-lookup"><span data-stu-id="fdd24-103">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
 <span data-ttu-id="fdd24-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="fdd24-104">\<system.identityModel></span></span>  
<span data-ttu-id="fdd24-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="fdd24-105">\<identityConfiguration></span></span>  
<span data-ttu-id="fdd24-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="fdd24-106">\<securityTokenHandlers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdd24-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fdd24-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fdd24-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fdd24-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fdd24-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fdd24-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fdd24-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="fdd24-110">Attributes</span></span>  
  
|<span data-ttu-id="fdd24-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="fdd24-111">Attribute</span></span>|<span data-ttu-id="fdd24-112">Popis</span><span class="sxs-lookup"><span data-stu-id="fdd24-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fdd24-113">name</span><span class="sxs-lookup"><span data-stu-id="fdd24-113">name</span></span>|<span data-ttu-id="fdd24-114">Určuje název kolekce obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="fdd24-114">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="fdd24-115">Jsou pouze hodnoty rozpoznáno rozhraní "ActAs" a "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="fdd24-115">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="fdd24-116">Pokud obslužná rutina tokenu kolekce jsou zadané s některou z těchto názvů, kolekce se použije při zpracování ActAs nebo prostřednictvím profilu OnBehalfOf tokeny v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="fdd24-116">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fdd24-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fdd24-117">Child Elements</span></span>  
  
|<span data-ttu-id="fdd24-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="fdd24-118">Element</span></span>|<span data-ttu-id="fdd24-119">Popis</span><span class="sxs-lookup"><span data-stu-id="fdd24-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fdd24-120">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="fdd24-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="fdd24-121">Obslužná rutina tokenu zabezpečení se přidá do kolekce obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="fdd24-121">Adds a security token handler to the token handler collection.</span></span>|  
|[<span data-ttu-id="fdd24-122">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="fdd24-122">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)|<span data-ttu-id="fdd24-123">Vymaže všechny rutiny tokenu zabezpečení z kolekce obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="fdd24-123">Clears all security token handlers from the token handler collection.</span></span>|  
|[<span data-ttu-id="fdd24-124">\<Odebrat ></span><span class="sxs-lookup"><span data-stu-id="fdd24-124">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)|<span data-ttu-id="fdd24-125">Obslužná rutina tokenu zabezpečení se odebere z kolekce obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="fdd24-125">Removes a security token handler from the token handler collection.</span></span>|  
|[<span data-ttu-id="fdd24-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="fdd24-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="fdd24-127">Poskytuje konfigurace pro kolekci tokenu obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="fdd24-127">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fdd24-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fdd24-128">Parent Elements</span></span>  
  
|<span data-ttu-id="fdd24-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="fdd24-129">Element</span></span>|<span data-ttu-id="fdd24-130">Popis</span><span class="sxs-lookup"><span data-stu-id="fdd24-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fdd24-131">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="fdd24-131">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="fdd24-132">Určuje nastavení identity úrovně služeb.</span><span class="sxs-lookup"><span data-stu-id="fdd24-132">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdd24-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fdd24-133">Remarks</span></span>  
 <span data-ttu-id="fdd24-134">V konfiguraci služby můžete zadat jednu nebo více pojmenované kolekcí obslužných rutin, token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="fdd24-134">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="fdd24-135">Můžete zadat název pro kolekci pomocí `name` atribut.</span><span class="sxs-lookup"><span data-stu-id="fdd24-135">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="fdd24-136">Pouze názvy, které zpracovává rozhraní jsou "ActAs" a "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="fdd24-136">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="fdd24-137">Pokud v těchto kolekcích existuje obslužné rutiny, použijí se pomocí služby tokenů zabezpečení (STS) namísto výchozí obslužné rutiny při zpracování `ActAs` a `OnBehalfOf` tokeny.</span><span class="sxs-lookup"><span data-stu-id="fdd24-137">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="fdd24-138">Ve výchozím nastavení, je kolekce naplněný následující typy obslužných rutin: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, a <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="fdd24-138">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="fdd24-139">Kolekce můžete upravit pomocí `<add>`, `<remove>`, a `<clear>` elementy.</span><span class="sxs-lookup"><span data-stu-id="fdd24-139">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="fdd24-140">Je nutné zajistit, že pouze jeden obslužná rutina žádný konkrétní typ v kolekci existuje.</span><span class="sxs-lookup"><span data-stu-id="fdd24-140">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="fdd24-141">Například pokud odvozujete obslužnou rutinu z <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídy buď vaší obslužné rutiny nebo <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> může být nakonfigurována v jedné kolekci, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="fdd24-141">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="fdd24-142">Použití `<securityTokenHandlerConfiguration>` element ke specifikaci nastavení konfigurace pro obslužné rutiny, v kolekci.</span><span class="sxs-lookup"><span data-stu-id="fdd24-142">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="fdd24-143">Nastavení zadána prostřednictvím tohoto elementu přepíšou zadaný u služby pomocí [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span><span class="sxs-lookup"><span data-stu-id="fdd24-143">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="fdd24-144">Některé obslužné rutiny (včetně několik typů předdefinované obslužné rutiny) může podporovat další konfiguraci prostřednictvím podřízeného prvku `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="fdd24-144">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="fdd24-145">Bylo nastaveno na obslužnou rutinu přepsat ekvivalentní nastavení zadané v kolekci nebo službu.</span><span class="sxs-lookup"><span data-stu-id="fdd24-145">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>
