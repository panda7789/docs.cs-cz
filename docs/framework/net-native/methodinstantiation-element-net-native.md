---
title: <MethodInstantiation> – Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae15e6d61267feb0388170ee27dcd939035329b0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61867078"
---
# <a name="methodinstantiation-element-net-native"></a><span data-ttu-id="07457-102">\<MethodInstantiation > – Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="07457-102">\<MethodInstantiation> Element (.NET Native)</span></span>
<span data-ttu-id="07457-103">Použije zásady reflexe runtime konstruovanou obecnou metodu.</span><span class="sxs-lookup"><span data-stu-id="07457-103">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07457-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07457-104">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07457-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="07457-105">Attributes and Elements</span></span>  
 <span data-ttu-id="07457-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="07457-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07457-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="07457-107">Attributes</span></span>  
  
|<span data-ttu-id="07457-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="07457-108">Attribute</span></span>|<span data-ttu-id="07457-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="07457-109">Attribute type</span></span>|<span data-ttu-id="07457-110">Popis</span><span class="sxs-lookup"><span data-stu-id="07457-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="07457-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="07457-111">General</span></span>|<span data-ttu-id="07457-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="07457-112">Required attribute.</span></span> <span data-ttu-id="07457-113">Určuje název metody.</span><span class="sxs-lookup"><span data-stu-id="07457-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="07457-114">Obecné</span><span class="sxs-lookup"><span data-stu-id="07457-114">General</span></span>|<span data-ttu-id="07457-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="07457-115">Optional attribute.</span></span> <span data-ttu-id="07457-116">Určuje pojmenované parametry metody.</span><span class="sxs-lookup"><span data-stu-id="07457-116">Specifies named parameters of the method.</span></span> <span data-ttu-id="07457-117">Více pojmenované parametry jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="07457-117">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="07457-118">`Signature` Atribut se používá k rozlišení přetížené metody.</span><span class="sxs-lookup"><span data-stu-id="07457-118">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="07457-119">Obecné</span><span class="sxs-lookup"><span data-stu-id="07457-119">General</span></span>|<span data-ttu-id="07457-120">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="07457-120">Required attribute.</span></span> <span data-ttu-id="07457-121">Určuje argumenty obecného typu.</span><span class="sxs-lookup"><span data-stu-id="07457-121">Specifies the generic type arguments.</span></span> <span data-ttu-id="07457-122">Pokud je více argumentů, jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="07457-122">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="07457-123">Reflexe</span><span class="sxs-lookup"><span data-stu-id="07457-123">Reflection</span></span>|<span data-ttu-id="07457-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="07457-124">Optional attribute.</span></span> <span data-ttu-id="07457-125">Ovládací prvky dotazování na informace o nebo vytváření výčtu metody, ale nepovolí všechny dynamické vyvolání za běhu.</span><span class="sxs-lookup"><span data-stu-id="07457-125">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="07457-126">Reflexe</span><span class="sxs-lookup"><span data-stu-id="07457-126">Reflection</span></span>|<span data-ttu-id="07457-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="07457-127">Optional attribute.</span></span> <span data-ttu-id="07457-128">Ovládací prvky runtime přístup k konstruktoru nebo metody, které chcete povolit dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="07457-128">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="07457-129">Tato zásada zajistí, že člen může být vyvolána dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="07457-129">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="07457-130">Název atributu</span><span class="sxs-lookup"><span data-stu-id="07457-130">Name attribute</span></span>  
  
|<span data-ttu-id="07457-131">Value</span><span class="sxs-lookup"><span data-stu-id="07457-131">Value</span></span>|<span data-ttu-id="07457-132">Popis</span><span class="sxs-lookup"><span data-stu-id="07457-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="07457-133">*method_name*</span><span class="sxs-lookup"><span data-stu-id="07457-133">*method_name*</span></span>|<span data-ttu-id="07457-134">Název metody.</span><span class="sxs-lookup"><span data-stu-id="07457-134">The method name.</span></span> <span data-ttu-id="07457-135">Typ metody je definován nadřazený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) nebo [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="07457-135">The type of the method is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="07457-136">Atribut podpisu</span><span class="sxs-lookup"><span data-stu-id="07457-136">Signature attribute</span></span>  
  
|<span data-ttu-id="07457-137">Value</span><span class="sxs-lookup"><span data-stu-id="07457-137">Value</span></span>|<span data-ttu-id="07457-138">Popis</span><span class="sxs-lookup"><span data-stu-id="07457-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="07457-139">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="07457-139">*method_signature*</span></span>|<span data-ttu-id="07457-140">Určuje pojmenované parametry metody.</span><span class="sxs-lookup"><span data-stu-id="07457-140">Specifies the named parameters of the method.</span></span> <span data-ttu-id="07457-141">Pokud více parametrů jsou k dispozici, jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="07457-141">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="07457-142">Argumenty atributu</span><span class="sxs-lookup"><span data-stu-id="07457-142">Arguments attribute</span></span>  
  
|<span data-ttu-id="07457-143">Value</span><span class="sxs-lookup"><span data-stu-id="07457-143">Value</span></span>|<span data-ttu-id="07457-144">Popis</span><span class="sxs-lookup"><span data-stu-id="07457-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="07457-145">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="07457-145">*method_arguments*</span></span>|<span data-ttu-id="07457-146">Určuje argumenty obecného typu.</span><span class="sxs-lookup"><span data-stu-id="07457-146">Specifies the generic type arguments.</span></span> <span data-ttu-id="07457-147">Pokud je více argumentů, jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="07457-147">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="07457-148">Každý argument musí obsahovat plně kvalifikovaného názvu.</span><span class="sxs-lookup"><span data-stu-id="07457-148">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="07457-149">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="07457-149">All other attributes</span></span>  
  
|<span data-ttu-id="07457-150">Hodnota</span><span class="sxs-lookup"><span data-stu-id="07457-150">Value</span></span>|<span data-ttu-id="07457-151">Popis</span><span class="sxs-lookup"><span data-stu-id="07457-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="07457-152">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="07457-152">*policy_setting*</span></span>|<span data-ttu-id="07457-153">Toto nastavení platí pro tento typ zásad pro metodu.</span><span class="sxs-lookup"><span data-stu-id="07457-153">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="07457-154">Možné hodnoty jsou `Auto`, `Excluded`, `Included`, a `Required`.</span><span class="sxs-lookup"><span data-stu-id="07457-154">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="07457-155">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="07457-155">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="07457-156">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="07457-156">Child Elements</span></span>  
 <span data-ttu-id="07457-157">Žádné</span><span class="sxs-lookup"><span data-stu-id="07457-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="07457-158">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="07457-158">Parent Elements</span></span>  
  
|<span data-ttu-id="07457-159">Prvek</span><span class="sxs-lookup"><span data-stu-id="07457-159">Element</span></span>|<span data-ttu-id="07457-160">Popis</span><span class="sxs-lookup"><span data-stu-id="07457-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="07457-161">\<Type></span><span class="sxs-lookup"><span data-stu-id="07457-161">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="07457-162">Použije zásady reflexe pro typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="07457-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="07457-163">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="07457-163">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="07457-164">Použije zásady reflexe pro Konstruovaný obecný typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="07457-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07457-165">Poznámky</span><span class="sxs-lookup"><span data-stu-id="07457-165">Remarks</span></span>  
 <span data-ttu-id="07457-166">`<MethodInstantiation>` Prvek přepisuje zásady reflexe modulu runtime jeho odpovídající otevřít obecné metody.</span><span class="sxs-lookup"><span data-stu-id="07457-166">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07457-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="07457-167">See also</span></span>

- [<span data-ttu-id="07457-168">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="07457-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="07457-169">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="07457-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="07457-170">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="07457-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [<span data-ttu-id="07457-171">\<Metoda > – Element</span><span class="sxs-lookup"><span data-stu-id="07457-171">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
