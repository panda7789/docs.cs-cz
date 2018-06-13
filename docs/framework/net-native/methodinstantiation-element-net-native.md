---
title: Element &lt;MethodInstantiation&gt; (.NET Native)
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d741e8df8f2b8c6d90a1d867c73495a2ffd1304
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397790"
---
# <a name="ltmethodinstantiationgt-element-net-native"></a><span data-ttu-id="d8f61-102">Element &lt;MethodInstantiation&gt; (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="d8f61-102">&lt;MethodInstantiation&gt; Element (.NET Native)</span></span>
<span data-ttu-id="d8f61-103">Sestavené obecné metody se týká zásady reflexe modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="d8f61-103">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8f61-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8f61-104">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8f61-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d8f61-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d8f61-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d8f61-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8f61-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="d8f61-107">Attributes</span></span>  
  
|<span data-ttu-id="d8f61-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="d8f61-108">Attribute</span></span>|<span data-ttu-id="d8f61-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="d8f61-109">Attribute type</span></span>|<span data-ttu-id="d8f61-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d8f61-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="d8f61-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="d8f61-111">General</span></span>|<span data-ttu-id="d8f61-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="d8f61-112">Required attribute.</span></span> <span data-ttu-id="d8f61-113">Určuje název metody.</span><span class="sxs-lookup"><span data-stu-id="d8f61-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="d8f61-114">Obecné</span><span class="sxs-lookup"><span data-stu-id="d8f61-114">General</span></span>|<span data-ttu-id="d8f61-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="d8f61-115">Optional attribute.</span></span> <span data-ttu-id="d8f61-116">Určuje pojmenované parametry metody.</span><span class="sxs-lookup"><span data-stu-id="d8f61-116">Specifies named parameters of the method.</span></span> <span data-ttu-id="d8f61-117">Více pojmenované parametry jsou oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="d8f61-117">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="d8f61-118">`Signature` Atribut se používá k rozlišení přetížené metody.</span><span class="sxs-lookup"><span data-stu-id="d8f61-118">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="d8f61-119">Obecné</span><span class="sxs-lookup"><span data-stu-id="d8f61-119">General</span></span>|<span data-ttu-id="d8f61-120">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="d8f61-120">Required attribute.</span></span> <span data-ttu-id="d8f61-121">Určuje argumenty obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d8f61-121">Specifies the generic type arguments.</span></span> <span data-ttu-id="d8f61-122">Pokud jsou v něm více argumentů, jsou oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="d8f61-122">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="d8f61-123">Reflexe</span><span class="sxs-lookup"><span data-stu-id="d8f61-123">Reflection</span></span>|<span data-ttu-id="d8f61-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="d8f61-124">Optional attribute.</span></span> <span data-ttu-id="d8f61-125">Ovládací prvky dotazování na informace o nebo vytváření výčtu metodu, ale neumožňuje žádné dynamické volání za běhu.</span><span class="sxs-lookup"><span data-stu-id="d8f61-125">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="d8f61-126">Reflexe</span><span class="sxs-lookup"><span data-stu-id="d8f61-126">Reflection</span></span>|<span data-ttu-id="d8f61-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="d8f61-127">Optional attribute.</span></span> <span data-ttu-id="d8f61-128">Ovládací prvky runtime přístup k konstruktor nebo způsob povolení dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="d8f61-128">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="d8f61-129">Tato zásada zajistí, že člena nelze vyvolat dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="d8f61-129">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="d8f61-130">Atribut Name.</span><span class="sxs-lookup"><span data-stu-id="d8f61-130">Name attribute</span></span>  
  
|<span data-ttu-id="d8f61-131">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d8f61-131">Value</span></span>|<span data-ttu-id="d8f61-132">Popis</span><span class="sxs-lookup"><span data-stu-id="d8f61-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d8f61-133">*method_name*</span><span class="sxs-lookup"><span data-stu-id="d8f61-133">*method_name*</span></span>|<span data-ttu-id="d8f61-134">Název metody.</span><span class="sxs-lookup"><span data-stu-id="d8f61-134">The method name.</span></span> <span data-ttu-id="d8f61-135">Typ metody je definován nadřazený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) nebo [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span><span class="sxs-lookup"><span data-stu-id="d8f61-135">The type of the method is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="d8f61-136">Atribut podpisu</span><span class="sxs-lookup"><span data-stu-id="d8f61-136">Signature attribute</span></span>  
  
|<span data-ttu-id="d8f61-137">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d8f61-137">Value</span></span>|<span data-ttu-id="d8f61-138">Popis</span><span class="sxs-lookup"><span data-stu-id="d8f61-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d8f61-139">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="d8f61-139">*method_signature*</span></span>|<span data-ttu-id="d8f61-140">Určuje pojmenované parametry metody.</span><span class="sxs-lookup"><span data-stu-id="d8f61-140">Specifies the named parameters of the method.</span></span> <span data-ttu-id="d8f61-141">Pokud jsou v něm několik parametrů, jsou oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="d8f61-141">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="d8f61-142">Argumenty atributu</span><span class="sxs-lookup"><span data-stu-id="d8f61-142">Arguments attribute</span></span>  
  
|<span data-ttu-id="d8f61-143">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d8f61-143">Value</span></span>|<span data-ttu-id="d8f61-144">Popis</span><span class="sxs-lookup"><span data-stu-id="d8f61-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d8f61-145">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="d8f61-145">*method_arguments*</span></span>|<span data-ttu-id="d8f61-146">Určuje argumenty obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d8f61-146">Specifies the generic type arguments.</span></span> <span data-ttu-id="d8f61-147">Pokud jsou v něm více argumentů, jsou oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="d8f61-147">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="d8f61-148">Každý argument musí obsahovat plně kvalifikovaného názvu.</span><span class="sxs-lookup"><span data-stu-id="d8f61-148">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="d8f61-149">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="d8f61-149">All other attributes</span></span>  
  
|<span data-ttu-id="d8f61-150">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d8f61-150">Value</span></span>|<span data-ttu-id="d8f61-151">Popis</span><span class="sxs-lookup"><span data-stu-id="d8f61-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d8f61-152">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="d8f61-152">*policy_setting*</span></span>|<span data-ttu-id="d8f61-153">Nastavení, které chcete použít pro tento typ zásad pro metodu.</span><span class="sxs-lookup"><span data-stu-id="d8f61-153">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="d8f61-154">Možné hodnoty jsou `Auto`, `Excluded`, `Included`, a `Required`.</span><span class="sxs-lookup"><span data-stu-id="d8f61-154">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="d8f61-155">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="d8f61-155">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8f61-156">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d8f61-156">Child Elements</span></span>  
 <span data-ttu-id="d8f61-157">Žádné</span><span class="sxs-lookup"><span data-stu-id="d8f61-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8f61-158">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d8f61-158">Parent Elements</span></span>  
  
|<span data-ttu-id="d8f61-159">Prvek</span><span class="sxs-lookup"><span data-stu-id="d8f61-159">Element</span></span>|<span data-ttu-id="d8f61-160">Popis</span><span class="sxs-lookup"><span data-stu-id="d8f61-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8f61-161">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="d8f61-161">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="d8f61-162">Reflexe zásada se vztahuje na typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="d8f61-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="d8f61-163">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="d8f61-163">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="d8f61-164">Reflexe zásada se vztahuje na sestavené obecné typy a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="d8f61-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8f61-165">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d8f61-165">Remarks</span></span>  
 <span data-ttu-id="d8f61-166">`<MethodInstantiation>` Element přednost před zásadami reflexe runtime jeho odpovídající otevřete obecné metody.</span><span class="sxs-lookup"><span data-stu-id="d8f61-166">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8f61-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8f61-167">See Also</span></span>  
 [<span data-ttu-id="d8f61-168">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="d8f61-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="d8f61-169">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="d8f61-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="d8f61-170">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="d8f61-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="d8f61-171">\<Metoda > elementu</span><span class="sxs-lookup"><span data-stu-id="d8f61-171">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
