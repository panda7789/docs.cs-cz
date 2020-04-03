---
title: Nastavení konfigurace sítě
description: Přečtěte si o nastavení za běhu, která konfigurují sítě pro aplikace .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: f5ea47f0444a911dc2347a66817cabf585fd8e70
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635426"
---
# <a name="run-time-configuration-options-for-networking"></a>Možnosti konfigurace za běhu pro sítě

## <a name="http2-protocol"></a>Protokol HTTP/2

- Konfiguruje, zda je povolena podpora protokolu HTTP/2.
- Výchozí: Zakázáno (`false`).
- Zavedeno v rozhraní .NET Core 3.0.

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false`- zakázáno<br/>`true`- povoleno |
| **Proměnná prostředí** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0`- zakázáno<br/>`1`- povoleno |

## <a name="usesocketshttphandler"></a>UseSocketsHttpHandler

- Konfiguruje, zda jsou síťová <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> rozhraní API <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> vysoké úrovně, například <xref:System.Net.Http.HttpClient>, použití nebo implementace, která je založena na [libcurl](https://curl.haxx.se/libcurl/).
- Výchozí: <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> Použití`true`( ).
- Toto nastavení můžete nakonfigurovat programově voláním <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metody.

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.UseSocketsHttpHandler` | `true`- umožňuje použití<xref:System.Net.Http.SocketsHttpHandler><br/>`false`- umožňuje použití<xref:System.Net.Http.HttpClientHandler> |
| **Proměnná prostředí** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`- umožňuje použití<xref:System.Net.Http.SocketsHttpHandler><br/>`0`- umožňuje použití<xref:System.Net.Http.HttpClientHandler> |

> [!NOTE]
> Počínaje rozhraním .NET `System.Net.Http.UseSocketsHttpHandler` 5 již není nastavení k dispozici.
