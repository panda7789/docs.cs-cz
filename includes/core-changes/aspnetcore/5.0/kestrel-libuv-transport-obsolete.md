---
ms.openlocfilehash: 203d75f5858c8ff039cf579c0539efda0c5c9f02
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474372"
---
### <a name="kestrel-libuv-transport-marked-as-obsolete"></a>Kestrel: přenos Libuv označený jako zastaralý

Starší verze ASP.NET Core používaly Libuv jako podrobnosti implementace způsobu provedení asynchronního vstupu a výstupu. V ASP.NET Core 2,0 <xref:System.Net.Sockets.Socket> byl vyvinut alternativní přenos založený na bázi. V ASP.NET Core 2,1 Kestrel ve výchozím nastavení přepnuto na použití `Socket` přenosu založeného na bázi. Podpora Libuv byla udržována z důvodu kompatibility.

V tomto okamžiku `Socket` je použití přenosu založeného na bázi mnohem běžnější než Libuv přenos. V důsledku toho je podpora Libuv označena jako zastaralá v rozhraní .NET 5,0 a bude zcela odebrána v rozhraní .NET 6,0.

V rámci této změny se podpora Libuv pro nové platformy operačního systému (například Windows ARM64) nepřidá do časového rámce .NET 5,0.

Diskuzi o blokujících problémech, které vyžadují použití přenosu Libuv, najdete v tématu problém GitHubu v [dotnet/aspnetcore # 23409](https://github.com/dotnet/aspnetcore/issues/23409).

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 8

#### <a name="old-behavior"></a>Staré chování

Rozhraní Libuv API nejsou označena jako zastaralá.

#### <a name="new-behavior"></a>Nové chování

Rozhraní API Libuv jsou označena jako zastaralá.

#### <a name="reason-for-change"></a>Důvod změny

`Socket`Přenos založený na bázi je výchozí hodnota. Neexistují žádné přesvědčivé důvody pro pokračování v používání přenosu Libuv.

#### <a name="recommended-action"></a>Doporučená akce

Ukončit používání balíčku a rozšiřujících metod [Libuv](https://www.nuget.org/packages/Libuv)

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- [WebHostBuilderLibuvExtensions](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions?view=aspnetcore-3.0)
- [WebHostBuilderLibuvExtensions.UseLibuv](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions.uselibuv?view=aspnetcore-3.0)
- [Microsoft. AspNetCore. Server. Kestrel. Transport. Libuv. LibuvTransportOptions](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions?view=aspnetcore-3.0)
- [Microsoft. AspNetCore. Server. Kestrel. Transport. Libuv. LibuvTransportOptions. ThreadCount](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.threadcount?view=aspnetcore-3.0)
- [Microsoft. AspNetCore. Server. Kestrel. Transport. Libuv. LibuvTransportOptions. a zpoždění](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.nodelay?view=aspnetcore-3.0)
- [Microsoft. AspNetCore. Server. Kestrel. Transport. Libuv. LibuvTransportOptions. MaxWriteBufferSize](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxwritebuffersize?view=aspnetcore-3.0)
- [Microsoft. AspNetCore. Server. Kestrel. Transport. Libuv. LibuvTransportOptions. MaxReadBufferSize](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxreadbuffersize?view=aspnetcore-3.0)
- `Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions`
- `Overload:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions.UseLibuv`
- `T:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.ThreadCount`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.NoDelay`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxWriteBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxReadBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

-->
