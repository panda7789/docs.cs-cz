---
title: Obecné třídy – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: 5f898bf342c8596d9dd4cc0b03396aec4dcf545c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710755"
---
# <a name="generic-classes-c-programming-guide"></a><span data-ttu-id="d93fd-102">Obecné třídy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="d93fd-102">Generic Classes (C# Programming Guide)</span></span>
<span data-ttu-id="d93fd-103">Obecné třídy zapouzdření operace, které nejsou specifické pro konkrétní data typu.</span><span class="sxs-lookup"><span data-stu-id="d93fd-103">Generic classes encapsulate operations that are not specific to a particular data type.</span></span> <span data-ttu-id="d93fd-104">Nejběžnějším využitím obecných tříd je s kolekcí jako propojené seznamy zatřiďovacích tabulek, zásobníků, front, stromy a tak dále.</span><span class="sxs-lookup"><span data-stu-id="d93fd-104">The most common use for generic classes is with collections like linked lists, hash tables, stacks, queues, trees, and so on.</span></span> <span data-ttu-id="d93fd-105">Operace, jako jsou přidávání a odebírání položek z kolekce jsou prováděny v podstatě stejným způsobem bez ohledu na typ data ukládat.</span><span class="sxs-lookup"><span data-stu-id="d93fd-105">Operations such as adding and removing items from the collection are performed in basically the same way regardless of the type of data being stored.</span></span>  
  
 <span data-ttu-id="d93fd-106">Doporučený postup pro většinu scénářů, které vyžadují třídy kolekcí, je použít dotazy k dispozici v knihovně tříd rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="d93fd-106">For most scenarios that require collection classes, the recommended approach is to use the ones provided in the .NET class library.</span></span> <span data-ttu-id="d93fd-107">Další informace o použití těchto tříd naleznete v tématu [obecné kolekce na platformě .NET](../../../standard/generics/collections.md).</span><span class="sxs-lookup"><span data-stu-id="d93fd-107">For more information about using these classes, see [Generic Collections in .NET](../../../standard/generics/collections.md).</span></span>  
  
 <span data-ttu-id="d93fd-108">Obvykle vytvoříte obecných tříd od existující konkrétní třídy a změnou typy do parametry typu jeden po druhém, dokud se nedostanete optimální rovnováhu mezi Generalizace a použitelnost.</span><span class="sxs-lookup"><span data-stu-id="d93fd-108">Typically, you create generic classes by starting with an existing concrete class, and changing types into type parameters one at a time until you reach the optimal balance of generalization and usability.</span></span> <span data-ttu-id="d93fd-109">Při vytváření vlastní obecných tříd, důležité informace patří:</span><span class="sxs-lookup"><span data-stu-id="d93fd-109">When creating your own generic classes, important considerations include the following:</span></span>  
  
- <span data-ttu-id="d93fd-110">Jaké typy generalize do parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="d93fd-110">Which types to generalize into type parameters.</span></span>  
  
     <span data-ttu-id="d93fd-111">Váš kód bude jako pravidlo, další typy, které můžete parametrizovat, více flexibilní a opakovaně použitelné.</span><span class="sxs-lookup"><span data-stu-id="d93fd-111">As a rule, the more types you can parameterize, the more flexible and reusable your code becomes.</span></span> <span data-ttu-id="d93fd-112">Příliš mnoho generalizace však můžete vytvořit kód, který je obtížné pro jiné vývojáře pro čtení nebo pochopit.</span><span class="sxs-lookup"><span data-stu-id="d93fd-112">However, too much generalization can create code that is difficult for other developers to read or understand.</span></span>  
  
- <span data-ttu-id="d93fd-113">Jaká omezení, pokud chcete použít pro parametry typu (viz [omezení parametrů typů](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="d93fd-113">What constraints, if any, to apply to the type parameters (See [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)).</span></span>  
  
     <span data-ttu-id="d93fd-114">Pravidlo vhodné je použít maximální možné omezení, která bude stále umožňují zpracovat typy, které je třeba ošetřit.</span><span class="sxs-lookup"><span data-stu-id="d93fd-114">A good rule is to apply the maximum constraints possible that will still let you handle the types you must handle.</span></span> <span data-ttu-id="d93fd-115">Například pokud víte, že obecné třídy je určena pro použití pouze s typy odkazů, platí omezení třídy.</span><span class="sxs-lookup"><span data-stu-id="d93fd-115">For example, if you know that your generic class is intended for use only with reference types, apply the class constraint.</span></span> <span data-ttu-id="d93fd-116">Který bude zabránit neúmyslnému použití třídy s typy hodnot a vám umožní používat `as` operátoru u `T`a kontrola hodnot null.</span><span class="sxs-lookup"><span data-stu-id="d93fd-116">That will prevent unintended use of your class with value types, and will enable you to use the `as` operator on `T`, and check for null values.</span></span>  
  
- <span data-ttu-id="d93fd-117">Určuje, zda faktor obecné chování do základních tříd a podtříd.</span><span class="sxs-lookup"><span data-stu-id="d93fd-117">Whether to factor generic behavior into base classes and subclasses.</span></span>  
  
     <span data-ttu-id="d93fd-118">Protože obecné třídy může sloužit jako základní třídy, platí zde stejné aspekty návrhu stejně jako u neobecných třídách.</span><span class="sxs-lookup"><span data-stu-id="d93fd-118">Because generic classes can serve as base classes, the same design considerations apply here as with non-generic classes.</span></span> <span data-ttu-id="d93fd-119">Zobrazit pravidla o dědění z obecné základní třídy dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="d93fd-119">See the rules about inheriting from generic base classes later in this topic.</span></span>  
  
- <span data-ttu-id="d93fd-120">Určuje, zda implementovat jednu nebo více obecných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d93fd-120">Whether to implement one or more generic interfaces.</span></span>  
  
     <span data-ttu-id="d93fd-121">Například pokud navrhujete třídu, která se použije k vytvoření položek v kolekci na základě obecných typů, budete muset implementovat rozhraní jako <xref:System.IComparable%601> kde `T` je typ třídy.</span><span class="sxs-lookup"><span data-stu-id="d93fd-121">For example, if you are designing a class that will be used to create items in a generics-based collection, you may have to implement an interface such as <xref:System.IComparable%601> where `T` is the type of your class.</span></span>  
  
 <span data-ttu-id="d93fd-122">Příklad jednoduchou obecnou třídu, naleznete v tématu [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span><span class="sxs-lookup"><span data-stu-id="d93fd-122">For an example of a simple generic class, see [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span></span>  
  
 <span data-ttu-id="d93fd-123">Pravidla pro parametry typu a omezení mají několik důsledky pro obecnou třídu chování, zejména pokud jde o dědičnosti a člen usnadnění.</span><span class="sxs-lookup"><span data-stu-id="d93fd-123">The rules for type parameters and constraints have several implications for generic class behavior, especially regarding inheritance and member accessibility.</span></span> <span data-ttu-id="d93fd-124">Než budete pokračovat, měli byste pochopit některé podmínky.</span><span class="sxs-lookup"><span data-stu-id="d93fd-124">Before proceeding, you should understand some terms.</span></span> <span data-ttu-id="d93fd-125">Pro obecnou třídu `Node<T>,` klientský kód může odkazovat na třídu buď tak, že zadáte argument typu, chcete-li vytvořit uzavřený konstruovaný typ. (`Node<int>`).</span><span class="sxs-lookup"><span data-stu-id="d93fd-125">For a generic class `Node<T>,` client code can reference the class either by specifying a type argument, to create a closed constructed type (`Node<int>`).</span></span> <span data-ttu-id="d93fd-126">Případně ho můžete nechat parametr typu, který je tento parametr zadán, například když zadáte obecné základní třídy, chcete-li vytvořit otevřenou konstruovaný typ. (`Node<T>`).</span><span class="sxs-lookup"><span data-stu-id="d93fd-126">Alternatively, it can leave the type parameter unspecified, for example when you specify a generic base class, to create an open constructed type (`Node<T>`).</span></span> <span data-ttu-id="d93fd-127">Obecné třídy můžete dědit z konkrétní, uzavřený konstruovaný nebo otevřít konstruované základní třídy:</span><span class="sxs-lookup"><span data-stu-id="d93fd-127">Generic classes can inherit from concrete, closed constructed, or open constructed base classes:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#16)]  
  
 <span data-ttu-id="d93fd-128">Neobecné, jinými slovy, konkrétní, třídy mohou dědit z uzavřených konstruované základní třídy, ale není otevřené konstruovaný třídy nebo parametry typu, protože neexistuje žádný způsob v době běhu pro klientský kód zadáte argument typu vyžaduje vytvoření instance Základní třída.</span><span class="sxs-lookup"><span data-stu-id="d93fd-128">Non-generic, in other words, concrete, classes can inherit from closed constructed base classes, but not from open constructed classes or from type parameters because there is no way at run time for client code to supply the type argument required to instantiate the base class.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#17)]  
  
 <span data-ttu-id="d93fd-129">Obecné třídy, které dědí z otevřené sestavené typy musíte zadat argumenty typu pro všechny parametry typu základní třídy, které nejsou sdíleny dědičné třídě, jak je ukázáno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="d93fd-129">Generic classes that inherit from open constructed types must supply type arguments for any base class type parameters that are not shared by the inheriting class, as demonstrated in the following code:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#18)]  
  
 <span data-ttu-id="d93fd-130">Obecné třídy, které dědí z otevřené sestavené typy musíte zadat omezení, která je nadstavbou jazyka nebo implikovat, omezení u základního typu:</span><span class="sxs-lookup"><span data-stu-id="d93fd-130">Generic classes that inherit from open constructed types must specify constraints that are a superset of, or imply, the constraints on the base type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#19)]  
  
 <span data-ttu-id="d93fd-131">Obecné typy můžete použít více parametry typu a omezení, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="d93fd-131">Generic types can use multiple type parameters and constraints, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#20)]  
  
 <span data-ttu-id="d93fd-132">Otevřené sestavené typy vytvořený a uzavřených může sloužit jako parametry metody:</span><span class="sxs-lookup"><span data-stu-id="d93fd-132">Open constructed and closed constructed types can be used as method parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#21)]  
  
 <span data-ttu-id="d93fd-133">Pokud obecná třída implementuje rozhraní, všechny instance této třídy lze převést na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d93fd-133">If a generic class implements an interface, all instances of that class can be cast to that interface.</span></span>  
  
 <span data-ttu-id="d93fd-134">Obecné třídy se nebudou měnit.</span><span class="sxs-lookup"><span data-stu-id="d93fd-134">Generic classes are invariant.</span></span> <span data-ttu-id="d93fd-135">Jinými slovy Pokud určuje vstupní parametr `List<BaseClass>`, Chyba kompilace se zobrazí, když se pokusíte k poskytování `List<DerivedClass>`.</span><span class="sxs-lookup"><span data-stu-id="d93fd-135">In other words, if an input parameter specifies a `List<BaseClass>`, you will get a compile-time error if you try to provide a `List<DerivedClass>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d93fd-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d93fd-136">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="d93fd-137">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d93fd-137">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d93fd-138">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="d93fd-138">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="d93fd-139">Ukládání stavu čítače</span><span class="sxs-lookup"><span data-stu-id="d93fd-139">Saving the State of Enumerators</span></span>](https://blogs.msdn.microsoft.com/wesdyer/2006/01/13/saving-the-state-of-enumerators/)
- [<span data-ttu-id="d93fd-140">Díl stavebnice dědičnosti, část 1</span><span class="sxs-lookup"><span data-stu-id="d93fd-140">An Inheritance Puzzle, Part One</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/07/27/an-inheritance-puzzle-part-one/)
