---
title: Nastavení konfigurace sítě
description: Přečtěte si o nastaveních za běhu, které konfiguruje sítě pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 6b5e03b127f95911b712b66c0be8a4f5a2929fc2
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761938"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="568cf-103">Možnosti konfigurace pro používání sítě v době běhu</span><span class="sxs-lookup"><span data-stu-id="568cf-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="568cf-104">Protokol HTTP/2</span><span class="sxs-lookup"><span data-stu-id="568cf-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="568cf-105">Nakonfiguruje, jestli je povolená podpora pro protokol HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="568cf-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>

- <span data-ttu-id="568cf-106">Pokud toto nastavení vynecháte, podpora protokolu HTTP/2 je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="568cf-106">If you omit this setting, support for the HTTP/2 protocol is disabled.</span></span> <span data-ttu-id="568cf-107">To je ekvivalentní nastavení hodnoty na `false` .</span><span class="sxs-lookup"><span data-stu-id="568cf-107">This is equivalent to setting the value to `false`.</span></span>

- <span data-ttu-id="568cf-108">Představeno v .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="568cf-108">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="568cf-109">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="568cf-109">Setting name</span></span> | <span data-ttu-id="568cf-110">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="568cf-110">Values</span></span> |
| - | - | - |
| <span data-ttu-id="568cf-111">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="568cf-111">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="568cf-112">`false`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="568cf-112">`false` - disabled</span></span><br/><span data-ttu-id="568cf-113">`true`– povoleno</span><span class="sxs-lookup"><span data-stu-id="568cf-113">`true` - enabled</span></span> |
| <span data-ttu-id="568cf-114">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="568cf-114">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="568cf-115">`0`– zakázáno</span><span class="sxs-lookup"><span data-stu-id="568cf-115">`0` - disabled</span></span><br/><span data-ttu-id="568cf-116">`1`– povoleno</span><span class="sxs-lookup"><span data-stu-id="568cf-116">`1` - enabled</span></span> |

## <a name="usesocketshttphandler"></a><span data-ttu-id="568cf-117">UseSocketsHttpHandler</span><span class="sxs-lookup"><span data-stu-id="568cf-117">UseSocketsHttpHandler</span></span>

- <span data-ttu-id="568cf-118">Nakonfiguruje, jestli <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> používá <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> nebo starší zásobníky protokolu HTTP ( <xref:System.Net.Http.WinHttpHandler> ve Windows a `CurlHandler` , interní třída implementovaná nad [libcurl](https://curl.haxx.se/libcurl/), na Linux).</span><span class="sxs-lookup"><span data-stu-id="568cf-118">Configures whether <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uses <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or older HTTP protocol stacks (<xref:System.Net.Http.WinHttpHandler> on Windows and `CurlHandler`, an internal class implemented on top of [libcurl](https://curl.haxx.se/libcurl/), on Linux).</span></span>

  > [!NOTE]
  > <span data-ttu-id="568cf-119">Místo přímého vytváření instancí třídy můžete používat rozhraní API pro síť na vysoké úrovni <xref:System.Net.Http.HttpClientHandler> .</span><span class="sxs-lookup"><span data-stu-id="568cf-119">You may be using high-level networking APIs instead of directly instantiating the <xref:System.Net.Http.HttpClientHandler> class.</span></span> <span data-ttu-id="568cf-120">Toto nastavení má vliv také na to, který zásobník protokolu HTTP se používá v sítích API vysoké úrovně, včetně <xref:System.Net.Http.HttpClient> a [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118)).</span><span class="sxs-lookup"><span data-stu-id="568cf-120">This setting also affects which HTTP protocol stack is used by high-level networking APIs, including <xref:System.Net.Http.HttpClient> and [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118)).</span></span>

- <span data-ttu-id="568cf-121">Vynecháte-li toto nastavení, <xref:System.Net.Http.HttpClientHandler> používá nástroj <xref:System.Net.Http.SocketsHttpHandler> .</span><span class="sxs-lookup"><span data-stu-id="568cf-121">If you omit this setting, <xref:System.Net.Http.HttpClientHandler> uses <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="568cf-122">To je ekvivalentní nastavení hodnoty na `true` .</span><span class="sxs-lookup"><span data-stu-id="568cf-122">This is equivalent to setting the value to `true`.</span></span>

- <span data-ttu-id="568cf-123">Toto nastavení lze nakonfigurovat programově voláním <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="568cf-123">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="568cf-124">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="568cf-124">Setting name</span></span> | <span data-ttu-id="568cf-125">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="568cf-125">Values</span></span> |
| - | - | - |
| <span data-ttu-id="568cf-126">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="568cf-126">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="568cf-127">`true`– Povolí použití<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="568cf-127">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="568cf-128">`false`– Povolí použití <xref:System.Net.Http.WinHttpHandler> v systému Windows nebo [libcurl](https://curl.haxx.se/libcurl/) na platformě Linux.</span><span class="sxs-lookup"><span data-stu-id="568cf-128">`false` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |
| <span data-ttu-id="568cf-129">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="568cf-129">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="568cf-130">`1`– Povolí použití<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="568cf-130">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="568cf-131">`0`– Povolí použití <xref:System.Net.Http.WinHttpHandler> v systému Windows nebo [libcurl](https://curl.haxx.se/libcurl/) na platformě Linux.</span><span class="sxs-lookup"><span data-stu-id="568cf-131">`0` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |

> [!NOTE]
> <span data-ttu-id="568cf-132">Od rozhraní .NET 5 `System.Net.Http.UseSocketsHttpHandler` není nastavení již k dispozici.</span><span class="sxs-lookup"><span data-stu-id="568cf-132">Starting in .NET 5, the `System.Net.Http.UseSocketsHttpHandler` setting is no longer available.</span></span>
