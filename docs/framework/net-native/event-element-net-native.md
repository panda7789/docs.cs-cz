---
title: <Event>Element (nativní.NET)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
ms.openlocfilehash: 60da48d5872d7ce61afcffa7977411bc6e1efc7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181043"
---
# <a name="event-element-net-native"></a><span data-ttu-id="ab976-102">\<Prvek> události (nativní.NET)</span><span class="sxs-lookup"><span data-stu-id="ab976-102">\<Event> Element (.NET Native)</span></span>
<span data-ttu-id="ab976-103">Použije zásady reflexe za běhu na událost.</span><span class="sxs-lookup"><span data-stu-id="ab976-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab976-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab976-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"
       Browse="policy_type"
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab976-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ab976-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ab976-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ab976-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab976-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="ab976-107">Attributes</span></span>  
  
|<span data-ttu-id="ab976-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="ab976-108">Attribute</span></span>|<span data-ttu-id="ab976-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="ab976-109">Attribute type</span></span>|<span data-ttu-id="ab976-110">Popis</span><span class="sxs-lookup"><span data-stu-id="ab976-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="ab976-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="ab976-111">General</span></span>|<span data-ttu-id="ab976-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="ab976-112">Required attribute.</span></span> <span data-ttu-id="ab976-113">Určuje název události.</span><span class="sxs-lookup"><span data-stu-id="ab976-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="ab976-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="ab976-114">Reflection</span></span>|<span data-ttu-id="ab976-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ab976-115">Optional attribute.</span></span> <span data-ttu-id="ab976-116">Řídí dotazování na informace o události nebo výčet události, ale neumožňuje žádný dynamický přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="ab976-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="ab976-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="ab976-117">Reflection</span></span>|<span data-ttu-id="ab976-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ab976-118">Optional attribute.</span></span> <span data-ttu-id="ab976-119">Řídí přístup za běhu k události, aby bylo možné dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="ab976-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="ab976-120">Tato zásada zajišťuje, že událost může být zpracována dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="ab976-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="ab976-121">Atribut Název</span><span class="sxs-lookup"><span data-stu-id="ab976-121">Name attribute</span></span>  
  
|<span data-ttu-id="ab976-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ab976-122">Value</span></span>|<span data-ttu-id="ab976-123">Popis</span><span class="sxs-lookup"><span data-stu-id="ab976-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ab976-124">*method_name*</span><span class="sxs-lookup"><span data-stu-id="ab976-124">*method_name*</span></span>|<span data-ttu-id="ab976-125">Název události</span><span class="sxs-lookup"><span data-stu-id="ab976-125">The event name.</span></span> <span data-ttu-id="ab976-126">Typ události je definován nadřazeným [ \<typem>](type-element-net-native.md) nebo [ \<TypeInstantiation>](typeinstantiation-element-net-native.md) elementem.</span><span class="sxs-lookup"><span data-stu-id="ab976-126">The type of the event is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="ab976-127">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="ab976-127">All other attributes</span></span>  
  
|<span data-ttu-id="ab976-128">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ab976-128">Value</span></span>|<span data-ttu-id="ab976-129">Popis</span><span class="sxs-lookup"><span data-stu-id="ab976-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ab976-130">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="ab976-130">*policy_setting*</span></span>|<span data-ttu-id="ab976-131">Nastavení, které se má použít pro tento typ zásad pro událost.</span><span class="sxs-lookup"><span data-stu-id="ab976-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="ab976-132">Možné hodnoty `Auto` `Excluded`jsou `Included`, `Required`, a .</span><span class="sxs-lookup"><span data-stu-id="ab976-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="ab976-133">Další informace naleznete v tématu [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="ab976-133">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab976-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ab976-134">Child Elements</span></span>  
 <span data-ttu-id="ab976-135">Žádné.</span><span class="sxs-lookup"><span data-stu-id="ab976-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ab976-136">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ab976-136">Parent Elements</span></span>  
  
|<span data-ttu-id="ab976-137">Element</span><span class="sxs-lookup"><span data-stu-id="ab976-137">Element</span></span>|<span data-ttu-id="ab976-138">Popis</span><span class="sxs-lookup"><span data-stu-id="ab976-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab976-139">\<Typ></span><span class="sxs-lookup"><span data-stu-id="ab976-139">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="ab976-140">Použije zásady reflexe na typ a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="ab976-140">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="ab976-141">\<TypRychlé></span><span class="sxs-lookup"><span data-stu-id="ab976-141">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="ab976-142">Použije zásady reflexe na vytvořený obecný typ a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="ab976-142">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab976-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab976-143">Remarks</span></span>  
 <span data-ttu-id="ab976-144">Pokud zásady události není explicitně definována, dědí zásady runtime svého nadřazeného prvku.</span><span class="sxs-lookup"><span data-stu-id="ab976-144">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab976-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab976-145">See also</span></span>

- [<span data-ttu-id="ab976-146">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="ab976-146">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="ab976-147">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="ab976-147">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="ab976-148">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="ab976-148">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
