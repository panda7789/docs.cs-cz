---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: 017309436660991c69da569e9cc4219e842ecaa3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251877"
---
# <a name="securitytokenhandlers"></a><span data-ttu-id="6688b-101">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="6688b-101">\<securityTokenHandlers></span></span>
<span data-ttu-id="6688b-102">Určuje kolekci obslužných rutin tokenů zabezpečení, které jsou registrovány u koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="6688b-102">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
<span data-ttu-id="6688b-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6688b-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6688b-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="6688b-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="6688b-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="6688b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="6688b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<securityTokenHandlers >**</span><span class="sxs-lookup"><span data-stu-id="6688b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlers>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6688b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6688b-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6688b-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6688b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6688b-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6688b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6688b-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="6688b-110">Attributes</span></span>  
  
|<span data-ttu-id="6688b-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="6688b-111">Attribute</span></span>|<span data-ttu-id="6688b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6688b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6688b-113">name</span><span class="sxs-lookup"><span data-stu-id="6688b-113">name</span></span>|<span data-ttu-id="6688b-114">Určuje název kolekce obslužných rutin tokenu.</span><span class="sxs-lookup"><span data-stu-id="6688b-114">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="6688b-115">Pouze hodnoty rozpoznané rozhraním jsou "ActAs" a "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="6688b-115">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="6688b-116">Pokud jsou kolekce obslužných rutin tokenů zadány s některým z těchto názvů, kolekce bude použita při zpracování tokenů ActAs nebo OnBehalfOf.</span><span class="sxs-lookup"><span data-stu-id="6688b-116">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6688b-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6688b-117">Child Elements</span></span>  
  
|<span data-ttu-id="6688b-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="6688b-118">Element</span></span>|<span data-ttu-id="6688b-119">Popis</span><span class="sxs-lookup"><span data-stu-id="6688b-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6688b-120">\<add></span><span class="sxs-lookup"><span data-stu-id="6688b-120">\<add></span></span>](add.md)|<span data-ttu-id="6688b-121">Přidá obslužnou rutinu tokenu zabezpečení do kolekce obslužných rutin tokenů.</span><span class="sxs-lookup"><span data-stu-id="6688b-121">Adds a security token handler to the token handler collection.</span></span>|  
|[<span data-ttu-id="6688b-122">\<clear></span><span class="sxs-lookup"><span data-stu-id="6688b-122">\<clear></span></span>](clear.md)|<span data-ttu-id="6688b-123">Vymaže všechny obslužné rutiny tokenů zabezpečení z kolekce obslužných rutin tokenů.</span><span class="sxs-lookup"><span data-stu-id="6688b-123">Clears all security token handlers from the token handler collection.</span></span>|  
|[<span data-ttu-id="6688b-124">\<remove></span><span class="sxs-lookup"><span data-stu-id="6688b-124">\<remove></span></span>](remove.md)|<span data-ttu-id="6688b-125">Odebere obslužnou rutinu tokenu zabezpečení z kolekce obslužných rutin tokenu.</span><span class="sxs-lookup"><span data-stu-id="6688b-125">Removes a security token handler from the token handler collection.</span></span>|  
|[<span data-ttu-id="6688b-126">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="6688b-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="6688b-127">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů.</span><span class="sxs-lookup"><span data-stu-id="6688b-127">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6688b-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6688b-128">Parent Elements</span></span>  
  
|<span data-ttu-id="6688b-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="6688b-129">Element</span></span>|<span data-ttu-id="6688b-130">Popis</span><span class="sxs-lookup"><span data-stu-id="6688b-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6688b-131">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="6688b-131">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="6688b-132">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="6688b-132">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6688b-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6688b-133">Remarks</span></span>  
 <span data-ttu-id="6688b-134">V konfiguraci služby můžete zadat jednu nebo více pojmenovaných obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6688b-134">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="6688b-135">Název kolekce můžete zadat pomocí `name` atributu.</span><span class="sxs-lookup"><span data-stu-id="6688b-135">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="6688b-136">Jedinými názvy, které rozhraní zpracovává, jsou "ActAs" a "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="6688b-136">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="6688b-137">Pokud obslužné rutiny existují v těchto kolekcích, používají se pro službu tokenů zabezpečení (STS) místo výchozích obslužných rutin `ActAs` při `OnBehalfOf` zpracování tokenů.</span><span class="sxs-lookup"><span data-stu-id="6688b-137">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="6688b-138">Ve výchozím nastavení je kolekce naplněna následujícími typy obslužných rutin <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>: <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, a <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="6688b-138">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="6688b-139">Kolekci lze upravit pomocí `<add>` `<clear>` prvků, `<remove>`a.</span><span class="sxs-lookup"><span data-stu-id="6688b-139">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="6688b-140">Je nutné zajistit, aby v kolekci existovala pouze jedna obslužná rutina libovolného konkrétního typu.</span><span class="sxs-lookup"><span data-stu-id="6688b-140">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="6688b-141">Například pokud odvozujete obslužnou rutinu z <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídy, buď obslužnou rutinu, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> nebo může být konfigurována v jedné kolekci, ale ne v obou.</span><span class="sxs-lookup"><span data-stu-id="6688b-141">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="6688b-142">`<securityTokenHandlerConfiguration>` Použijte element k určení nastavení konfigurace obslužných rutin v kolekci.</span><span class="sxs-lookup"><span data-stu-id="6688b-142">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="6688b-143">Nastavení zadaná prostřednictvím tohoto elementu přepíší ty zadané ve službě prostřednictvím [ \<elementu IdentityConfiguration >](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="6688b-143">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="6688b-144">Některé obslužné rutiny (včetně několika vestavěných typů obslužných rutin) mohou podporovat další konfiguraci prostřednictvím podřízeného prvku `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="6688b-144">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="6688b-145">Nastavení zadané u obslužné rutiny přepište ekvivalentní nastavení zadané v kolekci nebo službě.</span><span class="sxs-lookup"><span data-stu-id="6688b-145">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>
