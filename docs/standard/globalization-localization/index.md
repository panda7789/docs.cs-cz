---
title: "Globalizace a lokalizace aplikací .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- international applications [.NET Framework]
- globalization [.NET Framework], encoding
- global applications
- internationalization
- world-ready applications
- application development [.NET Framework], globalization
- multilingual application development
ms.assetid: 9a59696b-d89b-45bd-946d-c75da4732d02
caps.latest.revision: "42"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 63f0e001280773c55f18f0604ca93986acbb9674
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2018
---
# <a name="globalizing-and-localizing-net-framework-applications"></a><span data-ttu-id="590a1-102">Globalizace a lokalizace aplikací .NET Framework</span><span class="sxs-lookup"><span data-stu-id="590a1-102">Globalizing and Localizing .NET Framework Applications</span></span>
<span data-ttu-id="590a1-103">Vývoj [aplikací připravených](http://msdn.microsoft.com/goglobal/bb978433.aspx), včetně aplikace, která je možné lokalizovat do jednoho nebo více jazyků, zahrnuje tři kroky: globalizace, lokalizovatelnosti a lokalizace.</span><span class="sxs-lookup"><span data-stu-id="590a1-103">Developing a [world-ready application](http://msdn.microsoft.com/goglobal/bb978433.aspx), including an application that can be localized into one or more languages, involves three steps: globalization, localizability review, and localization.</span></span>  
  
 [<span data-ttu-id="590a1-104">Globalizace</span><span class="sxs-lookup"><span data-stu-id="590a1-104">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)  
 <span data-ttu-id="590a1-105">Tento krok zahrnuje návrh a kódování aplikace, která je neutrální pro jazykové prostředí a daný jazyk a která podporuje lokalizovaná uživatelská rozhraní a regionální data pro všechny uživatele aplikace.</span><span class="sxs-lookup"><span data-stu-id="590a1-105">This step involves designing and coding an application that is culture-neutral and language-neutral, and that supports localized user interfaces and regional data for all users.</span></span> <span data-ttu-id="590a1-106">Patří sem proces vytvoření návrhu a rozhodnutí z oblasti programování, která nejsou založena na jazykových předpokladech.</span><span class="sxs-lookup"><span data-stu-id="590a1-106">It involves making design and programming decisions that are not based on culture-specific assumptions.</span></span> <span data-ttu-id="590a1-107">Zatímco globalizovaná aplikace není lokalizována, je i přesto navržena a napsána tak, aby bylo možné ji poměrně snadno následně lokalizovat do jednoho nebo více jazyků.</span><span class="sxs-lookup"><span data-stu-id="590a1-107">While a globalized application is not localized, it nevertheless is designed and written so that it can be subsequently localized into one or more languages with relative ease.</span></span>  
  
 [<span data-ttu-id="590a1-108">Vyhodnocení lokalizovatelnosti</span><span class="sxs-lookup"><span data-stu-id="590a1-108">Localizability Review</span></span>](../../../docs/standard/globalization-localization/localizability-review.md)  
 <span data-ttu-id="590a1-109">Tento krok zahrnuje revizi kódu a návrhu aplikace a zajišťuje, aby bylo možné ji snadno lokalizovat, identifikovat potenciální problémy lokalizace a ověřit, zda je spustitelný kód aplikace oddělen od prostředků.</span><span class="sxs-lookup"><span data-stu-id="590a1-109">This step involves reviewing an application's code and design to ensure that it can be localized easily and to identify potential roadblocks for localization, and verifying that the application's executable code is separated from its resources.</span></span> <span data-ttu-id="590a1-110">Pokud fáze globalizace byla účinná, přezkoumání lokalizovatelnosti potvrdí návrh a kódování provedené během globalizace.</span><span class="sxs-lookup"><span data-stu-id="590a1-110">If the globalization stage was effective, the localizability review will confirm the design and coding choices made during globalization.</span></span> <span data-ttu-id="590a1-111">Fáze lokalizovatelnosti může rovněž určit všechny zbývající problémy tak, aby zdrojový kód aplikace nemusel být změněn během fáze lokalizace.</span><span class="sxs-lookup"><span data-stu-id="590a1-111">The localizability stage may also identify any remaining issues so that an application's source code doesn't have to be modified during the localization stage.</span></span>  
  
 [<span data-ttu-id="590a1-112">Lokalizace</span><span class="sxs-lookup"><span data-stu-id="590a1-112">Localization</span></span>](../../../docs/standard/globalization-localization/localization.md)  
 <span data-ttu-id="590a1-113">Tento krok spočívá v přizpůsobení aplikace pro specifické jazykové verze nebo regiony.</span><span class="sxs-lookup"><span data-stu-id="590a1-113">This step involves customizing an application for specific cultures or regions.</span></span> <span data-ttu-id="590a1-114">Pokud byly kroky globalizace a lokalizovatelnosti provedeny správně, lokalizace sestává především z překladu uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="590a1-114">If the globalization and localizability steps have been performed correctly, localization consists primarily of translating the user interface.</span></span>  
  
 <span data-ttu-id="590a1-115">Následující tři kroky přináší dvě výhody:</span><span class="sxs-lookup"><span data-stu-id="590a1-115">Following these three steps provides two advantages:</span></span>  
  
-   <span data-ttu-id="590a1-116">Ho s není pozměnit aplikaci, která je určená pro podporu jednoho jazykové verzi, například USA Angličtina, pro podporu dalších jazykových verzí.</span><span class="sxs-lookup"><span data-stu-id="590a1-116">It frees you from having to retrofit an application that is designed to support a single culture, such as U.S. English, to support additional cultures.</span></span>  
  
-   <span data-ttu-id="590a1-117">Výsledkem jsou lokalizované aplikace, které jsou více stabilní a méně chybové.</span><span class="sxs-lookup"><span data-stu-id="590a1-117">It results in localized applications that are more stable and have fewer bugs.</span></span>  
  
 <span data-ttu-id="590a1-118">Rozhraní .NET Framework poskytuje rozsáhlou podporu pro vývoj globalizovaných a lokalizovaných aplikací.</span><span class="sxs-lookup"><span data-stu-id="590a1-118">The .NET Framework provides extensive support for the development of world-ready and localized applications.</span></span> <span data-ttu-id="590a1-119">Mnoho členů typů v knihovně tříd rozhraní .NET Framework podporuje globalizaci vrácením hodnot, které odpovídají konvencím aktuální jazykové verze nebo specifické jazykové verze uživatele.</span><span class="sxs-lookup"><span data-stu-id="590a1-119">In particular, many type members in the .NET Framework class library aid globalization by returning values that reflect the conventions of either the current user's culture or a specified culture.</span></span> <span data-ttu-id="590a1-120">Rozhraní .NET Framework podporuje také satelitní sestavení, která usnadňují proces lokalizace aplikace.</span><span class="sxs-lookup"><span data-stu-id="590a1-120">Also, the .NET Framework supports satellite assemblies, which facilitate the process of localizing an application.</span></span>  
  
 <span data-ttu-id="590a1-121">Další informace najdete v tématu [globalizace dokumentaci](/globalization/).</span><span class="sxs-lookup"><span data-stu-id="590a1-121">For additional information, see the [Globalization documentation](/globalization/).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="590a1-122">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="590a1-122">In This Section</span></span>  
 [<span data-ttu-id="590a1-123">Globalizace</span><span class="sxs-lookup"><span data-stu-id="590a1-123">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)  
 <span data-ttu-id="590a1-124">Tento článek popisuje první fázi vytváření globalizované aplikace, včetně návrhu a kódování aplikace, která je nezávislá na jazykové verzi a jazyce.</span><span class="sxs-lookup"><span data-stu-id="590a1-124">Discusses the first stage of creating a world-ready application, which involves designing and coding an application that is culture-neutral and language-neutral.</span></span>  
  
 [<span data-ttu-id="590a1-125">Vyhodnocení lokalizovatelnosti</span><span class="sxs-lookup"><span data-stu-id="590a1-125">Localizability Review</span></span>](../../../docs/standard/globalization-localization/localizability-review.md)  
 <span data-ttu-id="590a1-126">Tento článek popisuje vytvoření lokalizované aplikace, včetně identifikace možných potenciálních problémů při lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="590a1-126">Discusses the second stage of creating a localized application, which involves identifying potential roadblocks to localization.</span></span>  
  
 [<span data-ttu-id="590a1-127">Lokalizace</span><span class="sxs-lookup"><span data-stu-id="590a1-127">Localization</span></span>](../../../docs/standard/globalization-localization/localization.md)  
 <span data-ttu-id="590a1-128">Tento článek popisuje závěrečnou fázi vytvoření lokalizované aplikace, která spočívá v přizpůsobení uživatelského rozhraní pro konkrétní oblasti nebo jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="590a1-128">Discusses the final stage of creating a localized application, which involves customizing an application's user interface for specific regions or cultures.</span></span>  
  
 [<span data-ttu-id="590a1-129">Řetězcové operace nezávislé na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="590a1-129">Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 <span data-ttu-id="590a1-130">Popisuje způsob použití metod a tříd rozhraní .NET Framework, které jsou ve výchozím nastavení závislé na jazykové verzi, a to za účelem získání výsledků nezávislých na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="590a1-130">Describes how to use .NET Framework methods and classes that are culture-sensitive by default to obtain culture-insensitive results.</span></span>  
  
 [<span data-ttu-id="590a1-131">Doporučené postupy pro vývoj aplikací připravených k použití</span><span class="sxs-lookup"><span data-stu-id="590a1-131">Best Practices for Developing World-Ready Applications</span></span>](../../../docs/standard/globalization-localization/best-practices-for-developing-world-ready-apps.md)  
 <span data-ttu-id="590a1-132">Popisuje doporučené postupy pro globalizaci, lokalizaci a vývoj globalizovaných aplikací technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="590a1-132">Describes the best practices to follow for globalization, localization, and developing world-ready ASP.NET applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="590a1-133">Odkaz</span><span class="sxs-lookup"><span data-stu-id="590a1-133">Reference</span></span>  
 <span data-ttu-id="590a1-134"><xref:System.Globalization?displayProperty=nameWithType>obor názvů</span><span class="sxs-lookup"><span data-stu-id="590a1-134"><xref:System.Globalization?displayProperty=nameWithType> namespace</span></span>  
 <span data-ttu-id="590a1-135">Obsahuje třídy, které definují informace týkající se jazykové verze, jako je jazyk, země a oblast, používané kalendáře, vzory formátu data, měny a čísel a pořadí řazení řetězců.</span><span class="sxs-lookup"><span data-stu-id="590a1-135">Contains classes that define culture-related information, including the language, the country/region, the calendars in use, the format patterns for dates, currency, and numbers, and the sort order for strings.</span></span>  
  
 <span data-ttu-id="590a1-136"><xref:System.Resources>obor názvů</span><span class="sxs-lookup"><span data-stu-id="590a1-136"><xref:System.Resources> namespace</span></span>  
 <span data-ttu-id="590a1-137">Obsahuje třídy pro vytváření, manipulaci a používání prostředků.</span><span class="sxs-lookup"><span data-stu-id="590a1-137">Provides classes for creating, manipulating, and using resources.</span></span>  
  
 <span data-ttu-id="590a1-138"><xref:System.Text>obor názvů</span><span class="sxs-lookup"><span data-stu-id="590a1-138"><xref:System.Text> namespace</span></span>  
 <span data-ttu-id="590a1-139">Obsahuje třídy představující kódování znaků ASCII, ANSI, Unicode a další.</span><span class="sxs-lookup"><span data-stu-id="590a1-139">Contains classes representing ASCII, ANSI, Unicode, and other character encodings.</span></span>  
  
 [<span data-ttu-id="590a1-140">Resgen.exe (generátor zdrojových souborů)</span><span class="sxs-lookup"><span data-stu-id="590a1-140">Resgen.exe (Resource File Generator)</span></span>](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)  
 <span data-ttu-id="590a1-141">Popisuje způsob použití Resgen.exe pro převedení souborů TXT a souborů prostředků založených na formátu XML (RESX) na binární soubory .resources modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="590a1-141">Describes how to use Resgen.exe to convert .txt files and XML-based resource format (.resx) files to common language runtime binary .resources files.</span></span>  
  
 [<span data-ttu-id="590a1-142">Winres.exe (editor prostředků Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="590a1-142">Winres.exe (Windows Forms Resource Editor)</span></span>](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)  
 <span data-ttu-id="590a1-143">Popisuje způsob lokalizace formulářů Windows Forms pomocí nástroje Winres.exe.</span><span class="sxs-lookup"><span data-stu-id="590a1-143">Describes how to use Winres.exe to localize Windows Forms forms.</span></span>
