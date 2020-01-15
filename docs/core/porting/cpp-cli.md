---
title: Migrace C++projektů/CLI do .NET Core
description: Seznamte se s C++přenosem projektů/CLI do .NET Core.
author: mjrousos
ms.date: 01/10/2020
ms.openlocfilehash: eb03f2a5ff42e8279fd3ebd6ee6fb6d955f6798d
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964928"
---
# <a name="how-to-port-a-ccli-project-to-net-core"></a>Postup při portování C++projektu/CLI na .NET Core

Od verze .NET Core 3,1 a sady Visual Studio 2019 verze 16,4 můžou [ C++projekty/CLI](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) cílit na .NET Core. Tato podpora umožňuje portování desktopových aplikací pro Windows s C++vrstvami interoperability/CLI do .NET Core. Tento článek popisuje, jak přenést C++projekty/cli z .NET Framework do .net Core 3,1.

## <a name="ccli-net-core-limitations"></a>C++Omezení rozhraní/CLI .NET Core

Existuje několik důležitých omezení pro přenos projektů C++/CLI do .NET Core ve srovnání s jinými jazyky:

* C++Podpora/CLI pro .NET Core je jenom Windows.
* C++Projekty/CLI nemohou cílit na .NET Standard, pouze .NET Core (nebo .NET Framework).
* C++Projekty/CLI nepodporují nový formát souboru projektu ve stylu sady SDK. Místo toho, i když cílíte na C++projekty .NET Core,/CLI používají existující formát souboru VCXPROJ.
* C++Projekty/CLI nemohou více cílit na více platforem .NET. Pokud potřebujete sestavit projekt C++/cli pro .NET Framework i .NET Core, použijte samostatné soubory projektu.
* .NET Core nepodporuje kompilaci `-clr:pure` ani `-clr:safe`, pouze novou možnost `-clr:netcore` (která je ekvivalentem `-clr` pro .NET Framework).

## <a name="port-a-ccli-project"></a>Port a C++projekt/CLI

Chcete-li C++přenést projekt/CLI do .NET Core, proveďte následující změny v souboru VCXPROJ. Tyto kroky migrace se liší od kroků potřebných pro jiné typy projektů, C++protože projekty/CLI nepoužívají soubory projektu ve stylu sady SDK.

1. Nahradit vlastnosti `<CLRSupport>true</CLRSupport>` `<CLRSupport>NetCore</CLRSupport>`. Tato vlastnost je často ve skupinách vlastností specifických pro konfiguraci, takže ji možná budete muset nahradit na více místech.
2. Nahradit vlastnosti `<TargetFrameworkVersion>` `<TargetFramework>netcoreapp3.1</TargetFramework>`.
3. Odeberte všechny odkazy na .NET Framework (například `<Reference Include="System" />`). K .NET Core SDK sestavení se automaticky odkazuje při použití `<CLRSupport>NetCore</CLRSupport>`.
4. Aktualizujte využití rozhraní API v souborech cpp v případě potřeby pro odebrání rozhraní API nedostupných pro .NET Core. Vzhledem C++k tomu, že projekty/CLI mají za následek poměrně tenkou spolupráci vrstev, často není potřeba provádět mnoho změn. [Analyzátor přenositelnosti .NET](../../standard/analyzers/portability-analyzer.md) se dá použít k identifikaci nepodporovaných rozhraní API .NET C++používaných binárními soubory/CLI stejně jako s čistě spravovanými binárními soubory. Pokyny pro určení přenositelnosti kódu a aktualizace projektů pro práci s rozhraními API .NET Core jsou k dispozici v [pokynech pro přenos knihoven](./libraries.md#determine-portability).

### <a name="wpf-and-windows-forms-usage"></a>WPF a model Windows Forms využití

Projekty .NET C++Core/CLI můžou používat model Windows Forms a rozhraní API WPF. Chcete-li použít tato rozhraní API pro stolní počítače s Windows, je nutné přidat explicitní odkazy na rozhraní do knihoven uživatelského rozhraní. Projekty ve stylu sady SDK, které používají rozhraní API pro stolní počítače Windows, odkazují na potřebné knihovny rozhraní automaticky pomocí sady `Microsoft.NET.Sdk.WindowsDesktop` SDK. Vzhledem C++k tomu, že projekty/CLI nepoužívají formát projektu ve stylu sady SDK, musí při cílení na .NET Core přidat explicitní odkazy na rozhraní.

Chcete-li použít rozhraní API model Windows Forms, přidejte tento odkaz do souboru VCXPROJ:

```xml
<!-- Reference all of Windows Forms -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WindowsForms" />
```

Chcete-li použít rozhraní API WPF, přidejte tento odkaz do souboru VCXPROJ:

```xml
<!-- Reference all of WPF -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WPF" />
```

Chcete-li použít model Windows Forms i rozhraní API WPF, přidejte tento odkaz do souboru VCXPROJ:

```xml
<!-- Reference the entirety of the Windows desktop framework:
     Windows Forms, WPF, and the types that provide integration between them -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App" />
```

V současné době není možné přidávat tyto odkazy pomocí Správce odkazů sady Visual Studio. Místo toho aktualizujte soubor projektu ručně. Tuto aktualizaci lze provést v aplikaci Visual Studio uvolněním projektu a následným úpravou souboru projektu. Můžete také použít jiný editor, například VS Code.

## <a name="build-without-msbuild"></a>Sestavit bez MSBuild

Je také možné vytvořit C++projekty/CLI bez použití nástroje MSBuild. Postupujte podle těchto kroků a sestavte projekt C++/CLI pro .NET Core přímo s *CL. exe* a *Link. exe*:

1. Při kompilaci předejte `-clr:netcore` souboru *CL. exe*.
2. Odkaz na potřebná referenční sestavení .NET Core.
3. Při propojování zadejte jako `LibPath` adresář hostitele aplikace .NET Core (aby bylo možné najít *ijwhost. lib* ).
4. Zkopírujte *ijwhost. dll* (z adresáře hostitele aplikace .NET Core) do výstupního adresáře projektu.
5. Ujistěte se, že soubor [runtimeconfig. JSON](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) existuje pro první komponentu aplikace, která spustí spravovaný kód. Pokud má aplikace spravovaný vstupní bod, vytvoří se soubor `runtime.config` a automaticky se zkopíruje. Pokud má aplikace nativní vstupní bod, ale je třeba vytvořit soubor `runtimeconfig.json` pro první C++knihovnu/CLI, aby používal modul runtime .NET Core.

## <a name="known-issues"></a>Známé problémy

Při práci s C++projekty/CLI, které cílí na .NET Core, se můžete podívat na několik známých problémů.

* Odkaz na rozhraní WPF v projektech .NET C++Core/CLI aktuálně způsobuje některá nadbytečná upozornění na Import symbolů. Tato upozornění se dají bezpečně ignorovat a je potřeba je opravit brzy.
* Pokud má aplikace nativní vstupní bod, knihovna C++/CLI, která první spustí spravovaný kód, potřebuje soubor [runtimeconfig. JSON](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) . Tento konfigurační soubor se používá při spuštění modulu runtime .NET Core. C++Projekty/CLI nevytváří `runtimeconfig.json` soubory automaticky v době sestavování, proto je třeba soubor vygenerovat ručně. Je- C++li knihovna/CLI volána ze spravovaného vstupního bodu, knihovna C++/cli nepotřebuje soubor `runtimeconfig.json` (vzhledem k tomu, že sestavení vstupního bodu bude mít k dispozici, která se používá při spuštění modulu runtime). Níže je zobrazený jednoduchý ukázkový `runtimeconfig.json` soubor. Další informace najdete v tématu [specifikace na GitHubu](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).

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
