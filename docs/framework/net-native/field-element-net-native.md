---
title: <Field>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
ms.openlocfilehash: 2a63b88c399a999cd00750dee1614352cea10e80
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128423"
---
# <a name="field-element-net-native"></a><span data-ttu-id="8701e-102">\<Field>– Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="8701e-102">\<Field> Element (.NET Native)</span></span>
<span data-ttu-id="8701e-103">Aplikuje na pole zásady reflexe modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="8701e-103">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8701e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8701e-104">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8701e-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8701e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8701e-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8701e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8701e-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="8701e-107">Attributes</span></span>  
  
|<span data-ttu-id="8701e-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="8701e-108">Attribute</span></span>|<span data-ttu-id="8701e-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="8701e-109">Attribute type</span></span>|<span data-ttu-id="8701e-110">Description</span><span class="sxs-lookup"><span data-stu-id="8701e-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="8701e-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="8701e-111">General</span></span>|<span data-ttu-id="8701e-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="8701e-112">Required attribute.</span></span> <span data-ttu-id="8701e-113">Určuje název pole.</span><span class="sxs-lookup"><span data-stu-id="8701e-113">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="8701e-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="8701e-114">Reflection</span></span>|<span data-ttu-id="8701e-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="8701e-115">Optional attribute.</span></span> <span data-ttu-id="8701e-116">Řídí dotazování na informace o nebo výčet pole, ale nepovoluje žádný dynamický přístup v době běhu.</span><span class="sxs-lookup"><span data-stu-id="8701e-116">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="8701e-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="8701e-117">Reflection</span></span>|<span data-ttu-id="8701e-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="8701e-118">Optional attribute.</span></span> <span data-ttu-id="8701e-119">Řídí přístup za běhu k poli pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="8701e-119">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="8701e-120">Tato zásada zajišťuje, že pole lze v době běhu nastavit nebo načíst dynamicky.</span><span class="sxs-lookup"><span data-stu-id="8701e-120">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="8701e-121">Serializace</span><span class="sxs-lookup"><span data-stu-id="8701e-121">Serialization</span></span>|<span data-ttu-id="8701e-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="8701e-122">Optional attribute.</span></span> <span data-ttu-id="8701e-123">Řídí přístup za běhu k poli, aby se mohly instance typů serializovat pomocí knihoven, jako je Newtonsoft JSON serializátor nebo který se má použít pro datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="8701e-123">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="8701e-124">Atribut Name</span><span class="sxs-lookup"><span data-stu-id="8701e-124">Name attribute</span></span>  
  
|<span data-ttu-id="8701e-125">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8701e-125">Value</span></span>|<span data-ttu-id="8701e-126">Description</span><span class="sxs-lookup"><span data-stu-id="8701e-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8701e-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="8701e-127">*method_name*</span></span>|<span data-ttu-id="8701e-128">Název pole</span><span class="sxs-lookup"><span data-stu-id="8701e-128">The field name.</span></span> <span data-ttu-id="8701e-129">Typ pole je definován nadřazeným [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) prvkem nebo prvkem.</span><span class="sxs-lookup"><span data-stu-id="8701e-129">The type of the field is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="8701e-130">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="8701e-130">All other attributes</span></span>  
  
|<span data-ttu-id="8701e-131">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8701e-131">Value</span></span>|<span data-ttu-id="8701e-132">Description</span><span class="sxs-lookup"><span data-stu-id="8701e-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8701e-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="8701e-133">*policy_setting*</span></span>|<span data-ttu-id="8701e-134">Nastavení, které se má použít pro tento typ zásad pro pole</span><span class="sxs-lookup"><span data-stu-id="8701e-134">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="8701e-135">Možné hodnoty jsou `Auto` , `Excluded` , `Included` a `Required` .</span><span class="sxs-lookup"><span data-stu-id="8701e-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="8701e-136">Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="8701e-136">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8701e-137">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8701e-137">Child Elements</span></span>  
 <span data-ttu-id="8701e-138">Žádné</span><span class="sxs-lookup"><span data-stu-id="8701e-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8701e-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8701e-139">Parent Elements</span></span>  
  
|<span data-ttu-id="8701e-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="8701e-140">Element</span></span>|<span data-ttu-id="8701e-141">Description</span><span class="sxs-lookup"><span data-stu-id="8701e-141">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="8701e-142">Aplikuje zásadu odrazu na typ a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="8701e-142">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="8701e-143">Aplikuje zásadu odrazu na konstruovaný obecný typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="8701e-143">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8701e-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8701e-144">Remarks</span></span>  
 <span data-ttu-id="8701e-145">Pokud zásady pole nejsou explicitně definovány, zdědí zásady modulu runtime svého nadřazeného prvku.</span><span class="sxs-lookup"><span data-stu-id="8701e-145">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8701e-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="8701e-146">See also</span></span>

- [<span data-ttu-id="8701e-147">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="8701e-147">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="8701e-148">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="8701e-148">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="8701e-149">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="8701e-149">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
