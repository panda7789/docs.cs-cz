---
title: Konstruktory instancí – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: c7bb9d43991ca45e878dd8ac2a17f3996cb8f436
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596456"
---
# <a name="instance-constructors-c-programming-guide"></a><span data-ttu-id="ff8bd-102">Konstruktory instancí (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="ff8bd-102">Instance Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="ff8bd-103">Konstruktory instancí slouží k vytvoření a inicializaci všech proměnných členů instance při použití [nového](../../language-reference/operators/new-operator.md) výrazu pro vytvoření objektu [třídy](../../language-reference/keywords/class.md).</span><span class="sxs-lookup"><span data-stu-id="ff8bd-103">Instance constructors are used to create and initialize any instance member variables when you use the [new](../../language-reference/operators/new-operator.md) expression to create an object of a [class](../../language-reference/keywords/class.md).</span></span> <span data-ttu-id="ff8bd-104">Chcete-li inicializovat [statickou](../../language-reference/keywords/static.md) třídu nebo statické proměnné v nestatické třídě, Definujte statický konstruktor.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-104">To initialize a [static](../../language-reference/keywords/static.md) class, or static variables in a non-static class, you define a static constructor.</span></span> <span data-ttu-id="ff8bd-105">Další informace naleznete v tématu [statické konstruktory](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="ff8bd-105">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
 <span data-ttu-id="ff8bd-106">Následující příklad ukazuje konstruktor instance:</span><span class="sxs-lookup"><span data-stu-id="ff8bd-106">The following example shows an instance constructor:</span></span>  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
>  <span data-ttu-id="ff8bd-107">Pro přehlednost Tato třída obsahuje veřejná pole.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-107">For clarity, this class contains public fields.</span></span> <span data-ttu-id="ff8bd-108">Použití veřejných polí není doporučeným způsobem programování, protože umožňuje libovolné metodě kdekoli v programu neomezený a neověřený přístup k vnitřním pracovním postupům objektu.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-108">The use of public fields is not a recommended programming practice because it allows any method anywhere in a program unrestricted and unverified access to an object's inner workings.</span></span> <span data-ttu-id="ff8bd-109">Datové členy by měly být obecně soukromé a měly by být k dispozici pouze prostřednictvím metod a vlastností třídy.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-109">Data members should generally be private, and should be accessed only through class methods and properties.</span></span>  
  
 <span data-ttu-id="ff8bd-110">Tento konstruktor instance se volá vždycky, když se vytvoří objekt `Coords` založený na třídě.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-110">This instance constructor is called whenever an object based on the `Coords` class is created.</span></span> <span data-ttu-id="ff8bd-111">Konstruktor podobný tomuto typu, který nepřijímá žádné argumenty, se nazývá *konstruktor bez parametrů*.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-111">A constructor like this one, which takes no arguments, is called a *parameterless constructor*.</span></span> <span data-ttu-id="ff8bd-112">Je však často užitečné poskytnout další konstruktory.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-112">However, it is often useful to provide additional constructors.</span></span> <span data-ttu-id="ff8bd-113">Například můžeme přidat konstruktor do `Coords` třídy, která nám umožní zadat počáteční hodnoty pro datové členy:</span><span class="sxs-lookup"><span data-stu-id="ff8bd-113">For example, we can add a constructor to the `Coords` class that allows us to specify the initial values for the data members:</span></span>  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 <span data-ttu-id="ff8bd-114">To umožňuje `Coords` vytvářet objekty s výchozími nebo konkrétními počátečními hodnotami, jako jsou:</span><span class="sxs-lookup"><span data-stu-id="ff8bd-114">This allows `Coords` objects to be created with default or specific initial values, like this:</span></span>  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 <span data-ttu-id="ff8bd-115">Pokud třída nemá konstruktor, konstruktor bez parametrů se automaticky vygeneruje a k inicializaci polí objektu se použijí výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-115">If a class does not have a constructor, a parameterless constructor is automatically generated and default values are used to initialize the object fields.</span></span> <span data-ttu-id="ff8bd-116">Například hodnota [int](../../language-reference/builtin-types/integral-numeric-types.md) je inicializována na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-116">For example, an [int](../../language-reference/builtin-types/integral-numeric-types.md) is initialized to 0.</span></span> <span data-ttu-id="ff8bd-117">Další informace o výchozích hodnotách najdete v tématu [Tabulka výchozích hodnot](../../language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="ff8bd-117">For more information on default values, see [Default Values Table](../../language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="ff8bd-118">Proto vzhledem k tomu `Coords` , že konstruktor bez parametrů třídy inicializuje všechny datové členy na nulu, lze jej odebrat zcela, aniž by bylo nutné měnit způsob fungování třídy.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-118">Therefore, because the `Coords` class parameterless constructor initializes all data members to zero, it can be removed altogether without changing how the class works.</span></span> <span data-ttu-id="ff8bd-119">Kompletní příklad použití více konstruktorů je uveden v příkladu 1 dále v tomto tématu a příklad automaticky generovaného konstruktoru je uveden v příkladu 2.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-119">A complete example using multiple constructors is provided in Example 1 later in this topic, and an example of an automatically generated constructor is provided in Example 2.</span></span>  
  
 <span data-ttu-id="ff8bd-120">Konstruktory instancí lze také použít k volání konstruktorů instancí základních tříd.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-120">Instance constructors can also be used to call the instance constructors of base classes.</span></span> <span data-ttu-id="ff8bd-121">Konstruktor třídy může vyvolat konstruktor základní třídy prostřednictvím inicializátoru následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ff8bd-121">The class constructor can invoke the constructor of the base class through the initializer, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 <span data-ttu-id="ff8bd-122">V tomto příkladu `Circle` Třída předává hodnoty reprezentující poloměr a výšku do konstruktoru `Shape` poskytnutého z, který `Circle` je odvozen.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-122">In this example, the `Circle` class passes values representing radius and height to the constructor provided by `Shape` from which `Circle` is derived.</span></span> <span data-ttu-id="ff8bd-123">Úplný příklad s `Shape` využitím `Circle` a se zobrazí v tomto tématu jako příklad 3.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-123">A complete example using `Shape` and `Circle` appears in this topic as Example 3.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="ff8bd-124">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="ff8bd-124">Example 1</span></span>  
 <span data-ttu-id="ff8bd-125">Následující příklad ukazuje třídu se dvěma konstruktory třídy, jedna bez argumentů a jedna se dvěma argumenty.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-125">The following example demonstrates a class with two class constructors, one without arguments and one with two arguments.</span></span>  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a><span data-ttu-id="ff8bd-126">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="ff8bd-126">Example 2</span></span>  
 <span data-ttu-id="ff8bd-127">V tomto příkladu třída `Person` nemá žádné konstruktory. v takovém případě je konstruktor bez parametrů k dispozici automaticky a pole jsou inicializována na výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-127">In this example, the class `Person` does not have any constructors, in which case, a parameterless constructor is automatically provided and the fields are initialized to their default values.</span></span>  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 <span data-ttu-id="ff8bd-128">Všimněte si, že výchozí hodnota `age` je `0` `name` a výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-128">Notice that the default value of `age` is `0` and the default value of `name` is `null`.</span></span> <span data-ttu-id="ff8bd-129">Další informace o výchozích hodnotách najdete v tématu [Tabulka výchozích hodnot](../../language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="ff8bd-129">For more information on default values, see [Default Values Table](../../language-reference/keywords/default-values-table.md).</span></span>  
  
## <a name="example-3"></a><span data-ttu-id="ff8bd-130">Příklad 3</span><span class="sxs-lookup"><span data-stu-id="ff8bd-130">Example 3</span></span>  
 <span data-ttu-id="ff8bd-131">Následující příklad ukazuje použití inicializátoru základní třídy.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-131">The following example demonstrates using the base class initializer.</span></span> <span data-ttu-id="ff8bd-132">Třída je odvozena z obecné třídy `Shape`a `Cylinder` třída je odvozena z `Circle` třídy. `Circle`</span><span class="sxs-lookup"><span data-stu-id="ff8bd-132">The `Circle` class is derived from the general class `Shape`, and the `Cylinder` class is derived from the `Circle` class.</span></span> <span data-ttu-id="ff8bd-133">Konstruktor u každé odvozené třídy používá svůj inicializátor základní třídy.</span><span class="sxs-lookup"><span data-stu-id="ff8bd-133">The constructor on each derived class is using its base class initializer.</span></span>  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 <span data-ttu-id="ff8bd-134">Další příklady vyvolání konstruktorů základní třídy naleznete v tématu [Virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md)a [Base](../../language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="ff8bd-134">For more examples on invoking the base class constructors, see [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md), and [base](../../language-reference/keywords/base.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff8bd-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff8bd-135">See also</span></span>

- [<span data-ttu-id="ff8bd-136">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ff8bd-136">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ff8bd-137">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="ff8bd-137">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="ff8bd-138">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="ff8bd-138">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="ff8bd-139">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="ff8bd-139">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="ff8bd-140">static</span><span class="sxs-lookup"><span data-stu-id="ff8bd-140">static</span></span>](../../language-reference/keywords/static.md)
