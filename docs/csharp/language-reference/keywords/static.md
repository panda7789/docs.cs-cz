---
title: statický modifikátor – C# referenční informace
ms.date: 01/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: e7671e9db488a7b50f4ed736864d6fa8d95eef1a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744658"
---
# <a name="static-c-reference"></a><span data-ttu-id="8d09d-102">static – modifikátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8d09d-102">static (C# Reference)</span></span>

<span data-ttu-id="8d09d-103">Použijte modifikátor `static` k deklaraci statického člena, který patří do samotného typu, nikoli na konkrétní objekt.</span><span class="sxs-lookup"><span data-stu-id="8d09d-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="8d09d-104">Modifikátor `static` lze použít k deklarování `static` tříd.</span><span class="sxs-lookup"><span data-stu-id="8d09d-104">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="8d09d-105">V třídách, rozhraních a strukturách můžete přidat modifikátor `static` do polí, metod, vlastností, operátorů, událostí a konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="8d09d-105">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="8d09d-106">Modifikátor `static` nelze použít s indexery nebo finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="8d09d-106">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="8d09d-107">Další informace naleznete v tématu [statické třídy a statické členy třídy](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="8d09d-107">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="8d09d-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d09d-108">Example</span></span>

<span data-ttu-id="8d09d-109">Následující třída je deklarována jako `static` a obsahuje pouze `static` metody:</span><span class="sxs-lookup"><span data-stu-id="8d09d-109">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="8d09d-110">Deklarace konstanty nebo typu je implicitně `static` člen.</span><span class="sxs-lookup"><span data-stu-id="8d09d-110">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="8d09d-111">Na člena `static` nelze odkazovat prostřednictvím instance.</span><span class="sxs-lookup"><span data-stu-id="8d09d-111">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="8d09d-112">Místo toho je odkazováno pomocí názvu typu.</span><span class="sxs-lookup"><span data-stu-id="8d09d-112">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="8d09d-113">Zvažte například následující třídu:</span><span class="sxs-lookup"><span data-stu-id="8d09d-113">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="8d09d-114">Chcete-li odkazovat na `static` členský `x`, použijte plně kvalifikovaný název `MyBaseC.MyStruct.x`, pokud je člen přístupný ze stejného rozsahu:</span><span class="sxs-lookup"><span data-stu-id="8d09d-114">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="8d09d-115">I když instance třídy obsahuje samostatnou kopii všech polí instance třídy, je k dispozici pouze jedna kopie každého pole `static`.</span><span class="sxs-lookup"><span data-stu-id="8d09d-115">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="8d09d-116">Není možné použít [`this`](this.md) k odkazování na `static` metod nebo přístupových objektů vlastností.</span><span class="sxs-lookup"><span data-stu-id="8d09d-116">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="8d09d-117">Pokud je klíčové slovo `static` použito pro třídu, musí být všichni členové třídy `static`.</span><span class="sxs-lookup"><span data-stu-id="8d09d-117">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="8d09d-118">Třídy, rozhraní a `static` třídy mohou mít `static` konstruktory.</span><span class="sxs-lookup"><span data-stu-id="8d09d-118">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="8d09d-119">`static` konstruktor je volán v určitém bodě mezi okamžikem spuštění programu a instancí třídy.</span><span class="sxs-lookup"><span data-stu-id="8d09d-119">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="8d09d-120">Klíčové slovo `static` má více omezeného použití než C++v.</span><span class="sxs-lookup"><span data-stu-id="8d09d-120">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="8d09d-121">Pro porovnání s C++ klíčovým slovem, viz [třídyC++úložiště ()](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="8d09d-121">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="8d09d-122">K předvedení `static`ch členů zvažte třídu, která představuje zaměstnance společnosti.</span><span class="sxs-lookup"><span data-stu-id="8d09d-122">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="8d09d-123">Předpokládat, že třída obsahuje metodu pro počítání zaměstnanců a pole pro uložení počtu zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="8d09d-123">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="8d09d-124">Jak metoda, tak pole nepatří do žádné z těchto instancí zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="8d09d-124">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="8d09d-125">Místo toho patří do třídy zaměstnanci jako celek.</span><span class="sxs-lookup"><span data-stu-id="8d09d-125">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="8d09d-126">Měly by být deklarovány jako `static` členy třídy.</span><span class="sxs-lookup"><span data-stu-id="8d09d-126">They should be declared as `static` members of the class.</span></span>

## <a name="example"></a><span data-ttu-id="8d09d-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d09d-127">Example</span></span>

<span data-ttu-id="8d09d-128">Tento příklad přečte jméno a ID nového zaměstnance, zvýší čítač zaměstnanců o jednu a zobrazí informace o novém zaměstnanci a novém počtu zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="8d09d-128">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="8d09d-129">Tento program přečte aktuální počet zaměstnanců z klávesnice.</span><span class="sxs-lookup"><span data-stu-id="8d09d-129">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a><span data-ttu-id="8d09d-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d09d-130">Example</span></span>

<span data-ttu-id="8d09d-131">Tento příklad ukazuje, že můžete inicializovat pole `static` pomocí jiného pole `static`, které ještě není deklarované.</span><span class="sxs-lookup"><span data-stu-id="8d09d-131">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="8d09d-132">Výsledky nebudou definovány, dokud explicitně nepřiřadíte hodnotu poli `static`.</span><span class="sxs-lookup"><span data-stu-id="8d09d-132">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="8d09d-133">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8d09d-133">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="8d09d-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d09d-134">See also</span></span>

- [<span data-ttu-id="8d09d-135">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="8d09d-135">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8d09d-136">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8d09d-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8d09d-137">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8d09d-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8d09d-138">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="8d09d-138">Modifiers</span></span>](index.md)
- [<span data-ttu-id="8d09d-139">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="8d09d-139">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
