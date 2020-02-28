---
title: Co je nového v .NET Core 2.2
description: Přečtěte si o nových funkcích, které najdete v .NET Core 2,2.
dev_langs:
- csharp
- vb
ms.date: 12/04/2018
ms.openlocfilehash: e045c39240c99777d05ca86ee0a8cd1fa4309c4f
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156579"
---
# <a name="whats-new-in-net-core-22"></a>Co je nového v .NET Core 2.2

.NET Core 2,2 obsahuje vylepšení při nasazení aplikace, zpracování událostí pro služby runtime, ověřování pro Azure SQL Database, výkon kompilátoru JIT a vkládání kódu před provedením metody `Main`.

## <a name="new-deployment-mode"></a>Nový režim nasazení

Počínaje rozhraním .NET Core 2,2 můžete nasadit [spustitelné soubory závislé na rozhraních](../deploying/index.md#publish-runtime-dependent), které jsou soubory **. exe** namísto souborů **. dll** . Funguje podobně jako u nasazení závislých na rozhraních, v závislosti na architektuře (FDE) se pořád spoléhá na přítomnost sdílené systémové verze .NET Core, která se má spustit. Vaše aplikace obsahuje jenom váš kód a všechny závislosti třetích stran. Na rozdíl od nasazení závislých na rozhraních FDEs jsou specifické pro platformu.

Tento nový režim nasazení má odlišnou výhodu při vytváření spustitelného souboru místo knihovny, což znamená, že můžete svou aplikaci spustit přímo, aniž byste vyvolali `dotnet` jako první.

## <a name="core"></a>Jádro

**Zpracování událostí ve službách za běhu**

Chcete-li pochopit, jak ovlivňují vaši aplikaci, může být často vhodné monitorovat použití služeb runtime, jako je například GC, JIT, a nevlákenná vlákna. V systémech Windows to se obvykle provádí monitorováním událostí ETW aktuálního procesu. I když to bude i nadále fungovat dobře, není vždy možné používat trasování událostí pro Windows, pokud pracujete v prostředí s nízkým oprávněním nebo v systému Linux nebo macOS.

Počínaje .NET Core 2,2 události CoreCLR se teď dají spotřebovat pomocí třídy <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType>. Tyto události popisují chování takových služeb za běhu jako GC, JIT, fondu a spolupráci. Jedná se o stejné události, které jsou přístupné jako součást zprostředkovatele ETW CoreCLR.  Díky tomu můžou aplikace tyto události spotřebovat nebo použít transportní mechanismus k jejich posílání do agregační služby telemetrie. Můžete se podívat, jak se přihlásit k odběru událostí v následující ukázce kódu:

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

Kromě toho .NET Core 2,2 přidá následující dvě vlastnosti do třídy <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> k poskytnutí dalších informací o událostech ETW:

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a>Data

**Ověřování AAD pro databáze SQL Azure s vlastností SqlConnection. AccessToken**

Počínaje rozhraním .NET Core 2,2 je možné k ověřování ve službě Azure SQL Database použít přístupový token vydaný Azure Active Directory. Pro podporu přístupových tokenů byla vlastnost <xref:System.Data.SqlClient.SqlConnection.AccessToken> přidána do třídy <xref:System.Data.SqlClient.SqlConnection>. Pokud chcete využít výhod ověřování AAD, Stáhněte si balíček NuGet System. data. SqlClient verze 4,6. Aby bylo možné funkci používat, můžete získat hodnotu přístupového tokenu pomocí [Active Directory Authentication Library pro .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) , které jsou obsaženy v balíčku NuGet [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) .

## <a name="jit-compiler-improvements"></a>Vylepšení kompilátoru JIT

**Vrstvená kompilace zůstává funkcí výslovných přihlášení.**

V .NET Core 2,1 kompilátor JIT implementoval novou technologii kompilátoru, *vrstvenou kompilaci*, jako funkci opt-in. Cílem vrstvené kompilace je zlepšení výkonu. Jedním z důležitých úloh prováděných kompilátorem JIT je optimalizace provádění kódu. Pro málo používané cesty kódu však může kompilátor strávit více času optimalizací kódu, než modul runtime zpracovává neoptimalizovaný kód. Vrstvená kompilace přináší dvě fáze kompilace JIT:

- **První vrstva**, která generuje kód co nejrychleji.

- **Druhá vrstva**, která generuje optimalizovaný kód pro tyto metody, které jsou spouštěny často. Druhá vrstva kompilace se paralelně provádí za účelem zvýšení výkonu.

Informace o vylepšení výkonu, které může být výsledkem vrstvené kompilace, najdete v tématu [oznamujeme rozhraní .NET Core 2,2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).

Ve výchozím nastavení je v .NET Core 2,2 Preview 2 zapnutá vrstvená kompilace. Rozhodli jsme se však, že ve výchozím nastavení není stále připraveno povolit vrstvenou kompilaci. Takže v .NET Core 2,2 se vrstvená kompilace bude i nadále jednat o funkci výslovného souhlasu. Informace o tom, jak se na vrstvenou kompilaci rozvrstvit, najdete v tématu [vylepšení kompilátoru JIT](dotnet-core-2-1.md#jit-compiler-improvements) v tématu [co je nového v .NET Core 2,1](dotnet-core-2-1.md).

## <a name="runtime"></a>Modul runtime

**Vložení kódu před provedením metody Main**

Počínaje .NET Core 2,2 můžete použít spouštěcí zavěšení pro vložení kódu před spuštěním metody Main aplikace. Spouštěcí háky umožňují hostiteli přizpůsobit chování aplikací poté, co byly nasazeny, aniž by museli aplikaci znovu kompilovat nebo měnit.

Očekáváme, že poskytovatelé hostingu definují vlastní konfiguraci a zásady, včetně nastavení, která mohou mít vliv na chování při načítání hlavního vstupního bodu, například <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> chování. Zavěšení lze použít k nastavení trasování nebo injektáže telemetrie, k nastavení zpětných volání pro zpracování nebo k definování jiného chování závislého na prostředí. Zavěšení je oddělené od vstupního bodu, aby se kód uživatele nemuselo upravovat.

Další informace najdete v tématu [spouštěcí zavěšení hostitele](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) .

## <a name="see-also"></a>Viz také

- [Co je nového v .NET Core](index.md)
- [Co je nového v ASP.NET Core 2,2](/aspnet/core/release-notes/aspnetcore-2.2)
- [Nové funkce v EF Core 2,2](/ef/core/what-is-new/ef-core-2.2)
