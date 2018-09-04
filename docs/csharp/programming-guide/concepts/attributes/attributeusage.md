---
title: AttributeUsage (C#)
ms.date: 04/25/2018
ms.openlocfilehash: 37657a0611180d5b4c48b3e1778d33861afa5a74
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500569"
---
# <a name="attributeusage-c"></a><span data-ttu-id="7c136-102">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="7c136-102">AttributeUsage (C#)</span></span>

<span data-ttu-id="7c136-103">Určuje, jak je možné třídu vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="7c136-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="7c136-104"><xref:System.AttributeUsageAttribute> představuje atribut, které použijete pro vlastní atribut definice.</span><span class="sxs-lookup"><span data-stu-id="7c136-104"><xref:System.AttributeUsageAttribute> is an attribute you apply to custom attribute definitions.</span></span> <span data-ttu-id="7c136-105">`AttributeUsage` Atribut umožňuje řídit:</span><span class="sxs-lookup"><span data-stu-id="7c136-105">The `AttributeUsage` attribute enables you to control:</span></span>

- <span data-ttu-id="7c136-106">Které atribut prvky programu může použít pro.</span><span class="sxs-lookup"><span data-stu-id="7c136-106">Which program elements attribute may be applied to.</span></span> <span data-ttu-id="7c136-107">Pokud můžete omezit využití, je atribut může použije pro všechny z následujících prvků programu:</span><span class="sxs-lookup"><span data-stu-id="7c136-107">Unless you restrict is usage, an attribute may be applied to any of the following program elements:</span></span>
  - <span data-ttu-id="7c136-108">sestavení</span><span class="sxs-lookup"><span data-stu-id="7c136-108">assembly</span></span>
  - <span data-ttu-id="7c136-109">module</span><span class="sxs-lookup"><span data-stu-id="7c136-109">module</span></span>
  - <span data-ttu-id="7c136-110">pole</span><span class="sxs-lookup"><span data-stu-id="7c136-110">field</span></span>
  - <span data-ttu-id="7c136-111">event</span><span class="sxs-lookup"><span data-stu-id="7c136-111">event</span></span>
  - <span data-ttu-id="7c136-112">– metoda</span><span class="sxs-lookup"><span data-stu-id="7c136-112">method</span></span>
  - <span data-ttu-id="7c136-113">Param</span><span class="sxs-lookup"><span data-stu-id="7c136-113">param</span></span>
  - <span data-ttu-id="7c136-114">property</span><span class="sxs-lookup"><span data-stu-id="7c136-114">property</span></span>
  - <span data-ttu-id="7c136-115">return</span><span class="sxs-lookup"><span data-stu-id="7c136-115">return</span></span>
  - <span data-ttu-id="7c136-116">– typ</span><span class="sxs-lookup"><span data-stu-id="7c136-116">type</span></span>
- <span data-ttu-id="7c136-117">Určuje, zda atribut lze použít na jednom elementu programu několikrát.</span><span class="sxs-lookup"><span data-stu-id="7c136-117">Whether an attribute can be applied to a single program element multiple times.</span></span>
- <span data-ttu-id="7c136-118">Určuje, zda atributy jsou zděděny z odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="7c136-118">Whether attributes are inherited by derived classes.</span></span>

<span data-ttu-id="7c136-119">Výchozí nastavení vypadat jako v následujícím příkladu, při použití explicitně:</span><span class="sxs-lookup"><span data-stu-id="7c136-119">The default settings look like the following example when applied explicitly:</span></span>

[!code-csharp[Define a new attribute](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#1)]

<span data-ttu-id="7c136-120">V tomto příkladu `NewAttribute` třídy lze použít na libovolný prvek programu podporované.</span><span class="sxs-lookup"><span data-stu-id="7c136-120">In this example, the `NewAttribute` class can be applied to any supported program element.</span></span> <span data-ttu-id="7c136-121">Ale lze jej použít pouze jednou pro každou entitu.</span><span class="sxs-lookup"><span data-stu-id="7c136-121">But it can be applied only once to each entity.</span></span> <span data-ttu-id="7c136-122">Atribut je zděděn z odvozené třídy při použití na základní třídu.</span><span class="sxs-lookup"><span data-stu-id="7c136-122">The attribute is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="7c136-123"><xref:System.AttributeUsageAttribute.AllowMultiple> a <xref:System.AttributeUsageAttribute.Inherited> jsou argumenty nepovinné, tak má stejný účinek následující kód:</span><span class="sxs-lookup"><span data-stu-id="7c136-123">The <xref:System.AttributeUsageAttribute.AllowMultiple> and <xref:System.AttributeUsageAttribute.Inherited> arguments are optional, so the following code has the same effect:</span></span>

[!code-csharp[Omit optional attributes](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#2)]

<span data-ttu-id="7c136-124">První <xref:System.AttributeUsageAttribute> argument musí být jeden nebo více prvků <xref:System.AttributeTargets> výčtu.</span><span class="sxs-lookup"><span data-stu-id="7c136-124">The first <xref:System.AttributeUsageAttribute> argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="7c136-125">Více typů cíl může být propojený spolu s operátorem OR, stejně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="7c136-125">Multiple target types can be linked together with the OR operator, like the following example shows:</span></span>

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#1)]

<span data-ttu-id="7c136-126">Od C# 7.3, atributy lze použít u vlastnosti nebo pomocné pole automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7c136-126">Beginning in C# 7.3, attributes can be applied to either the property or the backing field for an auto-implemented property.</span></span> <span data-ttu-id="7c136-127">Pokud nezadáte platí atribut pro vlastnost, `field` specifikátor atributu.</span><span class="sxs-lookup"><span data-stu-id="7c136-127">The attribute applies to the property, unless you specify the `field` specifier on the attribute.</span></span> <span data-ttu-id="7c136-128">Obě jsou uvedeny v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="7c136-128">Both are shown in the following example:</span></span>

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#2)]

<span data-ttu-id="7c136-129">Pokud <xref:System.AttributeUsageAttribute.AllowMultiple> argument je `true`, pak výsledný atribut lze použít více než jednou na jednu entitu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="7c136-129">If the <xref:System.AttributeUsageAttribute.AllowMultiple> argument is `true`, then the resulting attribute can be applied more than once to a single entity, as shown in the following example:</span></span>

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/MultiUseAttribute.cs#1)]

<span data-ttu-id="7c136-130">V takovém případě `MultiUseAttribute` můžete použít opakovaně, protože `AllowMultiple` je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="7c136-130">In this case, `MultiUseAttribute` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="7c136-131">Oba formáty pro použití více atributů jsou platné.</span><span class="sxs-lookup"><span data-stu-id="7c136-131">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="7c136-132">Pokud <xref:System.AttributeUsageAttribute.Inherited> je `false`, pak atribut není zděděn z třídy odvozené z třídy s atributy.</span><span class="sxs-lookup"><span data-stu-id="7c136-132">If <xref:System.AttributeUsageAttribute.Inherited> is `false`, then the attribute isn't inherited by classes derived from an attributed class.</span></span> <span data-ttu-id="7c136-133">Příklad:</span><span class="sxs-lookup"><span data-stu-id="7c136-133">For example:</span></span>

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/NonInheritedAttribute.cs#1)]

<span data-ttu-id="7c136-134">V tomto případě `NonInheritedAttribute` neplatí pro `DClass` prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="7c136-134">In this case `NonInheritedAttribute` isn't applied to `DClass` via inheritance.</span></span>

## <a name="remarks"></a><span data-ttu-id="7c136-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7c136-135">Remarks</span></span>

<span data-ttu-id="7c136-136">`AttributeUsage` Atribut je jedno použití atributu – jej nelze použít více než jednou pro tutéž třídu.</span><span class="sxs-lookup"><span data-stu-id="7c136-136">The `AttributeUsage` attribute is a single-use attribute--it can't be applied more than once to the same class.</span></span> <span data-ttu-id="7c136-137">`AttributeUsage` je alias pro <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7c136-137">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>

<span data-ttu-id="7c136-138">Další informace najdete v tématu [přístup k atributy podle použití reflexe (C#)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="7c136-138">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="example"></a><span data-ttu-id="7c136-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c136-139">Example</span></span>

<span data-ttu-id="7c136-140">Následující příklad ukazuje účinek <xref:System.AttributeUsageAttribute.Inherited> a <xref:System.AttributeUsageAttribute.AllowMultiple> argumenty, které mají <xref:System.AttributeUsageAttribute> atribut a jak mohou být uvedené vlastní atributy použité na třídu.</span><span class="sxs-lookup"><span data-stu-id="7c136-140">The following example demonstrates the effect of the <xref:System.AttributeUsageAttribute.Inherited> and <xref:System.AttributeUsageAttribute.AllowMultiple> arguments to the <xref:System.AttributeUsageAttribute> attribute, and how the custom attributes applied to a class can be enumerated.</span></span>

[!code-csharp[Applying and querying attributes](../../../../../samples/snippets/csharp/attributes/Program.cs#1)]

## <a name="sample-output"></a><span data-ttu-id="7c136-141">Vzorový výstup</span><span class="sxs-lookup"><span data-stu-id="7c136-141">Sample Output</span></span>

```text
Attributes on Base Class:
FirstAttribute
SecondAttribute
Attributes on Derived Class:
ThirdAttribute
ThirdAttribute
SecondAttribute
```

## <a name="see-also"></a><span data-ttu-id="7c136-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c136-142">See Also</span></span>

- <xref:System.Attribute>  
- <xref:System.Reflection>  
- [<span data-ttu-id="7c136-143">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7c136-143">C# Programming Guide</span></span>](../..//index.md)  
- [<span data-ttu-id="7c136-144">Atributy</span><span class="sxs-lookup"><span data-stu-id="7c136-144">Attributes</span></span>](../../../..//standard/attributes/index.md)  
- [<span data-ttu-id="7c136-145">Reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="7c136-145">Reflection (C#)</span></span>](../reflection.md)  
- [<span data-ttu-id="7c136-146">Atributy</span><span class="sxs-lookup"><span data-stu-id="7c136-146">Attributes</span></span>](index.md)  
- [<span data-ttu-id="7c136-147">Vytváření vlastních atributů (C#)</span><span class="sxs-lookup"><span data-stu-id="7c136-147">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
- [<span data-ttu-id="7c136-148">Přístup k atributům pomocí reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="7c136-148">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
