---
ms.openlocfilehash: f561550d57e98a515fa3bdf56eea1dc1759b4e69
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2020
ms.locfileid: "88025012"
---
## <a name="available-counters"></a>Available counters

V rámci různých balíčků .NET jsou základní metriky uvolňování paměti (GC), JIT (just-in-time), sestavení, výjimek, práce s vlákny, sítě a webovými požadavky publikovány pomocí EventCounters.

### <a name="systemruntime-counters"></a>Čítače "System. Runtime"

Následující čítače jsou publikovány jako součást modulu .NET runtime a jsou udržovány v [`RuntimeEventSource.cs`](https://github.com/dotnet/coreclr/blob/master/src/System.Private.CoreLib/src/System/Diagnostics/Eventing/RuntimeEventSource.cs) .

| Čítač | Popis |
|--|--|
| :::no-loc text="% Time in GC since last GC"::: (`time-in-gc`) | Procento času v GC od posledního GC |
| :::no-loc text="Allocation Rate"::: (`alloc-rate`) | Sazba přidělení v bajtech |
| :::no-loc text="CPU Usage"::: (`cpu-usage`) | Procento využití procesoru |
| :::no-loc text="Exception Count"::: (`exception-count`) | Počet výjimek, ke kterým došlo |
| :::no-loc text="GC Heap Size"::: (`gc-heap-size`) | Počet bajtů, které se mají přidělit na základě<xref:System.GC.GetTotalMemory(System.Boolean)?displayProperty=nameWithType> |
| :::no-loc text="Gen 0 GC Count"::: (`gen-0-gc-count`) | Počet výskytů GC pro gen 0 |
| :::no-loc text="Gen 0 Size"::: (`gen-0-size`) | Počet bajtů pro GC s 0. generace |
| :::no-loc text="Gen 1 GC Count"::: (`gen-1-gc-count`) | Kolikrát došlo k GC pro Gen 1 |
| :::no-loc text="Gen 1 Size"::: (`gen-1-size`) | Počet bajtů pro GC 1. generace |
| :::no-loc text="Gen 2 GC Count"::: (`gen-2-gc-count`) | Kolikrát došlo k GC pro obecné 2 |
| :::no-loc text="Gen 2 Size"::: (`gen-2-size`) | Počet bajtů pro GC generace 2 |
| :::no-loc text="LOH Size"::: (`loh-size`) | Počet bajtů pro GC pro Gen 3 |
| :::no-loc text="Monitor Lock Contention Count"::: (`monitor-lock-contention-count`) | Počet sporů při pokusu o provedení zámku monitoru na základě<xref:System.Threading.Monitor.LockContentionCount?displayProperty=nameWithType> |
| :::no-loc text="Number of Active Timers"::: (`active-timer-count`) | Počet <xref:System.Threading.Timer> aktuálně aktivních instancí na základě<xref:System.Threading.Timer.ActiveCount?displayProperty=nameWithType> |
| :::no-loc text="Number of Assemblies Loaded"::: (`assembly-count`) | Počet <xref:System.Reflection.Assembly> instancí načtených do procesu v určitém časovém okamžiku |
| :::no-loc text="ThreadPool Completed Work Item Count"::: (`threadpool-completed-items-count`) | Počet pracovních položek, které byly doposud zpracovány v<xref:System.Threading.ThreadPool> |
| :::no-loc text="ThreadPool Queue Length"::: (`threadpool-queue-length`) | Počet pracovních položek, které jsou aktuálně zařazeny do fronty ke zpracování v<xref:System.Threading.ThreadPool> |
| :::no-loc text="ThreadPool Thread Count"::: (`threadpool-thread-count`) | Počet vláken fondu vláken, které aktuálně existují v <xref:System.Threading.ThreadPool> závislosti na<xref:System.Threading.ThreadPool.ThreadCount?displayProperty=nameWithType> |
| :::no-loc text="Working Set"::: (`working-set`) | Velikost fyzické paměti namapované na kontext procesu v bodu v čase – základ<xref:System.Environment.WorkingSet?displayProperty=nameWithType> |

### <a name="microsoftaspnetcorehosting-counters"></a>Čítače "Microsoft. AspNetCore. hosting"

Následující čítače jsou publikovány jako součást [ASP.NET Core](/aspnet/core) a jsou udržovány v [`HostingEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/master/src/Hosting/Hosting/src/Internal/HostingEventSource.cs) .

| Čítač | Popis |
|--|--|
| :::no-loc text="Current Requests"::: (`current-requests`) | Celkový počet požadavků, které byly spuštěny, ale nebyly dosud zastaveny |
| :::no-loc text="Failed Requests"::: (`failed-requests`) | Celkový počet neúspěšných žádostí, ke kterým došlo po dobu životnosti aplikace |
| :::no-loc text="Request Rate"::: (`requests-per-second`) | Počet požadavků, které se vyskytují za sekundu |
| :::no-loc text="Total Requests"::: (`total-requests`) | Celkový počet požadavků, které se vyskytly po celou dobu životnosti aplikace |

### <a name="microsoftaspnetcorehttpconnections-counters"></a>Čítače "Microsoft. AspNetCore. http. Connections"

Následující čítače jsou publikovány jako součást [ASP.NET Coreového signálu](/aspnet/core/signalr/introduction) a jsou udržovány v [`HttpConnectionsEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/master/src/SignalR/common/Http.Connections/src/Internal/HttpConnectionsEventSource.cs) .

| Čítač | Popis |
|--|--|
| :::no-loc text="Average Connection Duration"::: (`connections-duration`) | Průměrná doba trvání připojení v milisekundách |
| :::no-loc text="Current Connections"::: (`current-connections`) | Počet aktivních připojení, která byla spuštěna, ale ještě nebyla zastavena |
| :::no-loc text="Total Connections Started"::: (`connections-started`) | Celkový počet připojení, která byla spuštěna |
| :::no-loc text="Total Connections Stopped"::: (`connections-stopped`) | Celkový počet připojení, která byla zastavena |
| :::no-loc text="Total Connections Timed Out"::: (`connections-timed-out`) | Celkový počet připojení, jejichž časový limit vypršel. |

### <a name="microsoft-aspnetcore-server-kestrel-counters"></a>Čítače "Microsoft-AspNetCore-Server-Kestrel"

Následující čítače jsou publikovány jako součást [webového serveru ASP.NET Core Kestrel](/aspnet/core/fundamentals/servers/kestrel) a jsou udržovány v [`KestrelEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/master/src/Servers/Kestrel/Core/src/Internal/Infrastructure/KestrelEventSource.cs) .

| Čítač | Popis |
|--|--|
| :::no-loc text="Connection Queue Length"::: (`connection-queue-length`) | Aktuální délka fronty připojení |
| :::no-loc text="Connection Rate"::: (`connections-per-second`) | Počet připojení za sekundu k webovému serveru |
| :::no-loc text="Current Connections"::: (`current-connections`) | Aktuální počet aktivních připojení k webovému serveru |
| :::no-loc text="Current TLS Handshakes"::: (`current-tls-handshakes`) | Aktuální počet handshake TLS |
| :::no-loc text="Current Upgraded Requests (WebSockets)"::: (`current-upgraded-requests`) | Aktuální počet upgradovaných požadavků (WebSockets) |
| :::no-loc text="Failed TLS Handshakes"::: (`failed-tls-handshakes`) | Celkový počet neúspěšných handshakí TLS |
| :::no-loc text="Request Queue Length"::: (`request-queue-length`) | Aktuální délka fronty požadavků |
| :::no-loc text="TLS Handshake Rate"::: (`tls-handshakes-per-second`) | Počet handshakí TLS za sekundu |
| :::no-loc text="Total Connections"::: (`total-connections`) | Celkový počet připojení k webovému serveru |
| :::no-loc text="Total TLS Handshakes"::: (`total-tls-handshakes`) | Celkový počet handshake TLS s webovým serverem |
