---
ms.openlocfilehash: 84f570cbbd97be79426e117d4c97ec182a397fd4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981539"
---
### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a><span data-ttu-id="44757-101">IPad by neměl v souboru vlastní možnosti použít, protože je nyní schopnostech prohlížeče</span><span class="sxs-lookup"><span data-stu-id="44757-101">IPad should not be used in custom capabilities file because it is now a browser capability</span></span>

|   |   |
|---|---|
|<span data-ttu-id="44757-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="44757-102">Details</span></span>|<span data-ttu-id="44757-103">Počínaje .NET Framework 4.5, iPad je identifikátor v výchozí prohlížeč možnosti souboru ASP.NET, proto by neměl být použít v souboru vlastní funkce</span><span class="sxs-lookup"><span data-stu-id="44757-103">Beginning in .NET Framework 4.5, iPad is an identifier in the default ASP.NET browser capabilities file, so it should not be used in a custom capabilities file</span></span>|
|<span data-ttu-id="44757-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="44757-104">Suggestion</span></span>|<span data-ttu-id="44757-105">Pokud funkce specifické pro iPad, je potřeba změnit chování iPad nastavením možnosti na předem definované brány refID &quot;IPad&quot; místo generováním nového &quot;IPad&quot; ID podle uživatelského agenta porovnávání.</span><span class="sxs-lookup"><span data-stu-id="44757-105">If iPad-specific capabilities are required, it is necessary to modify iPad behavior by setting capabilities on the pre-defined gateway refID &quot;IPad&quot; instead of by generating a new &quot;IPad&quot; ID by user agent matching.</span></span>|
|<span data-ttu-id="44757-106">Rozsah</span><span class="sxs-lookup"><span data-stu-id="44757-106">Scope</span></span>|<span data-ttu-id="44757-107">Edge</span><span class="sxs-lookup"><span data-stu-id="44757-107">Edge</span></span>|
|<span data-ttu-id="44757-108">Version</span><span class="sxs-lookup"><span data-stu-id="44757-108">Version</span></span>|<span data-ttu-id="44757-109">4.5</span><span class="sxs-lookup"><span data-stu-id="44757-109">4.5</span></span>|
|<span data-ttu-id="44757-110">Type</span><span class="sxs-lookup"><span data-stu-id="44757-110">Type</span></span>|<span data-ttu-id="44757-111">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="44757-111">Runtime</span></span>|
