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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f03935c1ee38cec4ee20c4306213be484933f0bb
ms.sourcegitcommit: 6c480773ae896f45af4671fb3e26611a50e4dd81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2018
ms.locfileid: "35250996"
---
# <a name="globalizing-and-localizing-net-applications"></a>Globalizace a lokalizace aplikací .NET
Vývoj [aplikací připravených](http://msdn.microsoft.com/goglobal/bb978433.aspx), včetně aplikace, která je možné lokalizovat do jednoho nebo více jazyků, zahrnuje tři kroky: globalizace, lokalizovatelnosti a lokalizace.  
  
 [Globalizace](../../../docs/standard/globalization-localization/globalization.md)  
 Tento krok zahrnuje návrh a kódování aplikace, která je neutrální pro jazykové prostředí a daný jazyk a která podporuje lokalizovaná uživatelská rozhraní a regionální data pro všechny uživatele aplikace. Patří sem proces vytvoření návrhu a rozhodnutí z oblasti programování, která nejsou založena na jazykových předpokladech. Zatímco globalizovaná aplikace není lokalizována, je i přesto navržena a napsána tak, aby bylo možné ji poměrně snadno následně lokalizovat do jednoho nebo více jazyků.  
  
 [Revize lokalizovatelnosti](../../../docs/standard/globalization-localization/localizability-review.md)  
 Tento krok zahrnuje revizi kódu a návrhu aplikace a zajišťuje, aby bylo možné ji snadno lokalizovat, identifikovat potenciální problémy lokalizace a ověřit, zda je spustitelný kód aplikace oddělen od prostředků. Pokud fáze globalizace byla účinná, přezkoumání lokalizovatelnosti potvrdí návrh a kódování provedené během globalizace. Fáze lokalizovatelnosti může rovněž určit všechny zbývající problémy tak, aby zdrojový kód aplikace nemusel být změněn během fáze lokalizace.  
  
 [Lokalizace](../../../docs/standard/globalization-localization/localization.md)  
 Tento krok spočívá v přizpůsobení aplikace pro specifické jazykové verze nebo regiony. Pokud byly kroky globalizace a lokalizovatelnosti provedeny správně, lokalizace sestává především z překladu uživatelského rozhraní.  
  
 Následující tři kroky přináší dvě výhody:  
  
-   Ho s není pozměnit aplikaci, která je určená pro podporu jednoho jazykové verzi, například USA Angličtina, pro podporu dalších jazykových verzí.  
  
-   Výsledkem jsou lokalizované aplikace, které jsou více stabilní a méně chybové.  
  
 Rozhraní .NET poskytuje rozsáhlou podporu pro vývoj aplikací připravených a lokalizované. Mnoho na konkrétní typ členy v podpory globalizace rozhraní .NET třídy knihovny vrácením hodnoty, které odráží konvence jazykové verze aktuálního uživatele nebo zadaná jazyková verze. Rozhraní .NET podporuje také satelitní sestavení, které usnadňují proces lokalizace aplikace.  
  
 Další informace najdete v tématu [globalizace dokumentaci](/globalization/).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Globalizace](../../../docs/standard/globalization-localization/globalization.md)  
 Tento článek popisuje první fázi vytváření globalizované aplikace, včetně návrhu a kódování aplikace, která je nezávislá na jazykové verzi a jazyce.  
  
 [Revize lokalizovatelnosti](../../../docs/standard/globalization-localization/localizability-review.md)  
 Tento článek popisuje vytvoření lokalizované aplikace, včetně identifikace možných potenciálních problémů při lokalizaci.  
  
 [Lokalizace](../../../docs/standard/globalization-localization/localization.md)  
 Tento článek popisuje závěrečnou fázi vytvoření lokalizované aplikace, která spočívá v přizpůsobení uživatelského rozhraní pro konkrétní oblasti nebo jazykové verze.  
  
 [Operace s řetězci nezávislé na jazykové verzi](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 Popisuje způsob použití metod rozhraní .NET a třídy, které jsou závislé na jazykové verzi ve výchozím nastavení se získat výsledky na jazykové verzi.  
  
 [Osvědčené postupy pro vývoj aplikací připravených](../../../docs/standard/globalization-localization/best-practices-for-developing-world-ready-apps.md)  
 Popisuje doporučené postupy pro globalizaci, lokalizaci a vývoj globalizovaných aplikací technologie ASP.NET.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Globalization?displayProperty=nameWithType> obor názvů  
 Obsahuje třídy, které definují informace týkající se jazykové verze, jako je jazyk, země a oblast, používané kalendáře, vzory formátu data, měny a čísel a pořadí řazení řetězců.  
  
 <xref:System.Resources> obor názvů  
 Obsahuje třídy pro vytváření, manipulaci a používání prostředků.  
  
 <xref:System.Text> obor názvů  
 Obsahuje třídy představující kódování znaků ASCII, ANSI, Unicode a další.  
  
 [Resgen.exe (generátor zdrojových souborů)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)  
 Popisuje způsob použití Resgen.exe pro převedení souborů TXT a souborů prostředků založených na formátu XML (RESX) na binární soubory .resources modulu CLR (Common Language Runtime).  
  
 [Winres.exe (editor prostředků Windows Forms)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)  
 Popisuje způsob lokalizace formulářů Windows Forms pomocí nástroje Winres.exe.
