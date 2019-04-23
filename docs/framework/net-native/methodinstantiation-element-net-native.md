---
title: <MethodInstantiation> – Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae15e6d61267feb0388170ee27dcd939035329b0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121690"
---
# <a name="methodinstantiation-element-net-native"></a><span data-ttu-id="46b4c-102">\<MethodInstantiation > – Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="46b4c-102">\<MethodInstantiation> Element (.NET Native)</span></span>
<span data-ttu-id="46b4c-103">Použije zásady reflexe runtime konstruovanou obecnou metodu.</span><span class="sxs-lookup"><span data-stu-id="46b4c-103">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46b4c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46b4c-104">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46b4c-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="46b4c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="46b4c-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="46b4c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46b4c-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="46b4c-107">Attributes</span></span>  
  
|<span data-ttu-id="46b4c-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="46b4c-108">Attribute</span></span>|<span data-ttu-id="46b4c-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="46b4c-109">Attribute type</span></span>|<span data-ttu-id="46b4c-110">Popis</span><span class="sxs-lookup"><span data-stu-id="46b4c-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="46b4c-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="46b4c-111">General</span></span>|<span data-ttu-id="46b4c-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="46b4c-112">Required attribute.</span></span> <span data-ttu-id="46b4c-113">Určuje název metody.</span><span class="sxs-lookup"><span data-stu-id="46b4c-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="46b4c-114">Obecné</span><span class="sxs-lookup"><span data-stu-id="46b4c-114">General</span></span>|<span data-ttu-id="46b4c-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="46b4c-115">Optional attribute.</span></span> <span data-ttu-id="46b4c-116">Určuje pojmenované parametry metody.</span><span class="sxs-lookup"><span data-stu-id="46b4c-116">Specifies named parameters of the method.</span></span> <span data-ttu-id="46b4c-117">Více pojmenované parametry jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="46b4c-117">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="46b4c-118">`Signature` Atribut se používá k rozlišení přetížené metody.</span><span class="sxs-lookup"><span data-stu-id="46b4c-118">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="46b4c-119">Obecné</span><span class="sxs-lookup"><span data-stu-id="46b4c-119">General</span></span>|<span data-ttu-id="46b4c-120">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="46b4c-120">Required attribute.</span></span> <span data-ttu-id="46b4c-121">Určuje argumenty obecného typu.</span><span class="sxs-lookup"><span data-stu-id="46b4c-121">Specifies the generic type arguments.</span></span> <span data-ttu-id="46b4c-122">Pokud je více argumentů, jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="46b4c-122">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="46b4c-123">Reflexe</span><span class="sxs-lookup"><span data-stu-id="46b4c-123">Reflection</span></span>|<span data-ttu-id="46b4c-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="46b4c-124">Optional attribute.</span></span> <span data-ttu-id="46b4c-125">Ovládací prvky dotazování na informace o nebo vytváření výčtu metody, ale nepovolí všechny dynamické vyvolání za běhu.</span><span class="sxs-lookup"><span data-stu-id="46b4c-125">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="46b4c-126">Reflexe</span><span class="sxs-lookup"><span data-stu-id="46b4c-126">Reflection</span></span>|<span data-ttu-id="46b4c-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="46b4c-127">Optional attribute.</span></span> <span data-ttu-id="46b4c-128">Ovládací prvky runtime přístup k konstruktoru nebo metody, které chcete povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="46b4c-128">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="46b4c-129">Tato zásada zajistí, že člen může být vyvolána dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="46b4c-129">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="46b4c-130">Název atributu</span><span class="sxs-lookup"><span data-stu-id="46b4c-130">Name attribute</span></span>  
  
|<span data-ttu-id="46b4c-131">Value</span><span class="sxs-lookup"><span data-stu-id="46b4c-131">Value</span></span>|<span data-ttu-id="46b4c-132">Popis</span><span class="sxs-lookup"><span data-stu-id="46b4c-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="46b4c-133">*method_name*</span><span class="sxs-lookup"><span data-stu-id="46b4c-133">*method_name*</span></span>|<span data-ttu-id="46b4c-134">Název metody.</span><span class="sxs-lookup"><span data-stu-id="46b4c-134">The method name.</span></span> <span data-ttu-id="46b4c-135">Typ metody je definován nadřazený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) nebo [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="46b4c-135">The type of the method is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="46b4c-136">Atribut podpisu</span><span class="sxs-lookup"><span data-stu-id="46b4c-136">Signature attribute</span></span>  
  
|<span data-ttu-id="46b4c-137">Value</span><span class="sxs-lookup"><span data-stu-id="46b4c-137">Value</span></span>|<span data-ttu-id="46b4c-138">Popis</span><span class="sxs-lookup"><span data-stu-id="46b4c-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="46b4c-139">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="46b4c-139">*method_signature*</span></span>|<span data-ttu-id="46b4c-140">Určuje pojmenované parametry metody.</span><span class="sxs-lookup"><span data-stu-id="46b4c-140">Specifies the named parameters of the method.</span></span> <span data-ttu-id="46b4c-141">Pokud více parametrů jsou k dispozici, jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="46b4c-141">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="46b4c-142">Argumenty atributu</span><span class="sxs-lookup"><span data-stu-id="46b4c-142">Arguments attribute</span></span>  
  
|<span data-ttu-id="46b4c-143">Value</span><span class="sxs-lookup"><span data-stu-id="46b4c-143">Value</span></span>|<span data-ttu-id="46b4c-144">Popis</span><span class="sxs-lookup"><span data-stu-id="46b4c-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="46b4c-145">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="46b4c-145">*method_arguments*</span></span>|<span data-ttu-id="46b4c-146">Určuje argumenty obecného typu.</span><span class="sxs-lookup"><span data-stu-id="46b4c-146">Specifies the generic type arguments.</span></span> <span data-ttu-id="46b4c-147">Pokud je více argumentů, jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="46b4c-147">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="46b4c-148">Každý argument musí obsahovat plně kvalifikovaného názvu.</span><span class="sxs-lookup"><span data-stu-id="46b4c-148">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="46b4c-149">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="46b4c-149">All other attributes</span></span>  
  
|<span data-ttu-id="46b4c-150">Value</span><span class="sxs-lookup"><span data-stu-id="46b4c-150">Value</span></span>|<span data-ttu-id="46b4c-151">Popis</span><span class="sxs-lookup"><span data-stu-id="46b4c-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="46b4c-152">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="46b4c-152">*policy_setting*</span></span>|<span data-ttu-id="46b4c-153">Toto nastavení platí pro tento typ zásad pro metodu.</span><span class="sxs-lookup"><span data-stu-id="46b4c-153">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="46b4c-154">Možné hodnoty jsou `Auto`, `Excluded`, `Included`, a `Required`.</span><span class="sxs-lookup"><span data-stu-id="46b4c-154">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="46b4c-155">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="46b4c-155">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46b4c-156">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="46b4c-156">Child Elements</span></span>  
 <span data-ttu-id="46b4c-157">Žádné</span><span class="sxs-lookup"><span data-stu-id="46b4c-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="46b4c-158">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="46b4c-158">Parent Elements</span></span>  
  
|<span data-ttu-id="46b4c-159">Prvek</span><span class="sxs-lookup"><span data-stu-id="46b4c-159">Element</span></span>|<span data-ttu-id="46b4c-160">Popis</span><span class="sxs-lookup"><span data-stu-id="46b4c-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="46b4c-161">\<Type></span><span class="sxs-lookup"><span data-stu-id="46b4c-161">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="46b4c-162">Použije zásady reflexe pro typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="46b4c-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="46b4c-163">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="46b4c-163">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="46b4c-164">Použije zásady reflexe pro Konstruovaný obecný typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="46b4c-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46b4c-165">Poznámky</span><span class="sxs-lookup"><span data-stu-id="46b4c-165">Remarks</span></span>  
 <span data-ttu-id="46b4c-166">`<MethodInstantiation>` Prvek přepisuje zásady reflexe modulu runtime jeho odpovídající otevřít obecné metody.</span><span class="sxs-lookup"><span data-stu-id="46b4c-166">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46b4c-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46b4c-167">See also</span></span>

- [<span data-ttu-id="46b4c-168">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="46b4c-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="46b4c-169">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="46b4c-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="46b4c-170">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="46b4c-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [<span data-ttu-id="46b4c-171">\<Metoda > – Element</span><span class="sxs-lookup"><span data-stu-id="46b4c-171">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
