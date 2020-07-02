---
ms.openlocfilehash: e7f690030a5cb5605645f1ca42a6f08dcdd214f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615703"
---
### <a name="tls-1x-by-default-passes-the-sch_send_aux_record-flag-to-the-underlying-schannel-api"></a><span data-ttu-id="aa27b-101">TLS 1. x ve výchozím nastavení předá příznak SCH_SEND_AUX_RECORD základnímu rozhraní SCHANNEL API.</span><span class="sxs-lookup"><span data-stu-id="aa27b-101">TLS 1.x by default passes the SCH_SEND_AUX_RECORD flag to the underlying SCHANNEL API</span></span>

#### <a name="details"></a><span data-ttu-id="aa27b-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="aa27b-102">Details</span></span>

<span data-ttu-id="aa27b-103">Při použití TLS 1. x .NET Framework spoléhá na základní rozhraní Windows SCHANNEL API.</span><span class="sxs-lookup"><span data-stu-id="aa27b-103">When using TLS 1.x, the .NET Framework relies on the underlying Windows SCHANNEL API.</span></span> <span data-ttu-id="aa27b-104">Počínaje .NET Framework 4,6 se příznak [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) ve výchozím nastavení PŘEdává zprostředkovateli Schannel.</span><span class="sxs-lookup"><span data-stu-id="aa27b-104">Starting with .NET Framework 4.6, the [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) flag is passed by default to SCHANNEL.</span></span> <span data-ttu-id="aa27b-105">To způsobí, že SCHANNEL rozdělí data na dva samostatné záznamy, první jako jeden bajt a druhý jako <em>n</em>-1 bajtů. Ve výjimečných případech dojde k přerušení komunikace mezi klienty a stávajícími servery, které vytvářejí předpoklad, že se data nacházejí v jednom záznamu.</span><span class="sxs-lookup"><span data-stu-id="aa27b-105">This causes SCHANNEL to split data to be encrypted into two separate records, the first as a single byte and the second as <em>n</em>-1 bytes.In rare cases, this breaks communication between clients and existing servers that make the assumption that the data resides in a single record.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="aa27b-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="aa27b-106">Suggestion</span></span>

<span data-ttu-id="aa27b-107">Pokud tato změna přeruší komunikaci s existujícím serverem, můžete zakázat odesílání příznaku [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) a obnovit předchozí chování pro nerozdělení dat do samostatných záznamů přidáním následujícího přepínače do [<](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvku v [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) části konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="aa27b-107">If this change breaks communication with an existing server, you can disable sending the [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) flag and restore the previous behavior of not splitting data into separate records by adding the following switch to the [<](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchSendAuxRecord=true" />
</runtime>
```

> [!IMPORTANT]
> <span data-ttu-id="aa27b-108">Toto nastavení je k dispozici pouze pro zpětnou kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="aa27b-108">This setting is provided for backward compatibility only.</span></span> <span data-ttu-id="aa27b-109">Jeho použití není jinak doporučeno.</span><span class="sxs-lookup"><span data-stu-id="aa27b-109">Its use is otherwise not recommended.</span></span>

| <span data-ttu-id="aa27b-110">Name</span><span class="sxs-lookup"><span data-stu-id="aa27b-110">Name</span></span>    | <span data-ttu-id="aa27b-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="aa27b-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="aa27b-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="aa27b-112">Scope</span></span>   | <span data-ttu-id="aa27b-113">Edge</span><span class="sxs-lookup"><span data-stu-id="aa27b-113">Edge</span></span>        |
| <span data-ttu-id="aa27b-114">Verze</span><span class="sxs-lookup"><span data-stu-id="aa27b-114">Version</span></span> | <span data-ttu-id="aa27b-115">4.6</span><span class="sxs-lookup"><span data-stu-id="aa27b-115">4.6</span></span>         |
| <span data-ttu-id="aa27b-116">Typ</span><span class="sxs-lookup"><span data-stu-id="aa27b-116">Type</span></span>    | <span data-ttu-id="aa27b-117">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="aa27b-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="aa27b-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="aa27b-118">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.ServicePointManager?displayProperty=nameWithType>
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
