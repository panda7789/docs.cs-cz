---
title: <MethodInstantiation> – element (.NET Native)
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
ms.openlocfilehash: f19bd3c20088431bcbbafac298398b82a664bee9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128330"
---
# <a name="methodinstantiation-element-net-native"></a><span data-ttu-id="ec256-102">\<element > MethodInstantiation (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="ec256-102">\<MethodInstantiation> Element (.NET Native)</span></span>
<span data-ttu-id="ec256-103">Aplikuje zásady reflexe modulu runtime na vytvořenou obecnou metodu.</span><span class="sxs-lookup"><span data-stu-id="ec256-103">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec256-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec256-104">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec256-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ec256-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ec256-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ec256-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec256-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="ec256-107">Attributes</span></span>  
  
|<span data-ttu-id="ec256-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="ec256-108">Attribute</span></span>|<span data-ttu-id="ec256-109">Typ atributu</span><span class="sxs-lookup"><span data-stu-id="ec256-109">Attribute type</span></span>|<span data-ttu-id="ec256-110">Popis</span><span class="sxs-lookup"><span data-stu-id="ec256-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="ec256-111">Obecné</span><span class="sxs-lookup"><span data-stu-id="ec256-111">General</span></span>|<span data-ttu-id="ec256-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="ec256-112">Required attribute.</span></span> <span data-ttu-id="ec256-113">Určuje název metody.</span><span class="sxs-lookup"><span data-stu-id="ec256-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="ec256-114">Obecné</span><span class="sxs-lookup"><span data-stu-id="ec256-114">General</span></span>|<span data-ttu-id="ec256-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ec256-115">Optional attribute.</span></span> <span data-ttu-id="ec256-116">Určuje pojmenované parametry metody.</span><span class="sxs-lookup"><span data-stu-id="ec256-116">Specifies named parameters of the method.</span></span> <span data-ttu-id="ec256-117">Více pojmenovaných parametrů je odděleno čárkami.</span><span class="sxs-lookup"><span data-stu-id="ec256-117">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="ec256-118">Atribut `Signature` slouží k odlišení přetížených metod.</span><span class="sxs-lookup"><span data-stu-id="ec256-118">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="ec256-119">Obecné</span><span class="sxs-lookup"><span data-stu-id="ec256-119">General</span></span>|<span data-ttu-id="ec256-120">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="ec256-120">Required attribute.</span></span> <span data-ttu-id="ec256-121">Určuje argumenty obecného typu.</span><span class="sxs-lookup"><span data-stu-id="ec256-121">Specifies the generic type arguments.</span></span> <span data-ttu-id="ec256-122">Pokud je přítomno více argumentů, jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="ec256-122">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="ec256-123">Reflexe</span><span class="sxs-lookup"><span data-stu-id="ec256-123">Reflection</span></span>|<span data-ttu-id="ec256-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ec256-124">Optional attribute.</span></span> <span data-ttu-id="ec256-125">Řídí dotazování na informace o nebo výčet metody, ale neumožňuje žádné dynamické vyvolání za běhu.</span><span class="sxs-lookup"><span data-stu-id="ec256-125">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="ec256-126">Reflexe</span><span class="sxs-lookup"><span data-stu-id="ec256-126">Reflection</span></span>|<span data-ttu-id="ec256-127">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ec256-127">Optional attribute.</span></span> <span data-ttu-id="ec256-128">Řídí přístup za běhu k konstruktoru nebo metodě pro povolení dynamického programování.</span><span class="sxs-lookup"><span data-stu-id="ec256-128">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="ec256-129">Tato zásada zajišťuje, že člen může být v době běhu vyvolán dynamicky.</span><span class="sxs-lookup"><span data-stu-id="ec256-129">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="ec256-130">Atribut Name</span><span class="sxs-lookup"><span data-stu-id="ec256-130">Name attribute</span></span>  
  
|<span data-ttu-id="ec256-131">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ec256-131">Value</span></span>|<span data-ttu-id="ec256-132">Popis</span><span class="sxs-lookup"><span data-stu-id="ec256-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ec256-133">*method_name*</span><span class="sxs-lookup"><span data-stu-id="ec256-133">*method_name*</span></span>|<span data-ttu-id="ec256-134">Název metody.</span><span class="sxs-lookup"><span data-stu-id="ec256-134">The method name.</span></span> <span data-ttu-id="ec256-135">Typ metody je definován nadřazeným [\<typem >](type-element-net-native.md) nebo [\<elementu > TypeInstantiation](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="ec256-135">The type of the method is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="ec256-136">Atribut podpisu</span><span class="sxs-lookup"><span data-stu-id="ec256-136">Signature attribute</span></span>  
  
|<span data-ttu-id="ec256-137">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ec256-137">Value</span></span>|<span data-ttu-id="ec256-138">Popis</span><span class="sxs-lookup"><span data-stu-id="ec256-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ec256-139">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="ec256-139">*method_signature*</span></span>|<span data-ttu-id="ec256-140">Určuje pojmenované parametry metody.</span><span class="sxs-lookup"><span data-stu-id="ec256-140">Specifies the named parameters of the method.</span></span> <span data-ttu-id="ec256-141">Pokud je přítomno více parametrů, jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="ec256-141">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="ec256-142">Arguments – atribut</span><span class="sxs-lookup"><span data-stu-id="ec256-142">Arguments attribute</span></span>  
  
|<span data-ttu-id="ec256-143">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ec256-143">Value</span></span>|<span data-ttu-id="ec256-144">Popis</span><span class="sxs-lookup"><span data-stu-id="ec256-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ec256-145">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="ec256-145">*method_arguments*</span></span>|<span data-ttu-id="ec256-146">Určuje argumenty obecného typu.</span><span class="sxs-lookup"><span data-stu-id="ec256-146">Specifies the generic type arguments.</span></span> <span data-ttu-id="ec256-147">Pokud je přítomno více argumentů, jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="ec256-147">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="ec256-148">Každý argument musí obsahovat plně kvalifikovaný název typu.</span><span class="sxs-lookup"><span data-stu-id="ec256-148">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="ec256-149">Všechny ostatní atributy</span><span class="sxs-lookup"><span data-stu-id="ec256-149">All other attributes</span></span>  
  
|<span data-ttu-id="ec256-150">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ec256-150">Value</span></span>|<span data-ttu-id="ec256-151">Popis</span><span class="sxs-lookup"><span data-stu-id="ec256-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ec256-152">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="ec256-152">*policy_setting*</span></span>|<span data-ttu-id="ec256-153">Nastavení, které se má použít pro tento typ zásad pro metodu.</span><span class="sxs-lookup"><span data-stu-id="ec256-153">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="ec256-154">Možné hodnoty jsou `Auto`, `Excluded`, `Included`a `Required`.</span><span class="sxs-lookup"><span data-stu-id="ec256-154">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="ec256-155">Další informace najdete v tématu [nastavení zásad direktivy modulu runtime](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="ec256-155">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ec256-156">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ec256-156">Child Elements</span></span>  
 <span data-ttu-id="ec256-157">Žádné</span><span class="sxs-lookup"><span data-stu-id="ec256-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ec256-158">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ec256-158">Parent Elements</span></span>  
  
|<span data-ttu-id="ec256-159">Prvek</span><span class="sxs-lookup"><span data-stu-id="ec256-159">Element</span></span>|<span data-ttu-id="ec256-160">Popis</span><span class="sxs-lookup"><span data-stu-id="ec256-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec256-161">Typ\<</span><span class="sxs-lookup"><span data-stu-id="ec256-161">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="ec256-162">Aplikuje zásadu odrazu na typ a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="ec256-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="ec256-163">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="ec256-163">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="ec256-164">Aplikuje zásadu odrazu na konstruovaný obecný typ a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="ec256-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec256-165">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ec256-165">Remarks</span></span>  
 <span data-ttu-id="ec256-166">Element `<MethodInstantiation>` Přepisuje zásady reflexe modulu runtime příslušné otevřené obecné metody.</span><span class="sxs-lookup"><span data-stu-id="ec256-166">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec256-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec256-167">See also</span></span>

- [<span data-ttu-id="ec256-168">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="ec256-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="ec256-169">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="ec256-169">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="ec256-170">Nastavení zásad direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="ec256-170">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="ec256-171">\<> – element metody</span><span class="sxs-lookup"><span data-stu-id="ec256-171">\<Method> Element</span></span>](method-element-net-native.md)
