---
ms.openlocfilehash: 891c29b731214fb0028e960256b79cfc267d86b9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235249"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a><span data-ttu-id="714b4-101">Deserializace objektů mezi doménami appdomains může selhat.</span><span class="sxs-lookup"><span data-stu-id="714b4-101">Deserialization of objects across appdomains can fail</span></span>

|   |   |
|---|---|
|<span data-ttu-id="714b4-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="714b4-102">Details</span></span>|<span data-ttu-id="714b4-103">V některých případech kdy aplikace používá dvě nebo více domén aplikace s různými základy cesty aplikace, při pokusu o deserializaci objektů v logického kontextu volání mezi doménami aplikace výjimku.</span><span class="sxs-lookup"><span data-stu-id="714b4-103">In some cases, when an app uses two or more app domains with different application bases, trying to deserialize objects in the logical call context across app domains throws an exception.</span></span>|
|<span data-ttu-id="714b4-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="714b4-104">Suggestion</span></span>|<span data-ttu-id="714b4-105">Zobrazit [omezení rizik: Deserializace objektů mezi doménami aplikace](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span><span class="sxs-lookup"><span data-stu-id="714b4-105">See [Mitigation: Deserialization of Objects Across App Domains](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span></span>|
|<span data-ttu-id="714b4-106">Rozsah</span><span class="sxs-lookup"><span data-stu-id="714b4-106">Scope</span></span>|<span data-ttu-id="714b4-107">Edge</span><span class="sxs-lookup"><span data-stu-id="714b4-107">Edge</span></span>|
|<span data-ttu-id="714b4-108">Version</span><span class="sxs-lookup"><span data-stu-id="714b4-108">Version</span></span>|<span data-ttu-id="714b4-109">4.5.1</span><span class="sxs-lookup"><span data-stu-id="714b4-109">4.5.1</span></span>|
|<span data-ttu-id="714b4-110">Type</span><span class="sxs-lookup"><span data-stu-id="714b4-110">Type</span></span>|<span data-ttu-id="714b4-111">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="714b4-111">Runtime</span></span>|
