---
title: Co je nového v .NET Core 2.0
description: Další informace o nových funkcích v rozhraní .NET Core.
ms.date: 08/13/2017
ms.openlocfilehash: 115b3adc72b6798c6a7bac9cc18044a8822808a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398830"
---
# <a name="whats-new-in-net-core-20"></a>Co je nového v .NET Core 2.0

.NET Core 2.0 obsahuje vylepšení a nové funkce v následujících oblastech:

- [Nástroje](#tooling)
- [Podpora jazyků](#language-support)
- [Vylepšení platformy](#platform-improvements)
- [Změny rozhraní API](#api-changes-and-library-support)
- [Integrace se sadou Visual Studio](#visual-studio-integration)
- [Vylepšení dokumentace](#documentation-improvements)

## <a name="tooling"></a>Nástroje

### <a name="dotnet-restore-runs-implicitly"></a>Dotnet restore běží implicitně

V předchozích verzích rozhraní .NET Core bylo možné spustit příkaz [dotnet restore](../tools/dotnet-restore.md) ke stažení závislostí ihned po vytvoření nového projektu s novým příkazem [dotnet](../tools/dotnet-new.md) a také vždy, když jste do projektu přidali novou závislost.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Automatické vyvolání `dotnet restore` můžete také zakázat `--no-restore` předáním `new`přepínače na příkazy , `run` `build`, `publish`, `pack`, a `test` příkazy.

### <a name="retargeting-to-net-core-20"></a>Opětovné zacílení na rozhraní .NET Core 2.0

Pokud je nainstalována sada .NET Core 2.0 SDK, projekty, které cílí na rozhraní .NET Core 1.x, lze znovu zacílit na .NET Core 2.0.

Chcete-li znovu zacílit na .NET Core 2.0, `<TargetFramework>` upravte `<TargetFrameworks>` soubor projektu změnou hodnoty prvku (nebo prvku, pokud máte v souboru projektu více než jeden cíl) z 1.x na 2.0:

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

Stejným způsobem můžete také znovu zacílit knihovny .NET Standard na rozhraní .NET Standard 2.0:

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

Další informace o migraci projektu do rozhraní .NET Core 2.0 naleznete [v tématu Migrace z ASP.NET jádra 1.x na ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).

## <a name="language-support"></a>Podpora jazyků

Kromě podpory Jazyka C# a F#podporuje jazyk Visual Basic také rozhraní .NET Core 2.0.

### <a name="visual-basic"></a>Visual Basic

S verzí 2.0 rozhraní .NET Core nyní podporuje visual basic 2017. Pomocí jazyka Visual Basic můžete vytvořit následující typy projektů:

- Aplikace konzoly .NET Core
- Knihovny tříd .NET Core
- Knihovny tříd .NET Standard
- Testovací projekty základní jednotky .NET
- Testovací projekty .NET Core xUnit

Chcete-li například vytvořit aplikaci "Hello World" jazyka Visual Basic, proveďte z příkazového řádku následující kroky:

1. Otevřete okno konzoly, vytvořte adresář pro projekt a vytvořte z něj aktuální adresář.

1. Zadejte `dotnet new console -lang vb`příkaz .

   Příkaz vytvoří soubor projektu `.vbproj` s příponou souboru spolu se souborem zdrojového kódu jazyka Visual Basic s názvem *Program.vb*. Tento soubor obsahuje zdrojový kód pro napsání řetězce "Hello World!" do okna konzoly.

1. Zadejte `dotnet run`příkaz . Rozhraní [příkazového příkazu .NET Core](../tools/index.md) automaticky zkompiluje a spustí aplikaci, která zobrazí zprávu "Hello World!" v okně konzoly.

### <a name="support-for-c-71"></a>Podpora pro C# 7.1

.NET Core 2.0 podporuje C# 7.1, který přidává řadu nových funkcí, včetně:

- Metoda, `Main` vstupní bod aplikace, může být označena klíčovým slovem [async.](../../csharp/language-reference/keywords/async.md)
- Odvozené názvy řazené kolekce členů.
- Výchozí výrazy.

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a>Vylepšení platformy

Rozhraní .NET Core 2.0 obsahuje řadu funkcí, které usnadňují instalaci rozhraní .NET Core a jeho použití v podporovaných operačních systémech.

### <a name="net-core-for-linux-is-a-single-implementation"></a>.NET Core pro Linux je jedna implementace

.NET Core 2.0 nabízí jednu implementaci Linuxu, která funguje na více linuxových distribucích. .NET Core 1.x vyžaduje, abyste stáhli implementaci Linuxu specifickou pro distribuci.

Můžete také vyvíjet aplikace, které cílí na Linux jako jeden operační systém. .NET Core 1.x vyžaduje, abyste cílili každou distribuci Linuxu samostatně.

### <a name="support-for-the-apple-cryptographic-libraries"></a>Podpora kryptografických knihoven Apple

.NET Core 1.x v macOS vyžadoval kryptografickou knihovnu OpenSSL toolkit. .NET Core 2.0 používá kryptografické knihovny Apple a nevyžaduje OpenSSL, takže už ho nemusíte instalovat.

## <a name="api-changes-and-library-support"></a>Změny rozhraní API a podpora knihovny

### <a name="support-for-net-standard-20"></a>Podpora pro standard .NET 2.0

Standard .NET definuje sadu rozhraní API s verzí, která musí být k dispozici v implementacích .NET, které jsou v souladu s touto verzí standardu. Standard .NET je určen pro vývojáře knihoven. Jeho cílem je zaručit funkce, které jsou k dispozici pro knihovnu, která se zaměřuje na verzi standardu .NET na každé implementaci .NET. Rozhraní .NET Core 1.x podporuje rozhraní .NET Standard verze 1.6; .NET Core 2.0 podporuje nejnovější verzi .NET Standard 2.0. Další informace naleznete v tématu [.NET Standard](../../standard/net-standard.md).

Standard .NET Standard 2.0 obsahuje více než 20 000 více rozhraní API, než bylo k dispozici ve standardu .NET Standard 1.6. Velká část této rozšířené plochy je výsledkem začlenění rozhraní API, která jsou společná pro rozhraní .NET Framework a Xamarin do standardu .NET.

Knihovny tříd .NET Standard 2.0 mohou také odkazovat na knihovny tříd rozhraní .NET Framework za předpokladu, že volají rozhraní API, která jsou přítomna ve standardu .NET Standard 2.0. Není vyžadována žádná rekompilace knihoven rozhraní .NET Framework.

Seznam rozhraní API, která byla přidána do standardu .NET od jeho poslední verze, .NET Standard 1.6, naleznete [v tématu .NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

### <a name="expanded-surface-area"></a>Rozbalené plochy

Celkový počet rozhraní API dostupných na rozhraní .NET Core 2.0 se ve srovnání s rozhraním .NET Core 1.1 více než zdvojnásobil.

A s windows [compatibility pack](../porting/windows-compat-pack.md) portování z rozhraní .NET Framework se také stala mnohem jednodušší.

### <a name="support-for-net-framework-libraries"></a>Podpora knihoven rozhraní .NET Framework

Základní kód rozhraní .NET může odkazovat na existující knihovny rozhraní .NET Framework, včetně existujících balíčků NuGet. Všimněte si, že knihovny musí používat rozhraní API, které se nacházejí v .NET Standard.

## <a name="visual-studio-integration"></a>Integrace se sadou Visual Studio

Visual Studio 2017 verze 15.3 a v některých případech Visual Studio pro Mac nabízejí řadu významných vylepšení pro vývojáře .NET Core.

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a>Opětovné cílení na aplikace .NET Core a knihovny .NET Standard

Pokud je nainstalována sada .NET Core 2.0 SDK, můžete znovu zacílit na projekty .NET Core 1.x na knihovny .NET Core 2.0 a .NET Standard 1.x na .NET Standard 2.0.

Chcete-li znovu zacílit projekt v sadě Visual Studio, otevřete kartu **Aplikace** dialogového okna vlastností projektu a změňte hodnotu **cílového rozhraní** na **.NET Core 2.0** nebo **.NET Standard 2.0**. Můžete jej také změnit kliknutím pravým tlačítkem myši na projekt a výběrem **možnosti Upravit \*soubor .csproj.** Další informace naleznete v části [Nástroje](#tooling) dříve v tomto tématu.

### <a name="live-unit-testing-support-for-net-core"></a>Podpora Live Unit Testing pro .NET Core

Kdykoli změníte kód, live testování částí automaticky spustí všechny testy ovlivněné jednotky na pozadí a zobrazí výsledky a pokrytí kódu živě v prostředí sady Visual Studio. .NET Core 2.0 nyní podporuje živé testování částí. Dříve bylo živé testování částí k dispozici pouze pro aplikace rozhraní .NET Framework.

Další informace naleznete [v tématu Živé testování částí s Visual Studio](/visualstudio/test/live-unit-testing) a nejčastější dotazy k testování [živých částí](/visualstudio/test/live-unit-testing-faq).

### <a name="better-support-for-multiple-target-frameworks"></a>Lepší podpora pro více cílových rámců

Pokud vytváříte projekt pro více cílových architektur, můžete nyní vybrat cílovou platformu z nabídky nejvyšší úrovně. Na následujícím obrázku projekt s názvem SCD1 cílí na 64bitový`osx.10.11-x64`macOS X 10.11 ( )`win10-x64`a 64bitový systém Windows 10/Windows Server 2016 ( ). Můžete vybrat cílovou architekturu před výběrem tlačítka projektu, v tomto případě spustit sestavení ladění.

![Snímek obrazovky zobrazující výběr cílového rozhraní při vytváření projektu](./media/dotnet-core-2-0/target-framework-selection.png)

### <a name="side-by-side-support-for-net-core-sdks"></a>Souběžná podpora sad SDK jádra .NET

Nyní můžete nainstalovat sdk jádra .NET nezávisle na sadě Visual Studio. To umožňuje pro jednu verzi sady Visual Studio vytvářet projekty, které cílí na různé verze .NET Core. Dříve visual studio a sada .NET Core SDK byly pevně spojeny; konkrétní verze sady SDK doprovází konkrétní verzi sady Visual Studio.

## <a name="documentation-improvements"></a>Vylepšení dokumentace

### <a name="net-application-architecture"></a>Architektura aplikace .NET

[Architektura aplikací .NET](https://dotnet.microsoft.com/learn/dotnet/architecture-guides) umožňuje přístup k sadě e-knih, které poskytují pokyny, osvědčené postupy a ukázkové aplikace při vytváření rozhraní .NET:

- [Mikroslužeb a kontejnery Dockeru](../../architecture/microservices/index.md)
- [Webové aplikace s ASP.NET](../../architecture/modern-web-apps-azure/index.md)
- [Mobilní aplikace s Xamarinem](/xamarin/xamarin-forms/enterprise-application-patterns/index)
- [Aplikace, které jsou nasazené do cloudu s Azure](/azure/architecture/reference-architectures/index)

## <a name="see-also"></a>Viz také

- [Co je nového v ASP.NET Core 2.0](/aspnet/core/aspnetcore-2.0)
