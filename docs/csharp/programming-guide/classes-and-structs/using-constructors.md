---
title: Použití konstruktorů (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 5fe6f10e3842c0c0aac4b2669f8ca367fa8c3be2
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
---
# <a name="using-constructors-c-programming-guide"></a><span data-ttu-id="991dc-102">Použití konstruktorů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="991dc-102">Using Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="991dc-103">Když [– třída](../../../csharp/language-reference/keywords/class.md) nebo [struktura](../../../csharp/language-reference/keywords/struct.md) je vytvořen, se nazývá jeho konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="991dc-103">When a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="991dc-104">Konstruktory mít stejný název jako třídě nebo struktuře a obvykle inicializují datových členů nového objektu.</span><span class="sxs-lookup"><span data-stu-id="991dc-104">Constructors have the same name as the class or struct, and they usually initialize the data members of the new object.</span></span>  
  
 <span data-ttu-id="991dc-105">V následujícím příkladu třída s názvem `Taxi` se definuje pomocí jednoduchého konstruktor.</span><span class="sxs-lookup"><span data-stu-id="991dc-105">In the following example, a class named `Taxi` is defined by using a simple constructor.</span></span> <span data-ttu-id="991dc-106">Tato třída je pak vytvořena s [nové](../../../csharp/language-reference/keywords/new.md) operátor.</span><span class="sxs-lookup"><span data-stu-id="991dc-106">This class is then instantiated with the [new](../../../csharp/language-reference/keywords/new.md) operator.</span></span> <span data-ttu-id="991dc-107">`Taxi` Se vyvolat konstruktor `new` operátor ihned po paměti je přidělen pro nový objekt.</span><span class="sxs-lookup"><span data-stu-id="991dc-107">The `Taxi` constructor is invoked by the `new` operator immediately after memory is allocated for the new object.</span></span>  
  
 [!code-csharp[csProgGuideObjects#53](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_1.cs)]  
  
 <span data-ttu-id="991dc-108">Volání konstruktoru, které nepřijímá žádné parametry *výchozí konstruktor*.</span><span class="sxs-lookup"><span data-stu-id="991dc-108">A constructor that takes no parameters is called a *default constructor*.</span></span> <span data-ttu-id="991dc-109">Výchozí konstruktory jsou vyvolány při každém vytvoření instance objektu pomocí `new` operátor a odpovídající žádné argumenty `new`.</span><span class="sxs-lookup"><span data-stu-id="991dc-109">Default constructors are invoked whenever an object is instantiated by using the `new` operator and no arguments are provided to `new`.</span></span> <span data-ttu-id="991dc-110">Další informace najdete v tématu [konstruktory instancí](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="991dc-110">For more information, see [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  
  
 <span data-ttu-id="991dc-111">Pokud je třída [statické](../../../csharp/language-reference/keywords/static.md), tříd bez konstruktory jsou uvedeny výchozí veřejný konstruktor kompilátorem C#, chcete-li povolit vytváření instance třídy.</span><span class="sxs-lookup"><span data-stu-id="991dc-111">Unless the class is [static](../../../csharp/language-reference/keywords/static.md), classes without constructors are given a public default constructor by the C# compiler in order to enable class instantiation.</span></span> <span data-ttu-id="991dc-112">Další informace najdete v tématu [statické třídy a statické členy třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="991dc-112">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="991dc-113">Třídu můžete zabránit ve vytváření instancí tím, že konstruktoru privátní, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="991dc-113">You can prevent a class from being instantiated by making the constructor private, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_2.cs)]  
  
 <span data-ttu-id="991dc-114">Další informace najdete v tématu [soukromé konstruktory](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="991dc-114">For more information, see [Private Constructors](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).</span></span>  
  
 <span data-ttu-id="991dc-115">Konstruktory pro [struktura](../../../csharp/language-reference/keywords/struct.md) typy vypadat třída konstruktory, ale `structs` nemůže obsahovat explicitní výchozí konstruktor, protože je zadáno automaticky kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="991dc-115">Constructors for [struct](../../../csharp/language-reference/keywords/struct.md) types resemble class constructors, but `structs` cannot contain an explicit default constructor because one is provided automatically by the compiler.</span></span> <span data-ttu-id="991dc-116">Tento konstruktor inicializuje každé pole v `struct` na výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="991dc-116">This constructor initializes each field in the `struct` to the default values.</span></span> <span data-ttu-id="991dc-117">Další informace najdete v tématu [výchozí hodnoty tabulky](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="991dc-117">For more information, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="991dc-118">Však tato výchozí konstruktor je volána, pouze pokud `struct` je vytvořena s `new`.</span><span class="sxs-lookup"><span data-stu-id="991dc-118">However, this default constructor is only invoked if the `struct` is instantiated with `new`.</span></span> <span data-ttu-id="991dc-119">Například tento kód používá výchozí konstruktor pro <xref:System.Int32>, takže budete mít jistotu, že je inicializován na celé číslo:</span><span class="sxs-lookup"><span data-stu-id="991dc-119">For example, this code uses the default constructor for <xref:System.Int32>, so that you are assured that the integer is initialized:</span></span>  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="991dc-120">Následující kód, ale způsobí chybu kompilátoru, protože nepoužívá `new`, a protože se pokusí použít objekt, který není inicializovaný.:</span><span class="sxs-lookup"><span data-stu-id="991dc-120">The following code, however, causes a compiler error because it does not use `new`, and because it tries to use an object that has not been initialized:</span></span>  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="991dc-121">Případně na základě objektů `structs` (včetně všech předdefinovaných číselnými typy) může být inicializován nebo přiřadit a pak se použije jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="991dc-121">Alternatively, objects based on `structs` (including all built-in numeric types) can be initialized or assigned and then used as in the following example:</span></span>  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 <span data-ttu-id="991dc-122">Proto volání výchozí konstruktor pro typ hodnoty se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="991dc-122">So calling the default constructor for a value type is not required.</span></span>  
  
 <span data-ttu-id="991dc-123">Obě třídy a `structs` můžete definovat konstruktory, které nepřijímají parametry.</span><span class="sxs-lookup"><span data-stu-id="991dc-123">Both classes and `structs` can define constructors that take parameters.</span></span> <span data-ttu-id="991dc-124">Konstruktory, které nepřijímají parametry musí být voláno prostřednictvím `new` příkaz nebo [základní](../../../csharp/language-reference/keywords/base.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="991dc-124">Constructors that take parameters must be called through a `new` statement or a [base](../../../csharp/language-reference/keywords/base.md) statement.</span></span> <span data-ttu-id="991dc-125">Třídy a `structs` můžete také definovat více konstruktory a ani jeden z nich je potřeba definovat výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="991dc-125">Classes and `structs` can also define multiple constructors, and neither is required to define a default constructor.</span></span> <span data-ttu-id="991dc-126">Příklad:</span><span class="sxs-lookup"><span data-stu-id="991dc-126">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#54](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_3.cs)]  
  
 <span data-ttu-id="991dc-127">Tato třída lze vytvořit pomocí některé z následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="991dc-127">This class can be created by using either of the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#55](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_4.cs)]  
  
 <span data-ttu-id="991dc-128">Můžete použít konstruktor `base` – klíčové slovo volat konstruktor základní třídy.</span><span class="sxs-lookup"><span data-stu-id="991dc-128">A constructor can use the `base` keyword to call the constructor of a base class.</span></span> <span data-ttu-id="991dc-129">Příklad:</span><span class="sxs-lookup"><span data-stu-id="991dc-129">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#56](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_5.cs)]  
  
 <span data-ttu-id="991dc-130">V tomto příkladu v konstruktoru pro základní třídy je volána před provedením blok pro konstruktor.</span><span class="sxs-lookup"><span data-stu-id="991dc-130">In this example, the constructor for the base class is called before the block for the constructor is executed.</span></span> <span data-ttu-id="991dc-131">`base` – Klíčové slovo lze použít s nebo bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="991dc-131">The `base` keyword can be used with or without parameters.</span></span> <span data-ttu-id="991dc-132">Žádné parametry konstruktoru lze použít jako parametry, které `base`, nebo jako součást výrazu.</span><span class="sxs-lookup"><span data-stu-id="991dc-132">Any parameters to the constructor can be used as parameters to `base`, or as part of an expression.</span></span> <span data-ttu-id="991dc-133">Další informace najdete v tématu [základní](../../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="991dc-133">For more information, see [base](../../../csharp/language-reference/keywords/base.md).</span></span>  
  
 <span data-ttu-id="991dc-134">V odvozené třídě, pokud konstruktor základní třída není explicitně volána pomocí `base` – klíčové slovo, výchozí konstruktor, pokud existuje, nazývá implicitně.</span><span class="sxs-lookup"><span data-stu-id="991dc-134">In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the default constructor, if there is one, is called implicitly.</span></span> <span data-ttu-id="991dc-135">To znamená, že následující konstruktor deklarace jsou efektivně stejné:</span><span class="sxs-lookup"><span data-stu-id="991dc-135">This means that the following constructor declarations are effectively the same:</span></span>  
  
 [!code-csharp[csProgGuideObjects#58](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_6.cs)]  
  
 [!code-csharp[csProgGuideObjects#57](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_7.cs)]  
  
 <span data-ttu-id="991dc-136">Pokud základní třídu nenabízí výchozí konstruktor, odvozené třídy musí být být explicitní volání konstruktoru základní pomocí `base`.</span><span class="sxs-lookup"><span data-stu-id="991dc-136">If a base class does not offer a default constructor, the derived class must make an explicit call to a base constructor by using `base`.</span></span>  
  
 <span data-ttu-id="991dc-137">Konstruktor můžete vyvolat jiný konstruktor pro stejný objekt pomocí [to](../../../csharp/language-reference/keywords/this.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="991dc-137">A constructor can invoke another constructor in the same object by using the [this](../../../csharp/language-reference/keywords/this.md) keyword.</span></span> <span data-ttu-id="991dc-138">Jako `base`, `this` lze použít s nebo bez parametrů, a jsou k dispozici jako parametry pro všechny parametry v konstruktoru `this`, nebo jako součást výrazu.</span><span class="sxs-lookup"><span data-stu-id="991dc-138">Like `base`, `this` can be used with or without parameters, and any parameters in the constructor are available as parameters to `this`, or as part of an expression.</span></span> <span data-ttu-id="991dc-139">Druhý konstruktor v předchozím příkladu může být například přepsán pomocí `this`:</span><span class="sxs-lookup"><span data-stu-id="991dc-139">For example, the second constructor in the previous example can be rewritten using `this`:</span></span>  
  
 [!code-csharp[csProgGuideObjects#59](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_8.cs)]  
  
 <span data-ttu-id="991dc-140">Použití `this` – klíčové slovo v předchozím příkladu způsobí, že tento konstruktor k volání:</span><span class="sxs-lookup"><span data-stu-id="991dc-140">The use of the `this` keyword in the previous example causes this constructor to be called:</span></span>  
  
 [!code-csharp[csProgGuideObjects#60](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_9.cs)]  
  
 <span data-ttu-id="991dc-141">Může být konstruktory označený jako [veřejné](../../../csharp/language-reference/keywords/public.md), [privátní](../../../csharp/language-reference/keywords/private.md), [chráněné](../../../csharp/language-reference/keywords/protected.md), [interní](../../../csharp/language-reference/keywords/internal.md), [chráněné interní](../../../csharp/language-reference/keywords/protected-internal.md)nebo [privátní chráněné](../../../csharp/language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="991dc-141">Constructors can be marked as [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md) or [private protected](../../../csharp/language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="991dc-142">Tyto modifikátory přístupu definovat, jak uživatelé třídy můžete vytvořit třídu.</span><span class="sxs-lookup"><span data-stu-id="991dc-142">These access modifiers define how users of the class can construct the class.</span></span> <span data-ttu-id="991dc-143">Další informace najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="991dc-143">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="991dc-144">Konstruktor lze deklarovat statickou pomocí [statické](../../../csharp/language-reference/keywords/static.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="991dc-144">A constructor can be declared static by using the [static](../../../csharp/language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="991dc-145">Statické konstruktory jsou automaticky, volá se bezprostředně před všechny statická pole ke kterým se přistupuje a jsou obecně používány k chybě při inicializaci členové statické třídy.</span><span class="sxs-lookup"><span data-stu-id="991dc-145">Static constructors are called automatically, immediately before any static fields are accessed, and are generally used to initialize static class members.</span></span> <span data-ttu-id="991dc-146">Další informace najdete v tématu [statické konstruktory](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="991dc-146">For more information, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="991dc-147">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="991dc-147">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="991dc-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="991dc-148">See Also</span></span>  
 [<span data-ttu-id="991dc-149">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="991dc-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="991dc-150">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="991dc-150">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="991dc-151">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="991dc-151">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="991dc-152">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="991dc-152">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
