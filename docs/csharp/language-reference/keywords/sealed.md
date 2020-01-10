---
title: zapečetěný modifikátor C# – referenční informace
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: 686afd5d9d0394bb1a802551b65083732599f384
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713102"
---
# <a name="sealed-c-reference"></a><span data-ttu-id="2fc27-102">sealed (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2fc27-102">sealed (C# Reference)</span></span>

<span data-ttu-id="2fc27-103">Při použití na třídu brání modifikátoru `sealed`, aby z něho dědily jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="2fc27-103">When applied to a class, the `sealed` modifier prevents other classes from inheriting from it.</span></span> <span data-ttu-id="2fc27-104">V následujícím příkladu třída `B` dědí z třídy `A`, ale žádná třída nemůže dědit ze třídy `B`.</span><span class="sxs-lookup"><span data-stu-id="2fc27-104">In the following example, class `B` inherits from class `A`, but no class can inherit from class `B`.</span></span>

```csharp
class A {}
sealed class B : A {}
```

<span data-ttu-id="2fc27-105">Můžete také použít modifikátor `sealed` pro metodu nebo vlastnost, která přepisuje virtuální metodu nebo vlastnost v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="2fc27-105">You can also use the `sealed` modifier on a method or property that overrides a virtual method or property in a base class.</span></span> <span data-ttu-id="2fc27-106">To umožňuje, aby třídy byly odvozeny z vaší třídy a aby se zabránilo přepsání specifických virtuálních metod nebo vlastností.</span><span class="sxs-lookup"><span data-stu-id="2fc27-106">This enables you to allow classes to derive from your class and prevent them from overriding specific virtual methods or properties.</span></span>

## <a name="example"></a><span data-ttu-id="2fc27-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="2fc27-107">Example</span></span>

<span data-ttu-id="2fc27-108">V následujícím příkladu `Z` dědí z `Y`, ale `Z` nemůže přepsat virtuální funkci `F`, která je deklarována v `X` a zapečetěná v `Y`.</span><span class="sxs-lookup"><span data-stu-id="2fc27-108">In the following example, `Z` inherits from `Y` but `Z` cannot override the virtual function `F` that is declared in `X` and sealed in `Y`.</span></span>

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

<span data-ttu-id="2fc27-109">Při definování nových metod nebo vlastností ve třídě můžete zabránit odvození tříd z jejich přepsání jejich jejich deklarováním jako [Virtual](virtual.md).</span><span class="sxs-lookup"><span data-stu-id="2fc27-109">When you define new methods or properties in a class, you can prevent deriving classes from overriding them by not declaring them as [virtual](virtual.md).</span></span>

<span data-ttu-id="2fc27-110">Použití modifikátoru [abstract](abstract.md) s zapečetěnou třídou je chybné, protože abstraktní třída musí být zděděna třídou, která poskytuje implementaci abstraktních metod nebo vlastností.</span><span class="sxs-lookup"><span data-stu-id="2fc27-110">It is an error to use the [abstract](abstract.md) modifier with a sealed class, because an abstract class must be inherited by a class that provides an implementation of the abstract methods or properties.</span></span>

<span data-ttu-id="2fc27-111">Při použití na metodu nebo vlastnost musí být modifikátor `sealed` vždy použit s [přepsáním](override.md).</span><span class="sxs-lookup"><span data-stu-id="2fc27-111">When applied to a method or property, the `sealed` modifier must always be used with [override](override.md).</span></span>

<span data-ttu-id="2fc27-112">Protože jsou struktury implicitně zapečetěné, nedají se dědit.</span><span class="sxs-lookup"><span data-stu-id="2fc27-112">Because structs are implicitly sealed, they cannot be inherited.</span></span>

<span data-ttu-id="2fc27-113">Další informace najdete v tématu [Dědičnost](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="2fc27-113">For more information, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="2fc27-114">Další příklady naleznete v tématu [abstraktní a zapečetěné třídy a členy třídy](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="2fc27-114">For more examples, see [Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="2fc27-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="2fc27-115">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

<span data-ttu-id="2fc27-116">V předchozím příkladu se můžete pokusit dědit z zapečetěné třídy pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="2fc27-116">In the previous example, you might try to inherit from the sealed class by using the following statement:</span></span>

`class MyDerivedC: SealedClass {}   // Error`

<span data-ttu-id="2fc27-117">Výsledkem je chybová zpráva:</span><span class="sxs-lookup"><span data-stu-id="2fc27-117">The result is an error message:</span></span>

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="remarks"></a><span data-ttu-id="2fc27-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2fc27-118">Remarks</span></span>

<span data-ttu-id="2fc27-119">Chcete-li určit, zda má být třída, metoda nebo vlastnost zapečetěna, je třeba vzít v úvahu následující dva body:</span><span class="sxs-lookup"><span data-stu-id="2fc27-119">To determine whether to seal a class, method, or property, you should generally consider the following two points:</span></span>

- <span data-ttu-id="2fc27-120">Potenciální výhody, které odvozují třídy, mohou získat možnost přizpůsobení vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="2fc27-120">The potential benefits that deriving classes might gain through the ability to customize your class.</span></span>

- <span data-ttu-id="2fc27-121">Potenciál, který odvozují třídy, může upravit vaše třídy takovým způsobem, že by již nepracovaly správně nebo podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="2fc27-121">The potential that deriving classes could modify your classes in such a way that they would no longer work correctly or as expected.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2fc27-122">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2fc27-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="2fc27-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2fc27-123">See also</span></span>

- [<span data-ttu-id="2fc27-124">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="2fc27-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2fc27-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2fc27-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2fc27-126">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2fc27-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="2fc27-127">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="2fc27-127">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="2fc27-128">Abstraktní a uzavřené třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="2fc27-128">Abstract and Sealed Classes and Class Members</span></span>](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="2fc27-129">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="2fc27-129">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="2fc27-130">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="2fc27-130">Modifiers</span></span>](index.md)
- [<span data-ttu-id="2fc27-131">override</span><span class="sxs-lookup"><span data-stu-id="2fc27-131">override</span></span>](override.md)
- [<span data-ttu-id="2fc27-132">virtual</span><span class="sxs-lookup"><span data-stu-id="2fc27-132">virtual</span></span>](virtual.md)
