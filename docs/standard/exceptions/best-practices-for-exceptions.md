---
title: Osvědčené postupy pro výjimky – .NET
ms.date: 12/05/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
ms.openlocfilehash: 6a165c3e0f41603ef7233669d7148dd44b1d3ce6
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696764"
---
# <a name="best-practices-for-exceptions"></a><span data-ttu-id="0641d-102">Osvědčené postupy pro výjimky</span><span class="sxs-lookup"><span data-stu-id="0641d-102">Best practices for exceptions</span></span>

<span data-ttu-id="0641d-103">Za účelem zamezení pádu aplikace zpracovává dobře navržená aplikace výjimky a chyby.</span><span class="sxs-lookup"><span data-stu-id="0641d-103">A well-designed app handles exceptions and errors to prevent app crashes.</span></span> <span data-ttu-id="0641d-104">Tato část popisuje osvědčené postupy pro zpracování a vytváření výjimek.</span><span class="sxs-lookup"><span data-stu-id="0641d-104">This section describes best practices for handling and creating exceptions.</span></span>

## <a name="use-trycatchfinally-blocks-to-recover-from-errors-or-release-resources"></a><span data-ttu-id="0641d-105">Pro zotavení z chyb nebo uvolnění prostředků použijte bloky try/catch/finally.</span><span class="sxs-lookup"><span data-stu-id="0641d-105">Use try/catch/finally blocks to recover from errors or release resources</span></span>

<span data-ttu-id="0641d-106">Použijte `try` @ no__t-1 @ no__t-2 bloků kolem kódu, který může potenciálně generovat výjimku ***a*** váš kód může z této výjimky obnovit.</span><span class="sxs-lookup"><span data-stu-id="0641d-106">Use `try`/`catch` blocks around code that can potentially generate an exception ***and*** your code can recover from that exception.</span></span> <span data-ttu-id="0641d-107">V blocích `catch` vždy seřazení výjimek z největší odvozené na nejméně odvozené.</span><span class="sxs-lookup"><span data-stu-id="0641d-107">In `catch` blocks, always order exceptions from the most derived to the least derived.</span></span> <span data-ttu-id="0641d-108">Všechny výjimky jsou odvozeny z <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="0641d-108">All exceptions derive from <xref:System.Exception>.</span></span> <span data-ttu-id="0641d-109">Další odvozené výjimky nejsou zpracovány klauzulí catch, která předchází klauzuli catch pro základní třídu výjimky.</span><span class="sxs-lookup"><span data-stu-id="0641d-109">More derived exceptions are not handled by a catch clause that is preceded by a catch clause for a base exception class.</span></span> <span data-ttu-id="0641d-110">Když se váš kód nemůže zotavit z výjimky, nezachyťte tuto výjimku.</span><span class="sxs-lookup"><span data-stu-id="0641d-110">When your code cannot recover from an exception, don't catch that exception.</span></span> <span data-ttu-id="0641d-111">Pokud je to možné, povolte metody další v zásobníku volání pro obnovení.</span><span class="sxs-lookup"><span data-stu-id="0641d-111">Enable methods further up the call stack to recover if possible.</span></span>

<span data-ttu-id="0641d-112">Vyčistěte prostředky přidělené buď pomocí příkazů `using`, nebo bloků `finally`.</span><span class="sxs-lookup"><span data-stu-id="0641d-112">Clean up resources allocated with either `using` statements, or `finally` blocks.</span></span> <span data-ttu-id="0641d-113">Preferovat `using` příkazy k automatickému vyčištění prostředků, když jsou vyvolány výjimky.</span><span class="sxs-lookup"><span data-stu-id="0641d-113">Prefer `using` statements to automatically clean up resources when exceptions are thrown.</span></span> <span data-ttu-id="0641d-114">Pomocí bloků `finally` vyčistěte prostředky, které neimplementují <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="0641d-114">Use `finally` blocks to clean up resources that don't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="0641d-115">Kód v klauzuli `finally` je téměř vždy spouštěn i v případě, že jsou výjimky vyvolány.</span><span class="sxs-lookup"><span data-stu-id="0641d-115">Code in a `finally` clause is almost always executed even when exceptions are thrown.</span></span>

## <a name="handle-common-conditions-without-throwing-exceptions"></a><span data-ttu-id="0641d-116">Zpracování běžných podmínek bez vyvolání výjimek</span><span class="sxs-lookup"><span data-stu-id="0641d-116">Handle common conditions without throwing exceptions</span></span>

<span data-ttu-id="0641d-117">Pro podmínky, které se pravděpodobně vyskytují, ale mohou aktivovat výjimku, zvažte jejich zpracování způsobem, který se vyhne výjimce.</span><span class="sxs-lookup"><span data-stu-id="0641d-117">For conditions that are likely to occur but might trigger an exception, consider handling them in a way that will avoid the exception.</span></span> <span data-ttu-id="0641d-118">Například pokud se pokusíte zavřít připojení, které je již uzavřeno, získáte `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="0641d-118">For example, if you try to close a connection that is already closed, you'll get an `InvalidOperationException`.</span></span> <span data-ttu-id="0641d-119">Tomu můžete zabránit pomocí příkazu `if` ke kontrole stavu připojení před pokusem o jeho zavření.</span><span class="sxs-lookup"><span data-stu-id="0641d-119">You can avoid that by using an `if` statement to check the connection state before trying to close it.</span></span>

[!code-cpp[Conceptual.Exception.Handling#2](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]

<span data-ttu-id="0641d-120">Pokud před zavřením nezkontrolujete stav připojení, můžete zachytit výjimku `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="0641d-120">If you don't check connection state before closing, you can catch the `InvalidOperationException` exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#3](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]

<span data-ttu-id="0641d-121">Metoda, kterou zvolíte, závisí na tom, jak často očekáváte, že k události dojde.</span><span class="sxs-lookup"><span data-stu-id="0641d-121">The method to choose depends on how often you expect the event to occur.</span></span>

- <span data-ttu-id="0641d-122">Použijte zpracování výjimek, pokud k události nedochází velmi často, tzn. pokud k události dochází výjimečně a značí chybu (jako například neočekávaný konec souboru).</span><span class="sxs-lookup"><span data-stu-id="0641d-122">Use exception handling if the event doesn't occur very often, that is, if the event is truly exceptional and indicates an error (such as an unexpected end-of-file).</span></span> <span data-ttu-id="0641d-123">Při používání zpracování výjimek je za běžných podmínek provedena menší část kódu.</span><span class="sxs-lookup"><span data-stu-id="0641d-123">When you use exception handling, less code is executed in normal conditions.</span></span>

- <span data-ttu-id="0641d-124">Zkontroluje chybové podmínky v kódu, pokud k události dochází rutinně a mohla by být považována za součást normálního spuštění.</span><span class="sxs-lookup"><span data-stu-id="0641d-124">Check for error conditions in code if the event happens routinely and could be considered part of normal execution.</span></span> <span data-ttu-id="0641d-125">Při kontrole běžných chybových stavů se spustí méně kódu, protože se vyhnete výjimkám.</span><span class="sxs-lookup"><span data-stu-id="0641d-125">When you check for common error conditions, less code is executed because you avoid exceptions.</span></span>

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a><span data-ttu-id="0641d-126">Třídy návrhu tak, aby bylo možné vyhnout se výjimkám</span><span class="sxs-lookup"><span data-stu-id="0641d-126">Design classes so that exceptions can be avoided</span></span>

<span data-ttu-id="0641d-127">Třída může poskytovat metody nebo vlastnosti, které umožňují vyhnout se volání, které by aktivovalo výjimku.</span><span class="sxs-lookup"><span data-stu-id="0641d-127">A class can provide methods or properties that enable you to avoid making a call that would trigger an exception.</span></span> <span data-ttu-id="0641d-128">Například třída <xref:System.IO.FileStream> poskytuje metody, které vám pomůžou určit, jestli bylo dosaženo konce souboru.</span><span class="sxs-lookup"><span data-stu-id="0641d-128">For example, a <xref:System.IO.FileStream> class provides methods that help determine whether the end of the file has been reached.</span></span> <span data-ttu-id="0641d-129">Ty lze použít k zamezení výjimky, která je vyvolána, pokud přečtení za koncem souboru.</span><span class="sxs-lookup"><span data-stu-id="0641d-129">These can be used to avoid the exception that is thrown if you read past the end of the file.</span></span> <span data-ttu-id="0641d-130">Následující příklad ukazuje, jak číst na konec souboru bez vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="0641d-130">The following example shows how to read to the end of a file without triggering an exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#5](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]

<span data-ttu-id="0641d-131">Dalším způsobem, jak se vyhnout výjimkám, je vrátit hodnotu null (nebo výchozí) pro extrémně běžné chybové případy namísto vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="0641d-131">Another way to avoid exceptions is to return null (or default) for extremely common error cases instead of throwing an exception.</span></span> <span data-ttu-id="0641d-132">Za nejběžnější případ chyby lze považovat běžný tok řízení.</span><span class="sxs-lookup"><span data-stu-id="0641d-132">An extremely common error case can be considered normal flow of control.</span></span> <span data-ttu-id="0641d-133">Vrácením hodnoty null (nebo výchozí) v těchto případech minimalizujete dopad na výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="0641d-133">By returning null (or default) in these cases, you minimize the performance impact to an app.</span></span>

<span data-ttu-id="0641d-134">Pro typy hodnot bez ohledu na to, jestli se má jako indikátor chyby použít `Nullable<T>` nebo výchozí, je třeba zvážit konkrétní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0641d-134">For value types, whether to use `Nullable<T>` or default as your error indicator is something to consider for your particular app.</span></span> <span data-ttu-id="0641d-135">Pomocí `Nullable<Guid>` se `default` stal `null` namísto `Guid.Empty`.</span><span class="sxs-lookup"><span data-stu-id="0641d-135">By using `Nullable<Guid>`, `default` becomes `null` instead of `Guid.Empty`.</span></span> <span data-ttu-id="0641d-136">V některých případech může přidání `Nullable<T>` usnadnit jeho zrušení, pokud je hodnota přítomna nebo chybí.</span><span class="sxs-lookup"><span data-stu-id="0641d-136">Some times, adding `Nullable<T>` can make it clearer when a value is present or absent.</span></span> <span data-ttu-id="0641d-137">Jinak přidání `Nullable<T>` může vytvořit další případy, které nepotřebují, a sloužit pouze k vytváření potenciálních zdrojů chyb.</span><span class="sxs-lookup"><span data-stu-id="0641d-137">Other times, adding `Nullable<T>` can create extra cases to check that aren't necessary, and only serve to create potential sources of errors.</span></span> 

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a><span data-ttu-id="0641d-138">Vyvolat výjimky místo vrácení kódu chyby</span><span class="sxs-lookup"><span data-stu-id="0641d-138">Throw exceptions instead of returning an error code</span></span>

<span data-ttu-id="0641d-139">Výjimky zajišťují, že chyby nejdou nekontrolují, protože volání kódu nevrátilo návratový kód.</span><span class="sxs-lookup"><span data-stu-id="0641d-139">Exceptions ensure that failures do not go unnoticed because calling code didn't check a return code.</span></span>

## <a name="use-the-predefined-net-exception-types"></a><span data-ttu-id="0641d-140">Použít předdefinované typy výjimek .NET</span><span class="sxs-lookup"><span data-stu-id="0641d-140">Use the predefined .NET exception types</span></span>

<span data-ttu-id="0641d-141">Zaveďte novou třídu výjimky pouze v případě, že není použita předdefinovaná.</span><span class="sxs-lookup"><span data-stu-id="0641d-141">Introduce a new exception class only when a predefined one doesn't apply.</span></span> <span data-ttu-id="0641d-142">Příklad:</span><span class="sxs-lookup"><span data-stu-id="0641d-142">For example:</span></span>

- <span data-ttu-id="0641d-143">Vyvolejte výjimku <xref:System.InvalidOperationException>, pokud sada vlastností nebo volání metody není vhodná pro daný aktuální stav objektu.</span><span class="sxs-lookup"><span data-stu-id="0641d-143">Throw an <xref:System.InvalidOperationException> exception if a property set or method call is not appropriate given the object's current state.</span></span>

- <span data-ttu-id="0641d-144">Vyvolejte výjimku <xref:System.ArgumentException> nebo jednu z předdefinovaných tříd, které jsou odvozeny z <xref:System.ArgumentException>, pokud jsou předány neplatné parametry.</span><span class="sxs-lookup"><span data-stu-id="0641d-144">Throw an <xref:System.ArgumentException> exception or one of the predefined classes that derive from <xref:System.ArgumentException> if invalid parameters are passed.</span></span>

## <a name="end-exception-class-names-with-the-word-exception"></a><span data-ttu-id="0641d-145">Ukončit názvy tříd výjimek pomocí slova `Exception`</span><span class="sxs-lookup"><span data-stu-id="0641d-145">End exception class names with the word `Exception`</span></span>

<span data-ttu-id="0641d-146">Pokud je nezbytná vlastní výjimka, pojmenujte ji odpovídajícím způsobem a odvodit ji od třídy <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="0641d-146">When a custom exception is necessary, name it appropriately and derive it from the <xref:System.Exception> class.</span></span> <span data-ttu-id="0641d-147">Příklad:</span><span class="sxs-lookup"><span data-stu-id="0641d-147">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#4](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]

## <a name="include-three-constructors-in-custom-exception-classes"></a><span data-ttu-id="0641d-148">Zahrnout tři konstruktory do vlastních tříd výjimek</span><span class="sxs-lookup"><span data-stu-id="0641d-148">Include three constructors in custom exception classes</span></span>

<span data-ttu-id="0641d-149">Při vytváření vlastních tříd výjimek použijte alespoň tři společné konstruktory: konstruktor bez parametrů, konstruktor, který přijímá zprávu řetězce, a konstruktor, který přijímá zprávu řetězce a vnitřní výjimku.</span><span class="sxs-lookup"><span data-stu-id="0641d-149">Use at least the three common constructors when creating your own exception classes: the parameterless constructor, a constructor that takes a string message, and a constructor that takes a string message and an inner exception.</span></span>

- <span data-ttu-id="0641d-150">@no__t – 0, který používá výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0641d-150"><xref:System.Exception.%23ctor>, which uses default values.</span></span>

- <span data-ttu-id="0641d-151"><xref:System.Exception.%23ctor%28System.String%29>, který přijímá řetězcovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="0641d-151"><xref:System.Exception.%23ctor%28System.String%29>, which accepts a string message.</span></span>

- <span data-ttu-id="0641d-152"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, který přijímá řetězcovou zprávu a vnitřní výjimku.</span><span class="sxs-lookup"><span data-stu-id="0641d-152"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, which accepts a string message and an inner exception.</span></span>

<span data-ttu-id="0641d-153">Příklad naleznete v tématu [How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="0641d-153">For an example, see [How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).</span></span>

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a><span data-ttu-id="0641d-154">Ujistěte se, že data výjimky jsou k dispozici, když se kód spustí vzdáleně.</span><span class="sxs-lookup"><span data-stu-id="0641d-154">Ensure that exception data is available when code executes remotely</span></span>

<span data-ttu-id="0641d-155">Při vytváření uživatelem definovaných výjimek se ujistěte, že metadata pro výjimky jsou k dispozici pro kód, který se spouští vzdáleně.</span><span class="sxs-lookup"><span data-stu-id="0641d-155">When you create user-defined exceptions, ensure that the metadata for the exceptions is available to code that is executing remotely.</span></span>

<span data-ttu-id="0641d-156">Například u implementací rozhraní .NET, které podporují aplikační domény, se může vyskytnout výjimka napříč doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="0641d-156">For example, on .NET implementations that support App Domains, exceptions may occur across App domains.</span></span> <span data-ttu-id="0641d-157">Předpokládejme, že doména aplikace A vytvoří doménu aplikace B, která spustí kód, který vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="0641d-157">Suppose App Domain A creates App Domain B, which executes code that throws an exception.</span></span> <span data-ttu-id="0641d-158">Aby mohla doména aplikace A správně zachytit a zpracovat výjimku, musí být schopna najít sestavení, které obsahuje výjimku vyvolanou aplikační doménou B. Pokud doména aplikace B vyvolá výjimku, která je obsažena v sestavení v rámci jeho základu aplikace, ale ne v rámci databáze aplikace A, domény aplikace A nebude schopna najít výjimku a modul CLR vyvolá výjimku <xref:System.IO.FileNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="0641d-158">For App Domain A to properly catch and handle the exception, it must be able to find the assembly that contains the exception thrown by App Domain B. If App Domain B throws an exception that is contained in an assembly under its application base, but not under App Domain A's application base, App Domain A will not be able to find the exception, and the common language runtime will throw a <xref:System.IO.FileNotFoundException> exception.</span></span> <span data-ttu-id="0641d-159">Této situaci zamezíte tak, že nasadíte sestavení obsahující informace o výjimce dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="0641d-159">To avoid this situation, you can deploy the assembly that contains the exception information in two ways:</span></span>

- <span data-ttu-id="0641d-160">Sestavení umístěte do společného základu cesty aplikace sdíleného oběma doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="0641d-160">Put the assembly into a common application base shared by both app domains.</span></span>

    <span data-ttu-id="0641d-161">\- nebo-</span><span class="sxs-lookup"><span data-stu-id="0641d-161">\- or -</span></span>

- <span data-ttu-id="0641d-162">Pokud domény nesdílejí společný základ cesty aplikace, podepište sestavení obsahující informace o výjimce silným názvem a nasaďte sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="0641d-162">If the domains do not share a common application base, sign the assembly that contains the exception information with a strong name and deploy the assembly into the global assembly cache.</span></span>

## <a name="use-grammatically-correct-error-messages"></a><span data-ttu-id="0641d-163">Použití gramaticky správných chybových zpráv</span><span class="sxs-lookup"><span data-stu-id="0641d-163">Use grammatically correct error messages</span></span>

<span data-ttu-id="0641d-164">Pište jasné věty a zahrňte koncovou interpunkci.</span><span class="sxs-lookup"><span data-stu-id="0641d-164">Write clear sentences and include ending punctuation.</span></span> <span data-ttu-id="0641d-165">Každá věta v řetězci přiřazená vlastnosti <xref:System.Exception.Message?displayProperty=nameWithType> by měla končit tečkou.</span><span class="sxs-lookup"><span data-stu-id="0641d-165">Each sentence in the string assigned to the <xref:System.Exception.Message?displayProperty=nameWithType> property should end in a period.</span></span> <span data-ttu-id="0641d-166">Například "došlo k přetečení tabulky protokolu".</span><span class="sxs-lookup"><span data-stu-id="0641d-166">For example, "The log table has overflowed."</span></span> <span data-ttu-id="0641d-167">by byl vhodný řetězec zprávy.</span><span class="sxs-lookup"><span data-stu-id="0641d-167">would be an appropriate message string.</span></span>

## <a name="include-a-localized-string-message-in-every-exception"></a><span data-ttu-id="0641d-168">Zahrnout do každé výjimky lokalizovanou zprávu řetězce</span><span class="sxs-lookup"><span data-stu-id="0641d-168">Include a localized string message in every exception</span></span>

<span data-ttu-id="0641d-169">Chybová zpráva, kterou uživatel vidí, je odvozena z vlastnosti @no__t 0 výjimky, která byla vyvolána, a nikoli z názvu třídy Exception.</span><span class="sxs-lookup"><span data-stu-id="0641d-169">The error message that the user sees is derived from the <xref:System.Exception.Message?displayProperty=nameWithType> property of the exception that was thrown, and not from the name of the exception class.</span></span> <span data-ttu-id="0641d-170">Obvykle přiřadíte hodnotu vlastnosti <xref:System.Exception.Message?displayProperty=nameWithType> předáním řetězce zprávy do argumentu `message` [konstruktoru výjimky](xref:System.Exception.%23ctor%2A).</span><span class="sxs-lookup"><span data-stu-id="0641d-170">Typically, you assign a value to the <xref:System.Exception.Message?displayProperty=nameWithType>  property by passing the message string to the `message` argument of an [Exception constructor](xref:System.Exception.%23ctor%2A).</span></span>

<span data-ttu-id="0641d-171">Pro lokalizované aplikace byste měli poskytnout lokalizovaný řetězec zprávy pro všechny výjimky, které může vaše aplikace vyvolat.</span><span class="sxs-lookup"><span data-stu-id="0641d-171">For localized applications, you should provide a localized message string for every exception that your application can throw.</span></span> <span data-ttu-id="0641d-172">Soubory prostředků můžete použít k poskytnutí lokalizovaných chybových zpráv.</span><span class="sxs-lookup"><span data-stu-id="0641d-172">You use resource files to provide localized error messages.</span></span> <span data-ttu-id="0641d-173">Informace o lokalizaci aplikací a načítání lokalizovaných řetězců naleznete v následujících článcích:</span><span class="sxs-lookup"><span data-stu-id="0641d-173">For information on localizing applications and retrieving localized strings, see the following articles:</span></span>

- [<span data-ttu-id="0641d-174">Postupy: vytváření uživatelsky definovaných výjimek s lokalizovanými zprávami výjimek</span><span class="sxs-lookup"><span data-stu-id="0641d-174">How to: create user-defined exceptions with localized exception messages</span></span>](how-to-create-localized-exception-messages.md)
- [<span data-ttu-id="0641d-175">Prostředky v desktopových aplikacích</span><span class="sxs-lookup"><span data-stu-id="0641d-175">Resources in Desktop Apps</span></span>](../../framework/resources/index.md) 
- <xref:System.Resources.ResourceManager?displayProperty=nameWithType>

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a><span data-ttu-id="0641d-176">V možnosti vlastní výjimky zadejte podle potřeby další vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0641d-176">In custom exceptions, provide additional properties as needed</span></span>

<span data-ttu-id="0641d-177">Poskytněte další vlastnosti pro výjimku (kromě vlastního řetězce zprávy) pouze v případě, že existuje programový scénář, kde jsou další informace užitečné.</span><span class="sxs-lookup"><span data-stu-id="0641d-177">Provide additional properties for an exception (in addition to the custom message string) only when there's a programmatic scenario where the additional information is useful.</span></span> <span data-ttu-id="0641d-178">Například <xref:System.IO.FileNotFoundException> poskytuje vlastnost <xref:System.IO.FileNotFoundException.FileName>.</span><span class="sxs-lookup"><span data-stu-id="0641d-178">For example, the <xref:System.IO.FileNotFoundException> provides the <xref:System.IO.FileNotFoundException.FileName> property.</span></span>

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a><span data-ttu-id="0641d-179">Umístěte příkazy throw tak, aby trasování zásobníku bylo užitečné.</span><span class="sxs-lookup"><span data-stu-id="0641d-179">Place throw statements so that the stack trace will be helpful</span></span>

<span data-ttu-id="0641d-180">Trasování zásobníku začíná příkazem, kde je vyvolána výjimka a končí v příkazu `catch`, který zachycuje výjimku.</span><span class="sxs-lookup"><span data-stu-id="0641d-180">The stack trace begins at the statement where the exception is thrown and ends at the `catch` statement that catches the exception.</span></span>

## <a name="use-exception-builder-methods"></a><span data-ttu-id="0641d-181">Použití metod Tvůrce výjimek</span><span class="sxs-lookup"><span data-stu-id="0641d-181">Use exception builder methods</span></span>

<span data-ttu-id="0641d-182">Pro třídu je běžné vyvolat stejnou výjimku z různých míst v rámci příslušné implementace.</span><span class="sxs-lookup"><span data-stu-id="0641d-182">It is common for a class to throw the same exception from different places in its implementation.</span></span> <span data-ttu-id="0641d-183">Abyste zabránili nadbytečnému kódu, použijte pomocné metody k vytvoření výjimky a vrácení výjimky.</span><span class="sxs-lookup"><span data-stu-id="0641d-183">To avoid excessive code, use helper methods that create the exception and return it.</span></span> <span data-ttu-id="0641d-184">Příklad:</span><span class="sxs-lookup"><span data-stu-id="0641d-184">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#6](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]

<span data-ttu-id="0641d-185">V některých případech je vhodnější použít konstruktor výjimky k sestavení výjimky.</span><span class="sxs-lookup"><span data-stu-id="0641d-185">In some cases, it's more appropriate to use the exception's constructor to build the exception.</span></span> <span data-ttu-id="0641d-186">Příkladem je globální třída výjimek, jako je například <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="0641d-186">An example is a global exception class such as <xref:System.ArgumentException>.</span></span>

## <a name="restore-state-when-methods-dont-complete-due-to-exceptions"></a><span data-ttu-id="0641d-187">Obnovit stav, když se metody nedokončují kvůli výjimkám</span><span class="sxs-lookup"><span data-stu-id="0641d-187">Restore state when methods don't complete due to exceptions</span></span>

<span data-ttu-id="0641d-188">Volající by měl předpokládat, že při vyvolání výjimky z metody nedojde k žádným vedlejším účinkům.</span><span class="sxs-lookup"><span data-stu-id="0641d-188">Callers should be able to assume that there are no side effects when an exception is thrown from a method.</span></span> <span data-ttu-id="0641d-189">Například pokud máte kód, který přenáší peníze odebráním z jednoho účtu a uložením do jiného účtu, a při provádění zálohy dojde k výjimce, nechcete, aby stažení zůstalo v platnosti.</span><span class="sxs-lookup"><span data-stu-id="0641d-189">For example, if you have code that transfers money by withdrawing from one account and depositing in another account, and an exception is thrown while executing the deposit, you don't want the withdrawal to remain in effect.</span></span>

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

<span data-ttu-id="0641d-190">Výše uvedená metoda přímo nevyvolává žádné výjimky, ale musí být zapsána defensively, aby v případě, že operace vkladu nebyla úspěšná, je zrušení vrácení zpět.</span><span class="sxs-lookup"><span data-stu-id="0641d-190">The method above does not directly throw any exceptions, but must be written defensively so that if the deposit operation fails, the withdrawal is reversed.</span></span>

<span data-ttu-id="0641d-191">Jedním ze způsobů, jak tuto situaci zpracovat, je zachytit jakékoli výjimky vyvolané vkladovou transakcí a vrátit zpět odstoupení.</span><span class="sxs-lookup"><span data-stu-id="0641d-191">One way to handle this situation is to catch any exceptions thrown by the deposit transaction and roll back the withdrawal.</span></span>

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

<span data-ttu-id="0641d-192">Tento příklad ukazuje použití `throw` k opětovnému vyvolání původní výjimky, která může usnadnit volajícím zobrazit skutečnou příčinu problému bez nutnosti prozkoumávat vlastnost <xref:System.Exception.InnerException>.</span><span class="sxs-lookup"><span data-stu-id="0641d-192">This example illustrates the use of `throw` to re-throw the original exception, which can make it easier for callers to see the real cause of the problem without having to examine the <xref:System.Exception.InnerException> property.</span></span> <span data-ttu-id="0641d-193">Alternativou je vyvolat novou výjimku a zahrnout původní výjimku jako vnitřní výjimku:</span><span class="sxs-lookup"><span data-stu-id="0641d-193">An alternative is to throw a new exception and include the original exception as the inner exception:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0641d-194">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0641d-194">See also</span></span>

- [<span data-ttu-id="0641d-195">Výjimky</span><span class="sxs-lookup"><span data-stu-id="0641d-195">Exceptions</span></span>](index.md)
