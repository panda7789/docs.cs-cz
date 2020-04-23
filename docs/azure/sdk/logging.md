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
# <a name="logging-with-the-azure-sdk-for-net"></a>Protokolování pomocí sady Azure SDK pro rozhraní .NET

Sada [Azure SDK](https://azure.microsoft.com/downloads/) pro klientské knihovny .NET zahrnuje možnost protokolovat operace klientské knihovny. To umožňuje sledovat vstupně-va požadavky a odpovědi, které klientské knihovny dělají do služeb Azure. Protokoly se obvykle používají k ladění nebo diagnostikovat problémy s komunikací. Tento článek popisuje tři přístupy k povolení protokolování pomocí sady Azure SDK pro rozhraní .NET:

- Přihlásit se do okna konzoly
- Protokolovat do tras diagnostiky .NET
- Konfigurace vlastního protokolování

> [!IMPORTANT]
> Tento článek se vztahuje na klientské knihovny, které používají nejnovější verze sady Azure SDK pro rozhraní .NET. Chcete-li zjistit, zda je knihovna podporovaná, podívejte se na seznam [nejnovějších verzí sady Azure SDK](https://azure.github.io/azure-sdk/releases/latest/index.html). Pokud vaše aplikace používá starší verzi klientských knihoven Sady Azure SDK, naleznete konkrétní pokyny v příslušné dokumentaci ke službě.

## <a name="log-information"></a>Informace protokolu

Sada SDK protokoluje následující informace, dezinfekce parametrický dotaz a hodnoty záhlaví k odebrání osobních údajů.

Zadání protokolu požadavků HTTP:

- Jedinečné ID
- Metoda HTTP
- Identifikátor URI
- Hlavičky odchozích požadavků

Zadání protokolu odpovědí HTTP:

- Doba trvání vstupně-to-va/v provozu (uplynulý čas)
- ID požadavku
- Stavový kód HTTP
- Fráze důvod http
- Hlavičky odpovědi
- Informace o chybě, je-li k dispozici

Pro obsah požadavku a odpovědi:

- Obsah proudí jako text nebo bajty v závislosti na záhlaví Typu obsahu.
     > [! POZNÁMKA} Protokolování obsahu je ve výchozím nastavení zakázáno. Chcete-li jej `Diagnostics.IsLoggingContentEnabled` `true` povolit, nastavte v `ClientOptions`.

Protokoly událostí jsou výstup obvykle na jedné z těchto tří úrovní:

- Informace pro události požadavku a odpovědi
- Upozornění na chyby
- Podrobné informace o detailních zprávách a protokolování obsahu

## <a name="enable-logging-with-built-in-methods"></a>Povolení protokolování pomocí integrovaných metod

Sada Azure SDK pro klientské knihovny .NET protokoluje události protokolu do trasování událostí pro Windows (ETW) prostřednictvím [ `EventSource` třídy](/dotnet/api/system.diagnostics.tracing.eventsource), což je typické pro rozhraní .NET. Zdroje událostí umožňují používat strukturované protokolování v kódu aplikace s minimální režií výkonu. Chcete-li získat přístup k těmto protokolům událostí, je třeba zaregistrovat posluchače událostí.

Sada SDK `Azure.Core.Diagnostics.AzureEventSourceListener` zahrnuje třídu (definovanou v balíčku Azure.Core NuGet), která obsahuje dvě `CreateConsoleLogger` statické `CreateTraceLogger`metody, které zjednodušují komplexní protokolování pro vaši aplikaci .NET: a . Tyto metody trvat volitelný parametr, který určuje úroveň protokolu.

### <a name="log-to-the-console-window"></a>Přihlásit se do okna konzoly

Základním principem sady Azure SDK pro klientské knihovny .NET je zjednodušit možnost zobrazení komplexních protokolů v reálném čase. Metoda `CreateConsoleLogger` umožňuje odesílat protokoly do okna konzoly s jedním řádkem kódu:

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a>Protokolovat do diagnostických tras

Pokud implementujete naslouchací procesy trasování, můžete použít metodu `CreateTraceLogger` k přihlášení ke standardnímu mechanismu trasování událostí .NET ([`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)). Další informace o trasování událostí v rozhraní .NET naleznete v [tématu Posluchači trasování](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners). Tento příklad určuje úroveň protokolu podrobné:

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a>Konfigurace vlastního protokolování

Jak bylo uvedeno výše, je třeba zaregistrovat posluchače událostí pro příjem zpráv protokolu z sady Azure SDK pro rozhraní .NET. Pokud nechcete implementovat komplexní protokolování pomocí jedné zjednodušené metody výše, `AzureEventSourceListener` můžete vytvořit instanci třídy a předat ji funkci zpětného volání, kterou píšete. Tato metoda obdrží zprávy protokolu, které můžete zpracovat však je třeba. Kromě toho při vytváření instance, můžete určit úrovně protokolu zahrnout.

Následující příklad vytvoří naslouchací proces událostí, který se přihlásí ke konzole s vlastní zprávou a je filtrován na základní události Azure úrovně verbose.

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

## <a name="next-steps"></a>Další kroky

- [Povolení protokolování diagnostiky aplikací ve službě Azure App Service](https://docs.microsoft.com/azure/app-service/troubleshoot-diagnostic-logs)
- Kontrola možností [protokolování zabezpečení azure a auditování](https://docs.microsoft.com/azure/security/fundamentals/log-audit)
- Zjistěte, jak pracovat s [protokoly platformy Azure](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview)
- Další informace o [protokolování a trasování jádra .NET](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing)
