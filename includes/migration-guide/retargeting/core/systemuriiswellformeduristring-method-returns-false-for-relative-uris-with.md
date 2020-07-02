---
ms.openlocfilehash: f7dcf9c4c3dc7ea536ddc847769a1a30f1298bb2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617211"
---
### <a name="systemuriiswellformeduristring-method-returns-false-for-relative-uris-with-a-colon-char-in-first-segment"></a><span data-ttu-id="2f64b-101">Metoda System. URI. IsWellFormedUriString vrátí hodnotu false pro relativní identifikátory URI s znakem dvojtečky v prvním segmentu.</span><span class="sxs-lookup"><span data-stu-id="2f64b-101">System.Uri.IsWellFormedUriString method returns false for relative URIs with a colon char in first segment</span></span>

#### <a name="details"></a><span data-ttu-id="2f64b-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="2f64b-102">Details</span></span>

<span data-ttu-id="2f64b-103">Počínaje .NET Framework 4,5, <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> se budou považovat relativní identifikátory URI s `:` v prvním segmentu za nesprávný formát.</span><span class="sxs-lookup"><span data-stu-id="2f64b-103">Beginning with the .NET Framework 4.5, <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> will treat relative URIs with a `:` in their first segment as not well formed.</span></span> <span data-ttu-id="2f64b-104">Jedná se o změnu z <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> chování v .NET Framework 4,0, které bylo provedeno v souladu s RFC3986.</span><span class="sxs-lookup"><span data-stu-id="2f64b-104">This is a change from <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> behavior in the .NET Framework 4.0 that was made to conform to RFC3986.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2f64b-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="2f64b-105">Suggestion</span></span>

<span data-ttu-id="2f64b-106">Tato změna (například mnoho dalších změn identifikátorů URI) ovlivní pouze aplikace cílené na .NET Framework 4,5 (nebo novější).</span><span class="sxs-lookup"><span data-stu-id="2f64b-106">This change (like many other URI changes) will only affect applications targeting the .NET Framework 4.5 (or later).</span></span> <span data-ttu-id="2f64b-107">Chcete-li nadále používat staré chování, zaměřte aplikaci na .NET Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="2f64b-107">To keep using the old behavior, target the app against the .NET Framework 4.0.</span></span> <span data-ttu-id="2f64b-108">Případně můžete vyhledat identifikátor URI před voláním <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> hledání `:` znaků, které můžete chtít odebrat pro účely ověřování, pokud je staré chování žádoucí.</span><span class="sxs-lookup"><span data-stu-id="2f64b-108">Alternatively, scan URI's prior to calling <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> looking for `:` characters that you may want to remove for validation purposes, if the old behavior is desirable.</span></span>

| <span data-ttu-id="2f64b-109">Name</span><span class="sxs-lookup"><span data-stu-id="2f64b-109">Name</span></span>    | <span data-ttu-id="2f64b-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2f64b-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2f64b-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="2f64b-111">Scope</span></span>   | <span data-ttu-id="2f64b-112">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="2f64b-112">Minor</span></span>       |
| <span data-ttu-id="2f64b-113">Verze</span><span class="sxs-lookup"><span data-stu-id="2f64b-113">Version</span></span> | <span data-ttu-id="2f64b-114">4.5</span><span class="sxs-lookup"><span data-stu-id="2f64b-114">4.5</span></span>         |
| <span data-ttu-id="2f64b-115">Typ</span><span class="sxs-lookup"><span data-stu-id="2f64b-115">Type</span></span>    | <span data-ttu-id="2f64b-116">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="2f64b-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="2f64b-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="2f64b-117">Affected APIs</span></span>

- <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=nameWithType>
