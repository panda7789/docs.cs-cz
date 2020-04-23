---
title: Protokolování pomocí sady Azure SDK pro rozhraní .NET
description: Zjistěte, jak povolit protokolování pomocí sady Azure SDK pro klientské knihovny rozhraní .NET
ms.date: 03/20/2020
ms.custom: azure-sdk-dotnet
ms.author: casoper
author: camsoper
ms.openlocfilehash: b277045a60ef5cc065d77dad84878872dedc963e
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "82071988"
---
# <a name="logging-with-the-azure-sdk-for-net"></a><span data-ttu-id="5b167-103">Protokolování pomocí sady Azure SDK pro rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="5b167-103">Logging with the Azure SDK for .NET</span></span>

<span data-ttu-id="5b167-104">Sada [Azure SDK](https://azure.microsoft.com/downloads/) pro klientské knihovny .NET zahrnuje možnost protokolovat operace klientské knihovny.</span><span class="sxs-lookup"><span data-stu-id="5b167-104">The [Azure SDK](https://azure.microsoft.com/downloads/) for .NET client libraries includes the ability to log client library operations.</span></span> <span data-ttu-id="5b167-105">To umožňuje sledovat vstupně-va požadavky a odpovědi, které klientské knihovny dělají do služeb Azure.</span><span class="sxs-lookup"><span data-stu-id="5b167-105">This allows you to monitor I/O requests and responses that client libraries are making to Azure services.</span></span> <span data-ttu-id="5b167-106">Protokoly se obvykle používají k ladění nebo diagnostikovat problémy s komunikací.</span><span class="sxs-lookup"><span data-stu-id="5b167-106">Typically, the logs are used to debug or diagnose communication issues.</span></span> <span data-ttu-id="5b167-107">Tento článek popisuje tři přístupy k povolení protokolování pomocí sady Azure SDK pro rozhraní .NET:</span><span class="sxs-lookup"><span data-stu-id="5b167-107">This article describes three approaches to enable logging with the Azure SDK for .NET:</span></span>

- <span data-ttu-id="5b167-108">Přihlásit se do okna konzoly</span><span class="sxs-lookup"><span data-stu-id="5b167-108">Log to the console window</span></span>
- <span data-ttu-id="5b167-109">Protokolovat do tras diagnostiky .NET</span><span class="sxs-lookup"><span data-stu-id="5b167-109">Log to .NET diagnostics traces</span></span>
- <span data-ttu-id="5b167-110">Konfigurace vlastního protokolování</span><span class="sxs-lookup"><span data-stu-id="5b167-110">Configure custom logging</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b167-111">Tento článek se vztahuje na klientské knihovny, které používají nejnovější verze sady Azure SDK pro rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="5b167-111">This article applies to client libraries that use the most recent versions of the Azure SDK for .NET.</span></span> <span data-ttu-id="5b167-112">Chcete-li zjistit, zda je knihovna podporovaná, podívejte se na seznam [nejnovějších verzí sady Azure SDK](https://azure.github.io/azure-sdk/releases/latest/index.html).</span><span class="sxs-lookup"><span data-stu-id="5b167-112">To see if a library is supported, refer to the list of [Azure SDK latest releases](https://azure.github.io/azure-sdk/releases/latest/index.html).</span></span> <span data-ttu-id="5b167-113">Pokud vaše aplikace používá starší verzi klientských knihoven Sady Azure SDK, naleznete konkrétní pokyny v příslušné dokumentaci ke službě.</span><span class="sxs-lookup"><span data-stu-id="5b167-113">If your application is using an older version of the Azure SDK client libraries, refer to specific instructions in the applicable service documentation.</span></span>

## <a name="log-information"></a><span data-ttu-id="5b167-114">Informace protokolu</span><span class="sxs-lookup"><span data-stu-id="5b167-114">Log information</span></span>

<span data-ttu-id="5b167-115">Sada SDK protokoluje následující informace, dezinfekce parametrický dotaz a hodnoty záhlaví k odebrání osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="5b167-115">The SDK logs the following information, sanitizing parameter query and header values to remove personal data.</span></span>

<span data-ttu-id="5b167-116">Zadání protokolu požadavků HTTP:</span><span class="sxs-lookup"><span data-stu-id="5b167-116">HTTP request log entry:</span></span>

- <span data-ttu-id="5b167-117">Jedinečné ID</span><span class="sxs-lookup"><span data-stu-id="5b167-117">Unique ID</span></span>
- <span data-ttu-id="5b167-118">Metoda HTTP</span><span class="sxs-lookup"><span data-stu-id="5b167-118">HTTP method</span></span>
- <span data-ttu-id="5b167-119">Identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="5b167-119">URI</span></span>
- <span data-ttu-id="5b167-120">Hlavičky odchozích požadavků</span><span class="sxs-lookup"><span data-stu-id="5b167-120">Outgoing request headers</span></span>

<span data-ttu-id="5b167-121">Zadání protokolu odpovědí HTTP:</span><span class="sxs-lookup"><span data-stu-id="5b167-121">HTTP response log entry:</span></span>

- <span data-ttu-id="5b167-122">Doba trvání vstupně-to-va/v provozu (uplynulý čas)</span><span class="sxs-lookup"><span data-stu-id="5b167-122">Duration of I/O operation (time elapsed)</span></span>
- <span data-ttu-id="5b167-123">ID požadavku</span><span class="sxs-lookup"><span data-stu-id="5b167-123">Request ID</span></span>
- <span data-ttu-id="5b167-124">Stavový kód HTTP</span><span class="sxs-lookup"><span data-stu-id="5b167-124">HTTP status code</span></span>
- <span data-ttu-id="5b167-125">Fráze důvod http</span><span class="sxs-lookup"><span data-stu-id="5b167-125">HTTP reason phrase</span></span>
- <span data-ttu-id="5b167-126">Hlavičky odpovědi</span><span class="sxs-lookup"><span data-stu-id="5b167-126">Response headers</span></span>
- <span data-ttu-id="5b167-127">Informace o chybě, je-li k dispozici</span><span class="sxs-lookup"><span data-stu-id="5b167-127">Error information, when applicable</span></span>

<span data-ttu-id="5b167-128">Pro obsah požadavku a odpovědi:</span><span class="sxs-lookup"><span data-stu-id="5b167-128">For request and response content:</span></span>

- <span data-ttu-id="5b167-129">Obsah proudí jako text nebo bajty v závislosti na záhlaví Typu obsahu.</span><span class="sxs-lookup"><span data-stu-id="5b167-129">Content stream as text or bytes depending on the Content-Type header.</span></span>
     > <span data-ttu-id="5b167-130">[! POZNÁMKA} Protokolování obsahu je ve výchozím nastavení zakázáno.</span><span class="sxs-lookup"><span data-stu-id="5b167-130">[!NOTE} Content logging is disabled by default.</span></span> <span data-ttu-id="5b167-131">Chcete-li jej `Diagnostics.IsLoggingContentEnabled` `true` povolit, nastavte v `ClientOptions`.</span><span class="sxs-lookup"><span data-stu-id="5b167-131">To enable it, set `Diagnostics.IsLoggingContentEnabled` to `true` in `ClientOptions`.</span></span>

<span data-ttu-id="5b167-132">Protokoly událostí jsou výstup obvykle na jedné z těchto tří úrovní:</span><span class="sxs-lookup"><span data-stu-id="5b167-132">Event logs are output usually at one of these three levels:</span></span>

- <span data-ttu-id="5b167-133">Informace pro události požadavku a odpovědi</span><span class="sxs-lookup"><span data-stu-id="5b167-133">Informational for request and response events</span></span>
- <span data-ttu-id="5b167-134">Upozornění na chyby</span><span class="sxs-lookup"><span data-stu-id="5b167-134">Warning for errors</span></span>
- <span data-ttu-id="5b167-135">Podrobné informace o detailních zprávách a protokolování obsahu</span><span class="sxs-lookup"><span data-stu-id="5b167-135">Verbose for detailed messages and content logging</span></span>

## <a name="enable-logging-with-built-in-methods"></a><span data-ttu-id="5b167-136">Povolení protokolování pomocí integrovaných metod</span><span class="sxs-lookup"><span data-stu-id="5b167-136">Enable logging with built-in methods</span></span>

<span data-ttu-id="5b167-137">Sada Azure SDK pro klientské knihovny .NET protokoluje události protokolu do trasování událostí pro Windows (ETW) prostřednictvím [ `EventSource` třídy](/dotnet/api/system.diagnostics.tracing.eventsource), což je typické pro rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="5b167-137">The Azure SDK for .NET client libraries log events to Event Tracing for Windows (ETW) via the [`EventSource` class](/dotnet/api/system.diagnostics.tracing.eventsource), which is typical for .NET.</span></span> <span data-ttu-id="5b167-138">Zdroje událostí umožňují používat strukturované protokolování v kódu aplikace s minimální režií výkonu.</span><span class="sxs-lookup"><span data-stu-id="5b167-138">Event sources allow you to use structured logging in your application code with a minimal performance overhead.</span></span> <span data-ttu-id="5b167-139">Chcete-li získat přístup k těmto protokolům událostí, je třeba zaregistrovat posluchače událostí.</span><span class="sxs-lookup"><span data-stu-id="5b167-139">To gain access to these event logs, you need to register event listeners.</span></span>

<span data-ttu-id="5b167-140">Sada SDK `Azure.Core.Diagnostics.AzureEventSourceListener` zahrnuje třídu (definovanou v balíčku Azure.Core NuGet), která obsahuje dvě `CreateConsoleLogger` statické `CreateTraceLogger`metody, které zjednodušují komplexní protokolování pro vaši aplikaci .NET: a .</span><span class="sxs-lookup"><span data-stu-id="5b167-140">The SDK includes the `Azure.Core.Diagnostics.AzureEventSourceListener` class (defined in the Azure.Core NuGet package), which contains two static methods that simplify comprehensive logging for your .NET application: `CreateConsoleLogger` and `CreateTraceLogger`.</span></span> <span data-ttu-id="5b167-141">Tyto metody trvat volitelný parametr, který určuje úroveň protokolu.</span><span class="sxs-lookup"><span data-stu-id="5b167-141">These methods take an optional parameter that specifies a log level.</span></span>

### <a name="log-to-the-console-window"></a><span data-ttu-id="5b167-142">Přihlásit se do okna konzoly</span><span class="sxs-lookup"><span data-stu-id="5b167-142">Log to the console window</span></span>

<span data-ttu-id="5b167-143">Základním principem sady Azure SDK pro klientské knihovny .NET je zjednodušit možnost zobrazení komplexních protokolů v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="5b167-143">A core tenet of the Azure SDK for .NET client libraries is to simplify the ability to view comprehensive logs in real time.</span></span> <span data-ttu-id="5b167-144">Metoda `CreateConsoleLogger` umožňuje odesílat protokoly do okna konzoly s jedním řádkem kódu:</span><span class="sxs-lookup"><span data-stu-id="5b167-144">The `CreateConsoleLogger` method allows you to send logs to the console window with a single line of code:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a><span data-ttu-id="5b167-145">Protokolovat do diagnostických tras</span><span class="sxs-lookup"><span data-stu-id="5b167-145">Log to diagnostic traces</span></span>

<span data-ttu-id="5b167-146">Pokud implementujete naslouchací procesy trasování, můžete použít metodu `CreateTraceLogger` k přihlášení ke standardnímu mechanismu trasování událostí .NET ([`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)).</span><span class="sxs-lookup"><span data-stu-id="5b167-146">If you implement trace listeners, you can use the `CreateTraceLogger` method to log to the standard .NET event tracing mechanism ([`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)).</span></span> <span data-ttu-id="5b167-147">Další informace o trasování událostí v rozhraní .NET naleznete v [tématu Posluchači trasování](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners).</span><span class="sxs-lookup"><span data-stu-id="5b167-147">For more information on event tracing in .NET, see [Trace Listeners](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners).</span></span> <span data-ttu-id="5b167-148">Tento příklad určuje úroveň protokolu podrobné:</span><span class="sxs-lookup"><span data-stu-id="5b167-148">This example specifies a log level of verbose:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a><span data-ttu-id="5b167-149">Konfigurace vlastního protokolování</span><span class="sxs-lookup"><span data-stu-id="5b167-149">Configure custom logging</span></span>

<span data-ttu-id="5b167-150">Jak bylo uvedeno výše, je třeba zaregistrovat posluchače událostí pro příjem zpráv protokolu z sady Azure SDK pro rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="5b167-150">As mentioned above, you need to register event listeners to receive log messages from the Azure SDK for .NET.</span></span> <span data-ttu-id="5b167-151">Pokud nechcete implementovat komplexní protokolování pomocí jedné zjednodušené metody výše, `AzureEventSourceListener` můžete vytvořit instanci třídy a předat ji funkci zpětného volání, kterou píšete.</span><span class="sxs-lookup"><span data-stu-id="5b167-151">If you don’t want to implement comprehensive logging using one the simplified methods above, you can construct an instance of the `AzureEventSourceListener` class and pass it a callback function that you write.</span></span> <span data-ttu-id="5b167-152">Tato metoda obdrží zprávy protokolu, které můžete zpracovat však je třeba.</span><span class="sxs-lookup"><span data-stu-id="5b167-152">This method will receive log messages that you can process however you need to.</span></span> <span data-ttu-id="5b167-153">Kromě toho při vytváření instance, můžete určit úrovně protokolu zahrnout.</span><span class="sxs-lookup"><span data-stu-id="5b167-153">In addition, when you construct the instance, you can specify the log levels to include.</span></span>

<span data-ttu-id="5b167-154">Následující příklad vytvoří naslouchací proces událostí, který se přihlásí ke konzole s vlastní zprávou a je filtrován na základní události Azure úrovně verbose.</span><span class="sxs-lookup"><span data-stu-id="5b167-154">The following example creates an event listener that logs to the console with a custom message, and is filtered to Azure core events of the level verbose.</span></span>

```csharp
using AzureEventSourceListener listener = new AzureEventSourceListener((e, message) =>
    {
        // Only log messages from Azure-Core event source
        if (e.EventSource.Name == "Azure-Core")
        {
            Console.WriteLine($"{DateTime.Now} {message}");
        }
    },
    level: EventLevel.Verbose);
```

## <a name="next-steps"></a><span data-ttu-id="5b167-155">Další kroky</span><span class="sxs-lookup"><span data-stu-id="5b167-155">Next steps</span></span>

- [<span data-ttu-id="5b167-156">Povolení protokolování diagnostiky aplikací ve službě Azure App Service</span><span class="sxs-lookup"><span data-stu-id="5b167-156">Enable diagnostics logging for apps in Azure App Service</span></span>](https://docs.microsoft.com/azure/app-service/troubleshoot-diagnostic-logs)
- <span data-ttu-id="5b167-157">Kontrola možností [protokolování zabezpečení azure a auditování](https://docs.microsoft.com/azure/security/fundamentals/log-audit)</span><span class="sxs-lookup"><span data-stu-id="5b167-157">Review [Azure security logging and auditing](https://docs.microsoft.com/azure/security/fundamentals/log-audit) options</span></span>
- <span data-ttu-id="5b167-158">Zjistěte, jak pracovat s [protokoly platformy Azure](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview)</span><span class="sxs-lookup"><span data-stu-id="5b167-158">Learn how to work with [Azure platform logs](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview)</span></span>
- <span data-ttu-id="5b167-159">Další informace o [protokolování a trasování jádra .NET](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing)</span><span class="sxs-lookup"><span data-stu-id="5b167-159">Read more about [.NET Core logging and tracing](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing)</span></span>
