---
ms.openlocfilehash: 0024b2a53444319788b8cdd312d537f994070b5e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614509"
---
### <a name="sslstream-supports-tls-alerts"></a>SslStream podporuje výstrahy TLS.

#### <a name="details"></a>Podrobnosti

Po neúspěšném ověření TLS handshake <xref:System.IO.IOException?displayProperty=fullName> <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> bude při první vstupně-výstupní operaci čtení/zápisu vygenerována vnitřní výjimka. <xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=fullName>Kód pro je <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> možné namapovat na výstrahu TLS od vzdálené strany pomocí [kódů chyb Schannel pro výstrahy TLS a SSL](https://docs.microsoft.com/windows/desktop/SecAuthN/schannel-error-codes-for-tls-and-ssl-alerts). Další informace najdete v [dokumentu RFC 2246: upozornění na chyby oddílu](https://tools.ietf.org/html/rfc2246#section-7.2.2)s. <br/>Chování v .NET Framework 4.6.2 a starším je to, že transportní kanál (obvykle připojení TCP) bude mít časový limit během zápisu nebo čtení, pokud druhá strana nedokázala handshake a okamžitě následně odmítla připojení.

#### <a name="suggestion"></a>Návrh

Aplikace volající rozhraní API v/v sítě, jako <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)> / <xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)> je například obslužná rutina <xref:System.IO.IOException> nebo <xref:System.TimeoutException?displayProperty=fullName> .<br/>Ve výchozím nastavení je funkce výstrahy TLS povolená od .NET Framework 4,7. Aplikace cílené na verze .NET Framework od 4,0 do 4.6.2, které běží na .NET Framework 4,7 nebo vyšší systém, budou mít funkci zakázanou, aby zachovala kompatibilitu. <br/>K dispozici je následující konfigurační rozhraní API, které umožňuje povolit nebo zakázat funkci .NET Framework 4,6 a novějších aplikací spuštěných v .NET Framework 4,7 nebo novějším.

- Programově: musí se jednat o velmi první věc, kterou aplikace provede, protože Třída ServicePointManager se inicializuje jenom jednou:

    ```csharp
    AppContext.SetSwitch("TestSwitch.LocalAppContext.DisableCaching", true);

    // Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2.
    AppContext.SetSwitch("Switch.System.Net.DontEnableTlsAlerts", true);
    ```

- AppConfig

    ```xml
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Net.DontEnableTlsAlerts=true"/>
      <!-- Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2. -->
    </runtime>
    ```

- Klíč registru (globální počítač): nastavte hodnotu pro `false` Povolení funkce v .NET Framework 4,6-4.6.2.

    ```ini
    Key: HKLM\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\AppContext\Switch.System.Net.DontEnableTlsAlerts
    - Type: String
    - Value: "true"
    ```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4,7         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.WebRequest?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Http?displayProperty=nameWithType>
