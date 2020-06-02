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
ms.openlocfilehash: 10d07a02a7ff744a87b920fd97df24b076c22cc3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288287"
---
# <a name="globalizing-and-localizing-net-applications"></a><span data-ttu-id="ef294-102">Globalizace a lokalizace aplikací .NET</span><span class="sxs-lookup"><span data-stu-id="ef294-102">Globalizing and localizing .NET applications</span></span>

<span data-ttu-id="ef294-103">Vývoj aplikace připravené pro použití ve světě, včetně aplikace, která může být lokalizována do jednoho nebo více jazyků, zahrnuje tři kroky: globalizace, přezkoumání lokalizovatelnosti a lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="ef294-103">Developing a world-ready application, including an application that can be localized into one or more languages, involves three steps: globalization, localizability review, and localization.</span></span>

[<span data-ttu-id="ef294-104">Globalizace</span><span class="sxs-lookup"><span data-stu-id="ef294-104">Globalization</span></span>](globalization.md)

<span data-ttu-id="ef294-105">Tento krok zahrnuje návrh a kódování aplikace, která je neutrální pro jazykové prostředí a daný jazyk a která podporuje lokalizovaná uživatelská rozhraní a regionální data pro všechny uživatele aplikace.</span><span class="sxs-lookup"><span data-stu-id="ef294-105">This step involves designing and coding an application that is culture-neutral and language-neutral, and that supports localized user interfaces and regional data for all users.</span></span> <span data-ttu-id="ef294-106">Patří sem proces vytvoření návrhu a rozhodnutí z oblasti programování, která nejsou založena na jazykových předpokladech.</span><span class="sxs-lookup"><span data-stu-id="ef294-106">It involves making design and programming decisions that are not based on culture-specific assumptions.</span></span> <span data-ttu-id="ef294-107">Zatímco globalizovaná aplikace není lokalizována, je i přesto navržena a napsána tak, aby bylo možné ji poměrně snadno následně lokalizovat do jednoho nebo více jazyků.</span><span class="sxs-lookup"><span data-stu-id="ef294-107">While a globalized application is not localized, it nevertheless is designed and written so that it can be subsequently localized into one or more languages with relative ease.</span></span>

[<span data-ttu-id="ef294-108">Revize lokalizovatelnosti</span><span class="sxs-lookup"><span data-stu-id="ef294-108">Localizability review</span></span>](localizability-review.md)

<span data-ttu-id="ef294-109">Tento krok zahrnuje revizi kódu a návrhu aplikace a zajišťuje, aby bylo možné ji snadno lokalizovat, identifikovat potenciální problémy lokalizace a ověřit, zda je spustitelný kód aplikace oddělen od prostředků.</span><span class="sxs-lookup"><span data-stu-id="ef294-109">This step involves reviewing an application's code and design to ensure that it can be localized easily and to identify potential roadblocks for localization, and verifying that the application's executable code is separated from its resources.</span></span> <span data-ttu-id="ef294-110">Pokud fáze globalizace byla účinná, přezkoumání lokalizovatelnosti potvrdí návrh a kódování provedené během globalizace.</span><span class="sxs-lookup"><span data-stu-id="ef294-110">If the globalization stage was effective, the localizability review will confirm the design and coding choices made during globalization.</span></span> <span data-ttu-id="ef294-111">Fáze lokalizovatelnosti může rovněž určit všechny zbývající problémy tak, aby zdrojový kód aplikace nemusel být změněn během fáze lokalizace.</span><span class="sxs-lookup"><span data-stu-id="ef294-111">The localizability stage may also identify any remaining issues so that an application's source code doesn't have to be modified during the localization stage.</span></span>

[<span data-ttu-id="ef294-112">Lokalizace</span><span class="sxs-lookup"><span data-stu-id="ef294-112">Localization</span></span>](localization.md)

<span data-ttu-id="ef294-113">Tento krok spočívá v přizpůsobení aplikace pro specifické jazykové verze nebo regiony.</span><span class="sxs-lookup"><span data-stu-id="ef294-113">This step involves customizing an application for specific cultures or regions.</span></span> <span data-ttu-id="ef294-114">Pokud byly kroky globalizace a lokalizovatelnosti provedeny správně, lokalizace sestává především z překladu uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ef294-114">If the globalization and localizability steps have been performed correctly, localization consists primarily of translating the user interface.</span></span>

<span data-ttu-id="ef294-115">Následující tři kroky přináší dvě výhody:</span><span class="sxs-lookup"><span data-stu-id="ef294-115">Following these three steps provides two advantages:</span></span>

- <span data-ttu-id="ef294-116">Umožní vám vyhnout se zpětnému pozměnění aplikace, která byla navržena pro podporu jediné jazykové verze, například americké angličtiny, aby podporovala další jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="ef294-116">It frees you from having to retrofit an application that is designed to support a single culture, such as U.S. English, to support additional cultures.</span></span>

- <span data-ttu-id="ef294-117">Výsledkem jsou lokalizované aplikace, které jsou více stabilní a méně chybové.</span><span class="sxs-lookup"><span data-stu-id="ef294-117">It results in localized applications that are more stable and have fewer bugs.</span></span>

<span data-ttu-id="ef294-118">.NET poskytuje rozsáhlou podporu pro vývoj aplikací připravených pro použití ve světě.</span><span class="sxs-lookup"><span data-stu-id="ef294-118">.NET provides extensive support for the development of world-ready and localized applications.</span></span> <span data-ttu-id="ef294-119">Konkrétně mnoho členů typu v knihovně tříd .NET podporuje globalizaci vrácením hodnot, které odráží konvence buď aktuální jazykové verze uživatele, nebo zadané jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="ef294-119">In particular, many type members in the .NET class library aid globalization by returning values that reflect the conventions of either the current user's culture or a specified culture.</span></span> <span data-ttu-id="ef294-120">Rozhraní .NET také podporuje satelitní sestavení, která usnadňují proces lokalizace aplikace.</span><span class="sxs-lookup"><span data-stu-id="ef294-120">Also, .NET supports satellite assemblies, which facilitate the process of localizing an application.</span></span>

<span data-ttu-id="ef294-121">Další informace naleznete v dokumentaci k [globalizaci](/globalization/).</span><span class="sxs-lookup"><span data-stu-id="ef294-121">For additional information, see the [Globalization documentation](/globalization/).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ef294-122">V této části</span><span class="sxs-lookup"><span data-stu-id="ef294-122">In this section</span></span>

[<span data-ttu-id="ef294-123">Globalizace</span><span class="sxs-lookup"><span data-stu-id="ef294-123">Globalization</span></span>](globalization.md)

<span data-ttu-id="ef294-124">Tento článek popisuje první fázi vytváření globalizované aplikace, včetně návrhu a kódování aplikace, která je nezávislá na jazykové verzi a jazyce.</span><span class="sxs-lookup"><span data-stu-id="ef294-124">Discusses the first stage of creating a world-ready application, which involves designing and coding an application that is culture-neutral and language-neutral.</span></span>

[<span data-ttu-id="ef294-125">Rozhraní .NET globalizace a ICU</span><span class="sxs-lookup"><span data-stu-id="ef294-125">.NET globalization and ICU</span></span>](globalization-icu.md)

<span data-ttu-id="ef294-126">Popisuje, jak globalizace rozhraní .NET používá [mezinárodní komponenty pro kódování Unicode (ICU)](http://site.icu-project.org/home).</span><span class="sxs-lookup"><span data-stu-id="ef294-126">Describes how .NET globalization uses [International Components for Unicode (ICU)](http://site.icu-project.org/home).</span></span>

[<span data-ttu-id="ef294-127">Revize lokalizovatelnosti</span><span class="sxs-lookup"><span data-stu-id="ef294-127">Localizability review</span></span>](localizability-review.md)

<span data-ttu-id="ef294-128">Tento článek popisuje vytvoření lokalizované aplikace, včetně identifikace možných potenciálních problémů při lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="ef294-128">Discusses the second stage of creating a localized application, which involves identifying potential roadblocks to localization.</span></span>

[<span data-ttu-id="ef294-129">Lokalizace</span><span class="sxs-lookup"><span data-stu-id="ef294-129">Localization</span></span>](localization.md)

<span data-ttu-id="ef294-130">Tento článek popisuje závěrečnou fázi vytvoření lokalizované aplikace, která spočívá v přizpůsobení uživatelského rozhraní pro konkrétní oblasti nebo jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="ef294-130">Discusses the final stage of creating a localized application, which involves customizing an application's user interface for specific regions or cultures.</span></span>

[<span data-ttu-id="ef294-131">Řetězcové operace nezávislé na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="ef294-131">Culture-insensitive string operations</span></span>](culture-insensitive-string-operations.md)

<span data-ttu-id="ef294-132">Popisuje, jak používat metody a třídy .NET, které jsou ve výchozím nastavení závislé na jazykové verzi pro získání výsledků nezávislých na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="ef294-132">Describes how to use .NET methods and classes that are culture-sensitive by default to obtain culture-insensitive results.</span></span>

[<span data-ttu-id="ef294-133">Osvědčené postupy pro vývoj aplikací připravených pro použití ve světě</span><span class="sxs-lookup"><span data-stu-id="ef294-133">Best practices for developing world-ready applications</span></span>](best-practices-for-developing-world-ready-apps.md)

<span data-ttu-id="ef294-134">Popisuje doporučené postupy pro globalizaci, lokalizaci a vývoj globalizovaných aplikací technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ef294-134">Describes the best practices to follow for globalization, localization, and developing world-ready ASP.NET applications.</span></span>

## <a name="reference"></a><span data-ttu-id="ef294-135">Odkaz</span><span class="sxs-lookup"><span data-stu-id="ef294-135">Reference</span></span>

- <span data-ttu-id="ef294-136"><xref:System.Globalization?displayProperty=nameWithType>hosting</span><span class="sxs-lookup"><span data-stu-id="ef294-136"><xref:System.Globalization?displayProperty=nameWithType> namespace</span></span>

   <span data-ttu-id="ef294-137">Obsahuje třídy, které definují informace týkající se jazykové verze, jako je jazyk, země a oblast, používané kalendáře, vzory formátu data, měny a čísel a pořadí řazení řetězců.</span><span class="sxs-lookup"><span data-stu-id="ef294-137">Contains classes that define culture-related information, including the language, the country/region, the calendars in use, the format patterns for dates, currency, and numbers, and the sort order for strings.</span></span>

- <span data-ttu-id="ef294-138"><xref:System.Resources>hosting</span><span class="sxs-lookup"><span data-stu-id="ef294-138"><xref:System.Resources> namespace</span></span>

   <span data-ttu-id="ef294-139">Obsahuje třídy pro vytváření, manipulaci a používání prostředků.</span><span class="sxs-lookup"><span data-stu-id="ef294-139">Provides classes for creating, manipulating, and using resources.</span></span>

- <span data-ttu-id="ef294-140"><xref:System.Text>hosting</span><span class="sxs-lookup"><span data-stu-id="ef294-140"><xref:System.Text> namespace</span></span>

   <span data-ttu-id="ef294-141">Obsahuje třídy představující kódování znaků ASCII, ANSI, Unicode a další.</span><span class="sxs-lookup"><span data-stu-id="ef294-141">Contains classes representing ASCII, ANSI, Unicode, and other character encodings.</span></span>

- [<span data-ttu-id="ef294-142">Resgen. exe (generátor zdrojových souborů)</span><span class="sxs-lookup"><span data-stu-id="ef294-142">Resgen.exe (Resource File Generator)</span></span>](../../framework/tools/resgen-exe-resource-file-generator.md)

   <span data-ttu-id="ef294-143">Popisuje způsob použití Resgen.exe pro převedení souborů TXT a souborů prostředků založených na formátu XML (RESX) na binární soubory .resources modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="ef294-143">Describes how to use Resgen.exe to convert .txt files and XML-based resource format (.resx) files to common language runtime binary .resources files.</span></span>

- [<span data-ttu-id="ef294-144">Winres. exe (model Windows Forms editor prostředků)</span><span class="sxs-lookup"><span data-stu-id="ef294-144">Winres.exe (Windows Forms Resource Editor)</span></span>](../../framework/tools/winres-exe-windows-forms-resource-editor.md)

   <span data-ttu-id="ef294-145">Popisuje způsob lokalizace formulářů Windows Forms pomocí nástroje Winres.exe.</span><span class="sxs-lookup"><span data-stu-id="ef294-145">Describes how to use Winres.exe to localize Windows Forms forms.</span></span>
