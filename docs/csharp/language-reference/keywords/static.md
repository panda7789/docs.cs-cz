---
title: statický modifikátor – C# referenční informace
ms.date: 07/20/2015
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: f4ca3fcf809e723d2144654f1da949eb4d6de1b4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713063"
---
# <a name="static-c-reference"></a><span data-ttu-id="346da-102">static – modifikátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="346da-102">static (C# Reference)</span></span>

<span data-ttu-id="346da-103">Použijte modifikátor `static` k deklaraci statického člena, který patří do samotného typu, nikoli na konkrétní objekt.</span><span class="sxs-lookup"><span data-stu-id="346da-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="346da-104">Modifikátor `static` lze použít s třídami, poli, metodami, vlastnostmi, operátory, událostmi a konstruktory, ale nelze jej použít s indexery, finalizačními metodami nebo jinými typy než třídy.</span><span class="sxs-lookup"><span data-stu-id="346da-104">The `static` modifier can be used with classes, fields, methods, properties, operators, events, and constructors, but it cannot be used with indexers, finalizers, or types other than classes.</span></span> <span data-ttu-id="346da-105">Další informace naleznete v tématu [statické třídy a statické členy třídy](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="346da-105">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="346da-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="346da-106">Example</span></span>

<span data-ttu-id="346da-107">Následující třída je deklarována jako `static` a obsahuje pouze `static` metody:</span><span class="sxs-lookup"><span data-stu-id="346da-107">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="346da-108">Deklarace konstanty nebo typu je implicitně statickým členem.</span><span class="sxs-lookup"><span data-stu-id="346da-108">A constant or type declaration is implicitly a static member.</span></span>

<span data-ttu-id="346da-109">Na statický člen se nedá odkazovat prostřednictvím instance.</span><span class="sxs-lookup"><span data-stu-id="346da-109">A static member cannot be referenced through an instance.</span></span> <span data-ttu-id="346da-110">Místo toho je odkazováno prostřednictvím názvu typu.</span><span class="sxs-lookup"><span data-stu-id="346da-110">Instead, it is referenced through the type name.</span></span> <span data-ttu-id="346da-111">Zvažte například následující třídu:</span><span class="sxs-lookup"><span data-stu-id="346da-111">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="346da-112">Chcete-li odkazovat na statický členský `x`, použijte plně kvalifikovaný název, `MyBaseC.MyStruct.x`, pokud je člen přístupný ze stejného rozsahu:</span><span class="sxs-lookup"><span data-stu-id="346da-112">To refer to the static member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="346da-113">I když instance třídy obsahuje samostatnou kopii všech polí instance třídy, je k dispozici pouze jedna kopie každého statického pole.</span><span class="sxs-lookup"><span data-stu-id="346da-113">While an instance of a class contains a separate copy of all instance fields of the class, there is only one copy of each static field.</span></span>

<span data-ttu-id="346da-114">[Tuto](this.md) možnost nelze použít pro odkazování statických metod nebo přístupových objektů vlastností.</span><span class="sxs-lookup"><span data-stu-id="346da-114">It is not possible to use [this](this.md) to reference static methods or property accessors.</span></span>

<span data-ttu-id="346da-115">Pokud je klíčové slovo `static` použito pro třídu, všechny členy třídy musí být statické.</span><span class="sxs-lookup"><span data-stu-id="346da-115">If the `static` keyword is applied to a class, all the members of the class must be static.</span></span>

<span data-ttu-id="346da-116">Třídy a statické třídy mohou mít statické konstruktory.</span><span class="sxs-lookup"><span data-stu-id="346da-116">Classes and static classes may have static constructors.</span></span> <span data-ttu-id="346da-117">Statické konstruktory jsou volány v určitém bodě mezi okamžikem spuštění programu a instance třídy.</span><span class="sxs-lookup"><span data-stu-id="346da-117">Static constructors are called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="346da-118">Klíčové slovo `static` má více omezeného použití než C++v.</span><span class="sxs-lookup"><span data-stu-id="346da-118">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="346da-119">Pro porovnání s C++ klíčovým slovem, viz [třídyC++úložiště ()](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="346da-119">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="346da-120">Chcete-li předvést statické členy, zvažte třídu, která představuje zaměstnance společnosti.</span><span class="sxs-lookup"><span data-stu-id="346da-120">To demonstrate static members, consider a class that represents a company employee.</span></span> <span data-ttu-id="346da-121">Předpokládat, že třída obsahuje metodu pro počítání zaměstnanců a pole pro uložení počtu zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="346da-121">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="346da-122">Jak metoda, tak pole nepatří žádnému zaměstnanci instance.</span><span class="sxs-lookup"><span data-stu-id="346da-122">Both the method and the field do not belong to any instance employee.</span></span> <span data-ttu-id="346da-123">Místo toho patří do třídy Company.</span><span class="sxs-lookup"><span data-stu-id="346da-123">Instead they belong to the company class.</span></span> <span data-ttu-id="346da-124">Proto by měly být deklarovány jako statické členy třídy.</span><span class="sxs-lookup"><span data-stu-id="346da-124">Therefore, they should be declared as static members of the class.</span></span>

## <a name="example"></a><span data-ttu-id="346da-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="346da-125">Example</span></span>

<span data-ttu-id="346da-126">Tento příklad přečte jméno a ID nového zaměstnance, zvýší čítač zaměstnanců o jednu a zobrazí informace o novém zaměstnanci a novém počtu zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="346da-126">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="346da-127">Pro zjednodušení tento program přečte aktuální počet zaměstnanců z klávesnice.</span><span class="sxs-lookup"><span data-stu-id="346da-127">For simplicity, this program reads the current number of employees from the keyboard.</span></span> <span data-ttu-id="346da-128">V reálné aplikaci by měly být tyto informace čteny ze souboru.</span><span class="sxs-lookup"><span data-stu-id="346da-128">In a real application, this information should be read from a file.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a><span data-ttu-id="346da-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="346da-129">Example</span></span>

<span data-ttu-id="346da-130">Tento příklad ukazuje, že i když můžete inicializovat statické pole pomocí jiného statického pole, které dosud nebylo deklarováno, výsledky budou nedefinovány, dokud explicitně nepřiřadíte hodnotu do statického pole.</span><span class="sxs-lookup"><span data-stu-id="346da-130">This example shows that although you can initialize a static field by using another static field not yet declared, the results will be undefined until you explicitly assign a value to the static field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="346da-131">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="346da-131">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="346da-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="346da-132">See also</span></span>

- [<span data-ttu-id="346da-133">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="346da-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="346da-134">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="346da-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="346da-135">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="346da-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="346da-136">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="346da-136">Modifiers</span></span>](index.md)
- [<span data-ttu-id="346da-137">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="346da-137">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
