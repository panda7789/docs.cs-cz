---
ms.openlocfilehash: 480cbdecd681408a7e1d6fa366e3f1a4b131ab42
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857564"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="820c5-101">Standardní verze 8.0 kategorie sady Unicode teď podporuje</span><span class="sxs-lookup"><span data-stu-id="820c5-101">Unicode standard version 8.0 categories now supported</span></span>

|   |   |
|---|---|
|<span data-ttu-id="820c5-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="820c5-102">Details</span></span>|<span data-ttu-id="820c5-103">V rozhraní .NET Framework 4.6.2 data ve formátu Unicode byl upgradován z úrovně Unicode Standard verze 6.3 verzi 8.0.</span><span class="sxs-lookup"><span data-stu-id="820c5-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="820c5-104">Při požadování znaky kódování Unicode kategorií v rozhraní .NET Framework 4.6.2, nemusí některé výsledky odpovídají výsledky v předchozích verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="820c5-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="820c5-105">Změnit to většinou ovlivňuje Čerokézština slabik a nové značky samohlásky Tai odrá a tón znaky.</span><span class="sxs-lookup"><span data-stu-id="820c5-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>|
|<span data-ttu-id="820c5-106">Doporučení</span><span class="sxs-lookup"><span data-stu-id="820c5-106">Suggestion</span></span>|<span data-ttu-id="820c5-107">Revize kódu a odebrat nebo změnit logiku, která závisí na pevně zakódované kategoriích znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="820c5-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>|
|<span data-ttu-id="820c5-108">Scope</span><span class="sxs-lookup"><span data-stu-id="820c5-108">Scope</span></span>|<span data-ttu-id="820c5-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="820c5-109">Minor</span></span>|
|<span data-ttu-id="820c5-110">Version</span><span class="sxs-lookup"><span data-stu-id="820c5-110">Version</span></span>|<span data-ttu-id="820c5-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="820c5-111">4.6.2</span></span>|
|<span data-ttu-id="820c5-112">type</span><span class="sxs-lookup"><span data-stu-id="820c5-112">Type</span></span>|<span data-ttu-id="820c5-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="820c5-113">Runtime</span></span>|
|<span data-ttu-id="820c5-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="820c5-114">Affected APIs</span></span>|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|

