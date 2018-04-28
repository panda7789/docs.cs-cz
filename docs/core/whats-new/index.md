---
title: Co je nového v rozhraní .NET 2.0 jádra
description: Další informace o nových funkcích v .NET Core nalezen.
author: rpetrusha
ms.author: ronpet
ms.date: 08/13/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: f99b053f69c4e06606cee5c78e3da7749c427e6c
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="whats-new-in-net-core"></a>Co je nového v .NET Core

.NET core 2.0 obsahuje vylepšení a nové funkce v těchto oblastech:

- [Nástrojů](#tooling)
- [Jazyková podpora](#language-support)
- [Vylepšení platformy](#platform-improvements)
- [Rozhraní API změny](#api-changes-and-library-support)
- [Integrace aplikace Visual Studio](#visual-studio-integration)
- [Dokumentace k vylepšení](#documentation-improvements)

## <a name="tooling"></a>Nástrojů

### <a name="dotnet-restore-runs-implicitly"></a>implicitně spouští obnovení DotNet.

V předchozích verzích .NET Core musely být spuštěné [dotnet obnovení](../tools/dotnet-restore.md) příkaz ke stažení závislostí ihned po vytvoření nového projektu s [dotnet nové](../tools/dotnet-new.md) příkaz, a také vždy, když jste Přidat nové závislosti do projektu.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Můžete také zakázat automatické vyvolání `dotnet restore` předáním `--no-restore` přepnout `new`, `run`, `build`, `publish`, `pack`, a `test` příkazy. 

### <a name="retargeting-to-net-core-20"></a>Změna orientace na .NET Core 2.0

Pokud je nainstalovaný .NET Core 2.0 SDK, projekty, cílí na .NET Core 1.x může být změnit cíl na necílené .NET Core 2.0.

Přesměrovat na rozhraní .NET 2.0 jádra, upravte svůj soubor projektu tak, že změníte hodnotu `<TargetFramework>` elementu (nebo `<TargetFrameworks>` elementu, pokud máte více než jeden cíl v souboru projektu) z 1.x k 2.0:

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

Můžete také změnit cíl .NET standardní knihovny pro rozhraní .NET 2.0 standardní stejným způsobem jako:

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

Další informace o migraci projektu na .NET Core 2.0 najdete v tématu [migrace z ASP.NET Core 1.x na technologii ASP.NET 2.0 základní](/aspnet/core/migration/1x-to-2x/index).

## <a name="language-support"></a>Jazyková podpora

Vedle podpory jazyka C# a F #, rozhraní .NET 2.0 základní také podporuje jazyka Visual Basic.

### <a name="visual-basic"></a>Visual Basic

Verze 2.0 .NET Core teď podporuje 2017 Visual Basic. Můžete vytvořit tyto typy projektů jazyka Visual Basic:

- Aplikace konzoly .NET core
- Knihovny tříd .NET core
- .NET standard knihovny tříd
- .NET core projektů testování částí
- .NET core xUnit testovací projekty

Například pro vytvoření aplikace Visual Basic "Hello, World", proveďte následující kroky z příkazového řádku:

1. Otevřete okno konzoly, vytvořte adresář pro svůj projekt a nastavte jej aktuální adresář.

1. Zadejte příkaz `dotnet new console -lang vb`.

   Příkaz vytvoří soubor projektu s `.vbproj` souboru příponu, společně s souboru zdrojového kódu jazyka Visual Basic, s názvem *soubor Program.vb*. Tento soubor obsahuje zdrojový kód k zápisu řetězce "Hello, World!" v okně konzoly.

1.  Zadejte příkaz `dotnet run`. [Nástrojů příkazového řádku .NET Core](../tools/index.md) automaticky zkompilování a spuštění aplikace, které zobrazí zprávu "Hello, World!" v okně konzoly.

### <a name="support-for-c-71"></a>Podpora pro jazyk C# 7.1

.NET core 2.0 podporuje 7.1 C#, který přidá číslo nové funkce, včetně:

- `Main` Metoda, vstupní bod aplikace, může být označen [asynchronní](../../csharp/language-reference/keywords/async.md) – klíčové slovo.
- Inferredname řazené kolekce členů.
- Výchozí výrazy.

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a>Vylepšení platformy

.NET core 2.0 obsahuje několik funkcí, které usnadňují instalaci .NET Core a používat na podporovaných operačních systémech.

### <a name="net-core-for-linux-is-a-single-implementation"></a>.NET core pro Linux je jediná implementace

Rozhraní .NET 2.0 základní nabízí jediná implementace Linux, který funguje na více Linuxových distribucích. .NET core 1.x vyžaduje, abyste si stáhli na konkrétní distribuční Linux implementace.

Také můžete vyvíjet aplikace, které cílí na Linux jako jeden operační systém. .NET core 1.x požadované cílové každý distribuční Linux samostatně.

### <a name="support-for-the-apple-cryptographic-libraries"></a>Podporu pro kryptografické knihovny Apple

.NET core 1.x v systému macOS požadované kryptografické knihovny OpenSSL toolkit. Rozhraní .NET 2.0 základní využívá kryptografické knihovny Apple a nevyžaduje OpenSSL, takže potřebujete už ji nainstalovat.

## <a name="api-changes-and-library-support"></a>Rozhraní API změny a podpora knihovny

### <a name="support-for-net-standard-20"></a>Podpora pro rozhraní .NET Standard 2.0

.NET Standard definuje sadu rozhraní API, která musí být k dispozici na implementace rozhraní .NET, které jsou v souladu s touto verzí standardní verzí. .NET Standard je cílena na vývojáře knihovny. Zaměřuje se na zaručit funkce, které jsou k dispozici pro knihovnu, která je cílena na verzi rozhraní .NET standardní na každou implementaci rozhraní .NET. .NET core 1.x podporuje .NET standardní verzi 1.6; na nejnovější verzi rozhraní .NET 2.0 standardní podporuje rozhraní .NET 2.0 jádra. Další informace najdete v tématu [.NET Standard](../../standard/net-standard.md).

Standardní rozhraní .NET 2.0 obsahuje více než 20 000 další rozhraní API, než byly k dispozici v standardní 1.6 .NET. Velká část to rozšířit útoku na výsledky z zařadit rozhraní API, které jsou společné pro rozhraní .NET Framework a Xamarin do .NET Standard.

Knihovny tříd rozhraní .NET 2.0 standardní lze také odkazovat knihovny tříd rozhraní .NET Framework, za předpokladu, že se volání rozhraní API, které jsou v rozhraní .NET 2.0 standardní. Žádné rekompilace knihovny rozhraní .NET Framework je povinný.

Seznam rozhraní API, které byly přidány do .NET Standard od jeho poslední verze 1.6 standardní .NET, naleznete v části [vs standardní rozhraní .NET 2.0. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

### <a name="expanded-surface-area"></a>Rozšířené útoku

Celkový počet dostupných na rozhraní .NET 2.0 jádra rozhraní API obsahuje více než se používají ve srovnání s .NET Core 1.1.

A [Windows kompatibility Pack](../porting/windows-compat-pack.md) portování z rozhraní .NET Framework se staly také mnohem jednodušší.

### <a name="support-for-net-framework-libraries"></a>Podporu pro knihovny rozhraní .NET Framework

.NET core kód můžete odkazovat na existující knihovny rozhraní .NET Framework, včetně existující balíčky NuGet. Všimněte si, že v knihovnách musí používat rozhraní API, které se nacházejí v rozhraní .NET standardní.

## <a name="visual-studio-integration"></a>integrace sady Visual Studio

Visual Studio 2017 verze 15.3 a v některých případech Visual Studio pro Mac nabízí několik významných vylepšení pro vývojáře .NET Core.

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a>Změna orientace aplikace .NET Core a .NET Standard knihovny

Pokud je nainstalovaný .NET Core 2.0 SDK, můžete změnit cíl .NET Core 1.x projektů pro rozhraní .NET Core 2.0 a .NET standardní knihovny 1.x standardní rozhraní .NET 2.0.

Přesměrovat projektu v sadě Visual Studio, otevřete **aplikace** kartě dialogovém okně Vlastnosti projektu a změňte **cílové rozhraní** hodnotu **.NET Core 2.0** nebo **Rozhraní .NET 2.0 standardní**. Můžete ji také změnit kliknutím pravým tlačítkem myši na projekt a výběrem možnosti **upravit \*souboru .csproj** možnost. Další informace najdete v tématu [Tooling](#tooling) dříve v tomto tématu.

### <a name="live-unit-testing-support-for-net-core"></a>Podpora Live Unit Testing pro .NET Core

Vždy, když upravíte kódu, Live testování částí automaticky spustí všechny testy ovlivněných jednotku na pozadí a zobrazí výsledky a pokrytí kódu v prostředí Visual Studio za provozu. Rozhraní .NET 2.0 základní teď podporuje Live testování jednotky. Dříve Live testování částí nebylo k dispozici pouze pro aplikace .NET Framework.

Další informace najdete v tématu [Live testování částí s Visual Studio 2017](/visualstudio/test/live-unit-testing) a [Live testování částí – nejčastější dotazy](/visualstudio/test/live-unit-testing-faq).

### <a name="better-support-for-multiple-target-frameworks"></a>Lepší podporu pro více rozhraní target

Pokud vytváříte projekt pro více cílové rozhraní, můžete nyní vybrat cílové platformy v nabídce nejvyšší úrovně. Na následujícím obrázku, projekt s názvem SCD1 cílem 64bitová verze Mac OS X 10.11 (`osx.10.11-x64`) a 64bitová verze Windows 10 a Windows Server 2016 (`win10-x64`). Před výběrem tlačítko projektu v tomto případě spuštění sestavení ladicí verze, můžete vybrat cílové rozhraní.

![Výběr cílové rozhraní při sestavování projektu](media/multitarget.png)

### <a name="side-by-side-support-for-net-core-sdks"></a>Souběžně sdílená podpory pro rozhraní .NET Core SDK

Nyní můžete nainstalovat rozhraní .NET Core SDK nezávisle na Visual Studio. To umožňuje jedna verze sady Visual Studio k vytvoření projektů, že cíl různé verze .NET Core. Dříve Visual Studio a .NET Core SDK byly úzce párované; konkrétní verzi sady SDK spolu s konkrétní verze sady Visual Studio.

## <a name="documentation-improvements"></a>Dokumentace k vylepšení

### <a name="net-application-architecture"></a>Architektura aplikace .NET

[Architektura aplikace .NET](https://www.microsoft.com/net/learn/architecture) dává vám přístup k sadě e publikací, které obsahují pokyny, osvědčené postupy a ukázkové aplikace, při použití rozhraní .NET k sestavení:

- Mikroslužeb a Docker kontejnerů.
- Webové aplikace s ASP.NET.
- Mobilní aplikace s funkcí Xamarin.
- Aplikace, které jsou nasazeny do cloudu s Azure.

## <a name="see-also"></a>Viz také
 [Co je nového v technologii ASP.NET 2.0 jádra](/aspnet/core/aspnetcore-2.0)
