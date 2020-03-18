---
title: Globalizace a lokalizace aplikací .NET
ms.date: 06/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- international applications [.NET]
- globalization [.NET], encoding
- global applications
- internationalization
- world-ready applications
- application development [.NET], globalization
- multilingual application development
ms.assetid: 9a59696b-d89b-45bd-946d-c75da4732d02
ms.openlocfilehash: eae1c38c2383d13bfb4dab83f2fe9551970b39f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120889"
---
# <a name="globalizing-and-localizing-net-applications"></a><span data-ttu-id="169da-102">Globalizace a lokalizace aplikací .NET</span><span class="sxs-lookup"><span data-stu-id="169da-102">Globalizing and localizing .NET applications</span></span>

<span data-ttu-id="169da-103">Vývoj aplikace připravené pro svět, včetně aplikace, která může být lokalizována do jednoho nebo více jazyků, zahrnuje tři kroky: globalizace, kontrola lokalizovatelnosti a lokalizace.</span><span class="sxs-lookup"><span data-stu-id="169da-103">Developing a world-ready application, including an application that can be localized into one or more languages, involves three steps: globalization, localizability review, and localization.</span></span>

[<span data-ttu-id="169da-104">Globalizace</span><span class="sxs-lookup"><span data-stu-id="169da-104">Globalization</span></span>](globalization.md)

<span data-ttu-id="169da-105">Tento krok zahrnuje návrh a kódování aplikace, která je neutrální pro jazykové prostředí a daný jazyk a která podporuje lokalizovaná uživatelská rozhraní a regionální data pro všechny uživatele aplikace.</span><span class="sxs-lookup"><span data-stu-id="169da-105">This step involves designing and coding an application that is culture-neutral and language-neutral, and that supports localized user interfaces and regional data for all users.</span></span> <span data-ttu-id="169da-106">Patří sem proces vytvoření návrhu a rozhodnutí z oblasti programování, která nejsou založena na jazykových předpokladech.</span><span class="sxs-lookup"><span data-stu-id="169da-106">It involves making design and programming decisions that are not based on culture-specific assumptions.</span></span> <span data-ttu-id="169da-107">Zatímco globalizovaná aplikace není lokalizována, je i přesto navržena a napsána tak, aby bylo možné ji poměrně snadno následně lokalizovat do jednoho nebo více jazyků.</span><span class="sxs-lookup"><span data-stu-id="169da-107">While a globalized application is not localized, it nevertheless is designed and written so that it can be subsequently localized into one or more languages with relative ease.</span></span>

[<span data-ttu-id="169da-108">Revize lokalizovatelnosti</span><span class="sxs-lookup"><span data-stu-id="169da-108">Localizability review</span></span>](localizability-review.md)

<span data-ttu-id="169da-109">Tento krok zahrnuje revizi kódu a návrhu aplikace a zajišťuje, aby bylo možné ji snadno lokalizovat, identifikovat potenciální problémy lokalizace a ověřit, zda je spustitelný kód aplikace oddělen od prostředků.</span><span class="sxs-lookup"><span data-stu-id="169da-109">This step involves reviewing an application's code and design to ensure that it can be localized easily and to identify potential roadblocks for localization, and verifying that the application's executable code is separated from its resources.</span></span> <span data-ttu-id="169da-110">Pokud fáze globalizace byla účinná, přezkoumání lokalizovatelnosti potvrdí návrh a kódování provedené během globalizace.</span><span class="sxs-lookup"><span data-stu-id="169da-110">If the globalization stage was effective, the localizability review will confirm the design and coding choices made during globalization.</span></span> <span data-ttu-id="169da-111">Fáze lokalizovatelnosti může rovněž určit všechny zbývající problémy tak, aby zdrojový kód aplikace nemusel být změněn během fáze lokalizace.</span><span class="sxs-lookup"><span data-stu-id="169da-111">The localizability stage may also identify any remaining issues so that an application's source code doesn't have to be modified during the localization stage.</span></span>

[<span data-ttu-id="169da-112">Lokalizace</span><span class="sxs-lookup"><span data-stu-id="169da-112">Localization</span></span>](localization.md)

<span data-ttu-id="169da-113">Tento krok spočívá v přizpůsobení aplikace pro specifické jazykové verze nebo regiony.</span><span class="sxs-lookup"><span data-stu-id="169da-113">This step involves customizing an application for specific cultures or regions.</span></span> <span data-ttu-id="169da-114">Pokud byly kroky globalizace a lokalizovatelnosti provedeny správně, lokalizace sestává především z překladu uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="169da-114">If the globalization and localizability steps have been performed correctly, localization consists primarily of translating the user interface.</span></span>

<span data-ttu-id="169da-115">Následující tři kroky přináší dvě výhody:</span><span class="sxs-lookup"><span data-stu-id="169da-115">Following these three steps provides two advantages:</span></span>

- <span data-ttu-id="169da-116">Umožní vám vyhnout se zpětnému pozměnění aplikace, která byla navržena pro podporu jediné jazykové verze, například americké angličtiny, aby podporovala další jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="169da-116">It frees you from having to retrofit an application that is designed to support a single culture, such as U.S. English, to support additional cultures.</span></span>

- <span data-ttu-id="169da-117">Výsledkem jsou lokalizované aplikace, které jsou více stabilní a méně chybové.</span><span class="sxs-lookup"><span data-stu-id="169da-117">It results in localized applications that are more stable and have fewer bugs.</span></span>

<span data-ttu-id="169da-118">.NET poskytuje rozsáhlou podporu pro vývoj aplikací připravených pro svět a lokalizovaných aplikací.</span><span class="sxs-lookup"><span data-stu-id="169da-118">.NET provides extensive support for the development of world-ready and localized applications.</span></span> <span data-ttu-id="169da-119">Zejména mnoho členů typu v knihovně třídy .NET pomáhá globalizaci vrácením hodnot, které odrážejí konvence jazykové verze aktuálního uživatele nebo zadané jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="169da-119">In particular, many type members in the .NET class library aid globalization by returning values that reflect the conventions of either the current user's culture or a specified culture.</span></span> <span data-ttu-id="169da-120">Rozhraní .NET také podporuje satelitní sestavení, která usnadňují proces lokalizace aplikace.</span><span class="sxs-lookup"><span data-stu-id="169da-120">Also, .NET supports satellite assemblies, which facilitate the process of localizing an application.</span></span>

<span data-ttu-id="169da-121">Další informace naleznete v [dokumentaci globalizace](/globalization/).</span><span class="sxs-lookup"><span data-stu-id="169da-121">For additional information, see the [Globalization documentation](/globalization/).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="169da-122">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="169da-122">In this section</span></span>

[<span data-ttu-id="169da-123">Globalizace</span><span class="sxs-lookup"><span data-stu-id="169da-123">Globalization</span></span>](globalization.md)

<span data-ttu-id="169da-124">Tento článek popisuje první fázi vytváření globalizované aplikace, včetně návrhu a kódování aplikace, která je nezávislá na jazykové verzi a jazyce.</span><span class="sxs-lookup"><span data-stu-id="169da-124">Discusses the first stage of creating a world-ready application, which involves designing and coding an application that is culture-neutral and language-neutral.</span></span>

[<span data-ttu-id="169da-125">Revize lokalizovatelnosti</span><span class="sxs-lookup"><span data-stu-id="169da-125">Localizability review</span></span>](localizability-review.md)

<span data-ttu-id="169da-126">Tento článek popisuje vytvoření lokalizované aplikace, včetně identifikace možných potenciálních problémů při lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="169da-126">Discusses the second stage of creating a localized application, which involves identifying potential roadblocks to localization.</span></span>

[<span data-ttu-id="169da-127">Lokalizace</span><span class="sxs-lookup"><span data-stu-id="169da-127">Localization</span></span>](localization.md)

<span data-ttu-id="169da-128">Tento článek popisuje závěrečnou fázi vytvoření lokalizované aplikace, která spočívá v přizpůsobení uživatelského rozhraní pro konkrétní oblasti nebo jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="169da-128">Discusses the final stage of creating a localized application, which involves customizing an application's user interface for specific regions or cultures.</span></span>

[<span data-ttu-id="169da-129">Řetězcové operace nezávislé na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="169da-129">Culture-insensitive string operations</span></span>](culture-insensitive-string-operations.md)

<span data-ttu-id="169da-130">Popisuje, jak používat metody a třídy .NET, které jsou ve výchozím nastavení citlivé na jazykovou verzi, aby získaly výsledky necitlivé na jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="169da-130">Describes how to use .NET methods and classes that are culture-sensitive by default to obtain culture-insensitive results.</span></span>

[<span data-ttu-id="169da-131">Osvědčené postupy pro vývoj aplikací připravených pro svět</span><span class="sxs-lookup"><span data-stu-id="169da-131">Best practices for developing world-ready applications</span></span>](best-practices-for-developing-world-ready-apps.md)

<span data-ttu-id="169da-132">Popisuje doporučené postupy pro globalizaci, lokalizaci a vývoj globalizovaných aplikací technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="169da-132">Describes the best practices to follow for globalization, localization, and developing world-ready ASP.NET applications.</span></span>

## <a name="reference"></a><span data-ttu-id="169da-133">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="169da-133">Reference</span></span>

- <span data-ttu-id="169da-134"><xref:System.Globalization?displayProperty=nameWithType>Namespace</span><span class="sxs-lookup"><span data-stu-id="169da-134"><xref:System.Globalization?displayProperty=nameWithType> namespace</span></span>

   <span data-ttu-id="169da-135">Obsahuje třídy, které definují informace týkající se jazykové verze, jako je jazyk, země a oblast, používané kalendáře, vzory formátu data, měny a čísel a pořadí řazení řetězců.</span><span class="sxs-lookup"><span data-stu-id="169da-135">Contains classes that define culture-related information, including the language, the country/region, the calendars in use, the format patterns for dates, currency, and numbers, and the sort order for strings.</span></span>

- <span data-ttu-id="169da-136"><xref:System.Resources>Namespace</span><span class="sxs-lookup"><span data-stu-id="169da-136"><xref:System.Resources> namespace</span></span>

   <span data-ttu-id="169da-137">Obsahuje třídy pro vytváření, manipulaci a používání prostředků.</span><span class="sxs-lookup"><span data-stu-id="169da-137">Provides classes for creating, manipulating, and using resources.</span></span>

- <span data-ttu-id="169da-138"><xref:System.Text>Namespace</span><span class="sxs-lookup"><span data-stu-id="169da-138"><xref:System.Text> namespace</span></span>

   <span data-ttu-id="169da-139">Obsahuje třídy představující kódování znaků ASCII, ANSI, Unicode a další.</span><span class="sxs-lookup"><span data-stu-id="169da-139">Contains classes representing ASCII, ANSI, Unicode, and other character encodings.</span></span>

- [<span data-ttu-id="169da-140">Resgen.exe (generátor zdrojových souborů)</span><span class="sxs-lookup"><span data-stu-id="169da-140">Resgen.exe (Resource File Generator)</span></span>](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)

   <span data-ttu-id="169da-141">Popisuje způsob použití Resgen.exe pro převedení souborů TXT a souborů prostředků založených na formátu XML (RESX) na binární soubory .resources modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="169da-141">Describes how to use Resgen.exe to convert .txt files and XML-based resource format (.resx) files to common language runtime binary .resources files.</span></span>

- [<span data-ttu-id="169da-142">Winres.exe (editor prostředků Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="169da-142">Winres.exe (Windows Forms Resource Editor)</span></span>](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)

   <span data-ttu-id="169da-143">Popisuje způsob lokalizace formulářů Windows Forms pomocí nástroje Winres.exe.</span><span class="sxs-lookup"><span data-stu-id="169da-143">Describes how to use Winres.exe to localize Windows Forms forms.</span></span>
