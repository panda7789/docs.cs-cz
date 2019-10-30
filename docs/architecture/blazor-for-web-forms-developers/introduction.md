---
title: Úvod do Blazor pro vývojáře webových formulářů ASP.NET
description: Úvod do Blazor a psaní plně vrstvených webových aplikací s využitím .NET
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 6c045cd9c4378bd19f97dd722db054c969491d0b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087927"
---
# <a name="an-introduction-to-blazor-for-aspnet-web-forms-developers"></a>Úvod do Blazor pro vývojáře webových formulářů ASP.NET

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Rozhraní Web Forms v ASP.NET bylo sešívání vývoje webu .NET od chvíle, kdy .NET Framework poprvé dodal 2002. Zpět, když byl web stále v podstatě v rámci svých neozdobných, ASP.NET webových formulářů, které umožňují vytvářet webové aplikace snadno a efektivně, a to díky využití mnoha vzorů, které byly použity pro vývoj pro stolní počítače. Ve webových formulářích ASP.NET se dají webové stránky rychle skládat z opakovaně použitelných ovládacích prvků uživatelského rozhraní. Interakce s uživatelem jsou zpracovávány přirozeně jako události. Existují rozsáhlé ekosystémy ovládacích prvků uživatelského rozhraní webových formulářů, které poskytují dodavatelé Microsoftu a ovládají. Ovládací prvky usnadňují úsilí při připojování ke zdrojům dat a zobrazení bohatých vizualizací dat. Pro vizuálně skloněnou, návrhář webových formulářů, poskytuje jednoduché rozhraní přetažení pro správu ovládacích prvků.

V průběhu let společnost Microsoft zavedla nové webové architektury založené na ASP.NET pro řešení trendů vývoje webů. Mezi takové webové architektury patří ASP.NET MVC, webové stránky ASP.NET a další ASP.NET Core. U každé nové architektury byly některé z nich předpovězeny bezprostřední odmítnutí webových formulářů ASP.NET a criticized je jako zastaralé webové rozhraní outmoded. Bez ohledu na tyto předpovědi, mnoho webových vývojářů technologie .NET dál hledá ASP.NET webové formuláře, což je jednoduchý, stabilní a produktivní způsob práce.

V době psaní téměř poloviční miliony webových vývojářů využívají webové formuláře ASP.NET každý měsíc. Rozhraní webových formulářů ASP.NET je stabilní v bodě, kdy dokumentace, ukázky, knihy a blogové příspěvky z dekády zůstávají užitečné a relevantní. Pro mnoho webových vývojářů .NET je "ASP.NET" stále synonymem "ASP.NET Web Forms", stejně jako při prvním předí .NET. Argumenty pro profesionály a nevýhody webových formulářů ASP.NET ve srovnání s ostatními novými webovými rozhraními .NET Framework mohou být Rage zapnuty. Webové formuláře ASP.NET zůstanou oblíbená architektura pro vytváření webových aplikací.

I tak se inovace při vývoji softwaru nezpomalují. Všichni vývojáři softwaru musí mít přehled o nových technologiích a trendech. K tomu je potřeba zvážit dva trendy:

1. Posun na open source a pro různé platformy
2. Posunutí aplikační logiky na klienta

## <a name="an-open-source-and-cross-platform-net"></a>Rozhraní .NET open source a platforma pro různé platformy

Při prvním odeslání webových formulářů .NET a ASP.NET se ekosystém platforem napodobuje mnohem jiným než v současnosti. Stolní a serverové trhy byly na Windows. Alternativní platformy, jako je macOS a Linux, se stále působit potíže, aby se staly netrakcí. Webové formuláře ASP.NET jsou dodávány s .NET Framework jako součást systému Windows, což znamená, že aplikace webových formulářů ASP.NET lze spustit pouze na počítačích se systémem Windows Server. Mnoho moderních prostředí teď pro servery a vývojové počítače používá různé druhy platforem, což je absolutní požadavek na podporu více platforem pro mnoho uživatelů.

Většina moderních webových rozhraní je teď také open source, což má několik výhod. Uživatelé se beheld na jednoho vlastníka projektu, aby opravili chyby a přidali funkce. Open source projekty poskytují lepší transparentnost při vývoji a nadcházejících změnách. Open source projekty využívají příspěvky z celé komunity a podporují ekosystém open source. Navzdory rizikům Open Source mnoho spotřebitelů a přispěvatelů zjistila vhodná zmírnění rizik, která jim umožňují využívat výhody Open source ekosystému bezpečným a přiměřeným způsobem. Příklady takových rizik zahrnují licenční smlouvy přispěvatele, popisné licence, kontroly původu a podpůrné základy.

Komunita .NET zahrnuje podporu více platforem i open source. .NET Core je open source implementace rozhraní .NET pro různé platformy, která běží na spoustu platformách, včetně Windows, macOS a různých distribucí systému Linux. Xamarin poskytuje monofonní a open source verzi .NET. Mono běží na Androidu, iOS a v nejrůznějších faktorech, včetně kukátk a inteligentních televizorů. Společnost Microsoft oznámila, že [rozhraní .NET 5](https://devblogs.microsoft.com/dotnet/introducing-net-5/) bude sjednotit rozhraní .NET Core a mono do "jediného modulu .NET runtime a rozhraní, které lze použít všude a které má jednotné běhové chování a prostředí pro vývojáře".

Budou se výhody webových formulářů ASP.NET z přesunu na open source a podporu různých platforem? Odpověď, bohužel, je ne nebo alespoň ve stejném rozsahu jako zbytek platformy. Tým .NET [nedávno provedl vymazání](https://devblogs.microsoft.com/dotnet/net-core-is-the-future-of-net/) , že webové formuláře ASP.NET nebudou předáno do .NET Core nebo .NET 5. Proč je to?

V prvních dnech rozhraní .NET Core až po portování webových formulářů ASP.NET byly snahy. Bylo zjištěno, že počet požadovaných přerušujících změn je příliš závažný. K dispozici je také přístup i pro společnost Microsoft, ale omezení počtu webových rozhraní, která může podporovat souběžně. Možná někdo ve komunitě zabere v úvahu příčinu vytváření webových formulářů ASP.NET open source a pro různé platformy. [Zdrojový kód pro webové formuláře ASP.NET](https://github.com/microsoft/referencesource) byl zpřístupněn veřejně v referenčním formuláři. Ale v době, kdy se to zdá, se zdá, že webové formuláře ASP.NET zůstanou jenom pro Windows i bez Open Source modelu příspěvků. Pokud se podpora pro různé platformy nebo open source stane pro vaše scénáře důležitou, budete muset hledat něco nového.

Nejedná se tedy o neASP.NETelné webové *formuláře a neměly by se už* používat? Samozřejmě ne! Dokud je .NET Framework dodávána jako součást systému Windows, webové formuláře ASP.NET budou podporovanou architekturou. Pro mnoho vývojářů webových formulářů se nejedná o neproblémovou podporu pro různé platformy a open source. Pokud nemáte požadavek na podporu pro různé platformy, Open Source nebo jakékoli jiné nové funkce v rozhraní .NET Core nebo .NET 5, pak je ASP.NET webových formulářů v systému Windows v pořádku. Webové formuláře ASP.NET budou nadále produktivní způsob, jak psát webové aplikace po řadu let.

Ale existuje i další trend, který zvažujeme, a to je posun na klienta.

## <a name="client-side-web-development"></a>Vývoj webů na straně klienta

Vše. Webové architektury založené na síti, včetně webových formulářů ASP.NET, mají historicky jednu věc společného: jsou *vykresleny serverem*. V prohlížeči vyvykreslované webové aplikace vytvoří prohlížeč požadavek na server, který spustí nějaký kód (kód .NET v aplikacích ASP.NET) a vytvoří odpověď. Tato odpověď se pošle zpátky do prohlížeče, aby se mohla zpracovat. V tomto modelu se prohlížeč používá jako modul dynamického vykreslování. Tato pevná práce při vytváření uživatelského rozhraní, spuštění obchodní logiky a správy stavu probíhá na serveru.

Nicméně prohlížeče se stávají všestrannými platformami. Implementují neustále rostoucí počet otevřených webových standardů, které udělují přístup k schopnostem počítače uživatele. Proč nevyužít výpočetní výkon, úložiště, paměť a další prostředky klientského zařízení? Konkrétní interakce uživatelského rozhraní můžou při zpracovávání alespoň částečně nebo zcela na straně klienta těžit z bohatšího a interaktivního chování. Logika a data, která by se měla zpracovat na serveru, se pořád můžou zpracovávat na straně serveru. Je možné použít volání rozhraní Web API nebo dokonce i přes protokoly v reálném čase, jako jsou například objekty WebSockets. Tyto výhody jsou k dispozici vývojářům webu zdarma, pokud jsou ochotni psát JavaScript. Architektury uživatelského rozhraní na straně klienta, například úhlová, reakce a Vue, zjednoduší vývoj webů na straně klienta a vypěstují se v oblíbenosti. Vývojáři webových formulářů ASP.NET můžou také využít výhod využití klienta a dokonce i některé předem připravené podpory s integrovanými rozhraními JavaScript, jako je ASP.NET AJAX.

Přemostění dvou různých platforem a ekosystémů (.NET a JavaScript) ale přináší náklady. Odborné znalosti se vyžadují ve dvou paralelních světů s různými jazyky, rozhraními a nástroji. Kód a logiku nejde snadno sdílet mezi klientem a serverem, což vede k duplicitám a inženýrům. Může být také obtížné udržet si ekosystém JavaScriptu, který má historii vyvíjející se při Breakneck rychlosti. Rozhraní front-end a předvolby nástroje sestavení se rychle mění. V oboru byl zjištěn průběh od grunt po Gulp do sady Webpack a tak dále. U front-endové architektury, jako jsou jQuery, vykrojení, úhlová, reakce a Vue, došlo ke stejné restlessi. Ale v souvislosti s prohlížečem v jazyce JavaScript existuje v dané oblasti jen malá volba. To znamená, že dokud komunita webů nebude spojena a způsobila, že by *Miracle* .

## <a name="webassembly-fulfills-a-need"></a>Sestavení WebAssembly splňuje potřeby

V 2015 se k vytvoření nového otevřeného webového standardu s názvem WebAssembly přihlásili hlavní dodavatelé v prohlížeči do skupiny komunity konsorcia W3C. WebAssembly je bajtový kód pro web. Pokud můžete kód zkompilovat do webového sestavení, pak ho můžete spustit v jakémkoli prohlížeči na libovolné platformě v téměř nativní rychlosti. Počáteční úsilí se zaměřuje na CC++/. Výsledkem byla dramatická ukázka spouštění nativních 3D grafických modulů přímo v prohlížeči bez modulů plug-in. WebAssembly má od standardních a implementovaných ve všech hlavních prohlížečích standardizované a implementované.

Práce na běhu rozhraní .NET na WebAssembly byla oznámena v 2017. a očekává se dodávat v 2020, včetně podpory od rozhraní .NET 5. Možnost spouštět kód .NET přímo v prohlížeči umožňuje používat technologii .NET pro vytváření celého zásobníku.

## <a name="blazor-full-stack-web-development-with-net"></a>Blazor: vytváření celého zásobníku pro vývoj na webu pomocí .NET

Sám o sobě možnost spouštění kódu .NET v prohlížeči neposkytuje ucelené prostředí pro vytváření webových aplikací na straně klienta. To je místo, kde Blazor přichází. Blazor je rozhraní Web UI na straně klienta založené na C# jazyce místo JavaScriptu. Blazor lze spustit přímo v prohlížeči prostřednictvím webového sestavení. Nevyžadují se žádné moduly plug-in prohlížeče. Aplikace Blazor můžou taky spouštět na straně serveru .NET Core a zpracovávat všechny interakce uživatelů přes připojení v reálném čase pomocí prohlížeče.

Blazor má skvělou podporu nástrojů v aplikaci Visual Studio a Visual Studio Code. Rozhraní zahrnuje také úplný model komponenty uživatelského rozhraní a má Vestavěná zařízení pro:

- Formuláře a ověřování
- Injektáž závislostí
- Směrování na straně klienta
- Rozložení
- Ladění v prohlížeči
- Interoperabilita JavaScriptu

Blazor má hodně společného s webovými formuláři ASP.NET. Obě architektury nabízejí základní modely programování založené na událostech, které jsou založeny na komponentách. Hlavním rozdílem architektury je, že webové formuláře ASP.NET běží pouze na serveru. Blazor může běžet na klientovi v prohlížeči. Pokud ale připravujete na pozadí webových formulářů ASP.NET, je spousta Blazor, která se dobře seznámí. Blazor je přirozené řešení pro vývojáře webových formulářů ASP.NET, který hledá způsob, jak využít výhod vývoje na straně klienta a open source řešení .NET pro různé platformy.

Tato kniha poskytuje Úvod do Blazor, který je zaměřen konkrétně na vývojáře webových formulářů ASP.NET. Každý koncept Blazor je prezentován v kontextu podobných funkcí a postupů pro webové formuláře v ASP.NET. Na konci této knihy budete rozumět:

- Sestavování aplikací Blazor
- Jak Blazor funguje.
- Jak Blazor souvisí s .NET Core.
- Přiměřené strategie pro migraci stávajících aplikací ASP.NET Web Forms na Blazor, kde je to vhodné.

## <a name="get-started-with-blazor"></a>Začínáme s Blazor

Začínáme s Blazor je snadné. Přejděte na <https://blazor.net> a pomocí odkazů nainstalujte příslušné šablony projektů .NET Core SDK a Blazor. Najdete tady také pokyny pro nastavení nástrojů Blazor v aplikaci Visual Studio nebo Visual Studio Code.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[Další](architecture-comparison.md)
