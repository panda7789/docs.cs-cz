---
title: Protokolování pomocí sady Azure SDK pro .NET
description: Naučte se, jak povolit protokolování pomocí sady Azure SDK pro klientské knihovny .NET.
ms.date: 03/20/2020
ms.custom: azure-sdk-dotnet
ms.author: casoper
author: camsoper
ms.openlocfilehash: 5a1fb35aeca034a7cdd1caa813a3839919a5f926
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174935"
---
# <a name="logging-with-the-azure-sdk-for-net"></a>Protokolování pomocí sady Azure SDK pro .NET

[Sada Azure SDK](https://azure.microsoft.com/downloads/) pro klientské knihovny .NET zahrnuje možnost protokolování operací klientské knihovny. Díky tomu můžete monitorovat žádosti a odpovědi na vstupně-výstupní operace, které klientské knihovny využívají ke službám Azure. Protokoly se obvykle používají k ladění nebo diagnostikování potíží s komunikací. Tento článek popisuje tři přístupy k povolení protokolování v sadě Azure SDK pro .NET:

- Přihlaste se do okna konzoly.
- Protokolování trasování diagnostiky .NET
- Konfigurace vlastního protokolování

> [!IMPORTANT]
> Tento článek se týká klientských knihoven, které používají nejnovější verze sady Azure SDK pro .NET. Pokud chcete zjistit, jestli je knihovna podporovaná, přečtěte si seznam [nejnovějších verzí sady Azure SDK](https://azure.github.io/azure-sdk/releases/latest/index.html). Pokud vaše aplikace používá starší verzi klientských knihoven Azure SDK, přečtěte si konkrétní pokyny v příslušné dokumentaci ke službě.

## <a name="log-information"></a>Informace protokolu

Sada SDK protokoluje následující informace, upravené hodnoty dotazů a hodnot hlaviček pro odebrání osobních údajů.

Položka protokolu požadavku HTTP:

- Jedinečné ID
- Metoda HTTP
- Identifikátor URI
- Odchozí hlavičky požadavků

Položka protokolu odpovědi HTTP:

- Doba trvání vstupně-výstupních operací (uplynulý čas)
- ID požadavku
- Stavový kód HTTP
- Fráze pro důvod HTTP
- Hlavičky odpovědi
- Informace o chybě, pokud je k dispozici

Pro obsah požadavků a odpovědí:

- Stream obsahu jako text nebo bajtů v závislosti na záhlaví Content-Type.
     > [! Poznámka} protokolování obsahu je ve výchozím nastavení zakázané. Pokud ho chcete povolit, nastavte `Diagnostics.IsLoggingContentEnabled` na `true` v `ClientOptions` .

Výstup protokolů událostí je obvykle na jedné z těchto tří úrovní:

- Informativní pro události žádostí a odpovědí
- Upozornění pro chyby
- Verbose pro podrobné zprávy a protokolování obsahu

## <a name="enable-logging-with-built-in-methods"></a>Povolit protokolování pomocí integrovaných metod

Sada Azure SDK pro klientské knihovny .NET protokoluje události do trasování událostí pro Windows (ETW) prostřednictvím [ `EventSource` třídy](/dotnet/api/system.diagnostics.tracing.eventsource), která je typická pro .NET. Zdroje událostí umožňují používat strukturované protokolování v kódu aplikace s minimálními nároky na výkon. Chcete-li získat přístup k těmto protokolům událostí, je nutné zaregistrovat naslouchací proces událostí.

Sada SDK obsahuje `Azure.Core.Diagnostics.AzureEventSourceListener` třídu (definovaná v balíčku NuGet Azure. Core), která obsahuje dvě statické metody, které zjednodušují protokolování vaší aplikace .NET: `CreateConsoleLogger` a `CreateTraceLogger` . Tyto metody přijímají volitelný parametr, který určuje úroveň protokolu.

### <a name="log-to-the-console-window"></a>Přihlaste se do okna konzoly.

Základní principem sady Azure SDK pro klientské knihovny .NET je zjednodušení možnosti Zobrazit komplexní protokoly v reálném čase. `CreateConsoleLogger`Metoda umožňuje odeslat protokoly do okna konzoly s jedním řádkem kódu:

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a>Protokolování do diagnostických trasování

Pokud implementujete naslouchací procesy trasování, můžete použít `CreateTraceLogger` metodu pro přihlášení ke standardnímu mechanismu trasování událostí .NET ( [`System.Diagnostics.Tracing`](/dotnet/api/system.diagnostics.tracing) ). Další informace o trasování událostí v rozhraní .NET naleznete v tématu [Trace Listeners](/dotnet/framework/debug-trace-profile/trace-listeners). Tento příklad určuje úroveň protokolu s podrobnostmi:

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a>Konfigurace vlastního protokolování

Jak je uvedeno výše, je třeba registrovat naslouchací proces událostí, aby přijímal zprávy protokolu ze sady Azure SDK pro .NET. Pokud nechcete implementovat komplexní protokolování pomocí jedné z výše uvedených zjednodušených metod, můžete vytvořit instanci `AzureEventSourceListener` třídy a předat jí funkci zpětného volání, kterou píšete. Tato metoda obdrží zprávy protokolu, které můžete zpracovat, ale budete je potřebovat. Kromě toho, když vytváříte instanci, můžete určit, jaké úrovně protokolu mají být zahrnuty.

Následující příklad vytvoří naslouchací proces událostí, který se přihlásí do konzoly s vlastní zprávou a je filtrován na události Azure Core podrobností úrovně.

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

- [Povolit protokolování diagnostiky pro aplikace v Azure App Service](/azure/app-service/troubleshoot-diagnostic-logs)
- Kontrola možností [protokolování a auditování zabezpečení Azure](/azure/security/fundamentals/log-audit)
- Naučte se pracovat s [protokoly platformy Azure](/azure/azure-monitor/platform/platform-logs-overview) .
- Přečtěte si další informace o [protokolování a trasování .NET Core](/dotnet/core/diagnostics/logging-tracing)
