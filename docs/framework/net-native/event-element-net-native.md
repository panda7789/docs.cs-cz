---
title: <Event> – element (.NET Native)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
ms.openlocfilehash: 6966caede63faafa718b760be879f6bc6cbd3ab9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128495"
---
# <a name="event-element-net-native"></a><span data-ttu-id="586be-102">\<element > události (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="586be-102">\<Event> Element (.NET Native)</span></span>
<span data-ttu-id="586be-103">Aplikuje zásadu reflexe modulu runtime na událost.</span><span class="sxs-lookup"><span data-stu-id="586be-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="586be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="586be-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"   
       Browse="policy_type"   
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="586be-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="586be-105">Attributes and Elements</span></span>  
 <span data-ttu-id="586be-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="586be-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="586be-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="586be-107">Attributes</span></span>  
  
|<span data-ttu-id="586be-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="586be-108">Attribute</span></span>|<span data-ttu-id="586be-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="586be-109">Attribute type</span></span>|<span data-ttu-id="586be-110">Popis</span><span class="sxs-lookup"><span data-stu-id="586be-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="586be-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="586be-111">General</span></span>|<span data-ttu-id="586be-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="586be-112">Required attribute.</span></span> <span data-ttu-id="586be-113">Určuje název události.</span><span class="sxs-lookup"><span data-stu-id="586be-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="586be-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="586be-114">Reflection</span></span>|<span data-ttu-id="586be-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="586be-115">Optional attribute.</span></span> <span data-ttu-id="586be-116">Řídí dotazování na informace o nebo vytváření výčtu události, ale nepovoluje žádný dynamický přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="586be-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="586be-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="586be-117">Reflection</span></span>|<span data-ttu-id="586be-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="586be-118">Optional attribute.</span></span> <span data-ttu-id="586be-119">Řídí přístup za běhu k události pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="586be-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="586be-120">Tato zásada zajišťuje, že událost může být v době běhu zpracována dynamicky.</span><span class="sxs-lookup"><span data-stu-id="586be-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="586be-121">Atribut Name</span><span class="sxs-lookup"><span data-stu-id="586be-121">Name attribute</span></span>  
  
|<span data-ttu-id="586be-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="586be-122">Value</span></span>|<span data-ttu-id="586be-123">Popis</span><span class="sxs-lookup"><span data-stu-id="586be-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="586be-124">*method_name*</span><span class="sxs-lookup"><span data-stu-id="586be-124">*method_name*</span></span>|<span data-ttu-id="586be-125">Název události</span><span class="sxs-lookup"><span data-stu-id="586be-125">The event name.</span></span> <span data-ttu-id="586be-126">Typ události je definován nadřazeným [\<typem >](type-element-net-native.md) nebo [\<elementu > TypeInstantiation](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="586be-126">The type of the event is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="586be-127">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="586be-127">All other attributes</span></span>  
  
|<span data-ttu-id="586be-128">Hodnota</span><span class="sxs-lookup"><span data-stu-id="586be-128">Value</span></span>|<span data-ttu-id="586be-129">Popis</span><span class="sxs-lookup"><span data-stu-id="586be-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="586be-130">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="586be-130">*policy_setting*</span></span>|<span data-ttu-id="586be-131">Nastavení, které se má použít pro tento typ zásad pro událost</span><span class="sxs-lookup"><span data-stu-id="586be-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="586be-132">Možné hodnoty jsou `Auto`, `Excluded`, `Included`a `Required`.</span><span class="sxs-lookup"><span data-stu-id="586be-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="586be-133">Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="586be-133">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="586be-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="586be-134">Child Elements</span></span>  
 <span data-ttu-id="586be-135">Žádné</span><span class="sxs-lookup"><span data-stu-id="586be-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="586be-136">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="586be-136">Parent Elements</span></span>  
  
|<span data-ttu-id="586be-137">Prvek</span><span class="sxs-lookup"><span data-stu-id="586be-137">Element</span></span>|<span data-ttu-id="586be-138">Popis</span><span class="sxs-lookup"><span data-stu-id="586be-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="586be-139">Typ\<</span><span class="sxs-lookup"><span data-stu-id="586be-139">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="586be-140">Aplikuje zásadu odrazu na typ a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="586be-140">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="586be-141">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="586be-141">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="586be-142">Aplikuje zásadu odrazu na konstruovaný obecný typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="586be-142">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="586be-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="586be-143">Remarks</span></span>  
 <span data-ttu-id="586be-144">Pokud zásada události není explicitně definována, zdědí zásady modulu runtime svého nadřazeného prvku.</span><span class="sxs-lookup"><span data-stu-id="586be-144">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="586be-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="586be-145">See also</span></span>

- [<span data-ttu-id="586be-146">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="586be-146">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="586be-147">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="586be-147">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="586be-148">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="586be-148">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
