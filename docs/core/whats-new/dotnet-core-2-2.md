---
title: Co je nového v .NET Core 2.2
description: Další informace o nových funkcích v rozhraní .NET Core 2.2.
dev_langs:
- csharp
- vb
ms.date: 12/04/2018
ms.openlocfilehash: e045c39240c99777d05ca86ee0a8cd1fa4309c4f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156579"
---
# <a name="whats-new-in-net-core-22"></a>Co je nového v .NET Core 2.2

.NET Core 2.2 zahrnuje vylepšení v nasazení aplikací, zpracování událostí pro runtime služby, ověřování do databází Azure SQL, výkon kompilátoru JIT a vkládání kódu před spuštěním `Main` metody.

## <a name="new-deployment-mode"></a>Nový režim nasazení

Počínaje rozhraním .NET Core 2.2 můžete nasadit [spustitelné soubory závislé na rozhraní](../deploying/index.md#publish-runtime-dependent), což jsou soubory **EXE** namísto souborů **DLL.** Funkčně podobné nasazení závislé na rozhraní, spustitelné soubory závislé na rámci (FDE) stále spoléhají na přítomnost sdílené verze rozhraní .NET Core pro celý systém ke spuštění. Vaše aplikace obsahuje pouze váš kód a všechny závislosti třetích stran. Na rozdíl od nasazení závislých na rámci jsou FTE specifické pro platformu.

Tento nový režim nasazení má výraznou výhodu v budování spustitelného souboru namísto knihovny, což znamená, že aplikaci můžete spustit přímo bez vyvolání. `dotnet`

## <a name="core"></a>Jádro

**Zpracování událostí ve službách runtime**

Často můžete chtít sledovat použití služeb runtime vaší aplikace, jako je například GC, JIT a ThreadPool, abyste pochopili, jak ovlivňují vaši aplikaci.V systémech Windows se to obvykle provádí sledováním událostí ETW aktuálního procesu.I když to i nadále funguje dobře, není vždy možné používat ETW, pokud používáte v prostředí s nízkými oprávněními nebo na Linuxu nebo macOS.

Počínaje .NET Core 2.2, CoreCLR události lze <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> nyní spotřebovávat pomocí třídy. Tyto události popisují chování těchto runtime služeb jako GC, JIT, ThreadPool a interop. Jedná se o stejné události, které jsou vystaveny jako součást poskytovatele CoreCLR ETW.To umožňuje aplikacím využívat tyto události nebo použít mechanismus přenosu k jejich odeslání do služby agregace telemetrie. Můžete vidět, jak se přihlásit k odběru událostí v následující ukázce kódu:

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

Kromě toho .NET Core 2.2 přidá následující <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> dvě vlastnosti třídy poskytnout další informace o událostech ETW:

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a>Data

**Ověřování AAD do databází Azure SQL s vlastností SqlConnection.AccessToken**

Počínaje rozhraním .NET Core 2.2 lze přístupový token vydaný službou Azure Active Directory použít k ověření do databáze Azure SQL. Pro podporu přístupových <xref:System.Data.SqlClient.SqlConnection.AccessToken> tokenů byla vlastnost <xref:System.Data.SqlClient.SqlConnection> přidána do třídy. Chcete-li využít výhod ověřování AAD, stáhněte si verzi 4.6 balíčku System.Data.SqlClient NuGet. Chcete-li tuto funkci použít, můžete získat hodnotu přístupového tokenu pomocí [knihovny ověřování služby Active Directory pro rozhraní .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) obsažené v balíčku [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet.

## <a name="jit-compiler-improvements"></a>Vylepšení kompilátoru JIT

**Vrstvená kompilace zůstává funkcí opt-in**

V rozhraní .NET Core 2.1 implementoval kompilátor JIT novou technologii kompilátoru, *vrstvenou kompilaci*jako funkci opt-in. Cílem vrstvené kompilace je lepší výkon. Jedním z důležitých úkolů prováděných kompilátorem JIT je optimalizace spuštění kódu. Pro málo používané cesty kódu však kompilátor může strávit více času optimalizací kódu než modul runtime, který stráví prováděním neoptimalizovaného kódu. Vrstvená kompilace zavádí dvě fáze kompilace JIT:

- **První vrstva**, která generuje kód co nejrychleji.

- **Druhá vrstva**, která generuje optimalizovaný kód pro ty metody, které jsou často spouštěny. Druhá vrstva kompilace se provádí paralelně pro zvýšení výkonu.

Informace o zlepšení výkonu, které může být výsledkem vrstvené kompilace, naleznete [v tématu Oznámení .NET Core 2.2 Náhled 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).

V rozhraní .NET Core 2.2 Preview 2 byla ve výchozím nastavení povolena vrstvená kompilace. Rozhodli jsme se však, že stále nejsme připraveni povolit vrstvené kompilace ve výchozím nastavení. Takže v rozhraní .NET Core 2.2 je vrstvená kompilace i nadále funkcí opt-in. Informace o přihlášení k vrstvené kompilaci najdete v tématu [Vylepšení kompilátoru Jit](dotnet-core-2-1.md#jit-compiler-improvements) v [tématu Co je nového v rozhraní .NET Core 2.1](dotnet-core-2-1.md).

## <a name="runtime"></a>Modul runtime

**Vkládání kódu před spuštěním Hlavní metody**

Počínaje rozhraním .NET Core 2.2 můžete použít spouštěcí hák k vložení kódu před spuštěním metody Main aplikace. Spouštěcí háčky umožňují hostiteli přizpůsobit chování aplikací po jejich nasazení bez nutnosti překompilovat nebo změnit aplikaci.

Očekáváme, že poskytovatelé hostingu definovat vlastní konfiguraci a zásady, včetně nastavení, <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> které potenciálně ovlivňují chování zatížení hlavnívstupní bod, jako je například chování. Háček lze nastavit trasování nebo vkládání telemetrie, nastavit zpětná volání pro zpracování nebo definovat jiné chování závislé na prostředí. Háček je oddělen od vstupního bodu, takže uživatelský kód není nutné měnit.

Další informace naleznete [v tématu Háček pro spuštění hostitele.](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md)

## <a name="see-also"></a>Viz také

- [Co je nového v .NET Core](index.md)
- [Co je nového v ASP.NET Core 2.2](/aspnet/core/release-notes/aspnetcore-2.2)
- [Nové funkce v EF Core 2.2](/ef/core/what-is-new/ef-core-2.2)
