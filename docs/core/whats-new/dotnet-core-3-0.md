---
title: Co je nového v .NET Core 3.0
description: Informace o nových funkcích v rozhraní .NET Core 3.0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 05/06/2019
ms.openlocfilehash: 369c74d2d8e82f157de0eec4294a5ee50542292b
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169789"
---
# <a name="whats-new-in-net-core-30-preview-5"></a>Co je nového v .NET Core 3.0 (ve verzi Preview 5)

Tento článek popisuje, co je nového v .NET Core 3.0 (prostřednictvím ve verzi preview 5). Jedním z největších vylepšení je podpora aplikací klasické pracovní plochy Windows (jenom Windows). Pomocí sady SDK .NET Core 3.0 součásti Windows Desktop můžete port aplikace Windows Forms a Windows Presentation Foundation (WPF). Jasno, komponenta Windows Desktop pouze podporované a součástí Windows. Další informace najdete v tématu [Windows desktop](#windows-desktop) části dále v tomto článku.

Přidává podporu pro .NET core 3.0 C# 8.0. Důrazně doporučujeme používat nejnovější verze sady Visual Studio. 2019 Update 1 Preview nebo VSCode s příponou OmniSharp.

[Stáhnout a začít pracovat s .NET Core 3.0 ve verzi Preview 6](https://aka.ms/netcore3download) teď na Windows, Mac a Linux.

Další informace o jednotlivých verzí preview najdete v následující oznámení:

- [.NET core 3.0 ve verzi Preview 6 oznámení](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-6/)
- [.NET core 3.0 ve verzi Preview 5 oznámení](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-5/)
- [.NET core 3.0 ve verzi Preview 4 oznámení](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-4/)
- [.NET core 3.0 ve verzi Preview 3 oznámení](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-3/)
- [.NET core 3.0 ve verzi Preview 2 oznámení](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)
- [.NET core 3.0 ve verzi Preview 1 oznámení](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)

## <a name="net-core-sdk-windows-installer"></a>Instalační program Windows .NET core SDK

Instalační program MSI pro Windows se změnila od verze .NET Core 3.0. Instalační programy sady SDK se nyní upgradovat verze funkce band SDK na místě. Funkce pruhy, které jsou definovány v *stovky* skupiny v *opravy* část čísla verze. Například **3.0. * 101*** a **3.0. * 201*** jsou verze ve dvou různých funkčních pruhy při **3.0. * 101*** a **3.0. * 199*** jsou stejnou funkci obsluhy vzdálené správy. A když .NET Core SDK **3.0. * 101*** je nainstalovaná sada .NET Core SDK **3.0. * 100*** bude odebrána z počítače, pokud existuje. Když .NET Core SDK **3.0. * 200*** je nainstalovaná na stejném počítači, .NET Core SDK **3.0. * 101*** se neodeberou.

Další informace o správě verzí naleznete v tématu [přehled jak .NET Core se systémovou správou verzí](../versions/index.md).

## <a name="c-80-preview"></a>C#8.0 ve verzi preview

.NET core 3.0 podporuje C# 8 ve verzi preview. Další informace o C# 8.0 funkce, najdete v článku [co je nového v C# 8.0](../../csharp/whats-new/csharp-8.md).

## <a name="net-standard-21"></a>.NET Standard 2.1

Přestože podporuje .NET Core 3.0 **.NET Standard 2.1**, výchozí `dotnet new classlib` Šablona generuje projekt, který se zaměřuje **.NET Standard 2.0**. K cíli **.NET Standard 2.1**, upravte soubor projektu a změňte `TargetFramework` vlastnost `netstandard2.1`:

```xml
<Project Sdk="Microsoft.NET.Sdk">
 
  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>
 
</Project>
```

Pokud používáte Visual Studio, je třeba Visual Studio 2019, jak Visual Studio 2017 nepodporuje **.NET Standard 2.1** nebo **.NET Core 3.0**. Důrazně doporučujeme použít [Visual Studio. 2019 Update 1 Preview](https://visualstudio.microsoft.com/vs/preview/).

## <a name="improved-net-core-version-apis"></a>Vylepšení .NET Core verze rozhraní API

Od verze rozhraní .NET Core 3.0, verze, kterou najdete rozhraní API pomocí .NET Core teď vrácené informace měli očekávat. Příklad:

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
> Rozbíjející změny. Toto je technicky rozbíjející změny, protože došlo ke změně schématu vytváření verzí.

## <a name="net-platform-dependent-intrinsics"></a>Vnitřní objekty závislého na platformě .NET

Rozhraní API nepřidali, která umožňují přístup k určité pokyny orientované výkonu procesoru, jako **SIMD** nebo **Bit zpracování instrukcí** nastaví. Tyto pokyny mohou pomoci dosáhnout výrazné zlepšení výkonu v některých scénářích, jako je zpracování dat, efektivně paralelně. 

Kde je to vhodné, knihovny .NET jste začali, podle těchto pokynů ke zlepšení výkonu.

Další informace najdete v tématu [závislé vnitřní funkce platformy .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).

## <a name="default-executables"></a>Výchozí spustitelné soubory

Sestavení .NET core teď [závisí na architektuře spustitelných souborů](../deploying/index.md#framework-dependent-executables-fde) ve výchozím nastavení. Toto chování je nová pro aplikace, které používají globálně nainstalovanou verzi .NET Core. Předtím jenom [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) vytvoří spustitelný soubor.

Během `dotnet build` nebo `dotnet publish`, je vytvořen spustitelný soubor, který odpovídá prostředí a platformě sady SDK, které používáte. Můžete očekávat, že stejné operace tyto spustitelné soubory stejně jako další nativní spustitelné soubory, jako například:

* Můžete dvakrát kliknout na spustitelný soubor.
* Aplikace z příkazového řádku můžete spustit přímo, jako například `myapp.exe` na Windows, a `./myapp` v Linuxu a macOS.

## <a name="single-file-executables"></a>Spustitelné soubory jedním souborem

`dotnet publish` Příkaz podporuje vytváření balíčků aplikací do spustitelného souboru specifické pro platformu jedním souborem. Spustitelný soubor je samorozbalovací a obsahuje všechny závislosti (včetně nativní), které jsou potřeba ke spouštění vaší aplikace. Při prvním spuštění aplikace, aplikace je extrahován do adresáře podle aplikaci název a identifikátor sestavení. Po spuštění je rychlejší při dalším spuštění aplikace. Aplikace nemusí extrahovat samotné podruhé, pokud byla použita nová verze.

Chcete-li publikovat do jednoho souboru spustitelný soubor, nastavte `PublishSingleFile` ve vašem projektu nebo na příkazovém řádku se `dotnet publish` příkaz:

```console
dotnet publish -r win10-x64 /p:PublishSingleFile=true
```

Další informace o publikování jednoho souboru, najdete v článku [dokumentu návrh například položky bundler jedním souborem](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).

## <a name="assembly-linking"></a>Propojování sestavení

.NET core 3.0 SDK obsahuje nástroj, který můžete zmenšit velikost aplikací tak, že analýza IL a ořezávání nevyužité sestavení.

Samostatná aplikace patří vše potřebné pro spuštění kódu, bez nutnosti .NET být nainstalovaný na hostitelském počítači. Ale v mnoha případech aplikace vyžaduje pouze malou podmnožinu rozhraní pro funkci a další nepoužité knihovny nebylo možné odebrat.

.NET core teď zahrnuje nastavení, které budou používat [IL linkeru](https://github.com/mono/linker) nástroj pro skenování IL vaší aplikace. Tento nástroj rozpozná, jaký kód je povinný a potom ořízne nepoužité knihovny. Tento nástroj může výrazně snížit velikost některé aplikace pro nasazení.

Chcete povolit Tenhle nástroj `<PublishTrimmed>` nastavení ve vašem projektu a publikování samostatnou aplikaci:

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```console
dotnet publish -r <rid> -c Release
```

Například volání základní "hello world" nové konzoly šablony projektu, který je součástí, při publikování, velikost přibližně 70 MB. S použitím `<PublishTrimmed>`, zmenšení velikosti na přibližně 30 MB.

Je důležité vzít v úvahu, že aplikace nebo rozhraní (včetně ASP.NET Core a WPF), které používají reflexi nebo související dynamické funkce se často přerušit, když oříznut. Tato rozbití dochází, protože nebude vědět o toto dynamické chování linkeru a nemůže určit typy rozhraní framework, které jsou požadovány pro účely reflexe. Je potřeba vědět tento scénář lze nakonfigurovat nástroj IL Linker.

Nad všemi jinak nezapomeňte otestovat vaši aplikaci po oříznutí.

Další informace o nástroji IL Linkeru, naleznete v tématu [dokumentaci](https://aka.ms/dotnet-illink) , případně přejděte [mono/linkeru]( https://github.com/mono/linker) úložiště.

## <a name="tiered-compilation"></a>Vrstvené kompilace

[Vrstvené kompilace](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) je ve výchozím s .NET Core 3.0. Tato funkce umožňuje modulu runtime více Adaptivně kompilátor za běhu (JIT) umožňuje dosahovat vyšších výkonů.

Hlavní výhodou TC je povolit zpětný jitting metody s pomalejší – ale – rychlejší pro vytvoření kódu nebo vyšší kvality – ale pomalejší vytvářet kód. To pomáhá zvýšit výkon aplikace, protože probíhá různé fáze zpracování, od spuštění do stabilního stavu. Tím se liší od přístup bez TC, kde je zkompilován každou metodu jeden způsob (stejné jako na úrovni vysoce kvalitní), který je tendenční do stabilního stavu přes výkon při spouštění.

Pokud chcete povolit rychlé JIT (vrstva 0 kódu), použijte následující nastavení v souboru projektu:

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>true</TieredCompilationQuickJit>
</PropertyGroup>
```

Chcete-li zcela zakázat TC, použijte následující nastavení v souboru projektu:

```xml
<TieredCompilation>false</TieredCompilation>
```

## <a name="readytorun-images"></a>ReadyToRun imagí

Spuštění aplikace .NET Core můžete zlepšit kompilaci vaším sestavením aplikace jako formát ReadyToRun (R2R). R2R je forma kompilace ahead of time (AOT).

Binární soubory R2R zlepšit výkon při spuštění snížením množství práce, kompilátor just-in-time (JIT) se musí provést jako zatížení vašich aplikací. Binární soubory obsahují podobné nativního kódu ve srovnání s co by vytvořila kompilátor JIT.

R2R binární soubory jsou větší, protože obsahují i kód (IL intermediate language), který je stále potřeba pro některé scénáře a nativní verzi stejný kód. R2R je k dispozici pouze při publikování, který cílí modulu runtime specifické prostředí (RID), jako je Linux x64 nebo Windows x64 samostatnou aplikaci.

Chcete-li kompilovat aplikaci jako R2R, přidejte `<PublishReadyToRun>` nastavení:

```xml
<PropertyGroup>
  <PublishReadyToRun>true</PublishReadyToRun>
</PropertyGroup>
```

Publikování samostatnou aplikaci. Třeba tento příkaz vytvoří samostatnou aplikaci pro 64bitové verzi systému Windows:

```console
dotnet publish -c Release -r win-x64 --self-contained true
```

### <a name="cross-platformarchitecture-restrictions"></a>Pro různé platformy/architektura omezení

Kompilátor ReadyToRun v současné době nepodporuje cílí na různé. Je nutné kompilovat na daném cíli. Například pokud chcete R2R imagí Windows x64, musíte ke spuštění příkazu Publikovat v tomto prostředí.

Která cílí na různé výjimky:

- Windows x64 lze použít ke kompilaci Windows ARM32, ARM64 a x86 bitové kopie.
- Windows x86 lze použít ke kompilaci Windows ARM32 Image.
- Linux x64 lze použít ke kompilaci imagí Linuxu ARM32 a ARM64.

## <a name="build-copies-dependencies"></a>Vytvoření kopie závislosti

`dotnet build` Příkaz nyní zkopíruje závislostí NuGet pro vaši aplikaci z mezipaměti NuGet k výstupní složce sestavení. Dříve byly závislosti pouze zkopírovány jako součást `dotnet publish`.

Existují některé operace, jako je stránka propojení a razor publikování, který se stále vyžadují publikování.

## <a name="local-tools"></a>Místní nástroje

.NET core 3.0 představuje místní nástroje. Místní nástroje se podobají [globální nástroje](../tools/global-tools.md) , ale jsou spojeny s konkrétní umístění na disku. Místní nástroje nejsou k dispozici globálně a distribuují jako balíčky NuGet.

> [!WARNING]
> Pokud jste se pokusili místní nástroje .NET Core 3.0 ve verzi Preview 1, jako je například spuštění `dotnet tool restore` nebo `dotnet tool install`, odstraňte složku mezipaměti místní nástroje. V opačném případě nástrojů pro místní nebude fungovat v jakékoli novější verze. Tato složka nachází tady:
>
> V systému macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`
>
> Ve Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`

Místní nástroje spoléhají na název souboru manifestu `dotnet-tools.json` v aktuálním adresáři. Tento soubor manifestu definuje nástroje k dispozici v této složce a níže. Soubor manifestu můžete distribuovat s vaším kódem zajistit, že každý, kdo pracuje s vaším kódem můžete obnovit a použít stejné nástroje.

Pro globální a místní nástroje se vyžaduje kompatibilní verze modulu runtime. Mnoho nástrojů aktuálně na NuGet.org cílit na .NET Core Runtime 2.1. K instalaci těchto nástrojů globálně nebo místně, je stále třeba k instalaci [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).

## <a name="major-version-roll-forward"></a>Hlavní verze Posunutí vpřed

.NET core 3.0 zavádí přihlašovaná funkce, které vaše aplikace bude posunout vpřed na nejnovější hlavní verzi .NET Core. Kromě toho byla přidána nové nastavení pro řízení použití posunutí vpřed do vaší aplikace. To lze nastavit následujícími způsoby:

- Vlastnost souboru projektu: `RollForward`
- Vlastnost souboru konfigurace modulu runtime: `rollForward`
- Proměnné prostředí: `DOTNET_ROLL_FORWARD`
- Argument příkazového řádku: `--roll-forward`

Musíte zadat jeden z následujících hodnot. Pokud toto nastavení je tento parametr vynechán, **menší** je výchozí nastavení.

- **LatestPatch**\
Posunout vpřed na nejvyšší verzi opravy. Zakáže podverze Posunutí vpřed.
- **Podverze**\
Program posunout vpřed na nejnižší vyšší dílčí verze, pokud chybí požadovaný podverze. Pokud požadovaný dílčí verze je k dispozici, pak bude **LatestPatch** zásady použít.
- **Hlavní**\
Program posunout vpřed na nejnižší vyšší hlavní verze a nejnižší podverze, pokud chybí požadovaný hlavní verze. Pokud je k dispozici, vyžádaná hlavní verze pak bude **menší** použití zásad.
- **LatestMinor**\
Program posunout vpřed na nejvyšší podverze, i v případě, že požadovaný dílčí verze je k dispozici. Určeno pro scénáře hostování součásti.
- **LatestMajor**\
Vrátit vpřed na nejvyšší hlavní a nejvyšší podverze, i v případě, že požadovaný hlavní je k dispozici. Určeno pro scénáře hostování součásti.
- **Zakázat**\
Není posunout vpřed. Pouze vytvořit vazbu na zadanou verzi. Tato zásada se nedoporučuje pro obecné použití, protože zakáže schopnost posunout vpřed na nejnovějších oprav. Tato hodnota se doporučuje jenom pro účely testování.

Kromě **zakázat** nastavení, budou všechna nastavení používat nejvyšší verze k dispozici opravy.

## <a name="windows-desktop"></a>Plocha Windows

.NET core 3.0 podporuje desktopové aplikace Windows pomocí formulářů Windows a Windows Presentation Foundation (WPF). Tyto architektury podporují také pomocí moderních ovládací prvky a Fluent stylů v knihovně Windows uživatelského rozhraní XAML (WinUI) prostřednictvím [XAML ostrovy](/windows/uwp/xaml-platform/xaml-host-controls).

Komponenta Windows Desktop je součástí Windows .NET Core 3.0 SDK.

Můžete vytvořit novou aplikaci WPF nebo Windows Forms s následujícími `dotnet` příkazy:

```console
dotnet new wpf
dotnet new winforms
```

Visual Studio 2019 přidá **nový projekt** šablon pro .NET Core 3.0 Windows Forms a WPF.

Další informace o způsobu přenesení existující aplikaci .NET Framework najdete v tématu [projekty Port WPF](../porting/wpf.md) a [Port Windows Forms projekty](../porting/winforms.md).

## <a name="com-callable-components---windows-desktop"></a>Součásti COM-callable - Windows Desktop

Na Windows můžete teď vytvořit volatelná aplikacemi COM spravované součásti. Tato funkce je důležité pro použití .NET Core s modelu COM doplněk modely a také k poskytování parity pomocí rozhraní .NET Framework.

Na rozdíl od rozhraní .NET Framework ve kterém *mscoree.dll* byl použit jako COM server, .NET Core přidá Spouštěč nativní knihovnu dll *bin* adresáře při sestavování vaší komponenty modelu COM.

Příklad toho, jak vytvořit komponentu modelu COM a používat ji, najdete v článku [COM ukázka](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).

## <a name="msix-deployment---windows-desktop"></a>Nasazení MSIX – Windows Desktop

[MSIX](https://docs.microsoft.com/windows/msix/) je nový formát balíčku aplikace Windows. Slouží k nasazení rozhraní .NET Core 3.0 desktopové aplikace pro Windows 10.

[Projekt Windows Application Packaging](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), k dispozici v aplikaci Visual Studio 2019, vám umožní vytvořit MSIX balíčky s [samostatná](../deploying/index.md#self-contained-deployments-scd) aplikace .NET Core.

Soubor projektu .NET Core, musíte zadat podporované moduly Runtime v `<RuntimeIdentifiers>` vlastnost:

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="winforms-highdpi"></a>WinForms HighDPI

Aplikace modelu Windows Forms .NET core můžete nastavit režim vysokého nastavení DPI s <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>. `SetHighDpiMode` Metoda nastaví odpovídající režim vysokého nastavení DPI, pokud nastavení jinými způsoby `App.Manifest` nebo P/Invoke před `Application.Run`.

Možné `highDpiMode` hodnoty, jak je vyjádřen podle <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> výčtu jsou:

* `DpiUnaware`
* `SystemAware`
* `PerMonitor`
* `PerMonitorV2`
* `DpiUnawareGdiScaled`

Další informace o režimech vysokého nastavení DPI, naleznete v tématu [vysoké rozlišení DPI Desktop Application Development na Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).

### <a name="ranges-and-indices"></a>Rozsahy a indexy

Nové <xref:System.Index?displayProperty=nameWithType> typ lze použít k indexování. Můžete je vytvořit z `int` , které se počítá od začátku, nebo s předponou `^` – operátor (C#), které se počítá od konce:

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

K dispozici je také <xref:System.Range?displayProperty=nameWithType> typ, který se skládá ze dvou `Index` hodnoty, jeden pro spuštění a jeden pro ukončení a může být zapsaný s `x..y` výrazu v rozsahu (C#). Potom můžete index s využitím `Range`, které produkuje řez:

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

Další informace najdete v tématu [kurz rozsahy a indexy](../../csharp/tutorials/ranges-indexes.md).

### <a name="async-streams"></a>Asynchronní datové proudy

<xref:System.Collections.Generic.IAsyncEnumerable%601> Typ je nový asynchronní verze <xref:System.Collections.Generic.IEnumerable%601>. Jazyk umožňuje `await foreach` přes `IAsyncEnumerable<T>` využívat jejich prvky a použití `yield return` k nim pro produkci prvků.

Následující příklad ukazuje produkční scénáře i využití asynchronních streamů. `foreach` Příkaz je asynchronní a sama používá `yield return` vytvoří na asynchronní datový proud pro volající. Tento model (pomocí `yield return`) je doporučený model pro vytváření asynchronních streamů.

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

Kromě toho, že možnost `await foreach`, můžete také vytvořit asynchronní iterátory, například iterátoru, který vrátí `IAsyncEnumerable/IAsyncEnumerator` , můžete obě `await` a `yield` v. Pro objekty, které je potřeba se dá uvolnit, můžete použít `IAsyncDisposable`, které různé typy BCL implementovat jako `Stream` a `Timer`.

Další informace najdete v tématu [asynchronní datové proudy kurzu](../../csharp/tutorials/generate-consume-asynchronous-stream.md).

## <a name="ieee-floating-point-improvements"></a>Vylepšení plovoucí desetinné čárky IEEE

Číslo s plovoucí čárkou bodu rozhraní API se aktualizují v souladu s [IEEE 754-2008 revize](https://en.wikipedia.org/wiki/IEEE_754-2008_revision). Cílem těchto změn je vystavit všechny **požadované** operací a ujistěte se, že byly behaviorally kompatibilní s specifikace IEEE. Další informace o vylepšeních s plovoucí desetinnou čárkou, najdete v článku [vylepšení analýzy plovoucí desetinné čárky a formátování v .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blogový příspěvek.

Analýza a formátování opravy patří:

* Správně analyzovat a zaokrouhlit vstupů o libovolné délce.
* Správně analyzovat a formátování záporná nula.
* Správně analyzovat `Infinity` a `NaN` to dělat kontrolu velkých a malých písmen a volitelné předcházející `+` kde je to možné.

Nové <xref:System.Math?displayProperty=nameWithType> rozhraní API patří:

* <xref:System.Math.BitIncrement(System.Double)> a <xref:System.Math.BitDecrement(System.Double)>\
Odpovídá `nextUp` a `nextDown` IEEE operace. Vrátí nejmenší s plovoucí desetinnou čárkou čísla, která porovnává větší nebo menší než vstup (v uvedeném pořadí). Například `Math.BitIncrement(0.0)` vracel `double.Epsilon`.

* <xref:System.Math.MaxMagnitude(System.Double,System.Double)> a <xref:System.Math.MinMagnitude(System.Double,System.Double)>\
Odpovídá `maxNumMag` a `minNumMag` IEEE operace, vrátí hodnotu, která je větší nebo menší řádově dva vstupy (v uvedeném pořadí). Například `Math.MaxMagnitude(2.0, -3.0)` vracel `-3.0`.

* <xref:System.Math.ILogB(System.Double)>\
Odpovídá `logB` IEEE operace, která vrací celé číslo, vrátí integrální protokolu základu 2 vstupního parametru. Tato metoda je v podstatě totéž jako `floor(log2(x))`, ale ukončili minimální zaokrouhlovací chyby.

* <xref:System.Math.ScaleB(System.Double,System.Int32)>\
Odpovídá `scaleB` IEEE operace, která přebírá celé číslo, vrátí efektivně `x * pow(2, n)`, ale se provádí s minimálními zaokrouhlovací chyby.

* <xref:System.Math.Log2(System.Double)>\
Odpovídá `log2` IEEE operace Vrátí logaritmus o základu 2. Minimalizuje zaokrouhlovací chyby.

* <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
Odpovídá `fma` IEEE operace provádí roztaveného vynásobit sčítanec. To znamená, že nemá `(x * y) + z` jako jediná operace, existuje-minimalizací zaokrouhlovací chyby. Příkladem může být `FusedMultiplyAdd(1e308, 2.0, -1e308)` která vrací `1e308`. Standardní `(1e308 * 2.0) - 1e308` vrátí `double.PositiveInfinity`.

* <xref:System.Math.CopySign(System.Double,System.Double)>\
Odpovídá `copySign` IEEE operace, vrátí hodnotu `x`, ale s znaménko `y`.

## <a name="fast-built-in-json-support"></a>Rychlé integrovanou podporou JSON

Uživatelé rozhraní .NET mají do značné míry spoléhat [ **Json.NET** ](https://www.newtonsoft.com/json) a dalších oblíbených knihoven JSON, které dál vhodná rozhodnutí. **Json.NET** používá .NET řetězce jako jeho základní datový typ, který je UTF-16 pod pokličkou.

Nové integrované podpoře JSON je vysoce výkonné, nízká přidělení a na základě `Span<byte>`. Tři nové hlavní JSON související typy byly přidány pro .NET Core 3.0 <xref:System.Text.Json?displayProperty=nameWithType> oboru názvů. Tyto typy není *ještě* podporu prostý staré CLR objektů (POCO) serializace a deserializace.

### <a name="utf8jsonreader"></a>Utf8JsonReader

<xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> je vysoce výkonné, s nízkou přidělení, dopředné čtecí modul pro kódování UTF-8 kódovaný JSON čtení z textu `ReadOnlySpan<byte>`. `Utf8JsonReader` Je nízké úrovně, základní typ, který je možné vytvářet vlastní analyzátory a deserializers. Přečtení datovou část JSON pomocí nového `Utf8JsonReader` je 2 × rychleji než při použití reader od **Json.NET**. Nelze přidělit, dokud je potřeba actualize tokeny JSON jako řetězce (UTF-16).

Tady je příklad čtení až [ **launch.json** ](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) soubor vytvořený Visual Studio Code:

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJson)]

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJsonCall)]

### <a name="utf8jsonwriter"></a>Utf8JsonWriter

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> poskytuje vysoce výkonné, bez mezipaměti, dopředné až po zápisu kódování UTF-8, jako je JSON textu z běžných typů .NET `String`, `Int32`, a `DateTime`. Podobně jako čtenář je modul pro zápis nízké úrovně, základní typ, který je možné vytvářet vlastní serializátory. Zápis datové části JSON pomocí nového `Utf8JsonWriter` je 30 80 % rychlejší než při použití modulu pro zápis z **Json.NET** a nebude přidělovat.

### <a name="jsondocument"></a>JsonDocument

<xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> je postavený na `Utf8JsonReader`. `JsonDocument` Poskytuje schopnost analyzovat JSON data a sestavení jen pro čtení Document Object Model (DOM), který může být dotazována k podporují náhodný přístup a výčet. Elementy JSON, které tvoří dat přístupné prostřednictvím <xref:System.Text.Json.JsonElement> typ, který je zveřejněný prostřednictvím `JsonDocument` jako vlastnost s názvem `RootElement`. `JsonElement` Obsahuje čítačů, společně s rozhraním API pro převod textu JSON na běžné typy .NET pole a objektu JSON. Parsování typické datová část JSON a přístup k všechny její členy pomocí `JsonDocument` je 2 až 3 x rychlejší než **Json.NET** s malou přidělení pro data, která je poměrně velké (to znamená, že < 1 MB).

Tady je ukázkový používání `JsonDocument` a `JsonElement` , který může sloužit jako výchozí bod:

Tady je C# 8.0 Příklad čtení až [ **launch.json** ](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) soubor vytvořený Visual Studio Code:

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJson)]

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJsonCall)]

### <a name="jsonserializer"></a>JsonSerializer

<xref:System.Text.Json.Serialization.JsonSerializer?displayProperty=nameWithType> je postavený na <xref:System.Text.Json.Utf8JsonReader> a <xref:System.Text.Json.Utf8JsonWriter> poskytnout možnost serializace rychlé nedostatku paměti při práci s dokumenty JSON a fragmenty.

VYHLEDEJTE: https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/docs/SerializerProgrammingModel.md příklad port, který se v tomto článku

Tady je příklad serializace objektu do formátu JSON:

[!CODE-csharp[JsonSerializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonSerialize)]

Tady je příklad deserializaci řetězce JSON na objekt. Řetězec JSON vytvořený v předchozím příkladu můžete použít:

[!CODE-csharp[JsonDeserializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonDeserialize)]

## <a name="interop-improvements"></a>Vylepšení spolupráce

.NET core 3.0 zlepšuje nativní rozhraní API zprostředkovatele komunikace s objekty.

### <a name="type-nativelibrary"></a>Zadejte: NativeLibrary

<xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> zapouzdření pro načítání nativní knihovny (pomocí stejné logiky zatížení jako P/Invoke .NET Core) a poskytuje relevantní pomocných funkcí, jako `getSymbol`. Příklad kódu, najdete v článku [DLLMap ukázka](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).

### <a name="windows-native-interop"></a>Windows nativní interoperabilita

Windows nabízí bohaté nativní rozhraní API v podobě bez stromové struktury rozhraní API jazyka C, COM a WinRT. Přestože podporuje .NET Core **P/Invoke**, .NET Core 3.0 přidává možnost **souběžné vytvoření součásti COM API** a **aktivovat rozhraní API WinRT**. Příklad kódu, najdete v článku [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).

## <a name="http2-support"></a>Podpora HTTP/2

<xref:System.Net.Http.HttpClient?displayProperty=nameWithType> Typů podporuje protokol HTTP/2. Pokud je povolená HTTP/2, verzi protokolu HTTP se vyjedná přes protokol TLS/ALPN a HTTP/2 se používá v případě, že rozhodne ho použít server.

Výchozím protokolem zůstane HTTP/1.1, ale HTTP/2 je možné povolit dvěma různými způsoby. Nejprve můžete nastavit zprávy s požadavkem HTTP používat HTTP/2:

[!CODE-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

Za druhé, můžete změnit <xref:System.Net.Http.HttpClient> používat HTTP/2 ve výchozím nastavení:

[!CODE-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

V mnoha případech Když vyvíjíte aplikaci, budete chtít použít nezašifrované připojení. Pokud víte, že cílový koncový bod se pomocí protokolu HTTP/2, můžete zapnout nezašifrované připojení HTTP/2. Můžete zapnout ho tak, že nastavíte `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` proměnnou prostředí, aby `1` nebo tím, že v rámci aplikace:

[!CODE-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="tls-13--openssl-111-on-linux"></a>TLS verze 1.3 & OpenSSL 1.1.1 v Linuxu

Teď využívá výhod platformy .NET core [podpora protokolu TLS 1.3 v OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), až bude k dispozici v daném prostředí. S TLS 1.3:

* Čas připojení jsou vylepšeny sníženou má zpáteční převod vyžaduje mezi klientem a serverem.
* Vyšší úroveň zabezpečení z důvodu odstranění různých zastaralé a nezabezpečené kryptografické algoritmy.

Pokud je k dispozici, .NET Core 3.0 používá **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, nebo **OpenSSL 1.0.2** v systému Linux. Při **OpenSSL 1.1.1** je k dispozici, i <xref:System.Net.Security.SslStream?displayProperty=nameWithType> a <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> používat typy **TLS 1.3** (za předpokladu, že klient i server podpory **TLS 1.3**).

>[!IMPORTANT]
>Windows a macOS zatím ještě nepodporují **TLS 1.3**. Bude podporovat .NET core 3.0 **TLS 1.3** v těchto operačních systémech, jakmile je k dispozici podpora.

Následující C# 8.0 příklad ukazuje, .NET Core 3.0 na Ubuntu 18.10 propojíte <https://www.cloudflare.com>:

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

## <a name="cryptography-ciphers"></a>Šifry šifrování

Přidává podporu pro .NET 3.0 **AES-GCM** a **AES-CCM** šifry, prováděné s <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> a <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> v uvedeném pořadí. Tyto algoritmy jsou obě [ověření šifrování pomocí algoritmů přidružení dat (AEAD)](https://en.wikipedia.org/wiki/Authenticated_encryption).

Následující kód ukazuje použití `AesGcm` šifer k šifrování a dešifrování náhodná data.

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

## <a name="cryptographic-key-importexport"></a>Kryptografické klíče Import/Export

.NET core 3.0 podporuje příkaz import a export asymetrické veřejného a privátního klíče ze standardní formáty. Není nutné použít certifikát X.509.

Všechny klíče typy, jako například *RSA*, *DSA*, *ECDsa*, a *ECDiffieHellman*, podporu následujících formátů:

* **Veřejný klíč**
  * X.509 SubjectPublicKeyInfo

* **privátní klíč**
  * PKCS#8 PrivateKeyInfo
  * PKCS#8 EncryptedPrivateKeyInfo

Klíčů RSA také podporu:

* **Veřejný klíč**
  * PKCS č. 1 RSAPublicKey

* **privátní klíč**
  * PKCS č. 1 RSAPrivateKey

Export metody vracet kódování DER binárních dat, a metod importu očekávají, že stejné. Pokud je klíč uložený ve formátu PEM popisný text, volajícího bude nutné base64 – dekódování obsahu před voláním metody importu.

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

**PKCS č. 8** soubory můžete prozkoumat pomocí <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> a **PFX/PKCS #12** soubory můžete prozkoumat pomocí <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>. **PFX/PKCS #12** soubory lze manipulovat s <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.

## <a name="serialport-for-linux"></a>SerialPort pro Linux

.NET core 3.0 podporuje <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> v Linuxu.

Dříve, .NET Core, které jsou podporovány pouze při použití `SerialPort` na Windows.

## <a name="docker-and-cgroup-memory-limits"></a>Omezuje dockeru a cgroup paměti

Od verze Preview 3, spuštěné .NET Core 3.0 v Linuxu pomocí Dockeru lépe funguje s cgroup paměťová omezení. Spuštění kontejneru Dockeru s omezení paměti, například s `docker run -m`, změní chování .NET Core.

* Výchozí velikost haldy systému uvolňování paměti (GC): maximálně 20 mb nebo 75 % omezení paměti v kontejneru.
* Explicitní velikost můžete nastavit jako absolutní číslo nebo procento cgroup limit.
* Velikost minimální vyhrazeného segmentu na haldě uvolňování paměti je 16 mb. Tato velikost snižuje počet haldy, které jsou vytvořeny na počítačích.

## <a name="smaller-garbage-collection-heap-sizes"></a>Menší velikost haldy uvolňování paměti

Velikost haldy systému uvolňování paměti výchozí zkrátila, což vede k .NET Core pomocí méně paměti. Tato změna lépe sladěné s rozpočtem generace 0 přidělení s velikostí mezipaměti moderní procesoru.

## <a name="garbage-collection-large-page-support"></a>Podpora velkých stránek kolekce uvolnění paměti

Velké stránky (označované také jako velké stránky v Linuxu) je funkce, kde je operační systém schopný vytvořit oblasti paměti větší než velikost nativní stránky (často 4 kB) ke zlepšení výkonu aplikací, které požadují tyto velkých stránek.

Uvolňování paměti se teď dá nakonfigurovat s **GCLargePages** nastavení jako funkce opt-in k výběru přidělit velkých stránek ve Windows.

## <a name="gpio-support-for-raspberry-pi"></a>Podpora GPIO Raspberry Pi

Byly vydány dva balíčky nuget, který můžete použít pro programování GPIO:

* [System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio)
* [Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings)

GPIO balíčky obsahují rozhraní API pro *GPIO*, *SPI*, *I2C*, a *PWM* zařízení. Sada IoT vazby zahrnuje zařízení vazby. Další informace najdete v tématu [zařízení úložiště GitHub se vzorovými](https://github.com/dotnet/iot/blob/master/src/devices/).

## <a name="arm64-linux-support"></a>Podpora Linuxu ARM64

.NET core 3.0 přidává podporu pro ARM64 pro Linux. Případem primárního použití pro ARM64 je aktuálně s scénáře IoT. Další informace najdete v tématu [.NET Core ARM64 stav](https://github.com/dotnet/announcements/issues/82).

[Image dockeru pro .NET Core na ARM64](https://hub.docker.com/r/microsoft/dotnet/) jsou k dispozici pro Alpine, Debian a Ubuntu.

> [!NOTE]
> **ARM64** podporu Windows ještě není k dispozici.
