---
ms.openlocfilehash: 4a22d78f2308aab544d7a7d2e4d05ddc1ad5457d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617235"
---
### <a name="xml-schema-validation-is-stricter"></a><span data-ttu-id="324e2-101">Ověřování schématu XML je přísnější</span><span class="sxs-lookup"><span data-stu-id="324e2-101">XML schema validation is stricter</span></span>

#### <a name="details"></a><span data-ttu-id="324e2-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="324e2-102">Details</span></span>

<span data-ttu-id="324e2-103">V .NET Framework 4,5 je ověřování schématu XML přísnější.</span><span class="sxs-lookup"><span data-stu-id="324e2-103">In the .NET Framework 4.5, XML schema validation is more strict.</span></span> <span data-ttu-id="324e2-104">Jestliže použijete xsd:anyURI k vyhodnocení URI jako protokolu e-mailu a v URI jsou mezery, vyhodnocení selže.</span><span class="sxs-lookup"><span data-stu-id="324e2-104">If you use xsd:anyURI to validate a URI such as a mailto protocol, validation fails if there are spaces in the URI.</span></span> <span data-ttu-id="324e2-105">V předchozích verzích rozhraní .NET Framework ověření proběhlo úspěšně.</span><span class="sxs-lookup"><span data-stu-id="324e2-105">In previous versions of the .NET Framework, validation succeeded.</span></span> <span data-ttu-id="324e2-106">Tato změna ovlivní pouze aplikace, které cílí na .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="324e2-106">The change affects only applications that target the .NET Framework 4.5.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="324e2-107">Návrh</span><span class="sxs-lookup"><span data-stu-id="324e2-107">Suggestion</span></span>

<span data-ttu-id="324e2-108">Pokud je potřeba ověření k dis.NET Framework 4,0, ověřování aplikace může cílit na verzi 4,0 .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="324e2-108">If looser .NET Framework 4.0 validation is needed, the validating application can target version 4.0 of the .NET Framework.</span></span> <span data-ttu-id="324e2-109">Při přecílení na .NET Framework 4,5 byste však měli provést revizi kódu, aby bylo zajištěno, že neplatné identifikátory URI (s mezerami) nejsou očekávány jako hodnoty atributu s datovým typem anyURI.</span><span class="sxs-lookup"><span data-stu-id="324e2-109">When retargeting to .NET Framework 4.5, however, code review should be done to be sure that invalid URIs (with spaces) are not expected as attribute values with the anyURI data type.</span></span>

| <span data-ttu-id="324e2-110">Name</span><span class="sxs-lookup"><span data-stu-id="324e2-110">Name</span></span>    | <span data-ttu-id="324e2-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="324e2-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="324e2-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="324e2-112">Scope</span></span>   | <span data-ttu-id="324e2-113">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="324e2-113">Minor</span></span>       |
| <span data-ttu-id="324e2-114">Verze</span><span class="sxs-lookup"><span data-stu-id="324e2-114">Version</span></span> | <span data-ttu-id="324e2-115">4.5</span><span class="sxs-lookup"><span data-stu-id="324e2-115">4.5</span></span>         |
| <span data-ttu-id="324e2-116">Typ</span><span class="sxs-lookup"><span data-stu-id="324e2-116">Type</span></span>    | <span data-ttu-id="324e2-117">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="324e2-117">Retargeting</span></span> |
