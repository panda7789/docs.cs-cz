---
title: Co je nového v .NET Core 2.2
description: Informace o nových funkcích v rozhraní .NET Core 2.2.
dev_langs:
- csharp
- vb
author: rpetrusha
ms.author: ronpet
ms.date: 12/04/2018
ms.openlocfilehash: 49a65dd44159e9800f7cf50a1edaa3d9e9b82e47
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677263"
---
# <a name="whats-new-in-net-core-22"></a>Co je nového v .NET Core 2.2

.NET core 2.2 zahrnuje vylepšení v nasazení aplikací, zpracování událostí pro služby modulu runtime, ověřování pro Azure SQL Database, výkon kompilátoru JIT a injektáž kódu před spuštěním `Main` metody.

## <a name="new-deployment-mode"></a>Nový režim nasazení

Spouští se s nástroji .NET Core 2.2, můžete nasadit [závisí na architektuře spustitelných souborů](../deploying/index.md#framework-dependent-executables-fde), které jsou **.exe** soubory místo **.dll** soubory. Funkčně podobný nasazení závisí na architektuře, závisí na architektuře spustitelných souborů (FDE) stále spoléhat na přítomnost sdílené systémová verzi .NET Core pro spuštění. Vaše aplikace obsahuje pouze váš kód a případných závislostí třetích stran. Na rozdíl od nasazení závisí na architektuře FDEs jsou specifické pro platformu.

Tento nový režim nasazení má odlišné výhod sestavení spustitelného souboru namísto knihovny, což znamená, že spustíte svou aplikaci přímo bez vyvolání `dotnet` první.

## <a name="core"></a>Jádro

**Zpracování událostí v modulu runtime služeb**

Často můžete chtít sledovat vaše aplikace při používání služby modulu runtime, jako je například uvolňování paměti, JIT a fondu vláken, abyste pochopili, jak by mohly mít dopad vaší aplikace. V systémech Windows obvykle stačí monitorování událostí trasování událostí pro Windows aktuálního procesu. I když toto zůstává fungovat dobře, není vždy možné použít trasování událostí pro Windows, pokud používáte v prostředí s nízkou úrovní oprávnění, nebo v Linuxu nebo macOS. 

Spouští se s nástroji .NET Core 2.2, události CoreCLR se teď dají zpracovat pomocí <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> třídy. Tyto události popisují chování takové služby modulu runtime jako uvolňování paměti, JIT, fondu vláken a zprostředkovatele komunikace s objekty. Toto jsou stejné události, které jsou vystaveny jako součást poskytovatele trasování událostí pro Windows CoreCLR.  To umožňuje aplikacím používat tyto události nebo použít mechanismus přenosu k odesílání telemetrických dat služby agregace. Uvidíte jak přihlášení k odběru událostí v následujícím příkladu kódu:

```csharp
internal sealed class SimpleEventListener : EventListener
{
    // Called whenever an EventSource is created.
    protected override void OnEventSourceCreated(EventSource eventSource)
    {
        // Watch for the .NET runtime EventSource and enable all of its events.
        if (eventSource.Name.Equals("Microsoft-Windows-DotNETRuntime"))
        {
            EnableEvents(eventSource, EventLevel.Verbose, (EventKeywords)(-1));
        }
    }

    // Called whenever an event is written.
    protected override void OnEventWritten(EventWrittenEventArgs eventData)
    {
        // Write the contents of the event to the console.
        Console.WriteLine($"ThreadID = {eventData.OSThreadId} ID = {eventData.EventId} Name = {eventData.EventName}");
        for (int i = 0; i < eventData.Payload.Count; i++)
        {
            string payloadString = eventData.Payload[i]?.ToString() ?? string.Empty;
            Console.WriteLine($"\tName = \"{eventData.PayloadNames[i]}\" Value = \"{payloadString}\"");
        }
        Console.WriteLine("\n");
    }
}
```

Kromě toho přidá následující dvě vlastnosti do .NET Core 2.2 <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> třídy lze zadat další informace o trasování událostí pro Windows:

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a>Data

**Ověřování AAD k databázím Azure SQL s vlastností SqlConnection.AccessToken**

Spouští se s nástroji .NET Core 2.2, přístupový token vydala Azure Active Directory je možné k ověření ke službě Azure SQL database. Pro podporu přístupových tokenů <xref:System.Data.SqlClient.SqlConnection.AccessToken> byla přidána vlastnost <xref:System.Data.SqlClient.SqlConnection> třídy. Abyste mohli využívat ověřování AAD, stáhněte si verzi 4.6 balíček System.Data.SqlClient NuGet. Chcete-li použít funkci, můžete získat přístup pomocí tokenu hodnotu [Active Directory Authentication Library pro .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) součástí [ `Microsoft.IdentityModel.Clients.ActiveDirectory` ](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) balíček NuGet.

## <a name="jit-compiler-improvements"></a>Vylepšení kompilátoru JIT

**Vrstvené kompilace zůstává funkce opt-in**

V rozhraní .NET Core 2.1, kompilátor JIT implementovat novou technologii kompilátoru *vrstvené kompilace*, jako funkce opt-in. Cílem vrstvené kompilace je vylepšení výkonu. Mezi důležité úlohy prováděné kompilátorem JIT je optimalizace spuštění kódu. Cesty málo používané kódu ale může kompilátor věnovat víc času než modul runtime stráví spuštěním kódu neoptimalizované optimalizace kódu. Vrstvené kompilace zavádí dvě fáze kompilace JIT:

- A **první úroveň**, který generuje kód co nejrychleji.

- A **druhé vrstvy**, který generuje optimalizovaný kód pro tyto metody, které jsou spouštěny často. Druhá vrstva kompilace provádí paralelní pro lepší výkon.

Informace o vylepšení výkonu, které můžou být výsledkem kompilace vrstvený, naleznete v tématu [Ohlašujeme .NET Core 2.2 ve verzi Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).

V rozhraní .NET Core 2.2 ve verzi Preview 2 vrstvené kompilace byla povolena ve výchozím nastavení. Ale jsme jste se rozhodli, že budeme připravení stále není ve výchozím nastavení povolena vrstvené kompilace. Takže v .NET Core 2.2 vrstvené kompilace nadále funkce opt-in. Informace o vyjádření výslovného souhlasu s vrstvené kompilace, naleznete v tématu [vylepšení kompilátoru Jit](dotnet-core-2-1.md#jit-compiler-improvements) v [co je nového v .NET Core 2.1](dotnet-core-2-1.md).

## <a name="runtime"></a>Modul runtime

**Vkládání kódu před spuštěním metody Main**

Spouští se s nástroji .NET Core 2.2, vám pomůže spuštění hook vložení kódu před spuštěním aplikace metodu Main. Spouštění zachytávání umožňují hostitele po jejich nasazení bez nutnosti znovu kompilovat nebo změnit aplikaci přizpůsobit chování aplikace.

Očekáváme, že poskytovatelům hostingu definovat vlastní konfigurace a zásad, včetně nastavení, které potenciálně ovlivňují chování zatížení hlavní vstupní bod, jako <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> chování. Volání je možné nastavit trasování nebo shromažďování telemetrických vkládání, nastavit zpětná volání pro zpracování nebo definovat další chování závislé na prostředí. Volání je oddělené od vstupní bod tak, aby kód uživatele není potřeba upravit.

Zobrazit [hook spuštění hostitele](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) Další informace.

## <a name="see-also"></a>Viz také:

- [Co je nového v .NET Core](index.md)
- [Co je nového v ASP.NET Core 2.2](/aspnet/core/release-notes/aspnetcore-2.2)
- [Novinky v EF Core 2.2](/ef/core/what-is-new/ef-core-2.2)
