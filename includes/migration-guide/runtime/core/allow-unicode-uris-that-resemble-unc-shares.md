---
ms.openlocfilehash: 3e8601ba76dfb05e3d70b3af7440bd7e228768d0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621064"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a><span data-ttu-id="85f52-101">Povoluje kódování Unicode v identifikátorech URI, které se podobají sdíleným složkám UNC</span><span class="sxs-lookup"><span data-stu-id="85f52-101">Allow Unicode in URIs that resemble UNC shares</span></span>

#### <a name="details"></a><span data-ttu-id="85f52-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="85f52-102">Details</span></span>

<span data-ttu-id="85f52-103">V systému se <xref:System.Uri?displayProperty=fullName> konstrukce identifikátoru URI souboru, který obsahuje název sdílené složky UNC a znakům Unicode, již nevede k identifikátoru URI s neplatným vnitřním stavem.</span><span class="sxs-lookup"><span data-stu-id="85f52-103">In <xref:System.Uri?displayProperty=fullName>, constructing a file URI containing both a UNC share name and Unicode characters will no longer result in a URI with invalid internal state.</span></span> <span data-ttu-id="85f52-104">Chování se změní jenom v případě, že jsou splněné všechny následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="85f52-104">The behavior will change only when all of the following are true:</span></span><ul><li><span data-ttu-id="85f52-105">Identifikátor URI má schéma <code>file:</code> a je následován čtyřmi nebo více lomítky.</span><span class="sxs-lookup"><span data-stu-id="85f52-105">The URI has the scheme <code>file:</code> and is followed by four or more slashes.</span></span></li><li><span data-ttu-id="85f52-106">Název hostitele začíná podtržítkem nebo jiným nerezervovaným symbolem.</span><span class="sxs-lookup"><span data-stu-id="85f52-106">The host name begins with an underscore or other non-reserved symbol.</span></span></li><li><span data-ttu-id="85f52-107">Identifikátor URI obsahuje znaky Unicode.</span><span class="sxs-lookup"><span data-stu-id="85f52-107">The URI contains Unicode characters.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="85f52-108">Návrh</span><span class="sxs-lookup"><span data-stu-id="85f52-108">Suggestion</span></span>

<span data-ttu-id="85f52-109">Aplikace pracující se stejnými identifikátory URI, které obsahují Unicode, by mohly mít k dispozici toto chování k zakázání odkazů na sdílené složky UNC.</span><span class="sxs-lookup"><span data-stu-id="85f52-109">Applications working with URIs consistently containing Unicode could have conceivably used this behavior to disallow references to UNC shares.</span></span> <span data-ttu-id="85f52-110">Tyto aplikace by se měly používat <xref:System.Uri.IsUnc> místo toho.</span><span class="sxs-lookup"><span data-stu-id="85f52-110">Those applications should use <xref:System.Uri.IsUnc> instead.</span></span>

| <span data-ttu-id="85f52-111">Name</span><span class="sxs-lookup"><span data-stu-id="85f52-111">Name</span></span>    | <span data-ttu-id="85f52-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="85f52-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="85f52-113">Rozsah</span><span class="sxs-lookup"><span data-stu-id="85f52-113">Scope</span></span>   |<span data-ttu-id="85f52-114">Edge</span><span class="sxs-lookup"><span data-stu-id="85f52-114">Edge</span></span>|
|<span data-ttu-id="85f52-115">Verze</span><span class="sxs-lookup"><span data-stu-id="85f52-115">Version</span></span>|<span data-ttu-id="85f52-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="85f52-116">4.7.2</span></span>|
|<span data-ttu-id="85f52-117">Typ</span><span class="sxs-lookup"><span data-stu-id="85f52-117">Type</span></span>|<span data-ttu-id="85f52-118">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="85f52-118">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="85f52-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="85f52-119">Affected APIs</span></span>

-<xref:System.Uri?displayProperty=nameWithType></li></ul>|
