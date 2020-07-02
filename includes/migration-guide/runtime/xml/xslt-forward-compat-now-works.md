---
ms.openlocfilehash: e3b9711ac66901d69838de4c9f309d086b06fd4d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620114"
---
### <a name="xslt-forward-compat-now-works"></a><span data-ttu-id="b9b6c-101">Kompatibilita s přesměrováním XSLT teď funguje</span><span class="sxs-lookup"><span data-stu-id="b9b6c-101">XSLT forward compat now works</span></span>

#### <a name="details"></a><span data-ttu-id="b9b6c-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b9b6c-102">Details</span></span>

<span data-ttu-id="b9b6c-103">V .NET Framework 4 došlo k následujícím problémům s dopřednou kompatibilitou XSLT 1,0:</span><span class="sxs-lookup"><span data-stu-id="b9b6c-103">In the .NET Framework 4, XSLT 1.0 forward compatibility had the following issues:</span></span><ul><li><span data-ttu-id="b9b6c-104">Načítání šablony stylů se nezdařilo, pokud byla její verze nastavena jako 2.0 a analyzátor zjistil nerozpoznanou konstrukci XSLT 1.0.</span><span class="sxs-lookup"><span data-stu-id="b9b6c-104">Loading a style sheet failed if its version was set to 2.0 and the parser encountered an unrecognized XSLT 1.0 construct.</span></span></li><li><span data-ttu-id="b9b6c-105"><code>xsl:sort</code>Konstrukce nedokázala seřadit data, pokud byla verze předlohy stylů nastavena na 1,1.</span><span class="sxs-lookup"><span data-stu-id="b9b6c-105">The <code>xsl:sort</code> construct failed to sort data if the style sheet version was set to 1.1.</span></span></li></ul><span data-ttu-id="b9b6c-106">V .NET Framework 4,5 byly tyto problémy vyřešeny a režim dopředné kompatibility XSLT 1,0 funguje správně.</span><span class="sxs-lookup"><span data-stu-id="b9b6c-106">In the .NET Framework 4.5, these issues have been fixed, and XSLT 1.0 forward compatibility mode works properly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b9b6c-107">Návrh</span><span class="sxs-lookup"><span data-stu-id="b9b6c-107">Suggestion</span></span>

<span data-ttu-id="b9b6c-108">Většina aplikací by měla být neovlivněná, ale data se v některých případech řadí jinak v případě, že jsou dodržovány šablony stylů XSL: Sort.</span><span class="sxs-lookup"><span data-stu-id="b9b6c-108">Most apps should be unaffected, however data will be sorted differently in some cases now that xsl:sort is respected.</span></span> <span data-ttu-id="b9b6c-109">Pokud <code>xsl:sort</code> se používá v šablonách stylů 1,1, zkontrolujte, že aplikace nezávisí na neseřazeném pořadí dat.</span><span class="sxs-lookup"><span data-stu-id="b9b6c-109">If <code>xsl:sort</code> is used in 1.1 style sheets, confirm that apps were not depending on the unsorted order of data.</span></span> <span data-ttu-id="b9b6c-110">Pokud aplikace spoléhají na chování řazení 4,0, odeberte <code>xsl:sort</code> je ze seznamu stylů.</span><span class="sxs-lookup"><span data-stu-id="b9b6c-110">If apps rely on the 4.0 sorting behavior, remove <code>xsl:sort</code> from the style sheet.</span></span>

| <span data-ttu-id="b9b6c-111">Name</span><span class="sxs-lookup"><span data-stu-id="b9b6c-111">Name</span></span>    | <span data-ttu-id="b9b6c-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b9b6c-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b9b6c-113">Rozsah</span><span class="sxs-lookup"><span data-stu-id="b9b6c-113">Scope</span></span>   |<span data-ttu-id="b9b6c-114">Edge</span><span class="sxs-lookup"><span data-stu-id="b9b6c-114">Edge</span></span>|
|<span data-ttu-id="b9b6c-115">Verze</span><span class="sxs-lookup"><span data-stu-id="b9b6c-115">Version</span></span>|<span data-ttu-id="b9b6c-116">4.5</span><span class="sxs-lookup"><span data-stu-id="b9b6c-116">4.5</span></span>|
|<span data-ttu-id="b9b6c-117">Typ</span><span class="sxs-lookup"><span data-stu-id="b9b6c-117">Type</span></span>|<span data-ttu-id="b9b6c-118">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="b9b6c-118">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b9b6c-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b9b6c-119">Affected APIs</span></span>

-<xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType></li></ul>|
