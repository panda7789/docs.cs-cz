---
title: <Event> – Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89e8ddf9ea72db63c72bfb5393709b4c20de2a14
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162992"
---
# <a name="event-element-net-native"></a><span data-ttu-id="0b29c-102">\<Událost > – Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="0b29c-102">\<Event> Element (.NET Native)</span></span>
<span data-ttu-id="0b29c-103">Použije zásady reflexe runtime události.</span><span class="sxs-lookup"><span data-stu-id="0b29c-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b29c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b29c-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"   
       Browse="policy_type"   
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b29c-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0b29c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0b29c-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0b29c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b29c-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="0b29c-107">Attributes</span></span>  
  
|<span data-ttu-id="0b29c-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="0b29c-108">Attribute</span></span>|<span data-ttu-id="0b29c-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="0b29c-109">Attribute type</span></span>|<span data-ttu-id="0b29c-110">Popis</span><span class="sxs-lookup"><span data-stu-id="0b29c-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="0b29c-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="0b29c-111">General</span></span>|<span data-ttu-id="0b29c-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="0b29c-112">Required attribute.</span></span> <span data-ttu-id="0b29c-113">Určuje název události.</span><span class="sxs-lookup"><span data-stu-id="0b29c-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="0b29c-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="0b29c-114">Reflection</span></span>|<span data-ttu-id="0b29c-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0b29c-115">Optional attribute.</span></span> <span data-ttu-id="0b29c-116">Ovládací prvky dotazování na informace o nebo vytváření výčtu události, ale neumožňuje dynamické přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="0b29c-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="0b29c-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="0b29c-117">Reflection</span></span>|<span data-ttu-id="0b29c-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0b29c-118">Optional attribute.</span></span> <span data-ttu-id="0b29c-119">Modul runtime řídí přístup k události, které chcete povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="0b29c-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="0b29c-120">Tato zásada zajistí, že událost může být zpracována dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="0b29c-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="0b29c-121">Název atributu</span><span class="sxs-lookup"><span data-stu-id="0b29c-121">Name attribute</span></span>  
  
|<span data-ttu-id="0b29c-122">Value</span><span class="sxs-lookup"><span data-stu-id="0b29c-122">Value</span></span>|<span data-ttu-id="0b29c-123">Popis</span><span class="sxs-lookup"><span data-stu-id="0b29c-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0b29c-124">*method_name*</span><span class="sxs-lookup"><span data-stu-id="0b29c-124">*method_name*</span></span>|<span data-ttu-id="0b29c-125">Název události.</span><span class="sxs-lookup"><span data-stu-id="0b29c-125">The event name.</span></span> <span data-ttu-id="0b29c-126">Typ události je definován nadřazený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) nebo [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="0b29c-126">The type of the event is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="0b29c-127">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="0b29c-127">All other attributes</span></span>  
  
|<span data-ttu-id="0b29c-128">Value</span><span class="sxs-lookup"><span data-stu-id="0b29c-128">Value</span></span>|<span data-ttu-id="0b29c-129">Popis</span><span class="sxs-lookup"><span data-stu-id="0b29c-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0b29c-130">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="0b29c-130">*policy_setting*</span></span>|<span data-ttu-id="0b29c-131">Toto nastavení platí pro tento typ zásad pro událost.</span><span class="sxs-lookup"><span data-stu-id="0b29c-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="0b29c-132">Možné hodnoty jsou `Auto`, `Excluded`, `Included`, a `Required`.</span><span class="sxs-lookup"><span data-stu-id="0b29c-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="0b29c-133">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="0b29c-133">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b29c-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0b29c-134">Child Elements</span></span>  
 <span data-ttu-id="0b29c-135">Žádné</span><span class="sxs-lookup"><span data-stu-id="0b29c-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0b29c-136">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0b29c-136">Parent Elements</span></span>  
  
|<span data-ttu-id="0b29c-137">Prvek</span><span class="sxs-lookup"><span data-stu-id="0b29c-137">Element</span></span>|<span data-ttu-id="0b29c-138">Popis</span><span class="sxs-lookup"><span data-stu-id="0b29c-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0b29c-139">\<Type></span><span class="sxs-lookup"><span data-stu-id="0b29c-139">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="0b29c-140">Použije zásady reflexe pro typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="0b29c-140">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="0b29c-141">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="0b29c-141">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="0b29c-142">Použije zásady reflexe pro Konstruovaný obecný typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="0b29c-142">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b29c-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b29c-143">Remarks</span></span>  
 <span data-ttu-id="0b29c-144">Pokud zásady událostí nejsou výslovně definované, dědí zásady modulu runtime objektů svého nadřízeného elementu.</span><span class="sxs-lookup"><span data-stu-id="0b29c-144">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b29c-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b29c-145">See also</span></span>

- [<span data-ttu-id="0b29c-146">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="0b29c-146">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="0b29c-147">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="0b29c-147">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="0b29c-148">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="0b29c-148">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
