---
title: Vývoj knihoven pomocí nástrojů pro různé platformy
description: Zjistěte, jak vytvářet knihovny .NET Core pomocí nástroje příkazového řádku .NET Core. Vytvoříte knihovnu, která podporuje více platforem.
author: cartermp
ms.date: 05/01/2017
ms.custom: seodec18
ms.openlocfilehash: f93c39d6225eef180634b238414fcda99750189f
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169362"
---
# <a name="developing-libraries-with-cross-platform-tools"></a>Vývoj knihoven pomocí nástrojů pro různé platformy

Tento článek popisuje, jak napsat knihoven pro .NET pomocí nástrojů příkazového řádku pro různé platformy. Rozhraní příkazového řádku poskytuje efektivní a nízké úrovně funkce, která funguje v jakémkoli operačním systému podporovaný. Stále můžete vytvářet knihovny se zmírněními hrozeb Visual Studio, a pokud je to upřednostňovaný prostředí [příručce sady Visual Studio](libraries-with-vs.md).

## <a name="prerequisites"></a>Požadavky

Potřebujete [.NET Core SDK a rozhraní příkazového řádku](https://www.microsoft.com/net/core) na vašem počítači nainstalovaný.

V částech tohoto dokumentu se zabývá verze rozhraní .NET Framework, je nutné [rozhraní .NET Framework](https://dotnet.microsoft.com) nainstalovaná na počítači s Windows.

Kromě toho pokud chcete podporovat starší cíle rozhraní .NET Framework, je potřeba nainstalovat cílení/developer Pack pro starší verze rozhraní framework z [stáhnout .NET archivuje stránky](https://dotnet.microsoft.com/download/archives). Najdete v této tabulce:

| Verze rozhraní .NET framework | Co se má stáhnout                                       |
| ---------------------- | ------------------------------------------------------ |
| 4.6.1                  | Rozhraní .NET framework 4.6.1 Targeting Pack                    |
| 4.6                    | Rozhraní .NET framework 4.6 Targeting Pack                      |
| 4.5.2                  | Rozhraní .NET framework 4.5.2 Developer Pack                    |
| 4.5.1                  | Rozhraní .NET framework 4.5.1 Developer Pack                    |
| 4.5                    | Sada Windows SDK pro aplikace pro Windows 8         |
| 4.0                    | Windows SDK pro Windows 7 a rozhraní .NET Framework 4         |
| 2.0, 3.0 a 3.5      | Modul Runtime rozhraní .NET framework 3.5 SP1 (nebo verze systému Windows 8 +) |

## <a name="how-to-target-the-net-standard"></a>Tom, jak cílit na .NET Standard

Pokud si nejste zcela obeznámeni s .NET Standard, přečtěte si [.NET Standard](../../standard/net-standard.md) Další informace.

V tomto článku je tabulka, která mapuje na různé implementace .NET Standard verze:

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

Zde je, co tato tabulka znamená, že pro účely vytvoření knihovny:

Verze .NET standardu vyberete bude kompromis mezi přístup k nejnovější rozhraní API a možnosti cílit na více implementací rozhraní .NET a .NET Standard verze. Řídit řadu targetable platformy a verze na verzi výběrem `netstandardX.X` (kde `X.X` je číslo verze) a jeho přidání do souboru projektu (`.csproj` nebo `.fsproj`).

Existují tři primární možnosti při cílení na .NET Standard, v závislosti na potřebách.

1. Můžete použít výchozí verzi .NET Standard poskytuje šablony - `netstandard1.4` – které dává vám přístup k většině rozhraní API na .NET Standard, ale stále kompatibilní s UWP, rozhraní .NET Framework 4.6.1 a budoucích .NET Standard 2.0.

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. Pomocí úpravy hodnoty v můžete použít nižší nebo vyšší verze rozhraní .NET Standard `TargetFramework` uzlu souboru projektu.
    
    Verze .NET standard jsou zpětně kompatibilní. To znamená, že `netstandard1.0` knihovny spouštět `netstandard1.1` platformy a vyšší. Však neexistuje žádná dopředné kompatibility – nižší platformy .NET Standard nemůže odkazovat na větší z nich. To znamená, že `netstandard1.0` knihovny nelze referenční dokumentace knihovny, které cílí `netstandard1.1` nebo vyšší. Vyberte verzi Standard, která má správné kombinace podpoře platforem a rozhraní API pro vaše potřeby. Doporučujeme `netstandard1.4` teď.
    
3. Pokud chcete cílit na rozhraní .NET Framework verze 4.0 nebo níže, nebo chcete použít rozhraní API, které jsou k dispozici v rozhraní .NET Framework, ale ne v .NET Standard (například `System.Drawing`), přečtěte si následující části a zjistěte, jak multitarget.

## <a name="how-to-target-the-net-framework"></a>Jak se zaměřit na rozhraní .NET Framework

> [!NOTE]
> Tyto pokyny předpokládají, že máte na svém počítači nainstalováno rozhraní .NET Framework. Odkazovat [požadavky](#prerequisites) získání závislostí nainstalovány.

Mějte na paměti, že některé verze rozhraní .NET Framework se tady použít jsou už v technické podpory. Odkazovat [rozhraní .NET Framework podpory životního cyklu nejčastější dotazy k zásadám](https://support.microsoft.com/gp/framework_faq/en-us) týkajících se nepodporovaných verzí.

Pokud chcete dosáhnout maximálního počtu vývojáři a projekty, použijte jako základní cílové rozhraní .NET Framework 4.0. Chcete-li cílit na rozhraní .NET Framework, je potřeba začít s použitím správné cílové rozhraní Framework Moniker (TFM), která odpovídá verzi rozhraní .NET Framework, kterou chcete podporovat.

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

Vložte tento TFM do `TargetFramework` část souboru projektu. Například tady je způsob, měli byste napsat knihovnu, která cílí na rozhraní .NET Framework 4.0:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

A to je všechno! I když to zkompilovat pouze pro rozhraní .NET Framework 4, můžete použít knihovnu v novějších verzích rozhraní .NET Framework.

## <a name="how-to-multitarget"></a>Jak Multitarget

> [!NOTE]
> Následující pokyny předpokládají, že máte na svém počítači nainstalováno rozhraní .NET Framework. Odkazovat [požadavky](#prerequisites) naleznete další závislosti, které je potřeba nainstalovat a kam stáhnete z.

Budete muset svůj projekt podporuje rozhraní .NET Framework a .NET Core cíleny na starší verze rozhraní .NET Framework. V tomto scénáři, pokud chcete použít pro novější cíle novějších rozhraní API a jazykovým konstrukcím, použijte `#if` direktiv ve vašem kódu. Potřebujete také přidat různé balíčky a závislosti pro každou platformu, na kterou cílíte zahrnout do různých rozhraní API potřebné pro každý případ.

Řekněme například, že máte knihovnu, která provádí síťové operace přes protokol HTTP. Pro .NET Standard a .NET Framework verze 4.5 nebo vyšší, můžete použít `HttpClient` třídy z `System.Net.Http` oboru názvů. Však nemají dřívějších verzích rozhraní .NET Framework `HttpClient` třídy, takže můžete použít `WebClient` třídy z `System.Net` obor názvů pro ty místo.

Váš soubor projektu může vypadat takto:

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

Všimněte si tři hlavní změny tady:

1. `TargetFramework` Uzlu se nahradil `TargetFrameworks`, a tři Tfm jsou vyjádřeny v.
1. Je `<ItemGroup>` uzel `net40 ` cílové souhrnné informace v jednom odkazu rozhraní .NET Framework.
1. Je `<ItemGroup>` uzel `net45` cílové stahování dva odkazy na rozhraní .NET Framework.

Systém sestavení je seznámen následující symboly preprocesoru používané `#if` direktivy:

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

Tady je příklad provedete použití podmíněné kompilace na cíle:

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

Pokud vytvoříte tento projekt s `dotnet build`, uvidíte tři adresářů podřízených adresáři `bin/` složky:

```
net40/
net45/
netstandard1.4/
```

Každý z nich obsahuje `.dll` soubory pro každý cíl.

## <a name="how-to-test-libraries-on-net-core"></a>Testování knihovny v rozhraní .NET Core

Je důležité mít možnost Testovat napříč platformami. Můžete použít buď [xUnit](https://xunit.github.io/) nebo MSTest úprav. Obě jsou dokonale vhodný pro testování vaší knihovny v .NET Core. Jak nastavit řešení s testovacími projekty, bude záviset na [struktura vašeho řešení](#structuring-a-solution). V následujícím příkladu se předpokládá, že live test a zdrojového adresáře ve stejném adresáři nejvyšší úrovně.

> [!NOTE]
> Tento mechanismus využívá některé [příkazy rozhraní příkazového řádku .NET Core](../tools/index.md). Zobrazit [dotnet nové](../tools/dotnet-new.md) a [dotnet sln](../tools/dotnet-sln.md) Další informace.

1. Nastavení řešení. Můžete tak učinit pomocí následujících příkazů:

   ```bash
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   To vytvoří projekty a propojit dohromady v řešení. V adresáři `SolutionWithSrcAndTest` by měl vypadat takto:

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. Přejděte do adresáře projektu testu a přidejte odkaz na `MyProject.Test` z `MyProject`.

   ```bash
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. Obnovení balíčků a sestavit projekty:

   ```bash
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. Ověřte, že xUnit běží spuštěním `dotnet test` příkazu. Pokud jste se rozhodli použít MSTest, byste místo toho spustit MSTest runner konzoly.
    
A to je všechno! Teď můžete otestovat vaši knihovnu na všech platformách pomocí nástrojů příkazového řádku. Pokračovat v testování teď, když máte všechno, co nastavíte, testování knihovny je velmi jednoduchý:

1. Proveďte změny v knihovně.
1. Spuštění testů z příkazového řádku v adresáři test s `dotnet test` příkazu.

Váš kód bude automaticky znovu vytvořen při vyvolání `dotnet test` příkazu.

## <a name="how-to-use-multiple-projects"></a>Jak používat více projektů

Běžné potřebu větší knihovny, je umístit funkce v různých projektech.

Představte si nepřejí vytvoří knihovnu, která by mohla využívat v idiomatickou C# a F#. To by znamenalo, že spotřebitelé knihovny je využívat způsoby, které jsou přirozené C# nebo F#. Například v jazyce C# může využívat knihovny takto:

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

V F#, může vypadat třeba takto:

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

Scénáře využití, jako je to znamená, že rozhraní API, ke kterému přistupujete musí mít odlišnou strukturu pro C# a F#.  Běžným přístupem k provádění to je zohlednit veškerou logiku knihovny do projektu core s C# a F# projekty definice rozhraní API vrstvy toto volání do tohoto projektu core.  Zbytek části budete používat následující názvy:

* **AwesomeLibrary.Core** – základní projekt, který bude obsahovat veškerou logiku pro knihovnu
* **AwesomeLibrary.CSharp** – projekt pomocí veřejných rozhraní API určené pro použití v jazyce C#
* **AwesomeLibrary.FSharp** – projekt pomocí veřejného rozhraní API určené pro využití vF#

Spuštěním následujících příkazů v terminálu vytvořit stejnou strukturu jako vodítko při tom tato:

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

Tato možnost přidá výše uvedených tří projektů a soubor řešení, které propojí je dohromady. Vytváření souboru řešení a propojování projektů vám umožní obnovit a sestavit projekty z nejvyšší úrovně.

### <a name="project-to-project-referencing"></a>Odkazování na projekt na projekt

Použití rozhraní příkazového řádku .NET Core k přidání odkazu na projekt je nejlepší způsob, jak odkazovat na projekt. Z **AwesomeLibrary.CSharp** a **AwesomeLibrary.FSharp** adresáře projektu, můžete spustit následující příkaz:

```console
$ dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

Soubory projektu pro obě **AwesomeLibrary.CSharp** a **AwesomeLibrary.FSharp** bude nyní odkaz **AwesomeLibrary.Core** jako `ProjectReference` cíl.  Můžete to ověřit tak kontrolu souborů projektu a zobrazuje v je následující:

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

V této části můžete ručně přidat do každého souboru projektu, pokud nechcete používat rozhraní příkazového řádku .NET Core.

### <a name="structuring-a-solution"></a>Strukturování řešení

Jiný důležitý aspekt řešení vícenásobného projektu se vytvářejí dobré celkovou strukturu projektu. Kód můžete uspořádat, ale potřebujete, a tak dlouho, dokud každý projekt odkazujete na soubor řešení s `dotnet sln add`, bude možné spustit `dotnet restore` a `dotnet build` na úrovni řešení.
