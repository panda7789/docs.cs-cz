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
# <a name="globalizing-and-localizing-net-applications"></a>Globalizace a lokalizace aplikací .NET

Vývoj aplikace připravené pro použití ve světě, včetně aplikace, která může být lokalizována do jednoho nebo více jazyků, zahrnuje tři kroky: globalizace, přezkoumání lokalizovatelnosti a lokalizaci.

[Globalizace](globalization.md)

Tento krok zahrnuje návrh a kódování aplikace, která je neutrální pro jazykové prostředí a daný jazyk a která podporuje lokalizovaná uživatelská rozhraní a regionální data pro všechny uživatele aplikace. Patří sem proces vytvoření návrhu a rozhodnutí z oblasti programování, která nejsou založena na jazykových předpokladech. Zatímco globalizovaná aplikace není lokalizována, je i přesto navržena a napsána tak, aby bylo možné ji poměrně snadno následně lokalizovat do jednoho nebo více jazyků.

[Revize lokalizovatelnosti](localizability-review.md)

Tento krok zahrnuje revizi kódu a návrhu aplikace a zajišťuje, aby bylo možné ji snadno lokalizovat, identifikovat potenciální problémy lokalizace a ověřit, zda je spustitelný kód aplikace oddělen od prostředků. Pokud fáze globalizace byla účinná, přezkoumání lokalizovatelnosti potvrdí návrh a kódování provedené během globalizace. Fáze lokalizovatelnosti může rovněž určit všechny zbývající problémy tak, aby zdrojový kód aplikace nemusel být změněn během fáze lokalizace.

[Lokalizace](localization.md)

Tento krok spočívá v přizpůsobení aplikace pro specifické jazykové verze nebo regiony. Pokud byly kroky globalizace a lokalizovatelnosti provedeny správně, lokalizace sestává především z překladu uživatelského rozhraní.

Následující tři kroky přináší dvě výhody:

- Umožní vám vyhnout se zpětnému pozměnění aplikace, která byla navržena pro podporu jediné jazykové verze, například americké angličtiny, aby podporovala další jazykové verze.

- Výsledkem jsou lokalizované aplikace, které jsou více stabilní a méně chybové.

.NET poskytuje rozsáhlou podporu pro vývoj aplikací připravených pro použití ve světě. Konkrétně mnoho členů typu v knihovně tříd .NET podporuje globalizaci vrácením hodnot, které odráží konvence buď aktuální jazykové verze uživatele, nebo zadané jazykové verze. Rozhraní .NET také podporuje satelitní sestavení, která usnadňují proces lokalizace aplikace.

Další informace naleznete v dokumentaci k [globalizaci](/globalization/).

## <a name="in-this-section"></a>V této části

[Globalizace](globalization.md)

Tento článek popisuje první fázi vytváření globalizované aplikace, včetně návrhu a kódování aplikace, která je nezávislá na jazykové verzi a jazyce.

[Rozhraní .NET globalizace a ICU](globalization-icu.md)

Popisuje, jak globalizace rozhraní .NET používá [mezinárodní komponenty pro kódování Unicode (ICU)](http://site.icu-project.org/home).

[Revize lokalizovatelnosti](localizability-review.md)

Tento článek popisuje vytvoření lokalizované aplikace, včetně identifikace možných potenciálních problémů při lokalizaci.

[Lokalizace](localization.md)

Tento článek popisuje závěrečnou fázi vytvoření lokalizované aplikace, která spočívá v přizpůsobení uživatelského rozhraní pro konkrétní oblasti nebo jazykové verze.

[Řetězcové operace nezávislé na jazykové verzi](culture-insensitive-string-operations.md)

Popisuje, jak používat metody a třídy .NET, které jsou ve výchozím nastavení závislé na jazykové verzi pro získání výsledků nezávislých na jazykové verzi.

[Osvědčené postupy pro vývoj aplikací připravených pro použití ve světě](best-practices-for-developing-world-ready-apps.md)

Popisuje doporučené postupy pro globalizaci, lokalizaci a vývoj globalizovaných aplikací technologie ASP.NET.

## <a name="reference"></a>Odkaz

- <xref:System.Globalization?displayProperty=nameWithType>hosting

   Obsahuje třídy, které definují informace týkající se jazykové verze, jako je jazyk, země a oblast, používané kalendáře, vzory formátu data, měny a čísel a pořadí řazení řetězců.

- <xref:System.Resources>hosting

   Obsahuje třídy pro vytváření, manipulaci a používání prostředků.

- <xref:System.Text>hosting

   Obsahuje třídy představující kódování znaků ASCII, ANSI, Unicode a další.

- [Resgen. exe (generátor zdrojových souborů)](../../framework/tools/resgen-exe-resource-file-generator.md)

   Popisuje způsob použití Resgen.exe pro převedení souborů TXT a souborů prostředků založených na formátu XML (RESX) na binární soubory .resources modulu CLR (Common Language Runtime).

- [Winres. exe (model Windows Forms editor prostředků)](../../framework/tools/winres-exe-windows-forms-resource-editor.md)

   Popisuje způsob lokalizace formulářů Windows Forms pomocí nástroje Winres.exe.
