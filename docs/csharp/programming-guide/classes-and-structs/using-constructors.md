---
title: Použití konstruktorů – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: cb6a0befb9e2e628f066061282532513019c1419
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418734"
---
# <a name="using-constructors-c-programming-guide"></a><span data-ttu-id="01660-102">Použití konstruktorů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="01660-102">Using Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="01660-103">Při vytvoření [třídy](../../language-reference/keywords/class.md) nebo [struktury](../../language-reference/keywords/struct.md) se zavolá její konstruktor.</span><span class="sxs-lookup"><span data-stu-id="01660-103">When a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="01660-104">Konstruktory mají stejný název jako třída nebo struktura a obvykle inicializují datové členy nového objektu.</span><span class="sxs-lookup"><span data-stu-id="01660-104">Constructors have the same name as the class or struct, and they usually initialize the data members of the new object.</span></span>  
  
 <span data-ttu-id="01660-105">V následujícím příkladu je třída s názvem `Taxi` definována pomocí jednoduchého konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="01660-105">In the following example, a class named `Taxi` is defined by using a simple constructor.</span></span> <span data-ttu-id="01660-106">Tato třída se pak vytvoří s operátorem [New](../../language-reference/operators/new-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="01660-106">This class is then instantiated with the [new](../../language-reference/operators/new-operator.md) operator.</span></span> <span data-ttu-id="01660-107">Konstruktor `Taxi` je vyvolán operátorem `new` ihned po přidělení paměti pro nový objekt.</span><span class="sxs-lookup"><span data-stu-id="01660-107">The `Taxi` constructor is invoked by the `new` operator immediately after memory is allocated for the new object.</span></span>  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 <span data-ttu-id="01660-108">Konstruktor, který nepřijímá žádné parametry, se nazývá *konstruktor bez parametrů*.</span><span class="sxs-lookup"><span data-stu-id="01660-108">A constructor that takes no parameters is called a *parameterless constructor*.</span></span> <span data-ttu-id="01660-109">Konstruktory bez parametrů jsou vyvolány pokaždé, když je vytvořena instance objektu pomocí operátoru `new` a nejsou k dispozici žádné argumenty pro `new`.</span><span class="sxs-lookup"><span data-stu-id="01660-109">Parameterless constructors are invoked whenever an object is instantiated by using the `new` operator and no arguments are provided to `new`.</span></span> <span data-ttu-id="01660-110">Další informace naleznete v tématu [konstruktory instancí](./instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="01660-110">For more information, see [Instance Constructors](./instance-constructors.md).</span></span>  
  
 <span data-ttu-id="01660-111">Pokud třída není [statická](../../language-reference/keywords/static.md), třídy bez konstruktorů mají za účelem povolení vytváření instancí třídy veřejný konstruktor C# bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="01660-111">Unless the class is [static](../../language-reference/keywords/static.md), classes without constructors are given a public parameterless constructor by the C# compiler in order to enable class instantiation.</span></span> <span data-ttu-id="01660-112">Další informace naleznete v tématu [statické třídy a statické členy třídy](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="01660-112">For more information, see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="01660-113">Instanci třídy lze zabránit vytvořením konstruktoru jako soukromého pomocí následujícího postupu:</span><span class="sxs-lookup"><span data-stu-id="01660-113">You can prevent a class from being instantiated by making the constructor private, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="01660-114">Další informace naleznete v tématu [Soukromé konstruktory](./private-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="01660-114">For more information, see [Private Constructors](./private-constructors.md).</span></span>  
  
 <span data-ttu-id="01660-115">Konstruktory pro typy [struktury](../../language-reference/keywords/struct.md) připomínají konstruktory třídy, ale `structs` nesmí obsahovat explicitní konstruktor bez parametrů, protože jeden je poskytnut automaticky kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="01660-115">Constructors for [struct](../../language-reference/keywords/struct.md) types resemble class constructors, but `structs` cannot contain an explicit parameterless constructor because one is provided automatically by the compiler.</span></span> <span data-ttu-id="01660-116">Tento konstruktor inicializuje každé pole v `struct` výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="01660-116">This constructor initializes each field in the `struct` to the default values.</span></span> <span data-ttu-id="01660-117">Další informace najdete v tématu [Tabulka výchozích hodnot](../../language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="01660-117">For more information, see [Default Values Table](../../language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="01660-118">Tento konstruktor bez parametrů je však vyvolána pouze v případě, že je vytvořena instance `struct` s `new`.</span><span class="sxs-lookup"><span data-stu-id="01660-118">However, this parameterless constructor is only invoked if the `struct` is instantiated with `new`.</span></span> <span data-ttu-id="01660-119">Například tento kód používá konstruktor bez parametrů pro <xref:System.Int32>, takže jste si jisti, že je inicializováno celé číslo:</span><span class="sxs-lookup"><span data-stu-id="01660-119">For example, this code uses the parameterless constructor for <xref:System.Int32>, so that you are assured that the integer is initialized:</span></span>  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="01660-120">Následující kód však způsobí chybu kompilátoru, protože nepoužívá `new`a protože se pokouší použít objekt, který nebyl inicializován:</span><span class="sxs-lookup"><span data-stu-id="01660-120">The following code, however, causes a compiler error because it does not use `new`, and because it tries to use an object that has not been initialized:</span></span>  
  
```csharp  
int i;  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="01660-121">Alternativně lze objekty založené na `structs` (včetně všech předdefinovaných číselných typů) inicializovat nebo přiřadit a pak použít jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="01660-121">Alternatively, objects based on `structs` (including all built-in numeric types) can be initialized or assigned and then used as in the following example:</span></span>  
  
```csharp  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 <span data-ttu-id="01660-122">Proto není požadováno volání konstruktoru bez parametrů pro typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="01660-122">So calling the parameterless constructor for a value type is not required.</span></span>  
  
 <span data-ttu-id="01660-123">Třídy i `structs` mohou definovat konstruktory, které přijímají parametry.</span><span class="sxs-lookup"><span data-stu-id="01660-123">Both classes and `structs` can define constructors that take parameters.</span></span> <span data-ttu-id="01660-124">Konstruktory, které přijímají parametry, musí být volány prostřednictvím příkazu `new` nebo [základního](../../language-reference/keywords/base.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="01660-124">Constructors that take parameters must be called through a `new` statement or a [base](../../language-reference/keywords/base.md) statement.</span></span> <span data-ttu-id="01660-125">Třídy a `structs` mohou také definovat více konstruktorů a není ani nutné definovat konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="01660-125">Classes and `structs` can also define multiple constructors, and neither is required to define a parameterless constructor.</span></span> <span data-ttu-id="01660-126">Příklad:</span><span class="sxs-lookup"><span data-stu-id="01660-126">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 <span data-ttu-id="01660-127">Tuto třídu lze vytvořit pomocí některého z následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="01660-127">This class can be created by using either of the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 <span data-ttu-id="01660-128">Konstruktor může použít klíčové slovo `base` pro volání konstruktoru základní třídy.</span><span class="sxs-lookup"><span data-stu-id="01660-128">A constructor can use the `base` keyword to call the constructor of a base class.</span></span> <span data-ttu-id="01660-129">Příklad:</span><span class="sxs-lookup"><span data-stu-id="01660-129">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 <span data-ttu-id="01660-130">V tomto příkladu je konstruktor pro základní třídu volán před provedením bloku pro konstruktor.</span><span class="sxs-lookup"><span data-stu-id="01660-130">In this example, the constructor for the base class is called before the block for the constructor is executed.</span></span> <span data-ttu-id="01660-131">Klíčové slovo `base` lze použít s parametry nebo bez nich.</span><span class="sxs-lookup"><span data-stu-id="01660-131">The `base` keyword can be used with or without parameters.</span></span> <span data-ttu-id="01660-132">Parametry konstruktoru lze použít jako parametry `base`nebo jako součást výrazu.</span><span class="sxs-lookup"><span data-stu-id="01660-132">Any parameters to the constructor can be used as parameters to `base`, or as part of an expression.</span></span> <span data-ttu-id="01660-133">Další informace naleznete v tématu [Base](../../language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="01660-133">For more information, see [base](../../language-reference/keywords/base.md).</span></span>  
  
 <span data-ttu-id="01660-134">V odvozené třídě, pokud konstruktor základní třídy není volán explicitně pomocí klíčového slova `base`, konstruktor bez parametrů, pokud existuje, je volán implicitně.</span><span class="sxs-lookup"><span data-stu-id="01660-134">In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the parameterless constructor, if there is one, is called implicitly.</span></span> <span data-ttu-id="01660-135">To znamená, že následující deklarace konstruktoru jsou efektivně stejné:</span><span class="sxs-lookup"><span data-stu-id="01660-135">This means that the following constructor declarations are effectively the same:</span></span>  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 <span data-ttu-id="01660-136">Pokud základní třída nenabízí konstruktor bez parametrů, musí odvozená třída vytvořit explicitní volání základního konstruktoru pomocí `base`.</span><span class="sxs-lookup"><span data-stu-id="01660-136">If a base class does not offer a parameterless constructor, the derived class must make an explicit call to a base constructor by using `base`.</span></span>  
  
 <span data-ttu-id="01660-137">Konstruktor může vyvolat jiný konstruktor ve stejném objektu pomocí klíčového slova [This](../../language-reference/keywords/this.md) .</span><span class="sxs-lookup"><span data-stu-id="01660-137">A constructor can invoke another constructor in the same object by using the [this](../../language-reference/keywords/this.md) keyword.</span></span> <span data-ttu-id="01660-138">Podobně jako `base`, `this` lze použít s parametry nebo bez parametrů a jakékoli parametry v konstruktoru jsou k dispozici jako parametry `this`nebo jako součást výrazu.</span><span class="sxs-lookup"><span data-stu-id="01660-138">Like `base`, `this` can be used with or without parameters, and any parameters in the constructor are available as parameters to `this`, or as part of an expression.</span></span> <span data-ttu-id="01660-139">Například druhý konstruktor v předchozím příkladu lze přepsat pomocí `this`:</span><span class="sxs-lookup"><span data-stu-id="01660-139">For example, the second constructor in the previous example can be rewritten using `this`:</span></span>  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 <span data-ttu-id="01660-140">Použití klíčového slova `this` v předchozím příkladu způsobí, že se tento konstruktor zavolá:</span><span class="sxs-lookup"><span data-stu-id="01660-140">The use of the `this` keyword in the previous example causes this constructor to be called:</span></span>  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 <span data-ttu-id="01660-141">Konstruktory mohou být označeny jako [veřejné](../../language-reference/keywords/public.md), [privátní](../../language-reference/keywords/private.md), [chráněné](../../language-reference/keywords/protected.md), [interní](../../language-reference/keywords/internal.md), [chráněné interní](../../language-reference/keywords/protected-internal.md) nebo [soukromé chráněné](../../language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="01660-141">Constructors can be marked as [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="01660-142">Tyto modifikátory přístupu definují, jak mohou uživatelé třídy vytvořit třídu.</span><span class="sxs-lookup"><span data-stu-id="01660-142">These access modifiers define how users of the class can construct the class.</span></span> <span data-ttu-id="01660-143">Další informace najdete v tématu [modifikátory přístupu](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="01660-143">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
 <span data-ttu-id="01660-144">Konstruktor lze deklarovat staticky pomocí klíčového slova [static](../../language-reference/keywords/static.md) .</span><span class="sxs-lookup"><span data-stu-id="01660-144">A constructor can be declared static by using the [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="01660-145">Statické konstruktory jsou volány automaticky, bezprostředně před tím, než jsou k dispozici statická pole a jsou obecně použity pro inicializaci statických členů třídy.</span><span class="sxs-lookup"><span data-stu-id="01660-145">Static constructors are called automatically, immediately before any static fields are accessed, and are generally used to initialize static class members.</span></span> <span data-ttu-id="01660-146">Další informace naleznete v tématu [statické konstruktory](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="01660-146">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="01660-147">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="01660-147">C# Language Specification</span></span>  

<span data-ttu-id="01660-148">Další informace naleznete v tématu [konstruktory instancí](~/_csharplang/spec/classes.md#instance-constructors) a [statické konstruktory](~/_csharplang/spec/classes.md#static-constructors) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="01660-148">For more information, see [Instance constructors](~/_csharplang/spec/classes.md#instance-constructors) and [Static constructors](~/_csharplang/spec/classes.md#static-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="01660-149">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="01660-149">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="01660-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01660-150">See also</span></span>

- [<span data-ttu-id="01660-151">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="01660-151">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="01660-152">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="01660-152">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="01660-153">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="01660-153">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="01660-154">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="01660-154">Finalizers</span></span>](./destructors.md)
