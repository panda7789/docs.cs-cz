---
title: "Doporučené postupy pro výjimky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4c5ea19077ff9ce8e36a33601b7e5e87c64afe60
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="best-practices-for-exceptions"></a><span data-ttu-id="617bb-102">Doporučené postupy pro výjimky</span><span class="sxs-lookup"><span data-stu-id="617bb-102">Best practices for exceptions</span></span>

<span data-ttu-id="617bb-103">Za účelem zamezení pádu aplikace zpracovává dobře navržená aplikace výjimky a chyby.</span><span class="sxs-lookup"><span data-stu-id="617bb-103">A well-designed app handles exceptions and errors to prevent app crashes.</span></span> <span data-ttu-id="617bb-104">Tato část popisuje doporučené postupy pro zpracování a vytváření výjimek.</span><span class="sxs-lookup"><span data-stu-id="617bb-104">This section describes best practices for handling and creating exceptions.</span></span>

## <a name="use-trycatchfinally-blocks"></a><span data-ttu-id="617bb-105">Použít try/catch/finally – bloky</span><span class="sxs-lookup"><span data-stu-id="617bb-105">Use try/catch/finally blocks</span></span>

<span data-ttu-id="617bb-106">Použití `try` / `catch` / `finally` bloky kolem kód, který může potenciálně generovat výjimku.</span><span class="sxs-lookup"><span data-stu-id="617bb-106">Use `try`/`catch`/`finally` blocks around code that can potentially generate an exception.</span></span> 

<span data-ttu-id="617bb-107">V `catch` blokuje vždy pořadí výjimky z nejvíce konkrétní nejméně specifická.</span><span class="sxs-lookup"><span data-stu-id="617bb-107">In `catch` blocks, always order exceptions from the most specific to the least specific.</span></span>

<span data-ttu-id="617bb-108">Použití `finally` blok k vyčištění prostředků, zda lze obnovit nebo ne.</span><span class="sxs-lookup"><span data-stu-id="617bb-108">Use a `finally` block to clean up resources, whether you can recover or not.</span></span>

## <a name="handle-common-conditions-without-throwing-exceptions"></a><span data-ttu-id="617bb-109">Zpracování běžné podmínky bez způsobení výjimky</span><span class="sxs-lookup"><span data-stu-id="617bb-109">Handle common conditions without throwing exceptions</span></span>

<span data-ttu-id="617bb-110">Podmínky, které by mohly nastat, ale může aktivovat výjimku, zvažte jejich zpracování způsobem, který zabrání výjimku.</span><span class="sxs-lookup"><span data-stu-id="617bb-110">For conditions that are likely to occur but might trigger an exception, consider handling them in a way that will avoid the exception.</span></span> <span data-ttu-id="617bb-111">Například pokud se pokusíte uzavřít připojení, který již byl uzavřen, získáte `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="617bb-111">For example, if you try to close a connection that is already closed, you'll get an `InvalidOperationException`.</span></span> <span data-ttu-id="617bb-112">Můžete vyhnout použitím `if` příkaz Zkontrolovat stav připojení před pokusem o zavřete ho.</span><span class="sxs-lookup"><span data-stu-id="617bb-112">You can avoid that by using an `if` statement to check the connection state before trying to close it.</span></span>

[!code-cpp[Conceptual.Exception.Handling#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]  

<span data-ttu-id="617bb-113">Pokud nemáte zkontrolovat stav připojení před zavřením, můžete zachytit `InvalidOperationException` výjimky.</span><span class="sxs-lookup"><span data-stu-id="617bb-113">If you don't check connection state before closing, you can catch the `InvalidOperationException` exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]  

<span data-ttu-id="617bb-114">Metoda zvolit závisí na tom, jak často předpokládáte dojde k události.</span><span class="sxs-lookup"><span data-stu-id="617bb-114">The method to choose depends on how often you expect the event to occur.</span></span>

- <span data-ttu-id="617bb-115">Použijte zpracování výjimek, pokud k události nedochází velmi často, tzn. pokud k události dochází výjimečně a značí chybu (jako například neočekávaný konec souboru).</span><span class="sxs-lookup"><span data-stu-id="617bb-115">Use exception handling if the event doesn't occur very often, that is, if the event is truly exceptional and indicates an error (such as an unexpected end-of-file).</span></span> <span data-ttu-id="617bb-116">Při používání zpracování výjimek je za běžných podmínek provedena menší část kódu.</span><span class="sxs-lookup"><span data-stu-id="617bb-116">When you use exception handling, less code is executed in normal conditions.</span></span>

- <span data-ttu-id="617bb-117">Pokud události se stane, pravidelně a může být považovány za součást normální spuštění Zkontrolujte chybové stavy v kódu.</span><span class="sxs-lookup"><span data-stu-id="617bb-117">Check for error conditions in code if the event happens routinely and could be considered part of normal execution.</span></span> <span data-ttu-id="617bb-118">Při kontrole běžné chybové stavy, méně kódu je provést, protože se vyhnout výjimky.</span><span class="sxs-lookup"><span data-stu-id="617bb-118">When you check for common error conditions, less code is executed because you avoid exceptions.</span></span>

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a><span data-ttu-id="617bb-119">Navrhování třídy tak, aby se vyhnout výjimky</span><span class="sxs-lookup"><span data-stu-id="617bb-119">Design classes so that exceptions can be avoided</span></span>

<span data-ttu-id="617bb-120">Třída může poskytnout metody nebo vlastnosti, které vám umožní vyhnout, že zavoláte vyvolalo výjimku.</span><span class="sxs-lookup"><span data-stu-id="617bb-120">A class can provide methods or properties that enable you to avoid making a call that would trigger an exception.</span></span> <span data-ttu-id="617bb-121">Například <xref:System.IO.FileStream> třída poskytuje metody, které pomáhají určit, zda byl dosažen konec souboru.</span><span class="sxs-lookup"><span data-stu-id="617bb-121">For example, a <xref:System.IO.FileStream> class provides methods that help determine whether the end of the file has been reached.</span></span> <span data-ttu-id="617bb-122">Tyto umožňuje vyhnout se výjimka, která je vyvolána, pokud čtete za konec souboru.</span><span class="sxs-lookup"><span data-stu-id="617bb-122">These can be used to avoid the exception that is thrown if you read past the end of the file.</span></span> <span data-ttu-id="617bb-123">Následující příklad ukazuje, jak číst na konec souboru bez vyvolání k výjimce.</span><span class="sxs-lookup"><span data-stu-id="617bb-123">The following example shows how to read to the end of a file without triggering an exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]  

<span data-ttu-id="617bb-124">Jiný způsob, jak zabránit výjimky je vrátit hodnotu null pro velmi běžné případy chyba místo došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="617bb-124">Another way to avoid exceptions is to return null for extremely common error cases instead of throwing an exception.</span></span> <span data-ttu-id="617bb-125">Za nejběžnější případ chyby lze považovat běžný tok řízení.</span><span class="sxs-lookup"><span data-stu-id="617bb-125">An extremely common error case can be considered normal flow of control.</span></span> <span data-ttu-id="617bb-126">Vrácením hodnoty null v těchto případech minimalizujete dopad výkonu pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="617bb-126">By returning null in these cases, you minimize the performance impact to an app.</span></span>

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a><span data-ttu-id="617bb-127">Generování výjimek místo vrací kód chyby</span><span class="sxs-lookup"><span data-stu-id="617bb-127">Throw exceptions instead of returning an error code</span></span>

<span data-ttu-id="617bb-128">Výjimky Ujistěte se, že selhání nedojde protože volání, že kód nebyl zkontrolovat návratový kód.</span><span class="sxs-lookup"><span data-stu-id="617bb-128">Exceptions ensure that failures do not go unnoticed because calling code didn't check a return code.</span></span> 

## <a name="use-the-predefined-net-exception-types"></a><span data-ttu-id="617bb-129">Pomocí předdefinovaných typů výjimek rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="617bb-129">Use the predefined .NET exception types</span></span>

<span data-ttu-id="617bb-130">Zavést nové třídy výjimky jenom v případě, že se netýká předdefinované jeden.</span><span class="sxs-lookup"><span data-stu-id="617bb-130">Introduce a new exception class only when a predefined one doesn't apply.</span></span> <span data-ttu-id="617bb-131">Příklad:</span><span class="sxs-lookup"><span data-stu-id="617bb-131">For example:</span></span>

- <span data-ttu-id="617bb-132">Throw – <xref:System.InvalidOperationException> výjimka, není-li vlastnost sadu nebo metoda volání odpovídající zadané aktuální stav objektu.</span><span class="sxs-lookup"><span data-stu-id="617bb-132">Throw an <xref:System.InvalidOperationException> exception if a property set or method call is not appropriate given the object's current state.</span></span>

- <span data-ttu-id="617bb-133">Throw – <xref:System.ArgumentException> výjimky nebo jeden z předdefinovaných tříd, které jsou odvozeny od <xref:System.ArgumentException> Pokud jsou předány neplatné parametry.</span><span class="sxs-lookup"><span data-stu-id="617bb-133">Throw an <xref:System.ArgumentException> exception or one of the predefined classes that derive from <xref:System.ArgumentException> if invalid parameters are passed.</span></span>

## <a name="end-exception-class-names-with-the-word-exception"></a><span data-ttu-id="617bb-134">Ukončete názvy tříd výjimek slovem`Exception`</span><span class="sxs-lookup"><span data-stu-id="617bb-134">End exception class names with the word `Exception`</span></span>

<span data-ttu-id="617bb-135">Při vlastní výjimky je nutné, pojmenujte ji odpovídajícím způsobem a odvodí z <xref:System.Exception> třídy.</span><span class="sxs-lookup"><span data-stu-id="617bb-135">When a custom exception is necessary, name it appropriately and derive it from the <xref:System.Exception> class.</span></span> <span data-ttu-id="617bb-136">Příklad:</span><span class="sxs-lookup"><span data-stu-id="617bb-136">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]  

## <a name="include-three-constructors-in-custom-exception-classes"></a><span data-ttu-id="617bb-137">Zahrnout tři konstruktory třídy vlastní výjimek</span><span class="sxs-lookup"><span data-stu-id="617bb-137">Include three constructors in custom exception classes</span></span>

<span data-ttu-id="617bb-138">Použijte alespoň tři společné konstruktory při vytváření vlastní třídy výjimek: výchozí konstruktor, konstruktor, který přebírá zprávu řetězec a konstruktor, který přebírá zprávu řetězec a vnitřní výjimku.</span><span class="sxs-lookup"><span data-stu-id="617bb-138">Use at least the three common constructors when creating your own exception classes: the default constructor, a constructor that takes a string message, and a constructor that takes a string message and an inner exception.</span></span>

* <span data-ttu-id="617bb-139"><xref:System.Exception.%23ctor>, který používá výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="617bb-139"><xref:System.Exception.%23ctor>, which uses default values.</span></span>
  
* <span data-ttu-id="617bb-140"><xref:System.Exception.%23ctor%28System.String%29>, která přijímá zprávy řetězec.</span><span class="sxs-lookup"><span data-stu-id="617bb-140"><xref:System.Exception.%23ctor%28System.String%29>, which accepts a string message.</span></span>  
  
* <span data-ttu-id="617bb-141"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, která přijímá zprávy řetězec a vnitřní výjimku.</span><span class="sxs-lookup"><span data-stu-id="617bb-141"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, which accepts a string message and an inner exception.</span></span>  
  
<span data-ttu-id="617bb-142">Příklad, naleznete v části [postup: výjimky Create User-Defined](how-to-create-user-defined-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="617bb-142">For an example, see [How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).</span></span>

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a><span data-ttu-id="617bb-143">Ujistěte se, že data výjimky je k dispozici, když kód provede vzdáleně</span><span class="sxs-lookup"><span data-stu-id="617bb-143">Ensure that exception data is available when code executes remotely</span></span>

<span data-ttu-id="617bb-144">Při vytváření uživatelsky definovaných výjimek, zajistěte, aby metadata pro výjimky k dispozici pro kód, který je spustit vzdáleně.</span><span class="sxs-lookup"><span data-stu-id="617bb-144">When you create user-defined exceptions, ensure that the metadata for the exceptions is available to code that is executing remotely.</span></span> 

<span data-ttu-id="617bb-145">Například na implementace rozhraní .NET, které podporují doménami aplikací, může dojít výjimek mezi doménami aplikací.</span><span class="sxs-lookup"><span data-stu-id="617bb-145">For example, on .NET implementations that support App Domains, exceptions may occur across App domains.</span></span> <span data-ttu-id="617bb-146">Předpokládejme, že doména aplikace A vytvoří aplikace domény B, který spustí kód, který vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="617bb-146">Suppose App Domain A creates App Domain B, which executes code that throws an exception.</span></span> <span data-ttu-id="617bb-147">Pro doménu aplikace A správně zachytit a zpracovat výjimku musí být schopna nalézt sestavení, které obsahuje výjimky vyvolané B. domény aplikace Pokud aplikace doména B vyvolá výjimku, která je součástí sestavení pod její základ cesty aplikace, ale není v rámci domény aplikací na základ cesty aplikace, doména aplikace A nebude možné najít výjimku a vyvolá výjimku modul common language runtime <xref:System.IO.FileNotFoundException> výjimka.</span><span class="sxs-lookup"><span data-stu-id="617bb-147">For App Domain A to properly catch and handle the exception, it must be able to find the assembly that contains the exception thrown by App Domain B. If App Domain B throws an exception that is contained in an assembly under its application base, but not under App Domain A's application base, App Domain A will not be able to find the exception, and the common language runtime will throw a <xref:System.IO.FileNotFoundException> exception.</span></span> <span data-ttu-id="617bb-148">Této situaci zamezíte tak, že nasadíte sestavení obsahující informace o výjimce dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="617bb-148">To avoid this situation, you can deploy the assembly that contains the exception information in two ways:</span></span>

- <span data-ttu-id="617bb-149">Sestavení umístěte do společného základu cesty aplikace sdíleného oběma doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="617bb-149">Put the assembly into a common application base shared by both app domains.</span></span>

    <span data-ttu-id="617bb-150">\-nebo –</span><span class="sxs-lookup"><span data-stu-id="617bb-150">\- or -</span></span>

- <span data-ttu-id="617bb-151">Pokud domény nesdílejí společný základ cesty aplikace, podepište sestavení obsahující informace o výjimce silným názvem a nasaďte sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="617bb-151">If the domains do not share a common application base, sign the assembly that contains the exception information with a strong name and deploy the assembly into the global assembly cache.</span></span>

## <a name="include-a-localized-description-string-in-every-exception"></a><span data-ttu-id="617bb-152">Zahrnout lokalizované řetězce popisu každé výjimky</span><span class="sxs-lookup"><span data-stu-id="617bb-152">Include a localized description string in every exception</span></span>

<span data-ttu-id="617bb-153">Chybová zpráva, která uživateli se zobrazí je odvozený z řetězce popis výjimky, která byla vydána a nikoli z název třídy výjimky.</span><span class="sxs-lookup"><span data-stu-id="617bb-153">The error message that the user sees is derived from the description string of the exception that was thrown, and not from the name of the exception class.</span></span>

## <a name="use-grammatically-correct-error-messages"></a><span data-ttu-id="617bb-154">Použijte gramaticky správné chybové zprávy</span><span class="sxs-lookup"><span data-stu-id="617bb-154">Use grammatically correct error messages</span></span>

<span data-ttu-id="617bb-155">Zápis zrušte věty a zahrnout koncové interpunkce.</span><span class="sxs-lookup"><span data-stu-id="617bb-155">Write clear sentences and include ending punctuation.</span></span> <span data-ttu-id="617bb-156">Jednotlivé věty v řetězci popisu výjimky by měly končit tečkou.</span><span class="sxs-lookup"><span data-stu-id="617bb-156">Each sentence in a description string of an exception should end in a period.</span></span> <span data-ttu-id="617bb-157">Například "v tabulce protokolu došlo k přetečení."</span><span class="sxs-lookup"><span data-stu-id="617bb-157">For example, "The log table has overflowed."</span></span> <span data-ttu-id="617bb-158">bude řetězec odpovídající popis.</span><span class="sxs-lookup"><span data-stu-id="617bb-158">would be an appropriate description string.</span></span>

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a><span data-ttu-id="617bb-159">Ve vlastní výjimky zadejte další vlastnosti podle potřeby</span><span class="sxs-lookup"><span data-stu-id="617bb-159">In custom exceptions, provide additional properties as needed</span></span>

<span data-ttu-id="617bb-160">Zadejte další vlastnosti pro výjimku (kromě řetězec popisu) jenom v případě, že je programový scénář, kde Další informace jsou užitečné.</span><span class="sxs-lookup"><span data-stu-id="617bb-160">Provide additional properties for an exception (in addition to the description string) only when there's a programmatic scenario where the additional information is useful.</span></span> <span data-ttu-id="617bb-161">Například <xref:System.IO.FileNotFoundException> poskytuje <xref:System.IO.FileNotFoundException.FileName> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="617bb-161">For example, the <xref:System.IO.FileNotFoundException> provides the <xref:System.IO.FileNotFoundException.FileName> property.</span></span>

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a><span data-ttu-id="617bb-162">Tak, aby trasování zásobníku budou užitečné místní throw – příkazy</span><span class="sxs-lookup"><span data-stu-id="617bb-162">Place throw statements so that the stack trace will be helpful</span></span>

<span data-ttu-id="617bb-163">Trasování zásobníku začíná na příkaz, kde je vyvolána výjimka a končí `catch` příkaz, který zachytí výjimky.</span><span class="sxs-lookup"><span data-stu-id="617bb-163">The stack trace begins at the statement where the exception is thrown and ends at the `catch` statement that catches the exception.</span></span>

## <a name="use-exception-builder-methods"></a><span data-ttu-id="617bb-164">Pomocí metody tvůrce výjimky</span><span class="sxs-lookup"><span data-stu-id="617bb-164">Use exception builder methods</span></span>

<span data-ttu-id="617bb-165">Pro třídu je běžné vyvolat stejnou výjimku z různých míst v rámci příslušné implementace.</span><span class="sxs-lookup"><span data-stu-id="617bb-165">It is common for a class to throw the same exception from different places in its implementation.</span></span> <span data-ttu-id="617bb-166">Abyste zabránili nadbytečnému kódu, použijte pomocné metody k vytvoření výjimky a vrácení výjimky.</span><span class="sxs-lookup"><span data-stu-id="617bb-166">To avoid excessive code, use helper methods that create the exception and return it.</span></span> <span data-ttu-id="617bb-167">Příklad:</span><span class="sxs-lookup"><span data-stu-id="617bb-167">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]  
  
<span data-ttu-id="617bb-168">V některých případech je vhodnější použít konstruktor v výjimky vytvořit výjimku.</span><span class="sxs-lookup"><span data-stu-id="617bb-168">In some cases, it's more appropriate to use the exception's constructor to build the exception.</span></span> <span data-ttu-id="617bb-169">Příklad, jako je třída globální výjimka <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="617bb-169">An example is a global exception class such as <xref:System.ArgumentException>.</span></span>

## <a name="clean-up-intermediate-results-when-throwing-an-exception"></a><span data-ttu-id="617bb-170">Odstranit mezilehlých výsledků při vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="617bb-170">Clean up intermediate results when throwing an exception</span></span>

<span data-ttu-id="617bb-171">Volající by měl předpokládat, že při vyvolání výjimky z metody nedojde k žádným vedlejším účinkům.</span><span class="sxs-lookup"><span data-stu-id="617bb-171">Callers should be able to assume that there are no side effects when an exception is thrown from a method.</span></span> <span data-ttu-id="617bb-172">Například pokud máte kód, který převádí peníze stažení z jednoho účtu a uloží v jiný účet, a při provádění uložení je vyvolána výjimka, nechcete odebrání zůstávají v platnosti.</span><span class="sxs-lookup"><span data-stu-id="617bb-172">For example, if you have code that transfers money by withdrawing from one account and depositing in another account, and an exception is thrown while executing the deposit, you don't want the withdrawal to remain in effect.</span></span>

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect. 
    to.Deposit(amount);
}
```

<span data-ttu-id="617bb-173">Jedním ze způsobů ke zpracování této situace je catch jakékoli výjimky vyvolané uložení transakce a vrácení stažení.</span><span class="sxs-lookup"><span data-stu-id="617bb-173">One way to handle this situation is to catch any exceptions thrown by the deposit transaction and roll back the withdrawal.</span></span>

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

<span data-ttu-id="617bb-174">Tento příklad ukazuje použití `throw` znovu vyvolat původní výjimka, která může usnadnit volající zobrazíte skutečná příčinu problému bez nutnosti zkontrolujte <xref:System.Exception.InnerException> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="617bb-174">This example illustrates the use of `throw` to re-throw the original exception, which can make it easier for callers to see the real cause of the problem without having to examine the <xref:System.Exception.InnerException> property.</span></span> <span data-ttu-id="617bb-175">Alternativou je throw novou výjimku a musí zahrnovat původní výjimka jako v popisu vnitřní výjimky:</span><span class="sxs-lookup"><span data-stu-id="617bb-175">An alternative is to throw a new exception and include the original exception as the inner exception:</span></span>

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new Exception("Withdrawal failed", ex);
}
```

## <a name="see-also"></a><span data-ttu-id="617bb-176">Viz také</span><span class="sxs-lookup"><span data-stu-id="617bb-176">See Also</span></span>  
[<span data-ttu-id="617bb-177">Výjimky</span><span class="sxs-lookup"><span data-stu-id="617bb-177">Exceptions</span></span>](index.md)
