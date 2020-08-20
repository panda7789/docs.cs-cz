---
ms.openlocfilehash: 92210f6becb5a5a43893ee0fd51ef51e2ddd7f8d
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325229"
---
### <a name="kestrel-http2-disabled-over-tls-on-incompatible-windows-versions"></a>Kestrel: HTTP/2 zakázáno přes TLS v nekompatibilních verzích Windows

Pokud chcete povolit protokol HTTP/2 přes TLS (Transport Layer Security) ve Windows, musí být splněné dva požadavky:

- Podpora vyjednávání protokolu ALPN (Application Layer Protocol), která je dostupná od Windows 8.1 a Windows Server 2012 R2.
- Sada šifr kompatibilních s HTTP/2, která je dostupná od Windows 10 a Windows serveru 2016.

V takovém případě se chování Kestrel při konfiguraci HTTP/2 přes TLS změnilo na:

- Přejít na `Http1` nižší úroveň a zaprotokolovat zprávu na `Information` úrovni, když je [ListenOptions. HttpProtocols](/dotnet/api/microsoft.aspnetcore.server.kestrel.core.httpprotocols) nastaveno na `Http1AndHttp2` . `Http1AndHttp2` je výchozí hodnota pro `ListenOptions.HttpProtocols` .
- Vyvolat výjimku, `NotSupportedException` Pokud `ListenOptions.HttpProtocols` je nastavena na `Http2` .

Diskuzi najdete v tématu problém [dotnet/aspnetcore # 23068](https://github.com/dotnet/aspnetcore/issues/23068).

#### <a name="version-introduced"></a>Představená verze

ASP.NET Core 5,0 Preview 7

#### <a name="old-behavior"></a>Staré chování

Následující tabulka popisuje chování při konfiguraci HTTP/2 přes TLS.

| Protokoly | Windows 7,<br />Windows Server 2008 R2,<br />nebo starší | Systém Windows 8,<br />Windows Server 2012 | Windows 8.1<br />Windows Server 2012 R2 | Windows 10,<br />Windows Server 2016,<br />nebo novější |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | Vyvolá `NotSupportedException`                   | Chyba při ověřování TLS     | Chyba při ověřování TLS &ast;     | Bez chyby |
| `Http1AndHttp2` | Downgradovat na `Http1`                    | Downgradovat na `Http1`     | Chyba při ověřování TLS &ast;     | Bez chyby |

&ast; Nakonfigurujte kompatibilní šifrovací sady pro povolení těchto scénářů.

#### <a name="new-behavior"></a>Nové chování

Následující tabulka popisuje chování při konfiguraci HTTP/2 přes TLS.

| Protokoly | Windows 7,<br />Windows Server 2008 R2,<br />nebo starší | Systém Windows 8,<br />Windows Server 2012 | Windows 8.1<br />Windows Server 2012 R2 | Windows 10,<br />Windows Server 2016,<br />nebo novější |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | Vyvolá `NotSupportedException`                   | Vyvolá `NotSupportedException`     | Throw `NotSupportedException`&ast;&ast;     | Bez chyby |
| `Http1AndHttp2` | Downgradovat na `Http1`                    | Downgradovat na `Http1`     | Downgradovat na `Http1`&ast;&ast;     | Bez chyby |

&ast;&ast; Nakonfigurujte kompatibilní šifrovací sady a nastavte kontext aplikace na přepínač `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` , `true` aby bylo možné tyto scénáře povolit.

#### <a name="reason-for-change"></a>Důvod změny

Tato změna zajišťuje, že chyby kompatibility pro HTTP/2 přes protokol TLS na starších verzích Windows jsou ploché a co nejblížeelné.

#### <a name="recommended-action"></a>Doporučená akce

Zajistěte, aby protokol HTTP/2 přes TLS byl zakázán v nekompatibilních verzích systému Windows. Windows 8.1 a Windows Server 2012 R2 jsou nekompatibilní, protože ve výchozím nastavení nemají nezbytné šifry. Je však možné aktualizovat nastavení konfigurace počítače tak, aby používala šifry kompatibilní s protokolem HTTP/2. Další informace najdete v tématu [šifrovací sady TLS v Windows 8.1](/windows/win32/secauthn/tls-cipher-suites-in-windows-8-1). Po nakonfigurování musí být protokol HTTP/2 přes TLS na Kestrel povolený nastavením přepínače kontextu aplikace `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` . Příklad:

```csharp
AppContext.SetSwitch("Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2", true);
```

Žádná základní podpora se nezměnila. Například HTTP/2 přes protokol TLS nikdy nefungovalo ve Windows 8 nebo Windows Serveru 2012. Tato změna mění způsob, jakým jsou prezentovány chyby v těchto nepodporovaných scénářích.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!--

#### Affected APIs

Not detectable via API analysis

-->
