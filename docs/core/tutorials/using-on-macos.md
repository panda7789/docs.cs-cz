---
title: Začínáme s .NET Core v systému macOS
description: Tento dokument obsahuje kroky a pracovní postup pro vytvoření základní řešení .NET pomocí Visual Studio Code.
keywords: Rozhraní .NET, .NET core, Mac, systému macOS, Visual Studio Code
author: bleroy
ms.author: mairaw
ms.date: 03/23/2017
ms.topic: get-started-article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8ad82148-dac8-4b31-9128-b0e9610f4d9b
ms.workload:
- dotnetcore
ms.openlocfilehash: d130ef34961d19c450dd7142c8a5996c83465646
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2018
---
# <a name="getting-started-with-net-core-on-macos"></a>Začínáme s .NET Core v systému macOS

Tento dokument obsahuje kroky a pracovní postup k vytvoření řešení pro systému macOS .NET Core. Naučte se vytvářet projekty, testy částí, použijte ladicí nástroje a začlenění knihoven jiných výrobců přes [NuGet](https://www.nuget.org/).

> [!NOTE]
> Tento článek používá [Visual Studio Code](http://code.visualstudio.com) v systému macOS.

## <a name="prerequisites"></a>Požadavky

Nainstalujte [.NET Core SDK](https://www.microsoft.com/net/core). .NET Core SDK zahrnuje nejnovější verze jádra rozhraní .NET framework a prostředí runtime.

Nainstalujte [Visual Studio Code](http://code.visualstudio.com). Během postupu v tomto článku můžete také nainstalovat rozšíření, které vylepšují vývoj .NET Core prostředí Visual Studio Code.

Nainstalovat rozšíření pro Visual Studio kódu C# otevřete Visual Studio Code a stisknutím klávesy <kbd>F1</kbd> otevřete Visual Studio Code paletu. Typ **ext nainstalovat** zobrazíte seznam přípon. Vyberte požadované rozšíření C#. Restartujte Visual Studio Code aktivovat rozšíření. Další informace najdete v tématu [kódu jazyka C# rozšíření sady Visual Studio dokumentaci](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="getting-started"></a>Začínáme

V tomto kurzu vytvoříte tří projektů: projekt knihovny testů pro tento projekt knihovny a Konzolová aplikace, která používá knihovnu. Můžete [zobrazit nebo stáhnout zdrojovou](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) pro toto téma na dotnet/samples úložišti na Githubu. Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Spusťte Visual Studio Code. Stiskněte klávesu <kbd>Ctrl</kbd> + <kbd> \` </kbd> (znak třemi nebo backtick) nebo vyberte **zobrazení > integrované Terminálové** v nabídce otevřete embedded terminálu ve Visual Studio Code. Externí prostředí stále můžete otevřít pomocí Průzkumníka **otevřete v příkazovém řádku** příkazu (**otevřete v terminálu** na Mac nebo Linux) Pokud dáváte přednost práci mimo Visual Studio Code.

Začněte vytvořením řešení souboru, který slouží jako kontejner pro jeden nebo více projekty .NET Core. V terminálu, vytvořte *zlaté* složky a otevřete složku. Tato složka je kořenový adresář řešení. Spustit [ `dotnet new` ](../tools/dotnet-new.md) příkazu vytvořte nové řešení *golden.sln*:

```console
dotnet new sln
```

Z *zlaté* složky, spusťte následující příkaz k vytvoření projektu knihovny, který vytvoří dva soubory,*library.csproj* a *Class1.cs*, v *knihovny* složky:

```console
dotnet new classlib -o library
```

Spuštění [ `dotnet sln` ](../tools/dotnet-sln.md) příkaz pro přidání nově vytvořený *library.csproj* projektu a řešení:

```console
dotnet sln add library/library.csproj
```

*Library.csproj* soubor obsahuje následující informace:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard1.4</TargetFramework>
  </PropertyGroup>

</Project>
```

Naše knihovna metody serializaci a deserializaci objektů ve formátu JSON. Pro podporu JSON serializace a deserializace, přidejte odkaz na `Newtonsoft.Json` balíček NuGet. `dotnet add` Příkaz přidá nové položky do projektu. Chcete-li přidat odkaz na balíček NuGet, použijte [ `dotnet add package` ](../tools/dotnet-add-package.md) příkaz a zadejte název balíčku:

```console
dotnet add library package Newtonsoft.Json
```

Tento postup přidá `Newtonsoft.Json` a jeho závislé součásti na projekt knihovny. Případně ručně upravit *library.csproj* souboru a přidejte následující uzly:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="10.0.1" />
</ItemGroup>
```

Spuštění [ `dotnet restore` ](../tools/dotnet-restore.md), ([viz Poznámka](#dotnet-restore-note)), který obnoví závislosti a vytvoří *obj* složky uvnitř *knihovny* s třemi soubory v, včetně *project.assets.json* souboru:

```console
dotnet restore
```

V *knihovny* složku, přejmenujte soubor *Class1.cs* k *Thing.cs*. Nahraďte kód tímto:

```csharp
using static Newtonsoft.Json.JsonConvert;

namespace Library
{
    public class Thing
    {
        public int Get(int left, int right) =>
            DeserializeObject<int>($"{left + right}");
    }
}
```

`Thing` Třída obsahuje jeden veřejná metoda `Get`, která vrací součet dvou čísla, ale součet převádění na řetězce a pak ho deserializaci do celé číslo. Toto využívá celou řadu moderní C# funkcí, jako například [ `using static` direktivy](../../csharp/language-reference/keywords/using-static.md), [výraz vozidlo členy](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), a [řetězec interpolace](../../csharp/language-reference/tokens/interpolated.md).

Sestavení knihovny s [ `dotnet build` ](../tools/dotnet-build.md) příkaz. Tímto se vytvoří *library.dll* souboru pod *golden/library/bin/Debug/netstandard1.4*:

```console
dotnet build
```

## <a name="create-the-test-project"></a>Vytvoření projektu testů

Vytvoření testovacího projektu knihovny. Z *zlaté* složky, vytvořte nový projekt testu:

```console
dotnet new xunit -o test-library
```

Do řešení přidáte k testovacímu projektu:

```console
dotnet sln add test-library/test-library.csproj
```

Přidáte odkaz na projekt knihovna, kterou jste vytvořili v předchozí části, aby kompilátor můžete najít a použití projektu knihovny. Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

Případně ručně upravit *test library.csproj* souboru a přidejte následující uzlu:

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

Teď, když jsou správně nakonfigurovány závislosti vytváření testů pro své knihovny. Otevřete *UnitTest1.cs* a nahraďte jeho obsah následujícím kódem:

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing() {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

Všimněte si assert hodnota 42 není rovno 19 + 23 (nebo 42) při prvním vytvoření testování částí (`Assert.NotEqual`), který se nezdaří. Důležitým krokem při vytváření testů jednotek je vytvoření testu, aby v případě selhání jednou nejprve potvrdit svou logikou.

Z *zlaté* složky, spuštěním následujících příkazů:

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

Tyto příkazy bude rekurzivní hledání, že všechny projekty k obnovení závislosti, je sestavení a aktivaci xUnit test runner ke spuštění testů. Jeden test se nezdaří, podle očekávání.

Upravit *UnitTest1.cs* soubor a změňte assertion z `Assert.NotEqual` k `Assert.Equal`. Spusťte následující příkaz z *zlaté* složku, kterou chcete znovu spustit test, který předává této doby:

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a>Vytvoření konzolové aplikace

Konzolové aplikace, které vytvoříte prostřednictvím následujících kroků má závislost na projekt knihovny jste dříve vytvořili a volá metodu jeho knihovny, když je spuštěna. Pomocí tohoto vzoru vývoj, můžete zjistit, jak vytvořit opakovaně použitelné knihovny pro více projektů.

Vytvořte novou konzolovou aplikaci z *zlaté* složky:

```console
dotnet new console -o app
```

Do řešení přidáte projekt konzolové aplikace:

```console
dotnet sln add app/app.csproj
```

Vytvoření závislosti na knihovně spuštěním `dotnet add reference` příkaz:

```console
dotnet add app/app.csproj reference library/library.csproj
```

Spustit `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) Chcete-li obnovit závislosti tři projekty v řešení. Otevřete *Program.cs* a nahraďte obsah `Main` metoda tento řádek:

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

Přidejte dva `using` direktivy do horní části *Program.cs* souboru:

```csharp
using static System.Console;
using Library;
```

Spuštěním následujících `dotnet run` příkaz ke spuštění spustitelného souboru, kde `-p` možnost k `dotnet run` určuje projekt, který pro hlavní aplikaci. Aplikace vytvoří řetězec "odpověď je 42".

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a>Ladění aplikace

Nastavte zarážky v `WriteLine` příkaz v `Main` metoda. To provedete buď stiskněte <kbd>F9</kbd> klíče, pokud se ukazatel myši `WriteLine` řádku nebo pomocí myši na levém okraji na řádek, na kterém chcete nastavit bod přerušení. Červené kolečko se zobrazí u okraje řádku řádek kódu. Když je dosaženo zarážkou, provádění kódu zastaví *před* řádek zarážek spustí.

Otevřete kartu ladicí program výběrem ikony ladění na panelu nástrojů Visual Studio Code výběr **zobrazení > ladění** z řádku nabídek nebo pomocí klávesové zkratky <kbd>CTRL</kbd> + <kbd> POSUNUTÍ</kbd>+<kbd>D</kbd>:

![Ladicí program Visual Studio Code](./media/using-on-macos/vscodedebugger.png)

Kliknutím na tlačítko Přehrát a spusťte aplikaci v části ladicího programu. Aplikace zahájí spuštění a běží na zarážku, kde se zastaví. Krokovat s vnořením `Get` metoda a ujistěte se, že předané ve správné argumenty. Potvrďte, že odpověď 42.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]