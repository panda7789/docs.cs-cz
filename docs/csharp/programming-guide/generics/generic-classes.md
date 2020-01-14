---
title: Obecné třídy – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: 1fdfaa833ad32428d341b6f3a61cc7f638036183
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937510"
---
# <a name="generic-classes-c-programming-guide"></a><span data-ttu-id="e54f2-102">Obecné třídy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="e54f2-102">Generic Classes (C# Programming Guide)</span></span>
<span data-ttu-id="e54f2-103">Obecné třídy zapouzdřují operace, které nejsou specifické pro konkrétní datový typ.</span><span class="sxs-lookup"><span data-stu-id="e54f2-103">Generic classes encapsulate operations that are not specific to a particular data type.</span></span> <span data-ttu-id="e54f2-104">Nejběžnější použití pro obecné třídy je kolekce, jako jsou propojené seznamy, zatřiďovací tabulky, zásobníky, fronty, stromy a tak dále.</span><span class="sxs-lookup"><span data-stu-id="e54f2-104">The most common use for generic classes is with collections like linked lists, hash tables, stacks, queues, trees, and so on.</span></span> <span data-ttu-id="e54f2-105">Operace, jako je přidání a odebrání položek z kolekce, jsou prováděny v podstatě stejným způsobem bez ohledu na typ uložených dat.</span><span class="sxs-lookup"><span data-stu-id="e54f2-105">Operations such as adding and removing items from the collection are performed in basically the same way regardless of the type of data being stored.</span></span>  
  
 <span data-ttu-id="e54f2-106">Pro většinu scénářů, které vyžadují třídy kolekcí, je doporučeným přístupem použití těch, které jsou k dispozici v knihovně tříd .NET.</span><span class="sxs-lookup"><span data-stu-id="e54f2-106">For most scenarios that require collection classes, the recommended approach is to use the ones provided in the .NET class library.</span></span> <span data-ttu-id="e54f2-107">Další informace o použití těchto tříd naleznete v tématu [Obecné kolekce v rozhraní .NET](../../../standard/generics/collections.md).</span><span class="sxs-lookup"><span data-stu-id="e54f2-107">For more information about using these classes, see [Generic Collections in .NET](../../../standard/generics/collections.md).</span></span>  
  
 <span data-ttu-id="e54f2-108">Obvykle vytvoříte obecné třídy pomocí existující konkrétní třídy a změnou typů na parametry typu po jednom, dokud nedosáhnete optimálního vyvážení generalizace a použitelnosti.</span><span class="sxs-lookup"><span data-stu-id="e54f2-108">Typically, you create generic classes by starting with an existing concrete class, and changing types into type parameters one at a time until you reach the optimal balance of generalization and usability.</span></span> <span data-ttu-id="e54f2-109">Při vytváření vlastních obecných tříd jsou důležité důležité informace, které zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="e54f2-109">When creating your own generic classes, important considerations include the following:</span></span>  
  
- <span data-ttu-id="e54f2-110">Typy, které se mají zobecnit do parametrů typu</span><span class="sxs-lookup"><span data-stu-id="e54f2-110">Which types to generalize into type parameters.</span></span>  
  
     <span data-ttu-id="e54f2-111">Jako pravidlo, čím více typů můžete parametrizovat, tím flexibilnější a opakovaně použitelný kód se stane.</span><span class="sxs-lookup"><span data-stu-id="e54f2-111">As a rule, the more types you can parameterize, the more flexible and reusable your code becomes.</span></span> <span data-ttu-id="e54f2-112">Příliš mnoho generalizace však může vytvořit kód, který je obtížné pro ostatní vývojáře ke čtení nebo pochopení.</span><span class="sxs-lookup"><span data-stu-id="e54f2-112">However, too much generalization can create code that is difficult for other developers to read or understand.</span></span>  
  
- <span data-ttu-id="e54f2-113">Jaká omezení se mají použít pro parametry typu (viz [omezení u parametrů typu](./constraints-on-type-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="e54f2-113">What constraints, if any, to apply to the type parameters (See [Constraints on Type Parameters](./constraints-on-type-parameters.md)).</span></span>  
  
     <span data-ttu-id="e54f2-114">Dobrým pravidlem je použít maximální možné omezení, které vám pořád umožní zpracovat typy, které musíte zpracovat.</span><span class="sxs-lookup"><span data-stu-id="e54f2-114">A good rule is to apply the maximum constraints possible that will still let you handle the types you must handle.</span></span> <span data-ttu-id="e54f2-115">Například pokud víte, že vaše obecná třída je určena pouze pro použití s odkazovým typem, použijte omezení třídy.</span><span class="sxs-lookup"><span data-stu-id="e54f2-115">For example, if you know that your generic class is intended for use only with reference types, apply the class constraint.</span></span> <span data-ttu-id="e54f2-116">Tím zabráníte nezamýšlenému použití vaší třídy s typy hodnot a umožníte použít operátor `as` v `T`a vyhledat hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="e54f2-116">That will prevent unintended use of your class with value types, and will enable you to use the `as` operator on `T`, and check for null values.</span></span>  
  
- <span data-ttu-id="e54f2-117">Určuje, zda se má faktorovat obecné chování pro základní třídy a podtřídy.</span><span class="sxs-lookup"><span data-stu-id="e54f2-117">Whether to factor generic behavior into base classes and subclasses.</span></span>  
  
     <span data-ttu-id="e54f2-118">Vzhledem k tomu, že obecné třídy mohou sloužit jako základní třídy, platí stejné požadavky na návrh jako u neobecné třídy.</span><span class="sxs-lookup"><span data-stu-id="e54f2-118">Because generic classes can serve as base classes, the same design considerations apply here as with non-generic classes.</span></span> <span data-ttu-id="e54f2-119">Přečtěte si pravidla o dědění z obecných základních tříd dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="e54f2-119">See the rules about inheriting from generic base classes later in this topic.</span></span>  
  
- <span data-ttu-id="e54f2-120">Zda má být implementováno jedno nebo více obecných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e54f2-120">Whether to implement one or more generic interfaces.</span></span>  
  
     <span data-ttu-id="e54f2-121">Například pokud navrhujete třídu, která bude použita k vytváření položek v obecných typech kolekce, bude pravděpodobně nutné implementovat rozhraní, například <xref:System.IComparable%601>, kde `T` je typ vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="e54f2-121">For example, if you are designing a class that will be used to create items in a generics-based collection, you may have to implement an interface such as <xref:System.IComparable%601> where `T` is the type of your class.</span></span>  
  
 <span data-ttu-id="e54f2-122">Příklad jednoduché obecné třídy naleznete v tématu [Úvod do obecných typů](./index.md).</span><span class="sxs-lookup"><span data-stu-id="e54f2-122">For an example of a simple generic class, see [Introduction to Generics](./index.md).</span></span>  
  
 <span data-ttu-id="e54f2-123">Pravidla pro parametry typu a omezení mají několik důsledků pro chování obecné třídy, zejména týkající se dědičnosti a přístupnosti členů.</span><span class="sxs-lookup"><span data-stu-id="e54f2-123">The rules for type parameters and constraints have several implications for generic class behavior, especially regarding inheritance and member accessibility.</span></span> <span data-ttu-id="e54f2-124">Než budete pokračovat, měli byste pochopit určité výrazy.</span><span class="sxs-lookup"><span data-stu-id="e54f2-124">Before proceeding, you should understand some terms.</span></span> <span data-ttu-id="e54f2-125">Pro obecnou třídu `Node<T>,` klientský kód může odkazovat na třídu buď zadáním argumentu typu, pro vytvoření uzavřeného konstruovaného typu (`Node<int>`).</span><span class="sxs-lookup"><span data-stu-id="e54f2-125">For a generic class `Node<T>,` client code can reference the class either by specifying a type argument, to create a closed constructed type (`Node<int>`).</span></span> <span data-ttu-id="e54f2-126">Alternativně může ponechat parametr typu neurčeno, například při zadání obecné základní třídy pro vytvoření otevřeného konstruovaného typu (`Node<T>`).</span><span class="sxs-lookup"><span data-stu-id="e54f2-126">Alternatively, it can leave the type parameter unspecified, for example when you specify a generic base class, to create an open constructed type (`Node<T>`).</span></span> <span data-ttu-id="e54f2-127">Obecné třídy mohou dědit od konkrétních, uzavřených nebo otevřených základních tříd:</span><span class="sxs-lookup"><span data-stu-id="e54f2-127">Generic classes can inherit from concrete, closed constructed, or open constructed base classes:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#16)]  
  
 <span data-ttu-id="e54f2-128">Neobecná, jinak řečeno, konkrétní třídy mohou dědit z uzavřených konstruovaných tříd, ale nikoli z otevřených konstruovaných tříd nebo z parametrů typu, protože v době spuštění není žádný způsob, jak pro kód klienta zadat argument typu, který je vyžadován pro vytvoření instance základní třída.</span><span class="sxs-lookup"><span data-stu-id="e54f2-128">Non-generic, in other words, concrete, classes can inherit from closed constructed base classes, but not from open constructed classes or from type parameters because there is no way at run time for client code to supply the type argument required to instantiate the base class.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#17)]  
  
 <span data-ttu-id="e54f2-129">Obecné třídy, které dědí z otevřených konstruovaných typů musí zadat argumenty typu pro všechny parametry typu základní třídy, které nejsou sdíleny třídou dědění, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="e54f2-129">Generic classes that inherit from open constructed types must supply type arguments for any base class type parameters that are not shared by the inheriting class, as demonstrated in the following code:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#18)]  
  
 <span data-ttu-id="e54f2-130">Obecné třídy, které dědí z otevřených konstruovaných typů musí určovat omezení, která jsou nadmnožinou, nebo implikuje omezení základního typu:</span><span class="sxs-lookup"><span data-stu-id="e54f2-130">Generic classes that inherit from open constructed types must specify constraints that are a superset of, or imply, the constraints on the base type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#19)]  
  
 <span data-ttu-id="e54f2-131">Obecné typy mohou použít vícenásobné parametry typu a omezení, a to následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e54f2-131">Generic types can use multiple type parameters and constraints, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#20)]  
  
 <span data-ttu-id="e54f2-132">Otevřené a uzavřené konstruované typy lze použít jako parametry metody:</span><span class="sxs-lookup"><span data-stu-id="e54f2-132">Open constructed and closed constructed types can be used as method parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#21)]  
  
 <span data-ttu-id="e54f2-133">Pokud Obecná třída implementuje rozhraní, všechny instance této třídy lze přetypovat na toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e54f2-133">If a generic class implements an interface, all instances of that class can be cast to that interface.</span></span>  
  
 <span data-ttu-id="e54f2-134">Obecné třídy jsou invariantní.</span><span class="sxs-lookup"><span data-stu-id="e54f2-134">Generic classes are invariant.</span></span> <span data-ttu-id="e54f2-135">Jinými slovy, pokud vstupní parametr určuje `List<BaseClass>`, zobrazí se při pokusu o poskytnutí `List<DerivedClass>`Chyba při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="e54f2-135">In other words, if an input parameter specifies a `List<BaseClass>`, you will get a compile-time error if you try to provide a `List<DerivedClass>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e54f2-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e54f2-136">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="e54f2-137">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e54f2-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e54f2-138">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="e54f2-138">Generics</span></span>](./index.md)
- [<span data-ttu-id="e54f2-139">Uložení stavu enumerátorů</span><span class="sxs-lookup"><span data-stu-id="e54f2-139">Saving the State of Enumerators</span></span>](https://docs.microsoft.com/archive/blogs/wesdyer/saving-the-state-of-enumerators)
- [<span data-ttu-id="e54f2-140">Skládanka dědičnosti, první část</span><span class="sxs-lookup"><span data-stu-id="e54f2-140">An Inheritance Puzzle, Part One</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/an-inheritance-puzzle-part-one)
