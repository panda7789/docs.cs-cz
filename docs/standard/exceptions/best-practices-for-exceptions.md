---
title: Doporučené postupy pro výjimky
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee61d01acbf9c409eaedc04ff3e949908e1d595e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44225133"
---
# <a name="best-practices-for-exceptions"></a><span data-ttu-id="6398f-102">Doporučené postupy pro výjimky</span><span class="sxs-lookup"><span data-stu-id="6398f-102">Best practices for exceptions</span></span>

<span data-ttu-id="6398f-103">Za účelem zamezení pádu aplikace zpracovává dobře navržená aplikace výjimky a chyby.</span><span class="sxs-lookup"><span data-stu-id="6398f-103">A well-designed app handles exceptions and errors to prevent app crashes.</span></span> <span data-ttu-id="6398f-104">Tato část popisuje osvědčené postupy pro zpracování a vytváření výjimek.</span><span class="sxs-lookup"><span data-stu-id="6398f-104">This section describes best practices for handling and creating exceptions.</span></span>

## <a name="use-trycatchfinally-blocks"></a><span data-ttu-id="6398f-105">Pomocí konstrukce try/catch/finally bloky</span><span class="sxs-lookup"><span data-stu-id="6398f-105">Use try/catch/finally blocks</span></span>

<span data-ttu-id="6398f-106">Použití `try` / `catch` / `finally` okolo kódu, který může potenciálně generovat výjimku.</span><span class="sxs-lookup"><span data-stu-id="6398f-106">Use `try`/`catch`/`finally` blocks around code that can potentially generate an exception.</span></span> 

<span data-ttu-id="6398f-107">V `catch` blokuje vždy nutné výjimky seřazovat od nejkonkrétnější po nejméně konkrétní.</span><span class="sxs-lookup"><span data-stu-id="6398f-107">In `catch` blocks, always order exceptions from the most specific to the least specific.</span></span>

<span data-ttu-id="6398f-108">Použití `finally` bloku pro vyčištění prostředků, zda lze obnovit nebo ne.</span><span class="sxs-lookup"><span data-stu-id="6398f-108">Use a `finally` block to clean up resources, whether you can recover or not.</span></span>

## <a name="handle-common-conditions-without-throwing-exceptions"></a><span data-ttu-id="6398f-109">Zpracování běžných podmínek bez vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="6398f-109">Handle common conditions without throwing exceptions</span></span>

<span data-ttu-id="6398f-110">Podmínky, které by mohly nastat, ale může být spuštění výjimky, zvažte jejich zpracování tak, aby se vyhnete výjimku.</span><span class="sxs-lookup"><span data-stu-id="6398f-110">For conditions that are likely to occur but might trigger an exception, consider handling them in a way that will avoid the exception.</span></span> <span data-ttu-id="6398f-111">Například pokud se pokusíte uzavřít připojení, který je už zavřený, získáte `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="6398f-111">For example, if you try to close a connection that is already closed, you'll get an `InvalidOperationException`.</span></span> <span data-ttu-id="6398f-112">Který můžete vyhnout použitím `if` příkaz a zkontrolujte stav připojení před dalším pokusem ho zavřít.</span><span class="sxs-lookup"><span data-stu-id="6398f-112">You can avoid that by using an `if` statement to check the connection state before trying to close it.</span></span>

[!code-cpp[Conceptual.Exception.Handling#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]  

<span data-ttu-id="6398f-113">Pokud se nezaregistrují stav připojení před zavřením, můžete zachytit `InvalidOperationException` výjimky.</span><span class="sxs-lookup"><span data-stu-id="6398f-113">If you don't check connection state before closing, you can catch the `InvalidOperationException` exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]  

<span data-ttu-id="6398f-114">Metoda zvolit, závisí na očekáváte, jak často má k události docházet.</span><span class="sxs-lookup"><span data-stu-id="6398f-114">The method to choose depends on how often you expect the event to occur.</span></span>

- <span data-ttu-id="6398f-115">Použijte zpracování výjimek, pokud k události nedochází velmi často, tzn. pokud k události dochází výjimečně a značí chybu (jako například neočekávaný konec souboru).</span><span class="sxs-lookup"><span data-stu-id="6398f-115">Use exception handling if the event doesn't occur very often, that is, if the event is truly exceptional and indicates an error (such as an unexpected end-of-file).</span></span> <span data-ttu-id="6398f-116">Při používání zpracování výjimek je za běžných podmínek provedena menší část kódu.</span><span class="sxs-lookup"><span data-stu-id="6398f-116">When you use exception handling, less code is executed in normal conditions.</span></span>

- <span data-ttu-id="6398f-117">Pokud k události dochází rutinně a může být považována za součást běžného provedení Zkontrolujte chybové stavy v kódu.</span><span class="sxs-lookup"><span data-stu-id="6398f-117">Check for error conditions in code if the event happens routinely and could be considered part of normal execution.</span></span> <span data-ttu-id="6398f-118">Při kontrole běžné chybové stavy, menší část kódu je provést, protože byste se vyhnout výjimky.</span><span class="sxs-lookup"><span data-stu-id="6398f-118">When you check for common error conditions, less code is executed because you avoid exceptions.</span></span>

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a><span data-ttu-id="6398f-119">Třídy Navrhujte tak, aby výjimky se můžete vyhnout.</span><span class="sxs-lookup"><span data-stu-id="6398f-119">Design classes so that exceptions can be avoided</span></span>

<span data-ttu-id="6398f-120">Třída může poskytnout metody nebo vlastnosti, které vám umožní vyhnout volání, která se aktivuje výjimku.</span><span class="sxs-lookup"><span data-stu-id="6398f-120">A class can provide methods or properties that enable you to avoid making a call that would trigger an exception.</span></span> <span data-ttu-id="6398f-121">Například <xref:System.IO.FileStream> třída poskytuje metody, které pomáhají určit, zda bylo dosaženo konce souboru.</span><span class="sxs-lookup"><span data-stu-id="6398f-121">For example, a <xref:System.IO.FileStream> class provides methods that help determine whether the end of the file has been reached.</span></span> <span data-ttu-id="6398f-122">Ty je možné, aby výjimka, která je vyvolána, pokud čtení za koncem souboru.</span><span class="sxs-lookup"><span data-stu-id="6398f-122">These can be used to avoid the exception that is thrown if you read past the end of the file.</span></span> <span data-ttu-id="6398f-123">Následující příklad znázorňuje způsob čtení do konce souboru bez vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="6398f-123">The following example shows how to read to the end of a file without triggering an exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]  

<span data-ttu-id="6398f-124">Jiný způsob, jak zabránit výjimky je k vrácení hodnoty null pro nejběžnější případy chyb namísto vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="6398f-124">Another way to avoid exceptions is to return null for extremely common error cases instead of throwing an exception.</span></span> <span data-ttu-id="6398f-125">Za nejběžnější případ chyby lze považovat běžný tok řízení.</span><span class="sxs-lookup"><span data-stu-id="6398f-125">An extremely common error case can be considered normal flow of control.</span></span> <span data-ttu-id="6398f-126">Vrácením hodnoty null v těchto případech minimalizujete dopad výkonu pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6398f-126">By returning null in these cases, you minimize the performance impact to an app.</span></span>

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a><span data-ttu-id="6398f-127">Vyvolat výjimky místo vrácení chybový kód</span><span class="sxs-lookup"><span data-stu-id="6398f-127">Throw exceptions instead of returning an error code</span></span>

<span data-ttu-id="6398f-128">Výjimky Ujistěte se, že selhání nedojde protože volání, že kód nezaškrtli návratový kód.</span><span class="sxs-lookup"><span data-stu-id="6398f-128">Exceptions ensure that failures do not go unnoticed because calling code didn't check a return code.</span></span> 

## <a name="use-the-predefined-net-exception-types"></a><span data-ttu-id="6398f-129">Použijte předdefinované typy výjimek .NET</span><span class="sxs-lookup"><span data-stu-id="6398f-129">Use the predefined .NET exception types</span></span>

<span data-ttu-id="6398f-130">Zavádí novou třídu výjimek pouze v případě, že neplatí předdefinované jeden.</span><span class="sxs-lookup"><span data-stu-id="6398f-130">Introduce a new exception class only when a predefined one doesn't apply.</span></span> <span data-ttu-id="6398f-131">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6398f-131">For example:</span></span>

- <span data-ttu-id="6398f-132">Vyvolání <xref:System.InvalidOperationException> výjimku, pokud vlastnost set nebo metoda volání není vhodné aktuální stav objektu.</span><span class="sxs-lookup"><span data-stu-id="6398f-132">Throw an <xref:System.InvalidOperationException> exception if a property set or method call is not appropriate given the object's current state.</span></span>

- <span data-ttu-id="6398f-133">Vyvolání <xref:System.ArgumentException> výjimky nebo jeden z předdefinovaných tříd, které jsou odvozeny z <xref:System.ArgumentException> Pokud jsou předány neplatné parametry.</span><span class="sxs-lookup"><span data-stu-id="6398f-133">Throw an <xref:System.ArgumentException> exception or one of the predefined classes that derive from <xref:System.ArgumentException> if invalid parameters are passed.</span></span>

## <a name="end-exception-class-names-with-the-word-exception"></a><span data-ttu-id="6398f-134">Názvy tříd výjimek ukončujte slovem End `Exception`</span><span class="sxs-lookup"><span data-stu-id="6398f-134">End exception class names with the word `Exception`</span></span>

<span data-ttu-id="6398f-135">Při vlastní výjimky je nezbytné, pojmenujte ji odpovídajícím způsobem a odvozovat z <xref:System.Exception> třídy.</span><span class="sxs-lookup"><span data-stu-id="6398f-135">When a custom exception is necessary, name it appropriately and derive it from the <xref:System.Exception> class.</span></span> <span data-ttu-id="6398f-136">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6398f-136">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]  

## <a name="include-three-constructors-in-custom-exception-classes"></a><span data-ttu-id="6398f-137">Zahrnout tři konstruktory ve třídách vlastní výjimky</span><span class="sxs-lookup"><span data-stu-id="6398f-137">Include three constructors in custom exception classes</span></span>

<span data-ttu-id="6398f-138">Použijte aspoň tři běžné konstruktory při vytváření vlastních tříd výjimek: výchozí konstruktor, konstruktor, který přijímá řetězcovou zprávu a konstruktor, který přijímá řetězcovou zprávu a vnitřní výjimku.</span><span class="sxs-lookup"><span data-stu-id="6398f-138">Use at least the three common constructors when creating your own exception classes: the default constructor, a constructor that takes a string message, and a constructor that takes a string message and an inner exception.</span></span>

* <span data-ttu-id="6398f-139"><xref:System.Exception.%23ctor>, který používá výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6398f-139"><xref:System.Exception.%23ctor>, which uses default values.</span></span>
  
* <span data-ttu-id="6398f-140"><xref:System.Exception.%23ctor%28System.String%29>, která přijímá řetězcovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="6398f-140"><xref:System.Exception.%23ctor%28System.String%29>, which accepts a string message.</span></span>  
  
* <span data-ttu-id="6398f-141"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, která přijímá řetězcovou zprávu a vnitřní výjimku.</span><span class="sxs-lookup"><span data-stu-id="6398f-141"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, which accepts a string message and an inner exception.</span></span>  
  
<span data-ttu-id="6398f-142">Příklad najdete v tématu [jak: Create User-defined výjimky](how-to-create-user-defined-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="6398f-142">For an example, see [How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).</span></span>

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a><span data-ttu-id="6398f-143">Ujistěte se, že data výjimky je k dispozici, když je kód spuštěn vzdáleně</span><span class="sxs-lookup"><span data-stu-id="6398f-143">Ensure that exception data is available when code executes remotely</span></span>

<span data-ttu-id="6398f-144">Při vytváření uživatelsky definovaných výjimek, ujistěte se, že je k dispozici pro kód, který je prováděn vzdáleně metadata pro výjimky.</span><span class="sxs-lookup"><span data-stu-id="6398f-144">When you create user-defined exceptions, ensure that the metadata for the exceptions is available to code that is executing remotely.</span></span> 

<span data-ttu-id="6398f-145">Například na implementace .NET, které podporují domén aplikace, může dojít k výjimkám mezi doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="6398f-145">For example, on .NET implementations that support App Domains, exceptions may occur across App domains.</span></span> <span data-ttu-id="6398f-146">Předpokládejme, že doména aplikace A vytvoří doménu aplikace B, která spustí kód, který vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="6398f-146">Suppose App Domain A creates App Domain B, which executes code that throws an exception.</span></span> <span data-ttu-id="6398f-147">Doména aplikace A k správně zachytila a zpracovala výjimku musí být schopna najít sestavení obsahující výjimku domény aplikace b Pokud doména aplikace B vyvolá výjimku, která je součástí sestavení v rámci její základ cesty aplikace, ale není pod základ cesty aplikace příslušné domény aplikace, doména aplikace A nebudete moci najít výjimku a modul common language runtime vyvolá výjimku <xref:System.IO.FileNotFoundException> výjimky.</span><span class="sxs-lookup"><span data-stu-id="6398f-147">For App Domain A to properly catch and handle the exception, it must be able to find the assembly that contains the exception thrown by App Domain B. If App Domain B throws an exception that is contained in an assembly under its application base, but not under App Domain A's application base, App Domain A will not be able to find the exception, and the common language runtime will throw a <xref:System.IO.FileNotFoundException> exception.</span></span> <span data-ttu-id="6398f-148">Této situaci zamezíte tak, že nasadíte sestavení obsahující informace o výjimce dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="6398f-148">To avoid this situation, you can deploy the assembly that contains the exception information in two ways:</span></span>

- <span data-ttu-id="6398f-149">Sestavení umístěte do společného základu cesty aplikace sdíleného oběma doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="6398f-149">Put the assembly into a common application base shared by both app domains.</span></span>

    <span data-ttu-id="6398f-150">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="6398f-150">\- or -</span></span>

- <span data-ttu-id="6398f-151">Pokud domény nesdílejí společný základ cesty aplikace, podepište sestavení obsahující informace o výjimce silným názvem a nasaďte sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="6398f-151">If the domains do not share a common application base, sign the assembly that contains the exception information with a strong name and deploy the assembly into the global assembly cache.</span></span>

## <a name="use-grammatically-correct-error-messages"></a><span data-ttu-id="6398f-152">Používejte gramaticky správné chybové zprávy</span><span class="sxs-lookup"><span data-stu-id="6398f-152">Use grammatically correct error messages</span></span>

<span data-ttu-id="6398f-153">Zápis vymazat věty a zahrnout koncové interpunkce.</span><span class="sxs-lookup"><span data-stu-id="6398f-153">Write clear sentences and include ending punctuation.</span></span> <span data-ttu-id="6398f-154">Jednotlivé věty v řetězci přiřazené <xref:System.Exception.Message?displayProperty=nameWithType> vlastnost by měla končit tečkou.</span><span class="sxs-lookup"><span data-stu-id="6398f-154">Each sentence in the string assigned to the <xref:System.Exception.Message?displayProperty=nameWithType> property should end in a period.</span></span> <span data-ttu-id="6398f-155">Například "The log table došlo k přetečení."</span><span class="sxs-lookup"><span data-stu-id="6398f-155">For example, "The log table has overflowed."</span></span> <span data-ttu-id="6398f-156">by být řetězec odpovídající zprávu.</span><span class="sxs-lookup"><span data-stu-id="6398f-156">would be an appropriate message string.</span></span>

## <a name="include-a-localized-string-message-in-every-exception"></a><span data-ttu-id="6398f-157">Přiložit zprávu lokalizované řetězce v každé výjimce</span><span class="sxs-lookup"><span data-stu-id="6398f-157">Include a localized string message in every exception</span></span>

<span data-ttu-id="6398f-158">Chybová zpráva, která se uživateli je odvozen z <xref:System.Exception.Message?displayProperty=nameWithType> vlastnost, která byla vyvolána výjimka a nikoli z názvu třídy výjimek.</span><span class="sxs-lookup"><span data-stu-id="6398f-158">The error message that the user sees is derived from the <xref:System.Exception.Message?displayProperty=nameWithType> property of the exception that was thrown, and not from the name of the exception class.</span></span> <span data-ttu-id="6398f-159">Obvykle přiřadit hodnotu <xref:System.Exception.Message?displayProperty=nameWithType> vlastnost tím, že předáte řetězec zprávy `message` argument [výjimky konstruktoru](xref:System.Exception.%23ctor%2A).</span><span class="sxs-lookup"><span data-stu-id="6398f-159">Typically, you assign a value to the <xref:System.Exception.Message?displayProperty=nameWithType>  property by passing the message string to the `message` argument of an [Exception constructor](xref:System.Exception.%23ctor%2A).</span></span> 

<span data-ttu-id="6398f-160">V případě lokalizovaných aplikací by měly poskytnout řetězce lokalizované zpráv pro každou výjimku, kterou vaše aplikace může vyvolat.</span><span class="sxs-lookup"><span data-stu-id="6398f-160">For localized applications, you should provide a localized message string for every exception that your application can throw.</span></span> <span data-ttu-id="6398f-161">Soubory prostředků vám poskytují lokalizované chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="6398f-161">You use resource files to provide localized error messages.</span></span> <span data-ttu-id="6398f-162">Informace o lokalizaci aplikací a načítání lokalizovaných řetězců naleznete v tématu [prostředky v desktopových aplikací](../../framework/resources/index.md) a <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6398f-162">For information on localizing applications and retrieving localized strings, see [Resources in Desktop Apps](../../framework/resources/index.md) and <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span>

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a><span data-ttu-id="6398f-163">Vlastní výjimky zadejte další vlastnosti podle potřeby</span><span class="sxs-lookup"><span data-stu-id="6398f-163">In custom exceptions, provide additional properties as needed</span></span>

<span data-ttu-id="6398f-164">Zadejte další vlastnosti pro výjimku (kromě řetězec vlastní zprávu) pouze v případě, že existuje programový scénář, kde Další informace jsou užitečné.</span><span class="sxs-lookup"><span data-stu-id="6398f-164">Provide additional properties for an exception (in addition to the custom message string) only when there's a programmatic scenario where the additional information is useful.</span></span> <span data-ttu-id="6398f-165">Například <xref:System.IO.FileNotFoundException> poskytuje <xref:System.IO.FileNotFoundException.FileName> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6398f-165">For example, the <xref:System.IO.FileNotFoundException> provides the <xref:System.IO.FileNotFoundException.FileName> property.</span></span>

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a><span data-ttu-id="6398f-166">Příkaz throw místo tak, že bude užitečné trasování zásobníku</span><span class="sxs-lookup"><span data-stu-id="6398f-166">Place throw statements so that the stack trace will be helpful</span></span>

<span data-ttu-id="6398f-167">Trasování zásobníků začíná u příkazu, kde je vyvolána výjimka a končí `catch` příkaz, který zachytí výjimku.</span><span class="sxs-lookup"><span data-stu-id="6398f-167">The stack trace begins at the statement where the exception is thrown and ends at the `catch` statement that catches the exception.</span></span>

## <a name="use-exception-builder-methods"></a><span data-ttu-id="6398f-168">Použijte metody tvůrce výjimky</span><span class="sxs-lookup"><span data-stu-id="6398f-168">Use exception builder methods</span></span>

<span data-ttu-id="6398f-169">Pro třídu je běžné vyvolat stejnou výjimku z různých míst v rámci příslušné implementace.</span><span class="sxs-lookup"><span data-stu-id="6398f-169">It is common for a class to throw the same exception from different places in its implementation.</span></span> <span data-ttu-id="6398f-170">Abyste zabránili nadbytečnému kódu, použijte pomocné metody k vytvoření výjimky a vrácení výjimky.</span><span class="sxs-lookup"><span data-stu-id="6398f-170">To avoid excessive code, use helper methods that create the exception and return it.</span></span> <span data-ttu-id="6398f-171">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6398f-171">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]  
  
<span data-ttu-id="6398f-172">V některých případech je vhodnější použít konstruktor k vytvoření výjimky.</span><span class="sxs-lookup"><span data-stu-id="6398f-172">In some cases, it's more appropriate to use the exception's constructor to build the exception.</span></span> <span data-ttu-id="6398f-173">Příkladem je třídy globálních výjimek, jako <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="6398f-173">An example is a global exception class such as <xref:System.ArgumentException>.</span></span>

## <a name="clean-up-intermediate-results-when-throwing-an-exception"></a><span data-ttu-id="6398f-174">Při vyvolání výjimky odstraňte dílčí výsledky</span><span class="sxs-lookup"><span data-stu-id="6398f-174">Clean up intermediate results when throwing an exception</span></span>

<span data-ttu-id="6398f-175">Volající by měl předpokládat, že při vyvolání výjimky z metody nedojde k žádným vedlejším účinkům.</span><span class="sxs-lookup"><span data-stu-id="6398f-175">Callers should be able to assume that there are no side effects when an exception is thrown from a method.</span></span> <span data-ttu-id="6398f-176">Například pokud máte kód, který převede peníze odebrání z jednoho účtu a uložení do jiného účtu, a je vyvolána výjimka při provádění uložení, nechcete stažení zůstávají v platnosti.</span><span class="sxs-lookup"><span data-stu-id="6398f-176">For example, if you have code that transfers money by withdrawing from one account and depositing in another account, and an exception is thrown while executing the deposit, you don't want the withdrawal to remain in effect.</span></span>

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect. 
    to.Deposit(amount);
}
```

<span data-ttu-id="6398f-177">Jedním ze způsobů tuto situaci je zachytit žádné výjimky vyvolané uložení transakce a vrátit zpět stažení.</span><span class="sxs-lookup"><span data-stu-id="6398f-177">One way to handle this situation is to catch any exceptions thrown by the deposit transaction and roll back the withdrawal.</span></span>

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

<span data-ttu-id="6398f-178">Tento příklad ukazuje použití metody `throw` pro opětovné vyvolání původní výjimku, která usnadní volajícím zobrazila skutečná příčinu problému bez nutnosti k prozkoumání <xref:System.Exception.InnerException> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6398f-178">This example illustrates the use of `throw` to re-throw the original exception, which can make it easier for callers to see the real cause of the problem without having to examine the <xref:System.Exception.InnerException> property.</span></span> <span data-ttu-id="6398f-179">Alternativou je novou výjimku a zahrnují původní výjimku jako vnitřní výjimka:</span><span class="sxs-lookup"><span data-stu-id="6398f-179">An alternative is to throw a new exception and include the original exception as the inner exception:</span></span>

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new Exception("Withdrawal failed", ex);
}
```

## <a name="see-also"></a><span data-ttu-id="6398f-180">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6398f-180">See also</span></span>

- [<span data-ttu-id="6398f-181">Výjimky</span><span class="sxs-lookup"><span data-stu-id="6398f-181">Exceptions</span></span>](index.md)
