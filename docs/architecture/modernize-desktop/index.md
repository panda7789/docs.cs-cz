---
title: Modernizaci desktopové aplikace ve Windows 10 s .NET Core 3,1
description: Naučte se modernizovat stávající desktopové aplikace pomocí .NET Core 3,1
ms.date: 05/12/2020
ms.openlocfilehash: 5861f806a9158ef761c47bc23e51327d4e2d0480
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423234"
---
# <a name="modernizing-desktop-apps-on-windows-10-with-net-core-31"></a>Modernizaci desktopové aplikace ve Windows 10 s .NET Core 3,1

![Snímek obrazovky zobrazující titulní knihu modernizovat desktopových aplikací](./media/modernizing-existing-desktop-apps-ebook-cover.png)

PUBLIKOVAL(A)

Týmy produktů Microsoft Developer divize, .NET a Visual Studio

Divize společnosti Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2020 od společnosti Microsoft Corporation

Všechna práva vyhrazena. Žádná část obsahu této knihy se nedá reprodukovat ani přenést v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.

Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora. Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.

Některé zde uvedené příklady slouží pouze k znázornění a jsou smyšlené. Neměli byste z nich vyvozovat žádné skutečné vztahy či spojení.

Microsoft a ochranné známky uvedené na <https://www.microsoft.com> webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.

Mac a macOS jsou ochranné známky společnosti Apple Inc.

Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.

Spoluautoři:

> **Olia Gavrysh**, programový manažer, tým .NET, Microsoft

> **Miguel Angel Castejón Dominguez**, architekt inovace, kabel

Účastníci a kontroloři:

> **Maira Wenzel**, vedoucí program, tým .NET, Microsoft

> **Andy de Gorge**, náměstek – vývojář obsahu, tým docs pro .NET, Microsoft

> **Miguel Ramos**, vedoucí program pro vývoj aplikací, tým vývojářů platformy Windows, Microsoft

> **Adam Braden**, hlavní správce programů, tým pro vývojáře Windows Developer Platform, Microsoft

> **Ricardo Minguez Pablos**, vedoucí program, tým Azure IoT, Microsoft

> **Nish Anil**, vedoucí program, tým .NET, Microsoft

> **Beth Massi**, vedoucí marketing pro produkty, Microsoft

> **Scott Hunterem**, správce programu partnera pro partnery, tým .NET, Microsoft

> **Marta Fuentes Lara**, kabel

> **Raúl Fernández de Córdoba**; kabel

> **Antonio Manuel Fernández Cantos**, kabel

## <a name="introduction"></a>Úvod

Tato kniha obsahuje informace o strategiích, které můžete použít k přesunutí stávajících aplikací klasické pracovní plochy prostřednictvím cesty k modernizaci a začlenit nejnovější funkce pro modul runtime, jazyk a platformu. Zjistíte, že neexistuje žádný jedinečný recept, protože každá aplikace je odlišná, a proto jsou vaše požadavky a předvolby. Dobrá zpráva je, že existují běžné přístupy, které můžete použít k přidání nových funkcí a možností do aplikací. Některé z nich ani nevyžadují významné změny kódu. V této knize si ukážeme, jak všechny tyto funkce fungují na pozadí a vysvětlují mechanismy jejich implementace. Kromě toho najdete některé běžné scénáře pro modernizaci existující aplikace klasické pracovní plochy, takže můžete najít inspiraci pro vývoj vašich projektů.

Přístup Microsoftu k modernizaci stávajících aplikací vám poskytne flexibilitu při vytváření vlastní přizpůsobené cesty. Všechny strategie pro moderní navýšení popsané v této příručce jsou většinou nezávislé. Můžete vybrat ty, které jsou relevantní pro vaši aplikaci, a přeskočit jiné, které pro vás nejsou důležité. Jinými slovy, můžete vzájemně kombinovat a odpovídat strategiím, které vašim potřebám vaší aplikace nejlépe vyřešíte.

## <a name="who-should-use-the-book"></a>Kdo má knihu používat

Tuto knihu jsme napsali pro vývojáře a architekty řešení, kteří chtějí modernizovat stávající desktopové aplikace model Windows Forms a WPF a využívat výhody .NET Core a Windows 10.

Tuto příručku můžete také najít užitečnou, pokud jste Tvůrce technického rozhodnutí, jako je například podnikový architekt nebo vedoucí vývoj nebo ředitel, který chce získat přehled o výhodách aktualizace existujících aplikací klasické pracovní plochy.

## <a name="how-to-use-the-book"></a>Jak používat knihu

Tato kniha obsahuje vysvětlení "Proč", proč byste mohli chtít modernizovat své stávající aplikace a konkrétní výhody, které získáte pomocí .NET Core 3,1 a MSIX pro modernizovat aplikací klasické pracovní plochy. Obsah knihy je navržený pro architekty a pracovníky technického rozhodování, kteří chtějí mít přehled, ale nepotřebují se soustředit na implementaci a technický krok, podrobné informace.

V různých kapitolách jsou k dispozici ukázkové fragmenty kódu implementace a snímky obrazovky, přičemž kapitola 5 nabízí kompletní proces migrace pro ukázkové aplikace.

## <a name="what-this-book-doesnt-cover"></a>Co tato kniha nepokrývá

Tato kniha se zabývá konkrétní podmnožinou scénářů, které se zaměřují na scénáře navýšení a posunutí, a vysvětluje způsob, jak získat výhody modernizaci bez snahy o přepis kódu.

Tato kniha nemá informace o vývoji moderních aplikací s využitím zcela nového .NET Core nebo o zahájení práce s model Windows Forms a WPF. Zaměřuje se na to, jak můžete aktualizovat existující aplikace klasické pracovní plochy s využitím nejnovějších technologií pro vývoj desktopových aplikací.

## <a name="samples-used-in-this-book"></a>Ukázky používané v této knize

K zdůraznění nezbytných kroků pro provedení modernizace budeme používat ukázkovou aplikaci s názvem `eShopModernizing` . Tato aplikace má dva typy, model Windows Forms a WPF, a my vám ukážeme podrobný postup, jak provést modernizaci na obou těchto počítačích pro .NET Core.

V úložišti GitHub pro tuto knihu najdete také výsledky procesu, pomocí kterých se můžete rozhodnout, jestli se rozhodnete postupovat podle podrobného kurzu.

## <a name="send-your-feedback"></a>Poslat svůj názor

Tato kniha a související ukázky se neustále vyvíjí, takže se vaše zpětná vazba vítá! Pokud máte komentáře k tomu, jak se tato kniha dá zlepšit, použijte část zpětná vazba v dolní části každé stránky založené na [problémech na GitHubu](https://github.com/dotnet/docs/issues).

>[!div class="step-by-step"]
>[Další](why-modern-applications.md)
