---
title: Doporučené postupy pro výjimky - .NET
ms.date: 12/05/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
ms.openlocfilehash: 1de231b01e3fa97e78a87ae6b0595a9b5536374e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160167"
---
# <a name="best-practices-for-exceptions"></a><span data-ttu-id="d3e91-102">Doporučené postupy pro výjimky</span><span class="sxs-lookup"><span data-stu-id="d3e91-102">Best practices for exceptions</span></span>

<span data-ttu-id="d3e91-103">Za účelem zamezení pádu aplikace zpracovává dobře navržená aplikace výjimky a chyby.</span><span class="sxs-lookup"><span data-stu-id="d3e91-103">A well-designed app handles exceptions and errors to prevent app crashes.</span></span> <span data-ttu-id="d3e91-104">Tato část popisuje osvědčené postupy pro zpracování a vytváření výjimek.</span><span class="sxs-lookup"><span data-stu-id="d3e91-104">This section describes best practices for handling and creating exceptions.</span></span>

## <a name="use-trycatchfinally-blocks-to-recover-from-errors-or-release-resources"></a><span data-ttu-id="d3e91-105">Pomocí bloků try/catch/finally se zotavit z chyb nebo uvolnit prostředky</span><span class="sxs-lookup"><span data-stu-id="d3e91-105">Use try/catch/finally blocks to recover from errors or release resources</span></span>

<span data-ttu-id="d3e91-106">`try` / Použijte `catch` bloky kolem kódu, který může potenciálně generovat výjimku ***a*** váš kód můžete obnovit z této výjimky.</span><span class="sxs-lookup"><span data-stu-id="d3e91-106">Use `try`/`catch` blocks around code that can potentially generate an exception ***and*** your code can recover from that exception.</span></span> <span data-ttu-id="d3e91-107">V `catch` blocích vždy seřizovat výjimky z nejvíce odvozené nejméně odvozené.</span><span class="sxs-lookup"><span data-stu-id="d3e91-107">In `catch` blocks, always order exceptions from the most derived to the least derived.</span></span> <span data-ttu-id="d3e91-108">Všechny výjimky <xref:System.Exception>jsou odvozeny z .</span><span class="sxs-lookup"><span data-stu-id="d3e91-108">All exceptions derive from <xref:System.Exception>.</span></span> <span data-ttu-id="d3e91-109">Více odvozené výjimky nejsou zpracovány catch klauzule, která předchází catch klauzule pro základní třídy výjimek.</span><span class="sxs-lookup"><span data-stu-id="d3e91-109">More derived exceptions are not handled by a catch clause that is preceded by a catch clause for a base exception class.</span></span> <span data-ttu-id="d3e91-110">Pokud váš kód nelze obnovit z výjimky, nezachytávejte tuto výjimku.</span><span class="sxs-lookup"><span data-stu-id="d3e91-110">When your code cannot recover from an exception, don't catch that exception.</span></span> <span data-ttu-id="d3e91-111">Povolit metody dále nahoru zásobníku volání obnovit, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="d3e91-111">Enable methods further up the call stack to recover if possible.</span></span>

<span data-ttu-id="d3e91-112">Vyčištění prostředků přidělených `using` buď příkazy nebo `finally` bloky.</span><span class="sxs-lookup"><span data-stu-id="d3e91-112">Clean up resources allocated with either `using` statements, or `finally` blocks.</span></span> <span data-ttu-id="d3e91-113">Preferovat `using` příkazy automaticky vyčistit prostředky při vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="d3e91-113">Prefer `using` statements to automatically clean up resources when exceptions are thrown.</span></span> <span data-ttu-id="d3e91-114">Pomocí `finally` bloků vyčistěte prostředky, které <xref:System.IDisposable>se neimplementují .</span><span class="sxs-lookup"><span data-stu-id="d3e91-114">Use `finally` blocks to clean up resources that don't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="d3e91-115">Kód v `finally` klauzuli je téměř vždy spuštěn, i když jsou vyvolány výjimky.</span><span class="sxs-lookup"><span data-stu-id="d3e91-115">Code in a `finally` clause is almost always executed even when exceptions are thrown.</span></span>

## <a name="handle-common-conditions-without-throwing-exceptions"></a><span data-ttu-id="d3e91-116">Zpracování běžných podmínek bez vyvolání výjimek</span><span class="sxs-lookup"><span data-stu-id="d3e91-116">Handle common conditions without throwing exceptions</span></span>

<span data-ttu-id="d3e91-117">Pro podmínky, které mohou nastat, ale může vyvolat výjimku, zvažte jejich zpracování způsobem, který zabrání výjimce.</span><span class="sxs-lookup"><span data-stu-id="d3e91-117">For conditions that are likely to occur but might trigger an exception, consider handling them in a way that will avoid the exception.</span></span> <span data-ttu-id="d3e91-118">Pokud se například pokusíte ukončit připojení, které je `InvalidOperationException`již uzavřeno, získáte .</span><span class="sxs-lookup"><span data-stu-id="d3e91-118">For example, if you try to close a connection that is already closed, you'll get an `InvalidOperationException`.</span></span> <span data-ttu-id="d3e91-119">Můžete se tomu vyhnout `if` pomocí příkazu ke kontrole stavu připojení před pokusem o jeho zavření.</span><span class="sxs-lookup"><span data-stu-id="d3e91-119">You can avoid that by using an `if` statement to check the connection state before trying to close it.</span></span>

[!code-cpp[Conceptual.Exception.Handling#2](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]

<span data-ttu-id="d3e91-120">Pokud před zavřením nezkontrolujete stav připojení, můžete výjimku `InvalidOperationException` zachytit.</span><span class="sxs-lookup"><span data-stu-id="d3e91-120">If you don't check connection state before closing, you can catch the `InvalidOperationException` exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#3](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]

<span data-ttu-id="d3e91-121">Metoda, kterou zvolit, závisí na tom, jak často očekáváte, že k události dojde.</span><span class="sxs-lookup"><span data-stu-id="d3e91-121">The method to choose depends on how often you expect the event to occur.</span></span>

- <span data-ttu-id="d3e91-122">Použijte zpracování výjimek, pokud k události nedochází velmi často, tzn. pokud k události dochází výjimečně a značí chybu (jako například neočekávaný konec souboru).</span><span class="sxs-lookup"><span data-stu-id="d3e91-122">Use exception handling if the event doesn't occur very often, that is, if the event is truly exceptional and indicates an error (such as an unexpected end-of-file).</span></span> <span data-ttu-id="d3e91-123">Při používání zpracování výjimek je za běžných podmínek provedena menší část kódu.</span><span class="sxs-lookup"><span data-stu-id="d3e91-123">When you use exception handling, less code is executed in normal conditions.</span></span>

- <span data-ttu-id="d3e91-124">Zkontrolujte chybové stavy v kódu, pokud k události dochází rutinně a může být považována za součást normálního spuštění.</span><span class="sxs-lookup"><span data-stu-id="d3e91-124">Check for error conditions in code if the event happens routinely and could be considered part of normal execution.</span></span> <span data-ttu-id="d3e91-125">Při kontrole běžných chybových stavů je spuštěno méně kódu, protože se vyhnete výjimkám.</span><span class="sxs-lookup"><span data-stu-id="d3e91-125">When you check for common error conditions, less code is executed because you avoid exceptions.</span></span>

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a><span data-ttu-id="d3e91-126">Navrhujte třídy tak, aby se zabránilo výjimkám</span><span class="sxs-lookup"><span data-stu-id="d3e91-126">Design classes so that exceptions can be avoided</span></span>

<span data-ttu-id="d3e91-127">Třída může poskytnout metody nebo vlastnosti, které umožňují vyhnout se volání, které by spustilo výjimku.</span><span class="sxs-lookup"><span data-stu-id="d3e91-127">A class can provide methods or properties that enable you to avoid making a call that would trigger an exception.</span></span> <span data-ttu-id="d3e91-128">Například <xref:System.IO.FileStream> třída poskytuje metody, které pomáhají určit, zda bylo dosaženo konce souboru.</span><span class="sxs-lookup"><span data-stu-id="d3e91-128">For example, a <xref:System.IO.FileStream> class provides methods that help determine whether the end of the file has been reached.</span></span> <span data-ttu-id="d3e91-129">Ty lze použít, aby se zabránilo výjimku, která je vyvolána, pokud čtete za koncem souboru.</span><span class="sxs-lookup"><span data-stu-id="d3e91-129">These can be used to avoid the exception that is thrown if you read past the end of the file.</span></span> <span data-ttu-id="d3e91-130">Následující příklad ukazuje, jak číst až do konce souboru bez spuštění výjimky.</span><span class="sxs-lookup"><span data-stu-id="d3e91-130">The following example shows how to read to the end of a file without triggering an exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#5](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]

<span data-ttu-id="d3e91-131">Dalším způsobem, jak se vyhnout výjimkám, je vrátit hodnotu null (nebo výchozí) pro extrémně běžné chybové případy namísto vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="d3e91-131">Another way to avoid exceptions is to return null (or default) for extremely common error cases instead of throwing an exception.</span></span> <span data-ttu-id="d3e91-132">Za nejběžnější případ chyby lze považovat běžný tok řízení.</span><span class="sxs-lookup"><span data-stu-id="d3e91-132">An extremely common error case can be considered normal flow of control.</span></span> <span data-ttu-id="d3e91-133">Vrácením null (nebo výchozí) v těchto případech minimalizovat dopad na výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="d3e91-133">By returning null (or default) in these cases, you minimize the performance impact to an app.</span></span>

<span data-ttu-id="d3e91-134">Pro typy hodnot, `Nullable<T>` zda použít nebo výchozí jako indikátor chyby je něco, co je třeba zvážit pro konkrétní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d3e91-134">For value types, whether to use `Nullable<T>` or default as your error indicator is something to consider for your particular app.</span></span> <span data-ttu-id="d3e91-135">Pomocí `Nullable<Guid>`aplikace `default` `null` se `Guid.Empty`místo aplikace stane .</span><span class="sxs-lookup"><span data-stu-id="d3e91-135">By using `Nullable<Guid>`, `default` becomes `null` instead of `Guid.Empty`.</span></span> <span data-ttu-id="d3e91-136">Někdy, přidání `Nullable<T>` může být jasnější, když je hodnota přítomna nebo chybí.</span><span class="sxs-lookup"><span data-stu-id="d3e91-136">Some times, adding `Nullable<T>` can make it clearer when a value is present or absent.</span></span> <span data-ttu-id="d3e91-137">Jindy přidání `Nullable<T>` můžete vytvořit další případy pro kontrolu, které nejsou nutné a slouží pouze k vytvoření potenciální zdroje chyb.</span><span class="sxs-lookup"><span data-stu-id="d3e91-137">Other times, adding `Nullable<T>` can create extra cases to check that aren't necessary, and only serve to create potential sources of errors.</span></span>

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a><span data-ttu-id="d3e91-138">Vyvolat výjimky namísto vrácení kódu chyby</span><span class="sxs-lookup"><span data-stu-id="d3e91-138">Throw exceptions instead of returning an error code</span></span>

<span data-ttu-id="d3e91-139">Výjimky zajišťují, že chyby nezůstávají bez povšimnutí, protože volající kód nezkontroloval návratový kód.</span><span class="sxs-lookup"><span data-stu-id="d3e91-139">Exceptions ensure that failures do not go unnoticed because calling code didn't check a return code.</span></span>

## <a name="use-the-predefined-net-exception-types"></a><span data-ttu-id="d3e91-140">Použití předdefinovaných typů výjimek .NET</span><span class="sxs-lookup"><span data-stu-id="d3e91-140">Use the predefined .NET exception types</span></span>

<span data-ttu-id="d3e91-141">Zavést novou třídu výjimek pouze v případě, že se nepoužije předdefinovaná třída.</span><span class="sxs-lookup"><span data-stu-id="d3e91-141">Introduce a new exception class only when a predefined one doesn't apply.</span></span> <span data-ttu-id="d3e91-142">Například:</span><span class="sxs-lookup"><span data-stu-id="d3e91-142">For example:</span></span>

- <span data-ttu-id="d3e91-143">Vyvolat <xref:System.InvalidOperationException> výjimku, pokud sada vlastností nebo volání metody není vhodné vzhledem k aktuálnímu stavu objektu.</span><span class="sxs-lookup"><span data-stu-id="d3e91-143">Throw an <xref:System.InvalidOperationException> exception if a property set or method call is not appropriate given the object's current state.</span></span>

- <span data-ttu-id="d3e91-144">Vyvolat <xref:System.ArgumentException> výjimku nebo jednu z předdefinovaných tříd, které jsou odvozeny z <xref:System.ArgumentException> pokud jsou předány neplatné parametry.</span><span class="sxs-lookup"><span data-stu-id="d3e91-144">Throw an <xref:System.ArgumentException> exception or one of the predefined classes that derive from <xref:System.ArgumentException> if invalid parameters are passed.</span></span>

## <a name="end-exception-class-names-with-the-word-exception"></a><span data-ttu-id="d3e91-145">Ukončení názvů tříd výjimek se slovem`Exception`</span><span class="sxs-lookup"><span data-stu-id="d3e91-145">End exception class names with the word `Exception`</span></span>

<span data-ttu-id="d3e91-146">Pokud je nutná vlastní výjimka, pojmenujte <xref:System.Exception> ji odpovídajícím způsobem a odvodte ji z třídy.</span><span class="sxs-lookup"><span data-stu-id="d3e91-146">When a custom exception is necessary, name it appropriately and derive it from the <xref:System.Exception> class.</span></span> <span data-ttu-id="d3e91-147">Například:</span><span class="sxs-lookup"><span data-stu-id="d3e91-147">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#4](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]

## <a name="include-three-constructors-in-custom-exception-classes"></a><span data-ttu-id="d3e91-148">Zahrnout tři konstruktory do vlastních tříd výjimek</span><span class="sxs-lookup"><span data-stu-id="d3e91-148">Include three constructors in custom exception classes</span></span>

<span data-ttu-id="d3e91-149">Při vytváření vlastních tříd výjimek použijte alespoň tři běžné konstruktory: konstruktor bez parametrů, konstruktor, který přebírá zprávu řetězce, a konstruktor, který přebírá zprávu řetězce a vnitřní výjimku.</span><span class="sxs-lookup"><span data-stu-id="d3e91-149">Use at least the three common constructors when creating your own exception classes: the parameterless constructor, a constructor that takes a string message, and a constructor that takes a string message and an inner exception.</span></span>

- <span data-ttu-id="d3e91-150"><xref:System.Exception.%23ctor>, který používá výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d3e91-150"><xref:System.Exception.%23ctor>, which uses default values.</span></span>

- <span data-ttu-id="d3e91-151"><xref:System.Exception.%23ctor%28System.String%29>, který přijímá zprávu řetězce.</span><span class="sxs-lookup"><span data-stu-id="d3e91-151"><xref:System.Exception.%23ctor%28System.String%29>, which accepts a string message.</span></span>

- <span data-ttu-id="d3e91-152"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, který přijímá zprávu řetězce a vnitřní výjimku.</span><span class="sxs-lookup"><span data-stu-id="d3e91-152"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, which accepts a string message and an inner exception.</span></span>

<span data-ttu-id="d3e91-153">Příklad najdete v [tématu How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="d3e91-153">For an example, see [How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).</span></span>

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a><span data-ttu-id="d3e91-154">Ujistěte se, že data výjimky jsou k dispozici při vzdáleném spuštění kódu</span><span class="sxs-lookup"><span data-stu-id="d3e91-154">Ensure that exception data is available when code executes remotely</span></span>

<span data-ttu-id="d3e91-155">Při vytváření uživatelem definovaných výjimek se ujistěte, že metadata pro výjimky jsou k dispozici pro kód, který je spuštěn vzdáleně.</span><span class="sxs-lookup"><span data-stu-id="d3e91-155">When you create user-defined exceptions, ensure that the metadata for the exceptions is available to code that is executing remotely.</span></span>

<span data-ttu-id="d3e91-156">Například na implementacích rozhraní .NET, které podporují domény aplikací, mohou v doménách aplikací nastat výjimky.</span><span class="sxs-lookup"><span data-stu-id="d3e91-156">For example, on .NET implementations that support App Domains, exceptions may occur across App domains.</span></span> <span data-ttu-id="d3e91-157">Předpokládejme, že doména aplikace A vytvoří doménu aplikace B, která spustí kód, který vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="d3e91-157">Suppose App Domain A creates App Domain B, which executes code that throws an exception.</span></span> <span data-ttu-id="d3e91-158">Pro doménu aplikace A správně zachytit a zpracovat výjimku, musí být schopen najít sestavení, které obsahuje výjimku vyváděnou doménou aplikace B. Pokud doména aplikace B vyvolá výjimku, která je obsažena v sestavení v rámci jeho aplikační základny, ale ne v rámci aplikační základny domény <xref:System.IO.FileNotFoundException> aplikace, doména aplikace A nebude moci najít výjimku a za běhu společného jazyka vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="d3e91-158">For App Domain A to properly catch and handle the exception, it must be able to find the assembly that contains the exception thrown by App Domain B. If App Domain B throws an exception that is contained in an assembly under its application base, but not under App Domain A's application base, App Domain A will not be able to find the exception, and the common language runtime will throw a <xref:System.IO.FileNotFoundException> exception.</span></span> <span data-ttu-id="d3e91-159">Této situaci zamezíte tak, že nasadíte sestavení obsahující informace o výjimce dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="d3e91-159">To avoid this situation, you can deploy the assembly that contains the exception information in two ways:</span></span>

- <span data-ttu-id="d3e91-160">Sestavení umístěte do společného základu cesty aplikace sdíleného oběma doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="d3e91-160">Put the assembly into a common application base shared by both app domains.</span></span>

    <span data-ttu-id="d3e91-161">\-nebo -</span><span class="sxs-lookup"><span data-stu-id="d3e91-161">\- or -</span></span>

- <span data-ttu-id="d3e91-162">Pokud domény nesdílejí společný základ cesty aplikace, podepište sestavení obsahující informace o výjimce silným názvem a nasaďte sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="d3e91-162">If the domains do not share a common application base, sign the assembly that contains the exception information with a strong name and deploy the assembly into the global assembly cache.</span></span>

## <a name="use-grammatically-correct-error-messages"></a><span data-ttu-id="d3e91-163">Použití gramaticky správných chybových zpráv</span><span class="sxs-lookup"><span data-stu-id="d3e91-163">Use grammatically correct error messages</span></span>

<span data-ttu-id="d3e91-164">Napište jasné věty a zahrňte koncovou interpunkci.</span><span class="sxs-lookup"><span data-stu-id="d3e91-164">Write clear sentences and include ending punctuation.</span></span> <span data-ttu-id="d3e91-165">Každá věta v řetězci přiřazené vlastnosti <xref:System.Exception.Message?displayProperty=nameWithType> by měla končit tečkou.</span><span class="sxs-lookup"><span data-stu-id="d3e91-165">Each sentence in the string assigned to the <xref:System.Exception.Message?displayProperty=nameWithType> property should end in a period.</span></span> <span data-ttu-id="d3e91-166">Například "Tabulka protokolu přetekl."</span><span class="sxs-lookup"><span data-stu-id="d3e91-166">For example, "The log table has overflowed."</span></span> <span data-ttu-id="d3e91-167">by byl vhodný řetězec zprávy.</span><span class="sxs-lookup"><span data-stu-id="d3e91-167">would be an appropriate message string.</span></span>

## <a name="include-a-localized-string-message-in-every-exception"></a><span data-ttu-id="d3e91-168">Zahrnout lokalizovanou zprávu řetězce do každé výjimky</span><span class="sxs-lookup"><span data-stu-id="d3e91-168">Include a localized string message in every exception</span></span>

<span data-ttu-id="d3e91-169">Chybová zpráva, která se zobrazí uživatel <xref:System.Exception.Message?displayProperty=nameWithType> je odvozen z vlastnosti výjimky, která byla vyvolána a nikoli z názvu třídy výjimky.</span><span class="sxs-lookup"><span data-stu-id="d3e91-169">The error message that the user sees is derived from the <xref:System.Exception.Message?displayProperty=nameWithType> property of the exception that was thrown, and not from the name of the exception class.</span></span> <span data-ttu-id="d3e91-170">Obvykle přiřadíte hodnotu <xref:System.Exception.Message?displayProperty=nameWithType> vlastnosti předáním řetězce `message` zprávy argumentu [konstruktoru Exception](xref:System.Exception.%23ctor%2A).</span><span class="sxs-lookup"><span data-stu-id="d3e91-170">Typically, you assign a value to the <xref:System.Exception.Message?displayProperty=nameWithType>  property by passing the message string to the `message` argument of an [Exception constructor](xref:System.Exception.%23ctor%2A).</span></span>

<span data-ttu-id="d3e91-171">Pro lokalizované aplikace byste měli zadat řetězec lokalizované zprávy pro každou výjimku, kterou může aplikace vyvolat.</span><span class="sxs-lookup"><span data-stu-id="d3e91-171">For localized applications, you should provide a localized message string for every exception that your application can throw.</span></span> <span data-ttu-id="d3e91-172">Soubory prostředků se používají k poskytování lokalizovaných chybových zpráv.</span><span class="sxs-lookup"><span data-stu-id="d3e91-172">You use resource files to provide localized error messages.</span></span> <span data-ttu-id="d3e91-173">Informace o lokalizaci aplikací a načítání lokalizovaných řetězců naleznete v následujících článcích:</span><span class="sxs-lookup"><span data-stu-id="d3e91-173">For information on localizing applications and retrieving localized strings, see the following articles:</span></span>

- [<span data-ttu-id="d3e91-174">Postupy: Vytváření uživatelsky definovaných výjimek s lokalizovanými zprávami výjimek</span><span class="sxs-lookup"><span data-stu-id="d3e91-174">How to: create user-defined exceptions with localized exception messages</span></span>](how-to-create-localized-exception-messages.md)
- [<span data-ttu-id="d3e91-175">Prostředky v aplikacích klasické pracovní plochy</span><span class="sxs-lookup"><span data-stu-id="d3e91-175">Resources in Desktop Apps</span></span>](../../framework/resources/index.md)
- <xref:System.Resources.ResourceManager?displayProperty=nameWithType>

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a><span data-ttu-id="d3e91-176">Ve vlastních výjimkách poskytněte podle potřeby další vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d3e91-176">In custom exceptions, provide additional properties as needed</span></span>

<span data-ttu-id="d3e91-177">Zadejte další vlastnosti pro výjimku (kromě řetězce vlastní zprávy) pouze v případě, že existuje programový scénář, kde jsou užitečné další informace.</span><span class="sxs-lookup"><span data-stu-id="d3e91-177">Provide additional properties for an exception (in addition to the custom message string) only when there's a programmatic scenario where the additional information is useful.</span></span> <span data-ttu-id="d3e91-178">Například poskytuje <xref:System.IO.FileNotFoundException> <xref:System.IO.FileNotFoundException.FileName> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d3e91-178">For example, the <xref:System.IO.FileNotFoundException> provides the <xref:System.IO.FileNotFoundException.FileName> property.</span></span>

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a><span data-ttu-id="d3e91-179">Umístit příkazy throw tak, aby trasování zásobníku bylo užitečné</span><span class="sxs-lookup"><span data-stu-id="d3e91-179">Place throw statements so that the stack trace will be helpful</span></span>

<span data-ttu-id="d3e91-180">Trasování zásobníku začíná na příkaz, kde je vyvolána výjimka a končí na `catch` příkaz, který zachytí výjimku.</span><span class="sxs-lookup"><span data-stu-id="d3e91-180">The stack trace begins at the statement where the exception is thrown and ends at the `catch` statement that catches the exception.</span></span>

## <a name="use-exception-builder-methods"></a><span data-ttu-id="d3e91-181">Použití metod tvůrce výjimek</span><span class="sxs-lookup"><span data-stu-id="d3e91-181">Use exception builder methods</span></span>

<span data-ttu-id="d3e91-182">Pro třídu je běžné vyvolat stejnou výjimku z různých míst v rámci příslušné implementace.</span><span class="sxs-lookup"><span data-stu-id="d3e91-182">It is common for a class to throw the same exception from different places in its implementation.</span></span> <span data-ttu-id="d3e91-183">Abyste zabránili nadbytečnému kódu, použijte pomocné metody k vytvoření výjimky a vrácení výjimky.</span><span class="sxs-lookup"><span data-stu-id="d3e91-183">To avoid excessive code, use helper methods that create the exception and return it.</span></span> <span data-ttu-id="d3e91-184">Například:</span><span class="sxs-lookup"><span data-stu-id="d3e91-184">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#6](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]

<span data-ttu-id="d3e91-185">V některých případech je vhodnější použít konstruktor výjimky k vytvoření výjimky.</span><span class="sxs-lookup"><span data-stu-id="d3e91-185">In some cases, it's more appropriate to use the exception's constructor to build the exception.</span></span> <span data-ttu-id="d3e91-186">Příkladem je globální třída výjimek, například <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="d3e91-186">An example is a global exception class such as <xref:System.ArgumentException>.</span></span>

## <a name="restore-state-when-methods-dont-complete-due-to-exceptions"></a><span data-ttu-id="d3e91-187">Obnovit stav, když metody nejsou dokončeny z důvodu výjimek</span><span class="sxs-lookup"><span data-stu-id="d3e91-187">Restore state when methods don't complete due to exceptions</span></span>

<span data-ttu-id="d3e91-188">Volající by měl předpokládat, že při vyvolání výjimky z metody nedojde k žádným vedlejším účinkům.</span><span class="sxs-lookup"><span data-stu-id="d3e91-188">Callers should be able to assume that there are no side effects when an exception is thrown from a method.</span></span> <span data-ttu-id="d3e91-189">Máte-li například kód, který převádí peníze výběrem z jednoho účtu a uložením na jiný účet, a při provádění vkladu je vyvolána výjimka, nechcete, aby výběr zůstal v platnosti.</span><span class="sxs-lookup"><span data-stu-id="d3e91-189">For example, if you have code that transfers money by withdrawing from one account and depositing in another account, and an exception is thrown while executing the deposit, you don't want the withdrawal to remain in effect.</span></span>

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect.
    to.Deposit(amount);
}
```

```vb
Public Sub TransferFunds(from As Account, [to] As Account, amount As Decimal)
    from.Withdrawal(amount)
    ' If the deposit fails, the withdrawal shouldn't remain in effect.
    [to].Deposit(amount)
End Sub
```

<span data-ttu-id="d3e91-190">Výše uvedená metoda nevyvolá žádné výjimky, ale musí být napsána defenzivně, takže pokud operace vkladu selže, výběr je obrácen.</span><span class="sxs-lookup"><span data-stu-id="d3e91-190">The method above does not directly throw any exceptions, but must be written defensively so that if the deposit operation fails, the withdrawal is reversed.</span></span>

<span data-ttu-id="d3e91-191">Jedním ze způsobů, jak tuto situaci zvládnout, je zachytit všechny výjimky vyvržené vkladovou transakcí a vrátit zpět výběr.</span><span class="sxs-lookup"><span data-stu-id="d3e91-191">One way to handle this situation is to catch any exceptions thrown by the deposit transaction and roll back the withdrawal.</span></span>

```csharp
private static void TransferFunds(Account from, Account to, decimal amount)
{
    string withdrawalTrxID = from.Withdrawal(amount);
    try
    {
        to.Deposit(amount);
    }
    catch
    {
        from.RollbackTransaction(withdrawalTrxID);
        throw;
    }
}
```

```vb
Private Shared Sub TransferFunds(from As Account, [to] As Account, amount As Decimal)
    Dim withdrawalTrxID As String = from.Withdrawal(amount)
    Try
        [to].Deposit(amount)
    Catch
        from.RollbackTransaction(withdrawalTrxID)
        Throw
    End Try
End Sub
```

<span data-ttu-id="d3e91-192">Tento příklad ilustruje použití `throw` znovu vyvolat původní výjimku, která může usnadnit volajícím zobrazit skutečnou příčinu <xref:System.Exception.InnerException> problému bez nutnosti zkoumat vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d3e91-192">This example illustrates the use of `throw` to re-throw the original exception, which can make it easier for callers to see the real cause of the problem without having to examine the <xref:System.Exception.InnerException> property.</span></span> <span data-ttu-id="d3e91-193">Alternativou je vyvolat novou výjimku a zahrnout původní výjimku jako vnitřní výjimku:</span><span class="sxs-lookup"><span data-stu-id="d3e91-193">An alternative is to throw a new exception and include the original exception as the inner exception:</span></span>

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new TransferFundsException("Withdrawal failed.", innerException: ex)
    {
        From = from,
        To = to,
        Amount = amount
    };
}
```

```vb
Catch ex As Exception
    from.RollbackTransaction(withdrawalTrxID)
    Throw New TransferFundsException("Withdrawal failed.", innerException:=ex) With
    {
        .From = from,
        .[To] = [to],
        .Amount = amount
    }
End Try
```

## <a name="see-also"></a><span data-ttu-id="d3e91-194">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3e91-194">See also</span></span>

- [<span data-ttu-id="d3e91-195">Výjimky</span><span class="sxs-lookup"><span data-stu-id="d3e91-195">Exceptions</span></span>](index.md)
