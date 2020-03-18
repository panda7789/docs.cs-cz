---
title: Nastavení konfigurace sítě
description: Přečtěte si o nastavení za běhu, která konfigurují sítě pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 622c4afbd36d3d9004edbd9219145fa9e5d326ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802769"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="1fa08-103">Možnosti konfigurace za běhu pro sítě</span><span class="sxs-lookup"><span data-stu-id="1fa08-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="1fa08-104">Protokol HTTP/2</span><span class="sxs-lookup"><span data-stu-id="1fa08-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="1fa08-105">Konfiguruje, zda je povolena podpora protokolu HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="1fa08-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>
- <span data-ttu-id="1fa08-106">Výchozí: Zakázáno (`false`).</span><span class="sxs-lookup"><span data-stu-id="1fa08-106">Default: Disabled (`false`).</span></span>
- <span data-ttu-id="1fa08-107">Zavedeno v rozhraní .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="1fa08-107">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="1fa08-108">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="1fa08-108">Setting name</span></span> | <span data-ttu-id="1fa08-109">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="1fa08-109">Values</span></span> |
| - | - |
| <span data-ttu-id="1fa08-110">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="1fa08-110">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="1fa08-111">`false`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="1fa08-111">`false` - disabled</span></span><br/><span data-ttu-id="1fa08-112">`true`- povoleno</span><span class="sxs-lookup"><span data-stu-id="1fa08-112">`true` - enabled</span></span> |
| <span data-ttu-id="1fa08-113">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="1fa08-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="1fa08-114">`0`- zakázáno</span><span class="sxs-lookup"><span data-stu-id="1fa08-114">`0` - disabled</span></span><br/><span data-ttu-id="1fa08-115">`1`- povoleno</span><span class="sxs-lookup"><span data-stu-id="1fa08-115">`1` - enabled</span></span> |

## <a name="sockets-http-handler"></a><span data-ttu-id="1fa08-116">Obslužná rutina HTTP soketů</span><span class="sxs-lookup"><span data-stu-id="1fa08-116">Sockets HTTP handler</span></span>

- <span data-ttu-id="1fa08-117">Konfiguruje, zda jsou síťová <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> rozhraní API <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> vysoké úrovně, například <xref:System.Net.Http.HttpClient>, použití nebo implementace, která je založena na [libcurl](https://curl.haxx.se/libcurl/).</span><span class="sxs-lookup"><span data-stu-id="1fa08-117">Configures whether high-level networking APIs, such as <xref:System.Net.Http.HttpClient>, use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or the implementation of <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> that's based on [libcurl](https://curl.haxx.se/libcurl/).</span></span>
- <span data-ttu-id="1fa08-118">Výchozí: <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> Použití`true`( ).</span><span class="sxs-lookup"><span data-stu-id="1fa08-118">Default: Use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`).</span></span>
- <span data-ttu-id="1fa08-119">Toto nastavení můžete nakonfigurovat programově voláním <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="1fa08-119">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="1fa08-120">Název nastavení</span><span class="sxs-lookup"><span data-stu-id="1fa08-120">Setting name</span></span> | <span data-ttu-id="1fa08-121">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="1fa08-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="1fa08-122">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="1fa08-122">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="1fa08-123">`true`- umožňuje použití<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="1fa08-123">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="1fa08-124">`false`- umožňuje použití<xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="1fa08-124">`false` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
| <span data-ttu-id="1fa08-125">**Proměnná prostředí**</span><span class="sxs-lookup"><span data-stu-id="1fa08-125">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="1fa08-126">`1`- umožňuje použití<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="1fa08-126">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="1fa08-127">`0`- umožňuje použití<xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="1fa08-127">`0` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
