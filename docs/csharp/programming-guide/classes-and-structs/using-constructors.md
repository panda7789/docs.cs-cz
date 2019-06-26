---
title: Použití konstruktorů - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 14ff272fe940c265dc8984d6b20985bb2d2ba12d
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398254"
---
# <a name="using-constructors-c-programming-guide"></a><span data-ttu-id="4b77b-102">Použití konstruktorů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="4b77b-102">Using Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="4b77b-103">Při [třídy](../../../csharp/language-reference/keywords/class.md) nebo [struktura](../../../csharp/language-reference/keywords/struct.md) je vytvořen, se nazývá konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="4b77b-103">When a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="4b77b-104">Konstruktory mají stejný název jako třídy nebo struktury a obvykle inicializují datové členy nového objektu.</span><span class="sxs-lookup"><span data-stu-id="4b77b-104">Constructors have the same name as the class or struct, and they usually initialize the data members of the new object.</span></span>  
  
 <span data-ttu-id="4b77b-105">V následujícím příkladu třída s názvem `Taxi` je definován pomocí jednoduchého konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="4b77b-105">In the following example, a class named `Taxi` is defined by using a simple constructor.</span></span> <span data-ttu-id="4b77b-106">Tato třída je pak vytvořena s [nové](../../../csharp/language-reference/operators/new-operator.md) operátor.</span><span class="sxs-lookup"><span data-stu-id="4b77b-106">This class is then instantiated with the [new](../../../csharp/language-reference/operators/new-operator.md) operator.</span></span> <span data-ttu-id="4b77b-107">`Taxi` Konstruktor vyvolá `new` je operátor ihned po paměti přidělené pro nový objekt.</span><span class="sxs-lookup"><span data-stu-id="4b77b-107">The `Taxi` constructor is invoked by the `new` operator immediately after memory is allocated for the new object.</span></span>  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 <span data-ttu-id="4b77b-108">Je volána konstruktor, který nepřijímá žádné parametry *konstruktor bez parametrů*.</span><span class="sxs-lookup"><span data-stu-id="4b77b-108">A constructor that takes no parameters is called a *parameterless constructor*.</span></span> <span data-ttu-id="4b77b-109">Výchozí konstruktory jsou vyvolány při každém objektu je vytvořena instance s použitím `new` operátor a bez argumentů `new`.</span><span class="sxs-lookup"><span data-stu-id="4b77b-109">Default constructors are invoked whenever an object is instantiated by using the `new` operator and no arguments are provided to `new`.</span></span> <span data-ttu-id="4b77b-110">Další informace najdete v tématu [konstruktory instancí](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="4b77b-110">For more information, see [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  
  
 <span data-ttu-id="4b77b-111">Pokud je třída [statické](../../../csharp/language-reference/keywords/static.md), třídy bez konstruktory jsou uvedeny veřejný konstruktor bez parametrů podle C# kompilátoru Chcete-li povolit vytváření instance třídy.</span><span class="sxs-lookup"><span data-stu-id="4b77b-111">Unless the class is [static](../../../csharp/language-reference/keywords/static.md), classes without constructors are given a public parameterless constructor by the C# compiler in order to enable class instantiation.</span></span> <span data-ttu-id="4b77b-112">Další informace najdete v tématu [statické třídy a statické členy třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="4b77b-112">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="4b77b-113">Třída může zabránit před tím, že konstruktor soukromý, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="4b77b-113">You can prevent a class from being instantiated by making the constructor private, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="4b77b-114">Další informace najdete v tématu [soukromé konstruktory](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="4b77b-114">For more information, see [Private Constructors](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).</span></span>  
  
 <span data-ttu-id="4b77b-115">Konstruktory pro [struktura](../../../csharp/language-reference/keywords/struct.md) typy vypadat podobně jako konstruktor třídy, ale `structs` nemůžou obsahovat explicitní konstruktor bez parametrů, protože je automaticky zadáno kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="4b77b-115">Constructors for [struct](../../../csharp/language-reference/keywords/struct.md) types resemble class constructors, but `structs` cannot contain an explicit parameterless constructor because one is provided automatically by the compiler.</span></span> <span data-ttu-id="4b77b-116">Tento konstruktor inicializuje každé pole v `struct` na výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4b77b-116">This constructor initializes each field in the `struct` to the default values.</span></span> <span data-ttu-id="4b77b-117">Další informace najdete v tématu [výchozí hodnoty tabulky](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="4b77b-117">For more information, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="4b77b-118">Nicméně, tento konstruktor je vyvolána pouze v případě `struct` je vytvořena instance s `new`.</span><span class="sxs-lookup"><span data-stu-id="4b77b-118">However, this parameterless constructor is only invoked if the `struct` is instantiated with `new`.</span></span> <span data-ttu-id="4b77b-119">Například tento kód používá konstruktor bez parametrů <xref:System.Int32>, takže budete mít jistotu, že je inicializován na celé číslo:</span><span class="sxs-lookup"><span data-stu-id="4b77b-119">For example, this code uses the parameterless constructor for <xref:System.Int32>, so that you are assured that the integer is initialized:</span></span>  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="4b77b-120">Následující kód, ale způsobí chybu kompilátoru, protože nepoužívá `new`, a protože se pokusí použít objekt, který není inicializovaná:</span><span class="sxs-lookup"><span data-stu-id="4b77b-120">The following code, however, causes a compiler error because it does not use `new`, and because it tries to use an object that has not been initialized:</span></span>  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="4b77b-121">Můžete také na základě objektů `structs` (včetně všech předdefinovaných číselných typů) může být inicializována nebo přiřazena a pak použít jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="4b77b-121">Alternatively, objects based on `structs` (including all built-in numeric types) can be initialized or assigned and then used as in the following example:</span></span>  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 <span data-ttu-id="4b77b-122">Proto volání konstruktoru bez parametrů typu hodnoty se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="4b77b-122">So calling the parameterless constructor for a value type is not required.</span></span>  
  
 <span data-ttu-id="4b77b-123">Obě třídy a `structs` můžete definovat konstruktory, které přijímají parametry.</span><span class="sxs-lookup"><span data-stu-id="4b77b-123">Both classes and `structs` can define constructors that take parameters.</span></span> <span data-ttu-id="4b77b-124">Konstruktory, které přijímají parametry musí být volána až `new` příkaz nebo [základní](../../../csharp/language-reference/keywords/base.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="4b77b-124">Constructors that take parameters must be called through a `new` statement or a [base](../../../csharp/language-reference/keywords/base.md) statement.</span></span> <span data-ttu-id="4b77b-125">Třídy a `structs` můžete také definovat víc konstruktorů a ani je potřeba definovat konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="4b77b-125">Classes and `structs` can also define multiple constructors, and neither is required to define a parameterless constructor.</span></span> <span data-ttu-id="4b77b-126">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4b77b-126">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 <span data-ttu-id="4b77b-127">Tuto třídu lze vytvořit pomocí některého z následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="4b77b-127">This class can be created by using either of the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 <span data-ttu-id="4b77b-128">Můžete použít konstruktor `base` – klíčové slovo volat konstruktor základní třídy.</span><span class="sxs-lookup"><span data-stu-id="4b77b-128">A constructor can use the `base` keyword to call the constructor of a base class.</span></span> <span data-ttu-id="4b77b-129">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4b77b-129">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 <span data-ttu-id="4b77b-130">V tomto příkladu je volána konstruktor základní třídy před provedením blok pro konstruktor.</span><span class="sxs-lookup"><span data-stu-id="4b77b-130">In this example, the constructor for the base class is called before the block for the constructor is executed.</span></span> <span data-ttu-id="4b77b-131">`base` – Klíčové slovo lze použít s nebo bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="4b77b-131">The `base` keyword can be used with or without parameters.</span></span> <span data-ttu-id="4b77b-132">Žádné parametry pro konstruktor může sloužit jako parametry pro `base`, nebo jako součást výrazu.</span><span class="sxs-lookup"><span data-stu-id="4b77b-132">Any parameters to the constructor can be used as parameters to `base`, or as part of an expression.</span></span> <span data-ttu-id="4b77b-133">Další informace najdete v tématu [základní](../../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="4b77b-133">For more information, see [base](../../../csharp/language-reference/keywords/base.md).</span></span>  
  
 <span data-ttu-id="4b77b-134">V odvozené třídě, pokud není explicitně volána konstruktor základní třídy pomocí `base` – klíčové slovo, konstruktor bez parametrů, pokud existuje, nazývá implicitně.</span><span class="sxs-lookup"><span data-stu-id="4b77b-134">In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the parameterless constructor, if there is one, is called implicitly.</span></span> <span data-ttu-id="4b77b-135">To znamená, že následující deklarace konstruktoru se prakticky neliší:</span><span class="sxs-lookup"><span data-stu-id="4b77b-135">This means that the following constructor declarations are effectively the same:</span></span>  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 <span data-ttu-id="4b77b-136">Pokud základní třída se nebude poskytovat konstruktor bez parametrů, odvozené třídy musí provést explicitní volání konstruktoru základní konstruktor pomocí `base`.</span><span class="sxs-lookup"><span data-stu-id="4b77b-136">If a base class does not offer a parameterless constructor, the derived class must make an explicit call to a base constructor by using `base`.</span></span>  
  
 <span data-ttu-id="4b77b-137">Konstruktor může vyvolat jiný konstruktor ve stejném objektu pomocí [to](../../../csharp/language-reference/keywords/this.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="4b77b-137">A constructor can invoke another constructor in the same object by using the [this](../../../csharp/language-reference/keywords/this.md) keyword.</span></span> <span data-ttu-id="4b77b-138">Stejně jako `base`, `this` lze použít s nebo bez parametrů, a jsou k dispozici jako parametry pro všechny parametry v konstruktoru `this`, nebo jako součást výrazu.</span><span class="sxs-lookup"><span data-stu-id="4b77b-138">Like `base`, `this` can be used with or without parameters, and any parameters in the constructor are available as parameters to `this`, or as part of an expression.</span></span> <span data-ttu-id="4b77b-139">Například, druhý konstruktor v předchozím příkladu může být přepsán pomocí `this`:</span><span class="sxs-lookup"><span data-stu-id="4b77b-139">For example, the second constructor in the previous example can be rewritten using `this`:</span></span>  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 <span data-ttu-id="4b77b-140">Použití `this` – klíčové slovo v předchozím příkladu způsobí, že tento konstruktor k volání:</span><span class="sxs-lookup"><span data-stu-id="4b77b-140">The use of the `this` keyword in the previous example causes this constructor to be called:</span></span>  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 <span data-ttu-id="4b77b-141">Konstruktory mohou být označeny jako [veřejné](../../../csharp/language-reference/keywords/public.md), [privátní](../../../csharp/language-reference/keywords/private.md), [chráněné](../../../csharp/language-reference/keywords/protected.md), [interní](../../../csharp/language-reference/keywords/internal.md), [chráněné vnitřní](../../../csharp/language-reference/keywords/protected-internal.md)nebo [private, protected](../../../csharp/language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="4b77b-141">Constructors can be marked as [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md) or [private protected](../../../csharp/language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="4b77b-142">Tyto modifikátory přístupu definují, jak uživatelé třídy můžete vytvořit třídu.</span><span class="sxs-lookup"><span data-stu-id="4b77b-142">These access modifiers define how users of the class can construct the class.</span></span> <span data-ttu-id="4b77b-143">Další informace najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="4b77b-143">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="4b77b-144">Konstruktor může být deklarované jako statické pomocí [statické](../../../csharp/language-reference/keywords/static.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="4b77b-144">A constructor can be declared static by using the [static](../../../csharp/language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="4b77b-145">Statické konstruktory jsou automaticky, volá se bezprostředně před všechny statické pole jsou přístupné a obvykle slouží k inicializaci statické členy třídy.</span><span class="sxs-lookup"><span data-stu-id="4b77b-145">Static constructors are called automatically, immediately before any static fields are accessed, and are generally used to initialize static class members.</span></span> <span data-ttu-id="4b77b-146">Další informace najdete v tématu [statické konstruktory](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="4b77b-146">For more information, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="4b77b-147">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4b77b-147">C# Language Specification</span></span>  

<span data-ttu-id="4b77b-148">Další informace najdete v tématu [Instance konstruktory](~/_csharplang/spec/classes.md#instance-constructors) a [statické konstruktory](~/_csharplang/spec/classes.md#static-constructors) v [ C# specifikace jazyka](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="4b77b-148">For more information, see [Instance constructors](~/_csharplang/spec/classes.md#instance-constructors) and [Static constructors](~/_csharplang/spec/classes.md#static-constructors) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="4b77b-149">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="4b77b-149">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4b77b-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b77b-150">See also</span></span>

- [<span data-ttu-id="4b77b-151">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4b77b-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4b77b-152">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="4b77b-152">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="4b77b-153">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="4b77b-153">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [<span data-ttu-id="4b77b-154">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="4b77b-154">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
