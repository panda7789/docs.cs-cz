---
title: Nastavení konfigurace sítě
description: Přečtěte si o nastaveních za běhu, které konfiguruje sítě pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 622c4afbd36d3d9004edbd9219145fa9e5d326ae
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802769"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="3f8c8-103">Možnosti konfigurace pro používání sítě v době běhu</span><span class="sxs-lookup"><span data-stu-id="3f8c8-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="3f8c8-104">Protokol HTTP/2</span><span class="sxs-lookup"><span data-stu-id="3f8c8-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="3f8c8-105">Nakonfiguruje, jestli je povolená podpora pro protokol HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="3f8c8-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>
- <span data-ttu-id="3f8c8-106">Výchozí: zakázáno (`false`).</span><span class="sxs-lookup"><span data-stu-id="3f8c8-106">Default: Disabled (`false`).</span></span>
- <span data-ttu-id="3f8c8-107">Představeno v .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="3f8c8-107">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="3f8c8-108">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="3f8c8-108">Setting name</span></span> | <span data-ttu-id="3f8c8-109">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="3f8c8-109">Values</span></span> |
| - | - |
| <span data-ttu-id="3f8c8-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="3f8c8-110">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="3f8c8-111">`false` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="3f8c8-111">`false` - disabled</span></span><br/><span data-ttu-id="3f8c8-112">`true` – povoleno</span><span class="sxs-lookup"><span data-stu-id="3f8c8-112">`true` - enabled</span></span> |
| <span data-ttu-id="3f8c8-113">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="3f8c8-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="3f8c8-114">`0` – zakázáno</span><span class="sxs-lookup"><span data-stu-id="3f8c8-114">`0` - disabled</span></span><br/><span data-ttu-id="3f8c8-115">`1` – povoleno</span><span class="sxs-lookup"><span data-stu-id="3f8c8-115">`1` - enabled</span></span> |

## <a name="sockets-http-handler"></a><span data-ttu-id="3f8c8-116">Obslužná rutina HTTP soketů</span><span class="sxs-lookup"><span data-stu-id="3f8c8-116">Sockets HTTP handler</span></span>

- <span data-ttu-id="3f8c8-117">Nakonfiguruje, jestli rozhraní API na vysoké úrovni sítě, jako je <xref:System.Net.Http.HttpClient>, používá <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> nebo implementaci <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> založené na [libcurl](https://curl.haxx.se/libcurl/).</span><span class="sxs-lookup"><span data-stu-id="3f8c8-117">Configures whether high-level networking APIs, such as <xref:System.Net.Http.HttpClient>, use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or the implementation of <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> that's based on [libcurl](https://curl.haxx.se/libcurl/).</span></span>
- <span data-ttu-id="3f8c8-118">Výchozí: použijte <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`).</span><span class="sxs-lookup"><span data-stu-id="3f8c8-118">Default: Use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`).</span></span>
- <span data-ttu-id="3f8c8-119">Toto nastavení lze nakonfigurovat programově voláním metody <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3f8c8-119">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="3f8c8-120">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="3f8c8-120">Setting name</span></span> | <span data-ttu-id="3f8c8-121">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="3f8c8-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="3f8c8-122">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="3f8c8-122">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="3f8c8-123">`true` – povolí použití <xref:System.Net.Http.SocketsHttpHandler>.</span><span class="sxs-lookup"><span data-stu-id="3f8c8-123">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="3f8c8-124">`false` – povolí použití <xref:System.Net.Http.HttpClientHandler>.</span><span class="sxs-lookup"><span data-stu-id="3f8c8-124">`false` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
| <span data-ttu-id="3f8c8-125">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="3f8c8-125">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="3f8c8-126">`1` – povolí použití <xref:System.Net.Http.SocketsHttpHandler>.</span><span class="sxs-lookup"><span data-stu-id="3f8c8-126">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="3f8c8-127">`0` – povolí použití <xref:System.Net.Http.HttpClientHandler>.</span><span class="sxs-lookup"><span data-stu-id="3f8c8-127">`0` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
