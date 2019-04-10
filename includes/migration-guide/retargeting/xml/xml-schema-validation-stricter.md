---
ms.openlocfilehash: ef0381dc2ce4373b2a62e8ebefa44152059ca332
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234639"
---
### <a name="xml-schema-validation-is-stricter"></a><span data-ttu-id="6b1c3-101">Je ověřování schématu XML přísnější</span><span class="sxs-lookup"><span data-stu-id="6b1c3-101">XML schema validation is stricter</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6b1c3-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6b1c3-102">Details</span></span>|<span data-ttu-id="6b1c3-103">V rozhraní .NET Framework 4.5 je ověřování schématu XML přísnější.</span><span class="sxs-lookup"><span data-stu-id="6b1c3-103">In the .NET Framework 4.5, XML schema validation is more strict.</span></span> <span data-ttu-id="6b1c3-104">Jestliže použijete xsd:anyURI k vyhodnocení URI jako protokolu e-mailu a v URI jsou mezery, vyhodnocení selže.</span><span class="sxs-lookup"><span data-stu-id="6b1c3-104">If you use xsd:anyURI to validate a URI such as a mailto protocol, validation fails if there are spaces in the URI.</span></span> <span data-ttu-id="6b1c3-105">V předchozích verzích rozhraní .NET Framework ověření proběhlo úspěšně.</span><span class="sxs-lookup"><span data-stu-id="6b1c3-105">In previous versions of the .NET Framework, validation succeeded.</span></span> <span data-ttu-id="6b1c3-106">Změna ovlivní pouze aplikace, které se zaměřují na rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="6b1c3-106">The change affects only applications that target the .NET Framework 4.5.</span></span>|
|<span data-ttu-id="6b1c3-107">Doporučení</span><span class="sxs-lookup"><span data-stu-id="6b1c3-107">Suggestion</span></span>|<span data-ttu-id="6b1c3-108">V případě potřeby volnější ověřování rozhraní .NET Framework 4.0 ověřování aplikace může cílit verzi 4.0 rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6b1c3-108">If looser .NET Framework 4.0 validation is needed, the validating application can target version 4.0 of the .NET Framework.</span></span> <span data-ttu-id="6b1c3-109">Pokud mění se cílení na .NET Framework 4.5, však musí ujistit se, že nejsou neplatné identifikátory URI (s mezerami) stanovená jako hodnoty atributů s datovým typem anyURI provedena revize kódu.</span><span class="sxs-lookup"><span data-stu-id="6b1c3-109">When retargeting to .NET Framework 4.5, however, code review should be done to be sure that invalid URIs (with spaces) are not expected as attribute values with the anyURI data type.</span></span>|
|<span data-ttu-id="6b1c3-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="6b1c3-110">Scope</span></span>|<span data-ttu-id="6b1c3-111">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="6b1c3-111">Minor</span></span>|
|<span data-ttu-id="6b1c3-112">Version</span><span class="sxs-lookup"><span data-stu-id="6b1c3-112">Version</span></span>|<span data-ttu-id="6b1c3-113">4.5</span><span class="sxs-lookup"><span data-stu-id="6b1c3-113">4.5</span></span>|
|<span data-ttu-id="6b1c3-114">Type</span><span class="sxs-lookup"><span data-stu-id="6b1c3-114">Type</span></span>|<span data-ttu-id="6b1c3-115">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="6b1c3-115">Retargeting</span></span>|
