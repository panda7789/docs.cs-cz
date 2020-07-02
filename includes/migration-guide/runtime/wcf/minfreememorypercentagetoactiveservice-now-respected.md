---
ms.openlocfilehash: f8e5dee9e97956cea78b7c8ec999af1afe9ac66b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620050"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a><span data-ttu-id="3636b-101">MinFreeMemoryPercentageToActiveService se teď dodržuje.</span><span class="sxs-lookup"><span data-stu-id="3636b-101">MinFreeMemoryPercentageToActiveService is now respected</span></span>

#### <a name="details"></a><span data-ttu-id="3636b-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3636b-102">Details</span></span>

<span data-ttu-id="3636b-103">Toto nastavení určuje minimální velikost paměti, která musí být k dispozici na serveru, než bude možné aktivovat službu WCF.</span><span class="sxs-lookup"><span data-stu-id="3636b-103">This setting establishes the minimum memory that must be available on the server before a WCF service can be activated.</span></span> <span data-ttu-id="3636b-104">Je navržena tak, aby nedocházelo k <xref:System.OutOfMemoryException?displayProperty=fullName> výjimkám.</span><span class="sxs-lookup"><span data-stu-id="3636b-104">It is designed to prevent <xref:System.OutOfMemoryException?displayProperty=fullName> exceptions.</span></span> <span data-ttu-id="3636b-105">V .NET Framework 4,5 Toto nastavení nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="3636b-105">In the .NET Framework 4.5, this setting had no effect.</span></span> <span data-ttu-id="3636b-106">V .NET Framework 4.5.1 je nastavení pozorováno.</span><span class="sxs-lookup"><span data-stu-id="3636b-106">In the .NET Framework 4.5.1, the setting is observed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3636b-107">Návrh</span><span class="sxs-lookup"><span data-stu-id="3636b-107">Suggestion</span></span>

<span data-ttu-id="3636b-108">K výjimce dojde, pokud je volná paměť na webovém serveru menší než procento definované konfiguračním nastavením.</span><span class="sxs-lookup"><span data-stu-id="3636b-108">An exception occurs if the free memory available on the web server is less than the percentage defined by the configuration setting.</span></span> <span data-ttu-id="3636b-109">Některé služby WCF, které úspěšně začaly a běžely v prostředí omezené paměti, teď můžou selhat.</span><span class="sxs-lookup"><span data-stu-id="3636b-109">Some WCF services that successfully started and ran in a constrained memory environment may now fail.</span></span>

| <span data-ttu-id="3636b-110">Name</span><span class="sxs-lookup"><span data-stu-id="3636b-110">Name</span></span>    | <span data-ttu-id="3636b-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3636b-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3636b-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="3636b-112">Scope</span></span>   |<span data-ttu-id="3636b-113">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="3636b-113">Minor</span></span>|
|<span data-ttu-id="3636b-114">Verze</span><span class="sxs-lookup"><span data-stu-id="3636b-114">Version</span></span>|<span data-ttu-id="3636b-115">4.5.1</span><span class="sxs-lookup"><span data-stu-id="3636b-115">4.5.1</span></span>|
|<span data-ttu-id="3636b-116">Typ</span><span class="sxs-lookup"><span data-stu-id="3636b-116">Type</span></span>|<span data-ttu-id="3636b-117">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="3636b-117">Runtime</span></span>|
