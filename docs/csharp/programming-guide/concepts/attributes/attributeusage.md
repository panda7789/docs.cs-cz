---
title: AttributeUsage (C#)
ms.date: 04/25/2018
ms.openlocfilehash: 869e6509e55268767915a783a8652f7f950d7137
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
ms.locfileid: "33955925"
---
# <a name="attributeusage-c"></a><span data-ttu-id="117ae-102">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="117ae-102">AttributeUsage (C#)</span></span>

<span data-ttu-id="117ae-103">Určuje, jak lze použít třídu vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="117ae-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="117ae-104"><xref:System.AttributeUsageAttribute> je atribut, který použijete pro definice vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="117ae-104"><xref:System.AttributeUsageAttribute> is an attribute you apply to custom attribute definitions.</span></span> <span data-ttu-id="117ae-105">`AttributeUsage` Atributů umožňují řídit:</span><span class="sxs-lookup"><span data-stu-id="117ae-105">The `AttributeUsage` attribute enables you to control:</span></span>

- <span data-ttu-id="117ae-106">Který atribut elementy program může použít.</span><span class="sxs-lookup"><span data-stu-id="117ae-106">Which program elements attribute may be applied to.</span></span> <span data-ttu-id="117ae-107">Pokud omezíte je využití atribut je možné používat k jakémukoli z těchto prvků program:</span><span class="sxs-lookup"><span data-stu-id="117ae-107">Unless you restrict is usage, an attribute may be applied to any of the following program elements:</span></span>
  - <span data-ttu-id="117ae-108">sestavení</span><span class="sxs-lookup"><span data-stu-id="117ae-108">assembly</span></span>
  - <span data-ttu-id="117ae-109">module</span><span class="sxs-lookup"><span data-stu-id="117ae-109">module</span></span>
  - <span data-ttu-id="117ae-110">pole</span><span class="sxs-lookup"><span data-stu-id="117ae-110">field</span></span>
  - <span data-ttu-id="117ae-111">event</span><span class="sxs-lookup"><span data-stu-id="117ae-111">event</span></span>
  - <span data-ttu-id="117ae-112">– metoda</span><span class="sxs-lookup"><span data-stu-id="117ae-112">method</span></span>
  - <span data-ttu-id="117ae-113">Param</span><span class="sxs-lookup"><span data-stu-id="117ae-113">param</span></span>
  - <span data-ttu-id="117ae-114">property</span><span class="sxs-lookup"><span data-stu-id="117ae-114">property</span></span>
  - <span data-ttu-id="117ae-115">return</span><span class="sxs-lookup"><span data-stu-id="117ae-115">return</span></span>
  - <span data-ttu-id="117ae-116">– typ</span><span class="sxs-lookup"><span data-stu-id="117ae-116">type</span></span>
- <span data-ttu-id="117ae-117">Více než jednou. jestli chcete v jednom elementu programu je použít atribut.</span><span class="sxs-lookup"><span data-stu-id="117ae-117">Whether an attribute can be applied to a single program element multiple times.</span></span>
- <span data-ttu-id="117ae-118">Zda jsou zdědí atributy odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="117ae-118">Whether attributes are inherited by derived classes.</span></span>

<span data-ttu-id="117ae-119">Výchozí nastavení vypadat podobně jako v následujícím příkladu při použití explicitně:</span><span class="sxs-lookup"><span data-stu-id="117ae-119">The default settings look like the following example when applied explicitly:</span></span>

[!code-csharp[Define a new attribute](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#1)]

<span data-ttu-id="117ae-120">V tomto příkladu `NewAttribute` třídy lze použít na všech podporovaných program element.</span><span class="sxs-lookup"><span data-stu-id="117ae-120">In this example, the `NewAttribute` class can be applied to any supported program element.</span></span> <span data-ttu-id="117ae-121">Ale dá se použít jenom jednou pro každé entity.</span><span class="sxs-lookup"><span data-stu-id="117ae-121">But it can be applied only once to each entity.</span></span> <span data-ttu-id="117ae-122">Atribut zdědí odvozené třídy při použití základní třídy.</span><span class="sxs-lookup"><span data-stu-id="117ae-122">The attribute is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="117ae-123"><xref:System.AttributeUsageAttribute.AllowMultiple> a <xref:System.AttributeUsageAttribute.Inherited> jsou argumenty nepovinné, takže stejného efektu má následující kód:</span><span class="sxs-lookup"><span data-stu-id="117ae-123">The <xref:System.AttributeUsageAttribute.AllowMultiple> and <xref:System.AttributeUsageAttribute.Inherited> arguments are optional, so the following code has the same effect:</span></span>

[!code-csharp[Omit optional attributes](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#2)]

<span data-ttu-id="117ae-124">První <xref:System.AttributeUsageAttribute> argument musí být jeden či více elementů <xref:System.AttributeTargets> výčtu.</span><span class="sxs-lookup"><span data-stu-id="117ae-124">The first <xref:System.AttributeUsageAttribute> argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="117ae-125">Více typy cíle může být propojený společně s operátoru OR, jako ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="117ae-125">Multiple target types can be linked together with the OR operator, like the following example shows:</span></span>

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#1)]

<span data-ttu-id="117ae-126">Počínaje 7.3 C#, můžete použít atributů vlastnost nebo pole Základní automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="117ae-126">Beginning in C# 7.3, attributes can be applied to either the property or the backing field for an auto-implemented property.</span></span> <span data-ttu-id="117ae-127">Atribut se vztahují na vlastnost, pokud nezadáte `field` specifikátor na atributu.</span><span class="sxs-lookup"><span data-stu-id="117ae-127">The attribute applies to the property, unless you specify the `field` specifier on the attribute.</span></span> <span data-ttu-id="117ae-128">Jak se zobrazuje v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="117ae-128">Both are shown in the following example:</span></span>

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#2)]

<span data-ttu-id="117ae-129">Pokud <xref:System.AttributeUsageAttribute.AllowMultiple> argument je `true`, pak výsledné atribut můžete použít více než jednou pro jednu entitu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="117ae-129">If the <xref:System.AttributeUsageAttribute.AllowMultiple> argument is `true`, then the resulting attribute can be applied more than once to a single entity, as shown in the following example:</span></span>

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/MultiUseAttribute.cs#1)]

<span data-ttu-id="117ae-130">V takovém případě `MultiUseAttribute` můžete použít opakovaně, protože `AllowMultiple` je nastaven na `true`.</span><span class="sxs-lookup"><span data-stu-id="117ae-130">In this case, `MultiUseAttribute` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="117ae-131">Platné jsou oba formáty pro použití více atributů.</span><span class="sxs-lookup"><span data-stu-id="117ae-131">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="117ae-132">Pokud <xref:System.AttributeUsageAttribute.Inherited> je `false`, pak atribut není zdědí třídy odvozené od s atributy třídy.</span><span class="sxs-lookup"><span data-stu-id="117ae-132">If <xref:System.AttributeUsageAttribute.Inherited> is `false`, then the attribute isn't inherited by classes derived from an attributed class.</span></span> <span data-ttu-id="117ae-133">Příklad:</span><span class="sxs-lookup"><span data-stu-id="117ae-133">For example:</span></span>

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/NonInheritedAttribute.cs#1)]

<span data-ttu-id="117ae-134">V takovém případě `NonInheritedAttribute` neplatí pro `DClass` prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="117ae-134">In this case `NonInheritedAttribute` isn't applied to `DClass` via inheritance.</span></span>

## <a name="remarks"></a><span data-ttu-id="117ae-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="117ae-135">Remarks</span></span>

<span data-ttu-id="117ae-136">`AttributeUsage` Se o jedno použití atribut – jej nelze použít více než jednou pro stejnou třídu.</span><span class="sxs-lookup"><span data-stu-id="117ae-136">The `AttributeUsage` attribute is a single-use attribute--it can't be applied more than once to the same class.</span></span> <span data-ttu-id="117ae-137">`AttributeUsage` je alias <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="117ae-137">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>

<span data-ttu-id="117ae-138">Další informace najdete v tématu [přístup k atributy podle pomocí reflexe (C#)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="117ae-138">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="example"></a><span data-ttu-id="117ae-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="117ae-139">Example</span></span>

<span data-ttu-id="117ae-140">Následující příklad ukazuje účinek <xref:System.AttributeUsageAttribute.Inherited> a <xref:System.AttributeUsageAttribute.AllowMultiple> argumenty, které mají <xref:System.AttributeUsageAttribute> atribut a jak mohou být uvedené vlastních atributů použitých na třídu.</span><span class="sxs-lookup"><span data-stu-id="117ae-140">The following example demonstrates the effect of the <xref:System.AttributeUsageAttribute.Inherited> and <xref:System.AttributeUsageAttribute.AllowMultiple> arguments to the <xref:System.AttributeUsageAttribute> attribute, and how the custom attributes applied to a class can be enumerated.</span></span>

[!code-csharp[Applying and querying attributes](../../../../../samples/snippets/csharp/attributes/Program.cs#1)]

## <a name="sample-output"></a><span data-ttu-id="117ae-141">Vzorový výstup</span><span class="sxs-lookup"><span data-stu-id="117ae-141">Sample Output</span></span>

```text
Attributes on Base Class:
FirstAttribute
SecondAttribute
Attributes on Derived Class:
ThirdAttribute
ThirdAttribute
SecondAttribute
```

## <a name="see-also"></a><span data-ttu-id="117ae-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="117ae-142">See Also</span></span>
 <xref:System.Attribute>  
 <xref:System.Reflection>  
 [<span data-ttu-id="117ae-143">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="117ae-143">C# Programming Guide</span></span>](../..//index.md)  
 [<span data-ttu-id="117ae-144">Atributy</span><span class="sxs-lookup"><span data-stu-id="117ae-144">Attributes</span></span>](../../../..//standard/attributes/index.md)  
 [<span data-ttu-id="117ae-145">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="117ae-145">Reflection (C#)</span></span>](../reflection.md)  
 [<span data-ttu-id="117ae-146">Atributy</span><span class="sxs-lookup"><span data-stu-id="117ae-146">Attributes</span></span>](index.md)  
 [<span data-ttu-id="117ae-147">Vytváření vlastních atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="117ae-147">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
 [<span data-ttu-id="117ae-148">Přístup k atributům pomocí reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="117ae-148">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
