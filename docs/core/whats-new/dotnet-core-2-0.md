---
title: Co je nového v .NET Core 2.0
description: Přečtěte si o nových funkcích, které najdete v .NET Core.
author: rpetrusha
ms.author: ronpet
ms.date: 08/13/2017
ms.openlocfilehash: c208f565bebedc06e244de1f6554129f21c77b8c
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849932"
---
# <a name="whats-new-in-net-core-20"></a>Co je nového v .NET Core 2.0

.NET Core 2,0 obsahuje vylepšení a nové funkce v následujících oblastech:

- [Nástroje](#tooling)
- [Podpora jazyků](#language-support)
- [Vylepšení platformy](#platform-improvements)
- [Změny rozhraní API](#api-changes-and-library-support)
- [Integrace sady Visual Studio](#visual-studio-integration)
- [Vylepšení dokumentace](#documentation-improvements)

## <a name="tooling"></a>Nástroje

### <a name="dotnet-restore-runs-implicitly"></a>dotnet restore se spouští implicitně.

V předchozích verzích .NET Core jste museli spustit příkaz [dotnet Restore](../tools/dotnet-restore.md) pro stahování závislostí hned po vytvoření nového projektu pomocí příkazu [dotnet New](../tools/dotnet-new.md) a také při každém přidání nové závislosti do projektu.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Automatické `dotnet restore` vyvolání `test` můžete také zakázat `--no-restore` předáním přepínače `new` `run` dopříkazů`build`,, `pack`,, a. `publish`

### <a name="retargeting-to-net-core-20"></a>Změna cílení na .NET Core 2,0

Pokud je nainstalovaná sada .NET Core 2,0 SDK, projekty, jejichž cílem je .NET Core 1. x, se dají změnit na .NET Core 2,0.

Chcete-li změnit cílení na .NET Core 2,0, upravte soubor projektu změnou hodnoty `<TargetFramework>` elementu (nebo prvku, `<TargetFrameworks>` Pokud máte více než jeden cíl v souboru projektu) od 1. x do 2,0:

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

Můžete také změnit cílení knihoven .NET Standard .NET Standard 2,0 stejným způsobem:

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

Další informace o migraci projektu na rozhraní .NET Core 2,0 naleznete v tématu [migrace z ASP.NET Core 1. x na ASP.NET Core 2,0](/aspnet/core/migration/1x-to-2x/index).

## <a name="language-support"></a>Podpora jazyků

Kromě podpory C# a F#podporuje .net Core 2,0 také Visual Basic.

### <a name="visual-basic"></a>Visual Basic

S verzí 2,0 teď .NET Core podporuje Visual Basic 2017. Pomocí Visual Basic můžete vytvořit následující typy projektů:

- Aplikace konzoly .NET Core
- Knihovny tříd .NET Core
- .NET Standard knihovny tříd
- Projekty testů jednotek .NET Core
- Projekty testů .NET Core xUnit

Chcete-li například vytvořit Visual Basic aplikaci "Hello World", proveďte následující kroky z příkazového řádku:

1. Otevřete okno konzoly, vytvořte adresář pro váš projekt a nastavte jej jako aktuální adresář.

1. Zadejte příkaz `dotnet new console -lang vb`.

   Příkaz vytvoří soubor projektu s `.vbproj` příponou souboru společně se souborem zdrojového kódu Visual Basic s názvem *program. vb*. Tento soubor obsahuje zdrojový kód pro zápis řetězce "Hello World!". do okna konzoly.

1. Zadejte příkaz `dotnet run`. [.NET Core CLI](../tools/index.md) automaticky zkompiluje a spustí aplikaci, která zobrazí zprávu "Hello World!". v okně konzoly.

### <a name="support-for-c-71"></a>Podpora pro C# 7,1

.NET Core 2,0 podporuje C# 7,1, který přidává řadu nových funkcí, včetně:

- Metodu, vstupní bod aplikace, lze označit pomocí klíčového slova [Async.](../../csharp/language-reference/keywords/async.md) `Main`
- Odvoditelné názvy řazené kolekce členů.
- Výchozí výrazy.

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a>Vylepšení platformy

.NET Core 2,0 obsahuje řadu funkcí, které usnadňují instalaci .NET Core a jejich použití v podporovaných operačních systémech.

### <a name="net-core-for-linux-is-a-single-implementation"></a>.NET Core pro Linux je jediná implementace.

.NET Core 2,0 nabízí jednu implementaci Linux, která funguje na více distribucích systému Linux. Rozhraní .NET Core 1. x vyžaduje stažení implementace Linux specifické pro distribuci.

Můžete také vyvíjet aplikace, které se zaměřují na Linux jako jeden operační systém. .NET Core 1. x vyžaduje, abyste každou distribuci systému Linux zacíleni samostatně.

### <a name="support-for-the-apple-cryptographic-libraries"></a>Podpora pro knihovny šifrování Apple

.NET Core 1. x v macOS vyžadovala knihovnu kryptografických knihoven sady OpenSSL Toolkit. .NET Core 2,0 používá kryptografické knihovny Apple a nevyžaduje OpenSSL, takže už je nemusíte instalovat.

## <a name="api-changes-and-library-support"></a>Změny rozhraní API a podpora knihoven

### <a name="support-for-net-standard-20"></a>Podpora pro .NET Standard 2,0

.NET Standard definuje sadu rozhraní API s verzí, která musí být k dispozici v implementacích .NET, které vyhovují této verzi standardu. .NET Standard je cílena na vývojáře knihovny. Cílem je zaručit funkčnost, která je k dispozici pro knihovnu, která cílí na verzi .NET Standard v každé implementaci rozhraní .NET. .NET Core 1. x podporuje .NET Standard verze 1,6; .NET Core 2,0 podporuje nejnovější verzi .NET Standard 2,0. Další informace najdete v tématu [.NET Standard](../../standard/net-standard.md).

.NET Standard 2,0 obsahuje více než 20 000 více rozhraní API, než bylo k dispozici v .NET Standard 1,6. Většina této rozšířené oblasti plochy je výsledkem zahrnutí rozhraní API, která jsou společná pro .NET Framework a Xamarin do .NET Standard.

Knihovny tříd .NET Standard 2,0 také mohou odkazovat .NET Framework knihovny tříd za předpokladu, že volají rozhraní API, která jsou přítomna v .NET Standard 2,0. Nevyžadují se žádná opětovná kompilace knihoven .NET Framework.

Seznam rozhraní API přidaných do .NET Standard od poslední verze .NET Standard 1,6 najdete v tématu [.NET Standard 2,0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

### <a name="expanded-surface-area"></a>Rozbalená oblast povrchu

Celkový počet rozhraní API dostupných v .NET Core 2,0 má více než dvojitou přesnost v porovnání s rozhraním .NET Core 1,1.

A se sadou [Windows Compatibility Pack](../porting/windows-compat-pack.md) pro přenos z .NET Framework se taky zjednodušilo mnohem jednodušší.

### <a name="support-for-net-framework-libraries"></a>Podpora pro knihovny .NET Framework

Kód .NET Core může odkazovat na existující knihovny .NET Framework, včetně existujících balíčků NuGet. Všimněte si, že knihovny musí používat rozhraní API, které najdete v .NET Standard.

## <a name="visual-studio-integration"></a>integrace sady Visual Studio

Visual Studio 2017 verze 15,3 a v některých případech Visual Studio pro Mac nabízí řadu významných vylepšení pro vývojáře na platformě .NET Core.

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a>Změna cílení na aplikace .NET Core a knihovny .NET Standard

Pokud je nainstalovaná sada .NET Core 2,0 SDK, můžete změnit cílení na projekty .NET Core 1. x na rozhraní .NET Core 2,0 a .NET Standard 1. x .NET Standard 2,0.

Chcete-li změnit cílení projektu v aplikaci Visual Studio, otevřete kartu **aplikace** v dialogovém okně Vlastnosti projektu a změňte **cílovou hodnotu rozhraní** **.net Core 2,0** nebo **.NET Standard 2,0**. Můžete ji také změnit kliknutím pravým tlačítkem myši na projekt a výběrem možnosti **Upravit \*soubor. csproj** . Další informace najdete v části [nástroje](#tooling) výše v tomto tématu.

### <a name="live-unit-testing-support-for-net-core"></a>Podpora Live Unit Testing pro .NET Core

Kdykoli upravíte kód, Live Unit Testing automaticky spustí všechny ovlivněné testy jednotek na pozadí a zobrazí výsledky a pokrytí kódu živě v prostředí sady Visual Studio. .NET Core 2,0 teď podporuje Live Unit Testing. Dříve byla Live Unit Testing k dispozici pouze pro .NET Framework aplikace.

Další informace najdete v tématu [Live Unit Testing se sadou Visual Studio 2017](/visualstudio/test/live-unit-testing) a v části [Live Unit Testing Nejčastější dotazy](/visualstudio/test/live-unit-testing-faq).

### <a name="better-support-for-multiple-target-frameworks"></a>Lepší podpora pro více cílových rozhraní

Pokud vytváříte projekt pro více cílových rozhraní, můžete nyní vybrat cílovou platformu z nabídky nejvyšší úrovně. Na následujícím obrázku je projekt nazvaný SCD1 Targeting 64-bit MacOS X 10,11 (`osx.10.11-x64`) a 64-bit Windows 10/Windows Server 2016 (`win10-x64`). Před výběrem tlačítka projekt můžete vybrat cílovou architekturu, a to v tomto případě pro spuštění sestavení ladění.

![Snímek obrazovky znázorňující výběr cílového rozhraní při sestavování projektu](./media/dotnet-core-2-0/target-framework-selection.png)

### <a name="side-by-side-support-for-net-core-sdks"></a>Souběžná podpora pro sady SDK .NET Core

Nyní můžete nainstalovat .NET Core SDK nezávisle na aplikaci Visual Studio. Díky tomu může jediná verze sady Visual Studio vytvářet projekty, které cílí na různé verze rozhraní .NET Core. Dříve byla aplikace Visual Studio a .NET Core SDK úzce spojena; konkrétní verze sady SDK se doprovází konkrétní verze sady Visual Studio.

## <a name="documentation-improvements"></a>Vylepšení dokumentace

### <a name="net-application-architecture"></a>Architektura aplikace .NET

[Architektura aplikace .NET](https://dotnet.microsoft.com/learn/dotnet/architecture-guides) poskytuje přístup k sadě elektronických knih, které poskytují pokyny, osvědčené postupy a ukázkové aplikace při použití .NET k sestavení:

- [Mikroslužby a kontejnery Docker](../../architecture/microservices/index.md)
- [Webové aplikace s ASP.NET](../../architecture/modern-web-apps-azure/index.md)
- [Mobilní aplikace s využitím Xamarin](/xamarin/xamarin-forms/enterprise-application-patterns/index)
- [Aplikace, které jsou nasazené do cloudu s Azure](/azure/architecture/reference-architectures/index)

## <a name="see-also"></a>Viz také:

- [Co je nového v ASP.NET Core 2,0](/aspnet/core/aspnetcore-2.0)
