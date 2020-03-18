---
title: Možnosti konfigurace za běhu
description: Zjistěte, jak nakonfigurovat aplikace .NET Core pomocí nastavení konfigurace za běhu.
ms.date: 01/21/2020
ms.openlocfilehash: ddf68c30e620a06856f65e71bd050e1b77618f20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399159"
---
# <a name="net-core-run-time-configuration-settings"></a>Nastavení konfigurace jádra .NET

Rozhraní .NET Core podporuje použití konfiguračních souborů a proměnných prostředí ke konfiguraci chování aplikací .NET Core za běhu. Konfigurace za běhu je atraktivní volbou, pokud:

- Nevlastníte ani neřídíte zdrojový kód aplikace, a proto jej nelze programově konfigurovat.

- Více instancí aplikace spustit současně v jednom systému a chcete nakonfigurovat každý pro optimální výkon.

> [!NOTE]
> Tato dokumentace je nedokončená práce. Pokud zjistíte, že zde uvedené informace jsou neúplné nebo nepřesné, [otevřete problém,](https://github.com/dotnet/docs/issues) abyste nám o tom měli vědět, nebo [odešlete žádost o přijetí informací](https://github.com/dotnet/docs/pulls) k řešení problému. Informace o odesílání žádostí o přijetí vyžádat pro úložiště dotnet/docs naleznete v [příručce přispěvatele](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).

Jádro .NET poskytuje následující mechanismy pro konfiguraci chování aplikací za běhu:

- [Soubor runtimeconfig.json](#runtimeconfigjson)

- [Vlastnosti MSBuild](#msbuild-properties)

- [Proměnné prostředí](#environment-variables)

Některé hodnoty konfigurace lze také nastavit programově voláním <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metody.

Články v této části dokumentace jsou uspořádány podle kategorie, například [ladění](debugging-profiling.md) a [uvolňování paměti](garbage-collector.md). V příslušných případech jsou zobrazeny možnosti konfigurace pro soubory *runtimeconfig.json,* vlastnosti MSBuild, proměnné prostředí a pro křížový odkaz soubory *app.config* pro projekty rozhraní .NET Framework.

## <a name="runtimeconfigjson"></a>runtimeconfig.json

Při [vytváření](../tools/dotnet-build.md)projektu je ve výstupním adresáři generován soubor *[appname].runtimeconfig.json.* Pokud soubor *runtimeconfig.template.json* existuje ve stejné složce jako soubor projektu, všechny možnosti konfigurace, které obsahuje, jsou sloučeny do souboru *[appname].runtimeconfig.json.* Pokud vytváříte aplikaci sami, vložte všechny možnosti konfigurace do souboru *runtimeconconfig.template.json.* Pokud právě spouštěte aplikaci, vložte je přímo do souboru *[appname].runtimeconfig.json.*

> [!NOTE]
> Soubor *[appname].runtimeconfig.json* bude přepsán na následujícísestavení.

V části **configProperties** souborů *runtimeconfig.json* určete možnosti konfigurace. Tato část má formulář:

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a>Příklad souboru [appname].runtimeconfig.json

Pokud umisťujete možnosti do výstupního souboru JSON, vnořte je pod `runtimeOptions` vlastnost.

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

### <a name="example-runtimeconfigtemplatejson-file"></a>Příklad souboru runtimeconfig.template.json

Pokud umisťujete možnosti do souboru Šablony `runtimeOptions` JSON, vyneche vlastnost.

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

Některé možnosti konfigurace za běhu lze nastavit pomocí vlastností MSBuild v souboru *.csproj* nebo *.vbproj* projektů .NET Core ve stylu sady SDK. Vlastnosti MSBuild mají přednost před možnostmi nastaveným v souboru *runtimeconfig.template.json.* Také přepsat všechny možnosti, které nastavíte v souboru *[appname].runtimeconfig.json* v době sestavení.

Zde je příklad souboru projektu ve stylu sady SDK s vlastnostmi msbuild pro konfiguraci chování za běhu:

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

Vlastnosti MSBuild pro konfiguraci chování za běhu jsou uvedeny v jednotlivých článcích pro každou oblast, například [uvolňování paměti](garbage-collector.md).

## <a name="environment-variables"></a>Proměnné prostředí

Proměnné prostředí lze použít k zadání některých informací o konfiguraci za běhu. Konfigurační knoflíky určené jako proměnné prostředí mají obecně předponu **COMPlus_**.

Proměnné prostředí můžete definovat z Ovládacích panelů systému Windows na příkazovém řádku nebo programově voláním <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> metody v systémech Windows i Unix.

Následující příklady ukazují, jak nastavit proměnnou prostředí na příkazovém řádku:

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
