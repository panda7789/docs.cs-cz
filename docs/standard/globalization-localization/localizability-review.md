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
ms.openlocfilehash: ef23cff2416792f13fda04dbe9beb34cbacfd7ea
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288274"
---
# <a name="localizability-review"></a><span data-ttu-id="07142-102">Revize lokalizovatelnosti</span><span class="sxs-lookup"><span data-stu-id="07142-102">Localizability review</span></span>

<span data-ttu-id="07142-103">Kontrola lokalizovatelnosti je přechodný krok vývoje aplikace připravené pro použití ve světě.</span><span class="sxs-lookup"><span data-stu-id="07142-103">The localizability review is an intermediate step in the development of a world-ready application.</span></span> <span data-ttu-id="07142-104">Ověřuje, zda je globální aplikace připravena k lokalizaci a identifikuje jakýkoli kód nebo jakékoli aspekty uživatelského rozhraní, které vyžadují zvláštní zpracování.</span><span class="sxs-lookup"><span data-stu-id="07142-104">It verifies that a globalized application is ready for localization and identifies any code or any aspects of the user interface that require special handling.</span></span> <span data-ttu-id="07142-105">Tento krok také pomáhá zajistit, že proces lokalizace nezavede do vaší aplikace žádné funkční nedostatky.</span><span class="sxs-lookup"><span data-stu-id="07142-105">This step also helps ensure that the localization process will not introduce any functional defects into your application.</span></span> <span data-ttu-id="07142-106">Když byly vyřešeny všechny problémy vyvolané přezkoumáním lokalizovatelnosti, je vaše aplikace připravená na lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="07142-106">When all the issues raised by the localizability review have been addressed, your application is ready for localization.</span></span> <span data-ttu-id="07142-107">Pokud je kontrola lokalizovatelnosti důkladná, neměli byste během procesu lokalizace upravovat žádný zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="07142-107">If the localizability review is thorough, you should not have to modify any source code during the localization process.</span></span>

<span data-ttu-id="07142-108">Kontrola lokalizovatelnosti se skládá z následujících tří kontrol:</span><span class="sxs-lookup"><span data-stu-id="07142-108">The localizability review consists of the following three checks:</span></span>

- [<span data-ttu-id="07142-109">Jsou implementovaná doporučení globalizace?</span><span class="sxs-lookup"><span data-stu-id="07142-109">Are the globalization recommendations implemented?</span></span>](#global)

- [<span data-ttu-id="07142-110">Jsou funkce závislé na jazykové verzi zpracovávány správně?</span><span class="sxs-lookup"><span data-stu-id="07142-110">Are culture-sensitive features handled correctly?</span></span>](#culture)

- [<span data-ttu-id="07142-111">Otestovali jste aplikaci s mezinárodními daty?</span><span class="sxs-lookup"><span data-stu-id="07142-111">Have you tested your application with international data?</span></span>](#test)

<a name="global"></a>
## <a name="implement-globalization-recommendations"></a><span data-ttu-id="07142-112">Implementace doporučení globalizace</span><span class="sxs-lookup"><span data-stu-id="07142-112">Implement globalization recommendations</span></span>

<span data-ttu-id="07142-113">Pokud jste aplikaci navrhli a vyvinuli s lokalizací a pokud jste postupovali s doporučeními popsanými v článku [globalizace](globalization.md) , přezkoumání lokalizovatelnosti bude převážně složitosti.</span><span class="sxs-lookup"><span data-stu-id="07142-113">If you have designed and developed your application with localization in mind, and if you have followed the recommendations discussed in the [Globalization](globalization.md) article, the localizability review will largely be a quality assurance pass.</span></span> <span data-ttu-id="07142-114">V opačném případě byste měli v průběhu této fáze zkontrolovat a implementovat doporučení pro [globalizaci](globalization.md) a opravit chyby ve zdrojovém kódu, které brání lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="07142-114">Otherwise, during this stage you should review and implement the recommendations for [globalization](globalization.md) and fix the errors in source code that prevent localization.</span></span>

<a name="culture"></a>
## <a name="handle-culture-sensitive-features"></a><span data-ttu-id="07142-115">Zpracování funkcí závislých na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="07142-115">Handle culture-sensitive features</span></span>

<span data-ttu-id="07142-116">Rozhraní .NET neposkytuje programovou podporu v řadě oblastí, které jsou široce závislé na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="07142-116">.NET does not provide programmatic support in a number of areas that vary widely by culture.</span></span> <span data-ttu-id="07142-117">Ve většině případů je třeba napsat vlastní kód, který bude zpracovávat oblasti funkcí jako následující:</span><span class="sxs-lookup"><span data-stu-id="07142-117">In most cases, you have to write custom code to handle feature areas like the following:</span></span>

- <span data-ttu-id="07142-118">Addresses (Adresy)</span><span class="sxs-lookup"><span data-stu-id="07142-118">Addresses</span></span>

- <span data-ttu-id="07142-119">Telefonní čísla</span><span class="sxs-lookup"><span data-stu-id="07142-119">Telephone numbers</span></span>

- <span data-ttu-id="07142-120">Velikosti papíru</span><span class="sxs-lookup"><span data-stu-id="07142-120">Paper sizes</span></span>

- <span data-ttu-id="07142-121">Měrné jednotky používané pro délky, váhy, oblast, hlasitost a teploty</span><span class="sxs-lookup"><span data-stu-id="07142-121">Units of measure used for lengths, weights, area, volume, and temperatures</span></span>

   <span data-ttu-id="07142-122">I když rozhraní .NET nenabízí integrovanou podporu pro převod mezi jednotkami měření, můžete použít <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> vlastnost k určení, zda konkrétní země nebo oblast používá systém metrik, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="07142-122">Although .NET does not offer built-in support for converting between units of measure, you can use the <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> property to determine whether a particular country or region uses the metric system, as the following example illustrates.</span></span>

   [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
   [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]

<a name="test"></a>
## <a name="test-your-application"></a><span data-ttu-id="07142-123">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="07142-123">Test your application</span></span>

<span data-ttu-id="07142-124">Před lokalizací aplikace byste ji měli otestovat pomocí mezinárodních dat v mezinárodní verzi operačního systému.</span><span class="sxs-lookup"><span data-stu-id="07142-124">Before you localize your application, you should test it by using international data on international versions of the operating system.</span></span> <span data-ttu-id="07142-125">I když většina uživatelského rozhraní nebude v tomto okamžiku lokalizována, budete moci detekovat následující problémy:</span><span class="sxs-lookup"><span data-stu-id="07142-125">Although most of the user interface will not be localized at this point, you will be able to detect problems such as the following:</span></span>

- <span data-ttu-id="07142-126">Serializovaná data, která nejsou v rámci verzí operačního systému správně reserializována.</span><span class="sxs-lookup"><span data-stu-id="07142-126">Serialized data that does not deserialize correctly across operating system versions.</span></span>

- <span data-ttu-id="07142-127">Číselná data, která nereflektují konvence aktuální jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="07142-127">Numeric data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="07142-128">Čísla lze například zobrazit s nepřesnými oddělovači skupin, oddělovači desetinných míst nebo symboly měny.</span><span class="sxs-lookup"><span data-stu-id="07142-128">For example, numbers may be displayed with inaccurate group separators, decimal separators, or currency symbols.</span></span>

- <span data-ttu-id="07142-129">Data a času, která nereflektují konvence aktuální jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="07142-129">Date and time data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="07142-130">Například čísla představující měsíc a den se mohou zobrazit v nesprávném pořadí, oddělovače dat mohou být nesprávné nebo informace o časovém pásmu mohou být nesprávné.</span><span class="sxs-lookup"><span data-stu-id="07142-130">For example, numbers that represent the month and day may appear in the wrong order, date separators may be incorrect, or time zone information may be incorrect.</span></span>

- <span data-ttu-id="07142-131">Prostředky, které se nenašly, protože jste pro svou aplikaci neoznačili výchozí jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="07142-131">Resources that cannot be found because you have not identified a default culture for your application.</span></span>

- <span data-ttu-id="07142-132">Řetězce, které jsou zobrazeny v neobvyklém pořadí pro konkrétní jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="07142-132">Strings that are displayed in an unusual order for the specific culture.</span></span>

- <span data-ttu-id="07142-133">Porovnávání řetězců nebo porovnání pro rovnost, které vracejí neočekávané výsledky.</span><span class="sxs-lookup"><span data-stu-id="07142-133">String comparisons or comparisons for equality that return unexpected results.</span></span>

<span data-ttu-id="07142-134">Pokud jste postupovali s doporučeními globalizace při vývoji aplikace, zpracování funkcí závislých na jazykové verzi a identifikaci a řešení problémů lokalizace, které vznikly během testování, můžete přejít k dalšímu kroku [lokalizace](localization.md).</span><span class="sxs-lookup"><span data-stu-id="07142-134">If you've followed the globalization recommendations when developing your application, handled culture-sensitive features correctly, and identified and addressed the localization issues that arose during testing, you can proceed to the next step, [Localization](localization.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="07142-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="07142-135">See also</span></span>

- [<span data-ttu-id="07142-136">Globalizace a lokalizace</span><span class="sxs-lookup"><span data-stu-id="07142-136">Globalization and Localization</span></span>](index.md)
- [<span data-ttu-id="07142-137">Lokalizace</span><span class="sxs-lookup"><span data-stu-id="07142-137">Localization</span></span>](localization.md)
- [<span data-ttu-id="07142-138">Globalizace</span><span class="sxs-lookup"><span data-stu-id="07142-138">Globalization</span></span>](globalization.md)
- [<span data-ttu-id="07142-139">Prostředky v aplikacích klasické pracovní plochy</span><span class="sxs-lookup"><span data-stu-id="07142-139">Resources in Desktop Apps</span></span>](../../framework/resources/index.md)
