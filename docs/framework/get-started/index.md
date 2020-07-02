---
title: Začínáme s .NET Framework
description: Začněte s .NET, což je běhové prostředí modulu runtime, které spravuje aplikace. Obsahuje modul CLR (Common Language Runtime) a rozsáhlou knihovnu tříd.
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, getting started
- getting started [.NET Framework]
ms.assetid: c693fd34-88fe-4d90-b332-19eeadf3b7e7
ms.openlocfilehash: b6ad74d2984443a3b8345c2261996e7ab30acdff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621649"
---
# <a name="get-started-with-net-framework"></a>Začínáme s .NET Framework

.NET Framework je běhové prostředí, které spravuje aplikace, které cílí na .NET Framework. Skládá se z modulu CLR (Common Language Runtime), který poskytuje správu paměti a další systémové služby a rozsáhlou knihovnu tříd, která programátorům umožňuje využít robustní a spolehlivý kód pro všechny hlavní oblasti vývoje aplikací.

> [!NOTE]
> .NET Framework je k dispozici pouze v systémech Windows. Pomocí [.NET Core](../../core/index.yml) můžete vyvíjet a spouštět aplikace v systémech Windows, MacOS a Linux.

## <a name="what-is-net-framework"></a>Co je .NET Framework?

.NET Framework je spravované spouštěcí prostředí pro Windows, které poskytuje různé služby pro své běžící aplikace. Skládá se ze dvou hlavních součástí: modulu CLR (Common Language Runtime), což je spouštěcí modul, který zpracovává spuštěné aplikace, a .NET Framework knihovny tříd, která poskytuje knihovnu testovaného a opakovaně použitelného kódu, který mohou vývojáři volat ze svých vlastních aplikací. Služby, které .NET Framework poskytují ke spouštění aplikací, zahrnují následující:

- Správa paměti. V řadě programovacích jazyků jsou programátory odpovědni za přidělování a uvolňování paměti a pro zpracování životnosti objektů. V .NET Framework aplikace poskytuje CLR tyto služby jménem aplikace.

- Společný systém typů. V tradičních programovacích jazycích jsou základní typy definovány kompilátorem, což ztěžuje vzájemnou funkční spolupráci mezi jazyky. V .NET Framework jsou základní typy definovány systémem .NET Framework typu a jsou společné pro všechny jazyky, které cílí .NET Framework.

- Rozsáhlá knihovna tříd. Místo toho, abyste museli zapisovat velké množství kódu pro zpracování běžných programovacích operací nízké úrovně, programátoři používají snadno dostupnou knihovnu typů a jejich členů z knihovny tříd .NET Framework.

- Vývojové architektury a technologie. .NET Framework jsou knihovny pro konkrétní oblasti vývoje aplikací, jako je například ASP.NET pro webové aplikace, ADO.NET pro přístup k datům, Windows Communication Foundation pro aplikace orientované na služby a Windows Presentation Foundation pro desktopové aplikace pro Windows.

- Vzájemná funkční spolupráce jazyka. Kompilátory jazyka, které cílí na .NET Framework emitují Mezikód s názvem Common Intermediate Language (CIL), který je zase zkompilován za běhu modulem CLR (Common Language Runtime). Pomocí této funkce jsou rutiny napsané v jednom jazyce dostupné ostatním jazykům a programátoři se zaměřují na vytváření aplikací v jejich preferovaných jazycích.

- Kompatibilita verzí. Aplikace, které jsou vyvíjené pomocí konkrétní verze .NET Framework v novější verzi, se budou spouštět beze změny.

- Souběžné spouštění. .NET Framework pomáhá vyřešit konflikty verzí tím, že v jednom počítači existuje více verzí modulu CLR (Common Language Runtime). To znamená, že více verzí aplikací může existovat současně a aplikace může běžet ve verzi .NET Framework, se kterou byla sestavena. Souběžné spouštění se vztahuje na skupiny .NET Framework verzí 1.0/1.1, 2.0/3.0/3.5 a 4/4.5. x/4.6. x/1,4. x/4.8.

- Cílení na více verzí. Díky cílení [.NET Standard](../../standard/net-standard.md)vývojářům vytvářet knihovny tříd, které pracují na více .NET Frameworkch platformách, které podporuje tato verze standardu. Knihovny, které cílí na .NET Standard 2,0, můžete například použít v aplikacích, které cílí na .NET Framework 4.6.1, .NET Core 2,0 a UWP 10.0.16299.

<a name="ForUsers"></a>
## <a name="the-net-framework-for-users"></a>.NET Framework pro uživatele

Pokud nevyvíjíte .NET Framework aplikace, ale použijete je, nemusíte mít konkrétní znalosti o .NET Framework nebo jeho fungování. Ve většině případů je rozhraní pro uživatele zcela transparentní.

Pokud používáte operační systém Windows, .NET Framework v počítači už možná máte nainstalovanou. Kromě toho, pokud instalujete aplikaci, která vyžaduje .NET Framework, instalační program aplikace může nainstalovat určitou verzi rozhraní .NET Framework v počítači. V některých případech se může zobrazit dialogové okno, které vás vyzve k instalaci .NET Framework. Pokud jste se pokusili spustit aplikaci pouze v případě, že se zobrazí toto dialogové okno a počítač má přístup k Internetu, můžete přejít na webovou stránku, která vám umožní nainstalovat chybějící verzi .NET Framework. Další informace najdete v [instalační příručce](../install/index.md).

Obecně platí, že byste neměli odinstalovat verze .NET Framework, které jsou nainstalovány na vašem počítači. To má dva důvody:

- Pokud aplikace, kterou používáte, závisí na konkrétní verzi .NET Framework, může se tato aplikace při odebrání této verze poškodit.

- Některé verze .NET Framework jsou místní aktualizace na starší verze. Například .NET Framework 3,5 je místní aktualizace verze 2,0 a .NET Framework 4,8 je místní aktualizace na verze 4 až 4.7.2. Další informace najdete v tématu [.NET Framework verze a závislosti](../migration-guide/versions-and-dependencies.md).

Pokud se v systému Windows před Windows 8 rozhodnete .NET Framework odebrat, odinstalujte je vždycky pomocí **programů a funkcí** z ovládacích panelů. Nikdy neodstraňujte verzi .NET Framework ručně. Ve Windows 8 a novějších verzích je .NET Framework součástí operačního systému a nedá se nezávisle odinstalovat.

V jednom počítači může současně existovat více verzí .NET Framework současně. To znamená, že není nutné odinstalovat předchozí verze, aby bylo možné nainstalovat novější verzi.

## <a name="net-framework-for-developers"></a>.NET Framework pro vývojáře

Pokud jste vývojář, vyberte programovací jazyk, který podporuje .NET Framework k vytváření aplikací. Vzhledem k tomu, že .NET Framework poskytuje nezávislost a interoperabilitu jazyka, můžete pracovat s ostatními .NET Framework aplikacemi a komponentami bez ohledu na jazyk, ve kterém byly vyvinuté.

Pokud chcete vyvíjet .NET Framework aplikace nebo komponenty, udělejte toto:

1. Pokud není předinstalována v operačním systému, nainstalujte verzi .NET Framework, na kterou bude vaše aplikace cílit. Nejnovější produkční verze je .NET Framework 4,8. Je předinstalována ve Windows 10 Květen 2019 Update a je dostupná ke stažení v dřívějších verzích operačního systému Windows. Požadavky na systém .NET Framework najdete v tématu [požadavky na systém](system-requirements.md). Informace o instalaci jiných verzí .NET Framework najdete v [Průvodci instalací](../install/guide-for-developers.md)nástroje. Další balíčky .NET Framework jsou vydány mimo pásmo, což znamená, že jsou vydávány na základě provozu mimo jakýkoli pravidelný nebo plánovaný cyklus vydaných verzí. Informace o těchto balíčcích najdete v tématu [.NET Framework a vzdálené verze](the-net-framework-and-out-of-band-releases.md).

2. Vyberte jazyky, které podporuje .NET Framework verze, kterou máte v úmyslu použít k vývoji aplikací. K dispozici je řada jazyků, včetně [Visual Basic](../../visual-basic/index.yml), [C#](../../csharp/index.yml), [F #](../../fsharp/index.yml)a [C++/CLI](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) od Microsoftu. (Programovací jazyk, který umožňuje vývoj aplikací pro .NET Framework dodržuje [specifikace Common Language Infrastructure (CLI)](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/).)

3. Vyberte a nainstalujte vývojové prostředí, které chcete použít k vytvoření aplikací a který podporuje vybraný programovací jazyk nebo jazyky. Integrované vývojové prostředí (IDE) Microsoftu pro aplikace .NET Framework je [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Je k dispozici v řadě edicí.

Další informace o vývoji aplikací, které cílí na .NET Framework, najdete v [příručce pro vývoj](../development-guide.md).

## <a name="related-articles"></a>Související články

| Nadpis | Popis |
| ----- |------------ |
| [Přehled](overview.md) | Poskytuje podrobné informace pro vývojáře, kteří vytvářejí aplikace, které cílí na .NET Framework. |
| [Průvodce instalací](../install/index.md) | Poskytuje informace o instalaci .NET Framework. |  
| [.NET Framework a vzdálené verze](the-net-framework-and-out-of-band-releases.md) | V této části najdete popis .NET Framework vzdáleně vydaných verzí a jejich použití ve vaší aplikaci. |
| [Požadavky na systém](system-requirements.md) | Uvádí požadavky na hardware a software pro provozování .NET Framework. |
| [.NET Core a open source](net-core-and-open-source.md) | Popisuje .NET Core v souvislosti s .NET Framework a přístup k otevřeným zdrojovým projektům .NET Core. |
| [Dokumentace k .NET Core](../../core/index.yml) | Poskytuje koncepční referenční dokumentaci rozhraní API pro .NET Core. |
| [.NET Standard](../../standard/net-standard.md) | Popisuje .NET Standard, specifikaci s verzí, kterou jednotlivé implementace rozhraní .NET podporují, aby bylo zaručeno, že konzistentní sada rozhraní API je k dispozici na různých platformách.

## <a name="see-also"></a>Viz také:

- [Průvodce rozhraním .NET Framework](../index.yml)
- [Co je nového](../whats-new/index.md)
- [Prohlížeč rozhraní .NET API](../../../api/index.md)
- [Průvodce vývojem](../development-guide.md)
