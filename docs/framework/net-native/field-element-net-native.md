---
title: <Field> – Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c58be27334bcb862367464475a4eade5e01bdbb2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61868532"
---
# <a name="field-element-net-native"></a><span data-ttu-id="2861e-102">\<Pole > – Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="2861e-102">\<Field> Element (.NET Native)</span></span>
<span data-ttu-id="2861e-103">Použije zásady reflexe runtime pole.</span><span class="sxs-lookup"><span data-stu-id="2861e-103">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2861e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2861e-104">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2861e-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2861e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2861e-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2861e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2861e-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="2861e-107">Attributes</span></span>  
  
|<span data-ttu-id="2861e-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="2861e-108">Attribute</span></span>|<span data-ttu-id="2861e-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="2861e-109">Attribute type</span></span>|<span data-ttu-id="2861e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="2861e-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="2861e-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="2861e-111">General</span></span>|<span data-ttu-id="2861e-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="2861e-112">Required attribute.</span></span> <span data-ttu-id="2861e-113">Určuje název pole.</span><span class="sxs-lookup"><span data-stu-id="2861e-113">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="2861e-114">Reflexe</span><span class="sxs-lookup"><span data-stu-id="2861e-114">Reflection</span></span>|<span data-ttu-id="2861e-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="2861e-115">Optional attribute.</span></span> <span data-ttu-id="2861e-116">Ovládací prvky dotazování na informace o nebo vytváření výčtu pole, ale neumožňuje dynamické přístup za běhu.</span><span class="sxs-lookup"><span data-stu-id="2861e-116">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="2861e-117">Reflexe</span><span class="sxs-lookup"><span data-stu-id="2861e-117">Reflection</span></span>|<span data-ttu-id="2861e-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="2861e-118">Optional attribute.</span></span> <span data-ttu-id="2861e-119">Ovládací prvky runtime přístup k poli Povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="2861e-119">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="2861e-120">Tato zásada zajistí, že pole můžete nastavit nebo načíst dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="2861e-120">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="2861e-121">Serializace</span><span class="sxs-lookup"><span data-stu-id="2861e-121">Serialization</span></span>|<span data-ttu-id="2861e-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="2861e-122">Optional attribute.</span></span> <span data-ttu-id="2861e-123">Určuje runtime přístup do pole, které chcete povolit instance typu bylo serializováno modulem knihoven, jako je například serializátor Newtonsoft JSON nebo má být použit pro vytváření datových vazeb.</span><span class="sxs-lookup"><span data-stu-id="2861e-123">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="2861e-124">Název atributu</span><span class="sxs-lookup"><span data-stu-id="2861e-124">Name attribute</span></span>  
  
|<span data-ttu-id="2861e-125">Value</span><span class="sxs-lookup"><span data-stu-id="2861e-125">Value</span></span>|<span data-ttu-id="2861e-126">Popis</span><span class="sxs-lookup"><span data-stu-id="2861e-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2861e-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="2861e-127">*method_name*</span></span>|<span data-ttu-id="2861e-128">Název pole.</span><span class="sxs-lookup"><span data-stu-id="2861e-128">The field name.</span></span> <span data-ttu-id="2861e-129">Typ pole je definován nadřazený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) nebo [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="2861e-129">The type of the field is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="2861e-130">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="2861e-130">All other attributes</span></span>  
  
|<span data-ttu-id="2861e-131">Value</span><span class="sxs-lookup"><span data-stu-id="2861e-131">Value</span></span>|<span data-ttu-id="2861e-132">Popis</span><span class="sxs-lookup"><span data-stu-id="2861e-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2861e-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="2861e-133">*policy_setting*</span></span>|<span data-ttu-id="2861e-134">Toto nastavení platí pro tento typ zásad pole.</span><span class="sxs-lookup"><span data-stu-id="2861e-134">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="2861e-135">Možné hodnoty jsou `Auto`, `Excluded`, `Included`, a `Required`.</span><span class="sxs-lookup"><span data-stu-id="2861e-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="2861e-136">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="2861e-136">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2861e-137">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2861e-137">Child Elements</span></span>  
 <span data-ttu-id="2861e-138">Žádné</span><span class="sxs-lookup"><span data-stu-id="2861e-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2861e-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2861e-139">Parent Elements</span></span>  
  
|<span data-ttu-id="2861e-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="2861e-140">Element</span></span>|<span data-ttu-id="2861e-141">Popis</span><span class="sxs-lookup"><span data-stu-id="2861e-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2861e-142">\<Type></span><span class="sxs-lookup"><span data-stu-id="2861e-142">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="2861e-143">Použije zásady reflexe pro typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="2861e-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="2861e-144">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="2861e-144">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="2861e-145">Použije zásady reflexe pro Konstruovaný obecný typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="2861e-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2861e-146">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2861e-146">Remarks</span></span>  
 <span data-ttu-id="2861e-147">Pokud nejsou výslovně definované zásady polí, dědí zásady modulu runtime objektů svého nadřízeného elementu.</span><span class="sxs-lookup"><span data-stu-id="2861e-147">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2861e-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2861e-148">See also</span></span>

- [<span data-ttu-id="2861e-149">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="2861e-149">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="2861e-150">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="2861e-150">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="2861e-151">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="2861e-151">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
