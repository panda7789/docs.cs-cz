---
ms.openlocfilehash: e7f690030a5cb5605645f1ca42a6f08dcdd214f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615703"
---
### <a name="tls-1x-by-default-passes-the-sch_send_aux_record-flag-to-the-underlying-schannel-api"></a>TLS 1. x ve výchozím nastavení předá příznak SCH_SEND_AUX_RECORD základnímu rozhraní SCHANNEL API.

#### <a name="details"></a>Podrobnosti

Při použití TLS 1. x .NET Framework spoléhá na základní rozhraní Windows SCHANNEL API. Počínaje .NET Framework 4,6 se příznak [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) ve výchozím nastavení PŘEdává zprostředkovateli Schannel. To způsobí, že SCHANNEL rozdělí data na dva samostatné záznamy, první jako jeden bajt a druhý jako <em>n</em>-1 bajtů. Ve výjimečných případech dojde k přerušení komunikace mezi klienty a stávajícími servery, které vytvářejí předpoklad, že se data nacházejí v jednom záznamu.

#### <a name="suggestion"></a>Návrh

Pokud tato změna přeruší komunikaci s existujícím serverem, můžete zakázat odesílání příznaku [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) a obnovit předchozí chování pro nerozdělení dat do samostatných záznamů přidáním následujícího přepínače do [<](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvku v [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) části konfiguračního souboru aplikace:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchSendAuxRecord=true" />
</runtime>
```

> [!IMPORTANT]
> Toto nastavení je k dispozici pouze pro zpětnou kompatibilitu. Jeho použití není jinak doporučeno.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.6         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.ServicePointManager?displayProperty=nameWithType>
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
