---
title: Revize lokalizovatelnosti
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- world-ready applications, localizability
- application development [.NET Framework], localization
- localizability [.NET Framework]
- international applications [.NET Framework], localizability
- globalization [.NET Framework], localizability
- culture, localizability
- localization [.NET Framework], localizability
- global applications, localizability
- localizing resources
ms.assetid: 3aee2fbb-de47-4e37-8fe4-ddebb9719247
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1907841694cde82cebada4a9e73b8ce703208611
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576126"
---
# <a name="localizability-review"></a><span data-ttu-id="df09f-102">Revize lokalizovatelnosti</span><span class="sxs-lookup"><span data-stu-id="df09f-102">Localizability Review</span></span>
<span data-ttu-id="df09f-103">Revize lokalizovatelnosti je přechodný krok pro vývoj aplikací připravených.</span><span class="sxs-lookup"><span data-stu-id="df09f-103">The localizability review is an intermediate step in the development of a world-ready application.</span></span> <span data-ttu-id="df09f-104">Ověří, že globalizovaná aplikace je připravena k lokalizaci a identifikuje kód, nebo všechny aspekty uživatelského rozhraní, které vyžadují zvláštní zpracování.</span><span class="sxs-lookup"><span data-stu-id="df09f-104">It verifies that a globalized application is ready for localization and identifies any code or any aspects of the user interface that require special handling.</span></span> <span data-ttu-id="df09f-105">Tento krok také pomáhá zajistit, že proces lokalizace nezavedou žádné funkční vady do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="df09f-105">This step also helps ensure that the localization process will not introduce any functional defects into your application.</span></span> <span data-ttu-id="df09f-106">Pokud byla vyřešili všechny problémy, které jsou vydané revize lokalizovatelnosti, je aplikace připravená pro lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="df09f-106">When all the issues raised by the localizability review have been addressed, your application is ready for localization.</span></span> <span data-ttu-id="df09f-107">Pokud revize lokalizovatelnosti důkladné, by neměl mít k úpravě jakékoli zdrojového kódu během procesu lokalizace.</span><span class="sxs-lookup"><span data-stu-id="df09f-107">If the localizability review is thorough, you should not have to modify any source code during the localization process.</span></span>  
  
 <span data-ttu-id="df09f-108">Revize lokalizovatelnosti se skládá z následujících tří kontroly:</span><span class="sxs-lookup"><span data-stu-id="df09f-108">The localizability review consists of the following three checks:</span></span>  
  
-   [<span data-ttu-id="df09f-109">Jsou implementované doporučení globalizace?</span><span class="sxs-lookup"><span data-stu-id="df09f-109">Are the globalization recommendations implemented?</span></span>](#global)  
  
-   [<span data-ttu-id="df09f-110">Jazykové funkce zpracovává správně?</span><span class="sxs-lookup"><span data-stu-id="df09f-110">Are culture-sensitive features handled correctly?</span></span>](#culture)  
  
-   [<span data-ttu-id="df09f-111">Jste otestovali vaší aplikace pomocí mezinárodní dat?</span><span class="sxs-lookup"><span data-stu-id="df09f-111">Have you tested your application with international data?</span></span>](#test)  
  
<a name="global"></a>   
## <a name="implementing-globalization-recommendations"></a><span data-ttu-id="df09f-112">Implementace doporučení pro globalizaci</span><span class="sxs-lookup"><span data-stu-id="df09f-112">Implementing globalization recommendations</span></span>  
 <span data-ttu-id="df09f-113">Pokud jste vytvořili a vyvinutá vaší aplikace pomocí na lokalizaci, a pokud jste postupovali podle doporučení popsaných v [globalizace](../../../docs/standard/globalization-localization/globalization.md) článku revize lokalizovatelnosti do značné míry budou kontrolou kvality .</span><span class="sxs-lookup"><span data-stu-id="df09f-113">If you have designed and developed your application with localization in mind, and if you have followed the recommendations discussed in the [Globalization](../../../docs/standard/globalization-localization/globalization.md) article, the localizability review will largely be a quality assurance pass.</span></span> <span data-ttu-id="df09f-114">V opačném během této fáze je vhodné zkontrolovat a doporučení pro implementaci [globalizace](../../../docs/standard/globalization-localization/globalization.md)a opravte chyby ve zdrojovém kódu, které zabraňují lokalizace.</span><span class="sxs-lookup"><span data-stu-id="df09f-114">Otherwise, during this stage you should review and implement the recommendations for [globalization](../../../docs/standard/globalization-localization/globalization.md), and fix the errors in source code that prevent localization.</span></span>  
  
<a name="culture"></a>   
## <a name="handling-culture-sensitive-features"></a><span data-ttu-id="df09f-115">Zpracování funkcí závislých na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="df09f-115">Handling culture-sensitive features</span></span>  
 <span data-ttu-id="df09f-116">Rozhraní .NET Framework neposkytuje programové podpory v různých oblastech, které jsou závislé na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="df09f-116">The .NET Framework does not provide programmatic support in a number of areas that vary widely by culture.</span></span> <span data-ttu-id="df09f-117">Ve většině případů budete muset psát vlastní kód pro zpracování oblastech funkce takto:</span><span class="sxs-lookup"><span data-stu-id="df09f-117">In most cases, you have to write custom code to handle feature areas like the following:</span></span>  
  
-   <span data-ttu-id="df09f-118">Adresy.</span><span class="sxs-lookup"><span data-stu-id="df09f-118">Addresses.</span></span>  
  
-   <span data-ttu-id="df09f-119">Telefonních čísel.</span><span class="sxs-lookup"><span data-stu-id="df09f-119">Telephone numbers.</span></span>  
  
-   <span data-ttu-id="df09f-120">Formáty papíru.</span><span class="sxs-lookup"><span data-stu-id="df09f-120">Paper sizes.</span></span>  
  
-   <span data-ttu-id="df09f-121">Jednotky měření, délky, váhu, oblasti, svazku a teploty.</span><span class="sxs-lookup"><span data-stu-id="df09f-121">Units of measure used for lengths, weights, area, volume, and temperatures.</span></span> <span data-ttu-id="df09f-122">Přestože rozhraní .NET Framework nenabízí integrovanou podporu pro převod mezi měrné jednotky, můžete použít <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> vlastnosti k určení, jestli konkrétní zemi či oblasti, používá metrika systému, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="df09f-122">Although the .NET Framework does not offer built-in support for converting between units of measure, you can use the <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> property to determine whether a particular country or region uses the metric system, as the following example illustrates.</span></span>  
  
     [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
     [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]  
  
<a name="test"></a>   
## <a name="testing-your-application"></a><span data-ttu-id="df09f-123">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="df09f-123">Testing your application</span></span>  
 <span data-ttu-id="df09f-124">Předtím, než je lokalizovat aplikaci, byste měli otestovat pomocí mezinárodní data na mezinárodní verze operačního systému.</span><span class="sxs-lookup"><span data-stu-id="df09f-124">Before you localize your application, you should test it by using international data on international versions of the operating system.</span></span> <span data-ttu-id="df09f-125">I když většina uživatelského rozhraní pro nebude v tomto okamžiku lokalizované, bude možné ke zjišťování problémů například následující:</span><span class="sxs-lookup"><span data-stu-id="df09f-125">Although most of the user interface will not be localized at this point, you will be able to detect problems such as the following:</span></span>  
  
-   <span data-ttu-id="df09f-126">Serializovaná data, která není správně deserializovat mezi verzemi operačního systému.</span><span class="sxs-lookup"><span data-stu-id="df09f-126">Serialized data that does not deserialize correctly across operating system versions.</span></span>  
  
-   <span data-ttu-id="df09f-127">Číselná data, která nemusí odpovídat konvence aktuální jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="df09f-127">Numeric data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="df09f-128">Například může zobrazit čísla s oddělovače nesprávné skupin, oddělovače desetinných míst nebo symboly měny.</span><span class="sxs-lookup"><span data-stu-id="df09f-128">For example, numbers may be displayed with inaccurate group separators, decimal separators, or currency symbols.</span></span>  
  
-   <span data-ttu-id="df09f-129">Datum a čas data, která nemusí odpovídat konvence aktuální jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="df09f-129">Date and time data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="df09f-130">Například čísla, která představují měsíce a dne se mohou objevit v nesprávném pořadí, oddělovače dat může být nesprávný nebo může být nesprávné informace o časovém pásmu.</span><span class="sxs-lookup"><span data-stu-id="df09f-130">For example, numbers that represent the month and day may appear in the wrong order, date separators may be incorrect, or time zone information may be incorrect.</span></span>  
  
-   <span data-ttu-id="df09f-131">Prostředky, které nelze nalézt, protože nebyly identifikovány výchozí jazykovou verzi pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="df09f-131">Resources that cannot be found because you have not identified a default culture for your application.</span></span>  
  
-   <span data-ttu-id="df09f-132">Řetězce, které se zobrazují v neobvyklou pořadí pro konkrétní jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="df09f-132">Strings that are displayed in an unusual order for the specific culture.</span></span>  
  
-   <span data-ttu-id="df09f-133">Řetězec porovnání nebo porovnání rovnosti, které vracejí neočekávané výsledky.</span><span class="sxs-lookup"><span data-stu-id="df09f-133">String comparisons or comparisons for equality that return unexpected results.</span></span>  
  
 <span data-ttu-id="df09f-134">Pokud jste postupovali podle doporučení globalizace při vývoji aplikace, zpracovává jazykové funkce správně a identifikovat a řešit problémy lokalizace, které vznikly během testování, můžete přejít k dalšímu kroku, [Lokalizace](../../../docs/standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="df09f-134">If you've followed the globalization recommendations when developing your application, handled culture-sensitive features correctly, and identified and addressed the localization issues that arose during testing, you can proceed to the next step, [Localization](../../../docs/standard/globalization-localization/localization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df09f-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="df09f-135">See Also</span></span>  
 [<span data-ttu-id="df09f-136">Globalizace a lokalizace</span><span class="sxs-lookup"><span data-stu-id="df09f-136">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)  
 [<span data-ttu-id="df09f-137">Lokalizace</span><span class="sxs-lookup"><span data-stu-id="df09f-137">Localization</span></span>](../../../docs/standard/globalization-localization/localization.md)  
 [<span data-ttu-id="df09f-138">Globalizace</span><span class="sxs-lookup"><span data-stu-id="df09f-138">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)  
 [<span data-ttu-id="df09f-139">Prostředky v desktopových aplikacích</span><span class="sxs-lookup"><span data-stu-id="df09f-139">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
