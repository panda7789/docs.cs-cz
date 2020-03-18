---
title: Migrace projektů C++/CLI do jádra .NET
description: Další informace o přenesení projektů C++/CLI do jádra .NET.
author: mjrousos
ms.date: 01/10/2020
ms.openlocfilehash: eb03f2a5ff42e8279fd3ebd6ee6fb6d955f6798d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75964928"
---
# <a name="how-to-port-a-ccli-project-to-net-core"></a>Jak portovat projekt C++/CLI do jádra .NET Core

Počínaje .NET Core 3.1 a Visual Studio 2019 verze 16.4, [C++/CLI projekty](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) mohou cílit na .NET Core. Tato podpora umožňuje portovat desktopové aplikace systému Windows s vrstvami interop c++/CLI do .NET Core. Tento článek popisuje, jak portovat projekty C++/CLI z rozhraní .NET Framework do rozhraní .NET Core 3.1.

## <a name="ccli-net-core-limitations"></a>Omezení jádra jazyka C++/CLI .NET

Existují některá důležitá omezení pro přenesení projektů C++/CLI na .NET Core ve srovnání s jinými jazyky:

* Podpora rozhraní C++/CLI pro rozhraní .NET Core je pouze pro Windows.
* Projekty jazyka C++/CLI nemohou cílit na standard .NET, pouze na jádro .NET (nebo rozhraní .NET Framework).
* Projekty jazyka C++/CLI nepodporují nový formát souboru projektu ve stylu sady SDK. Místo toho i při cílení na .NET Core, C++/CLI projekty používají existující formát souboru vcxproj.
* Projekty c++/CLI nemohou vícecílit na více platforem .NET. Pokud potřebujete vytvořit projekt C++/CLI pro rozhraní .NET Framework i .NET Core, použijte samostatné soubory projektu.
* .NET Core nepodporuje `-clr:pure` `-clr:safe` ani kompilace, `-clr:netcore` pouze nová možnost `-clr` (což je ekvivalentní pro rozhraní .NET Framework).

## <a name="port-a-ccli-project"></a>Port projektu C++/CLI

Chcete-li portovat projekt C++/CLI do jádra .NET Core, proveďte následující změny v souboru vcxproj. Tyto kroky migrace se liší od kroků potřebných pro jiné typy projektů, protože projekty C++/CLI nepoužívají soubory projektu ve stylu sady SDK.

1. `<CLRSupport>true</CLRSupport>` Nahraďte `<CLRSupport>NetCore</CLRSupport>`vlastnosti . Tato vlastnost je často ve skupinách vlastností specifických pro konfiguraci, takže ji možná budete muset nahradit na více místech.
2. `<TargetFrameworkVersion>` Nahraďte `<TargetFramework>netcoreapp3.1</TargetFramework>`vlastnosti .
3. Odeberte všechny odkazy rozhraní `<Reference Include="System" />`.NET Framework (například ). Sestavení sady .NET Core SDK jsou `<CLRSupport>NetCore</CLRSupport>`při použití automaticky odkazována .
4. Podle potřeby aktualizujte využití rozhraní API v souborech CPP a odeberte rozhraní API, která nejsou k dispozici pro jádro .NET Core. Vzhledem k tomu, že projekty Jazyka C++/CLI mají tendenci být poměrně tenké vrstvy interop, často není potřeba mnoho změn. [Analyzátor přenosovatelnosti rozhraní .NET](../../standard/analyzers/portability-analyzer.md) lze použít k identifikaci nepodporovaných rozhraní API rozhraní .NET používaných binárními soubory jazyka C++/CLI stejně jako u čistě spravovaných binárních souborů. Pokyny pro určení přenositelnosti kódu a aktualizaci projektů pro práci s rozhraními API .NET Core jsou k dispozici v [pokynech pro přenos portů knihovny](./libraries.md#determine-portability).

### <a name="wpf-and-windows-forms-usage"></a>WPF a Windows Forms použití

Projekty rozhraní .NET Core C++/CLI mohou používat rozhraní API systému Windows a WPF. Chcete-li použít tato rozhraní API plochy systému Windows, je třeba přidat explicitní odkazy na rozhraní do knihoven uživatelského rozhraní. Projekty ve stylu sady SDK, které používají rozhraní API `Microsoft.NET.Sdk.WindowsDesktop` plochy systému Windows, automaticky odkazují na nezbytné knihovny architektury pomocí sady SDK. Vzhledem k tomu, že projekty jazyka C++/CLI nepoužívají formát projektu ve stylu sady SDK, je třeba při cílení na jádro .NET přidat explicitní odkazy na rozhraní Framework.

Chcete-li použít soubory API pro formuláře systému Windows, přidejte tento odkaz do souboru vcxproj:

```xml
<!-- Reference all of Windows Forms -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WindowsForms" />
```

Chcete-li použít wpf api, přidejte tento odkaz do souboru vcxproj:

```xml
<!-- Reference all of WPF -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WPF" />
```

Chcete-li použít windows forms i wpf api, přidejte tento odkaz do souboru vcxproj:

```xml
<!-- Reference the entirety of the Windows desktop framework:
     Windows Forms, WPF, and the types that provide integration between them -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App" />
```

V současné době není možné přidat tyto odkazy pomocí správce odkazů sady Visual Studio. Místo toho aktualizujte soubor projektu ručně. Tuto aktualizaci lze provést v sadě Visual Studio uvolněním projektu a úpravou souboru projektu. Můžete také použít jiný editor, jako je VS Code.

## <a name="build-without-msbuild"></a>Sestavení bez MSBuild

Je také možné vytvářet projekty C++/CLI bez použití MSBuild. Následujícím postupem vytvořte projekt C++/CLI pro jazyk .NET Core přímo pomocí *cl.exe* a *link.exe*:

1. Při kompilaci přejděte `-clr:netcore` na *cl.exe*.
2. Odkaz na nezbytné sestavení odkazů .NET Core.
3. Při propojování zadejte adresář hostitele `LibPath` aplikace .NET Core jako adresář (aby bylo možné nalézt *soubor ijwhost.lib).*
4. Zkopírujte *soubor ijwhost.dll* (z adresáře hostitele aplikace .NET Core) do výstupního adresáře projektu.
5. Ujistěte se, že pro první součást aplikace, která bude spuštěn spravovaný kód, existuje soubor [runtimeconfig.json.](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) Pokud má aplikace spravovaný `runtime.config` vstupní bod, soubor se vytvoří a zkopíruje automaticky. Pokud má aplikace nativní vstupní bod, musíte `runtimeconfig.json` vytvořit soubor pro první knihovnu C++/CLI, abyste použili runtime .NET Core.

## <a name="known-issues"></a>Známé problémy

Existuje několik známých problémů, na které je třeba dávat pozor při práci s projekty C++/CLI zaměřenými na .NET Core.

* WPF odkaz na architekturu v projektech .NET Core C++/CLI aktuálně způsobuje některé nadbytečné upozornění o tom, že nelze importovat symboly. Tato upozornění mohou být bezpečně ignorována a měla by být brzy opravena.
* Pokud má aplikace nativní vstupní bod, potřebuje knihovna C++/CLI, která nejprve spustí spravovaný kód, soubor [runtimeconfig.json.](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) Tento konfigurační soubor se používá při spuštění runtime jádra .NET. Projekty C++/CLI ještě `runtimeconfig.json` nevytvářejí soubory automaticky v době sestavení, takže soubor musí být generován ručně. Pokud je knihovna C++/CLI volána ze spravovaného vstupního bodu, pak knihovna C++/CLI nepotřebuje `runtimeconfig.json` soubor (protože sestavení vstupního bodu bude mít ten, který se používá při spuštění běhu). Jednoduchý ukázkový `runtimeconfig.json` soubor je uveden níže. Další informace naleznete v [spec na GitHubu](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).

    ```json
    {
          "runtimeOptions": {
             "tfm": "netcoreapp3.1",
             "framework": {
                "name": "Microsoft.NETCore.App",
                "version": "3.1.0"
             }
          }
    }
    ```
