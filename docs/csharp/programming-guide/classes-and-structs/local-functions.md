---
title: Lokální funkce (C# Průvodce programováním)
ms.date: 06/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- local functions [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac18aa57f443f28f55779ff9c92a5349b9b39fd7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="local-functions-c-programming-guide"></a><span data-ttu-id="14226-102">Lokální funkce (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="14226-102">Local functions (C# Programming Guide)</span></span>

<span data-ttu-id="14226-103">Od verze jazyka C# 7.0, C# podporuje *lokální funkce*.</span><span class="sxs-lookup"><span data-stu-id="14226-103">Starting with C# 7.0, C# supports *local functions*.</span></span> <span data-ttu-id="14226-104">Lokální funkce jsou privátní metody typu, které jsou vnořené v jiného člena.</span><span class="sxs-lookup"><span data-stu-id="14226-104">Local functions are private methods of a type that are nested in another member.</span></span> <span data-ttu-id="14226-105">Může být volána pouze z jejich obsahující člen.</span><span class="sxs-lookup"><span data-stu-id="14226-105">They can only be called from their containing member.</span></span> <span data-ttu-id="14226-106">Lokální funkce můžete v deklarována a volat z:</span><span class="sxs-lookup"><span data-stu-id="14226-106">Local functions can be declared in and called from:</span></span>

- <span data-ttu-id="14226-107">Metody, hlavně iterator metody a asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="14226-107">Methods, especially iterator methods and async methods</span></span>
- <span data-ttu-id="14226-108">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="14226-108">Constructors</span></span>
- <span data-ttu-id="14226-109">Přístupové objekty vlastnosti</span><span class="sxs-lookup"><span data-stu-id="14226-109">Property accessors</span></span>
- <span data-ttu-id="14226-110">Přístupové objekty událostí</span><span class="sxs-lookup"><span data-stu-id="14226-110">Event accessors</span></span>
- <span data-ttu-id="14226-111">Anonymní metody</span><span class="sxs-lookup"><span data-stu-id="14226-111">Anonymous methods</span></span>
- <span data-ttu-id="14226-112">Lambda – výrazy</span><span class="sxs-lookup"><span data-stu-id="14226-112">Lambda expressions</span></span>
- <span data-ttu-id="14226-113">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="14226-113">Finalizers</span></span>
- <span data-ttu-id="14226-114">Další místní funkce</span><span class="sxs-lookup"><span data-stu-id="14226-114">Other local functions</span></span>

<span data-ttu-id="14226-115">Lokální funkce však nelze deklarovat uvnitř výrazu vozidlo člen.</span><span class="sxs-lookup"><span data-stu-id="14226-115">However, local functions can't be declared inside an expression-bodied member.</span></span>

> [!NOTE]
> <span data-ttu-id="14226-116">V některých případech můžete implementovat funkce podporovány také místní funkcí výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="14226-116">In some cases, you can use a lambda expression to implement functionality also supported by a local function.</span></span> <span data-ttu-id="14226-117">Porovnání najdete v tématu [lokální funkce ve srovnání s výrazy Lambda](../../local-functions-vs-lambdas.md).</span><span class="sxs-lookup"><span data-stu-id="14226-117">For a comparison, see [Local functions compared to Lambda expressions](../../local-functions-vs-lambdas.md).</span></span>

<span data-ttu-id="14226-118">Lokální funkce byl záměr vymazat kódu.</span><span class="sxs-lookup"><span data-stu-id="14226-118">Local functions make the intent of your code clear.</span></span> <span data-ttu-id="14226-119">Každý, kdo čtení kódu můžete uvidíte, že metoda není s výjimkou volatelné obsahující metoda.</span><span class="sxs-lookup"><span data-stu-id="14226-119">Anyone reading you code can see that the method is not callable except by the containing method.</span></span> <span data-ttu-id="14226-120">Pro týmové projekty, budou také znemožňují pro jiné vývojáře omylem zavolat metodu přímo z jinde v dané třídě nebo stuct.</span><span class="sxs-lookup"><span data-stu-id="14226-120">For team projects, they also make it impossible for another developer to mistakenly call the method directly from elsewhere in the class or stuct.</span></span>
 
## <a name="local-function-syntax"></a><span data-ttu-id="14226-121">Syntaxe místní – funkce</span><span class="sxs-lookup"><span data-stu-id="14226-121">Local function syntax</span></span>

<span data-ttu-id="14226-122">Místní funkce je definován jako vnořené metoda uvnitř obsahující člena.</span><span class="sxs-lookup"><span data-stu-id="14226-122">A local function is defined as a nested method inside a containing member.</span></span> <span data-ttu-id="14226-123">Její definice obsahuje následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="14226-123">Its definition has the following syntax:</span></span>

```txt
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

<span data-ttu-id="14226-124">Můžete použít místní funkce [asynchronní](../../language-reference/keywords/async.md) a [unsafe](../../language-reference/keywords/unsafe.md) modifikátory.</span><span class="sxs-lookup"><span data-stu-id="14226-124">Local functions can use the [async](../../language-reference/keywords/async.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span> 

<span data-ttu-id="14226-125">Všimněte si, že všechny místní proměnné, které jsou definovány v obsahující členovi, včetně jeho parametry metody jsou dostupné v místní funkce.</span><span class="sxs-lookup"><span data-stu-id="14226-125">Note that all local variables that are defined in the containing member, including its method parameters, are accessible in the local function.</span></span> 

<span data-ttu-id="14226-126">Na rozdíl od metoda definice definice místní funkce nesmí obsahovat následující prvky:</span><span class="sxs-lookup"><span data-stu-id="14226-126">Unlike a method definition, a local function definition cannot include the following elements:</span></span>

- <span data-ttu-id="14226-127">Modifikátor přístupu členů.</span><span class="sxs-lookup"><span data-stu-id="14226-127">The member access modifier.</span></span> <span data-ttu-id="14226-128">Protože všechny místní funkce privátní, včetně – modifikátor přístupu, jako například `private` – klíčové slovo, vygeneruje Chyba kompilátoru CS0106, "modifikátor 'privátní' není platný pro tuto položku."</span><span class="sxs-lookup"><span data-stu-id="14226-128">Because all local functions are private, including an access modifier, such as the `private` keyword, generates compiler error CS0106, "The modifier 'private' is not valid for this item."</span></span>
 
- <span data-ttu-id="14226-129">[Statické](../../language-reference/keywords/static.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="14226-129">The [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="14226-130">Včetně `static` – klíčové slovo vygeneruje Chyba kompilátoru CS0106, "modifikátor"statická"není platný pro tuto položku."</span><span class="sxs-lookup"><span data-stu-id="14226-130">Including the `static` keyword generates compiler error CS0106, "The modifier 'static' is not valid for this item."</span></span>

<span data-ttu-id="14226-131">Kromě toho atributy nelze použít k funkci místní nebo jeho parametry a parametry typu.</span><span class="sxs-lookup"><span data-stu-id="14226-131">In addition, attributes can't be applied to the local function or to its parameters and type parameters.</span></span> 
 
<span data-ttu-id="14226-132">V následujícím příkladu definuje místní funkce s názvem `AppendPathSeparator` , je pro metodu s názvem soukromý `GetText`:</span><span class="sxs-lookup"><span data-stu-id="14226-132">The following example defines a local function named `AppendPathSeparator` that is private to a method named `GetText`:</span></span>
   
[!code-csharp[LocalFunctionExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a><span data-ttu-id="14226-133">Místní funkce a výjimky</span><span class="sxs-lookup"><span data-stu-id="14226-133">Local functions and exceptions</span></span>

<span data-ttu-id="14226-134">Jedna z funkcí užitečné místní funkcí je, že umožňují výjimky prezentovat okamžitě.</span><span class="sxs-lookup"><span data-stu-id="14226-134">One of the useful features of local functions is that they can allow exceptions to surface immediately.</span></span> <span data-ttu-id="14226-135">Pro metodu iterátory výjimky jsou prezentované jenom v případě, že je výčet vrácený pořadí, a ne v případě, že se načítají iteraci.</span><span class="sxs-lookup"><span data-stu-id="14226-135">For method iterators, exceptions are surfaced only when the returned sequence is enumerated, and not when the iterator is retrieved.</span></span> <span data-ttu-id="14226-136">Pro asynchronní metody je možné vysledovat všechny výjimky vzniklé v asynchronní metody při vrácený úloh je očekáváno.</span><span class="sxs-lookup"><span data-stu-id="14226-136">For async methods, any exceptions thrown in an async method are observed when the returned task is awaited.</span></span> 

<span data-ttu-id="14226-137">V následujícím příkladu definuje `OddSequence` metoda, která vytvoří výčet liché číslo mezi zadaném rozsahu.</span><span class="sxs-lookup"><span data-stu-id="14226-137">The following example defines an `OddSequence` method that enumerates odd numbers between a specified range.</span></span> <span data-ttu-id="14226-138">Protože předává číslo větší než 100, která `OddSequence` enumerátor metoda vyvolá metoda <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="14226-138">Because it passes a number greater than 100 to the `OddSequence` enumerator method, the method throws an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="14226-139">Jak ukazuje výstup z příkladu, výjimka zobrazí jenom v případě, že iterace čísla, a ne už při načtení enumerátoru.</span><span class="sxs-lookup"><span data-stu-id="14226-139">As the output from the example shows, the exception surfaces only when you iterate the numbers, and not when you retrieve the enumerator.</span></span>

[!code-csharp[LocalFunctionIterator1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

<span data-ttu-id="14226-140">Místo toho můžete při provádění ověřování může vyvolat výjimku a před načtením iteraci vrácením iteraci z místní funkce, jako následující příklad ukazuje.</span><span class="sxs-lookup"><span data-stu-id="14226-140">Instead, you can throw an exception when performing validation and before retrieving the iterator by returning the iterator from a local function, as the following example shows.</span></span>

[!code-csharp[LocalFunctionIterator2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

<span data-ttu-id="14226-141">Místní funkcí lze podobným způsobem zpracování výjimek mimo asynchronní operaci.</span><span class="sxs-lookup"><span data-stu-id="14226-141">Local functions can be used in a similar way to handle exceptions outside of the asynchronous operation.</span></span> <span data-ttu-id="14226-142">Normálně, výjimky vzniklé v asynchronní metody vyžadují, že byste zkontrolovat vnitřní výjimky z <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="14226-142">Ordinarily, exceptions thrown in async method require that you examine the inner exceptions of an <xref:System.AggregateException>.</span></span> <span data-ttu-id="14226-143">Lokální funkce povolit kódu služeb při selhání rychle a povolit vaší výjimka být vyvolána i zjištěnými synchronně.</span><span class="sxs-lookup"><span data-stu-id="14226-143">Local functions allow your code to fail fast and allow your exception to be both thrown and observed synchronously.</span></span>

<span data-ttu-id="14226-144">Následující příklad používá asynchronní metodu s názvem `GetMultipleAsync` pozastavení pro zadaný počet sekund, a vrátí hodnotu, která je náhodný násobkem tento počet sekund.</span><span class="sxs-lookup"><span data-stu-id="14226-144">The following example uses an asynchronous method named `GetMultipleAsync` to pause for a specified number of seconds and return a value that is a random multiple of that number of seconds.</span></span> <span data-ttu-id="14226-145">Maximální zpoždění je 5 sekund; <xref:System.ArgumentOutOfRangeException> výsledků, pokud je hodnota větší než 5.</span><span class="sxs-lookup"><span data-stu-id="14226-145">The maximum delay is 5 seconds; an <xref:System.ArgumentOutOfRangeException> results if the value is greater than 5.</span></span> <span data-ttu-id="14226-146">Jak ukazuje následující příklad, výjimka, která se vyvolá, když hodnota 6 předána `GetMultipleAsync` metoda je uzavřen do <xref:System.AggregateException> po `GetMultipleAsync` metoda zahájí spuštění.</span><span class="sxs-lookup"><span data-stu-id="14226-146">As the following example shows, the exception that is thrown when a value of 6 is passed to the `GetMultipleAsync` method is wrapped in an <xref:System.AggregateException> after the `GetMultipleAsync` method begins execution.</span></span>

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

<span data-ttu-id="14226-147">Jako jsme to udělali s iterator metoda, jsme Refaktorovat kód z tohoto příkladu k ověření před voláním asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="14226-147">As we did with the method iterator, we can refactor the code from this example to perform the validation before calling the asynchronous method.</span></span> <span data-ttu-id="14226-148">Jako výstup z následující příklad ukazuje <xref:System.ArgumentOutOfRangeException> není uzavřen do < x:System.AggregateException >.</span><span class="sxs-lookup"><span data-stu-id="14226-148">As the output from the following example shows, the <xref:System.ArgumentOutOfRangeException> is not wrapped in a <x:System.AggregateException>.</span></span>

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a><span data-ttu-id="14226-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="14226-149">See also</span></span>
[<span data-ttu-id="14226-150">Metody</span><span class="sxs-lookup"><span data-stu-id="14226-150">Methods</span></span>](methods.md)
