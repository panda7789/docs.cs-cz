---
title: 'Kurz: Vytvoření řešení .NET Core v macOS pomocí kódu Visual Studia'
description: Tento dokument poskytuje kroky a pracovní postup k vytvoření .NET Core řešení pomocí kódu sady Visual Studio.
ms.date: 12/19/2019
ms.openlocfilehash: f5da16d413ddc25587ff35550fe9f308dc87f4bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156592"
---
# <a name="tutorial-create-a-net-core-solution-in-macos-using-visual-studio-code"></a>Kurz: Vytvoření řešení .NET Core v macOS pomocí kódu Visual Studia

Tento dokument obsahuje postup a pracovní postup k vytvoření řešení .NET Core pro macOS. Naučte se vytvářet projekty, testování částí, používat ladicí nástroje a začlenit knihovny třetích stran prostřednictvím [NuGet](https://www.nuget.org/).

> [!NOTE]
> Tento článek používá [Visual Studio Kód](https://code.visualstudio.com) na macOS.

## <a name="prerequisites"></a>Požadavky

Nainstalujte sadu [.NET Core SDK](https://dotnet.microsoft.com/download). Sada .NET Core SDK obsahuje nejnovější verzi rozhraní .NET Core framework a runtime.

Nainstalujte [kód sady Visual Studio](https://code.visualstudio.com). Během tohoto článku také nainstalovat rozšíření kódu sady Visual Studio, které zlepšují vývojové prostředí .NET Core.

Nainstalujte rozšíření Visual Studio Code C# otevřením kódu Sady Visual Studio a stisknutím <kbd>klávesy Fn</kbd>+<kbd>F1</kbd> otevřete paletu kódu sady Visual Studio. Zadejte **ext install** zobrazíte seznam rozšíření. Vyberte rozšíření C#. Restartujte visual studio kód pro aktivaci rozšíření. Další informace naleznete v [dokumentaci k rozšíření aplikace Visual Studio Code C# Extension](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="get-started"></a>Začínáme

V tomto kurzu vytvoříte tři projekty: projekt knihovny, testy pro tento projekt knihovny a konzolovou aplikaci, která využívá knihovnu. Zdroj tohoto článku můžete [zobrazit nebo stáhnout](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) v úložišti dotnet/samples na GitHubu. Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Spusťte kód sady Visual Studio. Stisknutím <kbd>klávesy Ctrl</kbd> <kbd>\`</kbd> (znak backquote nebo backtick) nebo vyberte **zobrazit** > **terminál** z nabídky a otevřete vložený terminál v kódu sady Visual Studio. Stále můžete otevřít externí prostředí s příkazem Otevřít explorer **v příkazovém řádku** **(Otevřít v terminálu** na macOS nebo Linux), pokud dáváte přednost práci mimo Visual Studio Code.

Začněte vytvořením souboru řešení, který slouží jako kontejner pro jeden nebo více projektů .NET Core. V terminálu spusťte [`dotnet new`](../tools/dotnet-new.md) příkaz a vytvořte nové řešení *golden.sln* uvnitř nové složky s názvem *golden*:

```dotnetcli
dotnet new sln -o golden
```

Přejděte do nové *zlaté* složky a spusťte následující příkaz k vytvoření projektu knihovny, který vytvoří dva soubory,*library.csproj* a *Class1.cs*, ve složce *knihovny:*

```dotnetcli
dotnet new classlib -o library
```

Spusťte [`dotnet sln`](../tools/dotnet-sln.md) příkaz a přidejte do řešení nově vytvořený projekt *library.csproj:*

```dotnetcli
dotnet sln add library/library.csproj
```

Soubor *library.csproj* obsahuje následující informace:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Naše metody knihovny serializují a rekonstruují objekty ve formátu JSON. Chcete-li podporovat serializaci a deserializaci JSON, přidejte odkaz na balíček `Newtonsoft.Json` NuGet. Příkaz `dotnet add` přidá do projektu nové položky. Chcete-li přidat odkaz na balíček [`dotnet add package`](../tools/dotnet-add-package.md) NuGet, použijte příkaz a zadejte název balíčku:

```dotnetcli
dotnet add library package Newtonsoft.Json
```

To `Newtonsoft.Json` přidá a jeho závislosti do projektu knihovny. Případně ručně upravte soubor *library.csproj* a přidejte následující uzel:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

Spustit [`dotnet restore`](../tools/dotnet-restore.md), ([viz poznámka),](#dotnet-restore-note)která obnoví závislosti a vytvoří složku *obj* uvnitř *knihovny* se třemi soubory, včetně souboru *project.assets.json:*

```dotnetcli
dotnet restore
```

Ve složce *knihovny* přejmenujte *Class1.cs* souborů na *Thing.cs*. Nahraďte kód následujícím:

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

Třída `Thing` obsahuje jednu `Get`veřejnou metodu , která vrací součet dvou čísel, ale činí tak převedením součtu na řetězec a následným deserializací na celé číslo. To využívá řadu moderních funkcí jazyka C#, jako [ `using static` jsou direktivy](../../csharp/language-reference/keywords/using-static.md), [členy s výrazovým tělem](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members)a [interpolace řetězců](../../csharp/language-reference/tokens/interpolated.md).

Vytvořte knihovnu [`dotnet build`](../tools/dotnet-build.md) pomocí příkazu. Tím se vytvoří soubor *library.dll* pod *položkou golden/library/bin/Debug/netstandard1.4*:

```dotnetcli
dotnet build
```

## <a name="create-the-test-project"></a>Vytvoření testovacího projektu

Vytvořte testovací projekt pro knihovnu. Ze *zlaté* složky vytvořte nový testovací projekt:

```dotnetcli
dotnet new xunit -o test-library
```

Přidejte testovací projekt do řešení:

```dotnetcli
dotnet sln add test-library/test-library.csproj
```

Přidejte odkaz na projekt knihovnu, kterou jste vytvořili v předchozí části, aby kompilátor mohl najít a použít projekt knihovny. Použijte [`dotnet add reference`](../tools/dotnet-add-reference.md) příkaz:

```dotnetcli
dotnet add test-library/test-library.csproj reference library/library.csproj
```

Případně ručně upravte soubor *test-library.csproj* a přidejte následující uzel:

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

Nyní, když byly správně nakonfigurovány závislosti, vytvořte testy pro vaši knihovnu. Otevřete *UnitTest1.cs* a nahraďte jeho obsah následujícím kódem:

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing()
        {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

Všimněte si, že tvrdíte, že hodnota 42 se nerovná 19 +23`Assert.NotEqual`(nebo 42) při prvním vytvoření testování částí ( ), které se nezdaří. Důležitým krokem při vytváření testů částí je vytvořit test nezdaří jednou první potvrdit jeho logiku.

Ze *zlaté* složky proveďte následující příkazy:

```dotnetcli
dotnet restore
dotnet test test-library/test-library.csproj
```

Tyto příkazy budou rekurzivně najít všechny projekty obnovit závislosti, jejich sestavení a aktivovat xUnit test runner spustit testy. Jeden test se nezdaří, jak očekáváte.

Upravte soubor *UnitTest1.cs* a `Assert.NotEqual` změňte kontrolní výraz z na `Assert.Equal`. Proveďte následující příkaz ze *zlaté* složky a znovu spusťte test, který tentokrát projde:

```dotnetcli
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a>Vytvoření konzolové aplikace

Konzolová aplikace, kterou vytvoříte v následujících krocích, bude závislá na projektu knihovny, který jste vytvořili dříve, a při spuštění zavolá metodu knihovny. Pomocí tohoto vzoru vývoje uvidíte, jak vytvořit opakovaně použitelné knihovny pro více projektů.

Vytvořte novou konzolovou aplikaci ze *zlaté* složky:

```dotnetcli
dotnet new console -o app
```

Přidejte projekt konzolové aplikace do řešení:

```dotnetcli
dotnet sln add app/app.csproj
```

Vytvořte závislost na knihovně `dotnet add reference` spuštěním příkazu:

```dotnetcli
dotnet add app/app.csproj reference library/library.csproj
```

Spustit `dotnet restore` ([viz poznámka)](#dotnet-restore-note)obnovit závislosti tří projektů v řešení. Otevřete *Program.cs* a nahraďte obsah `Main` metody následujícím řádkem:

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

Do `using` horní části *Program.cs* souboru přidejte dvě direktivy:

```csharp
using static System.Console;
using Library;
```

Proveďte `dotnet run` následující příkaz pro spuštění spustitelného souboru, `-p` kde možnost `dotnet run` určuje projekt pro hlavní aplikaci. Aplikace vytvoří řetězec "Odpověď je 42".

```dotnetcli
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a>Ladění aplikace

Nastavte zarážku `WriteLine` na `Main` příkaz v metodě. To buď stisknutím klávesy <kbd>Fn</kbd>+<kbd>F9,</kbd> když `WriteLine` je kurzor nad čárou, nebo kliknutím myši na levém okraji na řádku, kde chcete nastavit zarážku. Červený kruh se zobrazí na okraji vedle řádku kódu. Po dosažení zarážky spuštění kódu se zastaví *před* spuštěním řádku zarážky.

Otevřete kartu ladicího programu tak, že vyberete ikonu Ladění na panelu nástrojů Kód sady Visual Studio, vyberete **možnost Zobrazit** > **ladění** z řádku nabídek nebo pomocí klávesové zkratky <kbd>&#8679;</kbd> <kbd>&#8984;</kbd> <kbd>D</kbd>:

![Ladicí program kódu sady Visual Studio](./media/using-on-macos/visual-studio-code-debugger.png)

Stisknutím tlačítka Přehrát spusťte aplikaci pod ladicím programem. Vytvořili jste testovací projekt i aplikaci v tomto projektu. Ladicí program se zeptá, který projekt chcete spustit. Vyberte projekt "aplikace". Aplikace začne spouštění a spustí se na zarážku, kde se zastaví. Krok do `Get` metody a ujistěte se, že jste prošli ve správných argumentech. Potvrďte, že odpověď je 42.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
