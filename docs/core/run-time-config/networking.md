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
# <a name="run-time-configuration-options-for-networking"></a>Možnosti konfigurace pro používání sítě v době běhu

## <a name="http2-protocol"></a>Protokol HTTP/2

- Nakonfiguruje, jestli je povolená podpora pro protokol HTTP/2.

- Pokud toto nastavení vynecháte, podpora protokolu HTTP/2 je zakázaná. To je ekvivalentní nastavení hodnoty na `false` .

- Představeno v .NET Core 3,0.

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false`– zakázáno<br/>`true`– povoleno |
| **Proměnná prostředí** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0`– zakázáno<br/>`1`– povoleno |

## <a name="usesocketshttphandler"></a>UseSocketsHttpHandler

- Nakonfiguruje, jestli <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> používá <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> nebo starší zásobníky protokolu HTTP ( <xref:System.Net.Http.WinHttpHandler> ve Windows a `CurlHandler` , interní třída implementovaná nad [libcurl](https://curl.haxx.se/libcurl/), na Linux).

  > [!NOTE]
  > Místo přímého vytváření instancí třídy můžete používat rozhraní API pro síť na vysoké úrovni <xref:System.Net.Http.HttpClientHandler> . Toto nastavení má vliv také na to, který zásobník protokolu HTTP se používá v sítích API vysoké úrovně, včetně <xref:System.Net.Http.HttpClient> a [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118)).

- Vynecháte-li toto nastavení, <xref:System.Net.Http.HttpClientHandler> používá nástroj <xref:System.Net.Http.SocketsHttpHandler> . To je ekvivalentní nastavení hodnoty na `true` .

- Toto nastavení lze nakonfigurovat programově voláním <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metody.

| | Název nastavení | Hodnoty |
| - | - | - |
| **runtimeconfig. JSON** | `System.Net.Http.UseSocketsHttpHandler` | `true`– Povolí použití<xref:System.Net.Http.SocketsHttpHandler><br/>`false`– Povolí použití <xref:System.Net.Http.WinHttpHandler> v systému Windows nebo [libcurl](https://curl.haxx.se/libcurl/) na platformě Linux. |
| **Proměnná prostředí** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`– Povolí použití<xref:System.Net.Http.SocketsHttpHandler><br/>`0`– Povolí použití <xref:System.Net.Http.WinHttpHandler> v systému Windows nebo [libcurl](https://curl.haxx.se/libcurl/) na platformě Linux. |

> [!NOTE]
> Od rozhraní .NET 5 `System.Net.Http.UseSocketsHttpHandler` není nastavení již k dispozici.
