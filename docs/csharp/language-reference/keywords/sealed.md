---
title: sealed (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: 674c7e1cd87b95318f739ab22876f4bfe5ae73d8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514026"
---
# <a name="sealed-c-reference"></a><span data-ttu-id="4c2fe-102">sealed (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4c2fe-102">sealed (C# Reference)</span></span>
<span data-ttu-id="4c2fe-103">Při použití na třídu, `sealed` modifikátor zabrání ostatním třídám z něj dědí.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-103">When applied to a class, the `sealed` modifier prevents other classes from inheriting from it.</span></span> <span data-ttu-id="4c2fe-104">V následujícím příkladu třída `B` dědí z třídy `A`, ale žádná třída může dědit z třídy `B`.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-104">In the following example, class `B` inherits from class `A`, but no class can inherit from class `B`.</span></span>  
  
```csharp  
class A {}      
sealed class B : A {}  
```  
  
 <span data-ttu-id="4c2fe-105">Můžete také použít `sealed` modifikátor na metodu nebo vlastnost, která přepíše virtuální metody nebo vlastnosti v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-105">You can also use the `sealed` modifier on a method or property that overrides a virtual method or property in a base class.</span></span> <span data-ttu-id="4c2fe-106">To umožňuje povolit třídy, které jsou odvozeny z vaší třídy a zabránili jejich přepsání konkrétní virtuální metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-106">This enables you to allow classes to derive from your class and prevent them from overriding specific virtual methods or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c2fe-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="4c2fe-107">Example</span></span>  
 <span data-ttu-id="4c2fe-108">V následujícím příkladu `Z` dědí z `Y` ale `Z` nemůže přepsat virtuální funkci `F` , která je deklarována v `X` a uzavřené v `Y`.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-108">In the following example, `Z` inherits from `Y` but `Z` cannot override the virtual function `F` that is declared in `X` and sealed in `Y`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_1.cs)]  
  
 <span data-ttu-id="4c2fe-109">Při definování nové metody nebo vlastnosti ve třídě, můžete zabránit odvozená třídy přepsání není deklarací je jako [virtuální](../../../csharp/language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="4c2fe-109">When you define new methods or properties in a class, you can prevent deriving classes from overriding them by not declaring them as [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>  
  
 <span data-ttu-id="4c2fe-110">Jedná se o chybu používat [abstraktní](../../../csharp/language-reference/keywords/abstract.md) modifikátor zapečetěnou třídu, protože abstraktní třídy musí být zděděny třídu, která poskytuje implementaci abstraktní metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-110">It is an error to use the [abstract](../../../csharp/language-reference/keywords/abstract.md) modifier with a sealed class, because an abstract class must be inherited by a class that provides an implementation of the abstract methods or properties.</span></span>  
  
 <span data-ttu-id="4c2fe-111">Při použití na metodu nebo vlastnost, `sealed` modifikátor musí být vždy použit s [přepsat](../../../csharp/language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="4c2fe-111">When applied to a method or property, the `sealed` modifier must always be used with [override](../../../csharp/language-reference/keywords/override.md).</span></span>  
  
 <span data-ttu-id="4c2fe-112">Protože struktury jsou implicitně zapečetěná, nelze dědit.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-112">Because structs are implicitly sealed, they cannot be inherited.</span></span>  
  
 <span data-ttu-id="4c2fe-113">Další informace najdete v tématu [dědičnosti](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="4c2fe-113">For more information, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span>  
  
 <span data-ttu-id="4c2fe-114">Další příklady najdete v tématu [abstraktní a zapečetěné třídy a členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="4c2fe-114">For more examples, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c2fe-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="4c2fe-115">Example</span></span>  
 [!code-csharp[csrefKeywordsModifiers#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_2.cs)]  
  
 <span data-ttu-id="4c2fe-116">V předchozím příkladu můžete vyzkoušet dědit od zapečetěné třídy pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="4c2fe-116">In the previous example, you might try to inherit from the sealed class by using the following statement:</span></span>  
  
 `class MyDerivedC: SealedClass {}   // Error`  
  
 <span data-ttu-id="4c2fe-117">Výsledek se zobrazí chybová zpráva:</span><span class="sxs-lookup"><span data-stu-id="4c2fe-117">The result is an error message:</span></span>  
  
 `'MyDerivedC': cannot derive from sealed type 'SealedClass'`  
  
## <a name="c-language-specification"></a><span data-ttu-id="4c2fe-118">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4c2fe-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="remarks"></a><span data-ttu-id="4c2fe-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4c2fe-119">Remarks</span></span>  
 <span data-ttu-id="4c2fe-120">Pokud chcete zjistit, jestli se má zapečetit třídy, metody nebo vlastnosti, obecně byste měli zvážit následující dva body:</span><span class="sxs-lookup"><span data-stu-id="4c2fe-120">To determine whether to seal a class, method, or property, you should generally consider the following two points:</span></span>  
  
-   <span data-ttu-id="4c2fe-121">Potenciálních výhod, že odvozené třídy mohou získat prostřednictvím možnost přizpůsobit si své třídy.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-121">The potential benefits that deriving classes might gain through the ability to customize your class.</span></span>  
  
-   <span data-ttu-id="4c2fe-122">Potenciál odvozené třídy může změnit tříd takovým způsobem, že by už nebude fungovat správně nebo jako očekává.</span><span class="sxs-lookup"><span data-stu-id="4c2fe-122">The potential that deriving classes could modify your classes in such a way that they would no longer work correctly or as expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c2fe-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="4c2fe-123">See Also</span></span>

- [<span data-ttu-id="4c2fe-124">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4c2fe-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="4c2fe-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4c2fe-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="4c2fe-126">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4c2fe-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="4c2fe-127">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="4c2fe-127">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
- [<span data-ttu-id="4c2fe-128">Abstraktní a uzavřené třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="4c2fe-128">Abstract and Sealed Classes and Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [<span data-ttu-id="4c2fe-129">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="4c2fe-129">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [<span data-ttu-id="4c2fe-130">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="4c2fe-130">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
- [<span data-ttu-id="4c2fe-131">override</span><span class="sxs-lookup"><span data-stu-id="4c2fe-131">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
- [<span data-ttu-id="4c2fe-132">virtual</span><span class="sxs-lookup"><span data-stu-id="4c2fe-132">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)
