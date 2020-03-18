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
ms.openlocfilehash: b286bdd2c5d7b03a0a2b5f94478e252da6cd0ae2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120852"
---
# <a name="localizability-review"></a><span data-ttu-id="92307-102">Revize lokalizovatelnosti</span><span class="sxs-lookup"><span data-stu-id="92307-102">Localizability review</span></span>

<span data-ttu-id="92307-103">Kontrola lokalizovatelnosti je mezikrokem ve vývoji aplikace připravené pro svět.</span><span class="sxs-lookup"><span data-stu-id="92307-103">The localizability review is an intermediate step in the development of a world-ready application.</span></span> <span data-ttu-id="92307-104">Ověří, že globalizovaná aplikace je připravena k lokalizaci a identifikuje jakýkoli kód nebo jakékoli aspekty uživatelského rozhraní, které vyžadují zvláštní zpracování.</span><span class="sxs-lookup"><span data-stu-id="92307-104">It verifies that a globalized application is ready for localization and identifies any code or any aspects of the user interface that require special handling.</span></span> <span data-ttu-id="92307-105">Tento krok také pomáhá zajistit, že proces lokalizace nezavede do aplikace žádné funkční vady.</span><span class="sxs-lookup"><span data-stu-id="92307-105">This step also helps ensure that the localization process will not introduce any functional defects into your application.</span></span> <span data-ttu-id="92307-106">Pokud byly vyřešeny všechny problémy vyvolané kontrolou lokalizovatelnosti, aplikace je připravena k lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="92307-106">When all the issues raised by the localizability review have been addressed, your application is ready for localization.</span></span> <span data-ttu-id="92307-107">Pokud je kontrola lokalizovatelnosti důkladná, neměli byste během procesu lokalizace upravovat žádný zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="92307-107">If the localizability review is thorough, you should not have to modify any source code during the localization process.</span></span>

<span data-ttu-id="92307-108">Přezkum lokalizovatelnosti se skládá z těchto tří kontrol:</span><span class="sxs-lookup"><span data-stu-id="92307-108">The localizability review consists of the following three checks:</span></span>

- [<span data-ttu-id="92307-109">Jsou doporučení globalizace implementována?</span><span class="sxs-lookup"><span data-stu-id="92307-109">Are the globalization recommendations implemented?</span></span>](#global)

- [<span data-ttu-id="92307-110">Jsou funkce citlivé na jazykovou verzi správně zpracovány?</span><span class="sxs-lookup"><span data-stu-id="92307-110">Are culture-sensitive features handled correctly?</span></span>](#culture)

- [<span data-ttu-id="92307-111">Testovali jste svou aplikaci s mezinárodními daty?</span><span class="sxs-lookup"><span data-stu-id="92307-111">Have you tested your application with international data?</span></span>](#test)

<a name="global"></a>
## <a name="implement-globalization-recommendations"></a><span data-ttu-id="92307-112">Implementace doporučení globalizace</span><span class="sxs-lookup"><span data-stu-id="92307-112">Implement globalization recommendations</span></span>

<span data-ttu-id="92307-113">Pokud jste navrhli a vyvinuli aplikaci s ohledem na lokalizaci a pokud jste postupovali podle doporučení popsaných v článku [globalizace,](../../../docs/standard/globalization-localization/globalization.md) bude kontrola lokalizovatelnosti do značné míry průchodem zajištění kvality.</span><span class="sxs-lookup"><span data-stu-id="92307-113">If you have designed and developed your application with localization in mind, and if you have followed the recommendations discussed in the [Globalization](../../../docs/standard/globalization-localization/globalization.md) article, the localizability review will largely be a quality assurance pass.</span></span> <span data-ttu-id="92307-114">V opačném případě byste v této fázi měli zkontrolovat a implementovat doporučení pro [globalizaci](../../../docs/standard/globalization-localization/globalization.md) a opravit chyby ve zdrojovém kódu, které brání lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="92307-114">Otherwise, during this stage you should review and implement the recommendations for [globalization](../../../docs/standard/globalization-localization/globalization.md) and fix the errors in source code that prevent localization.</span></span>

<a name="culture"></a>
## <a name="handle-culture-sensitive-features"></a><span data-ttu-id="92307-115">Zpracování funkcí citlivých na jazykovou verzi</span><span class="sxs-lookup"><span data-stu-id="92307-115">Handle culture-sensitive features</span></span>

<span data-ttu-id="92307-116">Rozhraní .NET neposkytuje programovou podporu v řadě oblastí, které se značně liší podle jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="92307-116">.NET does not provide programmatic support in a number of areas that vary widely by culture.</span></span> <span data-ttu-id="92307-117">Ve většině případů je třeba napsat vlastní kód pro zpracování oblastí funkcí, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="92307-117">In most cases, you have to write custom code to handle feature areas like the following:</span></span>

- <span data-ttu-id="92307-118">Adresy</span><span class="sxs-lookup"><span data-stu-id="92307-118">Addresses</span></span>

- <span data-ttu-id="92307-119">Telefonní čísla</span><span class="sxs-lookup"><span data-stu-id="92307-119">Telephone numbers</span></span>

- <span data-ttu-id="92307-120">Formáty papíru</span><span class="sxs-lookup"><span data-stu-id="92307-120">Paper sizes</span></span>

- <span data-ttu-id="92307-121">Měrné jednotky používané pro délky, závaží, plochu, objem a teploty</span><span class="sxs-lookup"><span data-stu-id="92307-121">Units of measure used for lengths, weights, area, volume, and temperatures</span></span>

   <span data-ttu-id="92307-122">Přestože rozhraní .NET nenabízí integrovanou podporu pro převod mezi <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> měrnými jednotkami, můžete pomocí této vlastnosti určit, zda určitá země nebo oblast používá systém metrik, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="92307-122">Although .NET does not offer built-in support for converting between units of measure, you can use the <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> property to determine whether a particular country or region uses the metric system, as the following example illustrates.</span></span>

   [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
   [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]

<a name="test"></a>
## <a name="test-your-application"></a><span data-ttu-id="92307-123">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="92307-123">Test your application</span></span>

<span data-ttu-id="92307-124">Před lokalizací aplikace byste ji měli otestovat pomocí mezinárodních dat v mezinárodních verzích operačního systému.</span><span class="sxs-lookup"><span data-stu-id="92307-124">Before you localize your application, you should test it by using international data on international versions of the operating system.</span></span> <span data-ttu-id="92307-125">Přestože většina uživatelského rozhraní nebude v tomto okamžiku lokalizována, budete moci zjistit problémy, jako jsou následující:</span><span class="sxs-lookup"><span data-stu-id="92307-125">Although most of the user interface will not be localized at this point, you will be able to detect problems such as the following:</span></span>

- <span data-ttu-id="92307-126">Serializovaná data, která nejsou správně rekonstruována ve verzích operačního systému.</span><span class="sxs-lookup"><span data-stu-id="92307-126">Serialized data that does not deserialize correctly across operating system versions.</span></span>

- <span data-ttu-id="92307-127">Číselná data, která neodráží konvence aktuální jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="92307-127">Numeric data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="92307-128">Čísla mohou být například zobrazena s nepřesnými oddělovači skupin, oddělovači desetinných míst nebo symboly měny.</span><span class="sxs-lookup"><span data-stu-id="92307-128">For example, numbers may be displayed with inaccurate group separators, decimal separators, or currency symbols.</span></span>

- <span data-ttu-id="92307-129">Data a čas dat, která neodráží konvence aktuální jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="92307-129">Date and time data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="92307-130">Například čísla, která představují měsíc a den, se mohou zobrazit v nesprávném pořadí, oddělovače kalendářních dat mohou být nesprávné nebo informace o časovém pásmu mohou být nesprávné.</span><span class="sxs-lookup"><span data-stu-id="92307-130">For example, numbers that represent the month and day may appear in the wrong order, date separators may be incorrect, or time zone information may be incorrect.</span></span>

- <span data-ttu-id="92307-131">Prostředky, které nelze najít, protože jste neidentifikovali výchozí jazykovou verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="92307-131">Resources that cannot be found because you have not identified a default culture for your application.</span></span>

- <span data-ttu-id="92307-132">Řetězce, které jsou zobrazeny v neobvyklém pořadí pro konkrétní jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="92307-132">Strings that are displayed in an unusual order for the specific culture.</span></span>

- <span data-ttu-id="92307-133">Porovnání řetězců nebo porovnání rovnosti, které vracejí neočekávané výsledky.</span><span class="sxs-lookup"><span data-stu-id="92307-133">String comparisons or comparisons for equality that return unexpected results.</span></span>

<span data-ttu-id="92307-134">Pokud jste postupovali podle doporučení globalizace při vývoji aplikace, správně zpracovány funkce citlivé na jazykovou verzi a identifikovat a řešit problémy lokalizace, které vznikly během testování, můžete přistoupit k dalšímu kroku, [Lokalizace](../../../docs/standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="92307-134">If you've followed the globalization recommendations when developing your application, handled culture-sensitive features correctly, and identified and addressed the localization issues that arose during testing, you can proceed to the next step, [Localization](../../../docs/standard/globalization-localization/localization.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="92307-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="92307-135">See also</span></span>

- [<span data-ttu-id="92307-136">Globalizace a lokalizace</span><span class="sxs-lookup"><span data-stu-id="92307-136">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
- [<span data-ttu-id="92307-137">Lokalizace</span><span class="sxs-lookup"><span data-stu-id="92307-137">Localization</span></span>](../../../docs/standard/globalization-localization/localization.md)
- [<span data-ttu-id="92307-138">Globalizace</span><span class="sxs-lookup"><span data-stu-id="92307-138">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)
- [<span data-ttu-id="92307-139">Prostředky v aplikacích klasické pracovní plochy</span><span class="sxs-lookup"><span data-stu-id="92307-139">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
