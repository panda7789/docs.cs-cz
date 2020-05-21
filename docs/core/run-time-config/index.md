---
title: Možnosti konfigurace běhového běhu
description: Naučte se konfigurovat aplikace .NET Core pomocí nastavení konfigurace za běhu.
ms.date: 01/21/2020
ms.openlocfilehash: 68690689fd4f936e3af76ab647f0b58d8ec6ca27
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761951"
---
# <a name="net-core-run-time-configuration-settings"></a>Nastavení konfigurace runtime .NET Core

.NET Core podporuje použití konfiguračních souborů a proměnných prostředí ke konfiguraci chování aplikací .NET Core v době běhu. Konfigurace běhového běhu je atraktivní možnost, pokud:

- Zdrojový kód aplikace nevlastníte nebo neovládáte, a proto ji nelze programově nakonfigurovat.

- V jednom systému se spouští více instancí aplikace současně a chcete je nakonfigurovat pro optimální výkon.

> [!NOTE]
> Tato dokumentace je probíhající práce. Pokud si všimnete, že zde uvedené informace jsou buď neúplné, nebo nepřesné, buď [otevřete problém](https://github.com/dotnet/docs/issues) , abychom nás věděli, nebo [odešlete žádost](https://github.com/dotnet/docs/pulls) o přijetí změn k vyřešení problému. Informace o odesílání žádostí o přijetí změn pro úložiště dotnet/docs najdete v [příručce pro přispěvatele](https://docs.microsoft.com/contribute/dotnet/dotnet-contribute).

.NET Core poskytuje následující mechanismy pro konfiguraci chování aplikace v době běhu:

- [Soubor runtimeconfig. JSON](#runtimeconfigjson)

- [Vlastnosti nástroje MSBuild](#msbuild-properties)

- [Proměnné prostředí](#environment-variables)

> [!TIP]
> Konfigurace možnosti modulu runtime pomocí proměnné prostředí použije nastavení pro všechny aplikace .NET Core. Při konfiguraci možnosti modulu runtime v souboru *runtimeconfig. JSON* nebo projektu se použije nastavení jenom pro tuto aplikaci.

Některé hodnoty konfigurace lze také nastavit programově voláním <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metody.

Články v této části dokumentace jsou uspořádány podle kategorie, například [ladění](debugging-profiling.md) a [uvolňování paměti](garbage-collector.md). Pokud je to možné, zobrazí se možnosti konfigurace pro soubory *runtimeconfig. JSON* , vlastnosti MSBuild, proměnné prostředí a, pro křížové odkazy, soubory *App. config* pro .NET Framework projekty.

## <a name="runtimeconfigjson"></a>runtimeconfig. JSON

Při [sestavení](../tools/dotnet-build.md)projektu se ve výstupním adresáři vygeneruje soubor *[AppName]. runtimeconfig. JSON* . Pokud soubor *runtimeconfig. template. JSON* existuje ve stejné složce jako soubor projektu, všechny možnosti konfigurace, které obsahuje, jsou sloučeny do souboru *[název_aplikace]. runtimeconfig. JSON* . Pokud vytváříte aplikaci sami, vložte do souboru *runtimeconfig. template. JSON* všechny možnosti konfigurace. Pokud jste právě spustili aplikaci, vložte ji přímo do souboru *[název_aplikace]. runtimeconfig. JSON* .

> [!NOTE]
> Soubor *[AppName]. runtimeconfig. JSON* se přepíše v následných sestaveních.

Zadejte možnosti konfigurace modulu runtime v části **configProperties** souborů *runtimeconfig. JSON* . Tato část obsahuje formulář:

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a>Příklad souboru [AppName]. runtimeconfig. JSON

Pokud umístíte možnosti do výstupního souboru JSON, zanořit je do `runtimeOptions` Vlastnosti.

```json
{
  "runtimeOptions": {
    "tfm": "netcoreapp3.1",
    "framework": {
      "name": "Microsoft.NETCore.App",
      "version": "3.1.0"
    },
    "configProperties": {
      "System.GC.Concurrent": false,
      "System.Threading.ThreadPool.MinThreads": 4,
      "System.Threading.ThreadPool.MaxThreads": 25
    }
  }
}
```

### <a name="example-runtimeconfigtemplatejson-file"></a>Příklad souboru runtimeconfig. template. JSON

Pokud umístíte možnosti do souboru JSON šablony, vynechejte `runtimeOptions` vlastnost.

```json
{
  "configProperties": {
    "System.GC.Concurrent": false,
    "System.Threading.ThreadPool.MinThreads": "4",
    "System.Threading.ThreadPool.MaxThreads": "25"
  }
}
```

## <a name="msbuild-properties"></a>vlastnosti nástroje MSBuild

Některé možnosti konfigurace modulu runtime lze nastavit pomocí vlastností nástroje MSBuild v souboru *. csproj* nebo *. vbproj* v projektech .NET Core ve stylu sady SDK. Vlastnosti nástroje MSBuild mají přednost před možnostmi nastavenými v souboru *runtimeconfig. template. JSON* . Přepíší také všechny možnosti, které jste nastavili v souboru *[název_aplikace]. runtimeconfig. JSON* v době sestavení.

Zde je příklad souboru projektu ve stylu sady SDK s vlastnostmi MSBuild pro konfiguraci chování za běhu:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
    <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```

Vlastnosti nástroje MSBuild pro konfiguraci chování za běhu jsou uvedeny v jednotlivých článcích pro každou oblast, například [uvolňování paměti](garbage-collector.md). Jsou také uvedeny v části [Konfigurace modulu runtime](../project-sdk/msbuild-props.md#run-time-configuration-properties) Referenční dokumentace vlastností MSBuild pro projekty ve stylu sady SDK.

## <a name="environment-variables"></a>Proměnné prostředí

Proměnné prostředí lze použít k poskytnutí některých informací o konfiguraci run-time. Konfigurace možnosti modulu runtime pomocí proměnné prostředí použije nastavení pro všechny aplikace .NET Core. Konfigurační ovladače zadané jako proměnné prostředí mají obecně předponu **COMPlus_**.

Můžete definovat proměnné prostředí z ovládacích panelů systému Windows, na příkazovém řádku nebo programově voláním <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> metody v systémech Windows i UNIX.

Následující příklady ukazují, jak nastavit proměnnou prostředí na příkazovém řádku:

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
