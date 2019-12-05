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
# <a name="run-time-configuration-options-for-networking"></a>Možnosti konfigurace pro používání sítě v době běhu

## <a name="http2-protocol"></a>Protokol HTTP/2

- Nakonfiguruje, jestli je povolená podpora pro protokol HTTP/2.
- Výchozí: zakázáno (`false`).
- Představeno v .NET Core 3,0.

| | Název nastavení | Hodnoty |
| - | - |
| **runtimeconfig. JSON** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false` – zakázáno<br/>`true` – povoleno |
| **Proměnná prostředí** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0` – zakázáno<br/>`1` – povoleno |

## <a name="sockets-http-handler"></a>Obslužná rutina HTTP soketů

- Nakonfiguruje, jestli rozhraní API na vysoké úrovni sítě, jako je <xref:System.Net.Http.HttpClient>, používá <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> nebo implementaci <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> založené na [libcurl](https://curl.haxx.se/libcurl/).
- Výchozí: použijte <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`).
- Toto nastavení lze nakonfigurovat programově voláním metody <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>.

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | `System.Net.Http.UseSocketsHttpHandler` | `true` – povolí použití <xref:System.Net.Http.SocketsHttpHandler>.<br/>`false` – povolí použití <xref:System.Net.Http.HttpClientHandler>. |
| **Proměnná prostředí** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1` – povolí použití <xref:System.Net.Http.SocketsHttpHandler>.<br/>`0` – povolí použití <xref:System.Net.Http.HttpClientHandler>. |
