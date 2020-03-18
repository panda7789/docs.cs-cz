---
title: Co je nového v .NET Core 3.0
description: Další informace o nových funkcích v rozhraní .NET Core 3.0.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 01/27/2020
ms.openlocfilehash: 6e85c2c3e796ae59a13f944bd4913e4b7316c56a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398809"
---
# <a name="whats-new-in-net-core-30"></a>Co je nového v .NET Core 3.0

Tento článek popisuje, co je novév rozhraní .NET Core 3.0. Jedním z největších vylepšení je podpora desktopových aplikací pro Windows (pouze windows). Pomocí součásti .NET Core 3.0 SDK windows desktop můžete přenést windows forms a windows presentation foundation (WPF) aplikace. Aby bylo jasno, součást Plochy systému Windows je podporována a zahrnuta pouze v systému Windows. Další informace naleznete v části [Plocha systému Windows](#windows-desktop) dále v tomto článku.

.NET Core 3.0 přidává podporu pro C# 8.0. Důrazně doporučujeme používat [Visual Studio 2019 verze 16.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější, [Visual Studio pro Mac 8.3](/visualstudio/mac/install-preview) nebo novější nebo [Visual Studio Code](https://code.visualstudio.com/) s **nejnovějším rozšířením C#**.

[Stáhněte si a s rozhraním .NET Core 3.0](https://aka.ms/netcore3download) si můžete začít hned teď v systémech Windows, macOS nebo Linux.

Další informace o vydání naleznete v [oznámení .NET Core 3.0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).

.NET Core RC1 byl považován za připravený na výrobu společností Microsoft a byl plně podporován. Pokud používáte verzi preview, musíte přejít na verzi RTM, abyste měli trvalou podporu.

## <a name="language-improvements-c-80"></a>Vylepšení jazyka C# 8.0

C# 8.0 je také součástí této verze, která zahrnuje funkce [reference s možností null,](../../csharp/tutorials/nullable-reference-types.md) [asynchronní datové proudy](../../csharp/tutorials/generate-consume-asynchronous-stream.md)a [další vzorky](../../csharp/tutorials/pattern-matching.md). Další informace o funkcích jazyka C# 8.0 naleznete [v tématu Co je nového v c# 8.0](../../csharp/whats-new/csharp-8.md).

Pro podporu následujících funkcí rozhraní API, které jsou podrobně popsány, byla přidána vylepšení jazyka:

- [Rozsahy a indexy](#ranges-and-indices)
- [Asynchronní datové proudy](#async-streams)

## <a name="net-standard-21"></a>.NET Standard 2.1

.NET Core 3.0 implementuje **standard .NET 2.1**. Výchozí `dotnet new classlib` šablona však generuje projekt, který stále cílí **na standard .NET Standard 2.0**. Chcete-li cílit na **rozhraní .NET Standard 2.1**, upravte soubor projektu a změňte `TargetFramework` vlastnost na `netstandard2.1`:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

</Project>
```

Pokud používáte Visual Studio, potřebujete [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), protože Visual Studio 2017 nepodporuje **rozhraní .NET Standard 2.1** nebo **.NET Core 3.0**.

## <a name="compiledeploy"></a>Kompilace/nasazení

### <a name="default-executables"></a>Výchozí spustitelné soubory

Rozhraní .NET Core nyní ve výchozím nastavení vytváří [spustitelné soubory závislé na modulu runtime.](../deploying/index.md#publish-runtime-dependent) Toto chování je nové pro aplikace, které používají globálně nainstalovanou verzi .NET Core. Dříve pouze [samostatné nasazení](../deploying/index.md#publish-self-contained) by vytvořit spustitelný soubor.

Během `dotnet build` `dotnet publish`nebo , je vytvořen spustitelný soubor (označovaný jako **appHost**), který odpovídá prostředí a platformě sady SDK, kterou používáte. U těchto spustitelných souborů můžete očekávat stejné věci jako jiné nativní spustitelné soubory, například:

- Můžete poklepat na spustitelný soubor.
- Aplikaci můžete spustit přímo z příkazového `myapp.exe` řádku, `./myapp` například ve Windows a v Linuxu a macOS.

### <a name="macos-apphost-and-notarization"></a>aplikace macOSHost a notářská izace

*pouze macOS*

Počínaje notářsky opravovanou sadou .NET Core SDK 3.0 pro macOS je nastavení vytvoření výchozího spustitelného souboru (známého jako appHost) ve výchozím nastavení zakázáno. Další informace najdete v [tématu macOS Catalina Notarization a dopad na stahování a projekty .NET Core](../install/macos-notarization-issues.md).

Když je povoleno nastavení appHost, .NET Core generuje nativní Mach-O spustitelný soubor při vytváření nebo publikování. Vaše aplikace běží v kontextu appHost při spuštění ze `dotnet run` zdrojového kódu pomocí příkazu nebo spuštěním spustitelného souboru Mach-O přímo.

Bez appHost, jediný způsob, jak uživatel může spustit aplikaci `dotnet <filename.dll>` [závislou na běhu](../deploying/index.md#publish-runtime-dependent) je pomocí příkazu. AppHost se vždy vytvoří, když publikujete aplikaci [samostatnou](../deploying/index.md#publish-self-contained).

Můžete buď nakonfigurovat appHost na úrovni projektu, nebo přepnout `dotnet` appHost `-p:UseAppHost` pro konkrétní příkaz s parametrem:

- Soubor projektu

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- Parametr příkazového řádku

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

Další informace o `UseAppHost` nastavení naleznete v [tématu Vlastnosti MSBuild pro sadu Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).

### <a name="single-file-executables"></a>Spustitelné soubory s jedním souborem

Příkaz `dotnet publish` podporuje balení aplikace do spustitelného souboru pro jeden soubor specifický pro platformu. Spustitelný soubor je samorozbalovací a obsahuje všechny závislosti (včetně nativní), které jsou nutné ke spuštění aplikace. Při prvním spuštění aplikace se aplikace extrahuje do adresáře na základě názvu aplikace a identifikátoru sestavení. Při opětovném spuštění aplikace je spuštění rychlejší. Aplikace nemusí extrahovat sám podruhé, pokud byla použita nová verze.

Chcete-li publikovat spustitelný soubor `PublishSingleFile` s jedním souborem, nastavte `dotnet publish` v projektu nebo na příkazovém řádku pomocí příkazu:

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

-nebo-

```dotnetcli
dotnet publish -r win10-x64 -p:PublishSingleFile=true
```

Další informace o publikování na jednom souboru naleznete v [návrhovém dokumentu sdružených souborů s jedním souborem](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).

### <a name="assembly-linking"></a>Propojení sestavy

Sada .NET core 3.0 SDK je dodávána s nástrojem, který může zmenšit velikost aplikací analýzou IL a oříznutím nepoužívaných sestavení.

Samostatné aplikace obsahují vše potřebné ke spuštění kódu, aniž by bylo nutné nainstalovat rozhraní .NET do hostitelského počítače. Mnohokrát však aplikace vyžaduje pouze malou podmnožinu rozhraní pro fungování a jiné nepoužívané knihovny mohou být odebrány.

.NET Core nyní obsahuje nastavení, které bude používat nástroj [propojovací program IL](https://github.com/mono/linker) ke skenování IL vaší aplikace. Tento nástroj zjistí, jaký kód je vyžadován, a potom ořízne nepoužívané knihovny. Tento nástroj může výrazně snížit velikost nasazení některých aplikací.

Chcete-li tento nástroj `<PublishTrimmed>` povolit, přidejte nastavení do projektu a publikujte samostatnou aplikaci:

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```dotnetcli
dotnet publish -r <rid> -c Release
```

Jako příklad, základní "hello world" nová konzola projekt šablony, která je zahrnuta, při publikování, hity asi 70 MB ve velikosti. Pomocí `<PublishTrimmed>`, tato velikost je snížena na asi 30 MB.

Je důležité si uvědomit, že aplikace nebo architektury (včetně ASP.NET Core a WPF), které používají reflexe nebo související dynamické funkce, se často přeruší při oříznutí. K tomuto přerušení dochází, protože propojovací aplikace neví o toto dynamické chování a nelze určit, které typy rozhraní jsou požadovány pro reflexi. Nástroj propojovací nástroj IL lze nakonfigurovat tak, aby byl vědom tohoto scénáře.

Především nezapomeňte aplikaci otestovat po oříznutí.

Další informace o nástroji IL Linker naleznete v [dokumentaci](https://aka.ms/dotnet-illink) nebo na adrese [úložiště mono/linker.]( https://github.com/mono/linker)

### <a name="tiered-compilation"></a>Vrstvená kompilace

[Vrstvená kompilace](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md) (TC) je ve výchozím nastavení zapnuta s rozhraním .NET Core 3.0. Tato funkce umožňuje modulu runtime více adaptivně používat kompilátor just-in-time (JIT) k dosažení lepšího výkonu.

Hlavní výhodou vrstvené kompilace je poskytnout dva způsoby jitting metody: v nižší kvalitě, ale rychlejší úroveň nebo vyšší kvalita, ale pomalejší úroveň. Kvalita se týká toho, jak dobře je metoda optimalizována. TC pomáhá zlepšit výkon aplikace při průchodu různými fázemi provádění, od spuštění až po ustálený stav. Když je vrstvená kompilace zakázána, každá metoda je zkompilována jedním způsobem, který je zaujatý k výkonu ustáleného stavu oproti výkonu při spuštění.

Pokud je povoleno TC, následující chování platí pro kompilaci metody při spuštění aplikace:

- Pokud má metoda kód zkompilovaný předem nebo [ReadyToRun](#readytorun-images), použije se předgenerovaný kód.
- V opačném případě je metoda jitted. Tyto metody jsou obvykle obecné typy nad typy hodnot.
  - *Quick JIT* vytváří kód nižší kvality (nebo méně optimalizovaný) rychleji. V rozhraní .NET Core 3.0 je rychlý JIT ve výchozím nastavení povolen pro metody, které neobsahují smyčky a jsou upřednostňovány při spuštění.
  - Plně optimalizační JIT vytváří vyšší kvalitu (nebo více optimalizovaný) kód pomaleji. Pro metody, kde by se quick JIT nepoužil (například pokud je metoda přiřazena ) <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType>se používá plně optimalizační JIT.

Pro často nazývané metody kompilátor just-in-time nakonec vytvoří plně optimalizovaný kód na pozadí. Optimalizovaný kód pak nahradí předkompilogovaný kód pro tuto metodu.

Kód generovaný quick JIT může běžet pomaleji, přidělit více paměti nebo použít více místa zásobníku. Pokud se jedná o problémy, můžete zakázat Rychlé JIT pomocí této vlastnosti MSBuild v souboru projektu:

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

Chcete-li tc zcela zakázat, použijte tuto vlastnost MSBuild v souboru projektu:

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

> [!TIP]
> Pokud změníte tato nastavení v souboru projektu, bude pravděpodobně nutné provést čisté sestavení `obj` pro `bin` nové nastavení, které se projeví (odstranit a adresáře a znovu sestavit).

Další informace o konfiguraci kompilace za běhu naleznete v [tématu Možnosti konfigurace za běhu pro kompilaci](../run-time-config/compilation.md).

### <a name="readytorun-images"></a>Obrázky ReadyToRun

Čas spuštění aplikace .NET Core můžete zlepšit kompilací sestavení aplikací ve formátu ReadyToRun (R2R). R2R je forma kompilace před časem (AOT).

Binární soubory R2R zlepšují výkon při spuštění tím, že snižují množství práce, kterou kompilátor za čas (JIT) potřebuje provést při načítání aplikace. Binární soubory obsahují podobný nativní kód ve srovnání s tím, co by JIT vyrábět. Binární soubory R2R jsou však větší, protože obsahují kód zprostředkující jazyk (IL), který je stále potřeba pro některé scénáře a nativní verze stejného kódu. R2R je k dispozici pouze při publikování samostatné aplikace, která se zaměřuje na konkrétní runtime prostředí (RID), jako je Linux x64 nebo Windows x64.

Chcete-li zkompilovat projekt jako ReadyToRun, postupujte takto:

01. Přidejte `<PublishReadyToRun>` nastavení do projektu:

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. Publikujte samostatnou aplikaci. Tento příkaz například vytvoří samostatnou aplikaci pro 64bitovou verzi Systému Windows:

    ```dotnetcli
    dotnet publish -c Release -r win-x64 --self-contained
    ```

#### <a name="cross-platformarchitecture-restrictions"></a>Omezení mezi platformami a architekturou

Kompilátor ReadyToRun aktuálně nepodporuje křížové cílení. Je nutné zkompilovat na daný cíl. Například pokud chcete R2R obrazy pro Windows x64, je třeba spustit příkaz publikovat v tomto prostředí.

Výjimky pro křížové cílení:

- Windows x64 lze použít ke kompilaci bitových kopií windows ARM32, ARM64 a x86.
- Windows x86 lze použít ke kompilaci bitových kopií Windows ARM32.
- Linux x64 lze použít ke kompilaci linuxových obrazů ARM32 a ARM64.

## <a name="runtimesdk"></a>Doba běhu/sada SDK

### <a name="major-version-runtime-roll-forward"></a>Hlavní verze runtime posun vpřed

.NET Core 3.0 zavádí funkci opt-in, která umožňuje vaší aplikaci posunout se dopředu na nejnovější hlavní verzi .NET Core. Kromě toho bylo přidáno nové nastavení, které řídí, jak se v aplikaci použije posun vpřed. To lze nakonfigurovat následujícími způsoby:

- Vlastnost souboru projektu:`RollForward`
- Vlastnost konfiguračního souboru za běhu:`rollForward`
- Proměnná prostředí:`DOTNET_ROLL_FORWARD`
- Argument příkazového řádku:`--roll-forward`

Musí být zadána jedna z následujících hodnot. Pokud je nastavení vynecháno, je výchozí **hodnota Minor.**

- **NejnovějšíOprava**\
Přetočte se vpřed na nejvyšší verzi opravy. Tím se zakáže dílčí verze posunout vpřed.
- **Menší**\
Převrátit na nejnižší vyšší dílčí verze, pokud je požadována dílčí verze chybí. Pokud je k dispozici požadovaná dílčí verze, použije se zásada **LatestPatch.**
- **Hlavní**\
Převrátit na nejnižší vyšší hlavní verze a nejnižší dílčí verze, pokud je požadována hlavní verze chybí. Pokud je k dispozici požadovaná hlavní verze, použije se zásada **Vedlejší.**
- **NejnovějšíMenší**\
Převést vpřed na nejvyšší dílčí verzi, i v případě, že je k dispozici požadovaná dílčí verze. Určeno pro scénáře hostování komponent.
- **NejnovějšíMajor**\
Převrátit na nejvyšší hlavní a nejvyšší dílčí verze, i když je požadováno hlavní je k dispozici. Určeno pro scénáře hostování komponent.
- **Zakázat**\
Neotáčej se dopředu. Spojte se pouze se zadanou verzí. Tato zásada se nedoporučuje pro obecné použití, protože zakáže možnost převést na nejnovější opravy. Tato hodnota je doporučena pouze pro testování.

Kromě nastavení **Zakázat** budou všechna nastavení používat nejvyšší dostupnou verzi opravy.

### <a name="build-copies-dependencies"></a>Sestavení závislostí kopií

Příkaz `dotnet build` nyní zkopíruje závislosti NuGet pro vaši aplikaci z mezipaměti NuGet do výstupní složky sestavení. Dříve byly závislosti zkopírovány `dotnet publish`pouze jako součást .

Existují některé operace, jako je propojení a publikování holicí strojek stránky, které budou stále vyžadovat publikování.

### <a name="local-tools"></a>Místní nástroje

.NET Core 3.0 zavádí místní nástroje. Místní nástroje jsou podobné [globálním nástrojům,](../tools/global-tools.md) ale jsou přidruženy k určitému umístění na disku. Místní nástroje nejsou k dispozici globálně a jsou distribuovány jako balíčky NuGet.

> [!WARNING]
> Pokud jste vyzkoušeli místní nástroje v rozhraní .NET `dotnet tool restore` Core `dotnet tool install`3.0 Preview 1, například spuštění nebo , odstraňte složku mezipaměti místních nástrojů. V opačném případě místní nástroje nebudou fungovat na žádné novější verzi. Tato složka je umístěna na adrese:
>
> Na macOS, Linux:`rm -r $HOME/.dotnet/toolResolverCache`
>
> Ve Windows:`rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`

Místní nástroje spoléhají na `dotnet-tools.json` název souboru manifestu v aktuálním adresáři. Tento soubor manifestu definuje nástroje, které mají být k dispozici v této složce a níže. Soubor manifestu můžete distribuovat s kódem, abyste zajistili, že každý, kdo pracuje s vaším kódem, může obnovit a používat stejné nástroje.

Pro globální i místní nástroje je vyžadována kompatibilní verze runtime. Mnoho nástrojů aktuálně na NuGet.org cíl .NET Core Runtime 2.1. Chcete-li nainstalovat tyto nástroje globálně nebo místně, budete stále muset nainstalovat [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).

### <a name="new-globaljson-options"></a>Nové možnosti global.json

Soubor *global.json* obsahuje nové možnosti, které poskytují větší flexibilitu při pokusu o definování, která verze sady .NET Core SDK se používá. Nové možnosti jsou:

- `allowPrerelease`: Označuje, zda by měl překladač sady SDK zvážit předběžné verze při výběru verze sady SDK, která se má použít.
- `rollForward`: Označuje zásady pro předávání vpřed, které se mají použít při výběru verze sady SDK, buď jako záložní, pokud chybí konkrétní verze sady SDK, nebo jako direktivu pro použití vyšší verze.

Další informace o změnách včetně výchozích hodnot, podporovaných hodnot a nových pravidel párování naleznete v [přehledu global.json](../tools/global-json.md).

### <a name="smaller-garbage-collection-heap-sizes"></a>Menší velikosti haldy uvolňování paměti

Výchozí velikost haldy systému uvolňování paměti byla snížena, což vedlo k tomu, že jádro .NET core používá méně paměti. Tato změna lépe zarovná s rozpočtem přidělení generace 0 s moderními velikostmi mezipaměti procesoru.

### <a name="garbage-collection-large-page-support"></a>Podpora velké stránky uvolňování paměti

Velké stránky (označované také jako Obrovské stránky v Linuxu) je funkce, kde je operační systém schopen vytvořit oblasti paměti větší než nativní velikost stránky (často 4K) pro zlepšení výkonu aplikace požadující tyto velké stránky.

Systém uvolňování paměti lze nyní nakonfigurovat s nastavením **GCLargePages** jako funkci přihlášení, kterou chcete přidělit velké stránky v systému Windows.

## <a name="windows-desktop--com"></a>& plochy systému Windows COM

### <a name="net-core-sdk-windows-installer"></a>Instalační služba sady Windows core s rozhraním .NET Core SDK

Instalační služba MSI pro systém Windows se změnila počínaje rozhraním .NET Core 3.0. Instalační programy sady SDK nyní inovují verze funkce sady SDK na místě. Pásma funkcí jsou definována ve *stovkách* skupin v části *opravy* čísla verze. Například **3.0._ 101_ ** a **3.0._ 201_ ** jsou verze ve dvou různých pásmech funkcí, zatímco **3.0._ 101_ ** a **3.0._ 199_ ** jsou ve stejném souboru funkcí. A když .NET Core SDK **3.0._ Je_ ** nainstalována sada 101, sada .NET Core SDK **3.0._ 100_ ** bude odebráno ze stroje, pokud existuje. Když .NET Core SDK **3.0._ 200_ ** je nainstalován ve stejném počítači, .NET Core SDK **3.0._ 101_ ** nebude odstraněn.

Další informace o správu verzí naleznete v [tématu Přehled verzí jádra .NET](../versions/index.md).

### <a name="windows-desktop"></a>Plocha Windows

Rozhraní .NET Core 3.0 podporuje desktopové aplikace systému Windows pomocí zařízení Windows Presentation Foundation (WPF) a Windows Forms. Tyto architektury také podporují použití moderních ovládacích prvků a plynulého stylu z knihovny Windows UI XAML Library (WinUI) přes [ostrovy XAML](/windows/uwp/xaml-platform/xaml-host-controls).

Součást Plochy systému Windows je součástí sady Windows .NET Core 3.0 SDK.

Můžete vytvořit novou aplikaci WPF nebo `dotnet` Windows Forms s následujícími příkazy:

```dotnetcli
dotnet new wpf
dotnet new winforms
```

Visual Studio 2019 přidává nové šablony **projectu** pro .NET Core 3.0 Windows Forms a WPF.

Další informace o tom, jak přenést existující aplikaci rozhraní .NET Framework, naleznete [v tématu Port WPF projekty](../../desktop-wpf/migration/convert-project-from-net-framework.md) a [port windows forms projekty](../porting/winforms.md).

#### <a name="winforms-high-dpi"></a>WinForms vysoké DPI

Aplikace .NET Core Windows Forms mohou <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>nastavit režim vysokého dpi s aplikací . Metoda `SetHighDpiMode` nastaví odpovídající režim vysokého DPI, pokud nastavení `App.Manifest` nebylo nastaveno `Application.Run`jinými prostředky, jako je P/Invoke před .

Možné `highDpiMode` hodnoty vyjádřené výčtem <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> jsou:

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

Další informace o režimech vysoké hodu DPI naleznete v tématu [Vývoj aplikací pro stolní počítače s vysokým obsahem DPI v systému Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).

### <a name="create-com-components"></a>Vytvoření komponent modelu COM

V systému Windows nyní můžete vytvářet spravované součásti com callable. Tato funkce je důležité použít .NET Core s com add-in modely a také poskytnout paritu s rozhraním .NET Framework.

Na rozdíl od rozhraní .NET Framework, kde byl jako server COM použit soubor *mscoree.dll,* přidá rozhraní .NET Core při vytváření komponenty modelu COM do adresáře *bin* nativní spouštěč.

Příklad, jak vytvořit komponentu modelu COM a její využití, naleznete v [tématu Com Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).

### <a name="windows-native-interop"></a>Nativní interop systému Windows

Systém Windows nabízí bohaté nativní rozhraní API ve formě plochých rozhraní API C, COM a WinRT. Zatímco rozhraní .NET Core podporuje **P/Invoke**, rozhraní .NET Core 3.0 přidává možnost **vytváření rozhraní API COM** a aktivace rozhraní API **WinRT**. Příklad kódu najdete v [tématu Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).

### <a name="msix-deployment"></a>Nasazení MSIX

[MSIX](https://docs.microsoft.com/windows/msix/) je nový formát balíčku aplikací systému Windows. Lze jej použít k nasazení desktopových aplikací .NET Core 3.0 do systému Windows 10.

[Projekt balení aplikací systému Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), který je k dispozici v sadě Visual Studio 2019, umožňuje vytvářet balíčky MSIX s [samostatnými](../deploying/index.md#publish-self-contained) aplikacemi .NET Core.

Soubor projektu .NET Core musí ve vlastnosti zadat podporované moduly `<RuntimeIdentifiers>` runtimes:

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="linux-improvements"></a>Vylepšení Linuxu

### <a name="serialport-for-linux"></a>SerialPort pro Linux

.NET Core 3.0 poskytuje <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> základní podporu pro linux.

Dříve rozhraní .NET Core `SerialPort` podporovalo pouze použití v systému Windows.

Další informace o omezené podpoře sériového portu v Linuxu naleznete v tématu [Problém GitHubu #33146](https://github.com/dotnet/corefx/issues/33146).

### <a name="docker-and-cgroup-memory-limits"></a>Omezení paměti Dockeru a skupiny

Spuštění rozhraní .NET Core 3.0 na Linuxu s Dockerem funguje lépe s limity paměti cgroup. Spuštění kontejneru Dockeru s omezeními paměti, například s `docker run -m`, změní způsob, jakým se chová .NET Core.

- Výchozí velikost haldy uvolňování paměti :maximum 20 MB nebo 75 % limitu paměti v kontejneru.
- Explicitní velikost lze nastavit jako absolutní číslo nebo procento limitu skupiny cgroup.
- Minimální velikost rezervovaného segmentu na haldu GC je 16 MB. Tato velikost snižuje počet hromady, které jsou vytvořeny na počítačích.

### <a name="gpio-support-for-raspberry-pi"></a>Podpora GPIO pro Raspberry Pi

Dva balíčky byly vydány na NuGet, které můžete použít pro programování GPIO:

- [System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio)
- [Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings)

Balíčky GPIO obsahují api pro zařízení *GPIO*, *SPI*, *I2C*a *PWM.* Balíček IoT vazby obsahuje vazby zařízení. Další informace najdete v [tématu zařízení GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).

### <a name="arm64-linux-support"></a>Podpora pro ARM64 Linux

.NET Core 3.0 přidává podporu pro ARM64 pro Linux. Primární případ použití pro ARM64 je aktuálně se scénáři IoT. Další informace naleznete [v tématu .NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).

[Obrázky Dockeru pro .NET Core na ARM64](https://hub.docker.com/r/microsoft/dotnet/) jsou k dispozici pro Alpine, Debian a Ubuntu.

> [!NOTE]
> **ARM64** Podpora systému Windows ještě není k dispozici.

## <a name="security"></a>Zabezpečení

### <a name="tls-13--openssl-111-on-linux"></a>TLS 1.3 & OpenSSL 1.1.1 na Linuxu

.NET Core nyní využívá [podporu TLS 1.3 v OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), když je k dispozici v daném prostředí. S TLS 1.3:

- Doba připojení je vylepšena snížením počtu zpátečních cest mezi klientem a serverem.
- Vylepšené zabezpečení z důvodu odebrání různých zastaralých a nezabezpečených kryptografických algoritmů.

Pokud je k dispozici, .NET Core 3.0 používá **OpenSSL 1.1.1**, **OpenSSL 1.1.0**nebo **OpenSSL 1.0.2** v systému Linux. Pokud je k dispozici **OpenSSL 1.1.1,** budou <xref:System.Net.Security.SslStream?displayProperty=nameWithType> oba i <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> typy používat **TLS 1.3** (za předpokladu, že klient i server podporují **TLS 1.3**).

> [!IMPORTANT]
> Windows a macOS zatím nepodporují **TLS 1.3**. .NET Core 3.0 bude podporovat **TLS 1.3** v těchto operačních systémech, jakmile bude podpora k dispozici.

Následující příklad C# 8.0 ukazuje .NET Core 3.0 na Ubuntu <https://www.cloudflare.com>18.10 připojení k :

[!code-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

### <a name="cryptography-ciphers"></a>Kryptografické šifry

.NET 3.0 přidává podporu pro šifry **AES-GCM** a <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> **AES-CCM,** implementované s a <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> příslušně. Tyto algoritmy jsou oba [ověřené šifrování s algoritmy AEAD (Association Data).](https://en.wikipedia.org/wiki/Authenticated_encryption)

Následující kód ukazuje `AesGcm` použití šifry k šifrování a dešifrování náhodných dat.

[!code-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

### <a name="cryptographic-key-importexport"></a>Import a export kryptografického klíče

.NET Core 3.0 podporuje import a export asymetrických veřejných a soukromých klíčů ze standardních formátů. Není nutné používat certifikát X.509.

Všechny typy klíčů, například *RSA*, *DSA*, *ECDsa*a *ECDiffieHellman*, podporují následující formáty:

- **Veřejný klíč**
  - X.509 PředmětPublicKeyInfo

- **Privátní klíč**
  - PKCS#8 PrivateKeyInfo
  - PKCS#8 EncryptedPrivateKeyInfo

RsA klíče také podporují:

- **Veřejný klíč**
  - PKCS# 1 RSAPublicKey

- **Privátní klíč**
  - PKCS#1 RSAPrivateKey

Metody exportu vytvářejí binární data kódovaná der a metody importu očekávají totéž. Pokud je klíč uložen ve formátu PEM vhodnépro text, volající bude muset base64 dekódovat obsah před voláním metody importu.

[!code-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

**PKCS # 8** soubory mohou <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> být kontrolovány s a **PFX / PKCS # 12** soubory mohou být kontrolovány s <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>. **PFX/PKCS#12** soubory lze manipulovat <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>s .

## <a name="net-core-30-api-changes"></a>Změny rozhraní API rozhraní .NET Core 3.0

### <a name="ranges-and-indices"></a>Rozsahy a indexy

Nový <xref:System.Index?displayProperty=nameWithType> typ lze použít pro indexování. Můžete vytvořit jeden `int` z, který se počítá od `^` začátku, nebo s prefix operátor (C#), který se počítá od konce:

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

K dispozici je <xref:System.Range?displayProperty=nameWithType> také typ, který `Index` se skládá ze dvou hodnot, jeden pro začátek `x..y` a jeden pro konec a může být zapsán s výrazem rozsahu (C#). Poté můžete indexovat `Range`pomocí , který vytvoří řez:

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

Další informace naleznete v [kurzu rozsahy a indexy](../../csharp/tutorials/ranges-indexes.md).

### <a name="async-streams"></a>Asynchronní streamy

Typ <xref:System.Collections.Generic.IAsyncEnumerable%601> je nová asynchronní verze <xref:System.Collections.Generic.IEnumerable%601>aplikace . Jazyk umožňuje `await foreach` přejít `IAsyncEnumerable<T>` ke konzumaci jejich `yield return` prvky a použít k nim k výrobě prvků.

Následující příklad ukazuje jak výrobu, tak spotřebu asynchronních datových proudů. Příkaz `foreach` je asynchronní `yield return` a sám používá k vytvoření asynchronního datového proudu pro volající. Tento vzor `yield return`(pomocí) je doporučený model pro výrobu asynchronních proudů.

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

Kromě toho, že `await foreach`je možné , můžete také vytvořit asynchronní iterátory, například iterátor, který `IAsyncEnumerable/IAsyncEnumerator` vrací, že můžete i `await` `yield` in. Pro objekty, které je třeba `IAsyncDisposable`vyřadit, můžete použít `Stream` , `Timer`které různé typy BCL implementovat, například a .

Další informace naleznete [v kurzu asynchronních datových proudů](../../csharp/tutorials/generate-consume-asynchronous-stream.md).

### <a name="ieee-floating-point"></a>IEEE Plovoucí bod

Plovoucí desetinná místa API jsou aktualizovány tak, aby v souladu s [IEEE 754-2008 revize](https://en.wikipedia.org/wiki/IEEE_754-2008_revision). Cílem těchto změn je vystavit všechny **požadované** operace a zajistit, že jsou behaviorálně kompatibilní se specifikací IEEE. Další informace o vylepšeních s plovoucí desetinnou desetinnou desetinnou desetinnou tázání najdete v tématu Vylepšení analýzy plovoucí desetinné a formátování v příspěvku blogu [.NET Core 3.0.](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)

Mezi opravy analýzy a formátování patří:

- Správně analyzovat a zaoblené vstupy libovolné délky.
- Správně analyzovat a formátovat záporné nuly.
- Správně analyzovat `Infinity` `NaN` a provedením kontroly rozlišování velkých `+` a malých písmen a povolení volitelné předcházející, pokud je to možné.

Mezi <xref:System.Math?displayProperty=nameWithType> nová api patří:

- <xref:System.Math.BitIncrement(System.Double)>A<xref:System.Math.BitDecrement(System.Double)>\
Odpovídá operacím `nextUp` `nextDown` i IEEE. Vrátí nejmenší číslo s plovoucí desetinnou desetinnou desetinnou, která porovnává větší nebo menší než vstup (v uvedeném pořadí). Například `Math.BitIncrement(0.0)` vrátí `double.Epsilon`.

- <xref:System.Math.MaxMagnitude(System.Double,System.Double)>A<xref:System.Math.MinMagnitude(System.Double,System.Double)>\
Odpovídá `maxNumMag` a `minNumMag` IEEE operace, vrátí hodnotu, která je větší nebo menší velikost dvou vstupů (v uvedeném pořadí). Například `Math.MaxMagnitude(2.0, -3.0)` vrátí `-3.0`.

- <xref:System.Math.ILogB(System.Double)>\
Odpovídá operaci `logB` IEEE, která vrací integrální hodnotu, vrátí integrální base-2 protokolu vstupního parametru. Tato metoda je skutečně `floor(log2(x))`stejná jako , ale provádí se s minimální chybou zaokrouhlení.

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
Odpovídá operaci `scaleB` IEEE, která přebírá integrální `x * pow(2, n)`hodnotu, vrátí efektivně , ale provádí se s minimální chybou zaokrouhlení.

- <xref:System.Math.Log2(System.Double)>\
Odpovídá operaci `log2` IEEE, vrátí logaritmus base-2. Minimalizuje chybu zaokrouhlení.

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
Odpovídá operaci `fma` IEEE, provede tavené násobení přidat. To znamená, `(x * y) + z` že provádí jako jednu operaci, čímž minimalizuje chybu zaokrouhlení. Příkladem je `FusedMultiplyAdd(1e308, 2.0, -1e308)`, `1e308`který vrátí . Pravidelné `(1e308 * 2.0) - 1e308` vrátí `double.PositiveInfinity`.

- <xref:System.Math.CopySign(System.Double,System.Double)>\
Odpovídá operaci `copySign` IEEE, vrátí hodnotu `x`, ale se `y`znaménkem .

### <a name="net-platform-dependent-intrinsics"></a>Vnitřní objekty závislé na platformě .NET

Byla přidána api, která umožňují přístup k určitým pokynům procesoru orientovaným na perf, jako jsou **například instrukční** sady **SIMD** nebo Bit Manipulation. Tyto pokyny mohou pomoci dosáhnout významné zlepšení výkonu v určitých scénářích, jako je například zpracování dat efektivně paralelně.

V případě potřeby začaly knihovny .NET používat tyto pokyny ke zlepšení výkonu.

Další informace naleznete v tématu [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).

### <a name="improved-net-core-version-apis"></a>Vylepšená rozhraní API základní verze rozhraní .NET

Počínaje rozhraním .NET Core 3.0 nyní rozhraní API verze s rozhraním .NET Core vrátí informace, které očekáváte. Například:

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
// New result (notice the value includes any preview release information)
//   RuntimeInformation.FrameworkDescription: .NET Core 3.0.0-preview4-27615-11
```

> [!WARNING]
> Prolomení změn. Toto je technicky narušující změna, protože schéma správy verzí se změnilo.

### <a name="fast-built-in-json-support"></a>Rychlá integrovaná podpora JSON

Uživatelé .NET se do značné míry spoléhali na [Newtonsoft.Json](https://www.newtonsoft.com/json) a další populární knihovny JSON, které jsou i nadále dobrou volbou. `Newtonsoft.Json`používá řetězce .NET jako svůj základní datový typ, který je UTF-16 pod kapotou.

Nová integrovaná podpora JSON je vysoce výkonná, s nízkou alokací a pracuje s textem JSON kódovánu UTF-8. Další informace o <xref:System.Text.Json> oboru názvů a typech naleznete v následujících článcích:

* [Serializace JSON v rozhraní .NET - přehled](../../standard/serialization/system-text-json-overview.md)
* [Serializace a deserializace zařízení JSON v rozhraní .NET](../../standard/serialization/system-text-json-how-to.md).
* [Jak migrovat z Newtonsoft.Json na System.Text.Json](../../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md)

### <a name="http2-support"></a>Podpora HTTP/2

Typ <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> podporuje protokol HTTP/2. Pokud je povolenprotokol HTTP/2, je verze protokolu HTTP vyjednána prostřednictvím protokolu TLS/ALPN a protokol HTTP/2 se používá, pokud se server rozhodne ji použít.

Výchozí protokol zůstává HTTP/1.1, ale HTTP/2 lze povolit dvěma různými způsoby. Nejprve můžete nastavit zprávu požadavku HTTP tak, aby používala protokol HTTP/2:

[!code-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

Za druhé, <xref:System.Net.Http.HttpClient> můžete změnit použít HTTP/2 ve výchozím nastavení:

[!code-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

Mnohokrát při vývoji aplikace, chcete použít nešifrované připojení. Pokud víte, že cílový koncový bod bude používat protokol HTTP/2, můžete zapnout nešifrovaná připojení pro protokol HTTP/2. Můžete ji zapnout nastavením `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` proměnné `1` prostředí na nebo povolením v kontextu aplikace:

[!code-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="next-steps"></a>Další kroky

- [Zkontrolujte narušující změny mezi .NET Core 2.2 a 3.0.](../compatibility/2.2-3.0.md)
- [Projděte si nejnovější změny v rozhraní .NET Core 3.0 pro aplikace pro Windows Forms.](../compatibility/winforms.md#net-core-30)
