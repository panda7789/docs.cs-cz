---
title: Blazor pro vývojáře ASP.NET Web Forms
description: Naučte se vytvářet webové aplikace s plným zásobníkem pomocí rozhraní .NET pomocí Blazoru a .NET Core jednoduchým a známým způsobem.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 394d11038b59f4cbe9e9955df43b6198eb5daaf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73088133"
---
# <a name="blazor-for-aspnet-web-forms-developers"></a>Blazor pro vývojáře ASP.NET Web Forms

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![Snímek obrazovky, který zobrazuje obal e-knihy Aplikace bez serveru.](./media/index/blazor-for-web-forms-developers-cover.png)

> KE STAŽENÍ K DISPOZICI NA ADRESE:<https://aka.ms/blazor-ebook>

PUBLIKOVAL(A)

Produktové týmy Microsoft Developer Division, .NET a Visual Studio

Divize společnosti Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Autorská práva © 2019 společností Microsoft Corporation

Všechna práva vyhrazena. Žádná část obsahu této knihy nesmí být reprodukována nebo přenášena v jakékoli formě nebo jakýmkoli způsobem bez písemného souhlasu vydavatele.

Tato kniha je poskytována "tak, jak je" a vyjadřuje názory a názory autora. Názory, názory a informace vyjádřené v této knize, včetně URL a dalších odkazů na internetové stránky, se mohou změnit bez předchozího upozornění.

Některé zde uvedené příklady slouží pouze k znázornění a jsou smyšlené. Neměli byste z nich vyvozovat žádné skutečné vztahy či spojení.

Společnost Microsoft a ochranné <https://www.microsoft.com> známky uvedené na webové stránce "Ochranné známky" jsou ochrannými známkami skupiny společností Microsoft.

Mac a macOS jsou ochranné známky společnosti Apple Inc.

Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.

Autoři:

> **[Daniel Roth](https://github.com/danroth27)**, hlavní programový manažer společnosti Microsoft Corp.

> **[Jeff Fritz](https://github.com/csharpfritz)**, vedoucí programový manažer společnosti Microsoft Corp.

> **[Taylor Southwick](https://github.com/twsouthwick)**, hlavní softwarový inženýr, společnost Microsoft Corp.

> **[Scott Addie](https://github.com/scottaddie)**, hlavní vývojář obsahu, Microsoft Corp.

## <a name="introduction"></a>Úvod

.NET již dlouho podporuje vývoj webových aplikací prostřednictvím ASP.NET, komplexní sadu architektur a nástrojů pro vytváření jakéhokoli druhu webové aplikace. ASP.NET má vlastní linii webových rámců a technologií, které začínají až s klasickými stránkami Active Server Pages (ASP). Architektury, jako jsou ASP.NET Web Forms, ASP.NET MVC, ASP.NET webové stránky a v poslední době ASP.NET Core, poskytují produktivní a účinný způsob vytváření webových aplikací *vykreslených serverem,* kde je obsah uživatelského rozhraní dynamicky generován na serveru v reakci na požadavky HTTP. Každý ASP.NET rámec se zaměřuje na jiné publikum a filozofii vytváření aplikací. ASP.NET webových formulářů dodaných s původní verzí rozhraní .NET Framework a umožnilvývoj webu pomocí mnoha vzorů známých vývojářům stolních počítačů, jako jsou opakovaně použitelné ovládací prvky uživatelského rozhraní s jednoduchým zpracováním událostí. Žádná z ASP.NET nabídky však poskytují způsob spuštění kódu, který byl spuštěn v prohlížeči uživatele. K tomu, že vyžaduje psaní JavaScripta a pomocí některého z mnoha JavaScript rámců a nástrojů, které mají postupně a z popularity v průběhu let: jQuery, Knockout, Angular, Reagovat, a tak dále.

[Blazor](https://blazor.net) je nový webový framework, který mění to, co je možné při vytváření webových aplikací s .NET. Blazor je rozhraní webového uživatelského rozhraní na straně klienta založené na Jazyce C# namísto JavaScriptu. S Blazor můžete napsat logiku na straně klienta a komponenty uživatelského rozhraní v C#, zkompilovat je do normálních sestavení .NET a pak je spustit přímo v prohlížeči pomocí nového otevřeného webového standardu s názvem WebAssembly. Nebo alternativně Blazor můžete spustit komponenty rozhraní .NET uI na serveru a zpracovávat všechny interakce ui plynule přes real-time připojení s prohlížečem. Při spárování s rozhraním .NET spuštěným na serveru blazor umožňuje vývoj webu s rozhraním .NET v plném rozsahu. Zatímco Blazor sdílí mnoho společných rysů s ASP.NET Web Forms, jako je opakovaně použitelný model komponent a jednoduchý způsob, jak zpracovat uživatelské události, staví také na základech .NET Core, aby poskytl moderní a vysoce výkonné prostředí pro vývoj webových aplikací.

Tato kniha představuje ASP.NET vývojářů webových formulářů do Blazoru způsobem, který je známý a pohodlný. Představuje koncepty Blazor u analogických konceptů v ASP.NET Web Forms a zároveň vysvětluje nové koncepty, které mohou být méně známé. Pokrývá širokou škálu témat a obav, včetně vytváření komponent, směrování, rozložení, konfigurace a zabezpečení. A zatímco obsah této knihy je primárně pro povolení nového vývoje, zahrnuje také pokyny a strategie pro migraci stávajících ASP.NET webových formulářů do Blazoru, pokud chcete modernizovat stávající aplikaci.

## <a name="who-should-use-the-book"></a>Kdo by měl knihu používat

Tato kniha je pro ASP.NET vývojáři webových formulářů, kteří hledají úvod do Blazoru, který se vztahuje k jejich stávajícím znalostem a dovednostem. Tato kniha vám může pomoci s rychlým zahájením nového projektu založeného na Blazoru nebo s cílem zmapovat plán modernizace stávající aplikace ASP.NET webových formulářů.

## <a name="how-to-use-the-book"></a>Jak používat knihu

První část této knihy pokrývá to, co je Blazor, a porovnává ji s vývojem webových aplikací s ASP.NET Web Forms. Kniha pak pokrývá řadu témat Blazor, kapitola po kapitole, a spojuje každý koncept Blazor na odpovídající koncept v ASP.NET Web Forms, nebo vysvětluje plně všechny zcela nové pojmy. Kniha také pravidelně odkazuje na kompletní ukázkovou aplikaci implementovanou jak v ASP.NET Webových formulářích, tak v Blazoru, aby demonstrovala funkce Blazoru a poskytla případovou studii pro migraci z ASP.NET webových formulářů do Blazoru. Obě implementace ukázkové aplikace (ASP.NET webových formulářů a verzí Blazor) najdete na [GitHubu](https://github.com/dotnet-architecture/eshoponblazor).

## <a name="what-this-book-doesnt-cover"></a>Co tato kniha nepokrývá

Tato kniha je úvodem do Blazoru, nikoli komplexním průvodcem migrací. I když obsahuje pokyny, jak přistupovat k migraci projektu z ASP.NET Web Forms do Blazoru, nesnaží se pokrýt každou nuanci a detaily. Obecnější pokyny pro migraci z ASP.NET do ASP.NET jádra naleznete v [pokynech pro migraci](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/) v dokumentaci ASP.NET Core.

### <a name="additional-resources"></a>Další zdroje

Oficiální domovskou stránku Blazor u <https://blazor.net>vidíte najdete na adrese .

## <a name="send-your-feedback"></a>Pošlete svůj názor

Tato kniha a související vzorky se neustále vyvíjejí, takže vaše zpětná vazba je vítána! Pokud máte komentáře o tom, jak lze tuto knihu vylepšit, použijte sekci zpětné vazby v dolní části libovolné stránky postavené na [problémech githubu](https://github.com/dotnet/docs/issues).

>[!div class="step-by-step"]
>[Další](introduction.md)
