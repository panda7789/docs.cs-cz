---
title: statický modifikátor - C# Reference
ms.date: 04/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: 771bcfdac4c4bf27c15da4bc374d804405317a78
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102057"
---
# <a name="static-c-reference"></a><span data-ttu-id="18b97-102">static – modifikátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="18b97-102">static (C# Reference)</span></span>

<span data-ttu-id="18b97-103">Tato stránka `static` se zabývá klíčovým slovem modifikátoru.</span><span class="sxs-lookup"><span data-stu-id="18b97-103">This page covers the `static` modifier keyword.</span></span> <span data-ttu-id="18b97-104">Klíčové `static` slovo je také [`using static`](using-static.md) součástí směrnice.</span><span class="sxs-lookup"><span data-stu-id="18b97-104">The `static` keyword is also part of the [`using static`](using-static.md) directive.</span></span>

<span data-ttu-id="18b97-105">`static` Modifikátor použijte k deklarování statického člena, který patří k samotnému typu, nikoli k určitému objektu.</span><span class="sxs-lookup"><span data-stu-id="18b97-105">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="18b97-106">Modifikátor `static` lze deklarovat `static` třídy.</span><span class="sxs-lookup"><span data-stu-id="18b97-106">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="18b97-107">Ve třídách, rozhraních a strukturách můžete `static` přidat modifikátor do polí, metod, vlastností, operátorů, událostí a konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="18b97-107">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="18b97-108">Modifikátor `static` nelze použít s indexery nebo finalizačními metodami.</span><span class="sxs-lookup"><span data-stu-id="18b97-108">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="18b97-109">Další informace naleznete [v tématu Statické třídy a statické členy třídy](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="18b97-109">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example---static-class"></a><span data-ttu-id="18b97-110">Příklad - statická třída</span><span class="sxs-lookup"><span data-stu-id="18b97-110">Example - static class</span></span>

<span data-ttu-id="18b97-111">Následující třída je `static` deklarována jako a obsahuje pouze `static` metody:</span><span class="sxs-lookup"><span data-stu-id="18b97-111">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="18b97-112">Deklarace konstanty nebo typu `static` je implicitně členem.</span><span class="sxs-lookup"><span data-stu-id="18b97-112">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="18b97-113">Na `static` člena nelze odkazovat prostřednictvím instance.</span><span class="sxs-lookup"><span data-stu-id="18b97-113">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="18b97-114">Místo toho je odkazováno prostřednictvím názvu typu.</span><span class="sxs-lookup"><span data-stu-id="18b97-114">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="18b97-115">Zvažte například následující třídu:</span><span class="sxs-lookup"><span data-stu-id="18b97-115">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="18b97-116">Chcete-li `static` odkazovat na člen `x`, `MyBaseC.MyStruct.x`použijte plně kvalifikovaný název , , pokud člen není přístupný ze stejného oboru:</span><span class="sxs-lookup"><span data-stu-id="18b97-116">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="18b97-117">Zatímco instance třídy obsahuje samostatnou kopii všech polí instance třídy, je `static` pouze jedna kopie každého pole.</span><span class="sxs-lookup"><span data-stu-id="18b97-117">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="18b97-118">Není možné použít [`this`](this.md) k referenční `static` metody nebo přístupové objekty vlastností.</span><span class="sxs-lookup"><span data-stu-id="18b97-118">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="18b97-119">Pokud `static` je klíčové slovo použito pro třídu, musí `static`být všichni členové třídy .</span><span class="sxs-lookup"><span data-stu-id="18b97-119">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="18b97-120">Třídy, rozhraní `static` a třídy mohou mít `static` konstruktory.</span><span class="sxs-lookup"><span data-stu-id="18b97-120">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="18b97-121">Konstruktor `static` je volána v určitém okamžiku mezi spuštěním programu a instance třídy.</span><span class="sxs-lookup"><span data-stu-id="18b97-121">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="18b97-122">Klíčové `static` slovo má omezenější použití než v jazyce C++.</span><span class="sxs-lookup"><span data-stu-id="18b97-122">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="18b97-123">Chcete-li porovnat s c++ klíčové slovo, viz [Storage třídy (C++)](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="18b97-123">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="18b97-124">Chcete-li demonstrovat `static` členy, zvažte třídu, která představuje zaměstnance společnosti.</span><span class="sxs-lookup"><span data-stu-id="18b97-124">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="18b97-125">Předpokládejme, že třída obsahuje metodu počítání zaměstnanců a pole pro uložení počtu zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="18b97-125">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="18b97-126">Metoda i pole nepatří do žádné instance zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="18b97-126">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="18b97-127">Místo toho patří do třídy zaměstnanců jako celku.</span><span class="sxs-lookup"><span data-stu-id="18b97-127">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="18b97-128">Měly by `static` být deklarovány jako členové třídy.</span><span class="sxs-lookup"><span data-stu-id="18b97-128">They should be declared as `static` members of the class.</span></span>

## <a name="example---static-field-and-method"></a><span data-ttu-id="18b97-129">Příklad - statické pole a metoda</span><span class="sxs-lookup"><span data-stu-id="18b97-129">Example - static field and method</span></span>

<span data-ttu-id="18b97-130">Tento příklad přečte jméno a ID nového zaměstnance, zintáží čítač zaměstnance o jeden a zobrazí informace o novém zaměstnanci a novém počtu zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="18b97-130">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="18b97-131">Tento program čte aktuální počet zaměstnanců z klávesnice.</span><span class="sxs-lookup"><span data-stu-id="18b97-131">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a><span data-ttu-id="18b97-132">Příklad - statická inicializace</span><span class="sxs-lookup"><span data-stu-id="18b97-132">Example - static initialization</span></span>

<span data-ttu-id="18b97-133">Tento příklad ukazuje, že můžete `static` inicializovat pole pomocí jiného `static` pole, které ještě není deklarováno.</span><span class="sxs-lookup"><span data-stu-id="18b97-133">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="18b97-134">Výsledky nebudou definovány, dokud explicitně nepřiřadíte hodnotu `static` poli.</span><span class="sxs-lookup"><span data-stu-id="18b97-134">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="18b97-135">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="18b97-135">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="18b97-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="18b97-136">See also</span></span>

- [<span data-ttu-id="18b97-137">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="18b97-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="18b97-138">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="18b97-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="18b97-139">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="18b97-139">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="18b97-140">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="18b97-140">Modifiers</span></span>](index.md)
- [<span data-ttu-id="18b97-141">použití statické direktivy</span><span class="sxs-lookup"><span data-stu-id="18b97-141">using static directive</span></span>](using-static.md)
- [<span data-ttu-id="18b97-142">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="18b97-142">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
