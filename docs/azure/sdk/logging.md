---
title: Protokolování pomocí sady Azure SDK pro .NET
description: Naučte se, jak povolit protokolování pomocí sady Azure SDK pro klientské knihovny .NET.
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
# <a name="logging-with-the-azure-sdk-for-net"></a><span data-ttu-id="29e66-103">Protokolování pomocí sady Azure SDK pro .NET</span><span class="sxs-lookup"><span data-stu-id="29e66-103">Logging with the Azure SDK for .NET</span></span>

<span data-ttu-id="29e66-104">[Sada Azure SDK](https://azure.microsoft.com/downloads/) pro klientské knihovny .NET zahrnuje možnost protokolování operací klientské knihovny.</span><span class="sxs-lookup"><span data-stu-id="29e66-104">The [Azure SDK](https://azure.microsoft.com/downloads/) for .NET client libraries includes the ability to log client library operations.</span></span> <span data-ttu-id="29e66-105">Díky tomu můžete monitorovat žádosti a odpovědi na vstupně-výstupní operace, které klientské knihovny využívají ke službám Azure.</span><span class="sxs-lookup"><span data-stu-id="29e66-105">This allows you to monitor I/O requests and responses that client libraries are making to Azure services.</span></span> <span data-ttu-id="29e66-106">Protokoly se obvykle používají k ladění nebo diagnostikování potíží s komunikací.</span><span class="sxs-lookup"><span data-stu-id="29e66-106">Typically, the logs are used to debug or diagnose communication issues.</span></span> <span data-ttu-id="29e66-107">Tento článek popisuje tři přístupy k povolení protokolování v sadě Azure SDK pro .NET:</span><span class="sxs-lookup"><span data-stu-id="29e66-107">This article describes three approaches to enable logging with the Azure SDK for .NET:</span></span>

- <span data-ttu-id="29e66-108">Přihlaste se do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="29e66-108">Log to the console window</span></span>
- <span data-ttu-id="29e66-109">Protokolování trasování diagnostiky .NET</span><span class="sxs-lookup"><span data-stu-id="29e66-109">Log to .NET diagnostics traces</span></span>
- <span data-ttu-id="29e66-110">Konfigurace vlastního protokolování</span><span class="sxs-lookup"><span data-stu-id="29e66-110">Configure custom logging</span></span>

> [!IMPORTANT]
> <span data-ttu-id="29e66-111">Tento článek se týká klientských knihoven, které používají nejnovější verze sady Azure SDK pro .NET.</span><span class="sxs-lookup"><span data-stu-id="29e66-111">This article applies to client libraries that use the most recent versions of the Azure SDK for .NET.</span></span> <span data-ttu-id="29e66-112">Pokud chcete zjistit, jestli je knihovna podporovaná, přečtěte si seznam [nejnovějších verzí sady Azure SDK](https://azure.github.io/azure-sdk/releases/latest/index.html).</span><span class="sxs-lookup"><span data-stu-id="29e66-112">To see if a library is supported, refer to the list of [Azure SDK latest releases](https://azure.github.io/azure-sdk/releases/latest/index.html).</span></span> <span data-ttu-id="29e66-113">Pokud vaše aplikace používá starší verzi klientských knihoven Azure SDK, přečtěte si konkrétní pokyny v příslušné dokumentaci ke službě.</span><span class="sxs-lookup"><span data-stu-id="29e66-113">If your application is using an older version of the Azure SDK client libraries, refer to specific instructions in the applicable service documentation.</span></span>

## <a name="log-information"></a><span data-ttu-id="29e66-114">Informace protokolu</span><span class="sxs-lookup"><span data-stu-id="29e66-114">Log information</span></span>

<span data-ttu-id="29e66-115">Sada SDK protokoluje následující informace, upravené hodnoty dotazů a hodnot hlaviček pro odebrání osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="29e66-115">The SDK logs the following information, sanitizing parameter query and header values to remove personal data.</span></span>

<span data-ttu-id="29e66-116">Položka protokolu požadavku HTTP:</span><span class="sxs-lookup"><span data-stu-id="29e66-116">HTTP request log entry:</span></span>

- <span data-ttu-id="29e66-117">Jedinečné ID</span><span class="sxs-lookup"><span data-stu-id="29e66-117">Unique ID</span></span>
- <span data-ttu-id="29e66-118">Metoda HTTP</span><span class="sxs-lookup"><span data-stu-id="29e66-118">HTTP method</span></span>
- <span data-ttu-id="29e66-119">Identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="29e66-119">URI</span></span>
- <span data-ttu-id="29e66-120">Odchozí hlavičky požadavků</span><span class="sxs-lookup"><span data-stu-id="29e66-120">Outgoing request headers</span></span>

<span data-ttu-id="29e66-121">Položka protokolu odpovědi HTTP:</span><span class="sxs-lookup"><span data-stu-id="29e66-121">HTTP response log entry:</span></span>

- <span data-ttu-id="29e66-122">Doba trvání vstupně-výstupních operací (uplynulý čas)</span><span class="sxs-lookup"><span data-stu-id="29e66-122">Duration of I/O operation (time elapsed)</span></span>
- <span data-ttu-id="29e66-123">ID požadavku</span><span class="sxs-lookup"><span data-stu-id="29e66-123">Request ID</span></span>
- <span data-ttu-id="29e66-124">Stavový kód HTTP</span><span class="sxs-lookup"><span data-stu-id="29e66-124">HTTP status code</span></span>
- <span data-ttu-id="29e66-125">Fráze pro důvod HTTP</span><span class="sxs-lookup"><span data-stu-id="29e66-125">HTTP reason phrase</span></span>
- <span data-ttu-id="29e66-126">Hlavičky odpovědi</span><span class="sxs-lookup"><span data-stu-id="29e66-126">Response headers</span></span>
- <span data-ttu-id="29e66-127">Informace o chybě, pokud je k dispozici</span><span class="sxs-lookup"><span data-stu-id="29e66-127">Error information, when applicable</span></span>

<span data-ttu-id="29e66-128">Pro obsah požadavků a odpovědí:</span><span class="sxs-lookup"><span data-stu-id="29e66-128">For request and response content:</span></span>

- <span data-ttu-id="29e66-129">Stream obsahu jako text nebo bajtů v závislosti na záhlaví Content-Type.</span><span class="sxs-lookup"><span data-stu-id="29e66-129">Content stream as text or bytes depending on the Content-Type header.</span></span>
     > <span data-ttu-id="29e66-130">[! Poznámka} protokolování obsahu je ve výchozím nastavení zakázané.</span><span class="sxs-lookup"><span data-stu-id="29e66-130">[!NOTE} Content logging is disabled by default.</span></span> <span data-ttu-id="29e66-131">Pokud ho chcete povolit, `Diagnostics.IsLoggingContentEnabled` nastavte `true` na `ClientOptions`v.</span><span class="sxs-lookup"><span data-stu-id="29e66-131">To enable it, set `Diagnostics.IsLoggingContentEnabled` to `true` in `ClientOptions`.</span></span>

<span data-ttu-id="29e66-132">Výstup protokolů událostí je obvykle na jedné z těchto tří úrovní:</span><span class="sxs-lookup"><span data-stu-id="29e66-132">Event logs are output usually at one of these three levels:</span></span>

- <span data-ttu-id="29e66-133">Informativní pro události žádostí a odpovědí</span><span class="sxs-lookup"><span data-stu-id="29e66-133">Informational for request and response events</span></span>
- <span data-ttu-id="29e66-134">Upozornění pro chyby</span><span class="sxs-lookup"><span data-stu-id="29e66-134">Warning for errors</span></span>
- <span data-ttu-id="29e66-135">Verbose pro podrobné zprávy a protokolování obsahu</span><span class="sxs-lookup"><span data-stu-id="29e66-135">Verbose for detailed messages and content logging</span></span>

## <a name="enable-logging-with-built-in-methods"></a><span data-ttu-id="29e66-136">Povolit protokolování pomocí integrovaných metod</span><span class="sxs-lookup"><span data-stu-id="29e66-136">Enable logging with built-in methods</span></span>

<span data-ttu-id="29e66-137">Sada Azure SDK pro klientské knihovny .NET protokoluje události do trasování událostí pro Windows (ETW) prostřednictvím [ `EventSource` třídy](/dotnet/api/system.diagnostics.tracing.eventsource), která je typická pro .NET.</span><span class="sxs-lookup"><span data-stu-id="29e66-137">The Azure SDK for .NET client libraries log events to Event Tracing for Windows (ETW) via the [`EventSource` class](/dotnet/api/system.diagnostics.tracing.eventsource), which is typical for .NET.</span></span> <span data-ttu-id="29e66-138">Zdroje událostí umožňují používat strukturované protokolování v kódu aplikace s minimálními nároky na výkon.</span><span class="sxs-lookup"><span data-stu-id="29e66-138">Event sources allow you to use structured logging in your application code with a minimal performance overhead.</span></span> <span data-ttu-id="29e66-139">Chcete-li získat přístup k těmto protokolům událostí, je nutné zaregistrovat naslouchací proces událostí.</span><span class="sxs-lookup"><span data-stu-id="29e66-139">To gain access to these event logs, you need to register event listeners.</span></span>

<span data-ttu-id="29e66-140">Sada SDK obsahuje `Azure.Core.Diagnostics.AzureEventSourceListener` třídu (definovaná v balíčku NuGet Azure. Core), která obsahuje dvě statické metody, které zjednodušují protokolování vaší aplikace .NET: `CreateConsoleLogger` a. `CreateTraceLogger`</span><span class="sxs-lookup"><span data-stu-id="29e66-140">The SDK includes the `Azure.Core.Diagnostics.AzureEventSourceListener` class (defined in the Azure.Core NuGet package), which contains two static methods that simplify comprehensive logging for your .NET application: `CreateConsoleLogger` and `CreateTraceLogger`.</span></span> <span data-ttu-id="29e66-141">Tyto metody přijímají volitelný parametr, který určuje úroveň protokolu.</span><span class="sxs-lookup"><span data-stu-id="29e66-141">These methods take an optional parameter that specifies a log level.</span></span>

### <a name="log-to-the-console-window"></a><span data-ttu-id="29e66-142">Přihlaste se do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="29e66-142">Log to the console window</span></span>

<span data-ttu-id="29e66-143">Základní principem sady Azure SDK pro klientské knihovny .NET je zjednodušení možnosti Zobrazit komplexní protokoly v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="29e66-143">A core tenet of the Azure SDK for .NET client libraries is to simplify the ability to view comprehensive logs in real time.</span></span> <span data-ttu-id="29e66-144">`CreateConsoleLogger` Metoda umožňuje odeslat protokoly do okna konzoly s jedním řádkem kódu:</span><span class="sxs-lookup"><span data-stu-id="29e66-144">The `CreateConsoleLogger` method allows you to send logs to the console window with a single line of code:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a><span data-ttu-id="29e66-145">Protokolování do diagnostických trasování</span><span class="sxs-lookup"><span data-stu-id="29e66-145">Log to diagnostic traces</span></span>

<span data-ttu-id="29e66-146">Pokud implementujete naslouchací procesy trasování, můžete použít `CreateTraceLogger` metodu pro přihlášení ke standardnímu mechanismu trasování událostí .NET ([`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)).</span><span class="sxs-lookup"><span data-stu-id="29e66-146">If you implement trace listeners, you can use the `CreateTraceLogger` method to log to the standard .NET event tracing mechanism ([`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)).</span></span> <span data-ttu-id="29e66-147">Další informace o trasování událostí v rozhraní .NET naleznete v tématu [Trace Listeners](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners).</span><span class="sxs-lookup"><span data-stu-id="29e66-147">For more information on event tracing in .NET, see [Trace Listeners](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners).</span></span> <span data-ttu-id="29e66-148">Tento příklad určuje úroveň protokolu s podrobnostmi:</span><span class="sxs-lookup"><span data-stu-id="29e66-148">This example specifies a log level of verbose:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a><span data-ttu-id="29e66-149">Konfigurace vlastního protokolování</span><span class="sxs-lookup"><span data-stu-id="29e66-149">Configure custom logging</span></span>

<span data-ttu-id="29e66-150">Jak je uvedeno výše, je třeba registrovat naslouchací proces událostí, aby přijímal zprávy protokolu ze sady Azure SDK pro .NET.</span><span class="sxs-lookup"><span data-stu-id="29e66-150">As mentioned above, you need to register event listeners to receive log messages from the Azure SDK for .NET.</span></span> <span data-ttu-id="29e66-151">Pokud nechcete implementovat komplexní protokolování pomocí jedné z výše uvedených zjednodušených metod, můžete vytvořit instanci `AzureEventSourceListener` třídy a předat jí funkci zpětného volání, kterou píšete.</span><span class="sxs-lookup"><span data-stu-id="29e66-151">If you don’t want to implement comprehensive logging using one the simplified methods above, you can construct an instance of the `AzureEventSourceListener` class and pass it a callback function that you write.</span></span> <span data-ttu-id="29e66-152">Tato metoda obdrží zprávy protokolu, které můžete zpracovat, ale budete je potřebovat.</span><span class="sxs-lookup"><span data-stu-id="29e66-152">This method will receive log messages that you can process however you need to.</span></span> <span data-ttu-id="29e66-153">Kromě toho, když vytváříte instanci, můžete určit, jaké úrovně protokolu mají být zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="29e66-153">In addition, when you construct the instance, you can specify the log levels to include.</span></span>

<span data-ttu-id="29e66-154">Následující příklad vytvoří naslouchací proces událostí, který se přihlásí do konzoly s vlastní zprávou a je filtrován na události Azure Core podrobností úrovně.</span><span class="sxs-lookup"><span data-stu-id="29e66-154">The following example creates an event listener that logs to the console with a custom message, and is filtered to Azure core events of the level verbose.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="29e66-155">Další kroky</span><span class="sxs-lookup"><span data-stu-id="29e66-155">Next steps</span></span>

- [<span data-ttu-id="29e66-156">Povolit protokolování diagnostiky pro aplikace v Azure App Service</span><span class="sxs-lookup"><span data-stu-id="29e66-156">Enable diagnostics logging for apps in Azure App Service</span></span>](https://docs.microsoft.com/azure/app-service/troubleshoot-diagnostic-logs)
- <span data-ttu-id="29e66-157">Kontrola možností [protokolování a auditování zabezpečení Azure](https://docs.microsoft.com/azure/security/fundamentals/log-audit)</span><span class="sxs-lookup"><span data-stu-id="29e66-157">Review [Azure security logging and auditing](https://docs.microsoft.com/azure/security/fundamentals/log-audit) options</span></span>
- <span data-ttu-id="29e66-158">Naučte se pracovat s [protokoly platformy Azure](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview) .</span><span class="sxs-lookup"><span data-stu-id="29e66-158">Learn how to work with [Azure platform logs](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview)</span></span>
- <span data-ttu-id="29e66-159">Přečtěte si další informace o [protokolování a trasování .NET Core](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing)</span><span class="sxs-lookup"><span data-stu-id="29e66-159">Read more about [.NET Core logging and tracing](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing)</span></span>
