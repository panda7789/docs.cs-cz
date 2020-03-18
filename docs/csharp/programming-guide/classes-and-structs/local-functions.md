---
title: Místní funkce – programovací příručka Jazyka C#
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: b6924b8981af5115a474eeb6b2e5376dd1b17ff5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170232"
---
# <a name="local-functions-c-programming-guide"></a><span data-ttu-id="027cd-102">Místní funkce (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="027cd-102">Local functions (C# Programming Guide)</span></span>

<span data-ttu-id="027cd-103">Počínaje c# 7.0, C# podporuje *místní funkce*.</span><span class="sxs-lookup"><span data-stu-id="027cd-103">Starting with C# 7.0, C# supports *local functions*.</span></span> <span data-ttu-id="027cd-104">Místní funkce jsou soukromé metody typu, které jsou vnořeny v jiném členu.</span><span class="sxs-lookup"><span data-stu-id="027cd-104">Local functions are private methods of a type that are nested in another member.</span></span> <span data-ttu-id="027cd-105">Mohou být volány pouze z jejich obsahující člen.</span><span class="sxs-lookup"><span data-stu-id="027cd-105">They can only be called from their containing member.</span></span> <span data-ttu-id="027cd-106">Místní funkce lze deklarovat a volat z:</span><span class="sxs-lookup"><span data-stu-id="027cd-106">Local functions can be declared in and called from:</span></span>

- <span data-ttu-id="027cd-107">Metody, zejména metody iterátoru a asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="027cd-107">Methods, especially iterator methods and async methods</span></span>
- <span data-ttu-id="027cd-108">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="027cd-108">Constructors</span></span>
- <span data-ttu-id="027cd-109">Přístupové objekty vlastností</span><span class="sxs-lookup"><span data-stu-id="027cd-109">Property accessors</span></span>
- <span data-ttu-id="027cd-110">Přistupující přístupové akce</span><span class="sxs-lookup"><span data-stu-id="027cd-110">Event accessors</span></span>
- <span data-ttu-id="027cd-111">Anonymní metody</span><span class="sxs-lookup"><span data-stu-id="027cd-111">Anonymous methods</span></span>
- <span data-ttu-id="027cd-112">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="027cd-112">Lambda expressions</span></span>
- <span data-ttu-id="027cd-113">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="027cd-113">Finalizers</span></span>
- <span data-ttu-id="027cd-114">Další místní funkce</span><span class="sxs-lookup"><span data-stu-id="027cd-114">Other local functions</span></span>

<span data-ttu-id="027cd-115">Místní funkce však nelze deklarovat uvnitř člena s výrazem.</span><span class="sxs-lookup"><span data-stu-id="027cd-115">However, local functions can't be declared inside an expression-bodied member.</span></span>

> [!NOTE]
> <span data-ttu-id="027cd-116">V některých případech můžete použít výraz lambda k implementaci funkcí podporovaných také místní funkcí.</span><span class="sxs-lookup"><span data-stu-id="027cd-116">In some cases, you can use a lambda expression to implement functionality also supported by a local function.</span></span> <span data-ttu-id="027cd-117">Porovnání naleznete v tématu [Místní funkce ve srovnání s výrazy Lambda](../../local-functions-vs-lambdas.md).</span><span class="sxs-lookup"><span data-stu-id="027cd-117">For a comparison, see [Local functions compared to Lambda expressions](../../local-functions-vs-lambdas.md).</span></span>

<span data-ttu-id="027cd-118">Místní funkce, aby záměr kódu jasné.</span><span class="sxs-lookup"><span data-stu-id="027cd-118">Local functions make the intent of your code clear.</span></span> <span data-ttu-id="027cd-119">Každý, kdo čte váš kód, vidí, že metoda není volatelná s výjimkou metody obsahující.</span><span class="sxs-lookup"><span data-stu-id="027cd-119">Anyone reading your code can see that the method is not callable except by the containing method.</span></span> <span data-ttu-id="027cd-120">Pro týmové projekty také znemožňují jinému vývojáři chybně volat metodu přímo z jiných míst ve třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="027cd-120">For team projects, they also make it impossible for another developer to mistakenly call the method directly from elsewhere in the class or struct.</span></span>

## <a name="local-function-syntax"></a><span data-ttu-id="027cd-121">Syntaxe místní funkce</span><span class="sxs-lookup"><span data-stu-id="027cd-121">Local function syntax</span></span>

<span data-ttu-id="027cd-122">Místní funkce je definována jako vnořená metoda uvnitř obsahujícího člena.</span><span class="sxs-lookup"><span data-stu-id="027cd-122">A local function is defined as a nested method inside a containing member.</span></span> <span data-ttu-id="027cd-123">Jeho definice má následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="027cd-123">Its definition has the following syntax:</span></span>

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

<span data-ttu-id="027cd-124">Místní funkce mohou používat [asynchronní](../../language-reference/keywords/async.md) a [nebezpečné](../../language-reference/keywords/unsafe.md) modifikátory.</span><span class="sxs-lookup"><span data-stu-id="027cd-124">Local functions can use the [async](../../language-reference/keywords/async.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span>

<span data-ttu-id="027cd-125">Všimněte si, že všechny místní proměnné, které jsou definovány v obsahující člen, včetně jeho parametry metody, jsou přístupné v místní funkci.</span><span class="sxs-lookup"><span data-stu-id="027cd-125">Note that all local variables that are defined in the containing member, including its method parameters, are accessible in the local function.</span></span>

<span data-ttu-id="027cd-126">Na rozdíl od definice metody nemůže definice místní funkce obsahovat modifikátor přístupu člena.</span><span class="sxs-lookup"><span data-stu-id="027cd-126">Unlike a method definition, a local function definition cannot include the member access modifier.</span></span> <span data-ttu-id="027cd-127">Vzhledem k tomu, že všechny místní funkce `private` jsou soukromé, včetně modifikátoru přístupu, například klíčové slovo, generuje chybu kompilátoru CS0106, "Modifikátor 'private' není platný pro tuto položku.</span><span class="sxs-lookup"><span data-stu-id="027cd-127">Because all local functions are private, including an access modifier, such as the `private` keyword, generates compiler error CS0106, "The modifier 'private' is not valid for this item."</span></span>

> [!NOTE]
> <span data-ttu-id="027cd-128">Před C# 8.0 místní funkce `static` nemohou obsahovat modifikátor.</span><span class="sxs-lookup"><span data-stu-id="027cd-128">Prior to C# 8.0, local functions cannot include the `static` modifier.</span></span> <span data-ttu-id="027cd-129">Včetně `static` klíčového slova generuje chybu kompilátoru CS0106, "Modifikátor 'statické' není platný pro tuto položku."</span><span class="sxs-lookup"><span data-stu-id="027cd-129">Including the `static` keyword generates compiler error CS0106, "The modifier 'static' is not valid for this item."</span></span>

<span data-ttu-id="027cd-130">Kromě toho atributy nelze použít na místní funkci nebo na její parametry a parametry typu.</span><span class="sxs-lookup"><span data-stu-id="027cd-130">In addition, attributes can't be applied to the local function or to its parameters and type parameters.</span></span>

<span data-ttu-id="027cd-131">Následující příklad definuje místní funkci `AppendPathSeparator` s názvem, která `GetText`je soukromá pro metodu s názvem :</span><span class="sxs-lookup"><span data-stu-id="027cd-131">The following example defines a local function named `AppendPathSeparator` that is private to a method named `GetText`:</span></span>

[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  

## <a name="local-functions-and-exceptions"></a><span data-ttu-id="027cd-132">Místní funkce a výjimky</span><span class="sxs-lookup"><span data-stu-id="027cd-132">Local functions and exceptions</span></span>

<span data-ttu-id="027cd-133">Jednou z užitečných funkcí místních funkcí je, že mohou povolit výjimky na povrch okamžitě.</span><span class="sxs-lookup"><span data-stu-id="027cd-133">One of the useful features of local functions is that they can allow exceptions to surface immediately.</span></span> <span data-ttu-id="027cd-134">Pro metodu iterátory výjimky jsou zobrazeny pouze v případě, že vrácená sekvence je výčtu a ne při iterátoru je načten.</span><span class="sxs-lookup"><span data-stu-id="027cd-134">For method iterators, exceptions are surfaced only when the returned sequence is enumerated, and not when the iterator is retrieved.</span></span> <span data-ttu-id="027cd-135">Pro asynchronní metody jsou pozorovány všechny výjimky vyzdvižené v asynchronní metodě, když je očekávaná vrácená úloha.</span><span class="sxs-lookup"><span data-stu-id="027cd-135">For async methods, any exceptions thrown in an async method are observed when the returned task is awaited.</span></span>

<span data-ttu-id="027cd-136">Následující příklad definuje `OddSequence` metodu, která vytvoří vyjmenovává lichá čísla mezi zadaným rozsahem.</span><span class="sxs-lookup"><span data-stu-id="027cd-136">The following example defines an `OddSequence` method that enumerates odd numbers between a specified range.</span></span> <span data-ttu-id="027cd-137">Protože předá číslo větší než 100 do metody `OddSequence` čítače <xref:System.ArgumentOutOfRangeException>výčtu, metoda vyvolá .</span><span class="sxs-lookup"><span data-stu-id="027cd-137">Because it passes a number greater than 100 to the `OddSequence` enumerator method, the method throws an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="027cd-138">Jak ukazuje výstup z příkladu, výjimka se zobrazí pouze při iterát čísla a ne při načtení čítače výčtu.</span><span class="sxs-lookup"><span data-stu-id="027cd-138">As the output from the example shows, the exception surfaces only when you iterate the numbers, and not when you retrieve the enumerator.</span></span>

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)]

<span data-ttu-id="027cd-139">Místo toho můžete vyvolat výjimku při provádění ověření a před načtením iterátoru vrácením iterátoru z místní funkce, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="027cd-139">Instead, you can throw an exception when performing validation and before retrieving the iterator by returning the iterator from a local function, as the following example shows.</span></span>

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

<span data-ttu-id="027cd-140">Místní funkce lze použít podobným způsobem pro zpracování výjimek mimo asynchronní operaci.</span><span class="sxs-lookup"><span data-stu-id="027cd-140">Local functions can be used in a similar way to handle exceptions outside of the asynchronous operation.</span></span> <span data-ttu-id="027cd-141">Obvykle výjimky vyzývané v asynchronní metodě <xref:System.AggregateException>vyžadují, abyste prozkoumali vnitřní výjimky .</span><span class="sxs-lookup"><span data-stu-id="027cd-141">Ordinarily, exceptions thrown in async method require that you examine the inner exceptions of an <xref:System.AggregateException>.</span></span> <span data-ttu-id="027cd-142">Místní funkce umožňují váš kód selhat rychle a umožňují výjimku, které mají být vyvolány a sledovány synchronně.</span><span class="sxs-lookup"><span data-stu-id="027cd-142">Local functions allow your code to fail fast and allow your exception to be both thrown and observed synchronously.</span></span>

<span data-ttu-id="027cd-143">Následující příklad používá asynchronní metodu s názvem `GetMultipleAsync` pozastavit po zadaný počet sekund a vrátit hodnotu, která je náhodný násobek tohoto počtu sekund.</span><span class="sxs-lookup"><span data-stu-id="027cd-143">The following example uses an asynchronous method named `GetMultipleAsync` to pause for a specified number of seconds and return a value that is a random multiple of that number of seconds.</span></span> <span data-ttu-id="027cd-144">Maximální zpoždění je 5 sekund; výsledky, <xref:System.ArgumentOutOfRangeException> pokud je hodnota větší než 5.</span><span class="sxs-lookup"><span data-stu-id="027cd-144">The maximum delay is 5 seconds; an <xref:System.ArgumentOutOfRangeException> results if the value is greater than 5.</span></span> <span data-ttu-id="027cd-145">Jak ukazuje následující příklad, výjimka, která je vyvolána při `GetMultipleAsync` předání hodnoty 6 <xref:System.AggregateException> metodě, je zabalena v po `GetMultipleAsync` zahájení spuštění metody.</span><span class="sxs-lookup"><span data-stu-id="027cd-145">As the following example shows, the exception that is thrown when a value of 6 is passed to the `GetMultipleAsync` method is wrapped in an <xref:System.AggregateException> after the `GetMultipleAsync` method begins execution.</span></span>

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)]

<span data-ttu-id="027cd-146">Stejně jako jsme to udělali s metodou iterátoru, můžeme refaktorovat kód z tohoto příkladu provést ověření před voláním asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="027cd-146">As we did with the method iterator, we can refactor the code from this example to perform the validation before calling the asynchronous method.</span></span> <span data-ttu-id="027cd-147">Jak ukazuje výstup z následujícího <xref:System.ArgumentOutOfRangeException> příkladu, není <xref:System.AggregateException>zabalen v .</span><span class="sxs-lookup"><span data-stu-id="027cd-147">As the output from the following example shows, the <xref:System.ArgumentOutOfRangeException> is not wrapped in a <xref:System.AggregateException>.</span></span>

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)]

## <a name="see-also"></a><span data-ttu-id="027cd-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="027cd-148">See also</span></span>

- [<span data-ttu-id="027cd-149">Metody</span><span class="sxs-lookup"><span data-stu-id="027cd-149">Methods</span></span>](methods.md)
