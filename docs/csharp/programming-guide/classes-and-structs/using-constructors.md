---
title: Použití konstruktorů – programovací příručka Jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 7c227b61c6d5b4ead00fced0dba046b90683fde1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626409"
---
# <a name="using-constructors-c-programming-guide"></a><span data-ttu-id="899aa-102">Použití konstruktorů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="899aa-102">Using Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="899aa-103">Při vytvoření [třídy](../../language-reference/keywords/class.md) nebo [struktury](../../language-reference/builtin-types/struct.md) je volána její konstruktor.</span><span class="sxs-lookup"><span data-stu-id="899aa-103">When a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="899aa-104">Konstruktory mají stejný název jako třída nebo struktura a obvykle inicializují datové členy nového objektu.</span><span class="sxs-lookup"><span data-stu-id="899aa-104">Constructors have the same name as the class or struct, and they usually initialize the data members of the new object.</span></span>  
  
 <span data-ttu-id="899aa-105">V následujícím příkladu je `Taxi` třída s názvem definována pomocí jednoduchého konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="899aa-105">In the following example, a class named `Taxi` is defined by using a simple constructor.</span></span> <span data-ttu-id="899aa-106">Tato třída je pak vytvořena s [novým](../../language-reference/operators/new-operator.md) operátorem.</span><span class="sxs-lookup"><span data-stu-id="899aa-106">This class is then instantiated with the [new](../../language-reference/operators/new-operator.md) operator.</span></span> <span data-ttu-id="899aa-107">Konstruktor `Taxi` je vyvolán operátorem `new` ihned po přidělení paměti pro nový objekt.</span><span class="sxs-lookup"><span data-stu-id="899aa-107">The `Taxi` constructor is invoked by the `new` operator immediately after memory is allocated for the new object.</span></span>  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 <span data-ttu-id="899aa-108">Konstruktor, který nepřijímá žádné parametry, se nazývá *konstruktor bez parametrů*.</span><span class="sxs-lookup"><span data-stu-id="899aa-108">A constructor that takes no parameters is called a *parameterless constructor*.</span></span> <span data-ttu-id="899aa-109">Konstruktory bez parametrů jsou vyvolány vždy, když je `new` objekt vytvořen pomocí operátoru `new`a žádné argumenty jsou k dispozici .</span><span class="sxs-lookup"><span data-stu-id="899aa-109">Parameterless constructors are invoked whenever an object is instantiated by using the `new` operator and no arguments are provided to `new`.</span></span> <span data-ttu-id="899aa-110">Další informace naleznete v tématu [Instance Constructors](./instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="899aa-110">For more information, see [Instance Constructors](./instance-constructors.md).</span></span>  
  
 <span data-ttu-id="899aa-111">Pokud třída není [statická](../../language-reference/keywords/static.md), třídy bez konstruktorů jsou uvedeny veřejné konstruktor bez parametrů kompilátorem C# za účelem povolení instance třídy.</span><span class="sxs-lookup"><span data-stu-id="899aa-111">Unless the class is [static](../../language-reference/keywords/static.md), classes without constructors are given a public parameterless constructor by the C# compiler in order to enable class instantiation.</span></span> <span data-ttu-id="899aa-112">Další informace naleznete [v tématu Statické třídy a statické členy třídy](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="899aa-112">For more information, see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="899aa-113">Můžete zabránit vytvoření instance třídy tím, že konstruktor uvažuje takto:</span><span class="sxs-lookup"><span data-stu-id="899aa-113">You can prevent a class from being instantiated by making the constructor private, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="899aa-114">Další informace naleznete [v tématu Private Constructors](./private-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="899aa-114">For more information, see [Private Constructors](./private-constructors.md).</span></span>  
  
 <span data-ttu-id="899aa-115">Konstruktory pro [typy struktury](../../language-reference/builtin-types/struct.md) se podobají konstruktorům třídy, ale `structs` nemohou obsahovat explicitní konstruktor bez parametrů, protože je automaticky poskytován kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="899aa-115">Constructors for [struct](../../language-reference/builtin-types/struct.md) types resemble class constructors, but `structs` cannot contain an explicit parameterless constructor because one is provided automatically by the compiler.</span></span> <span data-ttu-id="899aa-116">Tento konstruktor inicializuje každé `struct` pole v [na výchozí hodnotu](../../language-reference/builtin-types/default-values.md).</span><span class="sxs-lookup"><span data-stu-id="899aa-116">This constructor initializes each field in the `struct` to the [default value](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="899aa-117">Tento konstruktor bez parametrů je však `struct` vyvolána pouze `new`v případě, že je vytvořena instance s .</span><span class="sxs-lookup"><span data-stu-id="899aa-117">However, this parameterless constructor is only invoked if the `struct` is instantiated with `new`.</span></span> <span data-ttu-id="899aa-118">Například tento kód používá konstruktor <xref:System.Int32>bez parametrů pro , takže máte jistotu, že celé číslo je inicializováno:</span><span class="sxs-lookup"><span data-stu-id="899aa-118">For example, this code uses the parameterless constructor for <xref:System.Int32>, so that you are assured that the integer is initialized:</span></span>  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="899aa-119">Následující kód však způsobí chybu kompilátoru, `new`protože nepoužívá , a protože se pokusí použít objekt, který nebyl inicializován:</span><span class="sxs-lookup"><span data-stu-id="899aa-119">The following code, however, causes a compiler error because it does not use `new`, and because it tries to use an object that has not been initialized:</span></span>  
  
```csharp  
int i;  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="899aa-120">Alternativně objekty `structs` založené na (včetně všech vestavěných číselných typů) mohou být inicializovány nebo přiřazeny a poté použity jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="899aa-120">Alternatively, objects based on `structs` (including all built-in numeric types) can be initialized or assigned and then used as in the following example:</span></span>  
  
```csharp  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 <span data-ttu-id="899aa-121">Takže volání konstruktoru bez parametrů pro typ hodnoty není vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="899aa-121">So calling the parameterless constructor for a value type is not required.</span></span>  
  
 <span data-ttu-id="899aa-122">Obě třídy a `structs` můžete definovat konstruktory, které berou parametry.</span><span class="sxs-lookup"><span data-stu-id="899aa-122">Both classes and `structs` can define constructors that take parameters.</span></span> <span data-ttu-id="899aa-123">Konstruktory, které berou parametry, `new` musí být volány prostřednictvím příkazu nebo [základního](../../language-reference/keywords/base.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="899aa-123">Constructors that take parameters must be called through a `new` statement or a [base](../../language-reference/keywords/base.md) statement.</span></span> <span data-ttu-id="899aa-124">Třídy `structs` a můžete také definovat více konstruktorů a ani je nutné definovat konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="899aa-124">Classes and `structs` can also define multiple constructors, and neither is required to define a parameterless constructor.</span></span> <span data-ttu-id="899aa-125">Například:</span><span class="sxs-lookup"><span data-stu-id="899aa-125">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 <span data-ttu-id="899aa-126">Tuto třídu lze vytvořit pomocí některého z následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="899aa-126">This class can be created by using either of the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 <span data-ttu-id="899aa-127">Konstruktor můžete použít `base` klíčové slovo volat konstruktor základní třídy.</span><span class="sxs-lookup"><span data-stu-id="899aa-127">A constructor can use the `base` keyword to call the constructor of a base class.</span></span> <span data-ttu-id="899aa-128">Například:</span><span class="sxs-lookup"><span data-stu-id="899aa-128">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 <span data-ttu-id="899aa-129">V tomto příkladu je konstruktor pro základní třídu volán před spuštěním bloku pro konstruktor.</span><span class="sxs-lookup"><span data-stu-id="899aa-129">In this example, the constructor for the base class is called before the block for the constructor is executed.</span></span> <span data-ttu-id="899aa-130">Klíčové `base` slovo lze použít s parametry nebo bez něj.</span><span class="sxs-lookup"><span data-stu-id="899aa-130">The `base` keyword can be used with or without parameters.</span></span> <span data-ttu-id="899aa-131">Všechny parametry konstruktoru lze použít jako `base`parametry pro nebo jako součást výrazu.</span><span class="sxs-lookup"><span data-stu-id="899aa-131">Any parameters to the constructor can be used as parameters to `base`, or as part of an expression.</span></span> <span data-ttu-id="899aa-132">Další informace naleznete v [tématu base](../../language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="899aa-132">For more information, see [base](../../language-reference/keywords/base.md).</span></span>  
  
 <span data-ttu-id="899aa-133">V odvozené třídě, pokud konstruktor základní třídy není `base` explicitně volána pomocí klíčového slova, konstruktor bez parametrů, pokud existuje, je volán implicitně.</span><span class="sxs-lookup"><span data-stu-id="899aa-133">In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the parameterless constructor, if there is one, is called implicitly.</span></span> <span data-ttu-id="899aa-134">To znamená, že následující deklarace konstruktoru jsou účinně stejné:</span><span class="sxs-lookup"><span data-stu-id="899aa-134">This means that the following constructor declarations are effectively the same:</span></span>  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 <span data-ttu-id="899aa-135">Pokud základní třída nenabízí konstruktor bez parametrů, odvozené třídy musí explicitní volání `base`základní konstruktor pomocí .</span><span class="sxs-lookup"><span data-stu-id="899aa-135">If a base class does not offer a parameterless constructor, the derived class must make an explicit call to a base constructor by using `base`.</span></span>  
  
 <span data-ttu-id="899aa-136">Konstruktor může vyvolat jiný konstruktor ve stejném objektu pomocí klíčového slova [This.](../../language-reference/keywords/this.md)</span><span class="sxs-lookup"><span data-stu-id="899aa-136">A constructor can invoke another constructor in the same object by using the [this](../../language-reference/keywords/this.md) keyword.</span></span> <span data-ttu-id="899aa-137">Stejně jako `base`, `this` lze použít s nebo bez parametrů a všechny parametry `this`v konstruktoru jsou k dispozici jako parametry pro , nebo jako součást výrazu.</span><span class="sxs-lookup"><span data-stu-id="899aa-137">Like `base`, `this` can be used with or without parameters, and any parameters in the constructor are available as parameters to `this`, or as part of an expression.</span></span> <span data-ttu-id="899aa-138">Například druhý konstruktor v předchozím příkladu lze `this`přepsat pomocí :</span><span class="sxs-lookup"><span data-stu-id="899aa-138">For example, the second constructor in the previous example can be rewritten using `this`:</span></span>  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 <span data-ttu-id="899aa-139">Použití klíčového `this` slova v předchozím příkladu způsobí, že tento konstruktor se nazývá:</span><span class="sxs-lookup"><span data-stu-id="899aa-139">The use of the `this` keyword in the previous example causes this constructor to be called:</span></span>  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 <span data-ttu-id="899aa-140">Konstruktory mohou být označeny jako [veřejné](../../language-reference/keywords/public.md), [soukromé](../../language-reference/keywords/private.md), [chráněné](../../language-reference/keywords/protected.md), [interní](../../language-reference/keywords/internal.md), [chráněné vnitřní](../../language-reference/keywords/protected-internal.md) nebo soukromé [chráněné](../../language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="899aa-140">Constructors can be marked as [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="899aa-141">Tyto modifikátory přístupu definují, jak mohou uživatelé třídy vytvořit třídu.</span><span class="sxs-lookup"><span data-stu-id="899aa-141">These access modifiers define how users of the class can construct the class.</span></span> <span data-ttu-id="899aa-142">Další informace naleznete [v tématu Access Modifiers](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="899aa-142">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
 <span data-ttu-id="899aa-143">Konstruktor lze deklarovat statické pomocí [statické](../../language-reference/keywords/static.md) klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="899aa-143">A constructor can be declared static by using the [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="899aa-144">Statické konstruktory jsou volány automaticky, bezprostředně před všechny statická pole jsou přístupné a obecně se používají k inicializaci statické členy třídy.</span><span class="sxs-lookup"><span data-stu-id="899aa-144">Static constructors are called automatically, immediately before any static fields are accessed, and are generally used to initialize static class members.</span></span> <span data-ttu-id="899aa-145">Další informace naleznete [v tématu Statické konstruktory](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="899aa-145">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="899aa-146">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="899aa-146">C# Language Specification</span></span>  

<span data-ttu-id="899aa-147">Další informace naleznete [v tématu instance konstruktory](~/_csharplang/spec/classes.md#instance-constructors) a [statické konstruktory](~/_csharplang/spec/classes.md#static-constructors) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="899aa-147">For more information, see [Instance constructors](~/_csharplang/spec/classes.md#instance-constructors) and [Static constructors](~/_csharplang/spec/classes.md#static-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="899aa-148">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="899aa-148">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="899aa-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="899aa-149">See also</span></span>

- [<span data-ttu-id="899aa-150">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="899aa-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="899aa-151">Třídy a struky</span><span class="sxs-lookup"><span data-stu-id="899aa-151">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="899aa-152">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="899aa-152">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="899aa-153">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="899aa-153">Finalizers</span></span>](./destructors.md)
