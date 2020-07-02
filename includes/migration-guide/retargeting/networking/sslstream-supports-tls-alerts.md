---
ms.openlocfilehash: 0024b2a53444319788b8cdd312d537f994070b5e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614509"
---
### <a name="sslstream-supports-tls-alerts"></a><span data-ttu-id="287fd-101">SslStream podporuje výstrahy TLS.</span><span class="sxs-lookup"><span data-stu-id="287fd-101">SslStream supports TLS Alerts</span></span>

#### <a name="details"></a><span data-ttu-id="287fd-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="287fd-102">Details</span></span>

<span data-ttu-id="287fd-103">Po neúspěšném ověření TLS handshake <xref:System.IO.IOException?displayProperty=fullName> <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> bude při první vstupně-výstupní operaci čtení/zápisu vygenerována vnitřní výjimka.</span><span class="sxs-lookup"><span data-stu-id="287fd-103">After a failed TLS handshake, an <xref:System.IO.IOException?displayProperty=fullName> with an inner <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> exception will be thrown by the first I/O Read/Write operation.</span></span> <span data-ttu-id="287fd-104"><xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=fullName>Kód pro je <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> možné namapovat na výstrahu TLS od vzdálené strany pomocí [kódů chyb Schannel pro výstrahy TLS a SSL](https://docs.microsoft.com/windows/desktop/SecAuthN/schannel-error-codes-for-tls-and-ssl-alerts). Další informace najdete v [dokumentu RFC 2246: upozornění na chyby oddílu](https://tools.ietf.org/html/rfc2246#section-7.2.2)s.</span><span class="sxs-lookup"><span data-stu-id="287fd-104">The <xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=fullName> code for the <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> can be mapped to the TLS Alert from the remote party using the [Schannel error codes for TLS and SSL alerts](https://docs.microsoft.com/windows/desktop/SecAuthN/schannel-error-codes-for-tls-and-ssl-alerts).For more information, see [RFC 2246: Section 7.2.2 Error alerts](https://tools.ietf.org/html/rfc2246#section-7.2.2).</span></span> <br/><span data-ttu-id="287fd-105">Chování v .NET Framework 4.6.2 a starším je to, že transportní kanál (obvykle připojení TCP) bude mít časový limit během zápisu nebo čtení, pokud druhá strana nedokázala handshake a okamžitě následně odmítla připojení.</span><span class="sxs-lookup"><span data-stu-id="287fd-105">The behavior in .NET Framework 4.6.2 and earlier is that the transport channel (usually TCP connection) will timeout during either Write or Read if the other party failed the handshake and immediately afterwards rejected the connection.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="287fd-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="287fd-106">Suggestion</span></span>

<span data-ttu-id="287fd-107">Aplikace volající rozhraní API v/v sítě, jako <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)> / <xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)> je například obslužná rutina <xref:System.IO.IOException> nebo <xref:System.TimeoutException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="287fd-107">Applications calling network I/O APIs such as <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)>/<xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)> should handle <xref:System.IO.IOException> or <xref:System.TimeoutException?displayProperty=fullName>.</span></span><br/><span data-ttu-id="287fd-108">Ve výchozím nastavení je funkce výstrahy TLS povolená od .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="287fd-108">The TLS Alerts feature is enabled by default starting with .NET Framework 4.7.</span></span> <span data-ttu-id="287fd-109">Aplikace cílené na verze .NET Framework od 4,0 do 4.6.2, které běží na .NET Framework 4,7 nebo vyšší systém, budou mít funkci zakázanou, aby zachovala kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="287fd-109">Applications targeting versions of the .NET Framework from 4.0 through 4.6.2 running on a .NET Framework 4.7 or higher system will have the feature disabled to preserve compatibility.</span></span> <br/><span data-ttu-id="287fd-110">K dispozici je následující konfigurační rozhraní API, které umožňuje povolit nebo zakázat funkci .NET Framework 4,6 a novějších aplikací spuštěných v .NET Framework 4,7 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="287fd-110">The following configuration API is available to enable or disable the feature for .NET Framework 4.6 and later applications running on .NET Framework 4.7 or later.</span></span>

- <span data-ttu-id="287fd-111">Programově: musí se jednat o velmi první věc, kterou aplikace provede, protože Třída ServicePointManager se inicializuje jenom jednou:</span><span class="sxs-lookup"><span data-stu-id="287fd-111">Programmatically:   Must be the very first thing the application does since ServicePointManager will initialize only once:</span></span>

    ```csharp
    AppContext.SetSwitch("TestSwitch.LocalAppContext.DisableCaching", true);

    // Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2.
    AppContext.SetSwitch("Switch.System.Net.DontEnableTlsAlerts", true);
    ```

- <span data-ttu-id="287fd-112">AppConfig</span><span class="sxs-lookup"><span data-stu-id="287fd-112">AppConfig:</span></span>

    ```xml
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Net.DontEnableTlsAlerts=true"/>
      <!-- Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2. -->
    </runtime>
    ```

- <span data-ttu-id="287fd-113">Klíč registru (globální počítač): nastavte hodnotu pro `false` Povolení funkce v .NET Framework 4,6-4.6.2.</span><span class="sxs-lookup"><span data-stu-id="287fd-113">Registry key (machine global):   Set the Value to `false` to enable the feature in .NET Framework 4.6 - 4.6.2.</span></span>

    ```ini
    Key: HKLM\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\AppContext\Switch.System.Net.DontEnableTlsAlerts
    - Type: String
    - Value: "true"
    ```

| <span data-ttu-id="287fd-114">Name</span><span class="sxs-lookup"><span data-stu-id="287fd-114">Name</span></span>    | <span data-ttu-id="287fd-115">Hodnota</span><span class="sxs-lookup"><span data-stu-id="287fd-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="287fd-116">Rozsah</span><span class="sxs-lookup"><span data-stu-id="287fd-116">Scope</span></span>   | <span data-ttu-id="287fd-117">Edge</span><span class="sxs-lookup"><span data-stu-id="287fd-117">Edge</span></span>        |
| <span data-ttu-id="287fd-118">Verze</span><span class="sxs-lookup"><span data-stu-id="287fd-118">Version</span></span> | <span data-ttu-id="287fd-119">4,7</span><span class="sxs-lookup"><span data-stu-id="287fd-119">4.7</span></span>         |
| <span data-ttu-id="287fd-120">Typ</span><span class="sxs-lookup"><span data-stu-id="287fd-120">Type</span></span>    | <span data-ttu-id="287fd-121">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="287fd-121">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="287fd-122">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="287fd-122">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.WebRequest?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Http?displayProperty=nameWithType>
