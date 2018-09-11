---
title: Co je nového v .NET Core 2.0
description: Informace o nových funkcích v .NET Core.
author: rpetrusha
ms.author: ronpet
ms.date: 08/13/2017
ms.openlocfilehash: 02aac2dab2b892927c0c98fae30bb287a6e24ad6
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44361969"
---
# <a name="whats-new-in-net-core-20"></a>Co je nového v .NET Core 2.0

.NET core 2.0 obsahuje vylepšení a nových funkcí v těchto oblastech:

- [Nástroje](#tooling)
- [Podpora jazyků](#language-support)
- [Vylepšení platformy](#platform-improvements)
- [Změny rozhraní API](#api-changes-and-library-support)
- [Integrace se sadou Visual Studio](#visual-studio-integration)
- [Dokumentace k vylepšení](#documentation-improvements)

## <a name="tooling"></a>Nástroje

### <a name="dotnet-restore-runs-implicitly"></a>DotNet restore se implicitně spouští

V předchozích verzích .NET Core, musíte spustit [dotnet restore](../tools/dotnet-restore.md) příkazu stáhněte závislosti ihned poté, co jste vytvořili nový projekt s [dotnet nové](../tools/dotnet-new.md) příkazu, a také pokaždé, když jste do projektu přidá novou závislost.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Můžete také zakázat automatické vyvolání `dotnet restore` předáním `--no-restore` přepněte `new`, `run`, `build`, `publish`, `pack`, a `test` příkazy.

### <a name="retargeting-to-net-core-20"></a>Mění se cílení na .NET Core 2.0

Pokud je nainstalovaná sada .NET Core 2.0 SDK, projekty, jejichž cílem .NET Core 1.x můžete měli změnit cílení na .NET Core 2.0.

Chcete-li změnit cílení na .NET Core 2.0, upravte soubor projektu tak, že změníte hodnotu `<TargetFramework>` elementu (nebo `<TargetFrameworks>` element, pokud máte více než jeden cíl v souboru projektu) z 1.x do 2.0:

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

Můžete také změnit cíl knihoven .NET Standard a .NET Standard 2.0 stejným způsobem jako:

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

Další informace o migraci vašich projektů .NET Core 2.0 najdete v tématu [migrace z ASP.NET Core 1.x do ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).

## <a name="language-support"></a>Podpora jazyků

Kromě podpory jazyka C# a F #, .NET Core 2.0 podporuje taky Visual Basic.

### <a name="visual-basic"></a>Visual Basic

S verzí 2.0 .NET Core teď podporuje 2017 jazyka Visual Basic. Můžete vytvořit následující typy projektů jazyka Visual Basic:

- Aplikace konzoly .NET core
- Knihovny tříd .NET core
- Knihovny tříd .NET standard
- Projekty testů jednotek .NET core
- Projekty testů xUnit .NET core

Například k vytvoření aplikace v jazyce Visual Basic "Hello World", proveďte následující kroky z příkazového řádku:

1. Otevřete okno konzole, vytvořte adresář pro váš projekt a usnadnit aktuální adresář.

1. Zadejte příkaz `dotnet new console -lang vb`.

   Příkaz vytvoří soubor projektu s `.vbproj` příponou spolu s názvem souboru zdrojového kódu jazyka Visual Basic *soubor Program.vb*. Tento soubor obsahuje zdrojový kód k zápisu řetězce "Hello World!" v okně konzoly.

1. Zadejte příkaz `dotnet run`. [Rozhraní příkazového řádku .NET Core](../tools/index.md) automaticky zkompiluje a spustí aplikaci, které zobrazí zprávu "Hello World!" v okně konzoly.

### <a name="support-for-c-71"></a>Podpora pro jazyk C# 7.1

.NET core 2.0 podporuje C# 7.1, který přidává řadu nových funkcí, včetně:

- `Main` Metoda vstupní bod aplikace, může být označena [asynchronní](../../csharp/language-reference/keywords/async.md) – klíčové slovo.
- Inferredname řazené kolekce členů.
- Výchozí výrazy.

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a>Vylepšení platformy

.NET core 2.0 obsahuje několik funkcí, které usnadňují nainstalovat sadu .NET Core a používat na podporovaných operačních systémech.

### <a name="net-core-for-linux-is-a-single-implementation"></a>.NET core pro Linux je jedna implementace

.NET core 2.0 nabízí jedna implementace systému Linux, která funguje v několika Linuxových distribucích. .NET core 1.x vyžaduje, stáhněte si distribuce Linuxu je implementace.

Můžete také vyvíjet aplikace, které cílí na Linux jako jeden operační systém. .NET core 1.x požadované cílové samostatně každá distribuce Linuxu.

### <a name="support-for-the-apple-cryptographic-libraries"></a>Podpora pro kryptografické knihovny Apple

.NET core 1.x v systému macOS vyžaduje kryptografické knihovny OpenSSL toolkit. .NET core 2.0 využívá kryptografické knihovny Apple a nevyžaduje, aby OpenSSL, takže už nemusíte jej nainstalovat.

## <a name="api-changes-and-library-support"></a>Změny rozhraní API a podpora knihovny

### <a name="support-for-net-standard-20"></a>Podpora pro .NET Standard 2.0

.NET Standard definuje sadu rozhraní API, která musí být k dispozici na implementace .NET, které jsou v souladu s touto verzí standardu systémovou správou verzí. .NET Standard je cílena na vývojáře knihovny. Cílem je zajistit funkce, které jsou k dispozici pro knihovnu, která cílí na verzi .NET Standard na každá implementace .NET. .NET core 1.x podporuje .NET Standard verzi 1.6, .NET Core 2.0 podporuje nejnovější verzi rozhraní .NET Standard 2.0. Další informace najdete v tématu [.NET Standard](../../standard/net-standard.md).

Rozhraní .NET standard 2.0 obsahuje více než 20 000 další rozhraní API, než byly k dispozici v rozhraní .NET Standard 1.6. Velká část to rozšířit styčné plochy výsledky z využívá rozhraní API, které jsou společné pro rozhraní .NET Framework a Xamarin do .NET Standard.

Knihovny tříd .NET standard 2.0 lze také odkazovat knihovny tříd rozhraní .NET Framework, za předpokladu, že volání rozhraní API, která jsou k dispozici v rozhraní .NET Standard 2.0. Žádné rekompilace knihovny rozhraní .NET Framework je povinný.

Seznam rozhraní API, která byla přidána do .NET Standard od jeho poslední verze rozhraní .NET Standard 1.6, najdete v části [vs .NET Standard 2.0. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

### <a name="expanded-surface-area"></a>Rozšířené plochy

Celkový počet rozhraní API na .NET Core 2.0 k dispozici více než zdvojnásobil ve srovnání s .NET Core 1.1.

A [Windows Compatibility Pack](../porting/windows-compat-pack.md) přenos z rozhraní .NET Framework se stal také mnohem jednodušší.

### <a name="support-for-net-framework-libraries"></a>Podporu pro knihovny rozhraní .NET Framework

Kód .NET core může odkazovat na existující knihovny rozhraní .NET Framework, včetně existujících balíčků NuGet. Všimněte si, že tyto knihovny musí používat rozhraní API, která se nacházejí v .NET Standard.

## <a name="visual-studio-integration"></a>integrace sady Visual Studio

Visual Studio 2017 verze 15.3 a v některých případech Visual Studio for Mac nabízí řadu významných vylepšení pro vývojáře v .NET Core.

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a>Mění se cílení aplikace .NET Core a knihovny .NET Standard

Pokud je nainstalovaná sada .NET Core 2.0 SDK, můžete změnit cíl projektů .NET Core 1.x do 1.x knihoven .NET Core 2.0 a .NET Standard a .NET Standard 2.0.

Chcete-li změnit cíl projektu v sadě Visual Studio, otevřete **aplikace** kartu dialogové okno Vlastnosti projektu a změňte **Cílová architektura** hodnota, která se **.NET Core 2.0** nebo **.NET standard 2.0**. Můžete ho můžete změnit tak, že kliknete pravým tlačítkem na projekt a vyberete **upravit \*soubor .csproj** možnost. Další informace najdete v tématu [nástrojů](#tooling) dříve v tomto tématu.

### <a name="live-unit-testing-support-for-net-core"></a>Podpora Live Unit Testing pro .NET Core

Pokaždé, když se váš kód upravíte, Live Unit Testing automaticky spustí všechny testy ovlivněné jednotek na pozadí a zobrazí výsledky a pokrytí kódu živě v prostředí sady Visual Studio. Live Unit Testing nyní podporuje .NET core 2.0. Live Unit Testing byla dříve k dispozici pouze u aplikací využívajících rozhraní .NET Framework.

Další informace najdete v tématu [Live Unit Testing v sadě Visual Studio 2017](/visualstudio/test/live-unit-testing) a [Live Unit Testing – nejčastější dotazy](/visualstudio/test/live-unit-testing-faq).

### <a name="better-support-for-multiple-target-frameworks"></a>Lepší podporu pro více cílových platforem

Pokud vytváříte projekt pro více cílových platforem, teď můžete vybrat cílovou platformu z nabídek nejvyšší úrovně. Na následujícím obrázku, projekt s názvem SCD1 cíle 64bitová verze macOS X 10.11 (`osx.10.11-x64`) a 64bitová verze Windows 10/Windows Server 2016 (`win10-x64`). Před výběrem tlačítka projektu, v tomto případě ke spuštění sestavení pro ladění, můžete vybrat cílovou architekturu.

![Výběr cílové rozhraní při sestavování projektu](media/multitarget.png)

### <a name="side-by-side-support-for-net-core-sdks"></a>Podpora .NET Core SDK vedle sebe

Nyní můžete nainstalovat sadu .NET Core SDK nezávisle na Visual Studio. Díky tomu je možné pro jednu verzi sady Visual Studio k sestavení projektů zaměřené na různé verze rozhraní .NET Core. Dříve Visual Studio a .NET Core SDK byly úzce párované; konkrétní verze sady SDK spolu s konkrétní verzí sady Visual Studio.

## <a name="documentation-improvements"></a>Dokumentace k vylepšení

### <a name="net-application-architecture"></a>Architektura aplikace .NET

[Architektura aplikace .NET](https://www.microsoft.com/net/learn/architecture) vám umožní přístup k sadě elektronické knihy, které obsahují pokyny, osvědčené postupy a ukázkové aplikace při používání technologie .NET k sestavení:

- [Mikroslužby a kontejnery Dockeru](../../standard/microservices-architecture/index.md)
- [Webové aplikace s ASP.NET](../../standard/modern-web-apps-azure-architecture/index.md)
- [Mobilní aplikace s využitím kódu Xamarin](/xamarin/xamarin-forms/enterprise-application-patterns/index.md)
- [Aplikace, které jsou nasazeny do cloudu s Azure](/azure/architecture/reference-architectures/index.md)

## <a name="see-also"></a>Viz také:

* [Co je nového v ASP.NET Core 2.0](/aspnet/core/aspnetcore-2.0)
