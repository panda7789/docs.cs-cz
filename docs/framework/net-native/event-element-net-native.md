---
title: <Event>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
ms.openlocfilehash: 60da48d5872d7ce61afcffa7977411bc6e1efc7f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79181043"
---
# <a name="event-element-net-native"></a><span data-ttu-id="668b2-102">\<Event>– Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="668b2-102">\<Event> Element (.NET Native)</span></span>
<span data-ttu-id="668b2-103">Aplikuje zásadu reflexe modulu runtime na událost.</span><span class="sxs-lookup"><span data-stu-id="668b2-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="668b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="668b2-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"
       Browse="policy_type"
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="668b2-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="668b2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="668b2-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="668b2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="668b2-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="668b2-107">Attributes</span></span>  
  
|<span data-ttu-id="668b2-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="668b2-108">Attribute</span></span>|<span data-ttu-id="668b2-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="668b2-109">Attribute type</span></span>|<span data-ttu-id="668b2-110">Description</span><span class="sxs-lookup"><span data-stu-id="668b2-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="668b2-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="668b2-111">General</span></span>|<span data-ttu-id="668b2-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="668b2-112">Required attribute.</span></span> <span data-ttu-id="668b2-113">Určuje název události.</span><span class="sxs-lookup"><span data-stu-id="668b2-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="668b2-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="668b2-114">Reflection</span></span>|<span data-ttu-id="668b2-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="668b2-115">Optional attribute.</span></span> <span data-ttu-id="668b2-116">Řídí dotazování na informace o nebo vytváření výčtu události, ale nepovoluje žádný dynamický přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="668b2-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="668b2-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="668b2-117">Reflection</span></span>|<span data-ttu-id="668b2-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="668b2-118">Optional attribute.</span></span> <span data-ttu-id="668b2-119">Řídí přístup za běhu k události pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="668b2-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="668b2-120">Tato zásada zajišťuje, že událost může být v době běhu zpracována dynamicky.</span><span class="sxs-lookup"><span data-stu-id="668b2-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="668b2-121">Atribut Name</span><span class="sxs-lookup"><span data-stu-id="668b2-121">Name attribute</span></span>  
  
|<span data-ttu-id="668b2-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="668b2-122">Value</span></span>|<span data-ttu-id="668b2-123">Description</span><span class="sxs-lookup"><span data-stu-id="668b2-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="668b2-124">*method_name*</span><span class="sxs-lookup"><span data-stu-id="668b2-124">*method_name*</span></span>|<span data-ttu-id="668b2-125">Název události</span><span class="sxs-lookup"><span data-stu-id="668b2-125">The event name.</span></span> <span data-ttu-id="668b2-126">Typ události je definován nadřazeným [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) prvkem nebo prvkem.</span><span class="sxs-lookup"><span data-stu-id="668b2-126">The type of the event is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="668b2-127">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="668b2-127">All other attributes</span></span>  
  
|<span data-ttu-id="668b2-128">Hodnota</span><span class="sxs-lookup"><span data-stu-id="668b2-128">Value</span></span>|<span data-ttu-id="668b2-129">Description</span><span class="sxs-lookup"><span data-stu-id="668b2-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="668b2-130">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="668b2-130">*policy_setting*</span></span>|<span data-ttu-id="668b2-131">Nastavení, které se má použít pro tento typ zásad pro událost</span><span class="sxs-lookup"><span data-stu-id="668b2-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="668b2-132">Možné hodnoty jsou `Auto` , `Excluded` , `Included` a `Required` .</span><span class="sxs-lookup"><span data-stu-id="668b2-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="668b2-133">Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="668b2-133">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="668b2-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="668b2-134">Child Elements</span></span>  
 <span data-ttu-id="668b2-135">Žádné</span><span class="sxs-lookup"><span data-stu-id="668b2-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="668b2-136">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="668b2-136">Parent Elements</span></span>  
  
|<span data-ttu-id="668b2-137">Prvek</span><span class="sxs-lookup"><span data-stu-id="668b2-137">Element</span></span>|<span data-ttu-id="668b2-138">Description</span><span class="sxs-lookup"><span data-stu-id="668b2-138">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="668b2-139">Aplikuje zásadu odrazu na typ a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="668b2-139">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="668b2-140">Aplikuje zásadu odrazu na konstruovaný obecný typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="668b2-140">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="668b2-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="668b2-141">Remarks</span></span>  
 <span data-ttu-id="668b2-142">Pokud zásada události není explicitně definována, zdědí zásady modulu runtime svého nadřazeného prvku.</span><span class="sxs-lookup"><span data-stu-id="668b2-142">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="668b2-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="668b2-143">See also</span></span>

- [<span data-ttu-id="668b2-144">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="668b2-144">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="668b2-145">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="668b2-145">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="668b2-146">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="668b2-146">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
