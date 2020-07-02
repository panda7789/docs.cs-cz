---
ms.openlocfilehash: a20fad5f9c95e59c14ffd91f4921cf8bfab443cd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621073"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="f7f08-101">Podporuje se teď Standard Unicode Standard verze 8,0.</span><span class="sxs-lookup"><span data-stu-id="f7f08-101">Unicode standard version 8.0 categories now supported</span></span>

#### <a name="details"></a><span data-ttu-id="f7f08-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="f7f08-102">Details</span></span>

<span data-ttu-id="f7f08-103">V .NET Framework 4.6.2 byla data Unicode upgradována z verze Standard Unicode 6,3 na verzi 8,0.</span><span class="sxs-lookup"><span data-stu-id="f7f08-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="f7f08-104">Při požadování kategorií znaků Unicode v .NET Framework 4.6.2 nemusí některé výsledky odpovídat výsledkům v předchozích .NET Framework verzích.</span><span class="sxs-lookup"><span data-stu-id="f7f08-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="f7f08-105">Tato změna většinou ovlivňuje modifikátory slabik a nové Tai Lue – značky a značky tónů.</span><span class="sxs-lookup"><span data-stu-id="f7f08-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f7f08-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="f7f08-106">Suggestion</span></span>

<span data-ttu-id="f7f08-107">Zkontrolujte kód a odeberte nebo změňte logiku, která závisí na pevně zakódovaných kategoriích znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="f7f08-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>

| <span data-ttu-id="f7f08-108">Name</span><span class="sxs-lookup"><span data-stu-id="f7f08-108">Name</span></span>    | <span data-ttu-id="f7f08-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f7f08-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f7f08-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="f7f08-110">Scope</span></span>   |<span data-ttu-id="f7f08-111">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="f7f08-111">Minor</span></span>|
|<span data-ttu-id="f7f08-112">Verze</span><span class="sxs-lookup"><span data-stu-id="f7f08-112">Version</span></span>|<span data-ttu-id="f7f08-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="f7f08-113">4.6.2</span></span>|
|<span data-ttu-id="f7f08-114">Typ</span><span class="sxs-lookup"><span data-stu-id="f7f08-114">Type</span></span>|<span data-ttu-id="f7f08-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="f7f08-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f7f08-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="f7f08-116">Affected APIs</span></span>

-<xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|
