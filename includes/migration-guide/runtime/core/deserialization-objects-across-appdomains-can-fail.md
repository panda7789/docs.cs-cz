---
ms.openlocfilehash: 891c29b731214fb0028e960256b79cfc267d86b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649050"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a><span data-ttu-id="4782b-101">Deserializace objektů mezi doménami appdomains může selhat.</span><span class="sxs-lookup"><span data-stu-id="4782b-101">Deserialization of objects across appdomains can fail</span></span>

|   |   |
|---|---|
|<span data-ttu-id="4782b-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="4782b-102">Details</span></span>|<span data-ttu-id="4782b-103">V některých případech kdy aplikace používá dvě nebo více domén aplikace s různými základy cesty aplikace, při pokusu o deserializaci objektů v logického kontextu volání mezi doménami aplikace výjimku.</span><span class="sxs-lookup"><span data-stu-id="4782b-103">In some cases, when an app uses two or more app domains with different application bases, trying to deserialize objects in the logical call context across app domains throws an exception.</span></span>|
|<span data-ttu-id="4782b-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="4782b-104">Suggestion</span></span>|<span data-ttu-id="4782b-105">Zobrazit [omezení rizik: Deserializace objektů mezi doménami aplikace](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span><span class="sxs-lookup"><span data-stu-id="4782b-105">See [Mitigation: Deserialization of Objects Across App Domains](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span></span>|
|<span data-ttu-id="4782b-106">Rozsah</span><span class="sxs-lookup"><span data-stu-id="4782b-106">Scope</span></span>|<span data-ttu-id="4782b-107">Edge</span><span class="sxs-lookup"><span data-stu-id="4782b-107">Edge</span></span>|
|<span data-ttu-id="4782b-108">Version</span><span class="sxs-lookup"><span data-stu-id="4782b-108">Version</span></span>|<span data-ttu-id="4782b-109">4.5.1</span><span class="sxs-lookup"><span data-stu-id="4782b-109">4.5.1</span></span>|
|<span data-ttu-id="4782b-110">Type</span><span class="sxs-lookup"><span data-stu-id="4782b-110">Type</span></span>|<span data-ttu-id="4782b-111">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="4782b-111">Runtime</span></span>|
