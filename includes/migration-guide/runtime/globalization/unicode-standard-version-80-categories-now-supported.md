---
ms.openlocfilehash: efa0efaf40e2e432d477f1659d7bde3abc98241d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857564"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="c33cd-101">Nyní podporované kategorie standardu Unicode verze 8.0</span><span class="sxs-lookup"><span data-stu-id="c33cd-101">Unicode standard version 8.0 categories now supported</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c33cd-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c33cd-102">Details</span></span>|<span data-ttu-id="c33cd-103">V rozhraní .NET Framework 4.6.2 byla data unicode upgradována z unicode standard verze 6.3 na verzi 8.0.</span><span class="sxs-lookup"><span data-stu-id="c33cd-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="c33cd-104">Při požadování kategorií znaků Unicode v rozhraní .NET Framework 4.6.2 nemusí některé výsledky odpovídat výsledkům v předchozích verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c33cd-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="c33cd-105">Tato změna se týká především Cherokee slabiky a New Tai Lue samohlásek znamení a tón značky.</span><span class="sxs-lookup"><span data-stu-id="c33cd-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>|
|<span data-ttu-id="c33cd-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="c33cd-106">Suggestion</span></span>|<span data-ttu-id="c33cd-107">Zkontrolujte kód a odeberte/změňte logiku, která závisí na pevně zakódovaných kategoriích znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="c33cd-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>|
|<span data-ttu-id="c33cd-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="c33cd-108">Scope</span></span>|<span data-ttu-id="c33cd-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="c33cd-109">Minor</span></span>|
|<span data-ttu-id="c33cd-110">Version</span><span class="sxs-lookup"><span data-stu-id="c33cd-110">Version</span></span>|<span data-ttu-id="c33cd-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="c33cd-111">4.6.2</span></span>|
|<span data-ttu-id="c33cd-112">Typ</span><span class="sxs-lookup"><span data-stu-id="c33cd-112">Type</span></span>|<span data-ttu-id="c33cd-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="c33cd-113">Runtime</span></span>|
|<span data-ttu-id="c33cd-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c33cd-114">Affected APIs</span></span>|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|
