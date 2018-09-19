---
title: Výrazy s výchozími hodnotami (C# Programming Guide)
description: Výrazy s výchozími hodnotami vytvořit výchozí hodnotu pro libovolný typ odkazu nebo typ hodnoty
ms.date: 04/25/2018
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.openlocfilehash: 94866f22fb3ad921a834cffb16fe17e44cef5965
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46007032"
---
# <a name="default-value-expressions-c-programming-guide"></a><span data-ttu-id="77d53-103">výrazy s výchozími hodnotami (C# programovací příručka)</span><span class="sxs-lookup"><span data-stu-id="77d53-103">default value expressions (C# programming guide)</span></span>

<span data-ttu-id="77d53-104">Výraz výchozí hodnoty `default(T)` vytvoří výchozí hodnota typu `T`.</span><span class="sxs-lookup"><span data-stu-id="77d53-104">A default value expression `default(T)` produces the default value of a type `T`.</span></span> <span data-ttu-id="77d53-105">V následující tabulce jsou uvedeny hodnoty, které jsou vytvořeny pro různé typy:</span><span class="sxs-lookup"><span data-stu-id="77d53-105">The following table shows which values are produced for various types:</span></span>

|<span data-ttu-id="77d53-106">Typ</span><span class="sxs-lookup"><span data-stu-id="77d53-106">Type</span></span>|<span data-ttu-id="77d53-107">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="77d53-107">Default value</span></span>|
|---------|---------|
|<span data-ttu-id="77d53-108">jakéhokoliv odkazového typu</span><span class="sxs-lookup"><span data-stu-id="77d53-108">Any reference type</span></span>|`null`|
|<span data-ttu-id="77d53-109">Zadejte číselnou hodnotu</span><span class="sxs-lookup"><span data-stu-id="77d53-109">Numeric value type</span></span>|<span data-ttu-id="77d53-110">Nula</span><span class="sxs-lookup"><span data-stu-id="77d53-110">Zero</span></span>|
|[<span data-ttu-id="77d53-111">bool</span><span class="sxs-lookup"><span data-stu-id="77d53-111">bool</span></span>](../../language-reference/keywords/bool.md)|`false`|
|[<span data-ttu-id="77d53-112">char</span><span class="sxs-lookup"><span data-stu-id="77d53-112">char</span></span>](../../language-reference/keywords/char.md)|`'\0'`|
|[<span data-ttu-id="77d53-113">enum</span><span class="sxs-lookup"><span data-stu-id="77d53-113">enum</span></span>](../../language-reference/keywords/enum.md)|<span data-ttu-id="77d53-114">Hodnota vytvořený podle výrazu `(E)0`, kde `E` je identifikátor výčtu.</span><span class="sxs-lookup"><span data-stu-id="77d53-114">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="77d53-115">struct</span><span class="sxs-lookup"><span data-stu-id="77d53-115">struct</span></span>](../../language-reference/keywords/struct.md)|<span data-ttu-id="77d53-116">Hodnotu vytvořenou testovaným nastavení všechny hodnoty pole na výchozí hodnoty a všechny odkazují na typ pole na `null`.</span><span class="sxs-lookup"><span data-stu-id="77d53-116">The value produced by setting all value type fields to their default value and all reference type fields to `null`.</span></span>|
|<span data-ttu-id="77d53-117">Typ s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="77d53-117">Nullable type</span></span>|<span data-ttu-id="77d53-118">Instance, pro kterou <xref:System.Nullable%601.HasValue%2A> vlastnost `false` a <xref:System.Nullable%601.Value%2A> vlastnost není definována.</span><span class="sxs-lookup"><span data-stu-id="77d53-118">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span>|

<span data-ttu-id="77d53-119">Výrazy s výchozími hodnotami jsou zvláště užitečné při obecné třídy a metody.</span><span class="sxs-lookup"><span data-stu-id="77d53-119">Default value expressions are particularly useful in generic classes and methods.</span></span> <span data-ttu-id="77d53-120">Jedním problémem, který nastane použití obecných typů je výchozí hodnota parametry typu přiřazení `T` Pokud neznáte následující předem:</span><span class="sxs-lookup"><span data-stu-id="77d53-120">One issue that arises using generics is how to assign a default value of a parameterized type `T` when you don't know the following in advance:</span></span>

- <span data-ttu-id="77d53-121">Zda `T` je typem odkazu nebo hodnotového typu.</span><span class="sxs-lookup"><span data-stu-id="77d53-121">Whether `T` is a reference type or a value type.</span></span>
- <span data-ttu-id="77d53-122">Pokud `T` je typ hodnoty, ať už se jedná o číselnou hodnotu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="77d53-122">If `T` is a value type, whether it's a numeric value or a struct.</span></span>

 <span data-ttu-id="77d53-123">Zadané proměnné `t` parametry typu `T`, příkaz `t = null` je platná pouze pokud `T` je typem odkazu.</span><span class="sxs-lookup"><span data-stu-id="77d53-123">Given a variable `t` of a parameterized type `T`, the statement `t = null` is only valid if `T` is a reference type.</span></span> <span data-ttu-id="77d53-124">Přiřazení `t = 0` funguje jenom u typů číselnou hodnotu, ale nikoli pro struktury.</span><span class="sxs-lookup"><span data-stu-id="77d53-124">The assignment `t = 0` only works for numeric value types but not for structs.</span></span> <span data-ttu-id="77d53-125">Chcete-li to vyřešit, použijte výraz výchozí hodnoty:</span><span class="sxs-lookup"><span data-stu-id="77d53-125">To solve that, use a default value expression:</span></span>

```csharp
T t = default(T);
```

<span data-ttu-id="77d53-126">`default(T)` Výraz není omezena pouze na obecné třídy a metody.</span><span class="sxs-lookup"><span data-stu-id="77d53-126">The `default(T)` expression is not limited to generic classes and methods.</span></span> <span data-ttu-id="77d53-127">Výrazy s výchozími hodnotami lze použít s žádným typem spravované.</span><span class="sxs-lookup"><span data-stu-id="77d53-127">Default value expressions can be used with any managed type.</span></span> <span data-ttu-id="77d53-128">Platné jsou některé z těchto výrazů:</span><span class="sxs-lookup"><span data-stu-id="77d53-128">Any of these expressions are valid:</span></span>

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 <span data-ttu-id="77d53-129">Následující příklad z `GenericList<T>` třídy ukazuje způsob použití `default(T)` operátor v obecné třídě.</span><span class="sxs-lookup"><span data-stu-id="77d53-129">The following example from the `GenericList<T>` class shows how to use the `default(T)` operator in a generic class.</span></span> <span data-ttu-id="77d53-130">Další informace najdete v tématu [Úvod do obecných typů](../generics/introduction-to-generics.md).</span><span class="sxs-lookup"><span data-stu-id="77d53-130">For more information, see [Introduction to Generics](../generics/introduction-to-generics.md).</span></span>

 [!code-csharp[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a><span data-ttu-id="77d53-131">Výchozí literál a odvození typu</span><span class="sxs-lookup"><span data-stu-id="77d53-131">default literal and type inference</span></span>

<span data-ttu-id="77d53-132">Od verze C# 7.1, `default` literal lze použít pro výrazy s výchozími hodnotami, pokud kompilátor může odvodit typ výrazu.</span><span class="sxs-lookup"><span data-stu-id="77d53-132">Beginning with C# 7.1, the `default` literal can be used for default value expressions when the compiler can infer the type of the expression.</span></span> <span data-ttu-id="77d53-133">`default` Literál vytvoří stejnou hodnotu jako odpovídající `default(T)` kde `T` je odvozený typ.</span><span class="sxs-lookup"><span data-stu-id="77d53-133">The `default` literal produces the same value as the equivalent `default(T)` where `T` is the inferred type.</span></span> <span data-ttu-id="77d53-134">To lze díky kód stručnější snižují redundanci deklarování typu více než jednou.</span><span class="sxs-lookup"><span data-stu-id="77d53-134">This can make code more concise by reducing the redundancy of declaring a type more than once.</span></span> <span data-ttu-id="77d53-135">`default` Literál je možné v některém z následujících umístění:</span><span class="sxs-lookup"><span data-stu-id="77d53-135">The `default` literal can be used in any of the following locations:</span></span>

- <span data-ttu-id="77d53-136">Inicializátor proměnné.</span><span class="sxs-lookup"><span data-stu-id="77d53-136">variable initializer</span></span>
- <span data-ttu-id="77d53-137">přiřazení proměnné</span><span class="sxs-lookup"><span data-stu-id="77d53-137">variable assignment</span></span>
- <span data-ttu-id="77d53-138">deklarování výchozí hodnota volitelného parametru</span><span class="sxs-lookup"><span data-stu-id="77d53-138">declaring the default value for an optional parameter</span></span>
- <span data-ttu-id="77d53-139">poskytuje hodnoty pro argument volání metody</span><span class="sxs-lookup"><span data-stu-id="77d53-139">providing the value for a method call argument</span></span>
- <span data-ttu-id="77d53-140">návratový příkaz (nebo výrazu v vozidlo člen typu výrazu)</span><span class="sxs-lookup"><span data-stu-id="77d53-140">return statement (or expression in an expression bodied member)</span></span>

<span data-ttu-id="77d53-141">Následující příklad ukazuje mnoho použití `default` literál ve výrazu výchozí hodnoty:</span><span class="sxs-lookup"><span data-stu-id="77d53-141">The following example shows many usages of the `default` literal in a default value expression:</span></span>

[!code-csharp[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a><span data-ttu-id="77d53-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="77d53-142">See Also</span></span>

- <xref:System.Collections.Generic>  
- [<span data-ttu-id="77d53-143">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="77d53-143">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="77d53-144">Obecné typy (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="77d53-144">Generics (C# Programming Guide)</span></span>](../generics/index.md)  
- [<span data-ttu-id="77d53-145">Obecné metody</span><span class="sxs-lookup"><span data-stu-id="77d53-145">Generic Methods</span></span>](../generics/generic-methods.md)  
- [<span data-ttu-id="77d53-146">Obecné typy v .NET</span><span class="sxs-lookup"><span data-stu-id="77d53-146">Generics in .NET</span></span>](~/docs/standard/generics/index.md)  
- [<span data-ttu-id="77d53-147">Tabulka výchozích hodnot</span><span class="sxs-lookup"><span data-stu-id="77d53-147">Default values table</span></span>](../../language-reference/keywords/default-values-table.md)
