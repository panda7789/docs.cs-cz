---
ms.openlocfilehash: 377a80e2580d035f63ee757de4687f293b120609
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760990"
---
### <a name="tls-1x-by-default-passes-the-schsendauxrecord-flag-to-the-underlying-schannel-api"></a>Protokol TLS 1.x ve výchozím nastavení se předá příznak SCH_SEND_AUX_RECORD základního rozhraní API zprostředkovatele SCHANNEL

|   |   |
|---|---|
|Podrobnosti|Při použití protokolu TLS 1.x, rozhraní .NET Framework spoléhá na základního rozhraní API Windows SCHANNEL. Od verze rozhraní .NET Framework 4.6, [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/desktop/api/schannel/ns-schannel-_schannel_cred) příznak je předán ve výchozím nastavení zprostředkovatele SCHANNEL. To způsobí, že SCHANNEL pro rozdělení dat šifrování na dva samostatné záznamy, první jako jeden bajt a druhý jako <em>n</em>-1 bajtů. Ve výjimečných případech tím je prolomen komunikace mezi klienty a existujících serverů, které se předpokládá, že se data nachází v jednom záznamu.|
|Doporučení|Pokud tuto změnu přeruší komunikace s existujícím serverem, můžete zakázat odesílání [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/desktop/api/schannel/ns-schannel-_schannel_cred) příznak a obnovit předchozí chování není rozdělení dat na samostatné záznamy přidáním následujícího přepínač tak, aby [ \<AppContextSwitchOverrides >](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvek [ \<runtime >](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontEnableSchSendAuxRecord=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] Toto nastavení je dostupné pouze z důvodů zpětné kompatibility. Jeho použití v opačném případě se nedoporučuje.</blockquote> |
|Rozsah|Edge|
|Version|4.6|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|

