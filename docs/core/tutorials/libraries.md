---
title: Vývoj knihoven pomocí rozhraní CLI jádra .NET
description: Přečtěte si, jak vytvořit knihovny .NET Core pomocí rozhraní CLI jádra .NET. Vytvoříte knihovnu, která podporuje více architektur.
author: cartermp
ms.date: 05/01/2017
ms.openlocfilehash: c23c1f027b4d6d09c50eb2257d34f72ec56302f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503507"
---
# <a name="develop-libraries-with-the-net-core-cli"></a>Vývoj knihoven pomocí rozhraní CLI jádra .NET

Tento článek popisuje, jak psát knihovny pro rozhraní .NET pomocí rozhraní CLI jádra .NET. ClI poskytuje efektivní a nízké úrovně prostředí, které funguje v rámci všech podporovaných operačních systémů. Stále můžete vytvářet knihovny s Visual Studio a pokud je vaše upřednostňované prostředí [naleznete v průvodci Visual Studio](library-with-visual-studio.md).

## <a name="prerequisites"></a>Požadavky

Potřebujete v [počítači nainstalovanou sadu .NET Core SDK a CLI.](https://dotnet.microsoft.com/download)

Pro části tohoto dokumentu, které se zabývají verzemi rozhraní .NET Framework, potřebujete rozhraní [.NET Framework](https://dotnet.microsoft.com) nainstalované v počítači se systémem Windows.

Pokud chcete podporovat starší cíle rozhraní .NET Framework, je třeba nainstalovat balíčky cílení nebo vývojářské balíčky ze [stránky archivů ke stažení rozhraní .NET](https://dotnet.microsoft.com/download/archives). Viz tato tabulka:

| Verze rozhraní .NET Framework | Co stáhnout                                       |
| ---------------------- | ------------------------------------------------------ |
| 4.6.1                  | Balíček cílení rozhraní .NET Framework 4.6.1                    |
| 4.6                    | Balíček cílení rozhraní .NET Framework 4.6                      |
| 4.5.2                  | Sada .NET Framework 4.5.2 Developer Pack                    |
| 4.5.1                  | Sada .NET Framework 4.5.1 Developer Pack                    |
| 4.5                    | Sada Windows SDK pro aplikace pro Windows 8         |
| 4.0                    | Sada Windows SDK pro systémy Windows 7 a rozhraní .NET Framework 4         |
| 2,0, 3,0 a 3,5      | Běhčasu .NET Framework 3.5 SP1 (nebo verze windows 8+) |

## <a name="how-to-target-the-net-standard"></a>Jak cílit na standard .NET

Pokud nejste obeznámeni s .NET Standard, naleznete [v .NET Standard](../../standard/net-standard.md) další informace.

V tomto článku je tabulka, která mapuje verze .NET Standard na různé implementace:

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

Tato tabulka znamená pro vytvoření knihovny:

Verze rozhraní .NET Standard, kterou vyberete, bude kompromisem mezi přístupem k nejnovějším rozhraním API a možností zaměřit se na další implementace rozhraní .NET a verze .NET Standard. Rozsah cílových platforem a verzí můžete řídit `netstandardX.X` výběrem `X.X` verze (kde je číslo verze) a`.csproj` `.fsproj`jeho přidáním do souboru projektu ( nebo ).

Máte tři primární možnosti při cílení .NET Standard, v závislosti na vašich potřebách.

1. Můžete použít výchozí verzi standardu .NET, `netstandard1.4`která je dodávána šablonami , která umožňuje přístup k většině rozhraní API ve standardu .NET Standard, zatímco je stále kompatibilní s uwp, rozhraními .NET Framework 4.6.1 a .NET Standard 2.0.

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. Nižší nebo vyšší verzi standardu .NET můžete použít úpravou hodnoty v `TargetFramework` uzlu souboru projektu.

    Verze .NET Standard jsou zpětně kompatibilní. To znamená, že `netstandard1.0` `netstandard1.1` knihovny běží na platformách a vyšší. Neexistuje však žádná dopředná kompatibilita. Nižší platformy .NET Standard nemohou odkazovat na vyšší. To znamená, že `netstandard1.0` knihovny `netstandard1.1` nemohou odkazovat na knihovny, které cílí na nebo jsou vyšší. Vyberte standardní verzi, která má správnou kombinaci api a podpory platformy pro vaše potřeby. Prozatím `netstandard1.4` doporučujeme.

3. Pokud chcete cílit na rozhraní .NET Framework verze 4.0 nebo nižší nebo chcete použít rozhraní API dostupné `System.Drawing`v rozhraní .NET Framework, ale ne v rozhraní .NET Standard (například), přečtěte si následující části a zjistěte, jak vícecílit.

## <a name="how-to-target-net-framework"></a>Jak cílit na rozhraní .NET Framework

> [!NOTE]
> Tyto pokyny předpokládají, že máte v počítači nainstalovanou architekturu .NET Framework. Naleznete [požadavky získat](#prerequisites) nainstalované závislosti.

Mějte na paměti, že některé verze rozhraní .NET Framework, které jsou zde používány, již nejsou podporovány. Informace o nepodporovaných verzích naleznete v [nejčastějších dotazech k zásadám životního cyklu podpory rozhraní .NET](https://support.microsoft.com/gp/framework_faq/en-us) Framework.

Pokud chcete dosáhnout maximálního počtu vývojářů a projektů, použijte rozhraní .NET Framework 4.0 jako cíl směrného plánu. Chcete-li cílit na rozhraní .NET Framework, začněte pomocí správného zástupný název cílového rozhraní (TFM), který odpovídá verzi rozhraní .NET Framework, kterou chcete podporovat.

| Verze rozhraní .NET Framework | Tfm      |
| ---------------------- | -------- |
| .NET Framework 2,0     | `net20`  |
| .NET Framework 3.0     | `net30`  |
| .NET Framework 3.5     | `net35`  |
| .NET Framework 4.0     | `net40`  |
| .NET Framework 4.5     | `net45`  |
| .NET Framework 4.5.1   | `net451` |
| .NET Framework 4.5.2   | `net452` |
| .NET Framework 4.6     | `net46`  |
| .NET Framework 4.6.1   | `net461` |
| .NET Framework 4.6.2   | `net462` |
| Rozhraní .NET Framework 4.7     | `net47`  |
|  .NET Framework 4.8     | `net48`  |

Potom vložíte tento TFM do `TargetFramework` části souboru projektu. Například, tady je návod, jak byste napsat knihovnu, která se zaměřuje na rozhraní .NET Framework 4.0:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

A to je vše! I když to zkompilován pouze pro rozhraní .NET Framework 4, můžete použít knihovnu na novější verze rozhraní .NET Framework.

## <a name="how-to-multitarget"></a>Jak vícecílit

> [!NOTE]
> Následující pokyny předpokládají, že máte v počítači nainstalovanou architekturu .NET Framework. V části [Požadavky](#prerequisites) se dozvíte, které závislosti je třeba nainstalovat a odkud je stáhnout.

Možná budete muset cílit na starší verze rozhraní .NET Framework, pokud váš projekt podporuje rozhraní .NET Framework i .NET Core. V tomto scénáři pokud chcete použít novější rozhraní API a jazykové konstrukce `#if` pro novější cíle, použijte direktivy v kódu. Také může být nutné přidat různé balíčky a závislosti pro každou platformu, na kterou cílíte, aby zahrnovala různá řešení API potřebná pro každý případ.

Řekněme například, že máte knihovnu, která provádí síťové operace přes protokol HTTP. Pro standard .NET Standard a rozhraní .NET Framework verze 4.5 nebo vyšší můžete použít třídu `HttpClient` z oboru `System.Net.Http` názvů. Dřívější verze rozhraní .NET Framework však nemají `HttpClient` třídu, takže `WebClient` místo toho `System.Net` můžete použít třídu z oboru názvů pro ty.

Soubor projektu může vypadat takto:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.0 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net40'">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.5 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net45'">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>
</Project>
```

Zde si všimnete tří hlavních změn:

1. Uzel `TargetFramework` byl nahrazen `TargetFrameworks`a tři TFM jsou vyjádřeny uvnitř.
1. Existuje `<ItemGroup>` uzel pro `net40` cíl tahání v jednom odkazu rozhraní .NET Framework.
1. Existuje `<ItemGroup>` uzel pro `net45` cíl tahání ve dvou odkazech rozhraní .NET Framework.

Systém sestavení si je vědom následujících `#if` preprocesorových symbolů používaných v direktivách:

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

Zde je příklad využití podmíněné kompilace na cíl:

```csharp
using System;
using System.Text.RegularExpressions;
#if NET40
// This only compiles for the .NET Framework 4 targets
using System.Net;
#else
 // This compiles for all other targets
using System.Net.Http;
using System.Threading.Tasks;
#endif

namespace MultitargetLib
{
    public class Library
    {
#if NET40
        private readonly WebClient _client = new WebClient();
        private readonly object _locker = new object();
#else
        private readonly HttpClient _client = new HttpClient();
#endif

#if NET40
        // .NET Framework 4.0 does not have async/await
        public string GetDotNetCount()
        {
            string url = "https://www.dotnetfoundation.org/";

            var uri = new Uri(url);

            string result = "";

            // Lock here to provide thread-safety.
            lock(_locker)
            {
                result = _client.DownloadString(uri);
            }

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"Dotnet Foundation mentions .NET {dotNetCount} times!";
        }
#else
        // .NET 4.5+ can use async/await!
        public async Task<string> GetDotNetCountAsync()
        {
            string url = "https://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

Pokud tento projekt `dotnet build`vytváříte s , zaznamenáte `bin/` ve složce tři adresáře:

```
net40/
net45/
netstandard1.4/
```

Každý z nich `.dll` obsahuje soubory pro každý cíl.

## <a name="how-to-test-libraries-on-net-core"></a>Jak testovat knihovny na .NET Core

Je důležité, aby bylo možné testovat napříč platformami. Můžete použít [buď xUnit](https://xunit.github.io/) nebo MSTest po vybalení z krabice. Obě jsou dokonale vhodné pro testování částí knihovny na .NET Core. Způsob nastavení řešení pomocí testovacích projektů bude záviset na [struktuře vašeho řešení](#structuring-a-solution). Následující příklad předpokládá, že testovací a zdrojové adresáře žijí ve stejném adresáři nejvyšší úrovně.

> [!NOTE]
> To používá některé příkazy [rozhraní příkazového příkazu .NET Core CLI.](../tools/index.md) Další informace naleznete [v tématu dotnet new](../tools/dotnet-new.md) a [dotnet sln.](../tools/dotnet-sln.md)

1. Nastavte řešení. Můžete tak učinit pomocí následujících příkazů:

   ```dotnetcli
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   Tím se vytvoří projekty a propojí je v řešení. Adresář pro `SolutionWithSrcAndTest` by měl vypadat takto:

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. Přejděte do adresáře testovacího projektu `MyProject.Test` a `MyProject`přidejte odkaz z aplikace .

   ```dotnetcli
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. Obnovení balíčků a vytváření projektů:

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. Ověřte, zda xUnit `dotnet test` běží spuštěním příkazu. Pokud jste zvolili použití MSTest, pak konzola MSTest runner by měl spustit místo.

A to je vše! Nyní můžete otestovat knihovnu na všech platformách pomocí nástrojů příkazového řádku. Chcete-li pokračovat v testování nyní, že máte vše nastaveno, testování knihovny je velmi jednoduché:

1. Proveďte změny v knihovně.
1. Spusťte testy z příkazového řádku `dotnet test` v testovacím adresáři pomocí příkazu.

Váš kód bude automaticky znovu `dotnet test` sestaven při vyvolání příkazu.

## <a name="how-to-use-multiple-projects"></a>Jak používat více projektů

Běžnou potřebou větších knihoven je umístění funkcí v různých projektech.

Představte si, že chcete vytvořit knihovnu, která by mohla být spotřebována v idiomatic C# a F#. To by znamenalo, že spotřebitelé vaší knihovny spotřebovávají způsobem, který je přirozený pro C# nebo F#. Například v C# můžete využívat knihovnu takto:

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

V F# to může vypadat takto:

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

Scénáře spotřeby, jako je tento, znamenají, že rozhraní API, která jsou přístupná, musí mít jinou strukturu pro C# a F#.  Běžným přístupem k dosažení tohoto je faktor všechny logiky knihovny do základního projektu, s C# a F# projekty definující vrstvy rozhraní API, které volají do tohoto základního projektu.  Zbytek oddílu bude používat následující názvy:

* **AwesomeLibrary.Core** - základní projekt, který obsahuje všechny logiky pro knihovnu
* **AwesomeLibrary.CSharp** - projekt s veřejnými rozhraními API určenými ke spotřebě v C #
* **AwesomeLibrary.FSharp** - projekt s veřejnými rozhraními API určenými ke spotřebě v F #

V terminálu můžete spustit následující příkazy a vytvořit tak stejnou strukturu jako tato příručka:

```dotnetcli
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang "F#"
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

Tím přidáte tři výše uvedené projekty a soubor řešení, který je propojí dohromady. Vytvoření souboru řešení a propojení projektů vám umožní obnovit a vytvářet projekty z nejvyšší úrovně.

### <a name="project-to-project-referencing"></a>Odkazování na projekt-projekt

Nejlepší způsob, jak odkazovat na projekt, je použít rozhraní CLI jádra .NET k přidání odkazu na projekt. Z adresářů projektu **AwesomeLibrary.CSharp** a **AwesomeLibrary.FSharp** můžete spustit následující příkaz:

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

Soubory projektu pro **AwesomeLibrary.CSharp** a **AwesomeLibrary.FSharp** bude nyní odkazovat **AwesomeLibrary.Core** jako `ProjectReference` cíl.  Můžete to ověřit kontrolou souborů projektu a zobrazením následujících položek v nich:

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

Tuto část můžete přidat do každého souboru projektu ručně, pokud nechcete používat rozhraní CLI jádra .NET.

### <a name="structuring-a-solution"></a>Strukturování roztoku

Dalším důležitým aspektem řešení pro více projektů je vytvoření dobré celkové struktury projektů. Můžete uspořádat kód, jak se vám líbí, a tak `dotnet sln add`dlouho, jak propojit `dotnet restore` každý `dotnet build` projekt se souborem řešení s , budete moci spustit a na úrovni řešení.
