---
ms.openlocfilehash: 92210f6becb5a5a43893ee0fd51ef51e2ddd7f8d
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325229"
---
### <a name="kestrel-http2-disabled-over-tls-on-incompatible-windows-versions"></a><span data-ttu-id="edd41-101">Kestrel: HTTP/2 zakázáno přes TLS v nekompatibilních verzích Windows</span><span class="sxs-lookup"><span data-stu-id="edd41-101">Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions</span></span>

<span data-ttu-id="edd41-102">Pokud chcete povolit protokol HTTP/2 přes TLS (Transport Layer Security) ve Windows, musí být splněné dva požadavky:</span><span class="sxs-lookup"><span data-stu-id="edd41-102">To enable HTTP/2 over Transport Layer Security (TLS) on Windows, two requirements need to be met:</span></span>

- <span data-ttu-id="edd41-103">Podpora vyjednávání protokolu ALPN (Application Layer Protocol), která je dostupná od Windows 8.1 a Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="edd41-103">Application-Layer Protocol Negotiation (ALPN) support, which is available starting with Windows 8.1 and Windows Server 2012 R2.</span></span>
- <span data-ttu-id="edd41-104">Sada šifr kompatibilních s HTTP/2, která je dostupná od Windows 10 a Windows serveru 2016.</span><span class="sxs-lookup"><span data-stu-id="edd41-104">A set of ciphers compatible with HTTP/2, which is available starting with Windows 10 and Windows Server 2016.</span></span>

<span data-ttu-id="edd41-105">V takovém případě se chování Kestrel při konfiguraci HTTP/2 přes TLS změnilo na:</span><span class="sxs-lookup"><span data-stu-id="edd41-105">As such, Kestrel's behavior when HTTP/2 over TLS is configured has changed to:</span></span>

- <span data-ttu-id="edd41-106">Přejít na `Http1` nižší úroveň a zaprotokolovat zprávu na `Information` úrovni, když je [ListenOptions. HttpProtocols](/dotnet/api/microsoft.aspnetcore.server.kestrel.core.httpprotocols) nastaveno na `Http1AndHttp2` .</span><span class="sxs-lookup"><span data-stu-id="edd41-106">Downgrade to `Http1` and log a message at the `Information` level when [ListenOptions.HttpProtocols](/dotnet/api/microsoft.aspnetcore.server.kestrel.core.httpprotocols) is set to `Http1AndHttp2`.</span></span> <span data-ttu-id="edd41-107">`Http1AndHttp2` je výchozí hodnota pro `ListenOptions.HttpProtocols` .</span><span class="sxs-lookup"><span data-stu-id="edd41-107">`Http1AndHttp2` is the default value for `ListenOptions.HttpProtocols`.</span></span>
- <span data-ttu-id="edd41-108">Vyvolat výjimku, `NotSupportedException` Pokud `ListenOptions.HttpProtocols` je nastavena na `Http2` .</span><span class="sxs-lookup"><span data-stu-id="edd41-108">Throw a `NotSupportedException` when `ListenOptions.HttpProtocols` is set to `Http2`.</span></span>

<span data-ttu-id="edd41-109">Diskuzi najdete v tématu problém [dotnet/aspnetcore # 23068](https://github.com/dotnet/aspnetcore/issues/23068).</span><span class="sxs-lookup"><span data-stu-id="edd41-109">For discussion, see issue [dotnet/aspnetcore#23068](https://github.com/dotnet/aspnetcore/issues/23068).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="edd41-110">Představená verze</span><span class="sxs-lookup"><span data-stu-id="edd41-110">Version introduced</span></span>

<span data-ttu-id="edd41-111">ASP.NET Core 5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="edd41-111">ASP.NET Core 5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="edd41-112">Staré chování</span><span class="sxs-lookup"><span data-stu-id="edd41-112">Old behavior</span></span>

<span data-ttu-id="edd41-113">Následující tabulka popisuje chování při konfiguraci HTTP/2 přes TLS.</span><span class="sxs-lookup"><span data-stu-id="edd41-113">The following table outlines the behavior when HTTP/2 over TLS is configured.</span></span>

| <span data-ttu-id="edd41-114">Protokoly</span><span class="sxs-lookup"><span data-stu-id="edd41-114">Protocols</span></span> | <span data-ttu-id="edd41-115">Windows 7,</span><span class="sxs-lookup"><span data-stu-id="edd41-115">Windows 7,</span></span><br /><span data-ttu-id="edd41-116">Windows Server 2008 R2,</span><span class="sxs-lookup"><span data-stu-id="edd41-116">Windows Server 2008 R2,</span></span><br /><span data-ttu-id="edd41-117">nebo starší</span><span class="sxs-lookup"><span data-stu-id="edd41-117">or earlier</span></span> | <span data-ttu-id="edd41-118">Systém Windows 8,</span><span class="sxs-lookup"><span data-stu-id="edd41-118">Windows 8,</span></span><br /><span data-ttu-id="edd41-119">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="edd41-119">Windows Server 2012</span></span> | <span data-ttu-id="edd41-120">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="edd41-120">Windows 8.1,</span></span><br /><span data-ttu-id="edd41-121">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="edd41-121">Windows Server 2012 R2</span></span> | <span data-ttu-id="edd41-122">Windows 10,</span><span class="sxs-lookup"><span data-stu-id="edd41-122">Windows 10,</span></span><br /><span data-ttu-id="edd41-123">Windows Server 2016,</span><span class="sxs-lookup"><span data-stu-id="edd41-123">Windows Server 2016,</span></span><br /><span data-ttu-id="edd41-124">nebo novější</span><span class="sxs-lookup"><span data-stu-id="edd41-124">or newer</span></span> |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | <span data-ttu-id="edd41-125">Vyvolá `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="edd41-125">Throw `NotSupportedException`</span></span>                   | <span data-ttu-id="edd41-126">Chyba při ověřování TLS</span><span class="sxs-lookup"><span data-stu-id="edd41-126">Error during TLS handshake</span></span>     | <span data-ttu-id="edd41-127">Chyba při ověřování TLS &ast;</span><span class="sxs-lookup"><span data-stu-id="edd41-127">Error during TLS handshake &ast;</span></span>     | <span data-ttu-id="edd41-128">Bez chyby</span><span class="sxs-lookup"><span data-stu-id="edd41-128">No error</span></span> |
| `Http1AndHttp2` | <span data-ttu-id="edd41-129">Downgradovat na `Http1`</span><span class="sxs-lookup"><span data-stu-id="edd41-129">Downgrade to `Http1`</span></span>                    | <span data-ttu-id="edd41-130">Downgradovat na `Http1`</span><span class="sxs-lookup"><span data-stu-id="edd41-130">Downgrade to `Http1`</span></span>     | <span data-ttu-id="edd41-131">Chyba při ověřování TLS &ast;</span><span class="sxs-lookup"><span data-stu-id="edd41-131">Error during TLS handshake &ast;</span></span>     | <span data-ttu-id="edd41-132">Bez chyby</span><span class="sxs-lookup"><span data-stu-id="edd41-132">No error</span></span> |

<span data-ttu-id="edd41-133">&ast; Nakonfigurujte kompatibilní šifrovací sady pro povolení těchto scénářů.</span><span class="sxs-lookup"><span data-stu-id="edd41-133">&ast; Configure compatible cipher suites to enable these scenarios.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="edd41-134">Nové chování</span><span class="sxs-lookup"><span data-stu-id="edd41-134">New behavior</span></span>

<span data-ttu-id="edd41-135">Následující tabulka popisuje chování při konfiguraci HTTP/2 přes TLS.</span><span class="sxs-lookup"><span data-stu-id="edd41-135">The following table outlines the behavior when HTTP/2 over TLS is configured.</span></span>

| <span data-ttu-id="edd41-136">Protokoly</span><span class="sxs-lookup"><span data-stu-id="edd41-136">Protocols</span></span> | <span data-ttu-id="edd41-137">Windows 7,</span><span class="sxs-lookup"><span data-stu-id="edd41-137">Windows 7,</span></span><br /><span data-ttu-id="edd41-138">Windows Server 2008 R2,</span><span class="sxs-lookup"><span data-stu-id="edd41-138">Windows Server 2008 R2,</span></span><br /><span data-ttu-id="edd41-139">nebo starší</span><span class="sxs-lookup"><span data-stu-id="edd41-139">or earlier</span></span> | <span data-ttu-id="edd41-140">Systém Windows 8,</span><span class="sxs-lookup"><span data-stu-id="edd41-140">Windows 8,</span></span><br /><span data-ttu-id="edd41-141">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="edd41-141">Windows Server 2012</span></span> | <span data-ttu-id="edd41-142">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="edd41-142">Windows 8.1,</span></span><br /><span data-ttu-id="edd41-143">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="edd41-143">Windows Server 2012 R2</span></span> | <span data-ttu-id="edd41-144">Windows 10,</span><span class="sxs-lookup"><span data-stu-id="edd41-144">Windows 10,</span></span><br /><span data-ttu-id="edd41-145">Windows Server 2016,</span><span class="sxs-lookup"><span data-stu-id="edd41-145">Windows Server 2016,</span></span><br /><span data-ttu-id="edd41-146">nebo novější</span><span class="sxs-lookup"><span data-stu-id="edd41-146">or newer</span></span> |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | <span data-ttu-id="edd41-147">Vyvolá `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="edd41-147">Throw `NotSupportedException`</span></span>                   | <span data-ttu-id="edd41-148">Vyvolá `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="edd41-148">Throw `NotSupportedException`</span></span>     | <span data-ttu-id="edd41-149">Throw `NotSupportedException`&ast;&ast;</span><span class="sxs-lookup"><span data-stu-id="edd41-149">Throw `NotSupportedException` &ast;&ast;</span></span>     | <span data-ttu-id="edd41-150">Bez chyby</span><span class="sxs-lookup"><span data-stu-id="edd41-150">No error</span></span> |
| `Http1AndHttp2` | <span data-ttu-id="edd41-151">Downgradovat na `Http1`</span><span class="sxs-lookup"><span data-stu-id="edd41-151">Downgrade to `Http1`</span></span>                    | <span data-ttu-id="edd41-152">Downgradovat na `Http1`</span><span class="sxs-lookup"><span data-stu-id="edd41-152">Downgrade to `Http1`</span></span>     | <span data-ttu-id="edd41-153">Downgradovat na `Http1`&ast;&ast;</span><span class="sxs-lookup"><span data-stu-id="edd41-153">Downgrade to `Http1` &ast;&ast;</span></span>     | <span data-ttu-id="edd41-154">Bez chyby</span><span class="sxs-lookup"><span data-stu-id="edd41-154">No error</span></span> |

<span data-ttu-id="edd41-155">&ast;&ast; Nakonfigurujte kompatibilní šifrovací sady a nastavte kontext aplikace na přepínač `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` , `true` aby bylo možné tyto scénáře povolit.</span><span class="sxs-lookup"><span data-stu-id="edd41-155">&ast;&ast; Configure compatible cipher suites and set the app context switch `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` to `true` to enable these scenarios.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="edd41-156">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="edd41-156">Reason for change</span></span>

<span data-ttu-id="edd41-157">Tato změna zajišťuje, že chyby kompatibility pro HTTP/2 přes protokol TLS na starších verzích Windows jsou ploché a co nejblížeelné.</span><span class="sxs-lookup"><span data-stu-id="edd41-157">This change ensures compatibility errors for HTTP/2 over TLS on older Windows versions are surfaced as early and as clearly as possible.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="edd41-158">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="edd41-158">Recommended action</span></span>

<span data-ttu-id="edd41-159">Zajistěte, aby protokol HTTP/2 přes TLS byl zakázán v nekompatibilních verzích systému Windows.</span><span class="sxs-lookup"><span data-stu-id="edd41-159">Ensure HTTP/2 over TLS is disabled on incompatible Windows versions.</span></span> <span data-ttu-id="edd41-160">Windows 8.1 a Windows Server 2012 R2 jsou nekompatibilní, protože ve výchozím nastavení nemají nezbytné šifry.</span><span class="sxs-lookup"><span data-stu-id="edd41-160">Windows 8.1 and Windows Server 2012 R2 are incompatible since they lack the necessary ciphers by default.</span></span> <span data-ttu-id="edd41-161">Je však možné aktualizovat nastavení konfigurace počítače tak, aby používala šifry kompatibilní s protokolem HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="edd41-161">However, it's possible to update the Computer Configuration settings to use HTTP/2 compatible ciphers.</span></span> <span data-ttu-id="edd41-162">Další informace najdete v tématu [šifrovací sady TLS v Windows 8.1](/windows/win32/secauthn/tls-cipher-suites-in-windows-8-1).</span><span class="sxs-lookup"><span data-stu-id="edd41-162">For more information, see [TLS cipher suites in Windows 8.1](/windows/win32/secauthn/tls-cipher-suites-in-windows-8-1).</span></span> <span data-ttu-id="edd41-163">Po nakonfigurování musí být protokol HTTP/2 přes TLS na Kestrel povolený nastavením přepínače kontextu aplikace `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` .</span><span class="sxs-lookup"><span data-stu-id="edd41-163">Once configured, HTTP/2 over TLS on Kestrel must be enabled by setting the app context switch `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2`.</span></span> <span data-ttu-id="edd41-164">Příklad:</span><span class="sxs-lookup"><span data-stu-id="edd41-164">For example:</span></span>

```csharp
AppContext.SetSwitch("Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2", true);
```

<span data-ttu-id="edd41-165">Žádná základní podpora se nezměnila.</span><span class="sxs-lookup"><span data-stu-id="edd41-165">No underlying support has changed.</span></span> <span data-ttu-id="edd41-166">Například HTTP/2 přes protokol TLS nikdy nefungovalo ve Windows 8 nebo Windows Serveru 2012.</span><span class="sxs-lookup"><span data-stu-id="edd41-166">For example, HTTP/2 over TLS has never worked on Windows 8 or Windows Server 2012.</span></span> <span data-ttu-id="edd41-167">Tato změna mění způsob, jakým jsou prezentovány chyby v těchto nepodporovaných scénářích.</span><span class="sxs-lookup"><span data-stu-id="edd41-167">This change modifies how errors in these unsupported scenarios are presented.</span></span>

#### <a name="category"></a><span data-ttu-id="edd41-168">Kategorie</span><span class="sxs-lookup"><span data-stu-id="edd41-168">Category</span></span>

<span data-ttu-id="edd41-169">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="edd41-169">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="edd41-170">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="edd41-170">Affected APIs</span></span>

<span data-ttu-id="edd41-171">Žádné</span><span class="sxs-lookup"><span data-stu-id="edd41-171">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
