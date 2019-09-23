---
title: Blazor pro vývojáře webových formulářů ASP.NET
description: Naučte se vytvářet plnohodnotné webové aplikace s využitím .NET pomocí Blazor a .NET Core jednoduchým a známým způsobem.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: a80483f6a1f1cb9e5a3e2ffff18cbd59c5b67af3
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183796"
---
# <a name="blazor-for-aspnet-web-forms-developers"></a>Blazor pro vývojáře webových formulářů ASP.NET

![Snímek obrazovky zobrazující titulní knihu aplikací bez serveru](./media/index/blazor-for-web-forms-developers-cover.png)

> STAŽENÍ k dispozici v:<https://aka.ms/blazor-ebook>

PUBLIKOVAL (A)

Týmy produktů Microsoft Developer divize, .NET a Visual Studio

Divize společnosti Microsoft Corporation

Jeden způsob Microsoftu

Redmond, Washington 98052-6399

Copyright © 2019 by Microsoft Corporation

Všechna práva vyhrazena. Žádná část obsahu této knihy se nedá reprodukovat ani přenést v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.

Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora. Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.

Některé příklady, které jsou zde uvedeny, jsou k dispozici pouze pro ilustraci a jsou smyšlené. Neexistuje žádné skutečné přidružení nebo připojení, které by mělo být odvozeno.

Microsoft a ochranné známky uvedené <https://www.microsoft.com> na webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.

Mac a macOS jsou ochranné známky společnosti Apple Inc.

Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.

Autoři

> **[Daniel Skořepa](https://github.com/danroth27)** , hlavní správce programů, Microsoft Corp.

> **[Jan Fritz](https://github.com/csharpfritz)** , vedoucí program Manager, Microsoft Corp.

> **[Taylor Southwick](https://github.com/twsouthwick)** , vedoucí softwarový inženýr, Microsoft Corp.

> **[Scott Addie](https://github.com/scottaddie)** , náměstek – vývojář obsahu, společnost Microsoft Corp.

## <a name="introduction"></a>Úvod

.NET podporuje vývoj webových aplikací prostřednictvím ASP.NET, komplexní sadu platforem a nástrojů pro vytváření libovolných webových aplikací. ASP.NET má svou vlastní linii webových architektur a technologií, které začínají na klasických Active Server stránkách (ASP). Prostředí, jako jsou webové formuláře ASP.NET, ASP.NET MVC, ASP.NET webové stránky a další ASP.NET Core, poskytují produktivní a výkonný způsob, jak vytvořit *serverově vykreslené* webové aplikace, kde se obsah uživatelského rozhraní dynamicky generuje na serveru v reakci na http. požádal. Jednotlivé architektury ASP.NET Framework se přifilozofie k různým cílovým skupinám a sestavování aplikací. ASP.NET webové formuláře dodávané s původní verzí .NET Framework a s podporou vývoje webů s využitím mnoha vzorů, které jsou známé vývojářům desktopových aplikací, jako jsou opakovaně použitelné ovládací prvky uživatelského rozhraní s jednoduchým zpracováním událostí. Žádná z nabídek ASP.NET však neposkytuje způsob, jak spustit kód, který je spuštěn v prohlížeči uživatele. To uděláte tak, že vyžaduje zápis JavaScriptu a používání kteréhokoli z mnoha rozhraní a nástrojů JavaScript, které byly postupně rozloženy do několika let: jQuery, vykrojení, úhlová reakce a tak dále.

[Blazor](https://blazor.net) je nová webová architektura, která mění, co je možné při sestavování webových aplikací pomocí .NET. Blazor je rozhraní Web UI na straně klienta založené na C# jazyce místo JavaScriptu. Pomocí Blazor můžete napsat logiku na straně klienta a komponenty uživatelského rozhraní v C#, zkompilovat je do normálních sestavení .NET a pak je spustit přímo v prohlížeči pomocí nového otevřeného webového standardu s názvem WebAssembly. Případně může Blazor spustit komponenty uživatelského rozhraní .NET na serveru a zpracovávat všechny interakce uživatelského rozhraní po celou dobu přes připojení v reálném čase s prohlížečem. Když se spáruje s .NET spuštěným na serveru, Blazor umožňuje vytváření celého zásobníku na webu pomocí .NET. I když Blazor sdílí mnoho commonalities s ASP.NET webovými formuláři, jako je třeba opakovaně použitelný model komponenty a jednoduchý způsob, jak zpracovávat události uživatelů, vytvoří se také na základech .NET Core za účelem poskytování moderního a vysoce výkonného prostředí pro vývoj webů.

Tato kniha zavádí ASP.NET vývojářům webových formulářů Blazor způsobem, který je známý a pohodlný. Zavádí Blazor koncepty paralelně s podobnými koncepty ve webových formulářích ASP.NET a zároveň vysvětluje nové koncepty, které mohou být méně známé. Zahrnuje širokou škálu témat a otázek, mezi které patří vytváření komponent, směrování, rozložení, konfigurace a zabezpečení. A přestože obsah této knihy je primárně určen pro nové vývojové prostředí, zahrnuje také pokyny a strategie pro migraci stávajících webových formulářů ASP.NET do Blazor pro, kdy chcete modernizovat existující aplikaci.

## <a name="who-should-use-the-book"></a>Kdo má knihu používat

Tato kniha je určená pro vývojáře webových formulářů ASP.NET, kteří hledají Úvod k Blazorům, které se týkají jejich stávajících znalostí a dovedností. Tato kniha vám může pomáhat s rychlým zahájením práce na novém projektu založeném na Blazor nebo s cílem pokládat se seznámení s plánem modernizaci existující aplikace webového formuláře ASP.NET.

## <a name="how-to-use-the-book"></a>Jak používat knihu

První část této knihy popisuje, co Blazor je a porovnává je s vývojem webových aplikací pomocí webových formulářů ASP.NET. Kniha se pak zabývá nejrůznějšími tématy Blazor, kapitolami podle kapitoly a souvisí s každým Blazor konceptem odpovídajícím pojmem ve webových formulářích ASP.NET nebo vysvětluje úplně nové koncepty. V knize se také pravidelně odkazuje na kompletní ukázkovou aplikaci implementovanou v ASP.NET webových formulářích i v Blazor, která předvádí funkce Blazor a poskytuje případovou studii pro migraci z ASP.NET webových formulářů na Blazor. Obě implementace ukázkové aplikace (ASP.NET Web Forms a Blazor verze) najdete na [GitHubu](https://github.com/dotnet-architecture/eshoponblazor).

## <a name="what-this-book-doesnt-cover"></a>Co tato kniha nepokrývá

Tato kniha představuje úvod do Blazor, ne komplexní průvodce migrací. I když obsahuje pokyny k tomu, jak získat přístup k migraci projektu z webových formulářů ASP.NET na Blazor, se nepokouší pokrýt všechny nuance a podrobnosti. Obecnější pokyny týkající se migrace z ASP.NET na ASP.NET Core najdete v dokumentaci k ASP.NET Core v dokumentaci k [migraci](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/) .

### <a name="additional-resources"></a>Další zdroje

Oficiální domovskou stránku Blazor a dokumentaci najdete na adrese <https://blazor.net>.

## <a name="send-your-feedback"></a>Poslat svůj názor

Tato kniha a související ukázky se neustále vyvíjí, takže se vaše zpětná vazba vítá! Pokud máte komentáře k tomu, jak se tato kniha dá zlepšit, použijte část zpětná vazba v dolní části každé stránky založené na [problémech na GitHubu](https://github.com/dotnet/docs/issues).

>[!div class="step-by-step"]
>[Next](introduction.md)
