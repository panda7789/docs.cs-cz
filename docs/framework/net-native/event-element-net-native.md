---
title: <Event>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fb0245c50677da0397ba9c4918f171dcb217ba6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049850"
---
# <a name="event-element-net-native"></a><span data-ttu-id="17ae7-102">\<Element > události (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="17ae7-102">\<Event> Element (.NET Native)</span></span>
<span data-ttu-id="17ae7-103">Aplikuje zásadu reflexe modulu runtime na událost.</span><span class="sxs-lookup"><span data-stu-id="17ae7-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17ae7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17ae7-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"   
       Browse="policy_type"   
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17ae7-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="17ae7-105">Attributes and Elements</span></span>  
 <span data-ttu-id="17ae7-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="17ae7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17ae7-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="17ae7-107">Attributes</span></span>  
  
|<span data-ttu-id="17ae7-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="17ae7-108">Attribute</span></span>|<span data-ttu-id="17ae7-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="17ae7-109">Attribute type</span></span>|<span data-ttu-id="17ae7-110">Popis</span><span class="sxs-lookup"><span data-stu-id="17ae7-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="17ae7-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="17ae7-111">General</span></span>|<span data-ttu-id="17ae7-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="17ae7-112">Required attribute.</span></span> <span data-ttu-id="17ae7-113">Určuje název události.</span><span class="sxs-lookup"><span data-stu-id="17ae7-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="17ae7-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="17ae7-114">Reflection</span></span>|<span data-ttu-id="17ae7-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="17ae7-115">Optional attribute.</span></span> <span data-ttu-id="17ae7-116">Řídí dotazování na informace o nebo vytváření výčtu události, ale nepovoluje žádný dynamický přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="17ae7-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="17ae7-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="17ae7-117">Reflection</span></span>|<span data-ttu-id="17ae7-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="17ae7-118">Optional attribute.</span></span> <span data-ttu-id="17ae7-119">Řídí přístup za běhu k události pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="17ae7-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="17ae7-120">Tato zásada zajišťuje, že událost může být v době běhu zpracována dynamicky.</span><span class="sxs-lookup"><span data-stu-id="17ae7-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="17ae7-121">Atribut Name</span><span class="sxs-lookup"><span data-stu-id="17ae7-121">Name attribute</span></span>  
  
|<span data-ttu-id="17ae7-122">Value</span><span class="sxs-lookup"><span data-stu-id="17ae7-122">Value</span></span>|<span data-ttu-id="17ae7-123">Popis</span><span class="sxs-lookup"><span data-stu-id="17ae7-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="17ae7-124">*method_name*</span><span class="sxs-lookup"><span data-stu-id="17ae7-124">*method_name*</span></span>|<span data-ttu-id="17ae7-125">Název události</span><span class="sxs-lookup"><span data-stu-id="17ae7-125">The event name.</span></span> <span data-ttu-id="17ae7-126">Typ události je definován nadřazeným [ \<typem >](type-element-net-native.md) nebo [ \<elementem > TypeInstantiation](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="17ae7-126">The type of the event is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="17ae7-127">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="17ae7-127">All other attributes</span></span>  
  
|<span data-ttu-id="17ae7-128">Value</span><span class="sxs-lookup"><span data-stu-id="17ae7-128">Value</span></span>|<span data-ttu-id="17ae7-129">Popis</span><span class="sxs-lookup"><span data-stu-id="17ae7-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="17ae7-130">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="17ae7-130">*policy_setting*</span></span>|<span data-ttu-id="17ae7-131">Nastavení, které se má použít pro tento typ zásad pro událost</span><span class="sxs-lookup"><span data-stu-id="17ae7-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="17ae7-132">Možné hodnoty jsou `Auto`, `Excluded`, `Included`a. `Required`</span><span class="sxs-lookup"><span data-stu-id="17ae7-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="17ae7-133">Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="17ae7-133">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17ae7-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="17ae7-134">Child Elements</span></span>  
 <span data-ttu-id="17ae7-135">Žádné</span><span class="sxs-lookup"><span data-stu-id="17ae7-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="17ae7-136">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="17ae7-136">Parent Elements</span></span>  
  
|<span data-ttu-id="17ae7-137">Prvek</span><span class="sxs-lookup"><span data-stu-id="17ae7-137">Element</span></span>|<span data-ttu-id="17ae7-138">Popis</span><span class="sxs-lookup"><span data-stu-id="17ae7-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="17ae7-139">\<Zadejte ></span><span class="sxs-lookup"><span data-stu-id="17ae7-139">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="17ae7-140">Aplikuje zásadu odrazu na typ a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="17ae7-140">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="17ae7-141">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="17ae7-141">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="17ae7-142">Aplikuje zásadu odrazu na konstruovaný obecný typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="17ae7-142">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17ae7-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="17ae7-143">Remarks</span></span>  
 <span data-ttu-id="17ae7-144">Pokud zásada události není explicitně definována, zdědí zásady modulu runtime svého nadřazeného prvku.</span><span class="sxs-lookup"><span data-stu-id="17ae7-144">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17ae7-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17ae7-145">See also</span></span>

- [<span data-ttu-id="17ae7-146">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="17ae7-146">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="17ae7-147">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="17ae7-147">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="17ae7-148">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="17ae7-148">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
