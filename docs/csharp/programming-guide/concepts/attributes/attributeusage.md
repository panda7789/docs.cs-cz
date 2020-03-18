---
title: AttributeUsage (C#)
ms.date: 04/25/2018
ms.openlocfilehash: a3a82e33d7259ec56ec3e907bc3d4d9f8a01167d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61668715"
---
# <a name="attributeusage-c"></a><span data-ttu-id="b42de-102">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="b42de-102">AttributeUsage (C#)</span></span>

<span data-ttu-id="b42de-103">Určuje, jak lze použít vlastní třídu atributů.</span><span class="sxs-lookup"><span data-stu-id="b42de-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="b42de-104"><xref:System.AttributeUsageAttribute>je atribut, který aplikujete na vlastní definice atributů.</span><span class="sxs-lookup"><span data-stu-id="b42de-104"><xref:System.AttributeUsageAttribute> is an attribute you apply to custom attribute definitions.</span></span> <span data-ttu-id="b42de-105">Atribut `AttributeUsage` umožňuje řídit:</span><span class="sxs-lookup"><span data-stu-id="b42de-105">The `AttributeUsage` attribute enables you to control:</span></span>

- <span data-ttu-id="b42de-106">U kterých programových prvků může být atribut použit.</span><span class="sxs-lookup"><span data-stu-id="b42de-106">Which program elements attribute may be applied to.</span></span> <span data-ttu-id="b42de-107">Pokud neomezíte jeho použití, může být atribut použit na některý z následujících prvků programu:</span><span class="sxs-lookup"><span data-stu-id="b42de-107">Unless you restrict its usage, an attribute may be applied to any of the following program elements:</span></span>
  - <span data-ttu-id="b42de-108">sestavení</span><span class="sxs-lookup"><span data-stu-id="b42de-108">assembly</span></span>
  - <span data-ttu-id="b42de-109">module</span><span class="sxs-lookup"><span data-stu-id="b42de-109">module</span></span>
  - <span data-ttu-id="b42de-110">pole</span><span class="sxs-lookup"><span data-stu-id="b42de-110">field</span></span>
  - <span data-ttu-id="b42de-111">event</span><span class="sxs-lookup"><span data-stu-id="b42de-111">event</span></span>
  - <span data-ttu-id="b42de-112">method</span><span class="sxs-lookup"><span data-stu-id="b42de-112">method</span></span>
  - <span data-ttu-id="b42de-113">Param</span><span class="sxs-lookup"><span data-stu-id="b42de-113">param</span></span>
  - <span data-ttu-id="b42de-114">property</span><span class="sxs-lookup"><span data-stu-id="b42de-114">property</span></span>
  - <span data-ttu-id="b42de-115">return</span><span class="sxs-lookup"><span data-stu-id="b42de-115">return</span></span>
  - <span data-ttu-id="b42de-116">type</span><span class="sxs-lookup"><span data-stu-id="b42de-116">type</span></span>
- <span data-ttu-id="b42de-117">Určuje, zda lze atribut použít na jeden prvek programu vícekrát.</span><span class="sxs-lookup"><span data-stu-id="b42de-117">Whether an attribute can be applied to a single program element multiple times.</span></span>
- <span data-ttu-id="b42de-118">Určuje, zda jsou atributy zděděny odvozenými třídami.</span><span class="sxs-lookup"><span data-stu-id="b42de-118">Whether attributes are inherited by derived classes.</span></span>

<span data-ttu-id="b42de-119">Výchozí nastavení vypadá jako v následujícím příkladu při explicitním použití:</span><span class="sxs-lookup"><span data-stu-id="b42de-119">The default settings look like the following example when applied explicitly:</span></span>

[!code-csharp[Define a new attribute](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#1)]

<span data-ttu-id="b42de-120">V tomto příkladu lze třídu `NewAttribute` použít na libovolný podporovaný prvek programu.</span><span class="sxs-lookup"><span data-stu-id="b42de-120">In this example, the `NewAttribute` class can be applied to any supported program element.</span></span> <span data-ttu-id="b42de-121">Ale to může být použita pouze jednou pro každou entitu.</span><span class="sxs-lookup"><span data-stu-id="b42de-121">But it can be applied only once to each entity.</span></span> <span data-ttu-id="b42de-122">Atribut je zděděn odvozenými třídami při použití na základní třídu.</span><span class="sxs-lookup"><span data-stu-id="b42de-122">The attribute is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="b42de-123">A <xref:System.AttributeUsageAttribute.AllowMultiple> <xref:System.AttributeUsageAttribute.Inherited> argumenty jsou volitelné, takže následující kód má stejný účinek:</span><span class="sxs-lookup"><span data-stu-id="b42de-123">The <xref:System.AttributeUsageAttribute.AllowMultiple> and <xref:System.AttributeUsageAttribute.Inherited> arguments are optional, so the following code has the same effect:</span></span>

[!code-csharp[Omit optional attributes](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#2)]

<span data-ttu-id="b42de-124">První <xref:System.AttributeUsageAttribute> argument musí být jeden nebo <xref:System.AttributeTargets> více prvků výčtu.</span><span class="sxs-lookup"><span data-stu-id="b42de-124">The first <xref:System.AttributeUsageAttribute> argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="b42de-125">Více typů cílů lze propojit společně s operátorem OR, jako je následující příklad:</span><span class="sxs-lookup"><span data-stu-id="b42de-125">Multiple target types can be linked together with the OR operator, like the following example shows:</span></span>

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#1)]

<span data-ttu-id="b42de-126">Počínaje C# 7.3, atributy lze použít buď vlastnost nebo záložní pole pro automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b42de-126">Beginning in C# 7.3, attributes can be applied to either the property or the backing field for an auto-implemented property.</span></span> <span data-ttu-id="b42de-127">Atribut se vztahuje na vlastnost, pokud `field` nezadáte specifikátor atributu.</span><span class="sxs-lookup"><span data-stu-id="b42de-127">The attribute applies to the property, unless you specify the `field` specifier on the attribute.</span></span> <span data-ttu-id="b42de-128">Obě jsou uvedeny v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b42de-128">Both are shown in the following example:</span></span>

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#2)]

<span data-ttu-id="b42de-129">Pokud <xref:System.AttributeUsageAttribute.AllowMultiple> je `true`argument , pak výsledný atribut lze použít více než jednou na jednu entitu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b42de-129">If the <xref:System.AttributeUsageAttribute.AllowMultiple> argument is `true`, then the resulting attribute can be applied more than once to a single entity, as shown in the following example:</span></span>

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/MultiUseAttribute.cs#1)]

<span data-ttu-id="b42de-130">V tomto `MultiUseAttribute` případě lze použít `AllowMultiple` opakovaně, `true`protože je nastavena na .</span><span class="sxs-lookup"><span data-stu-id="b42de-130">In this case, `MultiUseAttribute` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="b42de-131">Oba formáty zobrazené pro použití více atributů jsou platné.</span><span class="sxs-lookup"><span data-stu-id="b42de-131">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="b42de-132">Pokud <xref:System.AttributeUsageAttribute.Inherited> `false`je , pak atribut není zděděn podle tříd odvozených z atributu třídy.</span><span class="sxs-lookup"><span data-stu-id="b42de-132">If <xref:System.AttributeUsageAttribute.Inherited> is `false`, then the attribute isn't inherited by classes derived from an attributed class.</span></span> <span data-ttu-id="b42de-133">Například:</span><span class="sxs-lookup"><span data-stu-id="b42de-133">For example:</span></span>

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/NonInheritedAttribute.cs#1)]

<span data-ttu-id="b42de-134">V tomto `NonInheritedAttribute` případě se `DClass` nevztahuje na prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="b42de-134">In this case `NonInheritedAttribute` isn't applied to `DClass` via inheritance.</span></span>

## <a name="remarks"></a><span data-ttu-id="b42de-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b42de-135">Remarks</span></span>

<span data-ttu-id="b42de-136">Atribut `AttributeUsage` je atribut na jedno použití – nelze jej použít více než jednou na stejnou třídu.</span><span class="sxs-lookup"><span data-stu-id="b42de-136">The `AttributeUsage` attribute is a single-use attribute--it can't be applied more than once to the same class.</span></span> <span data-ttu-id="b42de-137">`AttributeUsage`je alias <xref:System.AttributeUsageAttribute>pro aplikaci .</span><span class="sxs-lookup"><span data-stu-id="b42de-137">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>

<span data-ttu-id="b42de-138">Další informace naleznete [v tématu Přístup k atributům pomocí reflexe (C#)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="b42de-138">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="example"></a><span data-ttu-id="b42de-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="b42de-139">Example</span></span>

<span data-ttu-id="b42de-140">Následující příklad ukazuje účinek <xref:System.AttributeUsageAttribute.Inherited> a <xref:System.AttributeUsageAttribute.AllowMultiple> argumenty <xref:System.AttributeUsageAttribute> na atribut a jak lze vyjmenovat vlastní atributy použité pro třídu.</span><span class="sxs-lookup"><span data-stu-id="b42de-140">The following example demonstrates the effect of the <xref:System.AttributeUsageAttribute.Inherited> and <xref:System.AttributeUsageAttribute.AllowMultiple> arguments to the <xref:System.AttributeUsageAttribute> attribute, and how the custom attributes applied to a class can be enumerated.</span></span>

[!code-csharp[Applying and querying attributes](../../../../../samples/snippets/csharp/attributes/Program.cs#1)]

## <a name="sample-output"></a><span data-ttu-id="b42de-141">Vzorový výstup</span><span class="sxs-lookup"><span data-stu-id="b42de-141">Sample Output</span></span>

```text
Attributes on Base Class:
FirstAttribute
SecondAttribute
Attributes on Derived Class:
ThirdAttribute
ThirdAttribute
SecondAttribute
```

## <a name="see-also"></a><span data-ttu-id="b42de-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="b42de-142">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="b42de-143">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b42de-143">C# Programming Guide</span></span>](../..//index.md)
- [<span data-ttu-id="b42de-144">Atributy</span><span class="sxs-lookup"><span data-stu-id="b42de-144">Attributes</span></span>](../../../..//standard/attributes/index.md)
- [<span data-ttu-id="b42de-145">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="b42de-145">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="b42de-146">Atributy</span><span class="sxs-lookup"><span data-stu-id="b42de-146">Attributes</span></span>](index.md)
- [<span data-ttu-id="b42de-147">Vytváření vlastních atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="b42de-147">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="b42de-148">Přístup k atributům pomocí reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="b42de-148">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
