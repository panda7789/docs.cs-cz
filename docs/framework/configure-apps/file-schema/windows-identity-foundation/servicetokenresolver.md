---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 30a53c11b551623311f7ca3f957143fc702568a1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251851"
---
# <a name="servicetokenresolver"></a><span data-ttu-id="5ee49-101">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="5ee49-101">\<serviceTokenResolver></span></span>
<span data-ttu-id="5ee49-102">Registruje překladač tokenů služby, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenu.</span><span class="sxs-lookup"><span data-stu-id="5ee49-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="5ee49-103">Překladač tokenů služby se používá k překladu šifrovacího tokenu na příchozích tokenech a zprávách.</span><span class="sxs-lookup"><span data-stu-id="5ee49-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="5ee49-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5ee49-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5ee49-105">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="5ee49-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="5ee49-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="5ee49-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="5ee49-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="5ee49-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="5ee49-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="5ee49-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="5ee49-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceTokenResolver >**</span><span class="sxs-lookup"><span data-stu-id="5ee49-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ee49-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ee49-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ee49-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5ee49-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5ee49-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5ee49-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ee49-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="5ee49-113">Attributes</span></span>  
  
|<span data-ttu-id="5ee49-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="5ee49-114">Attribute</span></span>|<span data-ttu-id="5ee49-115">Popis</span><span class="sxs-lookup"><span data-stu-id="5ee49-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ee49-116">– typ</span><span class="sxs-lookup"><span data-stu-id="5ee49-116">type</span></span>|<span data-ttu-id="5ee49-117">Určuje typ překladače tokenu služby.</span><span class="sxs-lookup"><span data-stu-id="5ee49-117">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="5ee49-118">Buď typ, nebo typ, který je odvozen <xref:System.IdentityModel.Selectors.SecurityTokenResolver> od třídy. <xref:System.IdentityModel.Selectors.SecurityTokenResolver></span><span class="sxs-lookup"><span data-stu-id="5ee49-118">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="5ee49-119">Další informace o tom, jak zadat `type` atribut, naleznete v tématu [odkazy na vlastní typ].</span><span class="sxs-lookup"><span data-stu-id="5ee49-119">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="5ee49-120">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="5ee49-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ee49-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5ee49-121">Child Elements</span></span>  
 <span data-ttu-id="5ee49-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="5ee49-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ee49-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5ee49-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5ee49-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="5ee49-124">Element</span></span>|<span data-ttu-id="5ee49-125">Popis</span><span class="sxs-lookup"><span data-stu-id="5ee49-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ee49-126">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="5ee49-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="5ee49-127">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5ee49-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ee49-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5ee49-128">Remarks</span></span>  
 <span data-ttu-id="5ee49-129">Překladač tokenů služby se dá použít k vyřešení šifrovacího tokenu u příchozích tokenů a zpráv.</span><span class="sxs-lookup"><span data-stu-id="5ee49-129">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="5ee49-130">Používá se k načtení klíče, který by se měl použít k dešifrování příchozích tokenů.</span><span class="sxs-lookup"><span data-stu-id="5ee49-130">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="5ee49-131">Je nutné zadat `type` atribut.</span><span class="sxs-lookup"><span data-stu-id="5ee49-131">You must specify the `type` attribute.</span></span> <span data-ttu-id="5ee49-132">Zadaný typ může být buď <xref:System.IdentityModel.Selectors.SecurityTokenResolver> nebo vlastní typ, který je odvozen <xref:System.IdentityModel.Selectors.SecurityTokenResolver> od třídy.</span><span class="sxs-lookup"><span data-stu-id="5ee49-132">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="5ee49-133">Některé obslužné rutiny tokenů umožňují zadat nastavení překladače tokenu služby v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="5ee49-133">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="5ee49-134">Nastavení pro obslužné rutiny jednotlivých tokenů přepíší ty zadané v kolekci obslužných rutin tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5ee49-134">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ee49-135">Určení prvku jako podřízeného prvku [ \<prvku IdentityConfiguration >](identityconfiguration.md) je zastaralé, ale stále se podporuje z důvodu zpětné kompatibility. `<serviceTokenResolver>`</span><span class="sxs-lookup"><span data-stu-id="5ee49-135">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="5ee49-136">Nastavení na `<securityTokenHandlerConfiguration>` elementu přepíší tyto prvky `<identityConfiguration>` na elementu.</span><span class="sxs-lookup"><span data-stu-id="5ee49-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ee49-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="5ee49-137">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
 