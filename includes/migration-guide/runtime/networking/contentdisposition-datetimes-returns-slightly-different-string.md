---
ms.openlocfilehash: c103dff320ae30d02c12ea5c585a47b589da8237
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621133"
---
### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a><span data-ttu-id="eec37-101">ContentDisposition DateTime vrátí mírně odlišný řetězec.</span><span class="sxs-lookup"><span data-stu-id="eec37-101">ContentDisposition DateTimes returns slightly different string</span></span>

#### <a name="details"></a><span data-ttu-id="eec37-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="eec37-102">Details</span></span>

<span data-ttu-id="eec37-103">Řetězcové reprezentace 's byly <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName> aktualizovány, počínaje 4,6, aby vždy představovaly hodinovou komponentu <xref:System.DateTime?displayProperty=fullName> se dvěma číslicemi.</span><span class="sxs-lookup"><span data-stu-id="eec37-103">String representations of <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName>'s have been updated, beginning in 4.6, to always represent the hour component of a <xref:System.DateTime?displayProperty=fullName> with two digits.</span></span> <span data-ttu-id="eec37-104">To je v dodržování [RFC822](https://www.ietf.org/rfc/rfc0822.txt) a [RFC2822](https://www.ietf.org/rfc/rfc2822.txt).</span><span class="sxs-lookup"><span data-stu-id="eec37-104">This is to comply with [RFC822](https://www.ietf.org/rfc/rfc0822.txt) and [RFC2822](https://www.ietf.org/rfc/rfc2822.txt).</span></span> <span data-ttu-id="eec37-105">To způsobí, <xref:System.Net.Mime.ContentDisposition.ToString> že v případě, že jeden z časových prvků dispozice byl před 10:00 dop., se v 4,6 ve scénářích vrátí trochu odlišný řetězec.</span><span class="sxs-lookup"><span data-stu-id="eec37-105">This causes <xref:System.Net.Mime.ContentDisposition.ToString> to return a slightly different string in 4.6 in scenarios where one of the disposition's time elements was before 10:00 AM.</span></span> <span data-ttu-id="eec37-106">Všimněte si, že ContentDispositions jsou někdy serializovány prostřednictvím převodu na řetězce, takže <xref:System.Net.Mime.ContentDisposition.ToString> by měly být přezkoumány všechny operace, serializace nebo volání GetHashCode.</span><span class="sxs-lookup"><span data-stu-id="eec37-106">Note that ContentDispositions are sometimes serialized via converting them to strings, so any <xref:System.Net.Mime.ContentDisposition.ToString> operations, serialization, or GetHashCode calls should be reviewed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="eec37-107">Návrh</span><span class="sxs-lookup"><span data-stu-id="eec37-107">Suggestion</span></span>

<span data-ttu-id="eec37-108">Neočekává se, že řetězcové reprezentace ContentDispositions z různých verzí .NET Framework budou správně porovnány.</span><span class="sxs-lookup"><span data-stu-id="eec37-108">Do not expect that string representations of ContentDispositions from different .NET Framework versions will correctly compare to one another.</span></span> <span data-ttu-id="eec37-109">Pokud je to možné, převeďte řetězce zpět na ContentDispositions, než provedete porovnání.</span><span class="sxs-lookup"><span data-stu-id="eec37-109">Convert the strings back to ContentDispositions, if possible, before conducting a comparison.</span></span>

| <span data-ttu-id="eec37-110">Name</span><span class="sxs-lookup"><span data-stu-id="eec37-110">Name</span></span>    | <span data-ttu-id="eec37-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="eec37-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="eec37-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="eec37-112">Scope</span></span>   |<span data-ttu-id="eec37-113">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="eec37-113">Minor</span></span>|
|<span data-ttu-id="eec37-114">Verze</span><span class="sxs-lookup"><span data-stu-id="eec37-114">Version</span></span>|<span data-ttu-id="eec37-115">4.6</span><span class="sxs-lookup"><span data-stu-id="eec37-115">4.6</span></span>|
|<span data-ttu-id="eec37-116">Typ</span><span class="sxs-lookup"><span data-stu-id="eec37-116">Type</span></span>|<span data-ttu-id="eec37-117">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="eec37-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="eec37-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="eec37-118">Affected APIs</span></span>

-<xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType></li><li><xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType></li></ul>|
