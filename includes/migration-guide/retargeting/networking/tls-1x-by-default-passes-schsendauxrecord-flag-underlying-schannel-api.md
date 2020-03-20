---
ms.openlocfilehash: fc17efbad63ee43ddcdfd14e2fbd1557d2b3d31c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "72424771"
---
### <a name="tls-1x-by-default-passes-the-sch_send_aux_record-flag-to-the-underlying-schannel-api"></a>TLS 1.x ve výchozím nastavení předá příznak SCH_SEND_AUX_RECORD podkladovému rozhraní API kanálu SCHANNEL

|   |   |
|---|---|
|Podrobnosti|Při použití TLS 1.x, rozhraní .NET Framework spoléhá na základní rozhraní API Windows SCHANNEL. Počínaje rozhraním .NET Framework 4.6 je příznak [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) ve výchozím nastavení předán schannel. To způsobí, že SCHANNEL rozdělit data, která mají být zašifrována do dvou samostatných záznamů, první jako jeden bajt a druhý jako <em>n</em>-1 bajtů. Ve výjimečných případech to přeruší komunikaci mezi klienty a existujícími servery, které zapředpokladu, že data jsou umístěna v jednom záznamu.|
|Návrh|Pokud tato změna přeruší komunikaci s existujícím serverem, můžete zakázat odesílání [příznaku SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) a obnovit [<](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) předchozí chování [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) nerozdělení dat do samostatných záznamů přidáním následujícího přepínače k prvku v části konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontEnableSchSendAuxRecord=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] Toto nastavení je k dispozici pouze pro zpětnou kompatibilitu. Jeho použití se jinak nedoporučuje.</blockquote> |
|Rozsah|Edge|
|Version|4.6|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|
