---
ms.openlocfilehash: fa472b3a142f55f0cbdd83eabbbb00bddd9786d8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981531"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a><span data-ttu-id="34fcb-101">Nyní je dodržena MinFreeMemoryPercentageToActiveService</span><span class="sxs-lookup"><span data-stu-id="34fcb-101">MinFreeMemoryPercentageToActiveService is now respected</span></span>

|   |   |
|---|---|
|<span data-ttu-id="34fcb-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="34fcb-102">Details</span></span>|<span data-ttu-id="34fcb-103">Toto nastavení vytváří minimální velikost paměti, které musí být k dispozici na serveru, před aktivací služby WCF.</span><span class="sxs-lookup"><span data-stu-id="34fcb-103">This setting establishes the minimum memory that must be available on the server before a WCF service can be activated.</span></span> <span data-ttu-id="34fcb-104">Slouží k zabránění <xref:System.OutOfMemoryException?displayProperty=name> výjimky.</span><span class="sxs-lookup"><span data-stu-id="34fcb-104">It is designed to prevent <xref:System.OutOfMemoryException?displayProperty=name> exceptions.</span></span> <span data-ttu-id="34fcb-105">Toto nastavení v rozhraní .NET Framework 4.5, nemělo žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="34fcb-105">In the .NET Framework 4.5, this setting had no effect.</span></span> <span data-ttu-id="34fcb-106">V rozhraní .NET Framework 4.5.1 nezaznamenáme nastavení.</span><span class="sxs-lookup"><span data-stu-id="34fcb-106">In the .NET Framework 4.5.1, the setting is observed.</span></span>|
|<span data-ttu-id="34fcb-107">Doporučení</span><span class="sxs-lookup"><span data-stu-id="34fcb-107">Suggestion</span></span>|<span data-ttu-id="34fcb-108">Pokud volné paměti dostupné na webovém serveru je nižší než procento definované v nastavení konfigurace, dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="34fcb-108">An exception occurs if the free memory available on the web server is less than the percentage defined by the configuration setting.</span></span> <span data-ttu-id="34fcb-109">Některé služby WCF, které úspěšně spuštěny a byl spuštěn v prostředí omezené paměti teď může selhat.</span><span class="sxs-lookup"><span data-stu-id="34fcb-109">Some WCF services that successfully started and ran in a constrained memory environment may now fail.</span></span>|
|<span data-ttu-id="34fcb-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="34fcb-110">Scope</span></span>|<span data-ttu-id="34fcb-111">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="34fcb-111">Minor</span></span>|
|<span data-ttu-id="34fcb-112">Version</span><span class="sxs-lookup"><span data-stu-id="34fcb-112">Version</span></span>|<span data-ttu-id="34fcb-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="34fcb-113">4.5.1</span></span>|
|<span data-ttu-id="34fcb-114">Type</span><span class="sxs-lookup"><span data-stu-id="34fcb-114">Type</span></span>|<span data-ttu-id="34fcb-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="34fcb-115">Runtime</span></span>|
