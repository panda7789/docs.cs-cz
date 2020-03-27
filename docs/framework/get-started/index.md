---
title: Začínáme s rozhraním .NET Framework
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, getting started
- getting started [.NET Framework]
ms.assetid: c693fd34-88fe-4d90-b332-19eeadf3b7e7
ms.openlocfilehash: 8708fbd21967c5acb548e0e77ba5d9e060336c50
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345047"
---
# <a name="get-started-with-net-framework"></a>Začínáme s rozhraním .NET Framework

Rozhraní .NET Framework je prostředí pro spuštění za běhu, které spravuje aplikace, které cílí na rozhraní .NET Framework. Skládá se ze společného jazyka runtime, který poskytuje správu paměti a další systémové služby, a rozsáhlé knihovny tříd, který umožňuje programátorům využít robustní, spolehlivý kód pro všechny hlavní oblasti vývoje aplikací.

> [!NOTE]
> Rozhraní .NET Framework je k dispozici pouze v systémech Windows. [Pomocí rozhraní .NET Core](../../core/index.yml) můžete vyvíjet a spouštět aplikace ve Windows, MacOS a Linuxu.

## <a name="what-is-net-framework"></a>Co je rozhraní .NET Framework?

Rozhraní .NET Framework je prostředí spravovaného spuštění systému Windows, které poskytuje různé služby pro spuštěné aplikace. Skládá se ze dvou hlavních součástí: modul CLR (COMMON Language runtime), což je modul provádění, který zpracovává spuštěné aplikace, a knihovna tříd rozhraní .NET Framework, která poskytuje knihovnu testovaného opakovaně použitelného kódu, který mohou vývojáři volat z vlastních aplikací. Mezi služby, které rozhraní .NET Framework poskytuje spuštěných aplikacím, patří následující:

- Správa paměti. V mnoha programovacích jazycích jsou programátoři zodpovědní za přidělování a uvolňování paměti a za zpracování životnosti objektů. V aplikacích rozhraní .NET Framework poskytuje CLR tyto služby jménem aplikace.

- Běžný typový systém. V tradičních programovacích jazycích jsou základní typy definovány kompilátorem, což komplikuje interoperabilitu mezi jazyky. V rozhraní .NET Framework jsou základní typy definovány systémem typu rozhraní .NET Framework a jsou společné pro všechny jazyky, které cílí na rozhraní .NET Framework.

- Rozsáhlá knihovna tříd. Místo toho, aby museli psát obrovské množství kódu pro zpracování běžných nízkoúrovňových programovacích operací, programátoři používají snadno přístupnou knihovnu typů a jejich členů z knihovny tříd rozhraní .NET Framework.

- Vývojové rámce a technologie. Rozhraní .NET Framework zahrnuje knihovny pro konkrétní oblasti vývoje aplikací, jako jsou ASP.NET pro webové aplikace, ADO.NET pro přístup k datům, Windows Communication Foundation pro aplikace orientované na služby a Windows Presentation Foundation pro desktopové aplikace pro Windows.

- Jazyková interoperabilita. Kompilátory jazyka, které cílí na rozhraní .NET Framework, vyzařují zprostředkující kód s názvem Common Intermediate Language (CIL), který je zase kompilován za běhu běžným jazykem runtime. Díky této funkci jsou rutiny napsané v jednom jazyce přístupné do jiných jazyků a programátoři se zaměřují na vytváření aplikací v preferovaných jazycích.

- Kompatibilita verzí. S výjimečnými výjimkami aplikace, které jsou vyvinuty pomocí konkrétní verze rozhraní .NET Framework spustit beze změn v novější verzi.

- Souběžné provedení. Rozhraní .NET Framework pomáhá vyřešit konflikty verzí tím, že umožňuje, aby ve stejném počítači existovalo více verzí běžného jazykového běhu. To znamená, že více verzí aplikací může existovat společně a že aplikace může běžet ve verzi rozhraní .NET Framework, se kterým byla vytvořena. Souběžné spuštění platí pro skupiny verzí rozhraní .NET Framework 1.0/1.1, 2.0/3.0/3.5 a 4/4.5.x/4.6.x/4.7.x/4.7.x/4.8.

- Multitargeting. Cílením [na rozhraní .NET Standard](../../standard/net-standard.md)vytvářejí vývojáři knihovny tříd, které pracují na více platformách rozhraní .NET Framework podporovaných toto unormy. Například knihovny, které cílí na standard .NET Standard 2.0, mohou používat aplikace, které cílí na rozhraní .NET Framework 4.6.1, .NET Core 2.0 a UWP 10.0.16299.

<a name="ForUsers"></a>
## <a name="the-net-framework-for-users"></a>Rozhraní .NET Framework pro uživatele

Pokud nevyvíjíte aplikace rozhraní .NET Framework, ale používáte je, nemusíte mít konkrétní znalosti o rozhraní .NET Framework nebo jeho provozu. Z větší části je rámec pro uživatele zcela transparentní.

Pokud používáte operační systém Windows, rozhraní .NET Framework již může být v počítači nainstalováno. Kromě toho pokud nainstalujete aplikaci, která vyžaduje rozhraní .NET Framework, instalační program aplikace může nainstalovat konkrétní verzi rozhraní do počítače. V některých případech se může zobrazit dialogové okno s dotazem na instalaci rozhraní .NET Framework. Pokud jste se právě pokusili spustit aplikaci, když se zobrazí toto dialogové okno a pokud má váš počítač přístup k internetu, můžete přejít na webovou stránku, která vám umožní nainstalovat chybějící verzi rozhraní .NET Framework. Další informace naleznete v [příručce k instalaci](../install/index.md).

Obecně byste neměli odinstalovat verze rozhraní .NET Framework, které jsou nainstalovány v počítači. To má dva důvody:

- Pokud aplikace, kterou používáte, závisí na konkrétní verzi rozhraní .NET Framework, může se tato aplikace přerušit, pokud je tato verze odebrána.

- Některé verze rozhraní .NET Framework jsou na místě aktualizace dřívějších verzí. Například rozhraní .NET Framework 3.5 je aktualizace na místě verze 2.0 a rozhraní .NET Framework 4.8 je aktualizace na místě pro verze 4 až 4.7.2. Další informace naleznete [v tématu verze rozhraní .NET Framework a závislosti](../migration-guide/versions-and-dependencies.md).

Pokud se ve verzích systému Windows před systémem Windows 8 rozhodnete odebrat rozhraní .NET Framework, odinstalujte ji vždy pomocí **programů a funkcí** z Ovládacích panelů. Nikdy neodstraňujte verzi rozhraní .NET Framework ručně. V systému Windows 8 a vyšší, .NET Framework je součást operačního systému a nelze nezávisle odinstalovat.

Více verzí rozhraní .NET Framework může existovat současně v jednom počítači. To znamená, že k instalaci novější verze není nutné odinstalovat předchozí verze.

## <a name="net-framework-for-developers"></a>Rozhraní .NET Framework pro vývojáře

Pokud jste vývojář, zvolte libovolný programovací jazyk, který podporuje rozhraní .NET Framework a vytvořte aplikace. Vzhledem k tomu, že rozhraní .NET Framework poskytuje nezávislost jazyka a interoperabilitu, můžete pracovat s jinými aplikacemi a součástmi rozhraní .NET Framework bez ohledu na jazyk, se kterým byly vyvinuty.

Chcete-li vyvíjet aplikace nebo součásti rozhraní .NET Framework, postupujte takto:

1. Pokud není předinstalován v operačním systému, nainstalujte verzi rozhraní .NET Framework, na kterou bude vaše aplikace cílit. Nejnovější produkční verze je rozhraní .NET Framework 4.8. Je předinstalován v aktualizaci Windows 10 Květen 2019 Update a je k dispozici ke stažení v dřívějších verzích operačního systému Windows. Požadavky na systém rozhraní .NET Framework naleznete v [tématu Systémové požadavky](system-requirements.md). Informace o instalaci jiných verzí rozhraní .NET Framework naleznete v [příručce k instalaci](../install/guide-for-developers.md). Další balíčky rozhraní .NET Framework jsou uvolněny mimo pásmo, což znamená, že jsou vydávány na základě postupného mimo jakýkoli běžný nebo plánovaný cyklus vydání. Informace o těchto balíčcích naleznete [v tématu .NET Framework a Out-of-Band Releases](the-net-framework-and-out-of-band-releases.md).

2. Vyberte jazyk nebo jazyky podporované verzí rozhraní .NET Framework, které chcete použít k vývoji aplikací. K dispozici je řada jazyků, včetně [jazyka Visual Basic](../../visual-basic/index.yml), [C#](../../csharp/index.yml), [F#](../../fsharp/index.yml)a [C++/CLI](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) od společnosti Microsoft. (Programovací jazyk, který umožňuje vyvíjet aplikace pro rozhraní .NET Framework, dodržuje [specifikaci ClI (Common Language Infrastructure).](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/)

3. Vyberte a nainstalujte vývojové prostředí, které chcete použít k vytvoření aplikací a které podporuje vybraný programovací jazyk nebo jazyky. Integrované vývojové prostředí (IDE) společnosti Microsoft pro aplikace rozhraní .NET Framework je [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Je k dispozici v několika vydáních.

Další informace o vývoji aplikací, které cílí na rozhraní .NET Framework, naleznete v [Průvodci vývojem](../development-guide.md).

## <a name="related-articles"></a>Související články

| Nadpis | Popis |
| ----- |------------ |
| [Přehled](overview.md) | Obsahuje podrobné informace pro vývojáře, kteří vytvářejí aplikace, které cílí na rozhraní .NET Framework. |
| [Průvodce instalací](../install/index.md) | Obsahuje informace o instalaci rozhraní .NET Framework. |  
| [Rozhraní .NET Framework a nepásmová vydání](the-net-framework-and-out-of-band-releases.md) | Popisuje neintegrované verze rozhraní .NET Framework a jejich použití ve vaší aplikaci. |
| [Systémové požadavky](system-requirements.md) | Uvádí požadavky na hardware a software pro spuštění rozhraní .NET Framework. |
| [.NET Core a open source](net-core-and-open-source.md) | Popisuje rozhraní .NET Core ve vztahu k rozhraní .NET Framework a přístup k projektům open source .NET Core. |
| [Základní dokumentace rozhraní .NET](../../core/index.yml) | Obsahuje dokumentaci ke koncepčním a referenčním dokumentům rozhraní API pro službu .NET Core. |
| [.NET Standard](../../standard/net-standard.md) | Popisuje .NET Standard, specifikace s verzí, kterou jednotlivé implementace rozhraní .NET podporují, aby bylo zaručeno, že konzistentní sada rozhraní API je k dispozici na více platformách.

## <a name="see-also"></a>Viz také

- [Průvodce rozhraním .NET Framework](../index.yml)
- [Co je nového](../whats-new/index.md)
- [Prohlížeč rozhraní API pro .NET](../../../api/index.md)
- [Průvodce vývojem](../development-guide.md)
