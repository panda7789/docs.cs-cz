---
title: Začínáme s .NET Core v macOS
description: Tento dokument obsahuje kroky a pracovní postup k vytvoření řešení .NET Core používat Visual Studio Code.
author: bleroy
ms.date: 03/23/2017
ms.custom: seodec18
ms.openlocfilehash: e79f5dd90124d2a1902194af2edbde0f5df107c7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633981"
---
# <a name="get-started-with-net-core-on-macos"></a>Začínáme s .NET Core v macOS

Tento dokument obsahuje kroky a pracovní postup pro vytvoření řešení .NET Core pro macOS. Zjistěte, jak vytvářet projekty testování částí, použijte ladicí nástroje a začlenit knihovny třetích stran přes [NuGet](https://www.nuget.org/).

> [!NOTE]
> Tento článek používá [Visual Studio Code](https://code.visualstudio.com) v systému macOS.

## <a name="prerequisites"></a>Požadavky

Nainstalujte [.NET Core SDK](https://www.microsoft.com/net/core). .NET Core SDK obsahuje nejnovější verzi rozhraní .NET Core framework a modulu runtime.

Nainstalujte [Visual Studio Code](https://code.visualstudio.com). V průběhu tohoto článku můžete také nainstalovat rozšíření, které zlepšují .NET Core. vývojové prostředí Visual Studio Code.

Instalace rozšíření Visual Studio kódu C# otevřete Visual Studio Code a stisknutím klávesy <kbd>F1</kbd> otevřete paletu Visual Studio Code. Typ **ext, přípona instalace** zobrazíte seznam přípon. Vyberte rozšíření jazyka C#. Restartujte Visual Studio Code k aktivaci rozšíření. Další informace najdete v tématu [dokumentaci kódu C# rozšíření sady Visual Studio](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="get-started"></a>Začínáme

V tomto kurzu vytvoříte tři projekty: projekt knihovny testů pro daný projekt knihovny a konzolové aplikace, která používá knihovnu. Je možné [zobrazení nebo stažení zdroj](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) pro toto téma v úložišti dotnet/samples na Githubu. Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Spusťte Visual Studio Code. Stisknutím klávesy <kbd>Ctrl</kbd> + <kbd> \` </kbd> (znak třemi nebo prvními) nebo vyberte **zobrazení > integrovaný terminál** v nabídce otevřít vložený Terminál ve Visual Studio Code. Externí prostředí stále můžete otevřít pomocí Průzkumníka **otevřete příkazový řádek** příkazu (**spusťte v terminálu** v systému Mac nebo Linux) Pokud chcete raději pracovat mimo Visual Studio Code.

Začněte vytvořením souboru řešení, která slouží jako kontejner pro jeden nebo více projektů .NET Core. V terminálu vytvořte *zlaté* složky a otevřete složku. Tato složka je kořenový adresář řešení. Spustit [ `dotnet new` ](../tools/dotnet-new.md) příkaz pro vytvoření nového řešení *golden.sln*:

```console
dotnet new sln
```

Z *zlaté* složky, spusťte následující příkaz pro vytvoření projektu knihovny, který vytvoří dva soubory,*library.csproj* a *Class1.cs*, v *knihovny* složky:

```console
dotnet new classlib -o library
```

Spustit [ `dotnet sln` ](../tools/dotnet-sln.md) příkaz pro přidání nově vytvořené *library.csproj* projektu do řešení:

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

Tento postup přidá `Newtonsoft.Json` a jeho závislosti do projektu knihovny. Případně ručně upravit *library.csproj* a přidejte následující uzel:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="10.0.1" />
</ItemGroup>
```

Spustit [ `dotnet restore` ](../tools/dotnet-restore.md), ([viz Poznámka](#dotnet-restore-note)) která obnoví závislosti a vytvoří *obj* složky uvnitř *knihovny* s třemi soubory, včetně *project.assets.json* souboru:

```console
dotnet restore
```

V *knihovny* složka, soubor přejmenujte *Class1.cs* k *Thing.cs*. Nahraďte kód následujícím kódem:

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

`Thing` Třída obsahuje jednu veřejnou metodu `Get`, která vrací součet dvou čísel ale dosahuje tím, že součet převodu na řetězec a deserializovat ho do celé číslo. Toto využívá celou řadou moderní funkce C#, jako například [ `using static` direktivy](../../csharp/language-reference/keywords/using-static.md), [členové tvoření](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), a [interpolace](../../csharp/language-reference/tokens/interpolated.md).

Vytvoření knihovny pomocí [ `dotnet build` ](../tools/dotnet-build.md) příkazu. Tímto se vytvoří *library.dll* soubor *golden/library/bin/Debug/netstandard1.4*:

```console
dotnet build
```

## <a name="create-the-test-project"></a>Vytvořte projekt testu

Vytvoření testovacího projektu knihovny. Z *zlaté* složku, vytvořte nový projekt testu:

```console
dotnet new xunit -o test-library
```

Přidejte projekt testu k řešení:

```console
dotnet sln add test-library/test-library.csproj
```

Přidáte odkaz na projekt knihovna, kterou jste vytvořili v předchozí části tak, aby kompilátor můžete najít a používat projekt knihovny. Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

Případně ručně upravit *testovací library.csproj* a přidejte následující uzel:

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

Teď, když závislosti byla správně nakonfigurovaná, vytvořte testy pro knihovnu. Otevřít *UnitTest1.cs* a nahraďte jeho obsah následujícím kódem:

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

Mějte na paměti, vyhodnocení, hodnota 42 není roven 19 + 23 (nebo 42) při prvním vytvoření testu jednotek (`Assert.NotEqual`), který se nezdaří. Důležitým krokem při vytváření testů jednotek je pro vytvoření testu po prvním selhání potvrďte svou logikou.

Z *zlaté* složky, spusťte následující příkazy:

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

Tyto příkazy se rekurzivně hledat všechny projekty k obnovení závislostí, je vytvořit a aktivovat xUnit test runner pro spuštění testů. Jeden test selže, tak, jak očekáváte.

Upravit *UnitTest1.cs* soubor a změňte kontrolního výrazu z `Assert.NotEqual` k `Assert.Equal`. Spusťte následující příkaz z *zlaté* složku, kterou chcete znovu spustit test, které vyhovují této doby:

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a>Vytvoření konzolové aplikace

Konzolovou aplikaci, které vytvoříte prostřednictvím následujících kroků je závislá na projekt knihovny vytvořené dříve a volá metodu jeho knihovna při spuštění. Použití tohoto modelu vývoje, můžete zjistit, jak vytvářet opakovaně použitelné knihovny pro více projektů.

Vytvořte novou konzolovou aplikaci z *zlaté* složky:

```console
dotnet new console -o app
```

Přidáte do řešení projekt konzolové aplikace:

```console
dotnet sln add app/app.csproj
```

Vytvořte závislosti na knihovně spuštěním `dotnet add reference` příkaz:

```console
dotnet add app/app.csproj reference library/library.csproj
```

Spustit `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) Chcete-li obnovit závislosti tří projektů v řešení. Otevřít *Program.cs* a nahraďte obsah `Main` metoda tento řádek:

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

Přidejte dva `using` direktivy k hornímu okraji *Program.cs* souboru:

```csharp
using static System.Console;
using Library;
```

Spuštěním následujících `dotnet run` příkaz ke spuštění spustitelného souboru, kde `-p` umožňuje `dotnet run` určuje projekt, pro hlavní aplikaci. Aplikace vytvoří řetězec "odpověď je 42".

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a>Ladění aplikace

Nastavit zarážku na `WriteLine` příkaz v `Main` metody. To udělat buď stisknutím <kbd>F9</kbd> klávesy, když se ukazatel myši nachází `WriteLine` řádek nebo kliknutím myši na levý okraj řádku, ve které chcete nastavit zarážku. Na okraji vedle řádku kódu se zobrazí červený kruh. Při dosažení zarážky zastaví provádění kódu *před* provedením řádku zarážku.

Výběrem ikony ladění na panelu nástrojů Visual Studio Code otevřete kartu ladicí program výběrem **zobrazení > ladění** z řádku nabídek nebo pomocí klávesové zkratky <kbd>CTRL</kbd> + <kbd> SHIFT</kbd>+<kbd>D</kbd>:

![Ladicí program sady Visual Studio Code](./media/using-on-macos/visual-studio-code-debugger.png)

Kliknutím na tlačítko Přehrát a spusťte tak aplikaci v ladicím programu. Aplikace zahájí vykonávání a běží na zarážku, kde se zastaví. Krokovat s vnořením `Get` metoda a ujistěte se, že jste předali v správné argumenty. Potvrďte, že odpověď je 42.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
