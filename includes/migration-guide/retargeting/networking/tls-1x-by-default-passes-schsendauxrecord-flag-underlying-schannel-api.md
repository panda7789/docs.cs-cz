---
ms.openlocfilehash: 19dcdf006de0bfa7c6b0a8127612a49a66a24802
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804616"
---
### <a name="tls-1x-by-default-passes-the-schsendauxrecord-flag-to-the-underlying-schannel-api"></a>Protokol TLS 1.x ve výchozím nastavení se předá příznak SCH_SEND_AUX_RECORD základního rozhraní API zprostředkovatele SCHANNEL

|   |   |
|---|---|
|Podrobnosti|Při použití protokolu TLS 1.x, rozhraní .NET Framework spoléhá na základního rozhraní API Windows SCHANNEL. Od verze rozhraní .NET Framework 4.6, [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/desktop/api/schannel/ns-schannel-_schannel_cred) příznak je předán ve výchozím nastavení zprostředkovatele SCHANNEL. To způsobí, že SCHANNEL pro rozdělení dat šifrování na dva samostatné záznamy, první jako jeden bajt a druhý jako <em>n</em>-1 bajtů. Ve výjimečných případech tím je prolomen komunikace mezi klienty a existujících serverů, které se předpokládá, že se data nachází v jednom záznamu.|
|Doporučení|Pokud tuto změnu přeruší komunikace s existujícím serverem, můžete zakázat odesílání [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/desktop/api/schannel/ns-schannel-_schannel_cred) příznak a obnovit předchozí chování není rozdělení dat na samostatné záznamy přidáním následujícího přepínač tak, aby [ < ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvek [ < ](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontEnableSchSendAuxRecord=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] Toto nastavení je dostupné pouze z důvodů zpětné kompatibility. Jeho použití v opačném případě se nedoporučuje.</blockquote> |
|Scope|Edge|
|Version|4.6|
|type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|

