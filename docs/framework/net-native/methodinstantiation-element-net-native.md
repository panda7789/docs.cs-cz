---
title: Element &lt;MethodInstantiation&gt; (.NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 37e3ff3e792b8067b6d9409d799cf6e30350606a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltmethodinstantiationgt-element-net-native"></a><span data-ttu-id="ada47-102">Element &lt;MethodInstantiation&gt; (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="ada47-102">&lt;MethodInstantiation&gt; Element (.NET Native)</span></span>
<span data-ttu-id="ada47-103">Sestavené obecné metody se týká zásady reflexe modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ada47-103">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ada47-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ada47-104">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ada47-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ada47-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ada47-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ada47-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ada47-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="ada47-107">Attributes</span></span>  
  
|<span data-ttu-id="ada47-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="ada47-108">Attribute</span></span>|<span data-ttu-id="ada47-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="ada47-109">Attribute type</span></span>|<span data-ttu-id="ada47-110">Popis</span><span class="sxs-lookup"><span data-stu-id="ada47-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="ada47-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="ada47-111">General</span></span>|<span data-ttu-id="ada47-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="ada47-112">Required attribute.</span></span> <span data-ttu-id="ada47-113">Určuje název metody.</span><span class="sxs-lookup"><span data-stu-id="ada47-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="ada47-114">Obecné</span><span class="sxs-lookup"><span data-stu-id="ada47-114">General</span></span>|<span data-ttu-id="ada47-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ada47-115">Optional attribute.</span></span> <span data-ttu-id="ada47-116">Určuje pojmenované parametry metody.</span><span class="sxs-lookup"><span data-stu-id="ada47-116">Specifies named parameters of the method.</span></span> <span data-ttu-id="ada47-117">Více pojmenované parametry jsou oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="ada47-117">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="ada47-118">`Signature` Atribut se používá k rozlišení přetížené metody.</span><span class="sxs-lookup"><span data-stu-id="ada47-118">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="ada47-119">Obecné</span><span class="sxs-lookup"><span data-stu-id="ada47-119">General</span></span>|<span data-ttu-id="ada47-120">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="ada47-120">Required attribute.</span></span> <span data-ttu-id="ada47-121">Určuje argumenty obecného typu.</span><span class="sxs-lookup"><span data-stu-id="ada47-121">Specifies the generic type arguments.</span></span> <span data-ttu-id="ada47-122">Pokud jsou v něm více argumentů, jsou oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="ada47-122">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="ada47-123">Reflexe</span><span class="sxs-lookup"><span data-stu-id="ada47-123">Reflection</span></span>|<span data-ttu-id="ada47-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ada47-124">Optional attribute.</span></span> <span data-ttu-id="ada47-125">Ovládací prvky dotazování na informace o nebo vytváření výčtu metodu, ale neumožňuje žádné dynamické volání za běhu.</span><span class="sxs-lookup"><span data-stu-id="ada47-125">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="ada47-126">Reflexe</span><span class="sxs-lookup"><span data-stu-id="ada47-126">Reflection</span></span>|<span data-ttu-id="ada47-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ada47-127">Optional attribute.</span></span> <span data-ttu-id="ada47-128">Ovládací prvky runtime přístup k konstruktor nebo způsob povolení dynamické programování.</span><span class="sxs-lookup"><span data-stu-id="ada47-128">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="ada47-129">Tato zásada zajistí, že člena nelze vyvolat dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="ada47-129">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="ada47-130">Atribut Name.</span><span class="sxs-lookup"><span data-stu-id="ada47-130">Name attribute</span></span>  
  
|<span data-ttu-id="ada47-131">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ada47-131">Value</span></span>|<span data-ttu-id="ada47-132">Popis</span><span class="sxs-lookup"><span data-stu-id="ada47-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ada47-133">*method_name*</span><span class="sxs-lookup"><span data-stu-id="ada47-133">*method_name*</span></span>|<span data-ttu-id="ada47-134">Název metody.</span><span class="sxs-lookup"><span data-stu-id="ada47-134">The method name.</span></span> <span data-ttu-id="ada47-135">Typ metody je definován nadřazený [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) nebo [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span><span class="sxs-lookup"><span data-stu-id="ada47-135">The type of the method is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="ada47-136">Atribut podpisu</span><span class="sxs-lookup"><span data-stu-id="ada47-136">Signature attribute</span></span>  
  
|<span data-ttu-id="ada47-137">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ada47-137">Value</span></span>|<span data-ttu-id="ada47-138">Popis</span><span class="sxs-lookup"><span data-stu-id="ada47-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ada47-139">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="ada47-139">*method_signature*</span></span>|<span data-ttu-id="ada47-140">Určuje pojmenované parametry metody.</span><span class="sxs-lookup"><span data-stu-id="ada47-140">Specifies the named parameters of the method.</span></span> <span data-ttu-id="ada47-141">Pokud jsou v něm několik parametrů, jsou oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="ada47-141">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="ada47-142">Argumenty atributu</span><span class="sxs-lookup"><span data-stu-id="ada47-142">Arguments attribute</span></span>  
  
|<span data-ttu-id="ada47-143">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ada47-143">Value</span></span>|<span data-ttu-id="ada47-144">Popis</span><span class="sxs-lookup"><span data-stu-id="ada47-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ada47-145">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="ada47-145">*method_arguments*</span></span>|<span data-ttu-id="ada47-146">Určuje argumenty obecného typu.</span><span class="sxs-lookup"><span data-stu-id="ada47-146">Specifies the generic type arguments.</span></span> <span data-ttu-id="ada47-147">Pokud jsou v něm více argumentů, jsou oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="ada47-147">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="ada47-148">Každý argument musí obsahovat plně kvalifikovaného názvu.</span><span class="sxs-lookup"><span data-stu-id="ada47-148">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="ada47-149">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="ada47-149">All other attributes</span></span>  
  
|<span data-ttu-id="ada47-150">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ada47-150">Value</span></span>|<span data-ttu-id="ada47-151">Popis</span><span class="sxs-lookup"><span data-stu-id="ada47-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ada47-152">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="ada47-152">*policy_setting*</span></span>|<span data-ttu-id="ada47-153">Nastavení, které chcete použít pro tento typ zásad pro metodu.</span><span class="sxs-lookup"><span data-stu-id="ada47-153">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="ada47-154">Možné hodnoty jsou `Auto`, `Excluded`, `Included`, a `Required`.</span><span class="sxs-lookup"><span data-stu-id="ada47-154">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="ada47-155">Další informace najdete v tématu [nastavení zásad direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="ada47-155">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ada47-156">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ada47-156">Child Elements</span></span>  
 <span data-ttu-id="ada47-157">Žádné</span><span class="sxs-lookup"><span data-stu-id="ada47-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ada47-158">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ada47-158">Parent Elements</span></span>  
  
|<span data-ttu-id="ada47-159">Prvek</span><span class="sxs-lookup"><span data-stu-id="ada47-159">Element</span></span>|<span data-ttu-id="ada47-160">Popis</span><span class="sxs-lookup"><span data-stu-id="ada47-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ada47-161">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="ada47-161">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="ada47-162">Reflexe zásada se vztahuje na typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="ada47-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="ada47-163">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="ada47-163">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="ada47-164">Reflexe zásada se vztahuje na sestavené obecné typy a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="ada47-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ada47-165">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ada47-165">Remarks</span></span>  
 <span data-ttu-id="ada47-166">`<MethodInstantiation>` Element přednost před zásadami reflexe runtime jeho odpovídající otevřete obecné metody.</span><span class="sxs-lookup"><span data-stu-id="ada47-166">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ada47-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="ada47-167">See Also</span></span>  
 [<span data-ttu-id="ada47-168">Odkaz na soubor konfigurace modulu runtime direktivy (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="ada47-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="ada47-169">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="ada47-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="ada47-170">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="ada47-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="ada47-171">\<Metoda > elementu</span><span class="sxs-lookup"><span data-stu-id="ada47-171">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
