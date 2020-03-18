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
# <a name="run-time-configuration-options-for-networking"></a>Možnosti konfigurace za běhu pro sítě

## <a name="http2-protocol"></a>Protokol HTTP/2

- Konfiguruje, zda je povolena podpora protokolu HTTP/2.
- Výchozí: Zakázáno (`false`).
- Zavedeno v rozhraní .NET Core 3.0.

| | Název nastavení | Hodnoty |
| - | - |
| **runtimeconfig.json** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false`- zakázáno<br/>`true`- povoleno |
| **Proměnná prostředí** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0`- zakázáno<br/>`1`- povoleno |

## <a name="sockets-http-handler"></a>Obslužná rutina HTTP soketů

- Konfiguruje, zda jsou síťová <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> rozhraní API <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> vysoké úrovně, například <xref:System.Net.Http.HttpClient>, použití nebo implementace, která je založena na [libcurl](https://curl.haxx.se/libcurl/).
- Výchozí: <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> Použití`true`( ).
- Toto nastavení můžete nakonfigurovat programově voláním <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metody.

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.UseSocketsHttpHandler` | `true`- umožňuje použití<xref:System.Net.Http.SocketsHttpHandler><br/>`false`- umožňuje použití<xref:System.Net.Http.HttpClientHandler> |
| **Proměnná prostředí** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`- umožňuje použití<xref:System.Net.Http.SocketsHttpHandler><br/>`0`- umožňuje použití<xref:System.Net.Http.HttpClientHandler> |
