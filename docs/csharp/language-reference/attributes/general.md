---
title: 'C# vyhrazené atributy: Podmíněné, Zastaralé, AttributeUsage'
ms.date: 04/09/2020
description: Tyto atributy jsou interpretovány kompilátorem ovlivnit kód generovaný kompilátorem
ms.openlocfilehash: c6d697dd08233ffc88900949998047137ee170a9
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021763"
---
# <a name="reserved-attributes-conditionalattribute-obsoleteattribute-attributeusageattribute"></a><span data-ttu-id="3dce3-103">Vyhrazené atributy: ConditionalAttribute, ObsoleteAttribute, AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="3dce3-103">Reserved attributes: ConditionalAttribute, ObsoleteAttribute, AttributeUsageAttribute</span></span>

<span data-ttu-id="3dce3-104">Tyto atributy lze použít na prvky v kódu.</span><span class="sxs-lookup"><span data-stu-id="3dce3-104">These attributes can be applied to elements in your code.</span></span> <span data-ttu-id="3dce3-105">Přidávají těmto prvkům sémantický význam.</span><span class="sxs-lookup"><span data-stu-id="3dce3-105">They add semantic meaning to those elements.</span></span> <span data-ttu-id="3dce3-106">Kompilátor používá tyto sémantické významy změnit svůj výstup a sestavy možných chyb vývojáři pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="3dce3-106">The compiler uses those semantic meanings to alter its output and report possible mistakes by developers using your code.</span></span>

## <a name="conditional-attribute"></a><span data-ttu-id="3dce3-107">Atribut `Conditional`</span><span class="sxs-lookup"><span data-stu-id="3dce3-107">`Conditional` attribute</span></span>

<span data-ttu-id="3dce3-108">Atribut `Conditional` umožňuje provádění metody závislé na identifikátor předběžného zpracování.</span><span class="sxs-lookup"><span data-stu-id="3dce3-108">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="3dce3-109">Atribut `Conditional` je alias <xref:System.Diagnostics.ConditionalAttribute>pro aplikaci a lze jej použít na metodu nebo třídu atributu.</span><span class="sxs-lookup"><span data-stu-id="3dce3-109">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>

<span data-ttu-id="3dce3-110">V následujícím příkladu `Conditional` se používá metoda povolení nebo zakázání zobrazení diagnostických informací specifických pro program:</span><span class="sxs-lookup"><span data-stu-id="3dce3-110">In the following example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>

:::code language="csharp" source="snippets/trace.cs" interactive="try-dotnet" :::

<span data-ttu-id="3dce3-111">Pokud `TRACE_ON` identifikátor není definován, výstup trasování se nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="3dce3-111">If the `TRACE_ON` identifier isn't defined, the trace output isn't displayed.</span></span> <span data-ttu-id="3dce3-112">Prozkoumejte sami v interaktivním okně.</span><span class="sxs-lookup"><span data-stu-id="3dce3-112">Explore for yourself in the interactive window.</span></span>

<span data-ttu-id="3dce3-113">Atribut `Conditional` se často používá `DEBUG` s identifikátorem povolit trasování a protokolování funkce pro ladění sestavení, ale ne ve verzi sestavení, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="3dce3-113">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditional" :::

<span data-ttu-id="3dce3-114">Pokud je volána metoda označená jako podmíněná, přítomnost nebo nepřítomnost zadaného symbolu předběžného zpracování určuje, zda je volání zahrnuto nebo vynecháno.</span><span class="sxs-lookup"><span data-stu-id="3dce3-114">When a method marked conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="3dce3-115">Pokud je definován symbol, je zahrnuto volání; v opačném případě je volání vynecháno.</span><span class="sxs-lookup"><span data-stu-id="3dce3-115">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="3dce3-116">Podmíněná metoda musí být metoda v deklaraci třídy `void` nebo struktury a musí mít návratový typ.</span><span class="sxs-lookup"><span data-stu-id="3dce3-116">A conditional method must be a method in a class or struct declaration and must have a `void` return type.</span></span> <span data-ttu-id="3dce3-117">Použití `Conditional` je čistší, elegantnější a méně náchylné k `#if…#endif` chybám než ohraničování metod uvnitř bloků.</span><span class="sxs-lookup"><span data-stu-id="3dce3-117">Using `Conditional` is cleaner, more elegant, and less error-prone than enclosing methods inside `#if…#endif` blocks.</span></span>

<span data-ttu-id="3dce3-118">Pokud má metoda `Conditional` více atributů, je zahrnuto volání metody, pokud je definován jeden nebo více podmíněných symbolů (symboly jsou logicky propojeny pomocí operátoru OR).</span><span class="sxs-lookup"><span data-stu-id="3dce3-118">If a method has multiple `Conditional` attributes, a call to the method is included if at one or more conditional symbols is defined (the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="3dce3-119">V následujícím příkladu přítomnost `A` buď `B` nebo má za následek volání metody:</span><span class="sxs-lookup"><span data-stu-id="3dce3-119">In the following example, the presence of either `A` or `B` results in a method call:</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetMultipleConditions" :::

### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="3dce3-120">Použití `Conditional` s třídami atributů</span><span class="sxs-lookup"><span data-stu-id="3dce3-120">Using `Conditional` with attribute classes</span></span>

<span data-ttu-id="3dce3-121">Atribut `Conditional` lze také použít na definici třídy atributu.</span><span class="sxs-lookup"><span data-stu-id="3dce3-121">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="3dce3-122">V následujícím příkladu bude `Documentation` vlastní atribut přidávat informace `DEBUG` pouze do metadat, pokud je definován.</span><span class="sxs-lookup"><span data-stu-id="3dce3-122">In the following example, the custom attribute `Documentation` will only add information to the metadata if `DEBUG` is defined.</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditionalConditionalAttribute" :::

## <a name="obsolete-attribute"></a><span data-ttu-id="3dce3-123">Atribut `Obsolete`</span><span class="sxs-lookup"><span data-stu-id="3dce3-123">`Obsolete` attribute</span></span>

<span data-ttu-id="3dce3-124">Atribut `Obsolete` označí prvek kódu jako již doporučený pro použití.</span><span class="sxs-lookup"><span data-stu-id="3dce3-124">The `Obsolete` attribute marks a code element as no longer recommended for use.</span></span> <span data-ttu-id="3dce3-125">Použití entity označené jako zastaralé generuje upozornění nebo chybu.</span><span class="sxs-lookup"><span data-stu-id="3dce3-125">Use of an entity marked obsolete generates a warning or an error.</span></span> <span data-ttu-id="3dce3-126">Atribut `Obsolete` je atribut na jedno použití a lze jej použít pro libovolnou entitu, která umožňuje atributy.</span><span class="sxs-lookup"><span data-stu-id="3dce3-126">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="3dce3-127">`Obsolete`je alias <xref:System.ObsoleteAttribute>pro aplikaci .</span><span class="sxs-lookup"><span data-stu-id="3dce3-127">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>

<span data-ttu-id="3dce3-128">V následujícím příkladu `Obsolete` je atribut `A` použit `B.OldMethod`pro třídu a metodu .</span><span class="sxs-lookup"><span data-stu-id="3dce3-128">In the following example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="3dce3-129">Vzhledem k tomu, že druhý `B.OldMethod` argument `true`konstruktoru atributu aplikovaný na je `A` nastavena na , tato metoda způsobí chybu kompilátoru, vzhledem k tomu, že pomocí třídy pouze vytvoří upozornění.</span><span class="sxs-lookup"><span data-stu-id="3dce3-129">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="3dce3-130">Volání `B.NewMethod`, však nevytváří žádné upozornění nebo chybu.</span><span class="sxs-lookup"><span data-stu-id="3dce3-130">Calling `B.NewMethod`, however, produces no warning or error.</span></span> <span data-ttu-id="3dce3-131">Například při použití s předchozími definicemi, následující kód generuje dvě upozornění a jednu chybu:</span><span class="sxs-lookup"><span data-stu-id="3dce3-131">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>

:::code language="csharp" source="snippets/ObsoleteExample.cs" interactive="try-dotnet" :::

<span data-ttu-id="3dce3-132">Řetězec zadaný jako první argument konstruktoru atributu se zobrazí jako součást upozornění nebo chyby.</span><span class="sxs-lookup"><span data-stu-id="3dce3-132">The string provided as the first argument to the attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="3dce3-133">Jsou generována `A` dvě upozornění pro třídu: jeden pro deklaraci odkazu třídy a jeden pro konstruktor třídy.</span><span class="sxs-lookup"><span data-stu-id="3dce3-133">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span> <span data-ttu-id="3dce3-134">Atribut `Obsolete` lze použít bez argumentů, ale včetně vysvětlení, co použít místo toho se doporučuje.</span><span class="sxs-lookup"><span data-stu-id="3dce3-134">The `Obsolete` attribute can be used without arguments, but including an explanation what to use instead is recommended.</span></span>

## <a name="attributeusage-attribute"></a><span data-ttu-id="3dce3-135">Atribut `AttributeUsage`</span><span class="sxs-lookup"><span data-stu-id="3dce3-135">`AttributeUsage` attribute</span></span>

<span data-ttu-id="3dce3-136">Atribut `AttributeUsage` určuje, jak lze použít vlastní třídu atributu.</span><span class="sxs-lookup"><span data-stu-id="3dce3-136">The `AttributeUsage` attribute determines how a custom attribute class can be used.</span></span> <span data-ttu-id="3dce3-137"><xref:System.AttributeUsageAttribute>je atribut, který aplikujete na vlastní definice atributů.</span><span class="sxs-lookup"><span data-stu-id="3dce3-137"><xref:System.AttributeUsageAttribute> is an attribute you apply to custom attribute definitions.</span></span> <span data-ttu-id="3dce3-138">Atribut `AttributeUsage` umožňuje řídit:</span><span class="sxs-lookup"><span data-stu-id="3dce3-138">The `AttributeUsage` attribute enables you to control:</span></span>

- <span data-ttu-id="3dce3-139">U kterých programových prvků může být atribut použit.</span><span class="sxs-lookup"><span data-stu-id="3dce3-139">Which program elements attribute may be applied to.</span></span> <span data-ttu-id="3dce3-140">Pokud neomezíte jeho použití, může být atribut použit na některý z následujících prvků programu:</span><span class="sxs-lookup"><span data-stu-id="3dce3-140">Unless you restrict its usage, an attribute may be applied to any of the following program elements:</span></span>
  - <span data-ttu-id="3dce3-141">sestavení</span><span class="sxs-lookup"><span data-stu-id="3dce3-141">assembly</span></span>
  - <span data-ttu-id="3dce3-142">module</span><span class="sxs-lookup"><span data-stu-id="3dce3-142">module</span></span>
  - <span data-ttu-id="3dce3-143">pole</span><span class="sxs-lookup"><span data-stu-id="3dce3-143">field</span></span>
  - <span data-ttu-id="3dce3-144">event</span><span class="sxs-lookup"><span data-stu-id="3dce3-144">event</span></span>
  - <span data-ttu-id="3dce3-145">method</span><span class="sxs-lookup"><span data-stu-id="3dce3-145">method</span></span>
  - <span data-ttu-id="3dce3-146">Param</span><span class="sxs-lookup"><span data-stu-id="3dce3-146">param</span></span>
  - <span data-ttu-id="3dce3-147">property</span><span class="sxs-lookup"><span data-stu-id="3dce3-147">property</span></span>
  - <span data-ttu-id="3dce3-148">return</span><span class="sxs-lookup"><span data-stu-id="3dce3-148">return</span></span>
  - <span data-ttu-id="3dce3-149">type</span><span class="sxs-lookup"><span data-stu-id="3dce3-149">type</span></span>
- <span data-ttu-id="3dce3-150">Určuje, zda lze atribut použít na jeden prvek programu vícekrát.</span><span class="sxs-lookup"><span data-stu-id="3dce3-150">Whether an attribute can be applied to a single program element multiple times.</span></span>
- <span data-ttu-id="3dce3-151">Určuje, zda jsou atributy zděděny odvozenými třídami.</span><span class="sxs-lookup"><span data-stu-id="3dce3-151">Whether attributes are inherited by derived classes.</span></span>

<span data-ttu-id="3dce3-152">Výchozí nastavení vypadá jako v následujícím příkladu při explicitním použití:</span><span class="sxs-lookup"><span data-stu-id="3dce3-152">The default settings look like the following example when applied explicitly:</span></span>

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageFirst" :::

<span data-ttu-id="3dce3-153">V tomto příkladu lze třídu `NewAttribute` použít na libovolný podporovaný prvek programu.</span><span class="sxs-lookup"><span data-stu-id="3dce3-153">In this example, the `NewAttribute` class can be applied to any supported program element.</span></span> <span data-ttu-id="3dce3-154">Ale to může být použita pouze jednou pro každou entitu.</span><span class="sxs-lookup"><span data-stu-id="3dce3-154">But it can be applied only once to each entity.</span></span> <span data-ttu-id="3dce3-155">Atribut je zděděn odvozenými třídami při použití na základní třídu.</span><span class="sxs-lookup"><span data-stu-id="3dce3-155">The attribute is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="3dce3-156">A <xref:System.AttributeUsageAttribute.AllowMultiple> <xref:System.AttributeUsageAttribute.Inherited> argumenty jsou volitelné, takže následující kód má stejný účinek:</span><span class="sxs-lookup"><span data-stu-id="3dce3-156">The <xref:System.AttributeUsageAttribute.AllowMultiple> and <xref:System.AttributeUsageAttribute.Inherited> arguments are optional, so the following code has the same effect:</span></span>

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageSecond" :::

<span data-ttu-id="3dce3-157">První <xref:System.AttributeUsageAttribute> argument musí být jeden nebo <xref:System.AttributeTargets> více prvků výčtu.</span><span class="sxs-lookup"><span data-stu-id="3dce3-157">The first <xref:System.AttributeUsageAttribute> argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="3dce3-158">Více typů cílů lze propojit společně s operátorem OR, jako je následující příklad:</span><span class="sxs-lookup"><span data-stu-id="3dce3-158">Multiple target types can be linked together with the OR operator, like the following example shows:</span></span>

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetDefinePropertyAttribute" :::

<span data-ttu-id="3dce3-159">Počínaje C# 7.3, atributy lze použít buď vlastnost nebo záložní pole pro automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3dce3-159">Beginning in C# 7.3, attributes can be applied to either the property or the backing field for an auto-implemented property.</span></span> <span data-ttu-id="3dce3-160">Atribut se vztahuje na vlastnost, pokud `field` nezadáte specifikátor atributu.</span><span class="sxs-lookup"><span data-stu-id="3dce3-160">The attribute applies to the property, unless you specify the `field` specifier on the attribute.</span></span> <span data-ttu-id="3dce3-161">Obě jsou uvedeny v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="3dce3-161">Both are shown in the following example:</span></span>

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetUsePropertyAttribute" :::

<span data-ttu-id="3dce3-162">Pokud <xref:System.AttributeUsageAttribute.AllowMultiple> je `true`argument , pak výsledný atribut lze použít více než jednou na jednu entitu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="3dce3-162">If the <xref:System.AttributeUsageAttribute.AllowMultiple> argument is `true`, then the resulting attribute can be applied more than once to a single entity, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/MultiUseAttribute.cs" id="SnippetMultiUse" :::

<span data-ttu-id="3dce3-163">V tomto `MultiUseAttribute` případě lze použít `AllowMultiple` opakovaně, `true`protože je nastavena na .</span><span class="sxs-lookup"><span data-stu-id="3dce3-163">In this case, `MultiUseAttribute` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="3dce3-164">Oba formáty zobrazené pro použití více atributů jsou platné.</span><span class="sxs-lookup"><span data-stu-id="3dce3-164">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="3dce3-165">Pokud <xref:System.AttributeUsageAttribute.Inherited> `false`je , pak atribut není zděděn podle tříd odvozených z atributu třídy.</span><span class="sxs-lookup"><span data-stu-id="3dce3-165">If <xref:System.AttributeUsageAttribute.Inherited> is `false`, then the attribute isn't inherited by classes derived from an attributed class.</span></span> <span data-ttu-id="3dce3-166">Příklad:</span><span class="sxs-lookup"><span data-stu-id="3dce3-166">For example:</span></span>

:::code language="csharp" source="snippets/NonInheritedAttribute.cs" id="SnippetNonInherited" :::

<span data-ttu-id="3dce3-167">V tomto `NonInheritedAttribute` případě se `DClass` nevztahuje na prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="3dce3-167">In this case `NonInheritedAttribute` isn't applied to `DClass` via inheritance.</span></span>

## <a name="see-also"></a><span data-ttu-id="3dce3-168">Viz také</span><span class="sxs-lookup"><span data-stu-id="3dce3-168">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="3dce3-169">Atributy</span><span class="sxs-lookup"><span data-stu-id="3dce3-169">Attributes</span></span>](../../../standard/attributes/index.md)
- [<span data-ttu-id="3dce3-170">Reflexe</span><span class="sxs-lookup"><span data-stu-id="3dce3-170">Reflection</span></span>](../../programming-guide/concepts/reflection.md)
