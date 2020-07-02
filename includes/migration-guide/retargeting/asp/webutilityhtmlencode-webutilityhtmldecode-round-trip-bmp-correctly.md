---
ms.openlocfilehash: acb5b467fc8f0692d8fa1b3b8263fd27308cc124
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617150"
---
### <a name="webutilityhtmlencode-and-webutilityhtmldecode-round-trip-bmp-correctly"></a><span data-ttu-id="10320-101">Správně WebUtility.HtmlEncode a WebUtility.HtmlDecode Round-Trip BMP</span><span class="sxs-lookup"><span data-stu-id="10320-101">WebUtility.HtmlEncode and WebUtility.HtmlDecode round-trip BMP correctly</span></span>

#### <a name="details"></a><span data-ttu-id="10320-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="10320-102">Details</span></span>

<span data-ttu-id="10320-103">Pro aplikace, které cílí na .NET Framework 4,5, jsou znaky, které se předávají do metod, v případě, že jsou předávány do metod,, které jsou mimo základní (standarded) (BMP) <xref:System.Net.WebUtility.HtmlDecode(System.String)></span><span class="sxs-lookup"><span data-stu-id="10320-103">For applications that target the .NET Framework 4.5, characters that are outside the Basic Multilingual Plane (BMP) round-trip correctly when they are passed to the <xref:System.Net.WebUtility.HtmlDecode(System.String)> methods.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="10320-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="10320-104">Suggestion</span></span>

<span data-ttu-id="10320-105">Tato změna by neměla mít žádný vliv na aktuální aplikace, ale chcete-li obnovit původní chování, nastavte `targetFramework` atribut `<httpRuntime>` prvku na jiný řetězec než "4,5".</span><span class="sxs-lookup"><span data-stu-id="10320-105">This change should have no effect on current applications, but to restore the original behavior, set the `targetFramework` attribute of the `<httpRuntime>` element to a string other than "4.5".</span></span> <span data-ttu-id="10320-106">Můžete také nastavit `unicodeEncodingConformance` `unicodeDecodingConformance` atributy a `<webUtility>` elementu konfigurace pro řízení tohoto chování nezávisle na cílové verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="10320-106">You can also set the `unicodeEncodingConformance` and `unicodeDecodingConformance` attributes of the `<webUtility>` configuration element to control this behavior independently of the targeted version of the .NET Framework.</span></span>

| <span data-ttu-id="10320-107">Name</span><span class="sxs-lookup"><span data-stu-id="10320-107">Name</span></span>    | <span data-ttu-id="10320-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="10320-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="10320-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="10320-109">Scope</span></span>   | <span data-ttu-id="10320-110">Edge</span><span class="sxs-lookup"><span data-stu-id="10320-110">Edge</span></span>        |
| <span data-ttu-id="10320-111">Verze</span><span class="sxs-lookup"><span data-stu-id="10320-111">Version</span></span> | <span data-ttu-id="10320-112">4.5</span><span class="sxs-lookup"><span data-stu-id="10320-112">4.5</span></span>         |
| <span data-ttu-id="10320-113">Typ</span><span class="sxs-lookup"><span data-stu-id="10320-113">Type</span></span>    | <span data-ttu-id="10320-114">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="10320-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="10320-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="10320-115">Affected APIs</span></span>

- <xref:System.Net.WebUtility.HtmlEncode(System.String)?displayProperty=nameWithType>
- <xref:System.Net.WebUtility.HtmlEncode(System.String,System.IO.TextWriter)?displayProperty=nameWithType>
