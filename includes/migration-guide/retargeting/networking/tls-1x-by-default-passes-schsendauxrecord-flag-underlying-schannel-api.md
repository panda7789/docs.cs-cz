---
ms.openlocfilehash: fc17efbad63ee43ddcdfd14e2fbd1557d2b3d31c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72424771"
---
### <a name="tls-1x-by-default-passes-the-sch_send_aux_record-flag-to-the-underlying-schannel-api"></a>TLS 1. x ve výchozím nastavení předá příznak SCH_SEND_AUX_RECORD k základnímu rozhraní SCHANNEL API.

|   |   |
|---|---|
|Podrobnosti|Při použití TLS 1. x .NET Framework spoléhá na základní rozhraní Windows SCHANNEL API. Počínaje .NET Framework 4,6 se příznak [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) ve výchozím nastavení PŘEdává zprostředkovateli Schannel. To způsobí, že SCHANNEL rozdělí data na dva samostatné záznamy, první jako jeden bajt a druhý jako <em>n</em>-1 bajtů. Ve výjimečných případech dojde k přerušení komunikace mezi klienty a stávajícími servery, které vytvářejí předpoklad, že se data nacházejí v jednom záznamu.|
|Doporučení|Pokud tato změna přeruší komunikaci s existujícím serverem, můžete zakázat odeslání příznaku [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) a obnovit předchozí chování pro nerozdělení dat do samostatných záznamů přidáním následujícího přepínače do [<](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) . element v části [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontEnableSchSendAuxRecord=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] Toto nastavení je k dispozici pouze pro zpětnou kompatibilitu. Jeho použití není jinak doporučeno.</blockquote> |
|Rozsah|Edge|
|Version|4.6|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|
