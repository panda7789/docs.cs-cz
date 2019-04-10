---
title: Začínáme s rozhraním .NET Framework
ms.custom: updateeachrelease
ms.date: 04/10/2018
helpviewer_keywords:
- .NET Framework, getting started
- getting started [.NET Framework]
ms.assetid: c693fd34-88fe-4d90-b332-19eeadf3b7e7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6604beca5c0031b55fc22fc48e0c23d27c8a37e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314968"
---
# <a name="get-started-with-the-net-framework"></a>Začínáme s rozhraním .NET Framework

Rozhraní .NET Framework je spouštěcí běhové prostředí, který spravuje aplikace, které se zaměřují rozhraní .NET Framework. Zahrnuje modul common language runtime, která poskytuje správu paměti a jiných služeb system a rozsáhlé knihovny tříd umožňující programátorům využívat robustní spolehlivý kód pro všechny hlavní oblasti vývoje aplikací.

> [!NOTE] 
> Rozhraní .NET Framework je k dispozici pouze v systémech Windows. Můžete použít [.NET Core](../../core/index.md) ke spuštění aplikace ve Windows, MacOS a Linuxu. 

<a name="Introducing"></a>
## <a name="what-is-the-net-framework"></a>Co je rozhraní .NET Framework?

Rozhraní .NET Framework je prostředí řízeného spouštění pro Windows, která poskytuje celou řadu služeb jeho spuštěné aplikace. Se skládá ze dvou hlavních částí: modul CLR (CLR), což je spouštěcí nástroj, který řídí spouštěné aplikace a knihovny tříd .NET Framework, která poskytuje knihovnu, testovat, opakovaně použitelný kód, který vývojáři mohou volat ze své vlastní aplikace. Služby, které rozhraní .NET Framework poskytuje pro spouštění aplikací patří:

- Správa paměti. V mnoha programovacích jazycích programátoři zodpovídají za přidělení a uvolnění paměti a správu životnosti objektů. V aplikacích rozhraní .NET Framework poskytuje CLR tyto služby namísto aplikace.

- Systém společných typů. V tradičních programovacích jazycích jsou základní typy definovány kompilátorem, což ztěžuje interoperabilitu mezi jazyky. Základní typy v rozhraní .NET Framework, jsou definovány systémem typů rozhraní .NET Framework a jsou společné pro všechny jazyky, které se zaměřují na rozhraní .NET Framework.

- Rozsáhlá knihovna tříd. Namísto nutnosti psát velký objem kódu pro zpracování běžných programovacích operací nízké úrovně, programátoři používají snadno přístupnou knihovnu typů a jejich členů z knihovny tříd rozhraní .NET Framework.

- Vývojové rámce a technologie. Rozhraní .NET Framework obsahuje knihovny pro konkrétní oblasti vývoje aplikací, jako je například technologie ASP.NET pro webové aplikace, ADO.NET pro přístup k datům, Windows Communication Foundation pro aplikace orientované na služby a aplikace klasické pracovní plochy Windows Presentation Foundation pro Windows.

- Vzájemná funkční spolupráce jazyka. Kompilátory, které jsou cíleny rozhraní .NET Framework, generují zprostředkující kód s názvem Common Intermediate Language (CIL), který je zase kompilován za běhu modulem common language runtime. S touto funkcí jsou přístupné pro ostatní jazyky a programátoři soustředit na vytváření aplikací v jejich mateřštině upřednostňované rutiny v jednom jazyce.

- Kompatibilita verzí. Se vzácnými výjimkami mohou aplikace, které jsou vyvíjeny pomocí konkrétní verzi rozhraní .NET Framework spuštěny bez úprav na novější verzi.

- Spuštění vedle sebe. Rozhraní .NET Framework pomáhá řešit konflikty verzí povolením více verzí modul common language runtime existovat ve stejném počítači. To znamená, že více verzí aplikace mohou existovat vedle sebe a spuštění aplikace na verzi rozhraní .NET Framework, pomocí kterého byla vytvořena. Spuštění vedle sebe platí pro skupiny verze rozhraní .NET Framework 1.0/1.1, 2.0/3.0/3.5 a 4/4.5.x/4.6.x/4.7.x.

- Cílení na více verzí. Pomocí cílení na [.NET Standard](../../standard/net-standard.md), vývojáři vytvoření knihovny tříd, které fungují na více platformách rozhraní .NET Framework nepodporuje danou verzi standard. Například je možné aplikace, které jsou cíleny rozhraní .NET Framework 4.6.1, .NET Core 2.0 a UPW 10.0.16299 knihovny cílené na .NET Standard 2.0. 

<a name="ForUsers"></a>
## <a name="the-net-framework-for-users"></a>Rozhraní .NET Framework pro uživatele

Pokud není při vývoji aplikací rozhraní .NET Framework, ale je používáte, není nutné mít specifické znalosti o rozhraní .NET Framework nebo jeho provozu. Ve většině případů je rozhraní .NET Framework pro uživatele zcela transparentní.

Pokud používáte operační systém Windows, rozhraní .NET Framework mohou již být nainstalováno ve vašem počítači. Kromě toho pokud instalujete aplikaci vyžadující rozhraní .NET Framework, instalační program aplikace nainstalovat určitou verzi rozhraní .NET Framework v počítači. V některých případech se může zobrazit dialogové okno s výzvou k instalaci rozhraní .NET Framework. Pokud jste právě zkusili spustit aplikaci, když se zobrazí toto dialogové okno a pokud má počítač přístup k Internetu, můžete přejít na webovou stránku, která vám umožní nainstalovat chybějící verzi rozhraní .NET Framework. Další informace najdete v tématu [Průvodce instalací](../install/index.md).

Obecně platí že byste neměli odinstalovávat verze rozhraní .NET Framework, které jsou nainstalovány ve vašem počítači. Existují dva důvody:

- Pokud aplikaci, kterou použijete, závisí na konkrétní verzi rozhraní .NET Framework, tato aplikace může přerušit, pokud je verze odebrána.

- Některé verze rozhraní .NET Framework jsou místní aktualizace na starší verze. Například [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] je místní aktualizace na verzi 2.0 a rozhraní .NET Framework 4.7.2 je místní aktualizace pro verze 4 až 4.7.1. Další informace najdete v tématu [verze rozhraní .NET Framework a závislosti](../migration-guide/versions-and-dependencies.md).

Na verze Windows starší než Windows 8, pokud se rozhodnete k odebrání rozhraní .NET Framework, vždy použijte **programy a funkce** z ovládacích panelů k jeho odinstalaci. Nikdy ručně odebrat verzi rozhraní .NET Framework. V systému Windows 8 a novější verze rozhraní .NET Framework je součástí operačního systému a nedá se odinstalovat nezávisle na sobě.

Všimněte si, že více verzí rozhraní .NET Framework mohou existovat vedle sebe v jednom počítači ve stejnou dobu. To znamená, že není nutné odinstalovat předchozí verze před instalací novější verze.

<a name="ForDevelopers"></a> 
## <a name="the-net-framework-for-developers"></a>Rozhraní .NET Framework pro vývojáře

Pokud jste vývojář, zvolte programovací jazyk, který podporuje rozhraní .NET Framework pro vytváření aplikací. Vzhledem k tomu, že rozhraní .NET Framework poskytuje jazykovou nezávislost a interoperabilitu, budete moct používat jiné aplikace rozhraní .NET Framework a komponenty bez ohledu na jazyk, se kterou byly vyvinuty.

K vývoji aplikací rozhraní .NET Framework nebo součástí, postupujte takto:

1. Pokud není předinstalován v operačním systému, instalace verze rozhraní .NET Framework, které vaše aplikace bude cílit. Nejnovější verze výroby je rozhraní .NET Framework 4.7.2. Je předinstalován v systému Windows 10. dubna 2018 Update a Windows 10. října 2018 aktualizací a je k dispozici ke stažení ve starších verzích operačního systému Windows. Požadavky na systém rozhraní .NET Framework, naleznete v tématu [požadavky na systém](system-requirements.md). Informace o instalaci jiných verzí rozhraní .NET Framework najdete v tématu [Průvodce instalací](../install/guide-for-developers.md). Další balíčky rozhraní .NET Framework jsou vydány mimo pásmo, což znamená, že jejich uvedení na trh na základě postupné mimo jakékoli pravidelné ani do plánovaných vývojového cyklu. Informace týkající se těchto balíčků naleznete v tématu [The .NET Framework a vydání Out-of-Band](the-net-framework-and-out-of-band-releases.md).

2. Vyberte jazyk nebo jazyky podporované rozhraním .NET Framework, kterou chcete použít pro vývoj aplikací. Počet jazyků, jsou k dispozici, včetně [jazyka Visual Basic](../../visual-basic/index.md), [ C# ](../../csharp/index.md), [ F# ](../../fsharp/index.md), a [ C++vyhodnocovací](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) z Společnosti Microsoft. (Programovací jazyk, který umožňuje vývoj aplikací pro rozhraní .NET Framework používá [společné jazykové infrastruktury (CLI) specifikace](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/).)

3. Vybrat a nainstalovat vývojové prostředí pro použití k vytvoření své aplikace a, který podporuje vybraný programovací jazyk nebo jazyky. Microsoft integrované vývojové prostředí (IDE) pro aplikace rozhraní .NET Framework je [sady Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Je k dispozici v různých edicích.

Další informace o vývoji aplikací určených pro rozhraní .NET Framework, najdete v článku [Příručka pro vývojáře](../development-guide.md).

## <a name="related-topics"></a>Související témata

| Název | Popis |
| ----- |------------ |
| [Přehled](overview.md) | Poskytuje podrobné informace pro vývojáře, kteří vytvářejí aplikace, které se zaměřují rozhraní .NET Framework. |
| [Průvodce instalací](../install/index.md) | Obsahuje informace o instalaci rozhraní .NET Framework. |  
| [Rozhraní .NET Framework a nesvázaná vydání](the-net-framework-and-out-of-band-releases.md) | Popisuje mimo obsluhy vzdálené správy verzí a jejich použití ve vaší aplikaci rozhraní .NET Framework. |
| [Požadavky na systém](system-requirements.md) | Uvádí požadavky na hardware a software pro spuštěné rozhraní .NET Framework. |
| [.NET Core a open source](net-core-and-open-source.md) | Popisuje .NET Core ve vztahu k rozhraní .NET Framework a jak získat přístup k open source projektů .NET Core. |
| [Dokumentace k .NET core](../../core/index.md) | Poskytuje koncepční a referenční dokumentace rozhraní API pro .NET Core. |
| [.NET Standard](../../standard/net-standard.md) | Tento článek popisuje .NET Standard, označené verzí specifikace, které podporují jednotlivé implementace .NET zajistit, že jsou k dispozici na několika platformách konzistentní sadu rozhraní API.

## <a name="see-also"></a>Viz také:

- [Průvodce rozhraním .NET Framework](../index.md)
- [Co je nového](../whats-new/index.md)
- [Prohlížeč rozhraní API pro .NET](../../../api/index.md)
- [Průvodce vývojem](../development-guide.md)
