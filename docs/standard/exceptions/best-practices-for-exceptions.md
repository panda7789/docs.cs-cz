---
title: Doporučené postupy pro výjimky
ms.date: 12/05.2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
ms.openlocfilehash: fb2da0d37a3c72941e9ffdac52a6fdf24ec71b3a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149585"
---
# <a name="best-practices-for-exceptions"></a><span data-ttu-id="2bf48-102">Doporučené postupy pro výjimky</span><span class="sxs-lookup"><span data-stu-id="2bf48-102">Best practices for exceptions</span></span>

<span data-ttu-id="2bf48-103">Za účelem zamezení pádu aplikace zpracovává dobře navržená aplikace výjimky a chyby.</span><span class="sxs-lookup"><span data-stu-id="2bf48-103">A well-designed app handles exceptions and errors to prevent app crashes.</span></span> <span data-ttu-id="2bf48-104">Tato část popisuje osvědčené postupy pro zpracování a vytváření výjimek.</span><span class="sxs-lookup"><span data-stu-id="2bf48-104">This section describes best practices for handling and creating exceptions.</span></span>

## <a name="use-trycatchfinally-blocks-to-recover-from-errors-or-release-resources"></a><span data-ttu-id="2bf48-105">Pomocí konstrukce try/catch/finally bloky zotavit z chyb nebo uvolnění prostředků</span><span class="sxs-lookup"><span data-stu-id="2bf48-105">Use try/catch/finally blocks to recover from errors or release resources</span></span>

<span data-ttu-id="2bf48-106">Použití `try` / `catch` okolo kódu, který může potenciálně generovat výjimku ***a*** kódu můžete obnovit z této výjimky.</span><span class="sxs-lookup"><span data-stu-id="2bf48-106">Use `try`/`catch` blocks around code that can potentially generate an exception ***and*** your code can recover from that exception.</span></span> <span data-ttu-id="2bf48-107">V `catch` blokuje vždy nutné výjimky seřazovat od nejvíce odvozené na nejméně odvozené.</span><span class="sxs-lookup"><span data-stu-id="2bf48-107">In `catch` blocks, always order exceptions from the most derived to the least derived.</span></span> <span data-ttu-id="2bf48-108">Všechny výjimky jsou odvozeny z <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="2bf48-108">All exceptions derive from <xref:System.Exception>.</span></span> <span data-ttu-id="2bf48-109">Více odvozeného výjimky nejsou zpracovávány klauzule catch, který předchází klauzuli catch. výjimky základní třídy.</span><span class="sxs-lookup"><span data-stu-id="2bf48-109">More derived exceptions are not handled by a catch clause that is preceded by a catch clause for a base exception class.</span></span> <span data-ttu-id="2bf48-110">Pokud váš kód nelze obnovit z výjimky, nezachycujte tuto výjimku.</span><span class="sxs-lookup"><span data-stu-id="2bf48-110">When your code cannot recover from an exception, don't catch that exception.</span></span> <span data-ttu-id="2bf48-111">Povolte další metody v zásobníku volání, pokud je to možné obnovit.</span><span class="sxs-lookup"><span data-stu-id="2bf48-111">Enable methods further up the call stack to recover if possible.</span></span>

<span data-ttu-id="2bf48-112">Vyčistěte prostředky přidělené s oběma `using` příkazy, nebo `finally` bloky.</span><span class="sxs-lookup"><span data-stu-id="2bf48-112">Clean up resources allocated with either `using` statements, or `finally` blocks.</span></span> <span data-ttu-id="2bf48-113">Preferovat `using` příkazy automaticky vyčistit prostředky, pokud jsou výjimky vyvolány.</span><span class="sxs-lookup"><span data-stu-id="2bf48-113">Prefer `using` statements to automatically clean up resources when exceptions are thrown.</span></span> <span data-ttu-id="2bf48-114">Použití `finally` bloky chcete vyčistit prostředky, které Neimplementujte <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="2bf48-114">Use `finally` blocks to clean up resources that don't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="2bf48-115">V kódu `finally` claus je téměř vždy spuštěn i v případě, že jsou výjimky vyvolány.</span><span class="sxs-lookup"><span data-stu-id="2bf48-115">Code in a `finally` claus is almost always executed even when exceptions are thrown.</span></span>

## <a name="handle-common-conditions-without-throwing-exceptions"></a><span data-ttu-id="2bf48-116">Zpracování běžných podmínek bez vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="2bf48-116">Handle common conditions without throwing exceptions</span></span>

<span data-ttu-id="2bf48-117">Podmínky, které by mohly nastat, ale může být spuštění výjimky, zvažte jejich zpracování tak, aby se vyhnete výjimku.</span><span class="sxs-lookup"><span data-stu-id="2bf48-117">For conditions that are likely to occur but might trigger an exception, consider handling them in a way that will avoid the exception.</span></span> <span data-ttu-id="2bf48-118">Například pokud se pokusíte uzavřít připojení, který je už zavřený, získáte `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="2bf48-118">For example, if you try to close a connection that is already closed, you'll get an `InvalidOperationException`.</span></span> <span data-ttu-id="2bf48-119">Který můžete vyhnout použitím `if` příkaz a zkontrolujte stav připojení před dalším pokusem ho zavřít.</span><span class="sxs-lookup"><span data-stu-id="2bf48-119">You can avoid that by using an `if` statement to check the connection state before trying to close it.</span></span>

[!code-cpp[Conceptual.Exception.Handling#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]  

<span data-ttu-id="2bf48-120">Pokud se nezaregistrují stav připojení před zavřením, můžete zachytit `InvalidOperationException` výjimky.</span><span class="sxs-lookup"><span data-stu-id="2bf48-120">If you don't check connection state before closing, you can catch the `InvalidOperationException` exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]  

<span data-ttu-id="2bf48-121">Metoda zvolit, závisí na očekáváte, jak často má k události docházet.</span><span class="sxs-lookup"><span data-stu-id="2bf48-121">The method to choose depends on how often you expect the event to occur.</span></span>

- <span data-ttu-id="2bf48-122">Použijte zpracování výjimek, pokud k události nedochází velmi často, tzn. pokud k události dochází výjimečně a značí chybu (jako například neočekávaný konec souboru).</span><span class="sxs-lookup"><span data-stu-id="2bf48-122">Use exception handling if the event doesn't occur very often, that is, if the event is truly exceptional and indicates an error (such as an unexpected end-of-file).</span></span> <span data-ttu-id="2bf48-123">Při používání zpracování výjimek je za běžných podmínek provedena menší část kódu.</span><span class="sxs-lookup"><span data-stu-id="2bf48-123">When you use exception handling, less code is executed in normal conditions.</span></span>

- <span data-ttu-id="2bf48-124">Pokud k události dochází rutinně a může být považována za součást běžného provedení Zkontrolujte chybové stavy v kódu.</span><span class="sxs-lookup"><span data-stu-id="2bf48-124">Check for error conditions in code if the event happens routinely and could be considered part of normal execution.</span></span> <span data-ttu-id="2bf48-125">Při kontrole běžné chybové stavy, menší část kódu je provést, protože byste se vyhnout výjimky.</span><span class="sxs-lookup"><span data-stu-id="2bf48-125">When you check for common error conditions, less code is executed because you avoid exceptions.</span></span>

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a><span data-ttu-id="2bf48-126">Třídy Navrhujte tak, aby výjimky se můžete vyhnout.</span><span class="sxs-lookup"><span data-stu-id="2bf48-126">Design classes so that exceptions can be avoided</span></span>

<span data-ttu-id="2bf48-127">Třída může poskytnout metody nebo vlastnosti, které vám umožní vyhnout volání, která se aktivuje výjimku.</span><span class="sxs-lookup"><span data-stu-id="2bf48-127">A class can provide methods or properties that enable you to avoid making a call that would trigger an exception.</span></span> <span data-ttu-id="2bf48-128">Například <xref:System.IO.FileStream> třída poskytuje metody, které pomáhají určit, zda bylo dosaženo konce souboru.</span><span class="sxs-lookup"><span data-stu-id="2bf48-128">For example, a <xref:System.IO.FileStream> class provides methods that help determine whether the end of the file has been reached.</span></span> <span data-ttu-id="2bf48-129">Ty je možné, aby výjimka, která je vyvolána, pokud čtení za koncem souboru.</span><span class="sxs-lookup"><span data-stu-id="2bf48-129">These can be used to avoid the exception that is thrown if you read past the end of the file.</span></span> <span data-ttu-id="2bf48-130">Následující příklad znázorňuje způsob čtení do konce souboru bez vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="2bf48-130">The following example shows how to read to the end of a file without triggering an exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]  

<span data-ttu-id="2bf48-131">Jiný způsob, jak zabránit výjimky je vrátit `null` pro nejběžnější případy chyb namísto vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="2bf48-131">Another way to avoid exceptions is to return `null` for extremely common error cases instead of throwing an exception.</span></span> <span data-ttu-id="2bf48-132">Za nejběžnější případ chyby lze považovat běžný tok řízení.</span><span class="sxs-lookup"><span data-stu-id="2bf48-132">An extremely common error case can be considered normal flow of control.</span></span> <span data-ttu-id="2bf48-133">Vrácením `null` v těchto případech minimalizujete dopad výkonu pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2bf48-133">By returning `null` in these cases, you minimize the performance impact to an app.</span></span>

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a><span data-ttu-id="2bf48-134">Vyvolat výjimky místo vrácení chybový kód</span><span class="sxs-lookup"><span data-stu-id="2bf48-134">Throw exceptions instead of returning an error code</span></span>

<span data-ttu-id="2bf48-135">Výjimky Ujistěte se, že selhání nedojde protože volání, že kód nezaškrtli návratový kód.</span><span class="sxs-lookup"><span data-stu-id="2bf48-135">Exceptions ensure that failures do not go unnoticed because calling code didn't check a return code.</span></span>

## <a name="use-the-predefined-net-exception-types"></a><span data-ttu-id="2bf48-136">Použijte předdefinované typy výjimek .NET</span><span class="sxs-lookup"><span data-stu-id="2bf48-136">Use the predefined .NET exception types</span></span>

<span data-ttu-id="2bf48-137">Zavádí novou třídu výjimek pouze v případě, že neplatí předdefinované jeden.</span><span class="sxs-lookup"><span data-stu-id="2bf48-137">Introduce a new exception class only when a predefined one doesn't apply.</span></span> <span data-ttu-id="2bf48-138">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2bf48-138">For example:</span></span>

- <span data-ttu-id="2bf48-139">Vyvolání <xref:System.InvalidOperationException> výjimku, pokud vlastnost set nebo metoda volání není vhodné aktuální stav objektu.</span><span class="sxs-lookup"><span data-stu-id="2bf48-139">Throw an <xref:System.InvalidOperationException> exception if a property set or method call is not appropriate given the object's current state.</span></span>

- <span data-ttu-id="2bf48-140">Vyvolání <xref:System.ArgumentException> výjimky nebo jeden z předdefinovaných tříd, které jsou odvozeny z <xref:System.ArgumentException> Pokud jsou předány neplatné parametry.</span><span class="sxs-lookup"><span data-stu-id="2bf48-140">Throw an <xref:System.ArgumentException> exception or one of the predefined classes that derive from <xref:System.ArgumentException> if invalid parameters are passed.</span></span>

## <a name="end-exception-class-names-with-the-word-exception"></a><span data-ttu-id="2bf48-141">Názvy tříd výjimek ukončujte slovem End `Exception`</span><span class="sxs-lookup"><span data-stu-id="2bf48-141">End exception class names with the word `Exception`</span></span>

<span data-ttu-id="2bf48-142">Při vlastní výjimky je nezbytné, pojmenujte ji odpovídajícím způsobem a odvozovat z <xref:System.Exception> třídy.</span><span class="sxs-lookup"><span data-stu-id="2bf48-142">When a custom exception is necessary, name it appropriately and derive it from the <xref:System.Exception> class.</span></span> <span data-ttu-id="2bf48-143">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2bf48-143">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]  

## <a name="include-three-constructors-in-custom-exception-classes"></a><span data-ttu-id="2bf48-144">Zahrnout tři konstruktory ve třídách vlastní výjimky</span><span class="sxs-lookup"><span data-stu-id="2bf48-144">Include three constructors in custom exception classes</span></span>

<span data-ttu-id="2bf48-145">Použijte aspoň tři běžné konstruktory při vytváření vlastních tříd výjimek: výchozí konstruktor, konstruktor, který přijímá řetězcovou zprávu a konstruktor, který přijímá řetězcovou zprávu a vnitřní výjimku.</span><span class="sxs-lookup"><span data-stu-id="2bf48-145">Use at least the three common constructors when creating your own exception classes: the default constructor, a constructor that takes a string message, and a constructor that takes a string message and an inner exception.</span></span>

* <span data-ttu-id="2bf48-146"><xref:System.Exception.%23ctor>, který používá výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2bf48-146"><xref:System.Exception.%23ctor>, which uses default values.</span></span>
  
* <span data-ttu-id="2bf48-147"><xref:System.Exception.%23ctor%28System.String%29>, která přijímá řetězcovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="2bf48-147"><xref:System.Exception.%23ctor%28System.String%29>, which accepts a string message.</span></span>  
  
* <span data-ttu-id="2bf48-148"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, která přijímá řetězcovou zprávu a vnitřní výjimku.</span><span class="sxs-lookup"><span data-stu-id="2bf48-148"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, which accepts a string message and an inner exception.</span></span>  
  
<span data-ttu-id="2bf48-149">Příklad najdete v tématu [jak: Vytvořit uživatelsky definovaných výjimek](how-to-create-user-defined-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="2bf48-149">For an example, see [How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).</span></span>

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a><span data-ttu-id="2bf48-150">Ujistěte se, že data výjimky je k dispozici, když je kód spuštěn vzdáleně</span><span class="sxs-lookup"><span data-stu-id="2bf48-150">Ensure that exception data is available when code executes remotely</span></span>

<span data-ttu-id="2bf48-151">Při vytváření uživatelsky definovaných výjimek, ujistěte se, že je k dispozici pro kód, který je prováděn vzdáleně metadata pro výjimky.</span><span class="sxs-lookup"><span data-stu-id="2bf48-151">When you create user-defined exceptions, ensure that the metadata for the exceptions is available to code that is executing remotely.</span></span> 

<span data-ttu-id="2bf48-152">Například na implementace .NET, které podporují domén aplikace, může dojít k výjimkám mezi doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="2bf48-152">For example, on .NET implementations that support App Domains, exceptions may occur across App domains.</span></span> <span data-ttu-id="2bf48-153">Předpokládejme, že doména aplikace A vytvoří doménu aplikace B, která spustí kód, který vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="2bf48-153">Suppose App Domain A creates App Domain B, which executes code that throws an exception.</span></span> <span data-ttu-id="2bf48-154">Doména aplikace A k správně zachytila a zpracovala výjimku musí být schopna najít sestavení obsahující výjimku domény aplikace b Pokud doména aplikace B vyvolá výjimku, která je součástí sestavení v rámci její základ cesty aplikace, ale není pod základ cesty aplikace příslušné domény aplikace, doména aplikace A nebudete moci najít výjimku a modul common language runtime vyvolá výjimku <xref:System.IO.FileNotFoundException> výjimky.</span><span class="sxs-lookup"><span data-stu-id="2bf48-154">For App Domain A to properly catch and handle the exception, it must be able to find the assembly that contains the exception thrown by App Domain B. If App Domain B throws an exception that is contained in an assembly under its application base, but not under App Domain A's application base, App Domain A will not be able to find the exception, and the common language runtime will throw a <xref:System.IO.FileNotFoundException> exception.</span></span> <span data-ttu-id="2bf48-155">Této situaci zamezíte tak, že nasadíte sestavení obsahující informace o výjimce dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="2bf48-155">To avoid this situation, you can deploy the assembly that contains the exception information in two ways:</span></span>

- <span data-ttu-id="2bf48-156">Sestavení umístěte do společného základu cesty aplikace sdíleného oběma doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="2bf48-156">Put the assembly into a common application base shared by both app domains.</span></span>

    <span data-ttu-id="2bf48-157">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="2bf48-157">\- or -</span></span>

- <span data-ttu-id="2bf48-158">Pokud domény nesdílejí společný základ cesty aplikace, podepište sestavení obsahující informace o výjimce silným názvem a nasaďte sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="2bf48-158">If the domains do not share a common application base, sign the assembly that contains the exception information with a strong name and deploy the assembly into the global assembly cache.</span></span>

## <a name="use-grammatically-correct-error-messages"></a><span data-ttu-id="2bf48-159">Používejte gramaticky správné chybové zprávy</span><span class="sxs-lookup"><span data-stu-id="2bf48-159">Use grammatically correct error messages</span></span>

<span data-ttu-id="2bf48-160">Zápis vymazat věty a zahrnout koncové interpunkce.</span><span class="sxs-lookup"><span data-stu-id="2bf48-160">Write clear sentences and include ending punctuation.</span></span> <span data-ttu-id="2bf48-161">Jednotlivé věty v řetězci přiřazené <xref:System.Exception.Message?displayProperty=nameWithType> vlastnost by měla končit tečkou.</span><span class="sxs-lookup"><span data-stu-id="2bf48-161">Each sentence in the string assigned to the <xref:System.Exception.Message?displayProperty=nameWithType> property should end in a period.</span></span> <span data-ttu-id="2bf48-162">Například "The log table došlo k přetečení."</span><span class="sxs-lookup"><span data-stu-id="2bf48-162">For example, "The log table has overflowed."</span></span> <span data-ttu-id="2bf48-163">by být řetězec odpovídající zprávu.</span><span class="sxs-lookup"><span data-stu-id="2bf48-163">would be an appropriate message string.</span></span>

## <a name="include-a-localized-string-message-in-every-exception"></a><span data-ttu-id="2bf48-164">Přiložit zprávu lokalizované řetězce v každé výjimce</span><span class="sxs-lookup"><span data-stu-id="2bf48-164">Include a localized string message in every exception</span></span>

<span data-ttu-id="2bf48-165">Chybová zpráva, která se uživateli je odvozen z <xref:System.Exception.Message?displayProperty=nameWithType> vlastnost, která byla vyvolána výjimka a nikoli z názvu třídy výjimek.</span><span class="sxs-lookup"><span data-stu-id="2bf48-165">The error message that the user sees is derived from the <xref:System.Exception.Message?displayProperty=nameWithType> property of the exception that was thrown, and not from the name of the exception class.</span></span> <span data-ttu-id="2bf48-166">Obvykle přiřadit hodnotu <xref:System.Exception.Message?displayProperty=nameWithType> vlastnost tím, že předáte řetězec zprávy `message` argument [výjimky konstruktoru](xref:System.Exception.%23ctor%2A).</span><span class="sxs-lookup"><span data-stu-id="2bf48-166">Typically, you assign a value to the <xref:System.Exception.Message?displayProperty=nameWithType>  property by passing the message string to the `message` argument of an [Exception constructor](xref:System.Exception.%23ctor%2A).</span></span> 

<span data-ttu-id="2bf48-167">V případě lokalizovaných aplikací by měly poskytnout řetězce lokalizované zpráv pro každou výjimku, kterou vaše aplikace může vyvolat.</span><span class="sxs-lookup"><span data-stu-id="2bf48-167">For localized applications, you should provide a localized message string for every exception that your application can throw.</span></span> <span data-ttu-id="2bf48-168">Soubory prostředků vám poskytují lokalizované chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="2bf48-168">You use resource files to provide localized error messages.</span></span> <span data-ttu-id="2bf48-169">Informace o lokalizaci aplikací a načítání lokalizovaných řetězců naleznete v tématu [prostředky v desktopových aplikací](../../framework/resources/index.md) a <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2bf48-169">For information on localizing applications and retrieving localized strings, see [Resources in Desktop Apps](../../framework/resources/index.md) and <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span>

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a><span data-ttu-id="2bf48-170">Vlastní výjimky zadejte další vlastnosti podle potřeby</span><span class="sxs-lookup"><span data-stu-id="2bf48-170">In custom exceptions, provide additional properties as needed</span></span>

<span data-ttu-id="2bf48-171">Zadejte další vlastnosti pro výjimku (kromě řetězec vlastní zprávu) pouze v případě, že existuje programový scénář, kde Další informace jsou užitečné.</span><span class="sxs-lookup"><span data-stu-id="2bf48-171">Provide additional properties for an exception (in addition to the custom message string) only when there's a programmatic scenario where the additional information is useful.</span></span> <span data-ttu-id="2bf48-172">Například <xref:System.IO.FileNotFoundException> poskytuje <xref:System.IO.FileNotFoundException.FileName> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2bf48-172">For example, the <xref:System.IO.FileNotFoundException> provides the <xref:System.IO.FileNotFoundException.FileName> property.</span></span>

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a><span data-ttu-id="2bf48-173">Příkaz throw místo tak, že bude užitečné trasování zásobníku</span><span class="sxs-lookup"><span data-stu-id="2bf48-173">Place throw statements so that the stack trace will be helpful</span></span>

<span data-ttu-id="2bf48-174">Trasování zásobníků začíná u příkazu, kde je vyvolána výjimka a končí `catch` příkaz, který zachytí výjimku.</span><span class="sxs-lookup"><span data-stu-id="2bf48-174">The stack trace begins at the statement where the exception is thrown and ends at the `catch` statement that catches the exception.</span></span>

## <a name="use-exception-builder-methods"></a><span data-ttu-id="2bf48-175">Použijte metody tvůrce výjimky</span><span class="sxs-lookup"><span data-stu-id="2bf48-175">Use exception builder methods</span></span>

<span data-ttu-id="2bf48-176">Pro třídu je běžné vyvolat stejnou výjimku z různých míst v rámci příslušné implementace.</span><span class="sxs-lookup"><span data-stu-id="2bf48-176">It is common for a class to throw the same exception from different places in its implementation.</span></span> <span data-ttu-id="2bf48-177">Abyste zabránili nadbytečnému kódu, použijte pomocné metody k vytvoření výjimky a vrácení výjimky.</span><span class="sxs-lookup"><span data-stu-id="2bf48-177">To avoid excessive code, use helper methods that create the exception and return it.</span></span> <span data-ttu-id="2bf48-178">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2bf48-178">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]  
  
<span data-ttu-id="2bf48-179">V některých případech je vhodnější použít konstruktor k vytvoření výjimky.</span><span class="sxs-lookup"><span data-stu-id="2bf48-179">In some cases, it's more appropriate to use the exception's constructor to build the exception.</span></span> <span data-ttu-id="2bf48-180">Příkladem je třídy globálních výjimek, jako <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="2bf48-180">An example is a global exception class such as <xref:System.ArgumentException>.</span></span>

## <a name="restore-state-when-methods-dont-complete-due-to-exceptions"></a><span data-ttu-id="2bf48-181">Obnovit stav, když metody není dokončit z důvodu výjimky</span><span class="sxs-lookup"><span data-stu-id="2bf48-181">Restore state when methods don't complete due to exceptions</span></span>

<span data-ttu-id="2bf48-182">Volající by měl předpokládat, že při vyvolání výjimky z metody nedojde k žádným vedlejším účinkům.</span><span class="sxs-lookup"><span data-stu-id="2bf48-182">Callers should be able to assume that there are no side effects when an exception is thrown from a method.</span></span> <span data-ttu-id="2bf48-183">Například pokud máte kód, který převede peníze odebrání z jednoho účtu a uložení do jiného účtu, a je vyvolána výjimka při provádění uložení, nechcete stažení zůstávají v platnosti.</span><span class="sxs-lookup"><span data-stu-id="2bf48-183">For example, if you have code that transfers money by withdrawing from one account and depositing in another account, and an exception is thrown while executing the deposit, you don't want the withdrawal to remain in effect.</span></span>

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect. 
    to.Deposit(amount);
}
```

<span data-ttu-id="2bf48-184">Výše uvedené metody přímo nevyvolá žádné výjimky, ale musí být napsaný defenzivně, takže pokud se nezdaří operace uložení, stažení je obrácený.</span><span class="sxs-lookup"><span data-stu-id="2bf48-184">The method above does not directly throw any exceptions, but must be written defensively so that if the deposit operation fails, the withdrawal is reversed.</span></span>

<span data-ttu-id="2bf48-185">Jedním ze způsobů tuto situaci je zachytit žádné výjimky vyvolané uložení transakce a vrátit zpět stažení.</span><span class="sxs-lookup"><span data-stu-id="2bf48-185">One way to handle this situation is to catch any exceptions thrown by the deposit transaction and roll back the withdrawal.</span></span>

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

<span data-ttu-id="2bf48-186">Tento příklad ukazuje použití metody `throw` pro opětovné vyvolání původní výjimku, která usnadní volajícím zobrazila skutečná příčinu problému bez nutnosti k prozkoumání <xref:System.Exception.InnerException> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2bf48-186">This example illustrates the use of `throw` to re-throw the original exception, which can make it easier for callers to see the real cause of the problem without having to examine the <xref:System.Exception.InnerException> property.</span></span> <span data-ttu-id="2bf48-187">Alternativou je novou výjimku a zahrnují původní výjimku jako vnitřní výjimka:</span><span class="sxs-lookup"><span data-stu-id="2bf48-187">An alternative is to throw a new exception and include the original exception as the inner exception:</span></span>

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new TransferFundsException("Withdrawal failed", innerException: ex)
    {
        From = from,
        To = to,
        Amount = amount
    };
}
```

## <a name="see-also"></a><span data-ttu-id="2bf48-188">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2bf48-188">See also</span></span>

- [<span data-ttu-id="2bf48-189">Výjimky</span><span class="sxs-lookup"><span data-stu-id="2bf48-189">Exceptions</span></span>](index.md)
