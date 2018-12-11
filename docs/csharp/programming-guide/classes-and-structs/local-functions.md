---
title: Lokální funkce - C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50dd7fbb35358ad153cfdbec62a2922fdc28775c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240226"
---
# <a name="local-functions-c-programming-guide"></a><span data-ttu-id="67f47-102">Lokální funkce (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="67f47-102">Local functions (C# Programming Guide)</span></span>

<span data-ttu-id="67f47-103">Od verze C# 7.0, C# podporuje *lokální funkce*.</span><span class="sxs-lookup"><span data-stu-id="67f47-103">Starting with C# 7.0, C# supports *local functions*.</span></span> <span data-ttu-id="67f47-104">Lokální funkce jsou privátní metody typu, které jsou vnořeny v jiném členu.</span><span class="sxs-lookup"><span data-stu-id="67f47-104">Local functions are private methods of a type that are nested in another member.</span></span> <span data-ttu-id="67f47-105">Může být volána pouze od jejich nadřazeného člena.</span><span class="sxs-lookup"><span data-stu-id="67f47-105">They can only be called from their containing member.</span></span> <span data-ttu-id="67f47-106">Lokální funkce může deklarovat v a volat z:</span><span class="sxs-lookup"><span data-stu-id="67f47-106">Local functions can be declared in and called from:</span></span>

- <span data-ttu-id="67f47-107">Metody, hlavně iterátory a asynchronní metody</span><span class="sxs-lookup"><span data-stu-id="67f47-107">Methods, especially iterator methods and async methods</span></span>
- <span data-ttu-id="67f47-108">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="67f47-108">Constructors</span></span>
- <span data-ttu-id="67f47-109">Přistupující objekty vlastnosti</span><span class="sxs-lookup"><span data-stu-id="67f47-109">Property accessors</span></span>
- <span data-ttu-id="67f47-110">Přístupové objekty událostí</span><span class="sxs-lookup"><span data-stu-id="67f47-110">Event accessors</span></span>
- <span data-ttu-id="67f47-111">Anonymní metody</span><span class="sxs-lookup"><span data-stu-id="67f47-111">Anonymous methods</span></span>
- <span data-ttu-id="67f47-112">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="67f47-112">Lambda expressions</span></span>
- <span data-ttu-id="67f47-113">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="67f47-113">Finalizers</span></span>
- <span data-ttu-id="67f47-114">Jiné místní funkce</span><span class="sxs-lookup"><span data-stu-id="67f47-114">Other local functions</span></span>

<span data-ttu-id="67f47-115">Lokální funkce však nemohou být deklarovány uvnitř na člena s výrazem v těle.</span><span class="sxs-lookup"><span data-stu-id="67f47-115">However, local functions can't be declared inside an expression-bodied member.</span></span>

> [!NOTE]
> <span data-ttu-id="67f47-116">V některých případech slouží k implementaci funkcionality také podporuje místní funkce výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="67f47-116">In some cases, you can use a lambda expression to implement functionality also supported by a local function.</span></span> <span data-ttu-id="67f47-117">Porovnání najdete v tématu [lokální funkce ve srovnání s Lambda výrazy](../../local-functions-vs-lambdas.md).</span><span class="sxs-lookup"><span data-stu-id="67f47-117">For a comparison, see [Local functions compared to Lambda expressions](../../local-functions-vs-lambdas.md).</span></span>

<span data-ttu-id="67f47-118">Lokální funkce zkontrolujte záměru kódu jasný.</span><span class="sxs-lookup"><span data-stu-id="67f47-118">Local functions make the intent of your code clear.</span></span> <span data-ttu-id="67f47-119">Každému, kdo čte kód můžete vidět, metoda se nedá volat s výjimkou obsahující metodou.</span><span class="sxs-lookup"><span data-stu-id="67f47-119">Anyone reading you code can see that the method is not callable except by the containing method.</span></span> <span data-ttu-id="67f47-120">Pro týmové projekty, jsou také znemožnit pro jiné vývojáře omylem volat metodu přímo z jinde v dané třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="67f47-120">For team projects, they also make it impossible for another developer to mistakenly call the method directly from elsewhere in the class or struct.</span></span>
 
## <a name="local-function-syntax"></a><span data-ttu-id="67f47-121">Syntaxe místní funkce</span><span class="sxs-lookup"><span data-stu-id="67f47-121">Local function syntax</span></span>

<span data-ttu-id="67f47-122">Lokální funkce je definován jako metodu vnořené uvnitř nadřazeného člena.</span><span class="sxs-lookup"><span data-stu-id="67f47-122">A local function is defined as a nested method inside a containing member.</span></span> <span data-ttu-id="67f47-123">Jeho definice má následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="67f47-123">Its definition has the following syntax:</span></span>

```txt
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

<span data-ttu-id="67f47-124">Lokální funkce můžete použít [asynchronní](../../language-reference/keywords/async.md) a [nebezpečné](../../language-reference/keywords/unsafe.md) modifikátory.</span><span class="sxs-lookup"><span data-stu-id="67f47-124">Local functions can use the [async](../../language-reference/keywords/async.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span> 

<span data-ttu-id="67f47-125">Všimněte si, že jsou k dispozici v lokální funkce všech místních proměnných, které jsou definovány v obsahující členu, včetně jeho parametry metody.</span><span class="sxs-lookup"><span data-stu-id="67f47-125">Note that all local variables that are defined in the containing member, including its method parameters, are accessible in the local function.</span></span> 

<span data-ttu-id="67f47-126">Na rozdíl od definice metody definice lokální funkce nesmí obsahovat následující prvky:</span><span class="sxs-lookup"><span data-stu-id="67f47-126">Unlike a method definition, a local function definition cannot include the following elements:</span></span>

- <span data-ttu-id="67f47-127">Členský modifikátor přístupu.</span><span class="sxs-lookup"><span data-stu-id="67f47-127">The member access modifier.</span></span> <span data-ttu-id="67f47-128">Protože jsou všechny lokální funkce privátní, včetně modifikátor přístupu, jako `private` – klíčové slovo, vygeneruje Chyba kompilátoru CS0106 "modifikátor 'private' není platný pro tuto položku."</span><span class="sxs-lookup"><span data-stu-id="67f47-128">Because all local functions are private, including an access modifier, such as the `private` keyword, generates compiler error CS0106, "The modifier 'private' is not valid for this item."</span></span>
 
- <span data-ttu-id="67f47-129">[Statické](../../language-reference/keywords/static.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="67f47-129">The [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="67f47-130">Včetně `static` – klíčové slovo vygeneruje Chyba kompilátoru CS0106, "modifikátor 'static' není platný pro tuto položku."</span><span class="sxs-lookup"><span data-stu-id="67f47-130">Including the `static` keyword generates compiler error CS0106, "The modifier 'static' is not valid for this item."</span></span>

<span data-ttu-id="67f47-131">Kromě toho atributy nejde použít na místní funkci nebo na jeho parametry a parametry typu.</span><span class="sxs-lookup"><span data-stu-id="67f47-131">In addition, attributes can't be applied to the local function or to its parameters and type parameters.</span></span> 
 
<span data-ttu-id="67f47-132">Následující příklad definuje lokální funkce s názvem `AppendPathSeparator` , který je pro metodu s názvem soukromý `GetText`:</span><span class="sxs-lookup"><span data-stu-id="67f47-132">The following example defines a local function named `AppendPathSeparator` that is private to a method named `GetText`:</span></span>
   
[!code-csharp[LocalFunctionExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a><span data-ttu-id="67f47-133">Lokální funkce a výjimky</span><span class="sxs-lookup"><span data-stu-id="67f47-133">Local functions and exceptions</span></span>

<span data-ttu-id="67f47-134">Jedním z užitečných funkcí lokální funkce je, že umožňují výjimky k poskytování okamžitě.</span><span class="sxs-lookup"><span data-stu-id="67f47-134">One of the useful features of local functions is that they can allow exceptions to surface immediately.</span></span> <span data-ttu-id="67f47-135">U metody iterátorů výjimky zobrazují se jenom v případě, že vrácená sekvence je vypočten, a ne v případě, že se načte iterátor.</span><span class="sxs-lookup"><span data-stu-id="67f47-135">For method iterators, exceptions are surfaced only when the returned sequence is enumerated, and not when the iterator is retrieved.</span></span> <span data-ttu-id="67f47-136">Pro asynchronní metody jsou dodržovány zůstanou veškeré výjimky vyvolané v asynchronní metodě při očekávání vrácené úlohy.</span><span class="sxs-lookup"><span data-stu-id="67f47-136">For async methods, any exceptions thrown in an async method are observed when the returned task is awaited.</span></span> 

<span data-ttu-id="67f47-137">Následující příklad definuje `OddSequence` metodu, která vytvoří výčet lichá čísla zadaného rozsahu.</span><span class="sxs-lookup"><span data-stu-id="67f47-137">The following example defines an `OddSequence` method that enumerates odd numbers between a specified range.</span></span> <span data-ttu-id="67f47-138">Protože předá číslo větší než 100, aby se `OddSequence` – metoda výčtu, metoda vyvolá <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="67f47-138">Because it passes a number greater than 100 to the `OddSequence` enumerator method, the method throws an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="67f47-139">Jak výstup z příkladu ukazuje, vyvolá výjimku pouze v případě, že je iterace čísla, a ne už při načtení enumerátoru.</span><span class="sxs-lookup"><span data-stu-id="67f47-139">As the output from the example shows, the exception surfaces only when you iterate the numbers, and not when you retrieve the enumerator.</span></span>

[!code-csharp[LocalFunctionIterator1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

<span data-ttu-id="67f47-140">Místo toho může vyvolat výjimku při provádění ověření a před načtením iterátor tak, že vrací iterátor z místní funkce, jako následující příklad ukazuje.</span><span class="sxs-lookup"><span data-stu-id="67f47-140">Instead, you can throw an exception when performing validation and before retrieving the iterator by returning the iterator from a local function, as the following example shows.</span></span>

[!code-csharp[LocalFunctionIterator2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

<span data-ttu-id="67f47-141">Lokální funkce můžete použít podobným způsobem jako pro zpracování výjimek mimo asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="67f47-141">Local functions can be used in a similar way to handle exceptions outside of the asynchronous operation.</span></span> <span data-ttu-id="67f47-142">Obvykle vyžadují výjimky vyvolané v asynchronní metodě, že zkoumají vnitřní výjimky, které <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="67f47-142">Ordinarily, exceptions thrown in async method require that you examine the inner exceptions of an <xref:System.AggregateException>.</span></span> <span data-ttu-id="67f47-143">Lokální funkce umožňují váš kód k rychle vygenerovala chybu a povolit výjimky být vyvolána i zjištěnými synchronně.</span><span class="sxs-lookup"><span data-stu-id="67f47-143">Local functions allow your code to fail fast and allow your exception to be both thrown and observed synchronously.</span></span>

<span data-ttu-id="67f47-144">Následující příklad používá asynchronní metodu s názvem `GetMultipleAsync` pozastavení pro zadaný počet sekund a vrací hodnotu, která je náhodné násobek tento počet sekund.</span><span class="sxs-lookup"><span data-stu-id="67f47-144">The following example uses an asynchronous method named `GetMultipleAsync` to pause for a specified number of seconds and return a value that is a random multiple of that number of seconds.</span></span> <span data-ttu-id="67f47-145">Maximální zpoždění je 5 sekund. <xref:System.ArgumentOutOfRangeException> výsledky, pokud je hodnota větší než 5.</span><span class="sxs-lookup"><span data-stu-id="67f47-145">The maximum delay is 5 seconds; an <xref:System.ArgumentOutOfRangeException> results if the value is greater than 5.</span></span> <span data-ttu-id="67f47-146">Jak ukazuje následující příklad, je předán výjimku, která je vyvolána, když je hodnota 6 `GetMultipleAsync` metoda zabalené do <xref:System.AggregateException> po `GetMultipleAsync` metoda zahájí vykonávání.</span><span class="sxs-lookup"><span data-stu-id="67f47-146">As the following example shows, the exception that is thrown when a value of 6 is passed to the `GetMultipleAsync` method is wrapped in an <xref:System.AggregateException> after the `GetMultipleAsync` method begins execution.</span></span>

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

<span data-ttu-id="67f47-147">Jako jsme to udělali s metodu iterátoru, jsme Refaktorovat kód z tohoto příkladu a provést ověření před volání asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="67f47-147">As we did with the method iterator, we can refactor the code from this example to perform the validation before calling the asynchronous method.</span></span> <span data-ttu-id="67f47-148">Jak výstup z následující příklad ukazuje <xref:System.ArgumentOutOfRangeException> není zabalena v <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="67f47-148">As the output from the following example shows, the <xref:System.ArgumentOutOfRangeException> is not wrapped in a <xref:System.AggregateException>.</span></span>

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a><span data-ttu-id="67f47-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="67f47-149">See Also</span></span>

- [<span data-ttu-id="67f47-150">Metody</span><span class="sxs-lookup"><span data-stu-id="67f47-150">Methods</span></span>](methods.md)
