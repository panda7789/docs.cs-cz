---
title: Vývoj knihoven pomocí .NET Core CLI
description: Naučte se vytvářet knihovny .NET Core pomocí .NET Core CLI. Vytvoříte knihovnu, která podporuje více rozhraní.
author: cartermp
ms.topic: how-to
ms.date: 05/01/2017
ms.openlocfilehash: 7aadaf7bf7819d52a57c3a137beff46d924d8cb0
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396203"
---
# <a name="develop-libraries-with-the-net-core-cli"></a>Vývoj knihoven pomocí .NET Core CLI

Tento článek popisuje, jak psát knihovny pro .NET pomocí .NET Core CLI. Rozhraní příkazového řádku poskytuje efektivní a nízké prostředí, které funguje v jakémkoli podporovaném operačním systému. Knihovny můžete vytvářet i v aplikaci Visual Studio a pokud je vaše preferované prostředí, [Přečtěte si průvodce sadou Visual Studio](library-with-visual-studio.md).

## <a name="prerequisites"></a>Požadavky

Potřebujete na svém počítači nainstalované [.NET Core SDK a CLI](https://dotnet.microsoft.com/download) .

V části tohoto dokumentu, které se týkají .NET Framework verzí, potřebujete [.NET Framework](https://dotnet.microsoft.com) nainstalovány na počítači s Windows.

Kromě toho, pokud chcete podporovat starší .NET Framework cíle, je nutné nainstalovat sady Target Packs nebo sady Developer Pack ze [stránky archivu stahování v rozhraní .NET](https://dotnet.microsoft.com/download/archives). Další informace najdete v této tabulce:

| Verze rozhraní .NET Framework | Co stáhnout                                       |
| ---------------------- | ------------------------------------------------------ |
| 4.6.1                  | .NET Framework 4.6.1 targeting pack                    |
| 4.6                    | Sada targeting pack .NET Framework 4,6                      |
| 4.5.2                  | .NET Framework 4.5.2 Developer Pack                    |
| 4.5.1                  | .NET Framework 4.5.1 Developer Pack                    |
| 4.5                    | Sada Windows SDK pro aplikace pro Windows 8         |
| 4.0                    | Windows SDK pro Windows 7 a .NET Framework 4         |
| 2,0, 3,0 a 3,5      | Runtime .NET Framework 3,5 SP1 (nebo Windows 8 + verze) |

## <a name="how-to-target-the-net-standard"></a>Jak cílit na .NET Standard

Pokud nejste obeznámeni s .NET Standard, další informace najdete v [.NET Standard](../../standard/net-standard.md) .

V tomto článku je k dispozici tabulka, která mapuje .NET Standard verze na různé implementace:

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

Zde je uvedeno, co tato tabulka znamená pro účely vytvoření knihovny:

Verze .NET Standard, kterou vyberete, bude kompromis mezi přístupem k nejnovějším rozhraním API a možností cílit na více implementací rozhraní .NET a .NET Standard verzí. Rozsah cílových platforem a verzí řídíte tak, že vybíráte verzi `netstandardX.X` (kde `X.X` je číslo verze) a přidáte ho do souboru projektu ( `.csproj` nebo `.fsproj` ).

V závislosti na vašich potřebách máte tři primární možnosti, které cílí na .NET Standard.

1. Můžete použít výchozí verzi .NET Standard poskytnutou šablonami, `netstandard1.4` která vám umožní přístup k většině rozhraní API v .NET Standard a pořád je kompatibilní s UWP, .NET Framework 4.6.1 a .NET Standard 2,0.

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. Můžete použít nižší nebo vyšší verzi .NET Standard úpravou hodnoty v `TargetFramework` uzlu souboru projektu.

    Verze .NET Standard jsou zpětně kompatibilní. To znamená, že `netstandard1.0` knihovny běží na `netstandard1.1` platformách a vyšších. Nejedná se však o dopředné kompatibility. Nižší .NET Standard platformy nemůžou odkazovat na vyšší úrovně. To znamená, že `netstandard1.0` knihovny nemohou odkazovat na knihovny cílené na `netstandard1.1` nebo vyšší. Vyberte standardní verzi, která má správnou kombinaci rozhraní API a podpory platforem podle vašich potřeb. Teď doporučujeme `netstandard1.4` .

3. Pokud chcete cílit .NET Framework verze 4,0 nebo nižší nebo chcete použít rozhraní API dostupné v .NET Framework, ale ne v .NET Standard (například `System.Drawing` ), přečtěte si následující oddíly a Naučte se, jak cílit.

## <a name="how-to-target-net-framework"></a>Jak cílit na .NET Framework

> [!NOTE]
> V těchto pokynech se předpokládá, že máte na svém počítači nainstalovanou .NET Framework. Pokud chcete získat nainstalované závislosti, přečtěte si [požadavky](#prerequisites) .

Mějte na paměti, že některé z .NET Framework používané verze už nejsou podporované. Přečtěte si [Nejčastější dotazy k zásadám životního cyklu podpory .NET Framework](https://support.microsoft.com/gp/framework_faq/en-us) pro nepodporované verze.

Pokud chcete dosáhnout maximálního počtu vývojářů a projektů, použijte jako cíl standardních hodnot .NET Framework 4,0. Chcete-li cílit na .NET Framework, začněte pomocí správného monikeru cílového rozhraní .NET Framework (TFM), který odpovídá .NET Framework verzi, kterou chcete podporovat.

| Verze rozhraní .NET Framework | TFM      |
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
| .NET Framework 4,7     | `net47`  |
|  .NET Framework 4.8     | `net48`  |

Pak tento TFM vložíte do `TargetFramework` části souboru projektu. Tady je příklad, jak byste měli napsat knihovnu, která cílí na .NET Framework 4,0:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

A to je vše! I když se tato kompilace kompiluje jenom pro .NET Framework 4, můžete použít knihovnu v novějších verzích .NET Framework.

## <a name="how-to-multitarget"></a>Jak cílit

> [!NOTE]
> V následujících pokynech se předpokládá, že máte na svém počítači nainstalovanou .NET Framework. Informace o závislostech, které potřebujete nainstalovat a odkud je stáhnout z nástroje, najdete v části [požadavky](#prerequisites) .

Je možné, že budete muset cílit na starší verze .NET Framework, pokud projekt podporuje .NET Framework i .NET Core. V tomto scénáři, pokud chcete používat novější rozhraní API a jazykové konstrukce pro novější cíle, použijte `#if` direktivy ve svém kódu. Také může být nutné přidat různé balíčky a závislosti pro každou platformu, na kterou cílíte, aby zahrnovala různá rozhraní API potřebná pro každý případ.

Řekněme například, že máte knihovnu, která provádí síťové operace přes HTTP. Pro .NET Standard a .NET Framework verze 4,5 nebo vyšší můžete použít `HttpClient` třídu z `System.Net.Http` oboru názvů. Starší verze .NET Framework však nemají `HttpClient` třídu, takže můžete `WebClient` místo toho použít třídu z `System.Net` oboru názvů.

Váš soubor projektu by mohl vypadat takto:

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

Tady si všimnete tří hlavních změn:

1. `TargetFramework`Uzel byl nahrazen `TargetFrameworks` a tři TFM jsou vyjádřeny uvnitř.
1. `<ItemGroup>`Uzel pro cíl se může `net40` vykázat v jednom .NET Framework referenci.
1. `<ItemGroup>`Uzel pro cíl se může `net45` na dvou .NET Framework odkazů.

Systém sestavení ví o následujících symbolech preprocesoru, které se používají ve `#if` směrnicích:

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

Tady je příklad, který využívá Podmíněná kompilace na cíl:

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

Pokud tento projekt sestavíte pomocí `dotnet build` , všimnete si tří adresářů ve `bin/` složce:

```
net40/
net45/
netstandard1.4/
```

Každá z nich obsahuje `.dll` soubory pro každý cíl.

## <a name="how-to-test-libraries-on-net-core"></a>Postup testování knihoven v .NET Core

Je důležité, abyste mohli testovat napříč platformami. V poli můžete použít buď [xUnit](https://xunit.github.io/) nebo MSTest. Obě jsou dokonale vhodné pro testování částí knihovny v .NET Core. Způsob nastavení řešení pomocí testovacích projektů bude záviset na [struktuře řešení](#structuring-a-solution). Následující příklad předpokládá, že testovací a zdrojové adresáře jsou ve stejném adresáři nejvyšší úrovně v provozu.

> [!NOTE]
> Používá se k tomu několik příkazů [.NET Core CLI](../tools/index.md) . Další informace naleznete v tématu [dotnet New](../tools/dotnet-new.md) a [dotnet sln](../tools/dotnet-sln.md) .

1. Nastavte své řešení. Můžete to udělat pomocí následujících příkazů:

   ```dotnetcli
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   Tím se vytvoří projekty a spojí se dohromady v řešení. Váš adresář `SolutionWithSrcAndTest` by měl vypadat takto:

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. Přejděte do adresáře testovacího projektu a přidejte odkaz na `MyProject.Test` z `MyProject` .

   ```dotnetcli
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. Obnovit balíčky a sestavit projekty:

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. Spuštěním příkazu ověřte, že xUnit běží `dotnet test` . Pokud jste se rozhodli používat MSTest, měl by se místo toho spustit spouštěč konzoly MSTest.

A to je vše! Pomocí nástrojů příkazového řádku teď můžete svoji knihovnu testovat napříč všemi platformami. Pokud chcete pokračovat v testování, když máte všechno nastavené, testování knihovny je velmi jednoduché:

1. Proveďte změny v knihovně.
1. Spusťte testy z příkazového řádku v adresáři testu pomocí `dotnet test` příkazu.

Váš kód bude automaticky znovu vytvořen při vyvolání `dotnet test` příkazu.

## <a name="how-to-use-multiple-projects"></a>Používání více projektů

Běžnou potřebou pro větší knihovny je umístit funkci do různých projektů.

Představte si, že chcete vytvořit knihovnu, která by mohla být spotřebována v idiomatickou C# a F #. To by znamenalo, že uživatelé vaší knihovny ji spotřebují způsobem, který je přirozený pro C# nebo F #. Například v jazyce C# můžete knihovnu spotřebovat takto:

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

V F # může vypadat takto:

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

Mezi scénáře spotřeby, jako je to znamená, že rozhraní API, ke kterým se přistupovalo, musí mít jinou strukturu pro C# a F #.  Běžným přístupem k tomu je vytvoření faktoru pro všechny logiky knihovny do základního projektu, v projektech C# a F #, které definují vrstvy rozhraní API, které volají do tohoto základního projektu.  Zbytek oddílu bude používat následující názvy:

* **AwesomeLibrary. Core** – projekt jádra, který obsahuje všechny logiky pro knihovnu
* **AwesomeLibrary. CSharp** – projekt s veřejnými rozhraními API určenými pro využití v C #
* **AwesomeLibrary. FSharp** – projekt s veřejnými rozhraními API určenými pro využití v F #

V terminálu můžete spustit následující příkazy, které tvoří stejnou strukturu jako tato příručka:

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

Tím se přidají tři projekty výše a soubor řešení, který je propojuje dohromady. Vytvoření souboru řešení a propojení projektů vám umožní obnovit a sestavit projekty z nejvyšší úrovně.

### <a name="project-to-project-referencing"></a>Odkazování na projekt na projekt

Nejlepším způsobem, jak odkazovat na projekt, je použít .NET Core CLI pro přidání odkazu na projekt. Z adresářů projektu **AwesomeLibrary. CSharp** a **AwesomeLibrary. FSharp** můžete spustit následující příkaz:

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

Soubory projektu pro **AwesomeLibrary. CSharp** a **AwesomeLibrary. FSharp** budou nyní odkazovat na **AwesomeLibrary. Core** jako na `ProjectReference` cíl.  To můžete ověřit kontrolou souborů projektu a zobrazením následujících v těchto souborech:

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

Tuto část můžete přidat do každého souboru projektu ručně, pokud nechcete používat .NET Core CLI.

### <a name="structuring-a-solution"></a>Strukturování řešení

Dalším důležitým aspektem řešení pro více projektů je vytvoření dobré celkové struktury projektu. Můžete uspořádat kód tak, jak chcete, a Pokud propojíte každý projekt se souborem řešení pomocí, budete `dotnet sln add` moci spustit `dotnet restore` a `dotnet build` na úrovni řešení.
