---
description: static – modifikátor – reference jazyka C#
title: static – modifikátor – reference jazyka C#
ms.date: 04/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: f42636d1bbdf4342297f46f50ec6dfc2a70eacad
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142060"
---
# <a name="static-c-reference"></a><span data-ttu-id="8d6f9-103">static – modifikátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8d6f9-103">static (C# Reference)</span></span>

<span data-ttu-id="8d6f9-104">Tato stránka obsahuje `static` klíčové slovo modifikátoru.</span><span class="sxs-lookup"><span data-stu-id="8d6f9-104">This page covers the `static` modifier keyword.</span></span> <span data-ttu-id="8d6f9-105">`static`Klíčové slovo je také součástí [`using static`](using-static.md) direktivy.</span><span class="sxs-lookup"><span data-stu-id="8d6f9-105">The `static` keyword is also part of the [`using static`](using-static.md) directive.</span></span>

<span data-ttu-id="8d6f9-106">Použijte `static` Modifikátor k deklaraci statického člena, který patří do samotného typu, nikoli na konkrétní objekt.</span><span class="sxs-lookup"><span data-stu-id="8d6f9-106">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="8d6f9-107">`static`Modifikátor lze použít k deklaraci `static` tříd.</span><span class="sxs-lookup"><span data-stu-id="8d6f9-107">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="8d6f9-108">V třídách, rozhraních a strukturách můžete přidat `static` modifikátor pro pole, metody, vlastnosti, operátory, události a konstruktory.</span><span class="sxs-lookup"><span data-stu-id="8d6f9-108">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="8d6f9-109">`static`Modifikátor nelze použít s indexery nebo finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="8d6f9-109">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="8d6f9-110">Další informace naleznete v tématu [statické třídy a statické členy třídy](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="8d6f9-110">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example---static-class"></a><span data-ttu-id="8d6f9-111">Příklad – statická třída</span><span class="sxs-lookup"><span data-stu-id="8d6f9-111">Example - static class</span></span>

<span data-ttu-id="8d6f9-112">Následující třída je deklarována jako `static` a obsahuje pouze `static` metody:</span><span class="sxs-lookup"><span data-stu-id="8d6f9-112">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="8d6f9-113">Deklarace konstanty nebo typu je implicitně `static` členem.</span><span class="sxs-lookup"><span data-stu-id="8d6f9-113">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="8d6f9-114">Na `static` člena se nedá odkazovat prostřednictvím instance.</span><span class="sxs-lookup"><span data-stu-id="8d6f9-114">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="8d6f9-115">Místo toho je odkazováno pomocí názvu typu.</span><span class="sxs-lookup"><span data-stu-id="8d6f9-115">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="8d6f9-116">Zvažte například následující třídu:</span><span class="sxs-lookup"><span data-stu-id="8d6f9-116">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="8d6f9-117">Chcete-li odkazovat na `static` člena `x` , použijte plně kvalifikovaný název, `MyBaseC.MyStruct.x` Pokud je člen přístupný ze stejného oboru:</span><span class="sxs-lookup"><span data-stu-id="8d6f9-117">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="8d6f9-118">I když instance třídy obsahuje samostatnou kopii všech polí instance třídy, je k dispozici pouze jedna kopie každého `static` pole.</span><span class="sxs-lookup"><span data-stu-id="8d6f9-118">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="8d6f9-119">Není možné použít [`this`](this.md) k odkazování `static` metod nebo přístupových objektů vlastností.</span><span class="sxs-lookup"><span data-stu-id="8d6f9-119">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="8d6f9-120">Pokud `static` je klíčové slovo použito pro třídu, musí být všichni členové třídy `static` .</span><span class="sxs-lookup"><span data-stu-id="8d6f9-120">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="8d6f9-121">Třídy, rozhraní a `static` třídy mohou mít `static` konstruktory.</span><span class="sxs-lookup"><span data-stu-id="8d6f9-121">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="8d6f9-122">`static`Konstruktor je volán v určitém bodě mezi okamžikem spuštění programu a instancí třídy.</span><span class="sxs-lookup"><span data-stu-id="8d6f9-122">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="8d6f9-123">`static`Klíčové slovo má více omezeného použití než v jazyce C++.</span><span class="sxs-lookup"><span data-stu-id="8d6f9-123">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="8d6f9-124">Pro porovnání s klíčovým slovem jazyka C++, viz [třídy úložiště (C++)](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="8d6f9-124">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="8d6f9-125">Chcete-li předvést `static` členy, zvažte třídu, která představuje zaměstnance společnosti.</span><span class="sxs-lookup"><span data-stu-id="8d6f9-125">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="8d6f9-126">Předpokládat, že třída obsahuje metodu pro počítání zaměstnanců a pole pro uložení počtu zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="8d6f9-126">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="8d6f9-127">Jak metoda, tak pole nepatří do žádné z těchto instancí zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="8d6f9-127">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="8d6f9-128">Místo toho patří do třídy zaměstnanci jako celek.</span><span class="sxs-lookup"><span data-stu-id="8d6f9-128">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="8d6f9-129">Měly by být deklarovány jako `static` členy třídy.</span><span class="sxs-lookup"><span data-stu-id="8d6f9-129">They should be declared as `static` members of the class.</span></span>

## <a name="example---static-field-and-method"></a><span data-ttu-id="8d6f9-130">Příklad – statické pole a metoda</span><span class="sxs-lookup"><span data-stu-id="8d6f9-130">Example - static field and method</span></span>

<span data-ttu-id="8d6f9-131">Tento příklad přečte jméno a ID nového zaměstnance, zvýší čítač zaměstnanců o jednu a zobrazí informace o novém zaměstnanci a novém počtu zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="8d6f9-131">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="8d6f9-132">Tento program přečte aktuální počet zaměstnanců z klávesnice.</span><span class="sxs-lookup"><span data-stu-id="8d6f9-132">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a><span data-ttu-id="8d6f9-133">Příklad – Statická inicializace</span><span class="sxs-lookup"><span data-stu-id="8d6f9-133">Example - static initialization</span></span>

<span data-ttu-id="8d6f9-134">Tento příklad ukazuje, že můžete inicializovat `static` pole pomocí jiného `static` pole, které ještě není deklarované.</span><span class="sxs-lookup"><span data-stu-id="8d6f9-134">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="8d6f9-135">Výsledky budou nedefinovány, dokud explicitně nepřiřadíte hodnotu k `static` poli.</span><span class="sxs-lookup"><span data-stu-id="8d6f9-135">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="8d6f9-136">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8d6f9-136">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="8d6f9-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d6f9-137">See also</span></span>

- [<span data-ttu-id="8d6f9-138">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8d6f9-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8d6f9-139">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="8d6f9-139">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8d6f9-140">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8d6f9-140">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8d6f9-141">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="8d6f9-141">Modifiers</span></span>](index.md)
- [<span data-ttu-id="8d6f9-142">použití statické direktivy</span><span class="sxs-lookup"><span data-stu-id="8d6f9-142">using static directive</span></span>](using-static.md)
- [<span data-ttu-id="8d6f9-143">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="8d6f9-143">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
