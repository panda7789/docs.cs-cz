---
title: Výchozí hodnota výrazy (C# programování průvodce)
description: Výchozí hodnota výrazy vytvořit výchozí hodnota pro všechny odkaz na typ nebo typ hodnoty
ms.date: 04/25/2018
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.openlocfilehash: be51ad253a2939f538144caf4500f39e144c1664
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336798"
---
# <a name="default-value-expressions-c-programming-guide"></a><span data-ttu-id="5a15b-103">Výchozí hodnota výrazy (C# programovací průvodce)</span><span class="sxs-lookup"><span data-stu-id="5a15b-103">default value expressions (C# programming guide)</span></span>

<span data-ttu-id="5a15b-104">Výraz výchozí hodnoty `default(T)` vytvoří výchozí hodnota typu `T`.</span><span class="sxs-lookup"><span data-stu-id="5a15b-104">A default value expression `default(T)` produces the default value of a type `T`.</span></span> <span data-ttu-id="5a15b-105">V následující tabulce jsou uvedeny hodnoty, které vytváří pro různé typy:</span><span class="sxs-lookup"><span data-stu-id="5a15b-105">The following table shows which values are produced for various types:</span></span>

|<span data-ttu-id="5a15b-106">Typ</span><span class="sxs-lookup"><span data-stu-id="5a15b-106">Type</span></span>|<span data-ttu-id="5a15b-107">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="5a15b-107">Default value</span></span>|
|---------|---------|
|<span data-ttu-id="5a15b-108">žádný odkaz na typ</span><span class="sxs-lookup"><span data-stu-id="5a15b-108">Any reference type</span></span>|`null`|
|<span data-ttu-id="5a15b-109">Typ číselné hodnoty</span><span class="sxs-lookup"><span data-stu-id="5a15b-109">Numeric value type</span></span>|<span data-ttu-id="5a15b-110">Nula</span><span class="sxs-lookup"><span data-stu-id="5a15b-110">Zero</span></span>|
|[<span data-ttu-id="5a15b-111">bool</span><span class="sxs-lookup"><span data-stu-id="5a15b-111">bool</span></span>](../../language-reference/keywords/bool.md)|`false`|
|[<span data-ttu-id="5a15b-112">char</span><span class="sxs-lookup"><span data-stu-id="5a15b-112">char</span></span>](../../language-reference/keywords/char.md)|`'\0'`|
|[<span data-ttu-id="5a15b-113">enum</span><span class="sxs-lookup"><span data-stu-id="5a15b-113">enum</span></span>](../../language-reference/keywords/enum.md)|<span data-ttu-id="5a15b-114">Hodnota vyprodukované výraz `(E)0`, kde `E` je identifikátor výčtu.</span><span class="sxs-lookup"><span data-stu-id="5a15b-114">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="5a15b-115">struct</span><span class="sxs-lookup"><span data-stu-id="5a15b-115">struct</span></span>](../../language-reference/keywords/struct.md)|<span data-ttu-id="5a15b-116">Hodnota vyprodukované nastavení všechny hodnoty typu pole na jejich výchozí hodnoty a všechny odkazovat typ pole k `null`.</span><span class="sxs-lookup"><span data-stu-id="5a15b-116">The value produced by setting all value type fields to their default value and all reference type fields to `null`.</span></span>|
|<span data-ttu-id="5a15b-117">Typ s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="5a15b-117">Nullable type</span></span>|<span data-ttu-id="5a15b-118">Instance pro kterou <xref:System.Nullable%601.HasValue%2A> vlastnost je `false` a <xref:System.Nullable%601.Value%2A> vlastnosti není definován.</span><span class="sxs-lookup"><span data-stu-id="5a15b-118">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span>|

<span data-ttu-id="5a15b-119">Výchozí hodnota výrazy jsou užitečné zejména v obecné třídy a metody.</span><span class="sxs-lookup"><span data-stu-id="5a15b-119">Default value expressions are particularly useful in generic classes and methods.</span></span> <span data-ttu-id="5a15b-120">Tom, jak přiřadit výchozí hodnotu parametrizované typu je jedním z problémů často vyvstává použití obecných typů `T` Pokud nevíte, následující předem:</span><span class="sxs-lookup"><span data-stu-id="5a15b-120">One issue that arises using generics is how to assign a default value of a parameterized type `T` when you don't know the following in advance:</span></span>

- <span data-ttu-id="5a15b-121">Jestli `T` odkazového typu nebo typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5a15b-121">Whether `T` is a reference type or a value type.</span></span>
- <span data-ttu-id="5a15b-122">Pokud `T` je typ hodnoty, zda je číselná hodnota nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="5a15b-122">If `T` is a value type, whether it's a numeric value or a struct.</span></span>

 <span data-ttu-id="5a15b-123">Zadané proměnné `t` parametrizované typu `T`, příkaz `t = null` je platná pouze v případě `T` typem je odkaz.</span><span class="sxs-lookup"><span data-stu-id="5a15b-123">Given a variable `t` of a parameterized type `T`, the statement `t = null` is only valid if `T` is a reference type.</span></span> <span data-ttu-id="5a15b-124">Přiřazení `t = 0` funguje pouze pro typy číselnou hodnotu, ale ne pro struktury.</span><span class="sxs-lookup"><span data-stu-id="5a15b-124">The assignment `t = 0` only works for numeric value types but not for structs.</span></span> <span data-ttu-id="5a15b-125">K řešení, které, použijte výraz výchozí hodnoty:</span><span class="sxs-lookup"><span data-stu-id="5a15b-125">To solve that, use a default value expression:</span></span>

```csharp
T t = default(T);
```

<span data-ttu-id="5a15b-126">`default(T)` Výraz není omezen na obecné třídy a metody.</span><span class="sxs-lookup"><span data-stu-id="5a15b-126">The `default(T)` expression is not limited to generic classes and methods.</span></span> <span data-ttu-id="5a15b-127">Výchozí hodnota výrazy lze použít všechny spravovaného typu.</span><span class="sxs-lookup"><span data-stu-id="5a15b-127">Default value expressions can be used with any managed type.</span></span> <span data-ttu-id="5a15b-128">Platné jsou některé z těchto výrazů:</span><span class="sxs-lookup"><span data-stu-id="5a15b-128">Any of these expressions are valid:</span></span>

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 <span data-ttu-id="5a15b-129">Následující příklad z `GenericList<T>` třída ukazuje způsob použití `default(T)` operátor v obecné třídy.</span><span class="sxs-lookup"><span data-stu-id="5a15b-129">The following example from the `GenericList<T>` class shows how to use the `default(T)` operator in a generic class.</span></span> <span data-ttu-id="5a15b-130">Další informace najdete v tématu [Úvod do obecných typů](../generics/introduction-to-generics.md).</span><span class="sxs-lookup"><span data-stu-id="5a15b-130">For more information, see [Introduction to Generics](../generics/introduction-to-generics.md).</span></span>

 [!code-csharp[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a><span data-ttu-id="5a15b-131">Výchozí literálu a odvození typu</span><span class="sxs-lookup"><span data-stu-id="5a15b-131">default literal and type inference</span></span>

<span data-ttu-id="5a15b-132">Od verze jazyka C# 7.1, `default` literál lze použít pro výchozí hodnotu výrazy při kompilátor lze odvodit typ výrazu.</span><span class="sxs-lookup"><span data-stu-id="5a15b-132">Beginning with C# 7.1, the `default` literal can be used for default value expressions when the compiler can infer the type of the expression.</span></span> <span data-ttu-id="5a15b-133">`default` Literál vytváří stejnou hodnotu jako ekvivalentní `default(T)` kde `T` je odvozeném typu.</span><span class="sxs-lookup"><span data-stu-id="5a15b-133">The `default` literal produces the same value as the equivalent `default(T)` where `T` is the inferred type.</span></span> <span data-ttu-id="5a15b-134">To můžete provést kód přesnější snížením redundance deklarování typu více než jednou.</span><span class="sxs-lookup"><span data-stu-id="5a15b-134">This can make code more concise by reducing the redundancy of declaring a type more than once.</span></span> <span data-ttu-id="5a15b-135">`default` Literál lze použít v některém z následujících umístění:</span><span class="sxs-lookup"><span data-stu-id="5a15b-135">The `default` literal can be used in any of the following locations:</span></span>

- <span data-ttu-id="5a15b-136">Inicializátor proměnné</span><span class="sxs-lookup"><span data-stu-id="5a15b-136">variable initializer</span></span>
- <span data-ttu-id="5a15b-137">přiřazení proměnné</span><span class="sxs-lookup"><span data-stu-id="5a15b-137">variable assignment</span></span>
- <span data-ttu-id="5a15b-138">Výchozí hodnota pro volitelný parametr deklarace</span><span class="sxs-lookup"><span data-stu-id="5a15b-138">declaring the default value for an optional parameter</span></span>
- <span data-ttu-id="5a15b-139">poskytnutí hodnota pro argument volání – metoda</span><span class="sxs-lookup"><span data-stu-id="5a15b-139">providing the value for a method call argument</span></span>
- <span data-ttu-id="5a15b-140">vrátí příkaz (nebo výraz v vozidlo člen výrazu)</span><span class="sxs-lookup"><span data-stu-id="5a15b-140">return statement (or expression in an expression bodied member)</span></span>

<span data-ttu-id="5a15b-141">Následující příklad ukazuje použití mnoha `default` literálu ve výrazu výchozí hodnota:</span><span class="sxs-lookup"><span data-stu-id="5a15b-141">The following example shows many usages of the `default` literal in a default value expression:</span></span>

[!code-csharp[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a><span data-ttu-id="5a15b-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a15b-142">See also</span></span>

 <xref:System.Collections.Generic>  
 [<span data-ttu-id="5a15b-143">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5a15b-143">C# Programming Guide</span></span>](../index.md)  
 [<span data-ttu-id="5a15b-144">Obecné typy (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="5a15b-144">Generics (C# Programming Guide)</span></span>](../generics/index.md)  
 [<span data-ttu-id="5a15b-145">Obecné metody</span><span class="sxs-lookup"><span data-stu-id="5a15b-145">Generic Methods</span></span>](../generics/generic-methods.md)  
 [<span data-ttu-id="5a15b-146">Obecné typy v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="5a15b-146">Generics in .NET</span></span>](~/docs/standard/generics/index.md)  
 [<span data-ttu-id="5a15b-147">Tabulka výchozích hodnot</span><span class="sxs-lookup"><span data-stu-id="5a15b-147">Default values table</span></span>](../../language-reference/keywords/default-values-table.md)
