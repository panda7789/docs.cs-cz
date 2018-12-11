---
title: zapečetěné modifikátor - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: babad3b07c5faea1381e6af13d3c713122de2332
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235173"
---
# <a name="sealed-c-reference"></a><span data-ttu-id="c962e-102">sealed (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c962e-102">sealed (C# Reference)</span></span>

<span data-ttu-id="c962e-103">Při použití na třídu, `sealed` modifikátor zabrání ostatním třídám z něj dědí.</span><span class="sxs-lookup"><span data-stu-id="c962e-103">When applied to a class, the `sealed` modifier prevents other classes from inheriting from it.</span></span> <span data-ttu-id="c962e-104">V následujícím příkladu třída `B` dědí z třídy `A`, ale žádná třída může dědit z třídy `B`.</span><span class="sxs-lookup"><span data-stu-id="c962e-104">In the following example, class `B` inherits from class `A`, but no class can inherit from class `B`.</span></span>

```csharp
class A {}
sealed class B : A {}
```

<span data-ttu-id="c962e-105">Můžete také použít `sealed` modifikátor na metodu nebo vlastnost, která přepíše virtuální metody nebo vlastnosti v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="c962e-105">You can also use the `sealed` modifier on a method or property that overrides a virtual method or property in a base class.</span></span> <span data-ttu-id="c962e-106">To umožňuje povolit třídy, které jsou odvozeny z vaší třídy a zabránili jejich přepsání konkrétní virtuální metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c962e-106">This enables you to allow classes to derive from your class and prevent them from overriding specific virtual methods or properties.</span></span>

## <a name="example"></a><span data-ttu-id="c962e-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="c962e-107">Example</span></span>

<span data-ttu-id="c962e-108">V následujícím příkladu `Z` dědí z `Y` ale `Z` nemůže přepsat virtuální funkci `F` , která je deklarována v `X` a uzavřené v `Y`.</span><span class="sxs-lookup"><span data-stu-id="c962e-108">In the following example, `Z` inherits from `Y` but `Z` cannot override the virtual function `F` that is declared in `X` and sealed in `Y`.</span></span>

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

<span data-ttu-id="c962e-109">Při definování nové metody nebo vlastnosti ve třídě, můžete zabránit odvozená třídy přepsání není deklarací je jako [virtuální](virtual.md).</span><span class="sxs-lookup"><span data-stu-id="c962e-109">When you define new methods or properties in a class, you can prevent deriving classes from overriding them by not declaring them as [virtual](virtual.md).</span></span>

<span data-ttu-id="c962e-110">Jedná se o chybu používat [abstraktní](abstract.md) modifikátor zapečetěnou třídu, protože abstraktní třídy musí být zděděny třídu, která poskytuje implementaci abstraktní metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c962e-110">It is an error to use the [abstract](abstract.md) modifier with a sealed class, because an abstract class must be inherited by a class that provides an implementation of the abstract methods or properties.</span></span>

<span data-ttu-id="c962e-111">Při použití na metodu nebo vlastnost, `sealed` modifikátor musí být vždy použit s [přepsat](override.md).</span><span class="sxs-lookup"><span data-stu-id="c962e-111">When applied to a method or property, the `sealed` modifier must always be used with [override](override.md).</span></span>

<span data-ttu-id="c962e-112">Protože struktury jsou implicitně zapečetěná, nelze dědit.</span><span class="sxs-lookup"><span data-stu-id="c962e-112">Because structs are implicitly sealed, they cannot be inherited.</span></span>

<span data-ttu-id="c962e-113">Další informace najdete v tématu [dědičnosti](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="c962e-113">For more information, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="c962e-114">Další příklady najdete v tématu [abstraktní a zapečetěné třídy a členové](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="c962e-114">For more examples, see [Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="c962e-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="c962e-115">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

<span data-ttu-id="c962e-116">V předchozím příkladu můžete vyzkoušet dědit od zapečetěné třídy pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="c962e-116">In the previous example, you might try to inherit from the sealed class by using the following statement:</span></span>

`class MyDerivedC: SealedClass {}   // Error`

<span data-ttu-id="c962e-117">Výsledek se zobrazí chybová zpráva:</span><span class="sxs-lookup"><span data-stu-id="c962e-117">The result is an error message:</span></span>

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="c-language-specification"></a><span data-ttu-id="c962e-118">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c962e-118">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="remarks"></a><span data-ttu-id="c962e-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c962e-119">Remarks</span></span>

<span data-ttu-id="c962e-120">Pokud chcete zjistit, jestli se má zapečetit třídy, metody nebo vlastnosti, obecně byste měli zvážit následující dva body:</span><span class="sxs-lookup"><span data-stu-id="c962e-120">To determine whether to seal a class, method, or property, you should generally consider the following two points:</span></span>

- <span data-ttu-id="c962e-121">Potenciálních výhod, že odvozené třídy mohou získat prostřednictvím možnost přizpůsobit si své třídy.</span><span class="sxs-lookup"><span data-stu-id="c962e-121">The potential benefits that deriving classes might gain through the ability to customize your class.</span></span>

- <span data-ttu-id="c962e-122">Potenciál odvozené třídy může změnit tříd takovým způsobem, že by už nebude fungovat správně nebo jako očekává.</span><span class="sxs-lookup"><span data-stu-id="c962e-122">The potential that deriving classes could modify your classes in such a way that they would no longer work correctly or as expected.</span></span>

## <a name="see-also"></a><span data-ttu-id="c962e-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c962e-123">See also</span></span>

- [<span data-ttu-id="c962e-124">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c962e-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c962e-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c962e-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c962e-126">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c962e-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c962e-127">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="c962e-127">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="c962e-128">Abstraktní a uzavřené třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="c962e-128">Abstract and Sealed Classes and Class Members</span></span>](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="c962e-129">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="c962e-129">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="c962e-130">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="c962e-130">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="c962e-131">override</span><span class="sxs-lookup"><span data-stu-id="c962e-131">override</span></span>](override.md)
- [<span data-ttu-id="c962e-132">virtual</span><span class="sxs-lookup"><span data-stu-id="c962e-132">virtual</span></span>](virtual.md)