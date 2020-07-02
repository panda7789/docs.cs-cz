---
ms.openlocfilehash: 349854b0dec5a585990b9c5e7c0b575df5bf70f3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615731"
---
### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a><span data-ttu-id="6ee46-101">Ověřování schématu XSD teď správně detekuje porušení jedinečných omezení, pokud se používají složené klíče a jeden klíč je prázdný.</span><span class="sxs-lookup"><span data-stu-id="6ee46-101">XSD Schema validation now correctly detects violations of unique constraints if compound keys are used and one key is empty</span></span>

#### <a name="details"></a><span data-ttu-id="6ee46-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6ee46-102">Details</span></span>

<span data-ttu-id="6ee46-103">Verze .NET Framework před 4,6 obsahovaly chybu, která způsobila, že ověření XSD nedetekuje jedinečná omezení u složených klíčů, pokud byl jeden z klíčů prázdný.</span><span class="sxs-lookup"><span data-stu-id="6ee46-103">Versions of the .NET Framework prior to 4.6 had a bug that caused XSD validation to not detect unique constraints on compound keys if one of the keys was empty.</span></span> <span data-ttu-id="6ee46-104">V .NET Framework 4,6 se tento problém opravuje.</span><span class="sxs-lookup"><span data-stu-id="6ee46-104">In the .NET Framework 4.6, this issue is corrected.</span></span> <span data-ttu-id="6ee46-105">Výsledkem bude přesnější ověření, ale může to mít také za následek, že některé XML neověřují, které dříve by měly.</span><span class="sxs-lookup"><span data-stu-id="6ee46-105">This will result in more correct validation, but it may also result in some XML not validating which previously would have.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6ee46-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="6ee46-106">Suggestion</span></span>

<span data-ttu-id="6ee46-107">Pokud je potřeba ověření k dis.NET Framework 4,0, ověření aplikace může cílit na verzi 4,5 (nebo starší) .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6ee46-107">If looser .NET Framework 4.0 validation is needed, the validating application can target version 4.5 (or earlier) of the .NET Framework.</span></span> <span data-ttu-id="6ee46-108">Při přecílení na .NET Framework 4,6 je však nutné provést revizi kódu, aby bylo zajištěno, že nebudou ověřeny duplicitní složené klíče (jak je popsáno v popisu tohoto problému).</span><span class="sxs-lookup"><span data-stu-id="6ee46-108">When retargeting to .NET Framework 4.6, however, code review should be done to be sure that duplicate compound keys (as described in this issue's description) are not expected to validate.</span></span>

| <span data-ttu-id="6ee46-109">Name</span><span class="sxs-lookup"><span data-stu-id="6ee46-109">Name</span></span>    | <span data-ttu-id="6ee46-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6ee46-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6ee46-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="6ee46-111">Scope</span></span>   | <span data-ttu-id="6ee46-112">Edge</span><span class="sxs-lookup"><span data-stu-id="6ee46-112">Edge</span></span>        |
| <span data-ttu-id="6ee46-113">Verze</span><span class="sxs-lookup"><span data-stu-id="6ee46-113">Version</span></span> | <span data-ttu-id="6ee46-114">4.6</span><span class="sxs-lookup"><span data-stu-id="6ee46-114">4.6</span></span>         |
| <span data-ttu-id="6ee46-115">Typ</span><span class="sxs-lookup"><span data-stu-id="6ee46-115">Type</span></span>    | <span data-ttu-id="6ee46-116">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="6ee46-116">Retargeting</span></span> |
