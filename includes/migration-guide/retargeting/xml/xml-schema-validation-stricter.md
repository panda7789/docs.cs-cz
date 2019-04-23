---
ms.openlocfilehash: ef0381dc2ce4373b2a62e8ebefa44152059ca332
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "60118474"
---
### <a name="xml-schema-validation-is-stricter"></a><span data-ttu-id="e5713-101">Je ověřování schématu XML přísnější</span><span class="sxs-lookup"><span data-stu-id="e5713-101">XML schema validation is stricter</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e5713-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e5713-102">Details</span></span>|<span data-ttu-id="e5713-103">V rozhraní .NET Framework 4.5 je ověřování schématu XML přísnější.</span><span class="sxs-lookup"><span data-stu-id="e5713-103">In the .NET Framework 4.5, XML schema validation is more strict.</span></span> <span data-ttu-id="e5713-104">Jestliže použijete xsd:anyURI k vyhodnocení URI jako protokolu e-mailu a v URI jsou mezery, vyhodnocení selže.</span><span class="sxs-lookup"><span data-stu-id="e5713-104">If you use xsd:anyURI to validate a URI such as a mailto protocol, validation fails if there are spaces in the URI.</span></span> <span data-ttu-id="e5713-105">V předchozích verzích rozhraní .NET Framework ověření proběhlo úspěšně.</span><span class="sxs-lookup"><span data-stu-id="e5713-105">In previous versions of the .NET Framework, validation succeeded.</span></span> <span data-ttu-id="e5713-106">Změna ovlivní pouze aplikace, které se zaměřují na rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="e5713-106">The change affects only applications that target the .NET Framework 4.5.</span></span>|
|<span data-ttu-id="e5713-107">Doporučení</span><span class="sxs-lookup"><span data-stu-id="e5713-107">Suggestion</span></span>|<span data-ttu-id="e5713-108">V případě potřeby volnější ověřování rozhraní .NET Framework 4.0 ověřování aplikace může cílit verzi 4.0 rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5713-108">If looser .NET Framework 4.0 validation is needed, the validating application can target version 4.0 of the .NET Framework.</span></span> <span data-ttu-id="e5713-109">Pokud mění se cílení na .NET Framework 4.5, však musí ujistit se, že nejsou neplatné identifikátory URI (s mezerami) stanovená jako hodnoty atributů s datovým typem anyURI provedena revize kódu.</span><span class="sxs-lookup"><span data-stu-id="e5713-109">When retargeting to .NET Framework 4.5, however, code review should be done to be sure that invalid URIs (with spaces) are not expected as attribute values with the anyURI data type.</span></span>|
|<span data-ttu-id="e5713-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="e5713-110">Scope</span></span>|<span data-ttu-id="e5713-111">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="e5713-111">Minor</span></span>|
|<span data-ttu-id="e5713-112">Version</span><span class="sxs-lookup"><span data-stu-id="e5713-112">Version</span></span>|<span data-ttu-id="e5713-113">4.5</span><span class="sxs-lookup"><span data-stu-id="e5713-113">4.5</span></span>|
|<span data-ttu-id="e5713-114">Type</span><span class="sxs-lookup"><span data-stu-id="e5713-114">Type</span></span>|<span data-ttu-id="e5713-115">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="e5713-115">Retargeting</span></span>|
