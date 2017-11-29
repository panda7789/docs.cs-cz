---
title: "Výchozí hodnota výrazy (C# programování průvodce)"
description: "Výchozí hodnota výrazy vytvořit výchozí hodnota pro všechny odkaz na typ nebo typ hodnoty"
ms.date: 08/23/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.assetid: b9daf449-4e64-496e-8592-6ed2c8875a98
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c2bb1c269e5347d615c47ab828506aef538c4761
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="default-value-expressions-c-programming-guide"></a><span data-ttu-id="77147-103">Výchozí hodnota výrazy (C# programovací průvodce)</span><span class="sxs-lookup"><span data-stu-id="77147-103">default value expressions (C# programming guide)</span></span>

<span data-ttu-id="77147-104">Výraz výchozí hodnoty vytvoří výchozí hodnota pro typ.</span><span class="sxs-lookup"><span data-stu-id="77147-104">A default value expression produces the default value for a type.</span></span> <span data-ttu-id="77147-105">Výchozí hodnota výrazy jsou užitečné zejména v obecné třídy a metody.</span><span class="sxs-lookup"><span data-stu-id="77147-105">Default value expressions are particularly useful in generic classes and methods.</span></span> <span data-ttu-id="77147-106">Jak přiřadit výchozí hodnotu typu parametrizované je jedním z problémů často vyvstává použití obecných typů `T` Pokud si nejste jisti následující předem:</span><span class="sxs-lookup"><span data-stu-id="77147-106">One issue that arises using generics is how to assign a default value to a parameterized type `T` when you do not know the following in advance:</span></span>

- <span data-ttu-id="77147-107">Jestli `T` odkazového typu nebo typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="77147-107">Whether `T` is a reference type or a value type.</span></span>
- <span data-ttu-id="77147-108">Pokud `T` je typ hodnoty, zda je číselná hodnota nebo struktury definovaný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="77147-108">If `T` is a value type, whether is a numeric value or a user-defined struct.</span></span>

 <span data-ttu-id="77147-109">Zadané proměnné `t` parametrizované typu `T`, příkaz `t = null` je platná pouze v případě `T` typem je odkaz.</span><span class="sxs-lookup"><span data-stu-id="77147-109">Given a variable `t` of a parameterized type `T`, the statement `t = null` is only valid if `T` is a reference type.</span></span> <span data-ttu-id="77147-110">Přiřazení `t = 0` funguje pouze pro typy číselnou hodnotu, ale ne pro struktury.</span><span class="sxs-lookup"><span data-stu-id="77147-110">The assignment `t = 0` only works for numeric value types but not for structs.</span></span> <span data-ttu-id="77147-111">Řešení, je použít výraz výchozí hodnotu, která vrátí hodnotu `null` pro odkazové typy (typy třídy a rozhraní typy) a pro typy číselnou hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="77147-111">The solution is to use a default value expression, which returns `null` for reference types (class types and interface types) and zero for numeric value types.</span></span> <span data-ttu-id="77147-112">Pro vlastní struktury vrátí struktura inicializována tak, aby nulové bit vzor, který vytváří 0 nebo `null` pro každého člena v závislosti na tom, jestli je daný člen typu hodnotu nebo odkaz.</span><span class="sxs-lookup"><span data-stu-id="77147-112">For user-defined structs, it returns the struct initialized to the zero bit pattern, which produces 0 or `null` for each member depending on whether that member is a value or reference type.</span></span> <span data-ttu-id="77147-113">U typů hodnot s povolenou hodnotou Null `default` vrátí <xref:System.Nullable%601?displayProperty=nameWithType>, který je inicializován jako jakékoli struktura.</span><span class="sxs-lookup"><span data-stu-id="77147-113">For nullable value types, `default` returns a <xref:System.Nullable%601?displayProperty=nameWithType>, which is initialized like any struct.</span></span>

<span data-ttu-id="77147-114">`default(T)` Výraz není omezen na obecné třídy a metody.</span><span class="sxs-lookup"><span data-stu-id="77147-114">The `default(T)` expression is not limited to generic classes and methods.</span></span> <span data-ttu-id="77147-115">Výchozí hodnota výrazy lze použít všechny spravovaného typu.</span><span class="sxs-lookup"><span data-stu-id="77147-115">Default value expressions can be used with any managed type.</span></span> <span data-ttu-id="77147-116">Platné jsou některé z těchto výrazů:</span><span class="sxs-lookup"><span data-stu-id="77147-116">Any of these expressions are valid:</span></span>

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 <span data-ttu-id="77147-117">Následující příklad z `GenericList<T>` třída ukazuje způsob použití `default(T)` operátor v obecné třídy.</span><span class="sxs-lookup"><span data-stu-id="77147-117">The following example from the `GenericList<T>` class shows how to use the `default(T)` operator in a generic class.</span></span> <span data-ttu-id="77147-118">Další informace najdete v tématu [přehled obecných typů](../generics/introduction-to-generics.md).</span><span class="sxs-lookup"><span data-stu-id="77147-118">For more information, see [Generics Overview](../generics/introduction-to-generics.md).</span></span>

 [!code-csharp[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a><span data-ttu-id="77147-119">Výchozí literálu a odvození typu</span><span class="sxs-lookup"><span data-stu-id="77147-119">default literal and type inference</span></span>

<span data-ttu-id="77147-120">Od verze jazyka C# 7.1, `default` literál lze použít pro výchozí hodnotu výrazy při kompilátor lze odvodit typ výrazu.</span><span class="sxs-lookup"><span data-stu-id="77147-120">Beginning with C# 7.1, the `default` literal can be used for default value expressions when the compiler can infer the type of the expression.</span></span> <span data-ttu-id="77147-121">`default` Literál vytváří stejnou hodnotu jako ekvivalentní `default(T)` kde `T` je odvozeném typu.</span><span class="sxs-lookup"><span data-stu-id="77147-121">The `default` literal produces the same value as the equivalent `default(T)` where `T` is the inferred type.</span></span> <span data-ttu-id="77147-122">To můžete provést kód přesnější snížením redundance deklarování typu více než jednou.</span><span class="sxs-lookup"><span data-stu-id="77147-122">This can make code more concise by reducing the redundancy of declaring a type more than once.</span></span> <span data-ttu-id="77147-123">`default` Literál lze použít v některém z následujících umístění:</span><span class="sxs-lookup"><span data-stu-id="77147-123">The `default` literal can be used in any of the following locations:</span></span>

- <span data-ttu-id="77147-124">Inicializátor proměnné</span><span class="sxs-lookup"><span data-stu-id="77147-124">variable initializer</span></span>
- <span data-ttu-id="77147-125">přiřazení proměnné</span><span class="sxs-lookup"><span data-stu-id="77147-125">variable assignment</span></span>
- <span data-ttu-id="77147-126">Výchozí hodnota pro volitelný parametr deklarace</span><span class="sxs-lookup"><span data-stu-id="77147-126">declaring the default value for an optional parameter</span></span>
- <span data-ttu-id="77147-127">poskytnutí hodnota pro argument volání – metoda</span><span class="sxs-lookup"><span data-stu-id="77147-127">providing the value for a method call argument</span></span>
- <span data-ttu-id="77147-128">vrátí příkaz (nebo výraz v vozidlo člen výrazu)</span><span class="sxs-lookup"><span data-stu-id="77147-128">return statement (or expression in an expression bodied member)</span></span>

<span data-ttu-id="77147-129">Následující příklad ukazuje použití mnoha `default` literálu ve výrazu výchozí hodnota:</span><span class="sxs-lookup"><span data-stu-id="77147-129">The following example shows many usages of the `default` literal in a default value expression:</span></span>

[!code-csharp[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a><span data-ttu-id="77147-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="77147-130">See also</span></span>

 <span data-ttu-id="77147-131"><xref:System.Collections.Generic>[Průvodce programováním v C#](../index.md)</span><span class="sxs-lookup"><span data-stu-id="77147-131"><xref:System.Collections.Generic> [C# Programming Guide](../index.md)</span></span>  
 [<span data-ttu-id="77147-132">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="77147-132">Generics</span></span>](../generics/index.md)  
 [<span data-ttu-id="77147-133">Obecné metody</span><span class="sxs-lookup"><span data-stu-id="77147-133">Generic Methods</span></span>](../generics/generic-methods.md)  
 [<span data-ttu-id="77147-134">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="77147-134">Generics</span></span>](~/docs/standard/generics/index.md)  
