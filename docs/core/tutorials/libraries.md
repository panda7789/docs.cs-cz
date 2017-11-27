---
title: "Vývoj knihovny s křížové nástrojů platformy"
description: "Naučte se vytvářet knihovny pro .NET pomocí nástrojů příkazového řádku .NET Core."
keywords: "Rozhraní .NET, .NET core"
author: cartermp
ms.author: mairaw
ms.date: 05/01/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 9f6e8679-bd7e-4317-b3f9-7255a260d9cf
ms.openlocfilehash: 21f8a4f4862cabd21ab9017056f3f71706e8e9a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="developing-libraries-with-cross-platform-tools"></a>Vývoj knihovny s křížové nástrojů platformy

Tento článek popisuje jak napsat knihovny pro rozhraní .NET pomocí nástrojů příkazového řádku pro různé platformy. Rozhraní příkazového řádku poskytuje efektivní a nízké úrovně prostředí, které funguje napříč libovolný podporovaný operační systém. Přesto můžete vytvořit knihovny pomocí sady Visual Studio, a pokud je prostředí upřednostňované [v sadě Visual Studio příručce](libraries-with-vs.md).

## <a name="prerequisites"></a>Požadavky

Je třeba [.NET Core SDK a rozhraní příkazového řádku](https://www.microsoft.com/net/core) nainstalovaný na počítači.

V částech tohoto dokumentu se zabývá verze rozhraní .NET Framework, musíte [rozhraní .NET Framework](http://getdotnet.azurewebsites.net/) nainstalovaná na počítači s Windows.

Kromě toho, pokud chcete pro podporu starší rozhraní .NET Framework cíle, je potřeba nainstalovat cílení/vývojáře sady pro starší verze framework [.NET cílové platformy stránky](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html). Najdete v této tabulce:

| Verze rozhraní .NET framework | Co chcete stáhnout                                       |
| ---------------------- | ------------------------------------------------------ |
| 4.6.1                  | Pack cílení na rozhraní .NET framework 4.6.1                    |
| 4.6                    | Pack cílení na rozhraní .NET framework 4.6                      |
| 4.5.2                  | Rozhraní .NET framework 4.5.2 Developer Pack                    |
| 4.5.1                  | Rozhraní .NET framework 4.5.1 Developer Pack                    |
| 4.5                    | Sada Windows SDK pro aplikace pro Windows 8         |
| 4.0                    | Windows SDK pro systém Windows 7 a rozhraní .NET Framework 4         |
| 2.0, 3.0 a 3.5      | Modul Runtime rozhraní .NET framework 3.5 SP1 (nebo verze systému Windows 8 +) |

## <a name="how-to-target-the-net-standard"></a>Postup cílí na Standard .NET

Pokud si nejste poměrně obeznámeni s .NET Standard, podívejte se na [.NET Standard](../../standard/net-standard.md) Další informace.

V tomto článku je tabulka, která se mapuje na různé implementace .NET Standard verze:

[!INCLUDE [net-standard-table](~/includes/net-standard-table.md)]

Tady je tato tabulka znamená pro účely vytvoření knihovny:

Verze vyberete standardního .NET bude kompromis mezi přístup k nejnovější rozhraní API a schopnost cílové Další implementace rozhraní .NET a .NET Standard verze. Rozsah targetable platformy a verze řídit výběr verzi `netstandardX.X` (kde `X.X` je číslo verze) a její přidání do souboru projektu (`.csproj` nebo `.fsproj`).

Máte tři možnosti primární, když se cílí na Standard .NET, podle potřeby.

1. Můžete použít výchozí verze poskytl šablony - standardního .NET `netstandard1.4` – které dává vám přístup k většině rozhraní API v rozhraní .NET standardní ale stále mít kompatibilní s UPW, rozhraní .NET Framework 4.6.1 a chystaný standardní rozhraní .NET 2.0.

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. Můžete použít nižší nebo vyšší verze rozhraní .NET standardního změnou hodnoty v `TargetFramework` uzlu souboru projektu.
    
    .NET standard verze jsou zpětně kompatibilní. To znamená, že `netstandard1.0` knihovny spusťte na `netstandard1.1` platformy a vyšší. Však neexistuje žádná dopřednou kompatibilitu – nižší platformy .NET standardní nemůže odkazovat na ty, které jsou vyšší. To znamená, že `netstandard1.0` knihovny nelze reference knihovny, které cílí `netstandard1.1` nebo vyšší. Vyberte standardní verzi, která má správné směs podpora rozhraní API a platformy pro vaše potřeby. Doporučujeme, abyste `netstandard1.4` teď.
    
3. Pokud budete chtít cílové verze rozhraní .NET Framework 4.0 nebo níže, nebo chcete použít rozhraní API, které jsou k dispozici v rozhraní .NET Framework, ale není v .NET Standard (například `System.Drawing`), přečtěte si následující části a zjistěte, jak multitarget.

## <a name="how-to-target-the-net-framework"></a>Postup cílové rozhraní .NET Framework

> [!NOTE]
> Tyto pokyny předpokládají, že máte rozhraní .NET Framework, který je nainstalovaný na počítači. Odkazovat [požadavky](#prerequisites) získat závislosti nainstalována.

Mějte na paměti, že některá z verzí rozhraní .NET Framework použít se zde jsou již v technické podpory. Odkazovat [rozhraní .NET Framework podporu životního cyklu nejčastější dotazy k zásadám](https://support.microsoft.com/gp/framework_faq/en-us) o Nepodporovaná verze.

Pokud chcete k dosažení maximální počet vývojáři a projekty, použijte jako cíl vaše základní rozhraní .NET Framework 4.0. Pokud chcete zacílit rozhraní .NET Framework, musíte začít s využitím správný cílový Framework Přezdívka (TFM) odpovídající verzi rozhraní .NET Framework, které chcete podporovat.

```
.NET Framework 2.0   --> net20
.NET Framework 3.0   --> net30
.NET Framework 3.5   --> net35
.NET Framework 4.0   --> net40
.NET Framework 4.5   --> net45
.NET Framework 4.5.1 --> net451
.NET Framework 4.5.2 --> net452
.NET Framework 4.6   --> net46
.NET Framework 4.6.1 --> net461
.NET Framework 4.6.2 --> net462
.NET Framework 4.7   --> net47
```

Potom vložte tento TFM do `TargetFramework` části souboru projektu. Můžete zde je ukázka, jak by zápisu knihovnu, která cílí rozhraní .NET Framework 4.0:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

A je to! I když to zkompilovat pouze pro rozhraní .NET Framework 4, můžete v knihovně na novější verze rozhraní .NET Framework.

## <a name="how-to-multitarget"></a>Postup Multitarget

> [!NOTE]
> Následující pokyny předpokládají, že máte rozhraní .NET Framework, který je nainstalovaný na počítači. Odkazovat [požadavky](#prerequisites) části Další závislosti, které je třeba nainstalovat a kam je z chcete stáhnout.

Musíte mít starší verze rozhraní .NET Framework Pokud projekt podporuje rozhraní .NET Framework a .NET Core. V tomto scénáři, pokud chcete použít novější rozhraní API a jazykové konstrukty pro novější cíle, použijte `#if` direktivy v kódu. Můžete také může být nutné přidat jiné balíčky a závislosti pro každou platformu, kterou jste cílení zahrnout různých rozhraní API pro každý případ potřeby.

Řekněme například, že je vaše knihovna, která provádí síťových operací přes protokol HTTP. Pro .NET Standard a rozhraní .NET Framework verze 4.5 nebo vyšší, můžete použít `HttpClient` třídy z `System.Net.Http` oboru názvů. Však nemají starší verze rozhraní .NET Framework `HttpClient` třídy, takže můžete použít `WebClient` třídy z `System.Net` obor názvů pro ty, místo toho.

Soubor projektu může vypadat například takto:

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

Můžete si všimnout tři hlavní změny tady:

1. `TargetFramework` Uzlu nahradila `TargetFrameworks`, a tři TFMs jsou vyjádřeny v.
1. Je `<ItemGroup>` uzel `net40 ` cíl stahování v jeden odkaz na rozhraní .NET Framework.
1. Je `<ItemGroup>` uzel `net45` cíl stahování v odkazech na dvě rozhraní .NET Framework.

Systém sestavení si je vědoma následující preprocesoru symboly použité v `#if` direktivy:

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

Tady je příklad které využijí Podmíněná kompilace za cíl:

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
            string url = "http://www.dotnetfoundation.org/";

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
            string url = "http://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

Pokud vytvoříte tento projekt s `dotnet build`, můžete si všimnout tři adresáře `bin/` složky:

```
net40/
net45/
netstandard1.4/
```

Každá z těchto obsahovat `.dll` soubory pro každý cíl.

## <a name="how-to-test-libraries-on-net-core"></a>Postup testování knihovny na .NET Core

Je důležité, abyste mohli otestovat napříč platformami. Můžete použít buď [xUnit](http://xunit.github.io/) nebo Mstestu z pole. Jsou obě perfektně vhodný pro testování vaší knihovny na .NET Core jednotky. Jak nastavit řešení pomocí projektů testování, bude záviset na [struktura řešení](#structuring-a-solution). V následujícím příkladu se předpokládá, že test a zdrojového adresáře za provozu ve stejném adresáři nejvyšší úrovně.

> [!NOTE]
> To se využívá část [.NET Core rozhraní příkazového řádku](../tools/index.md). V tématu [dotnet nové](../tools/dotnet-new.md) a [SLN – dotnet](../tools/dotnet-sln.md) Další informace.

1. Nastavte řešení. Můžete tak učinit pomocí následujících příkazů:

   ```bash
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   Tato akce vytvoří projekty a propojit je společně v řešení. V adresáři `SolutionWithSrcAndTest` by měla vypadat takto:

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. Přejděte do adresáře k testovacímu projektu a přidejte odkaz na `MyProject.Test` z `MyProject`.

   ```bash
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. Obnovení balíčků a sestavení projektů:

   ```bash
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. Ověřte, že xUnit běží spuštěním `dotnet test` příkaz. Pokud zvolíte použití Mstestu, měli místo toho spustit nástroj runner Mstestu konzoly.
    
A je to! Nyní můžete otestovat knihovnu pro všechny platformy, pomocí nástrojů příkazového řádku. Chcete-li pokračovat, testování nyní, když máte všechno nastavit, aby testování vaše knihovna je velmi jednoduchý:

1. Proveďte změny své knihovny.
1. Spouštění testů z příkazového řádku v adresáři test pomocí `dotnet test` příkaz.

Váš kód bude automaticky znovu vytvořen při vyvolání `dotnet test` příkaz.

## <a name="how-to-use-multiple-projects"></a>Použití více projektů

Běžné potřebu větší knihovny je funkce umístit do různých projektů.

Představte si, že jste si přáli pro sestavení knihovny, které by mohly spotřebovat v idiomatickou C# a F #. To znamená, že příjemci ve své knihovny je můžou využívat způsoby, které jsou přirozené C# nebo F #. Například v jazyce C# může využívat knihovně takto:

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

V jazyce F # může vypadat například takto:

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

Spotřeba scénáře, jako to znamená, že rozhraní API přistupuje musejí mít jinou strukturu pro C# a F #.  Společný přístup k provedení to je zohlednit veškerou logiku knihovny do projektu jádra, s projekty C# a F # definice rozhraní API vrstvy, které volání do tohoto projektu jádra.  Zbývající části použije tyto názvy:

* **AwesomeLibrary.Core** – základní projektu, který obsahuje veškerou logiku pro knihovnu
* **AwesomeLibrary.CSharp** -projekt se veřejná rozhraní API určená pro používání v jazyce C#
* **AwesomeLibrary.FSharp** -projekt se veřejná rozhraní API určená pro používání v jazyce F #

V terminálu k vytvoření stejná struktura jako tento průvodce můžete spustit následující příkazy:

```console
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang F#
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

Tím se přidá výše tři projekty a řešení soubor, který je společně odkazů. Soubor řešení vytváření a propojování projekty vám umožní obnovit a sestavení projektů z nejvyšší úrovně.

### <a name="project-to-project-referencing"></a>Odkazování na projekt na projekt

Nejlepší způsob, jak odkazovat na projekt je použití rozhraní příkazového řádku .NET Core přidat odkaz na projekt. Z **AwesomeLibrary.CSharp** a **AwesomeLibrary.FSharp** adresáře projektu, můžete spustit následující příkaz:

```console
$ dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

Soubory projektu pro obě **AwesomeLibrary.CSharp** a **AwesomeLibrary.FSharp** bude nyní odkaz **AwesomeLibrary.Core** jako `ProjectReference` cíl.  Můžete to ověřit tak, že zkontrolujete soubory projektu a zobrazuje následující v nich:

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

V této části můžete ručně přidat ke každému souboru projektu, pokud nechcete používat rozhraní příkazového řádku .NET Core.

### <a name="structuring-a-solution"></a>Strukturování řešení

Dalším důležitým aspektem řešení vícenásobného projektu navazuje dobrý celková struktura projektu. Kód můžete uspořádat, ale chcete, a také propojit každý projekt, ze souboru řešení s `dotnet sln add`, nebudete moci spustit `dotnet restore` a `dotnet build` na úrovni řešení.
