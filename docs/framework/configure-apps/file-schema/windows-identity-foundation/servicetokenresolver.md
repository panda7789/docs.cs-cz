---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 69d34cb54c2236f178ac4291ed24a3f5b45db48e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923108"
---
# <a name="servicetokenresolver"></a><span data-ttu-id="fb3ae-101">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="fb3ae-101">\<serviceTokenResolver></span></span>
<span data-ttu-id="fb3ae-102">Registruje překladač tokenů služby, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenu.</span><span class="sxs-lookup"><span data-stu-id="fb3ae-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="fb3ae-103">Překladač tokenů služby se používá k překladu šifrovacího tokenu na příchozích tokenech a zprávách.</span><span class="sxs-lookup"><span data-stu-id="fb3ae-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="fb3ae-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="fb3ae-104">\<system.identityModel></span></span>  
<span data-ttu-id="fb3ae-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="fb3ae-105">\<identityConfiguration></span></span>  
<span data-ttu-id="fb3ae-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="fb3ae-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="fb3ae-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="fb3ae-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="fb3ae-108">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="fb3ae-108">\<serviceTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb3ae-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb3ae-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb3ae-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fb3ae-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fb3ae-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fb3ae-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb3ae-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="fb3ae-112">Attributes</span></span>  
  
|<span data-ttu-id="fb3ae-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="fb3ae-113">Attribute</span></span>|<span data-ttu-id="fb3ae-114">Popis</span><span class="sxs-lookup"><span data-stu-id="fb3ae-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fb3ae-115">– typ</span><span class="sxs-lookup"><span data-stu-id="fb3ae-115">type</span></span>|<span data-ttu-id="fb3ae-116">Určuje typ překladače tokenu služby.</span><span class="sxs-lookup"><span data-stu-id="fb3ae-116">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="fb3ae-117">Buď typ, nebo typ, který je odvozen <xref:System.IdentityModel.Selectors.SecurityTokenResolver> od třídy. <xref:System.IdentityModel.Selectors.SecurityTokenResolver></span><span class="sxs-lookup"><span data-stu-id="fb3ae-117">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="fb3ae-118">Další informace o tom, jak zadat `type` atribut, naleznete v tématu [odkazy na vlastní typ].</span><span class="sxs-lookup"><span data-stu-id="fb3ae-118">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="fb3ae-119">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="fb3ae-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb3ae-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fb3ae-120">Child Elements</span></span>  
 <span data-ttu-id="fb3ae-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="fb3ae-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fb3ae-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fb3ae-122">Parent Elements</span></span>  
  
|<span data-ttu-id="fb3ae-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="fb3ae-123">Element</span></span>|<span data-ttu-id="fb3ae-124">Popis</span><span class="sxs-lookup"><span data-stu-id="fb3ae-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb3ae-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="fb3ae-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="fb3ae-126">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="fb3ae-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb3ae-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb3ae-127">Remarks</span></span>  
 <span data-ttu-id="fb3ae-128">Překladač tokenů služby se dá použít k vyřešení šifrovacího tokenu u příchozích tokenů a zpráv.</span><span class="sxs-lookup"><span data-stu-id="fb3ae-128">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="fb3ae-129">Používá se k načtení klíče, který by se měl použít k dešifrování příchozích tokenů.</span><span class="sxs-lookup"><span data-stu-id="fb3ae-129">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="fb3ae-130">Je nutné zadat `type` atribut.</span><span class="sxs-lookup"><span data-stu-id="fb3ae-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="fb3ae-131">Zadaný typ může být buď <xref:System.IdentityModel.Selectors.SecurityTokenResolver> nebo vlastní typ, který je odvozen <xref:System.IdentityModel.Selectors.SecurityTokenResolver> od třídy.</span><span class="sxs-lookup"><span data-stu-id="fb3ae-131">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="fb3ae-132">Některé obslužné rutiny tokenů umožňují zadat nastavení překladače tokenu služby v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="fb3ae-132">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="fb3ae-133">Nastavení pro obslužné rutiny jednotlivých tokenů přepíší ty zadané v kolekci obslužných rutin tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="fb3ae-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fb3ae-134">Určení prvku jako podřízeného prvku [ \<prvku IdentityConfiguration >](identityconfiguration.md) je zastaralé, ale stále se podporuje z důvodu zpětné kompatibility. `<serviceTokenResolver>`</span><span class="sxs-lookup"><span data-stu-id="fb3ae-134">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="fb3ae-135">Nastavení na `<securityTokenHandlerConfiguration>` elementu přepíší tyto prvky `<identityConfiguration>` na elementu.</span><span class="sxs-lookup"><span data-stu-id="fb3ae-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb3ae-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb3ae-136">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
