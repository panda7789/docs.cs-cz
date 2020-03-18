---
title: Konstruktory instancí – programovací příručka Jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: 621b8ca7510b0b9916c9c46f201ff77402c3c655
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75964740"
---
# <a name="instance-constructors-c-programming-guide"></a><span data-ttu-id="b445f-102">Konstruktory instancí (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="b445f-102">Instance Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="b445f-103">Instance konstruktory se používají k vytvoření a inicializaci všech proměnných členů instance při použití [nového](../../language-reference/operators/new-operator.md) výrazu k vytvoření objektu [třídy](../../language-reference/keywords/class.md).</span><span class="sxs-lookup"><span data-stu-id="b445f-103">Instance constructors are used to create and initialize any instance member variables when you use the [new](../../language-reference/operators/new-operator.md) expression to create an object of a [class](../../language-reference/keywords/class.md).</span></span> <span data-ttu-id="b445f-104">Chcete-li inicializovat [statickou](../../language-reference/keywords/static.md) třídu nebo statické proměnné v nestatické třídě, definujte statický konstruktor.</span><span class="sxs-lookup"><span data-stu-id="b445f-104">To initialize a [static](../../language-reference/keywords/static.md) class, or static variables in a non-static class, you define a static constructor.</span></span> <span data-ttu-id="b445f-105">Další informace naleznete [v tématu Statické konstruktory](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="b445f-105">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
 <span data-ttu-id="b445f-106">Následující příklad ukazuje konstruktor instance:</span><span class="sxs-lookup"><span data-stu-id="b445f-106">The following example shows an instance constructor:</span></span>  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
> <span data-ttu-id="b445f-107">Pro přehlednost tato třída obsahuje veřejná pole.</span><span class="sxs-lookup"><span data-stu-id="b445f-107">For clarity, this class contains public fields.</span></span> <span data-ttu-id="b445f-108">Použití veřejných polí není doporučenou programovací praxí, protože umožňuje libovolnou metodu kdekoli v programu neomezený a neověřený přístup k vnitřnímu fungování objektu.</span><span class="sxs-lookup"><span data-stu-id="b445f-108">The use of public fields is not a recommended programming practice because it allows any method anywhere in a program unrestricted and unverified access to an object's inner workings.</span></span> <span data-ttu-id="b445f-109">Datové členy by obecně měly být soukromé a měly by být přístupné pouze prostřednictvím metod a vlastností třídy.</span><span class="sxs-lookup"><span data-stu-id="b445f-109">Data members should generally be private, and should be accessed only through class methods and properties.</span></span>  
  
 <span data-ttu-id="b445f-110">Tento konstruktor instance je volána `Coords` vždy, když je vytvořen objekt založený na třídě.</span><span class="sxs-lookup"><span data-stu-id="b445f-110">This instance constructor is called whenever an object based on the `Coords` class is created.</span></span> <span data-ttu-id="b445f-111">Konstruktor, jako je tento, který nepřijímá žádné argumenty, se nazývá *konstruktor bez parametrů*.</span><span class="sxs-lookup"><span data-stu-id="b445f-111">A constructor like this one, which takes no arguments, is called a *parameterless constructor*.</span></span> <span data-ttu-id="b445f-112">Je však často užitečné poskytnout další konstruktory.</span><span class="sxs-lookup"><span data-stu-id="b445f-112">However, it is often useful to provide additional constructors.</span></span> <span data-ttu-id="b445f-113">Například můžeme přidat konstruktor do `Coords` třídy, která nám umožňuje zadat počáteční hodnoty pro datové členy:</span><span class="sxs-lookup"><span data-stu-id="b445f-113">For example, we can add a constructor to the `Coords` class that allows us to specify the initial values for the data members:</span></span>  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 <span data-ttu-id="b445f-114">To `Coords` umožňuje objekty, které mají být vytvořeny s výchozí nebo konkrétní počáteční hodnoty, například toto:</span><span class="sxs-lookup"><span data-stu-id="b445f-114">This allows `Coords` objects to be created with default or specific initial values, like this:</span></span>  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 <span data-ttu-id="b445f-115">Pokud třída nemá konstruktor, konstruktor bez parametrů je automaticky generován a výchozí hodnoty se používají k inicializaci polí objektu.</span><span class="sxs-lookup"><span data-stu-id="b445f-115">If a class does not have a constructor, a parameterless constructor is automatically generated and default values are used to initialize the object fields.</span></span> <span data-ttu-id="b445f-116">Například [int](../../language-reference/builtin-types/integral-numeric-types.md) je inicializován na 0.</span><span class="sxs-lookup"><span data-stu-id="b445f-116">For example, an [int](../../language-reference/builtin-types/integral-numeric-types.md) is initialized to 0.</span></span> <span data-ttu-id="b445f-117">Informace o výchozích hodnotách typu naleznete [v tématu Výchozí hodnoty typů jazyka C#](../../language-reference/builtin-types/default-values.md).</span><span class="sxs-lookup"><span data-stu-id="b445f-117">For information about the type default values, see [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="b445f-118">Proto protože `Coords` konstruktor bez parametrů třídy inicializuje všechny datové členy na nulu, lze jej odebrat zcela bezzměny způsobu fungování třídy.</span><span class="sxs-lookup"><span data-stu-id="b445f-118">Therefore, because the `Coords` class parameterless constructor initializes all data members to zero, it can be removed altogether without changing how the class works.</span></span> <span data-ttu-id="b445f-119">Úplný příklad pomocí více konstruktorů je k dispozici v příkladu 1 dále v tomto tématu a příklad automaticky generovanékonstruktor je k dispozici v příkladu 2.</span><span class="sxs-lookup"><span data-stu-id="b445f-119">A complete example using multiple constructors is provided in Example 1 later in this topic, and an example of an automatically generated constructor is provided in Example 2.</span></span>  
  
 <span data-ttu-id="b445f-120">Instance konstruktory lze také volat instance konstruktory základních tříd.</span><span class="sxs-lookup"><span data-stu-id="b445f-120">Instance constructors can also be used to call the instance constructors of base classes.</span></span> <span data-ttu-id="b445f-121">Konstruktor třídy můžete vyvolat konstruktor základní třídy prostřednictvím inicializátoru, takto:</span><span class="sxs-lookup"><span data-stu-id="b445f-121">The class constructor can invoke the constructor of the base class through the initializer, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 <span data-ttu-id="b445f-122">V tomto příkladu `Circle` třída předá hodnoty představující poloměr a `Shape` výšku `Circle` konstruktoru, ze kterého je odvozen.</span><span class="sxs-lookup"><span data-stu-id="b445f-122">In this example, the `Circle` class passes values representing radius and height to the constructor provided by `Shape` from which `Circle` is derived.</span></span> <span data-ttu-id="b445f-123">Úplný příklad `Shape` pomocí `Circle` a zobrazí se v tomto tématu jako příklad 3.</span><span class="sxs-lookup"><span data-stu-id="b445f-123">A complete example using `Shape` and `Circle` appears in this topic as Example 3.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="b445f-124">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="b445f-124">Example 1</span></span>  
 <span data-ttu-id="b445f-125">Následující příklad ukazuje třídu se dvěma konstruktory třídy, jeden bez argumentů a jeden se dvěma argumenty.</span><span class="sxs-lookup"><span data-stu-id="b445f-125">The following example demonstrates a class with two class constructors, one without arguments and one with two arguments.</span></span>  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a><span data-ttu-id="b445f-126">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="b445f-126">Example 2</span></span>  
 <span data-ttu-id="b445f-127">V tomto příkladu `Person` třída nemá žádné konstruktory, v takovém případě konstruktor bez parametrů je automaticky k dispozici a pole jsou inicializovány na jejich výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b445f-127">In this example, the class `Person` does not have any constructors, in which case, a parameterless constructor is automatically provided and the fields are initialized to their default values.</span></span>  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 <span data-ttu-id="b445f-128">Všimněte si, `age` že `0` výchozí hodnota `name` je `null`a výchozí hodnota je .</span><span class="sxs-lookup"><span data-stu-id="b445f-128">Notice that the default value of `age` is `0` and the default value of `name` is `null`.</span></span>
  
## <a name="example-3"></a><span data-ttu-id="b445f-129">Příklad 3</span><span class="sxs-lookup"><span data-stu-id="b445f-129">Example 3</span></span>  
 <span data-ttu-id="b445f-130">Následující příklad ukazuje pomocí inicializátoru základní třídy.</span><span class="sxs-lookup"><span data-stu-id="b445f-130">The following example demonstrates using the base class initializer.</span></span> <span data-ttu-id="b445f-131">Třída `Circle` je odvozena z `Shape`obecné třídy a `Cylinder` třída `Circle` je odvozena z třídy.</span><span class="sxs-lookup"><span data-stu-id="b445f-131">The `Circle` class is derived from the general class `Shape`, and the `Cylinder` class is derived from the `Circle` class.</span></span> <span data-ttu-id="b445f-132">Konstruktor na každé odvozené třídy používá jeho základní třídy inicializátoru.</span><span class="sxs-lookup"><span data-stu-id="b445f-132">The constructor on each derived class is using its base class initializer.</span></span>  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 <span data-ttu-id="b445f-133">Další příklady při vyvolání konstruktorů základní třídy naleznete v [tématu virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md)a [base](../../language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="b445f-133">For more examples on invoking the base class constructors, see [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md), and [base](../../language-reference/keywords/base.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b445f-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="b445f-134">See also</span></span>

- [<span data-ttu-id="b445f-135">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b445f-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b445f-136">Třídy a struky</span><span class="sxs-lookup"><span data-stu-id="b445f-136">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="b445f-137">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="b445f-137">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="b445f-138">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="b445f-138">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="b445f-139">Statické</span><span class="sxs-lookup"><span data-stu-id="b445f-139">static</span></span>](../../language-reference/keywords/static.md)
