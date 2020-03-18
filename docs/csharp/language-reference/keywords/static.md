---
title: statický modifikátor - C# Reference
ms.date: 01/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: e7671e9db488a7b50f4ed736864d6fa8d95eef1a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76744658"
---
# <a name="static-c-reference"></a><span data-ttu-id="8e340-102">static – modifikátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8e340-102">static (C# Reference)</span></span>

<span data-ttu-id="8e340-103">`static` Modifikátor použijte k deklarování statického člena, který patří k samotnému typu, nikoli k určitému objektu.</span><span class="sxs-lookup"><span data-stu-id="8e340-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="8e340-104">Modifikátor `static` lze deklarovat `static` třídy.</span><span class="sxs-lookup"><span data-stu-id="8e340-104">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="8e340-105">Ve třídách, rozhraních a strukturách můžete `static` přidat modifikátor do polí, metod, vlastností, operátorů, událostí a konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="8e340-105">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="8e340-106">Modifikátor `static` nelze použít s indexery nebo finalizačními metodami.</span><span class="sxs-lookup"><span data-stu-id="8e340-106">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="8e340-107">Další informace naleznete [v tématu Statické třídy a statické členy třídy](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="8e340-107">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="8e340-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e340-108">Example</span></span>

<span data-ttu-id="8e340-109">Následující třída je `static` deklarována jako a obsahuje pouze `static` metody:</span><span class="sxs-lookup"><span data-stu-id="8e340-109">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="8e340-110">Deklarace konstanty nebo typu `static` je implicitně členem.</span><span class="sxs-lookup"><span data-stu-id="8e340-110">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="8e340-111">Na `static` člena nelze odkazovat prostřednictvím instance.</span><span class="sxs-lookup"><span data-stu-id="8e340-111">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="8e340-112">Místo toho je odkazováno prostřednictvím názvu typu.</span><span class="sxs-lookup"><span data-stu-id="8e340-112">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="8e340-113">Zvažte například následující třídu:</span><span class="sxs-lookup"><span data-stu-id="8e340-113">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="8e340-114">Chcete-li `static` odkazovat na člen `x`, `MyBaseC.MyStruct.x`použijte plně kvalifikovaný název , , pokud člen není přístupný ze stejného oboru:</span><span class="sxs-lookup"><span data-stu-id="8e340-114">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="8e340-115">Zatímco instance třídy obsahuje samostatnou kopii všech polí instance třídy, je `static` pouze jedna kopie každého pole.</span><span class="sxs-lookup"><span data-stu-id="8e340-115">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="8e340-116">Není možné použít [`this`](this.md) k referenční `static` metody nebo přístupové objekty vlastností.</span><span class="sxs-lookup"><span data-stu-id="8e340-116">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="8e340-117">Pokud `static` je klíčové slovo použito pro třídu, musí `static`být všichni členové třídy .</span><span class="sxs-lookup"><span data-stu-id="8e340-117">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="8e340-118">Třídy, rozhraní `static` a třídy mohou mít `static` konstruktory.</span><span class="sxs-lookup"><span data-stu-id="8e340-118">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="8e340-119">Konstruktor `static` je volána v určitém okamžiku mezi spuštěním programu a instance třídy.</span><span class="sxs-lookup"><span data-stu-id="8e340-119">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="8e340-120">Klíčové `static` slovo má omezenější použití než v jazyce C++.</span><span class="sxs-lookup"><span data-stu-id="8e340-120">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="8e340-121">Chcete-li porovnat s c++ klíčové slovo, viz [Storage třídy (C++)](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="8e340-121">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="8e340-122">Chcete-li demonstrovat `static` členy, zvažte třídu, která představuje zaměstnance společnosti.</span><span class="sxs-lookup"><span data-stu-id="8e340-122">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="8e340-123">Předpokládejme, že třída obsahuje metodu počítání zaměstnanců a pole pro uložení počtu zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="8e340-123">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="8e340-124">Metoda i pole nepatří do žádné instance zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="8e340-124">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="8e340-125">Místo toho patří do třídy zaměstnanců jako celku.</span><span class="sxs-lookup"><span data-stu-id="8e340-125">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="8e340-126">Měly by `static` být deklarovány jako členové třídy.</span><span class="sxs-lookup"><span data-stu-id="8e340-126">They should be declared as `static` members of the class.</span></span>

## <a name="example"></a><span data-ttu-id="8e340-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e340-127">Example</span></span>

<span data-ttu-id="8e340-128">Tento příklad přečte jméno a ID nového zaměstnance, zintáží čítač zaměstnance o jeden a zobrazí informace o novém zaměstnanci a novém počtu zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="8e340-128">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="8e340-129">Tento program čte aktuální počet zaměstnanců z klávesnice.</span><span class="sxs-lookup"><span data-stu-id="8e340-129">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a><span data-ttu-id="8e340-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e340-130">Example</span></span>

<span data-ttu-id="8e340-131">Tento příklad ukazuje, že můžete `static` inicializovat pole pomocí jiného `static` pole, které ještě není deklarováno.</span><span class="sxs-lookup"><span data-stu-id="8e340-131">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="8e340-132">Výsledky nebudou definovány, dokud explicitně nepřiřadíte hodnotu `static` poli.</span><span class="sxs-lookup"><span data-stu-id="8e340-132">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="8e340-133">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8e340-133">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="8e340-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e340-134">See also</span></span>

- [<span data-ttu-id="8e340-135">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8e340-135">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8e340-136">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8e340-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8e340-137">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="8e340-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8e340-138">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="8e340-138">Modifiers</span></span>](index.md)
- [<span data-ttu-id="8e340-139">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="8e340-139">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
