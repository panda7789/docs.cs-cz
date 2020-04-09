---
title: Nastavení konfigurace sítě
description: Přečtěte si o nastavení za běhu, která konfigurují sítě pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 8d02087ad7260cc78c096090bf3b06a716d34678
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989100"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="44364-103">Možnosti konfigurace za běhu pro sítě</span><span class="sxs-lookup"><span data-stu-id="44364-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="44364-104">Protokol HTTP/2</span><span class="sxs-lookup"><span data-stu-id="44364-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="44364-105">Konfiguruje, zda je povolena podpora protokolu HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="44364-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>

- <span data-ttu-id="44364-106">Výchozí: Zakázáno (`false`).</span><span class="sxs-lookup"><span data-stu-id="44364-106">Default: Disabled (`false`).</span></span>

- <span data-ttu-id="44364-107">Zavedeno v rozhraní .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="44364-107">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="44364-108">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="44364-108">Setting name</span></span> | <span data-ttu-id="44364-109">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="44364-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="44364-110">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="44364-110">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="44364-111">`false`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="44364-111">`false` - disabled</span></span><br/><span data-ttu-id="44364-112">`true`- povoleno</span><span class="sxs-lookup"><span data-stu-id="44364-112">`true` - enabled</span></span> |
| <span data-ttu-id="44364-113">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="44364-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="44364-114">`0`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="44364-114">`0` - disabled</span></span><br/><span data-ttu-id="44364-115">`1`- povoleno</span><span class="sxs-lookup"><span data-stu-id="44364-115">`1` - enabled</span></span> |

## <a name="usesocketshttphandler"></a><span data-ttu-id="44364-116">UseSocketsHttpHandler</span><span class="sxs-lookup"><span data-stu-id="44364-116">UseSocketsHttpHandler</span></span>

- <span data-ttu-id="44364-117">Konfiguruje, <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> zda používá <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> <xref:System.Net.Http.WinHttpHandler> nebo starší `CurlHandler`http protokol zásobníky (v systému Windows a , vnitřní třídy implementované na vrcholu [libcurl](https://curl.haxx.se/libcurl/), na Linuxu).</span><span class="sxs-lookup"><span data-stu-id="44364-117">Configures whether <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uses <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or older HTTP protocol stacks (<xref:System.Net.Http.WinHttpHandler> on Windows and `CurlHandler`, an internal class implemented on top of [libcurl](https://curl.haxx.se/libcurl/), on Linux).</span></span>

  > [!NOTE]
  > <span data-ttu-id="44364-118">Je možné, že používáte vysoce úrovňové síťová <xref:System.Net.Http.HttpClientHandler> úložiště API namísto přímého vytváření instancí třídy.</span><span class="sxs-lookup"><span data-stu-id="44364-118">You may be using high-level networking APIs instead of directly instantiating the <xref:System.Net.Http.HttpClientHandler> class.</span></span> <span data-ttu-id="44364-119">Toto nastavení také ovlivňuje, který zásobník protokolu HTTP je <xref:System.Net.Http.HttpClient> používán síťovými síťovými sítěmi vysoké úrovně, včetně a [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118)).</span><span class="sxs-lookup"><span data-stu-id="44364-119">This setting also affects which HTTP protocol stack is used by high-level networking APIs, including <xref:System.Net.Http.HttpClient> and [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118)).</span></span>

- <span data-ttu-id="44364-120">Výchozí: <xref:System.Net.Http.SocketsHttpHandler> Použití`true`( ).</span><span class="sxs-lookup"><span data-stu-id="44364-120">Default: Use <xref:System.Net.Http.SocketsHttpHandler> (`true`).</span></span>

- <span data-ttu-id="44364-121">Toto nastavení můžete nakonfigurovat programově voláním <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="44364-121">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="44364-122">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="44364-122">Setting name</span></span> | <span data-ttu-id="44364-123">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="44364-123">Values</span></span> |
| - | - | - |
| <span data-ttu-id="44364-124">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="44364-124">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="44364-125">`true`- umožňuje použití<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="44364-125">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="44364-126">`false`- umožňuje použití <xref:System.Net.Http.WinHttpHandler> na Windows nebo [libcurl](https://curl.haxx.se/libcurl/) na Linuxu</span><span class="sxs-lookup"><span data-stu-id="44364-126">`false` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |
| <span data-ttu-id="44364-127">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="44364-127">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="44364-128">`1`- umožňuje použití<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="44364-128">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="44364-129">`0`- umožňuje použití <xref:System.Net.Http.WinHttpHandler> na Windows nebo [libcurl](https://curl.haxx.se/libcurl/) na Linuxu</span><span class="sxs-lookup"><span data-stu-id="44364-129">`0` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |

> [!NOTE]
> <span data-ttu-id="44364-130">Počínaje rozhraním .NET `System.Net.Http.UseSocketsHttpHandler` 5 již není nastavení k dispozici.</span><span class="sxs-lookup"><span data-stu-id="44364-130">Starting in .NET 5, the `System.Net.Http.UseSocketsHttpHandler` setting is no longer available.</span></span>
