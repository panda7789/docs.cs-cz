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

- Konfiguruje, <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> zda používá <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> <xref:System.Net.Http.WinHttpHandler> nebo starší `CurlHandler`http protokol zásobníky (v systému Windows a , vnitřní třídy implementované na vrcholu [libcurl](https://curl.haxx.se/libcurl/), na Linuxu).

  > [!NOTE]
  > Je možné, že používáte vysoce úrovňové síťová <xref:System.Net.Http.HttpClientHandler> úložiště API namísto přímého vytváření instancí třídy. Toto nastavení také ovlivňuje, který zásobník protokolu HTTP je <xref:System.Net.Http.HttpClient> používán síťovými síťovými sítěmi vysoké úrovně, včetně a [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118)).

- Výchozí: <xref:System.Net.Http.SocketsHttpHandler> Použití`true`( ).

- Toto nastavení můžete nakonfigurovat programově voláním <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metody.

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.UseSocketsHttpHandler` | `true`- umožňuje použití<xref:System.Net.Http.SocketsHttpHandler><br/>`false`- umožňuje použití <xref:System.Net.Http.WinHttpHandler> na Windows nebo [libcurl](https://curl.haxx.se/libcurl/) na Linuxu |
| **Proměnná prostředí** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`- umožňuje použití<xref:System.Net.Http.SocketsHttpHandler><br/>`0`- umožňuje použití <xref:System.Net.Http.WinHttpHandler> na Windows nebo [libcurl](https://curl.haxx.se/libcurl/) na Linuxu |

> [!NOTE]
> Počínaje rozhraním .NET `System.Net.Http.UseSocketsHttpHandler` 5 již není nastavení k dispozici.
