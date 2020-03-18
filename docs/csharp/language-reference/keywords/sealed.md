---
title: zapečetěný modifikátor - C# Reference
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: 686afd5d9d0394bb1a802551b65083732599f384
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713102"
---
# <a name="sealed-c-reference"></a><span data-ttu-id="a8638-102">sealed (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a8638-102">sealed (C# Reference)</span></span>

<span data-ttu-id="a8638-103">Při použití na třídu `sealed` modifikátor zabraňuje dědění jiných tříd z ní.</span><span class="sxs-lookup"><span data-stu-id="a8638-103">When applied to a class, the `sealed` modifier prevents other classes from inheriting from it.</span></span> <span data-ttu-id="a8638-104">V následujícím příkladu `B` třída dědí z třídy `A`, `B`ale žádná třída může dědit z třídy .</span><span class="sxs-lookup"><span data-stu-id="a8638-104">In the following example, class `B` inherits from class `A`, but no class can inherit from class `B`.</span></span>

```csharp
class A {}
sealed class B : A {}
```

<span data-ttu-id="a8638-105">`sealed` Modifikátor můžete také použít na metodu nebo vlastnost, která přepíše virtuální metodu nebo vlastnost v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="a8638-105">You can also use the `sealed` modifier on a method or property that overrides a virtual method or property in a base class.</span></span> <span data-ttu-id="a8638-106">To umožňuje povolit třídy odvodit z vaší třídy a zabránit jim v přepsání konkrétní virtuální metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a8638-106">This enables you to allow classes to derive from your class and prevent them from overriding specific virtual methods or properties.</span></span>

## <a name="example"></a><span data-ttu-id="a8638-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8638-107">Example</span></span>

<span data-ttu-id="a8638-108">V následujícím příkladu dědí `Z` z, `Z` `Y` ale `F` nelze přepsat `X` virtuální funkce, která je deklarována a zapečetěna v `Y`.</span><span class="sxs-lookup"><span data-stu-id="a8638-108">In the following example, `Z` inherits from `Y` but `Z` cannot override the virtual function `F` that is declared in `X` and sealed in `Y`.</span></span>

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

<span data-ttu-id="a8638-109">Když definujete nové metody nebo vlastnosti ve třídě, můžete zabránit odvození tříd y jejich přepsání tím, že je nedeklarujete jako [virtuální](virtual.md).</span><span class="sxs-lookup"><span data-stu-id="a8638-109">When you define new methods or properties in a class, you can prevent deriving classes from overriding them by not declaring them as [virtual](virtual.md).</span></span>

<span data-ttu-id="a8638-110">Je chyba použít [abstraktní](abstract.md) modifikátor s zapečetěné třídy, protože abstraktní třída musí být zděděna třídou, která poskytuje implementaci abstraktnímetody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a8638-110">It is an error to use the [abstract](abstract.md) modifier with a sealed class, because an abstract class must be inherited by a class that provides an implementation of the abstract methods or properties.</span></span>

<span data-ttu-id="a8638-111">Při použití na metodu `sealed` nebo vlastnost musí být modifikátor vždy použit s [přepsáním](override.md).</span><span class="sxs-lookup"><span data-stu-id="a8638-111">When applied to a method or property, the `sealed` modifier must always be used with [override](override.md).</span></span>

<span data-ttu-id="a8638-112">Vzhledem k tomu, že struktury jsou implicitně zapečetěny, nemohou být zděděny.</span><span class="sxs-lookup"><span data-stu-id="a8638-112">Because structs are implicitly sealed, they cannot be inherited.</span></span>

<span data-ttu-id="a8638-113">Další informace naleznete v [tématu Dědičnost](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="a8638-113">For more information, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="a8638-114">Další příklady naleznete [v tématu Abstraktní a zapečetěné třídy a členy třídy](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="a8638-114">For more examples, see [Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="a8638-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8638-115">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

<span data-ttu-id="a8638-116">V předchozím příkladu se můžete pokusit dědit z zapečetěné třídy pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="a8638-116">In the previous example, you might try to inherit from the sealed class by using the following statement:</span></span>

`class MyDerivedC: SealedClass {}   // Error`

<span data-ttu-id="a8638-117">Výsledkem je chybová zpráva:</span><span class="sxs-lookup"><span data-stu-id="a8638-117">The result is an error message:</span></span>

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="remarks"></a><span data-ttu-id="a8638-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8638-118">Remarks</span></span>

<span data-ttu-id="a8638-119">Chcete-li zjistit, zda chcete zapečetit třídu, metodu nebo vlastnost, měli byste obecně zvážit následující dva body:</span><span class="sxs-lookup"><span data-stu-id="a8638-119">To determine whether to seal a class, method, or property, you should generally consider the following two points:</span></span>

- <span data-ttu-id="a8638-120">Potenciální výhody, které odvozené třídy mohou získat díky možnosti přizpůsobit třídu.</span><span class="sxs-lookup"><span data-stu-id="a8638-120">The potential benefits that deriving classes might gain through the ability to customize your class.</span></span>

- <span data-ttu-id="a8638-121">Potenciál, který odvozené třídy může změnit vaše třídy takovým způsobem, že by již pracovat správně nebo podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="a8638-121">The potential that deriving classes could modify your classes in such a way that they would no longer work correctly or as expected.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a8638-122">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a8638-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a8638-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8638-123">See also</span></span>

- [<span data-ttu-id="a8638-124">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a8638-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a8638-125">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a8638-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a8638-126">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="a8638-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a8638-127">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="a8638-127">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="a8638-128">Abstraktní a uzavřené třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="a8638-128">Abstract and Sealed Classes and Class Members</span></span>](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="a8638-129">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="a8638-129">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="a8638-130">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="a8638-130">Modifiers</span></span>](index.md)
- [<span data-ttu-id="a8638-131">override</span><span class="sxs-lookup"><span data-stu-id="a8638-131">override</span></span>](override.md)
- [<span data-ttu-id="a8638-132">virtual</span><span class="sxs-lookup"><span data-stu-id="a8638-132">virtual</span></span>](virtual.md)
