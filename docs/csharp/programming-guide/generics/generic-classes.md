---
title: Obecné třídy – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: 1fdfaa833ad32428d341b6f3a61cc7f638036183
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937510"
---
# <a name="generic-classes-c-programming-guide"></a><span data-ttu-id="1f443-102">Obecné třídy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="1f443-102">Generic Classes (C# Programming Guide)</span></span>
<span data-ttu-id="1f443-103">Obecné třídy zapouzdřují operace, které nejsou specifické pro určitý datový typ.</span><span class="sxs-lookup"><span data-stu-id="1f443-103">Generic classes encapsulate operations that are not specific to a particular data type.</span></span> <span data-ttu-id="1f443-104">Nejběžnější použití pro obecné třídy je s kolekcemi, jako jsou propojené seznamy, tabulky hash, zásobníky, fronty, stromy a tak dále.</span><span class="sxs-lookup"><span data-stu-id="1f443-104">The most common use for generic classes is with collections like linked lists, hash tables, stacks, queues, trees, and so on.</span></span> <span data-ttu-id="1f443-105">Operace, jako je přidávání a odebírání položek z kolekce, jsou prováděny v podstatě stejným způsobem bez ohledu na typ uložených dat.</span><span class="sxs-lookup"><span data-stu-id="1f443-105">Operations such as adding and removing items from the collection are performed in basically the same way regardless of the type of data being stored.</span></span>  
  
 <span data-ttu-id="1f443-106">Pro většinu scénářů, které vyžadují třídy kolekce, je doporučeným přístupem použití ty, které jsou k dispozici v knihovně tříd .NET.</span><span class="sxs-lookup"><span data-stu-id="1f443-106">For most scenarios that require collection classes, the recommended approach is to use the ones provided in the .NET class library.</span></span> <span data-ttu-id="1f443-107">Další informace o použití těchto tříd naleznete [v tématu Obecné kolekce v rozhraní .NET](../../../standard/generics/collections.md).</span><span class="sxs-lookup"><span data-stu-id="1f443-107">For more information about using these classes, see [Generic Collections in .NET](../../../standard/generics/collections.md).</span></span>  
  
 <span data-ttu-id="1f443-108">Obvykle vytvoříte obecné třídy tak, že začnete s existující konkrétní třídou a přeřadíte typy na parametry typu jeden po druhém, dokud nedosáhnete optimální rovnováhy generalizace a použitelnosti.</span><span class="sxs-lookup"><span data-stu-id="1f443-108">Typically, you create generic classes by starting with an existing concrete class, and changing types into type parameters one at a time until you reach the optimal balance of generalization and usability.</span></span> <span data-ttu-id="1f443-109">Při vytváření vlastníobecné třídy, důležité důležité důležité informace patří následující:</span><span class="sxs-lookup"><span data-stu-id="1f443-109">When creating your own generic classes, important considerations include the following:</span></span>  
  
- <span data-ttu-id="1f443-110">Které typy chcete generalizovat do parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="1f443-110">Which types to generalize into type parameters.</span></span>  
  
     <span data-ttu-id="1f443-111">Zpravidla platí, že čím více typů můžete parametrizovat, tím flexibilnější a opakovaně použitelný kód se stane.</span><span class="sxs-lookup"><span data-stu-id="1f443-111">As a rule, the more types you can parameterize, the more flexible and reusable your code becomes.</span></span> <span data-ttu-id="1f443-112">Příliš mnoho generalizace však můžete vytvořit kód, který je obtížné pro ostatní vývojáře číst nebo pochopit.</span><span class="sxs-lookup"><span data-stu-id="1f443-112">However, too much generalization can create code that is difficult for other developers to read or understand.</span></span>  
  
- <span data-ttu-id="1f443-113">Jaká omezení, pokud existuje, použít na parametry typu (Viz [Omezení na parametry typu](./constraints-on-type-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="1f443-113">What constraints, if any, to apply to the type parameters (See [Constraints on Type Parameters](./constraints-on-type-parameters.md)).</span></span>  
  
     <span data-ttu-id="1f443-114">Dobrým pravidlem je použít maximální možná omezení, která vám stále umožní zpracovávat typy, které je nutné zpracovat.</span><span class="sxs-lookup"><span data-stu-id="1f443-114">A good rule is to apply the maximum constraints possible that will still let you handle the types you must handle.</span></span> <span data-ttu-id="1f443-115">Například pokud víte, že vaše obecná třída je určena pro použití pouze s typy odkazů, použijte omezení třídy.</span><span class="sxs-lookup"><span data-stu-id="1f443-115">For example, if you know that your generic class is intended for use only with reference types, apply the class constraint.</span></span> <span data-ttu-id="1f443-116">To zabrání nechtěnému použití vaší třídy s typy hodnot `as` a `T`umožní vám použít operátor na aplikaci a zkontrolovat hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="1f443-116">That will prevent unintended use of your class with value types, and will enable you to use the `as` operator on `T`, and check for null values.</span></span>  
  
- <span data-ttu-id="1f443-117">Určuje, zda má být obecné chování faktorováno do základních tříd a podtříd.</span><span class="sxs-lookup"><span data-stu-id="1f443-117">Whether to factor generic behavior into base classes and subclasses.</span></span>  
  
     <span data-ttu-id="1f443-118">Vzhledem k tomu, že obecné třídy mohou sloužit jako základní třídy, platí zde stejné aspekty návrhu jako u neobecných tříd.</span><span class="sxs-lookup"><span data-stu-id="1f443-118">Because generic classes can serve as base classes, the same design considerations apply here as with non-generic classes.</span></span> <span data-ttu-id="1f443-119">Viz pravidla o dědit z obecných základních tříd dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="1f443-119">See the rules about inheriting from generic base classes later in this topic.</span></span>  
  
- <span data-ttu-id="1f443-120">Určuje, zda má být implementováno jedno nebo více obecných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1f443-120">Whether to implement one or more generic interfaces.</span></span>  
  
     <span data-ttu-id="1f443-121">Například pokud navrhujete třídu, která bude použita k vytvoření položek v kolekci založené na <xref:System.IComparable%601> obecných, budete muset implementovat rozhraní, například kde `T` je typ vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="1f443-121">For example, if you are designing a class that will be used to create items in a generics-based collection, you may have to implement an interface such as <xref:System.IComparable%601> where `T` is the type of your class.</span></span>  
  
 <span data-ttu-id="1f443-122">Příklad jednoduché obecné třídy naleznete [v tématu Úvod do obecných typů](./index.md).</span><span class="sxs-lookup"><span data-stu-id="1f443-122">For an example of a simple generic class, see [Introduction to Generics](./index.md).</span></span>  
  
 <span data-ttu-id="1f443-123">Pravidla pro parametry typu a omezení mají několik důsledků pro chování obecné třídy, zejména pokud jde o dědičnost a usnadnění přístupu členů.</span><span class="sxs-lookup"><span data-stu-id="1f443-123">The rules for type parameters and constraints have several implications for generic class behavior, especially regarding inheritance and member accessibility.</span></span> <span data-ttu-id="1f443-124">Než budete pokračovat, měli byste pochopit některé pojmy.</span><span class="sxs-lookup"><span data-stu-id="1f443-124">Before proceeding, you should understand some terms.</span></span> <span data-ttu-id="1f443-125">Pro obecný `Node<T>,` kód klienta třídy můžete odkazovat na třídu buď zadáním`Node<int>`argumentu typu, chcete-li vytvořit uzavřený konstruovaný typ ( ).</span><span class="sxs-lookup"><span data-stu-id="1f443-125">For a generic class `Node<T>,` client code can reference the class either by specifying a type argument, to create a closed constructed type (`Node<int>`).</span></span> <span data-ttu-id="1f443-126">Alternativně může ponechat parametr typu nespecifikovaný, například když zadáte obecnou základní třídu, chcete-li vytvořit otevřený konstruovaný typ (`Node<T>`).</span><span class="sxs-lookup"><span data-stu-id="1f443-126">Alternatively, it can leave the type parameter unspecified, for example when you specify a generic base class, to create an open constructed type (`Node<T>`).</span></span> <span data-ttu-id="1f443-127">Obecné třídy mohou dědit z betonu, uzavřené konstrukce nebo otevřené konstruované základní třídy:</span><span class="sxs-lookup"><span data-stu-id="1f443-127">Generic classes can inherit from concrete, closed constructed, or open constructed base classes:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#16)]  
  
 <span data-ttu-id="1f443-128">Neobecné, jinými slovy, konkrétní, třídy mohou dědit z uzavřených konstruované základní třídy, ale ne z otevřené konstruované třídy nebo z parametrů typu, protože neexistuje žádný způsob, jak za běhu pro kód klienta zadat argument typu potřebné k vytvoření instance základní třídy.</span><span class="sxs-lookup"><span data-stu-id="1f443-128">Non-generic, in other words, concrete, classes can inherit from closed constructed base classes, but not from open constructed classes or from type parameters because there is no way at run time for client code to supply the type argument required to instantiate the base class.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#17)]  
  
 <span data-ttu-id="1f443-129">Obecné třídy, které dědí z otevřených konstruovaných typů, musí poskytovat argumenty typu pro všechny parametry typu základní třídy, které nejsou sdíleny děvčivou třídou, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="1f443-129">Generic classes that inherit from open constructed types must supply type arguments for any base class type parameters that are not shared by the inheriting class, as demonstrated in the following code:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#18)]  
  
 <span data-ttu-id="1f443-130">Obecné třídy, které dědí z otevřených konstruovaných typů, musí určit omezení, která jsou nadmnožinou nebo implikují omezení základního typu:</span><span class="sxs-lookup"><span data-stu-id="1f443-130">Generic classes that inherit from open constructed types must specify constraints that are a superset of, or imply, the constraints on the base type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#19)]  
  
 <span data-ttu-id="1f443-131">Obecné typy mohou používat více parametrů typu a omezení, a to následovně:</span><span class="sxs-lookup"><span data-stu-id="1f443-131">Generic types can use multiple type parameters and constraints, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#20)]  
  
 <span data-ttu-id="1f443-132">Jako parametry metody lze použít otevřené konstruované a uzavřené konstruované typy:</span><span class="sxs-lookup"><span data-stu-id="1f443-132">Open constructed and closed constructed types can be used as method parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#21)]  
  
 <span data-ttu-id="1f443-133">Pokud obecná třída implementuje rozhraní, všechny instance této třídy lze přetypovat do tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1f443-133">If a generic class implements an interface, all instances of that class can be cast to that interface.</span></span>  
  
 <span data-ttu-id="1f443-134">Obecné třídy jsou invariantní.</span><span class="sxs-lookup"><span data-stu-id="1f443-134">Generic classes are invariant.</span></span> <span data-ttu-id="1f443-135">Jinými slovy, pokud vstupní parametr `List<BaseClass>`určuje , zobrazí se chyba v době `List<DerivedClass>`kompilace, pokud se pokusíte poskytnout .</span><span class="sxs-lookup"><span data-stu-id="1f443-135">In other words, if an input parameter specifies a `List<BaseClass>`, you will get a compile-time error if you try to provide a `List<DerivedClass>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f443-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f443-136">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="1f443-137">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1f443-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1f443-138">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="1f443-138">Generics</span></span>](./index.md)
- [<span data-ttu-id="1f443-139">Uložení stavu výčtů</span><span class="sxs-lookup"><span data-stu-id="1f443-139">Saving the State of Enumerators</span></span>](https://docs.microsoft.com/archive/blogs/wesdyer/saving-the-state-of-enumerators)
- [<span data-ttu-id="1f443-140">Dědictví Puzzle, část první</span><span class="sxs-lookup"><span data-stu-id="1f443-140">An Inheritance Puzzle, Part One</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/an-inheritance-puzzle-part-one)
