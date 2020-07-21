---
ms.openlocfilehash: 203d75f5858c8ff039cf579c0539efda0c5c9f02
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474372"
---
### <a name="kestrel-libuv-transport-marked-as-obsolete"></a><span data-ttu-id="f3733-101">Kestrel: přenos Libuv označený jako zastaralý</span><span class="sxs-lookup"><span data-stu-id="f3733-101">Kestrel: Libuv transport marked as obsolete</span></span>

<span data-ttu-id="f3733-102">Starší verze ASP.NET Core používaly Libuv jako podrobnosti implementace způsobu provedení asynchronního vstupu a výstupu.</span><span class="sxs-lookup"><span data-stu-id="f3733-102">Earlier versions of ASP.NET Core used Libuv as an implementation detail of how asynchronous input and output was performed.</span></span> <span data-ttu-id="f3733-103">V ASP.NET Core 2,0 <xref:System.Net.Sockets.Socket> byl vyvinut alternativní přenos založený na bázi.</span><span class="sxs-lookup"><span data-stu-id="f3733-103">In ASP.NET Core 2.0, an alternative, <xref:System.Net.Sockets.Socket>-based transport was developed.</span></span> <span data-ttu-id="f3733-104">V ASP.NET Core 2,1 Kestrel ve výchozím nastavení přepnuto na použití `Socket` přenosu založeného na bázi.</span><span class="sxs-lookup"><span data-stu-id="f3733-104">In ASP.NET Core 2.1, Kestrel switched to using the `Socket`-based transport by default.</span></span> <span data-ttu-id="f3733-105">Podpora Libuv byla udržována z důvodu kompatibility.</span><span class="sxs-lookup"><span data-stu-id="f3733-105">Libuv support was maintained for compatibility reasons.</span></span>

<span data-ttu-id="f3733-106">V tomto okamžiku `Socket` je použití přenosu založeného na bázi mnohem běžnější než Libuv přenos.</span><span class="sxs-lookup"><span data-stu-id="f3733-106">At this point, use of the `Socket`-based transport is far more common than the Libuv transport.</span></span> <span data-ttu-id="f3733-107">V důsledku toho je podpora Libuv označena jako zastaralá v rozhraní .NET 5,0 a bude zcela odebrána v rozhraní .NET 6,0.</span><span class="sxs-lookup"><span data-stu-id="f3733-107">Consequently, Libuv support is marked as obsolete in .NET 5.0 and will be removed entirely in .NET 6.0.</span></span>

<span data-ttu-id="f3733-108">V rámci této změny se podpora Libuv pro nové platformy operačního systému (například Windows ARM64) nepřidá do časového rámce .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="f3733-108">As part of this change, Libuv support for new operating system platforms (like Windows ARM64) won't be added in the .NET 5.0 timeframe.</span></span>

<span data-ttu-id="f3733-109">Diskuzi o blokujících problémech, které vyžadují použití přenosu Libuv, najdete v tématu problém GitHubu v [dotnet/aspnetcore # 23409](https://github.com/dotnet/aspnetcore/issues/23409).</span><span class="sxs-lookup"><span data-stu-id="f3733-109">For discussion on blocking issues that require the use of the Libuv transport, see the GitHub issue at [dotnet/aspnetcore#23409](https://github.com/dotnet/aspnetcore/issues/23409).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f3733-110">Představená verze</span><span class="sxs-lookup"><span data-stu-id="f3733-110">Version introduced</span></span>

<span data-ttu-id="f3733-111">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="f3733-111">5.0 Preview 8</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f3733-112">Staré chování</span><span class="sxs-lookup"><span data-stu-id="f3733-112">Old behavior</span></span>

<span data-ttu-id="f3733-113">Rozhraní Libuv API nejsou označena jako zastaralá.</span><span class="sxs-lookup"><span data-stu-id="f3733-113">The Libuv APIs aren't marked as obsolete.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f3733-114">Nové chování</span><span class="sxs-lookup"><span data-stu-id="f3733-114">New behavior</span></span>

<span data-ttu-id="f3733-115">Rozhraní API Libuv jsou označena jako zastaralá.</span><span class="sxs-lookup"><span data-stu-id="f3733-115">The Libuv APIs are marked as obsolete.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f3733-116">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="f3733-116">Reason for change</span></span>

<span data-ttu-id="f3733-117">`Socket`Přenos založený na bázi je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="f3733-117">The `Socket`-based transport is the default.</span></span> <span data-ttu-id="f3733-118">Neexistují žádné přesvědčivé důvody pro pokračování v používání přenosu Libuv.</span><span class="sxs-lookup"><span data-stu-id="f3733-118">There aren't any compelling reasons to continue using the Libuv transport.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f3733-119">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="f3733-119">Recommended action</span></span>

<span data-ttu-id="f3733-120">Ukončit používání balíčku a rozšiřujících metod [Libuv](https://www.nuget.org/packages/Libuv)</span><span class="sxs-lookup"><span data-stu-id="f3733-120">Discontinue use of the [Libuv package](https://www.nuget.org/packages/Libuv) and extension methods.</span></span>

#### <a name="category"></a><span data-ttu-id="f3733-121">Kategorie</span><span class="sxs-lookup"><span data-stu-id="f3733-121">Category</span></span>

<span data-ttu-id="f3733-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f3733-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f3733-123">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="f3733-123">Affected APIs</span></span>

- [<span data-ttu-id="f3733-124">WebHostBuilderLibuvExtensions</span><span class="sxs-lookup"><span data-stu-id="f3733-124">WebHostBuilderLibuvExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions?view=aspnetcore-3.0)
- [<span data-ttu-id="f3733-125">WebHostBuilderLibuvExtensions.UseLibuv</span><span class="sxs-lookup"><span data-stu-id="f3733-125">WebHostBuilderLibuvExtensions.UseLibuv</span></span>](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions.uselibuv?view=aspnetcore-3.0)
- [<span data-ttu-id="f3733-126">Microsoft. AspNetCore. Server. Kestrel. Transport. Libuv. LibuvTransportOptions</span><span class="sxs-lookup"><span data-stu-id="f3733-126">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions?view=aspnetcore-3.0)
- [<span data-ttu-id="f3733-127">Microsoft. AspNetCore. Server. Kestrel. Transport. Libuv. LibuvTransportOptions. ThreadCount</span><span class="sxs-lookup"><span data-stu-id="f3733-127">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.ThreadCount</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.threadcount?view=aspnetcore-3.0)
- [<span data-ttu-id="f3733-128">Microsoft. AspNetCore. Server. Kestrel. Transport. Libuv. LibuvTransportOptions. a zpoždění</span><span class="sxs-lookup"><span data-stu-id="f3733-128">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.NoDelay</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.nodelay?view=aspnetcore-3.0)
- [<span data-ttu-id="f3733-129">Microsoft. AspNetCore. Server. Kestrel. Transport. Libuv. LibuvTransportOptions. MaxWriteBufferSize</span><span class="sxs-lookup"><span data-stu-id="f3733-129">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxWriteBufferSize</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxwritebuffersize?view=aspnetcore-3.0)
- [<span data-ttu-id="f3733-130">Microsoft. AspNetCore. Server. Kestrel. Transport. Libuv. LibuvTransportOptions. MaxReadBufferSize</span><span class="sxs-lookup"><span data-stu-id="f3733-130">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxReadBufferSize</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxreadbuffersize?view=aspnetcore-3.0)
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
