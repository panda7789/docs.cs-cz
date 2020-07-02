---
ms.openlocfilehash: 5c949b79eefa68ea6f8d4ad27c716c438e24f170
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619960"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a><span data-ttu-id="02b1e-101">Deserializace objektů napříč doménami aplikace může selhat.</span><span class="sxs-lookup"><span data-stu-id="02b1e-101">Deserialization of objects across appdomains can fail</span></span>

#### <a name="details"></a><span data-ttu-id="02b1e-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="02b1e-102">Details</span></span>

<span data-ttu-id="02b1e-103">V některých případech, když aplikace používá dvě nebo více domén aplikace s různými základy aplikace, se snaží deserializovat objekty v logickém kontextu volání napříč doménami aplikace vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="02b1e-103">In some cases, when an app uses two or more app domains with different application bases, trying to deserialize objects in the logical call context across app domains throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="02b1e-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="02b1e-104">Suggestion</span></span>

<span data-ttu-id="02b1e-105">Viz [zmírnění rizika: deserializace objektů napříč doménami aplikací](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span><span class="sxs-lookup"><span data-stu-id="02b1e-105">See [Mitigation: Deserialization of Objects Across App Domains](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span></span>

| <span data-ttu-id="02b1e-106">Name</span><span class="sxs-lookup"><span data-stu-id="02b1e-106">Name</span></span>    | <span data-ttu-id="02b1e-107">Hodnota</span><span class="sxs-lookup"><span data-stu-id="02b1e-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="02b1e-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="02b1e-108">Scope</span></span>   |<span data-ttu-id="02b1e-109">Edge</span><span class="sxs-lookup"><span data-stu-id="02b1e-109">Edge</span></span>|
|<span data-ttu-id="02b1e-110">Verze</span><span class="sxs-lookup"><span data-stu-id="02b1e-110">Version</span></span>|<span data-ttu-id="02b1e-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="02b1e-111">4.5.1</span></span>|
|<span data-ttu-id="02b1e-112">Typ</span><span class="sxs-lookup"><span data-stu-id="02b1e-112">Type</span></span>|<span data-ttu-id="02b1e-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="02b1e-113">Runtime</span></span>|
