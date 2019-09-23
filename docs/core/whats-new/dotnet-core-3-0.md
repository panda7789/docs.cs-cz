---
title: Co je nového v .NET Core 3.0
description: Přečtěte si o nových funkcích, které najdete v .NET Core 3,0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 09/17/2019
ms.openlocfilehash: 45d5117f264a24c2658debad9a111d4d4b9b9a8e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182444"
---
# <a name="whats-new-in-net-core-30-release-candidate-1"></a>Co je nového v .NET Core 3,0 (Release Candidate 1)

Tento článek popisuje, co je v .NET Core 3,0 až Release Candidate 1 (RC1) novinkou. Jedním z největších vylepšení je podpora desktopových aplikací pro Windows (jenom Windows). Pomocí aplikace .NET Core 3,0 SDK desktopové plochy systému Windows můžete přenést model Windows Forms aplikace a Windows Presentation Foundation (WPF). Aby bylo jasné, že je komponenta Desktop systému Windows podporována a je součástí systému Windows. Další informace najdete v části [Windows Desktop](#windows-desktop) dále v tomto článku.

.NET Core 3,0 přidává podporu pro C# 8,0. Důrazně doporučujeme používat [Visual Studio 2019 16,3 Preview 4](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+preview), [Visual Studio pro Mac 8,3](/visualstudio/mac/install-preview)nebo [Visual Studio Code](https://code.visualstudio.com/) s  **C# rozšířením**.

[Stáhněte si a začněte s .NET Core 3,0 RC1](https://aka.ms/netcore3download) hned na Windows, MacOS nebo Linux.

Další informace o jednotlivých vydaných verzích Preview najdete v následujících oznámeních:

- [Oznámení .NET Core 3,0 RC1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-release-candidate-1/)
- [Oznámení .NET Core 3,0 Preview 9](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-9/)
- [Oznámení .NET Core 3,0 Preview 8](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-8/)
- [Oznámení .NET Core 3,0 Preview 7](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-7/)
- [Oznámení .NET Core 3,0 Preview 6](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-6/)
- [Oznámení .NET Core 3,0 Preview 5](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-5/)
- [Oznámení .NET Core 3,0 Preview 4](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-4/)
- [Oznámení .NET Core 3,0 Preview 3](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-3/)
- [Oznámení .NET Core 3,0 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)
- [Oznámení .NET Core 3,0 Preview 1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)

## <a name="production-supported-preview"></a>Verze Preview podporovaná v produkci

.NET Core RC1 se považuje za produkční, které je připravené Microsoftem a je plně podporovaná. Počínaje verzí Preview 7 se vydání verzí zaměřuje na polštinu .NET Core 3,0 místo přidávání nových funkcí. Další informace o tom, co se změnilo v RC1, najdete v [oznámení RC1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-release-candidate-1/).

Pokud používáte předchozí verzi Preview, musíte přejít na RC1, aby pokračovala podpora "začít živě".

## <a name="net-core-sdk-windows-installer"></a>.NET Core SDK Instalační služba systému Windows

Instalační program MSI pro Windows se od verze .NET Core 3,0 změnil. Instalační programy sady SDK teď upgradují verze sady SDK, které jsou na místě. Pásma funkcí jsou definována ve *stovkách* v oddílu *patch* tohoto čísla verze. Například **3,0. _101_**  a **3,0. _201_**  jsou verze ve dvou různých pruzích funkcí během **3,0. _101_**  a **3,0. _199_**  jsou ve stejném pásmu funkcí. A při .NET Core SDK **3,0. _101_**  je nainstalováno, .NET Core SDK **3,0. _100_**  se odebere z počítače, pokud existuje. Při .NET Core SDK **3,0. _200_**  je nainstalována na stejném počítači .NET Core SDK **3,0. _101_**  nebude odebráno.

Další informace o tom, jak se správou verzí, najdete v tématu Přehled toho, [jak je verze .NET Core](../versions/index.md).

## <a name="c-80-preview"></a>C#8,0 Preview

.NET Core 3,0 podporuje C# 8 Preview. Další informace o C# funkcích 8,0 najdete v tématu [co je nového v C# 8,0](../../csharp/whats-new/csharp-8.md).

## <a name="net-standard-21"></a>.NET Standard 2,1

I když .NET Core 3,0 podporuje **.NET Standard 2,1**, výchozí `dotnet new classlib` šablona vygeneruje projekt, který cílí na **.NET Standard 2,0**. Chcete-li cílit na **.NET Standard 2,1**, upravte soubor projektu a `TargetFramework` změňte vlastnost `netstandard2.1`na:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

</Project>
```

Pokud používáte Visual Studio, budete potřebovat [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), protože Visual Studio 2017 nepodporuje **.NET Standard 2,1** nebo **.NET Core 3,0**.

## <a name="improved-net-core-version-apis"></a>Vylepšená rozhraní API verze .NET Core

Počínaje rozhraním .NET Core 3,0 verze rozhraní API poskytovaná pomocí .NET Core nyní vrátí očekávané informace. Příklad:

```csharp
System.Console.WriteLine($"Environment.Version: {System.Environment.Version}");

// Old result
//   Environment.Version: 4.0.30319.42000
//
// New result
//   Environment.Version: 3.0.0
```

```csharp
System.Console.WriteLine($"RuntimeInformation.FrameworkDescription: {System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription}");

// Old result
//   RuntimeInformation.FrameworkDescription: .NET Core 4.6.27415.71
//
// New result
//   RuntimeInformation.FrameworkDescription: .NET Core 3.0.0-preview4-27615-11
```

> [!WARNING]
> Zásadní změna. To je technicky zásadní změna, protože se změnilo schéma správy verzí.

## <a name="net-platform-dependent-intrinsics"></a>Vnitřní objekty závislé na platformě .NET

Byla přidána rozhraní API, která umožňují přístup k určitým pokynům pro procesor orientovaným na výkon, jako jsou **SIMD** nebo sady **instrukcí pro manipulaci** . Tyto pokyny vám pomůžou dosáhnout výrazného zlepšení výkonu v některých scénářích, jako je efektivní zpracování dat paralelně.

V případě potřeby se pomocí těchto pokynů Vylepšete knihovny .NET, aby se zlepšil výkon.

Další informace najdete v tématu věnovaném [vnitřním procesorům platformy .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).

## <a name="default-executables"></a>Výchozí spustitelné soubory

.NET Core teď ve výchozím nastavení vytváří [spustitelné soubory závislé na rozhraní](../deploying/index.md#framework-dependent-executables-fde) . Toto chování je nové u aplikací, které používají globálně nainstalovanou verzi .NET Core. Dříve mohli pouze [samostatně nasazená nasazení](../deploying/index.md#self-contained-deployments-scd) vyvolat spustitelný soubor.

Během `dotnet build` nebo`dotnet publish`se vytvoří spustitelný soubor, který odpovídá prostředí a platformě používané sady SDK. Pomocí těchto spustitelných souborů můžete očekávat stejné věci jako jiné nativní spustitelné soubory, jako například:

- Můžete dvakrát kliknout na spustitelný soubor.
- Aplikaci můžete spustit z příkazového řádku přímo, například `myapp.exe` ve Windows, a `./myapp` v systémech Linux a MacOS.

## <a name="single-file-executables"></a>Spustitelné soubory s jedním souborem

`dotnet publish` Příkaz podporuje balení vaší aplikace do spustitelného souboru specifického pro jednotlivé platformy. Spustitelný soubor je samorozbalovací a obsahuje všechny závislosti (včetně nativních), které jsou nutné ke spuštění vaší aplikace. Při prvním spuštění aplikace se aplikace extrahuje do adresáře na základě názvu aplikace a identifikátoru buildu. Spuštění je rychlejší, když aplikaci znovu spustíte. Pokud se nepoužila nová verze, aplikace se už nebude muset extrahovat druhou dobu.

Chcete-li publikovat soubor s jedním souborem, nastavte `PublishSingleFile` v projektu nebo na příkazovém řádku `dotnet publish` pomocí příkazu:

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

-nebo-

```dotnetcli
dotnet publish -r win10-x64 /p:PublishSingleFile=true
```

Další informace o publikování v jednom souboru najdete v [dokumentu návrhu sady prostředků s jedním souborem](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).

## <a name="assembly-linking"></a>Propojení sestavení

Sada .NET Core 3,0 SDK je dodávána s nástrojem, který umožňuje zmenšit velikost aplikací analýzou IL a oříznutím nepoužívaných sestavení.

Samostatné aplikace zahrnují vše potřebné ke spuštění kódu, aniž by bylo nutné nainstalovat rozhraní .NET do hostitelského počítače. Ale hodně, kolikrát aplikace jenom vyžaduje malou podmnožinu rozhraní, a další nepoužívané knihovny by se daly odebrat.

Rozhraní .NET Core nyní obsahuje nastavení, které bude používat nástroj [linkeru Il](https://github.com/mono/linker) ke kontrole Il vaší aplikace. Tento nástroj zjistí, jaký kód je požadován, a poté ořízne nepoužívané knihovny. Tento nástroj může významně snížit velikost nasazení některých aplikací.

Chcete-li tento nástroj povolit, `<PublishTrimmed>` přidejte do projektu nastavení a publikujte samostatně uzavřenou aplikaci:

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```dotnetcli
dotnet publish -r <rid> -c Release
```

Příklad: základní šablona projektu "Hello World", která je součástí, je-li publikována, má velikost přibližně 70 MB. Pomocí `<PublishTrimmed>`této velikosti se velikost zmenší na přibližně 30 MB.

Je důležité vzít v úvahu, že aplikace nebo architektury (včetně ASP.NET Core a WPF), které používají reflexi nebo související dynamické funkce, budou často přerušit při oříznutí. K tomuto zlomku dochází, protože linker neví o tomto dynamickém chování a nemůže určit, které typy rozhraní jsou pro reflexi vyžadovány. Nástroj linkeru IL se dá nakonfigurovat tak, aby se na tento scénář dozvěděl.

Nad všemi ostatními nezapomeňte aplikaci otestovat po jejím oříznutí.

Další informace o nástroji linkeru IL naleznete v [dokumentaci](https://aka.ms/dotnet-illink) nebo v úložišti [mono/linker]( https://github.com/mono/linker) .

## <a name="tiered-compilation"></a>Vrstvená kompilace

[Vrstvená kompilace](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) je ve výchozím nastavení zapnuté pomocí .NET Core 3,0. Tato funkce umožňuje modulu runtime pružně použít kompilátor JIT (just-in-time) a získat tak lepší výkon.

Hlavní výhodou TC je povolit (znovu) jitting metody s úrovní nižší kvality, ale rychleji nebo s vyšší kvalitou, ale nižší úrovní. To pomáhá zvýšit výkon aplikace, protože projde různými fázemi provádění, od spuštění po ustáleném stavu. To se liší od přístupu bez použití TC, kde je každá metoda zkompilována jedním způsobem (stejně jako vysoká úroveň kvality), která je pro výkon při spuštění posunuta na ustálený stav.

Chcete-li povolit rychlou JIT (zpracovaných kompilátorem JIT kód vrstvy 0), použijte toto nastavení v souboru projektu:

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>true</TieredCompilationQuickJit>
</PropertyGroup>
```

Chcete-li úplně zakázat použití TC, použijte toto nastavení v souboru projektu:

```xml
<TieredCompilation>false</TieredCompilation>
```

## <a name="readytorun-images"></a>ReadyToRun image

Můžete zlepšit čas spuštění aplikace .NET Core kompilováním sestavení aplikace jako formátu ReadyToRun (R2R). R2R je forma kompilace v čase před zahájením (AOT).

R2R binární soubory zlepšují výkon při spuštění tím, že snižují množství práce, které kompilátor JIT (just-in-time) potřebuje k tomu, aby se vaše aplikace načítají. Binární soubory obsahují podobný nativní kód v porovnání s tím, co by kompilátor JIT vytvořil. R2R binární soubory jsou však větší, protože obsahují kód pro mezilehlé jazyky (IL), který je stále potřeba pro některé scénáře, a nativní verzi stejného kódu. R2R je k dispozici pouze v případě, že publikujete samostatnou aplikaci, která cílí na konkrétní běhové prostředí (RID), jako je Linux x64 nebo Windows x64.

Chcete-li zkompilovat projekt jako ReadyToRun, postupujte takto:

01. `<PublishReadyToRun>` Přidat nastavení do projektu

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. Publikujte samostatně uzavřenou aplikaci. Tento příkaz například vytvoří samostatnou aplikaci pro 64 verzi Windows:

    ```dotnetcli
    dotnet publish -c Release -r win-x64 --self-contained true
    ```

### <a name="cross-platformarchitecture-restrictions"></a>Omezení pro různé platformy a architektury

Kompilátor ReadyToRun v současné době nepodporuje cílení na více platforem. Je nutné kompilovat na daném cíli. Například pokud chcete image R2R pro Windows x64, musíte v tomto prostředí spustit příkaz publikovat.

Výjimky pro cílení na více platforem:

- Systém Windows x64 lze použít ke kompilaci imagí Windows ARM32, ARM64 a x86.
- K kompilování imagí Windows ARM32 lze použít systém Windows x86.
- Linux x64 lze použít ke kompilaci imagí ARM32 a ARM64 pro Linux.

## <a name="build-copies-dependencies"></a>Sestavení kopíruje závislosti

`dotnet build` Příkaz nyní kopíruje závislosti NuGet pro vaši aplikaci z mezipaměti NuGet do výstupní složky sestavení. Dříve se závislosti zkopírovaly jenom jako součást `dotnet publish`.

Existují některé operace, jako je propojování a publikování stránek Razor, které budou nadále vyžadovat publikování.

## <a name="local-tools"></a>Místní nástroje

.NET Core 3,0 zavádí místní nástroje. Místní nástroje jsou podobné [globálním nástrojům](../tools/global-tools.md) , ale jsou přidruženy k určitému umístění na disku. Místní nástroje nejsou globálně dostupné a distribuují se jako balíčky NuGet.

> [!WARNING]
> Pokud jste si vyzkoušeli místní nástroje v rozhraní .NET Core 3,0 Preview 1 `dotnet tool restore` , `dotnet tool install`jako je třeba spuštění nebo, odstraňte složku mezipaměti místních nástrojů. V opačném případě místní nástroje nebudou fungovat v novější verzi. Tato složka je umístěna v umístění:
>
> V macOS, Linux:`rm -r $HOME/.dotnet/toolResolverCache`
>
> Ve Windows:`rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`

Místní nástroje spoléhají na název `dotnet-tools.json` souboru manifestu v aktuálním adresáři. Tento soubor manifestu definuje nástroje, které jsou k dispozici v této složce a níže. Můžete distribuovat soubor manifestu s vaším kódem, aby bylo zajištěno, že kdokoli, kdo spolupracuje s vaším kódem, může obnovit a použít stejné nástroje.

U globálních i místních nástrojů se vyžaduje kompatibilní verze modulu runtime. Mnoho nástrojů, které jsou aktuálně na NuGet.org Target pro .NET Core Runtime 2,1. Pokud chcete tyto nástroje nainstalovat globálně nebo lokálně, budete si muset nainstalovat [modul runtime .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1).

## <a name="major-version-roll-forward"></a>Hlavní verze – posunutí – posun

.NET Core 3,0 zavádí funkci pro výslovný souhlas, která umožňuje aplikaci přejít na nejnovější hlavní verzi .NET Core. Kromě toho bylo přidáno nové nastavení, které řídí, jak se ve vaší aplikaci aplikuje posunutí. Dá se nakonfigurovat následujícími způsoby:

- Vlastnost souboru projektu:`RollForward`
- Vlastnost konfiguračního souboru modulu runtime:`rollForward`
- Proměnná prostředí:`DOTNET_ROLL_FORWARD`
- Argument příkazového řádku:`--roll-forward`

Je nutné zadat jednu z následujících hodnot. Pokud je nastavení vynecháno, je výchozí hodnota **podverze** .

- **LatestPatch**\
Vraťte se k nejvyšší verzi opravy. Tím se zakáže dílčí verze s posunem.
- **Moll**\
V případě, že chybí požadovaná dílčí verze, převeďte nahoru na nejnižší nižší verzi. Pokud je k dispozici požadovaná dílčí verze, použije se zásada **LatestPatch** .
- **Nejdůležitější**\
Pokud chybí požadovaná hlavní verze, převeďte ji nahoru na nejnižší nejvyšší hlavní verzi a nejnižší podverzi. Pokud je k dispozici požadovaná hlavní verze, použije se **vedlejší** zásada.
- **LatestMinor**\
Převeďte do nejvyšší dílčí verze, i když je k dispozici požadovaná dílčí verze. Určeno pro scénáře hostování součástí.
- **LatestMajor**\
Převeďte do nejvyšší hlavní a nejvyšší dílčí verze, a to i v případě, že je k dispozici požadovaná hlavní verze. Určeno pro scénáře hostování součástí.
- **Dezaktivovat**\
Nezadávejte vše. Vytvoří se jenom vazba na určenou verzi. Tyto zásady se nedoporučují pro obecné použití, protože zakazují možnost navrátit se k nejnovějším opravám. Tato hodnota se doporučuje jenom pro testování.

Kromě nastavení **Zakázat** bude pro všechna nastavení použita nejvyšší dostupná verze opravy.

## <a name="windows-desktop"></a>Plocha Windows

.NET Core 3,0 podporuje desktopové aplikace Windows pomocí Windows Presentation Foundation (WPF) a model Windows Forms. Tyto architektury také podporují použití moderních ovládacích prvků a Fluent stylování z knihovny XAML uživatelského rozhraní systému Windows (WinUI) přes [ostrovy XAML](/windows/uwp/xaml-platform/xaml-host-controls).

Součást Desktop systému Windows je součástí sady Windows .NET Core 3,0 SDK.

Novou aplikaci WPF nebo model Windows Forms můžete vytvořit pomocí následujících `dotnet` příkazů:

```dotnetcli
dotnet new wpf
dotnet new winforms
```

Visual Studio 2019 přidává **nové šablony projektů** pro .net Core 3,0 model Windows Forms a WPF.

Další informace o tom, jak přenést existující aplikaci .NET Framework, naleznete v tématu [port WPF Projects](../porting/wpf.md) and [port model Windows Forms Projects](../porting/winforms.md).

## <a name="com-callable-components---windows-desktop"></a>Komponenty s podporou modelu COM – Desktop Windows

Ve Windows teď můžete vytvářet spravované komponenty, které lze volat v modelu COM. Tato možnost je zásadní pro použití .NET Core s modely doplňku COM a také k zajištění parity s .NET Framework.

Na rozdíl od .NET Framework, kde se *Knihovna Mscoree. dll* použila jako server com, .NET Core při sestavování komponenty com přidá nativní spouštěcí knihovnu DLL do adresáře *bin* .

Příklad vytvoření komponenty modelu COM a její využití naleznete v [ukázce modelu COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).

## <a name="msix-deployment---windows-desktop"></a>Nasazení MSIX – Desktop Windows

[MSIX](https://docs.microsoft.com/windows/msix/) je nový formát balíčku aplikace systému Windows. Dá se použít k nasazení desktopových aplikací .NET Core 3,0 do Windows 10.

[Projekt pro balení aplikace pro systém Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), který je k dispozici v aplikaci Visual Studio 2019, umožňuje vytvářet balíčky MSIX pomocí aplikací .NET Core s využitím [vlastních součástí](../deploying/index.md#self-contained-deployments-scd) .

Soubor projektu .NET Core musí určovat podporované běhové moduly ve `<RuntimeIdentifiers>` vlastnosti:

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="winforms-high-dpi"></a>Vysoké rozlišení DPI pro WinForms

Aplikace .NET Core model Windows Forms můžou nastavit režim s vysokým <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>rozlišením DPI pomocí. Metoda nastaví odpovídající režim vysoké úrovně dpi, pokud nastavení nebylo nastaveno jiným způsobem, jako `App.Manifest` je `Application.Run`nebo P/Invoke. `SetHighDpiMode`

Možné `highDpiMode` hodnoty, jak je vyjádřené <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> výčtem:

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

Další informace o režimech vysokého rozlišení DPI najdete v tématu [vývoj desktopových aplikací s vysokým rozlišením v systému Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).

## <a name="ranges-and-indices"></a>Rozsahy a indexy

Nový <xref:System.Index?displayProperty=nameWithType> typ lze použít k indexování. Můžete vytvořit jednu z `int` těchto počtů od začátku nebo s operátorem prefix `^` (C#), který se počítá od konce:

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

Je zde také <xref:System.Range?displayProperty=nameWithType> typ, který se skládá ze dvou `Index` hodnot, jeden pro začátek a jeden pro konec a `x..y` lze jej zapsat s výrazem rozsahu (C#). Pak můžete indexovat pomocí `Range`, který vytváří řez:

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

Další informace najdete v [kurzu rozsahy a indexy](../../csharp/tutorials/ranges-indexes.md).

## <a name="async-streams"></a>Asynchronní streamy

Typ je nová asynchronní <xref:System.Collections.Generic.IEnumerable%601>verze. <xref:System.Collections.Generic.IAsyncEnumerable%601> Jazyk vám umožní `await foreach` `IAsyncEnumerable<T>` využít jejich prvky a využít `yield return` je k vytváření prvků.

Následující příklad ukazuje produkci a spotřebu asynchronních datových proudů. Příkaz je asynchronní a sám používá `yield return` k tvorbě asynchronního datového proudu pro volající. `foreach` Tento vzor (použití `yield return`) je doporučeným modelem pro vytváření asynchronních datových proudů.

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

Kromě `await foreach`toho je možné také vytvořit asynchronní iterátory, například iterátor, který `IAsyncEnumerable/IAsyncEnumerator` vrátí `yield` , který můžete i `await` v. Pro objekty, které je třeba uvolnit, můžete použít `IAsyncDisposable`, které BCL různé typy, `Stream` například a `Timer`.

Další informace najdete v [kurzu asynchronní streamy](../../csharp/tutorials/generate-consume-asynchronous-stream.md).

## <a name="ieee-floating-point-improvements"></a>Vylepšení standardu IEEE s plovoucí desetinnou čárkou

Rozhraní API s plovoucí desetinnou čárkou se aktualizují tak, aby odpovídalo [revizi IEEE 754-2008](https://en.wikipedia.org/wiki/IEEE_754-2008_revision). Cílem těchto změn je vystavit všechny **požadované** operace a zajistit, aby byly vyhovující požadavkům standardu IEEE. Další informace o vylepšeních s plovoucí desetinnou čárkou naleznete v příspěvku na blogu [.NET Core 3,0 v oblasti analýzy a formátování plovoucí desetinné](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) čárky.

Mezi aktualizace pro analýzu a formátování patří:

- Správně Analyzujte a zaokrouhlujte vstupy libovolné délky.
- Správně Analyzujte a formátujete záporné hodnoty nula.
- Správně analyzovat `Infinity` a `NaN` provést kontrolu bez rozlišení velkých a malých písmen a povolit volitelnou předchozí `+` hodnotu.

Mezi <xref:System.Math?displayProperty=nameWithType> nová rozhraní API patří:

- <xref:System.Math.BitIncrement(System.Double)>ani<xref:System.Math.BitDecrement(System.Double)>\
Odpovídá operacím `nextDown` IEEE a.`nextUp` Vrátí nejmenší číslo s plovoucí desetinnou čárkou, které porovná větší nebo menší než vstup (v uvedeném pořadí). Například `Math.BitIncrement(0.0)` vrátí `double.Epsilon`.

- <xref:System.Math.MaxMagnitude(System.Double,System.Double)>ani<xref:System.Math.MinMagnitude(System.Double,System.Double)>\
Odpovídá operacím `minNumMag` IEEE a,vracíhodnotu,kterájevětšínebomenšívrozsahudvouvstupů(vuvedenémpořadí).`maxNumMag` Například `Math.MaxMagnitude(2.0, -3.0)` vrátí `-3.0`.

- <xref:System.Math.ILogB(System.Double)>\
Odpovídá operaci `logB` IEEE, která vrací celočíselnou hodnotu, vrátí protokol integrálního protokolu Base-2 vstupního parametru. Tato metoda je prakticky stejná jako `floor(log2(x))`, ale byla provedena s minimální chybou zaokrouhlení.

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
Odpovídá operaci `x * pow(2, n)`IEEE, která přebírá celočíselnou hodnotu, vrátí ji efektivně, ale provede minimální chybu zaokrouhlení. `scaleB`

- <xref:System.Math.Log2(System.Double)>\
Odpovídá operaci `log2` IEEE, vrátí logaritmus o základu 2. Minimalizuje chybu zaokrouhlování.

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
Odpovídá operaci `fma` IEEE, provádí přidaný násobek. To znamená, že se `(x * y) + z` jedná o jedinou operaci, čímž se minimalizuje chyba zaokrouhlování. Příkladem může být `FusedMultiplyAdd(1e308, 2.0, -1e308)` vrácení. `1e308` Funkce Regular `(1e308 * 2.0) - 1e308` vrátí `double.PositiveInfinity`.

- <xref:System.Math.CopySign(System.Double,System.Double)>\
Odpovídá operaci `x`IEEE, vrací hodnotu, `y`ale s znaménkem. `copySign`

## <a name="fast-built-in-json-support"></a>Rychlá integrovaná podpora JSON

Uživatelé rozhraní .NET mají převážně na [**JSON.NET**](https://www.newtonsoft.com/json) a další oblíbené knihovny JSON, které budou mít i nadále dobré možnosti. **JSON.NET** používá řetězce .NET jako základní datový typ, který je v digestoři UTF-16.

Nová integrovaná podpora JSON je vysoce výkonná, nízká alokace a založená na `Span<byte>`. Do .NET Core 3,0 <xref:System.Text.Json?displayProperty=nameWithType> oboru názvů se přidaly tři nové hlavní typy související s JSON. Tyto typy *ještě* nepodporují serializaci a deserializaci objektu CLR (POCO).

### <a name="utf8jsonreader"></a>Utf8JsonReader

<xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType>je pro text JSON s kódováním UTF-8 s vysokým výkonem k dispozici vysoce výkonné a nízké přidělení, načtený z `ReadOnlySpan<byte>`. `Utf8JsonReader` Je základní typ nízké úrovně, který lze použít k sestavení vlastních analyzátorů a deserializace. Čtení prostřednictvím datové části JSON pomocí nového `Utf8JsonReader` je 2x rychlejší než použití čtecího zařízení z **JSON.NET**. Nepřiřazuje se, dokud nebudete muset actualize tokeny JSON jako řetězce (UTF-16).

Tady je příklad, jak číst pomocí souboru [**Launch. JSON**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) vytvořeného pomocí Visual Studio Code:

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJson)]

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJsonCall)]

### <a name="utf8jsonwriter"></a>Utf8JsonWriter

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType>poskytuje vysoce výkonný a neuložený v mezipaměti, a to jenom pro psaní textu JSON v kódování UTF-8 ze běžných typů .NET, `String`jako `Int32`jsou, `DateTime`a. Podobně jako čtenář je modul pro zápis základní typ nízké úrovně, který lze použít k vytvoření vlastních serializátorů. Zápis datové části JSON pomocí nového `Utf8JsonWriter` je 30-80% rychlejší než použití zapisovače z **JSON.NET** a nepřiřazuje.

### <a name="jsondocument"></a>JsonDocument

<xref:System.Text.Json.JsonDocument?displayProperty=nameWithType>je postaven na začátku `Utf8JsonReader`. `JsonDocument` Poskytuje možnost analyzovat data JSON a sestavit model DOM (Document Object Model) (DOM) jen pro čtení, které se dají dotazovat na podporu náhodného přístupu a výčtu. Prvky JSON, které tvoří data, mohou být přístupné prostřednictvím <xref:System.Text.Json.JsonElement> typu, který je zveřejněn `JsonDocument` jako vlastnost s názvem `RootElement`. `JsonElement` Obsahuje enumerátory pole a objektu JSON spolu s rozhraními API pro převod textu JSON na běžné typy .NET. Analýza typické datové části JSON a přístup ke všem jeho členům pomocí `JsonDocument` je 2 – 3x rychlejší než **JSON.NET** s malým přidělením dat, která mají rozumně velikost (to znamená < 1 MB).

Zde je ukázkové použití `JsonDocument` a `JsonElement` , které lze použít jako výchozí bod:

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJson)]

Tady je příklad C# 8,0 souboru [Launch. JSON](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) vytvořeného pomocí Visual Studio Code:

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJsonCall)]

### <a name="jsonserializer"></a>JsonSerializer

<xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType>je postaven na začátku <xref:System.Text.Json.Utf8JsonReader> a <xref:System.Text.Json.Utf8JsonWriter> k poskytnutí rychlé možnosti serializace paměti při práci s dokumenty a fragmenty JSON.

Tady je příklad serializace objektu do formátu JSON:

[!CODE-csharp[JsonSerializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonSerialize)]

Zde je příklad deserializace řetězce JSON na objekt. Můžete použít řetězec JSON vyprodukovaný předchozím příkladem:

[!CODE-csharp[JsonDeserializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonDeserialize)]

## <a name="interop-improvements"></a>Vylepšení spolupráce

.NET Core 3,0 vylepšuje nativní interoperabilitu rozhraní API.

### <a name="type-nativelibrary"></a>Zadejte: NativeLibrary

<xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType>poskytuje zapouzdření pro načtení nativní knihovny (pomocí stejné logiky zatížení jako .NET Core P/Invoke) a poskytnutí relevantních pomocných funkcí, jako je `getSymbol`. Příklad kódu naleznete v [ukázce DLLMap](https://github.com/dotnet/samples/tree/master/core/extensions/DllMapDemo).

### <a name="windows-native-interop"></a>Nativní spolupráce Windows

Systém Windows nabízí bohatě nativní rozhraní API ve formě plochých rozhraní API jazyka C, COM a WinRT. I když .NET Core podporuje **volání nespravovaného voláním**.net Core 3,0, přidává možnost **vytvořit rozhraní API modelu COM** a **aktivovat rozhraní API WinRT**. Příklad kódu naleznete v [ukázce v aplikaci Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).

## <a name="http2-support"></a>Podpora HTTP/2

<xref:System.Net.Http.HttpClient?displayProperty=nameWithType> Typ podporuje protokol HTTP/2. Pokud je povolený protokol HTTP/2, vyjednává se verze protokolu HTTP prostřednictvím TLS/ALPN a protokol HTTP/2 se použije, pokud se server rozhodne ho použít.

Výchozí protokol zůstává HTTP/1.1, ale protokol HTTP/2 může být povolen dvěma různými způsoby. Nejdřív můžete nastavit zprávu požadavku HTTP na používání HTTP/2:

[!CODE-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

Za druhé, ve výchozím <xref:System.Net.Http.HttpClient> nastavení se dá změnit na použití HTTP/2:

[!CODE-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

V mnoha případech, kdy vyvíjíte aplikaci, chcete použít nešifrované připojení. Pokud víte, že cílový koncový bod bude používat protokol HTTP/2, můžete zapnout nezašifrovaná připojení pro HTTP/2. Můžete ji zapnout nastavením `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` proměnné prostředí na `1` nebo povolením v kontextu aplikace:

[!CODE-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="tls-13--openssl-111-on-linux"></a>TLS 1,3 & OpenSSL 1.1.1 v systému Linux

.NET Core teď využívá [podporu TLS 1,3 v OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), pokud je dostupná v daném prostředí. S protokolem TLS 1,3:

- Časy připojení se zlepšily s omezenou špičkou odezvy mezi klientem a serverem.
- Vylepšené zabezpečení kvůli odebrání různých zastaralých a nezabezpečených kryptografických algoritmů.

V případě, že je k dispozici, .NET Core 3,0 používá **OpenSSL 1.1.1**, **OpenSSL 1.1.0**nebo **OpenSSL 1.0.2** v systému Linux. Pokud je k dispozici služba **OpenSSL 1.1.1** <xref:System.Net.Security.SslStream?displayProperty=nameWithType> , budou v obou <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> typech použity **protokoly TLS 1,3** (za předpokladu, že klient i server podporují protokol **TLS 1,3**).

>[!IMPORTANT]
>Windows a macOS ještě nepodporují **TLS 1,3**. Až bude podpora k dispozici, bude .NET Core 3,0 podporovat **TLS 1,3** v těchto operačních systémech.

Následující C# příklad 8,0 ukazuje rozhraní .net Core 3,0 v Ubuntu 18,10, které <https://www.cloudflare.com>se připojuje k:

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

## <a name="cryptography-ciphers"></a>Kryptografická šifry

.NET 3,0 přidává podporu pro šifry **AES-GCM** a **AES-ccm** , implementovaná <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> v <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> a v uvedeném pořadí. Tyto algoritmy jsou jak [ověřené šifrování, tak i algoritmy AEAD (Association data)](https://en.wikipedia.org/wiki/Authenticated_encryption).

Následující kód demonstruje `AesGcm` použití šifry k šifrování a dešifrování náhodných dat.

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

## <a name="cryptographic-key-importexport"></a>Import/export kryptografického klíče

.NET Core 3,0 podporuje import a export asymetrických veřejných a privátních klíčů ze standardních formátů. Nemusíte používat certifikát X. 509.

Všechny typy klíčů, jako jsou *RSA*, *DSA*, *ECDSA*a *ECDiffieHellman*, podporují následující formáty:

- **Veřejný klíč**
  - X.509 SubjectPublicKeyInfo

- **Privátní klíč**
  - PKCS#8 PrivateKeyInfo
  - PKCS#8 EncryptedPrivateKeyInfo

Klíče RSA podporují i:

- **Veřejný klíč**
  - RSAPublicKey PKCS # 1

- **Privátní klíč**
  - RSAPrivateKey PKCS # 1

Metody exportu vytváří binární data kódovaná v kódování DER a metody importu očekávají stejné. Pokud je klíč uložený v textovém formátu PEM, volající bude muset před voláním metody import kódování Base64 a dekódovat obsah.

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

Soubory **PKCS # 8** lze kontrolovat pomocí <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> souborů a soubory **PFX a PKCS # 12** lze zkontrolovat pomocí. <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType> Soubory **PFX/PKCS # 12** se můžou manipulovat s <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.

## <a name="serialport-for-linux"></a>Portu SerialPort pro Linux

.NET Core 3,0 poskytuje základní podporu pro <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> systém Linux.

Dřív se .NET Core podporuje jenom pomocí `SerialPort` systému Windows.

Další informace o omezené podpoře sériového portu v systému Linux najdete v tématu [#33146 problému GitHubu](https://github.com/dotnet/corefx/issues/33146).

## <a name="docker-and-cgroup-memory-limits"></a>Omezení paměti Docker a CGROUP

Počínaje verzí Preview 3 je používání .NET Core 3,0 na platformě Linux s nástrojem Docker lépe kompatibilní s cgroupmi omezeními paměti. Spuštění kontejneru Docker s omezeními paměti, jako je například `docker run -m`s, se změní způsob, jakým se aplikace .NET Core chová.

- Výchozí velikost haldy systému uvolňování paměti (GC): maximálně 20 MB nebo 75% limitu paměti v kontejneru.
- Explicitní velikost lze nastavit jako absolutní číslo nebo procento limitu CGROUP.
- Minimální velikost rezervovaného segmentu na haldě GC je 16 MB. Tato velikost snižuje počet hald, které jsou vytvořeny na počítačích.

## <a name="smaller-garbage-collection-heap-sizes"></a>Menší velikosti haldy uvolňování paměti

Výchozí velikost haldy systému uvolňování paměti byla snížena z výsledku rozhraní .NET Core s menším množstvím paměti. Tato změna se lépe zarovnává s rozpočtem přidělení 0. generace s moderními velikostmi mezipaměti procesoru.

## <a name="garbage-collection-large-page-support"></a>Podpora velkokapacitních stránek uvolňování paměti

Velké stránky (označované také jako velké stránky na platformě Linux) jsou funkce, ve které může operační systém vytvořit oblasti paměti větší než velikost nativní stránky (často 4K), aby se zlepšil výkon aplikace požadující tyto velké stránky.

Systém uvolňování paměti se teď dá nakonfigurovat s nastavením **GCLargePages** jako funkce výslovného souhlasu, která se rozhodne přidělit velké stránky ve Windows.

## <a name="gpio-support-for-raspberry-pi"></a>Podpora GPIO pro maliny PI

Do NuGet byly vydány dva balíčky, které můžete použít pro GPIO programování:

- [System. Device. GPIO](https://www.nuget.org/packages/System.Device.Gpio)
- [IoT. Device. Bindings](https://www.nuget.org/packages/Iot.Device.Bindings)

Balíčky GPIO obsahují rozhraní API pro zařízení *GPIO*, *SPI*, *I2C*a *PWM* . Balíček vazeb IoT zahrnuje vazby zařízení. Další informace najdete v [úložišti GitHubu zařízení](https://github.com/dotnet/iot/blob/master/src/devices/).

## <a name="arm64-linux-support"></a>Podpora ARM64 Linux

.NET Core 3,0 přidává podporu pro ARM64 pro Linux. Primární případ použití pro ARM64 je aktuálně ve scénářích IoT. Další informace najdete v tématu [stav .NET Core ARM64](https://github.com/dotnet/announcements/issues/82).

[Image Docker pro .NET Core na ARM64](https://hub.docker.com/r/microsoft/dotnet/) jsou k dispozici pro Alpine, Debian a Ubuntu.

> [!NOTE]
> **ARM64** Podpora Windows není ještě dostupná.
