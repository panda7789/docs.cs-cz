---
ms.openlocfilehash: 3e4a5936bbac4e77efc5f7e68b55ddf49bae5d43
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614484"
---
### <a name="path-colon-checks-are-stricter"></a><span data-ttu-id="ed7d2-101">Kontroly dvojtečky cest jsou přísnější</span><span class="sxs-lookup"><span data-stu-id="ed7d2-101">Path colon checks are stricter</span></span>

#### <a name="details"></a><span data-ttu-id="ed7d2-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ed7d2-102">Details</span></span>

<span data-ttu-id="ed7d2-103">V .NET Framework 4.6.2 byl proveden určitý počet změn pro podporu dříve nepodporovaných cest (jak v délce, tak ve formátu).</span><span class="sxs-lookup"><span data-stu-id="ed7d2-103">In .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in length and format).</span></span> <span data-ttu-id="ed7d2-104">Kontroluje správnost syntaxe oddělovače jednotek (dvojtečky), která měla vedlejší účinky blokování některých cest URI v několika rozhraních API pro výběr cest, kde se používají k tolerování.</span><span class="sxs-lookup"><span data-stu-id="ed7d2-104">Checks for proper drive separator (colon) syntax were made more correct, which had the side effect of blocking some URI paths in a few select Path APIs where they used to be tolerated.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ed7d2-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="ed7d2-105">Suggestion</span></span>

<span data-ttu-id="ed7d2-106">Pokud předáváte identifikátor URI ovlivněným rozhraním API, upravte nejprve řetězec na platnou cestu.</span><span class="sxs-lookup"><span data-stu-id="ed7d2-106">If passing a URI to affected APIs, modify the string to be a legal path first.</span></span><ul><li><span data-ttu-id="ed7d2-107">Ruční odebrání schématu z adres URL (např. odebrání `file://` z adres URL)</span><span class="sxs-lookup"><span data-stu-id="ed7d2-107">Remove the scheme from URLs manually (e.g. remove `file://` from URLs)</span></span>

- <span data-ttu-id="ed7d2-108">Předat identifikátor URI <xref:System.Uri> třídě a použít<xref:System.Uri.LocalPath></span><span class="sxs-lookup"><span data-stu-id="ed7d2-108">Pass the URI to the <xref:System.Uri> class and use <xref:System.Uri.LocalPath></span></span>

<span data-ttu-id="ed7d2-109">Alternativně můžete odhlásit normalizaci nové cesty nastavením `Switch.System.IO.UseLegacyPathHandling` přepínače AppContext na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="ed7d2-109">Alternatively, you can opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling` AppContext switch to true.</span></span>

| <span data-ttu-id="ed7d2-110">Name</span><span class="sxs-lookup"><span data-stu-id="ed7d2-110">Name</span></span>    | <span data-ttu-id="ed7d2-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ed7d2-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ed7d2-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="ed7d2-112">Scope</span></span>   | <span data-ttu-id="ed7d2-113">Edge</span><span class="sxs-lookup"><span data-stu-id="ed7d2-113">Edge</span></span>        |
| <span data-ttu-id="ed7d2-114">Verze</span><span class="sxs-lookup"><span data-stu-id="ed7d2-114">Version</span></span> | <span data-ttu-id="ed7d2-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="ed7d2-115">4.6.2</span></span>       |
| <span data-ttu-id="ed7d2-116">Typ</span><span class="sxs-lookup"><span data-stu-id="ed7d2-116">Type</span></span>    | <span data-ttu-id="ed7d2-117">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="ed7d2-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="ed7d2-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ed7d2-118">Affected APIs</span></span>

- <xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType>
- <xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType>
