---
title: Místní funkce – C# Průvodce programováním
ms.custom: seodec18
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: 7b6b46a33430a4a58c78245a0ab3bed1e0fbcd9c
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73455384"
---
# <a name="local-functions-c-programming-guide"></a><span data-ttu-id="e80ab-102">Místní funkce (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="e80ab-102">Local functions (C# Programming Guide)</span></span>

<span data-ttu-id="e80ab-103">Počínaje C# 7,0 C# podporuje *místní funkce*.</span><span class="sxs-lookup"><span data-stu-id="e80ab-103">Starting with C# 7.0, C# supports *local functions*.</span></span> <span data-ttu-id="e80ab-104">Lokální funkce jsou soukromé metody typu, které jsou vnořené v jiném členu.</span><span class="sxs-lookup"><span data-stu-id="e80ab-104">Local functions are private methods of a type that are nested in another member.</span></span> <span data-ttu-id="e80ab-105">Mohou být volány pouze ze svých nadřazených členů.</span><span class="sxs-lookup"><span data-stu-id="e80ab-105">They can only be called from their containing member.</span></span> <span data-ttu-id="e80ab-106">Místní funkce mohou být deklarovány v a volány z:</span><span class="sxs-lookup"><span data-stu-id="e80ab-106">Local functions can be declared in and called from:</span></span>

- <span data-ttu-id="e80ab-107">Metody, zejména iterátorové metody a asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="e80ab-107">Methods, especially iterator methods and async methods</span></span>
- <span data-ttu-id="e80ab-108">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="e80ab-108">Constructors</span></span>
- <span data-ttu-id="e80ab-109">Přistupující objekty vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e80ab-109">Property accessors</span></span>
- <span data-ttu-id="e80ab-110">Přístupové objekty událostí</span><span class="sxs-lookup"><span data-stu-id="e80ab-110">Event accessors</span></span>
- <span data-ttu-id="e80ab-111">Anonymní metody</span><span class="sxs-lookup"><span data-stu-id="e80ab-111">Anonymous methods</span></span>
- <span data-ttu-id="e80ab-112">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="e80ab-112">Lambda expressions</span></span>
- <span data-ttu-id="e80ab-113">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="e80ab-113">Finalizers</span></span>
- <span data-ttu-id="e80ab-114">Jiné místní funkce</span><span class="sxs-lookup"><span data-stu-id="e80ab-114">Other local functions</span></span>

<span data-ttu-id="e80ab-115">Místní funkce však nelze deklarovat uvnitř člena Expression-těle.</span><span class="sxs-lookup"><span data-stu-id="e80ab-115">However, local functions can't be declared inside an expression-bodied member.</span></span>

> [!NOTE]
> <span data-ttu-id="e80ab-116">V některých případech můžete použít výraz lambda pro implementaci funkcí, které podporuje také místní funkce.</span><span class="sxs-lookup"><span data-stu-id="e80ab-116">In some cases, you can use a lambda expression to implement functionality also supported by a local function.</span></span> <span data-ttu-id="e80ab-117">Porovnání naleznete v tématu [místní funkce v porovnání s lambda výrazy](../../local-functions-vs-lambdas.md).</span><span class="sxs-lookup"><span data-stu-id="e80ab-117">For a comparison, see [Local functions compared to Lambda expressions](../../local-functions-vs-lambdas.md).</span></span>

<span data-ttu-id="e80ab-118">Místní funkce usnadňují záměr vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="e80ab-118">Local functions make the intent of your code clear.</span></span> <span data-ttu-id="e80ab-119">Každý, kdo čte váš kód, uvidí, že metoda není možné volat s výjimkou obsahující metody.</span><span class="sxs-lookup"><span data-stu-id="e80ab-119">Anyone reading your code can see that the method is not callable except by the containing method.</span></span> <span data-ttu-id="e80ab-120">U týmových projektů také znemožňuje, aby jiný vývojář omylem volal metodu přímo z jiného místa ve třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="e80ab-120">For team projects, they also make it impossible for another developer to mistakenly call the method directly from elsewhere in the class or struct.</span></span>
 
## <a name="local-function-syntax"></a><span data-ttu-id="e80ab-121">Syntaxe lokální funkce</span><span class="sxs-lookup"><span data-stu-id="e80ab-121">Local function syntax</span></span>

<span data-ttu-id="e80ab-122">Lokální funkce je definována jako vnořená metoda uvnitř nadřazeného člena.</span><span class="sxs-lookup"><span data-stu-id="e80ab-122">A local function is defined as a nested method inside a containing member.</span></span> <span data-ttu-id="e80ab-123">Jeho definice má následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="e80ab-123">Its definition has the following syntax:</span></span>

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

<span data-ttu-id="e80ab-124">Místní funkce můžou používat modifikátory [Async](../../language-reference/keywords/async.md) a [unsafe](../../language-reference/keywords/unsafe.md) .</span><span class="sxs-lookup"><span data-stu-id="e80ab-124">Local functions can use the [async](../../language-reference/keywords/async.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span> 

<span data-ttu-id="e80ab-125">Všimněte si, že všechny místní proměnné, které jsou definovány v nadřazeném členu, včetně jeho parametrů metody, jsou přístupné v místní funkci.</span><span class="sxs-lookup"><span data-stu-id="e80ab-125">Note that all local variables that are defined in the containing member, including its method parameters, are accessible in the local function.</span></span> 

<span data-ttu-id="e80ab-126">Na rozdíl od definice metody nemůže definice lokální funkce obsahovat následující prvky:</span><span class="sxs-lookup"><span data-stu-id="e80ab-126">Unlike a method definition, a local function definition cannot include the following elements:</span></span>

- <span data-ttu-id="e80ab-127">Modifikátor přístupu ke členu</span><span class="sxs-lookup"><span data-stu-id="e80ab-127">The member access modifier.</span></span> <span data-ttu-id="e80ab-128">Vzhledem k tomu, že jsou všechny místní funkce soukromé, včetně modifikátoru přístupu, jako je například klíčové slovo `private`, vygeneruje chybu kompilátoru CS0106, modifikátor Private není pro tuto položku platný.</span><span class="sxs-lookup"><span data-stu-id="e80ab-128">Because all local functions are private, including an access modifier, such as the `private` keyword, generates compiler error CS0106, "The modifier 'private' is not valid for this item."</span></span>
 
- <span data-ttu-id="e80ab-129">Klíčové slovo [static](../../language-reference/keywords/static.md) .</span><span class="sxs-lookup"><span data-stu-id="e80ab-129">The [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="e80ab-130">Zahrnutí klíčového slova `static` generuje chybu kompilátoru CS0106, modifikátor "static" není pro tuto položku platný. "</span><span class="sxs-lookup"><span data-stu-id="e80ab-130">Including the `static` keyword generates compiler error CS0106, "The modifier 'static' is not valid for this item."</span></span>

<span data-ttu-id="e80ab-131">Kromě toho nelze atributy použít pro místní funkci nebo její parametry a parametry typu.</span><span class="sxs-lookup"><span data-stu-id="e80ab-131">In addition, attributes can't be applied to the local function or to its parameters and type parameters.</span></span> 
 
<span data-ttu-id="e80ab-132">Následující příklad definuje místní funkci s názvem `AppendPathSeparator`, která je soukromá pro metodu s názvem `GetText`:</span><span class="sxs-lookup"><span data-stu-id="e80ab-132">The following example defines a local function named `AppendPathSeparator` that is private to a method named `GetText`:</span></span>
   
[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a><span data-ttu-id="e80ab-133">Místní funkce a výjimky</span><span class="sxs-lookup"><span data-stu-id="e80ab-133">Local functions and exceptions</span></span>

<span data-ttu-id="e80ab-134">Jednou z užitečných funkcí lokálních funkcí je to, že může dojít k okamžitému povrchování výjimek.</span><span class="sxs-lookup"><span data-stu-id="e80ab-134">One of the useful features of local functions is that they can allow exceptions to surface immediately.</span></span> <span data-ttu-id="e80ab-135">U iterátorů metod jsou výjimky vyhodnoceny pouze v případě, že je vyhodnocena vrácená sekvence, a ne při načtení iterátoru.</span><span class="sxs-lookup"><span data-stu-id="e80ab-135">For method iterators, exceptions are surfaced only when the returned sequence is enumerated, and not when the iterator is retrieved.</span></span> <span data-ttu-id="e80ab-136">Pro asynchronní metody jsou při očekávaných úlohách pozorovány jakékoli výjimky vyvolané v asynchronní metodě.</span><span class="sxs-lookup"><span data-stu-id="e80ab-136">For async methods, any exceptions thrown in an async method are observed when the returned task is awaited.</span></span> 

<span data-ttu-id="e80ab-137">Následující příklad definuje metodu `OddSequence`, která vytváří výčet lichých čísel mezi zadaným rozsahem.</span><span class="sxs-lookup"><span data-stu-id="e80ab-137">The following example defines an `OddSequence` method that enumerates odd numbers between a specified range.</span></span> <span data-ttu-id="e80ab-138">Vzhledem k tomu, že předává číslo větší než 100 metodě čítače `OddSequence`, vyvolá metoda <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="e80ab-138">Because it passes a number greater than 100 to the `OddSequence` enumerator method, the method throws an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="e80ab-139">Jak výstup z příkladu ukazuje, plochy výjimky pouze při iteraci čísel, a ne při načtení čítače výčtu.</span><span class="sxs-lookup"><span data-stu-id="e80ab-139">As the output from the example shows, the exception surfaces only when you iterate the numbers, and not when you retrieve the enumerator.</span></span>

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

<span data-ttu-id="e80ab-140">Místo toho můžete vyvolat výjimku při provádění ověřování a před načtením iterátoru vrácením iterátoru z místní funkce, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="e80ab-140">Instead, you can throw an exception when performing validation and before retrieving the iterator by returning the iterator from a local function, as the following example shows.</span></span>

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

<span data-ttu-id="e80ab-141">Místní funkce lze použít podobným způsobem pro zpracování výjimek mimo asynchronní operaci.</span><span class="sxs-lookup"><span data-stu-id="e80ab-141">Local functions can be used in a similar way to handle exceptions outside of the asynchronous operation.</span></span> <span data-ttu-id="e80ab-142">Výjimky vyvolané v asynchronní metodě obvykle vyžadují, abyste prozkoumali vnitřní výjimky <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="e80ab-142">Ordinarily, exceptions thrown in async method require that you examine the inner exceptions of an <xref:System.AggregateException>.</span></span> <span data-ttu-id="e80ab-143">Místní funkce umožňují vašemu kódu selhání rychle a umožňují, aby vaše výjimka byla vyvolána a byla sledována synchronně.</span><span class="sxs-lookup"><span data-stu-id="e80ab-143">Local functions allow your code to fail fast and allow your exception to be both thrown and observed synchronously.</span></span>

<span data-ttu-id="e80ab-144">Následující příklad používá asynchronní metodu s názvem `GetMultipleAsync` k pozastavení po zadaný počet sekund a vrátí hodnotu, která je náhodnou násobek tohoto počtu sekund.</span><span class="sxs-lookup"><span data-stu-id="e80ab-144">The following example uses an asynchronous method named `GetMultipleAsync` to pause for a specified number of seconds and return a value that is a random multiple of that number of seconds.</span></span> <span data-ttu-id="e80ab-145">Maximální zpoždění je 5 sekund; <xref:System.ArgumentOutOfRangeException> výsledků, pokud je hodnota větší než 5.</span><span class="sxs-lookup"><span data-stu-id="e80ab-145">The maximum delay is 5 seconds; an <xref:System.ArgumentOutOfRangeException> results if the value is greater than 5.</span></span> <span data-ttu-id="e80ab-146">Jak ukazuje následující příklad, výjimka, která je vyvolána, když je předána hodnota 6 do metody `GetMultipleAsync` je zabalena do <xref:System.AggregateException> poté, co metoda `GetMultipleAsync` zahájí provádění.</span><span class="sxs-lookup"><span data-stu-id="e80ab-146">As the following example shows, the exception that is thrown when a value of 6 is passed to the `GetMultipleAsync` method is wrapped in an <xref:System.AggregateException> after the `GetMultipleAsync` method begins execution.</span></span>

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

<span data-ttu-id="e80ab-147">Stejně jako u metody iterátoru můžeme kód z tohoto příkladu Refaktorovat, aby bylo ověřování provedeno před voláním asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="e80ab-147">As we did with the method iterator, we can refactor the code from this example to perform the validation before calling the asynchronous method.</span></span> <span data-ttu-id="e80ab-148">Jak ukazuje výstup z následujícího příkladu, <xref:System.ArgumentOutOfRangeException> není zabalen do <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="e80ab-148">As the output from the following example shows, the <xref:System.ArgumentOutOfRangeException> is not wrapped in a <xref:System.AggregateException>.</span></span>

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a><span data-ttu-id="e80ab-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e80ab-149">See also</span></span>

- [<span data-ttu-id="e80ab-150">Metody</span><span class="sxs-lookup"><span data-stu-id="e80ab-150">Methods</span></span>](methods.md)
