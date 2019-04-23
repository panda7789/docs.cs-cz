---
ms.openlocfilehash: 891c29b731214fb0028e960256b79cfc267d86b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803652"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a><span data-ttu-id="b9967-101">Deserializace objektů mezi doménami appdomains může selhat.</span><span class="sxs-lookup"><span data-stu-id="b9967-101">Deserialization of objects across appdomains can fail</span></span>

|   |   |
|---|---|
|<span data-ttu-id="b9967-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b9967-102">Details</span></span>|<span data-ttu-id="b9967-103">V některých případech kdy aplikace používá dvě nebo více domén aplikace s různými základy cesty aplikace, při pokusu o deserializaci objektů v logického kontextu volání mezi doménami aplikace výjimku.</span><span class="sxs-lookup"><span data-stu-id="b9967-103">In some cases, when an app uses two or more app domains with different application bases, trying to deserialize objects in the logical call context across app domains throws an exception.</span></span>|
|<span data-ttu-id="b9967-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="b9967-104">Suggestion</span></span>|<span data-ttu-id="b9967-105">Zobrazit [omezení rizik: Deserializace objektů mezi doménami aplikace](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span><span class="sxs-lookup"><span data-stu-id="b9967-105">See [Mitigation: Deserialization of Objects Across App Domains](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span></span>|
|<span data-ttu-id="b9967-106">Rozsah</span><span class="sxs-lookup"><span data-stu-id="b9967-106">Scope</span></span>|<span data-ttu-id="b9967-107">Edge</span><span class="sxs-lookup"><span data-stu-id="b9967-107">Edge</span></span>|
|<span data-ttu-id="b9967-108">Version</span><span class="sxs-lookup"><span data-stu-id="b9967-108">Version</span></span>|<span data-ttu-id="b9967-109">4.5.1</span><span class="sxs-lookup"><span data-stu-id="b9967-109">4.5.1</span></span>|
|<span data-ttu-id="b9967-110">Type</span><span class="sxs-lookup"><span data-stu-id="b9967-110">Type</span></span>|<span data-ttu-id="b9967-111">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="b9967-111">Runtime</span></span>|
