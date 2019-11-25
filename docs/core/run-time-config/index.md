---
title: Konfigurace run-time
description: Naučte se konfigurovat aplikace .NET Core pomocí nastavení konfigurace za běhu.
ms.date: 11/13/2019
ms.openlocfilehash: f7074b07bdd5aca23b6caae78952d630d905c489
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283987"
---
# <a name="net-core-run-time-configuration-settings"></a>Nastavení konfigurace runtime .NET Core

.NET Core podporuje použití konfiguračních souborů a proměnných prostředí ke konfiguraci chování aplikací .NET Core v době běhu. Konfigurace běhového běhu je atraktivní možnost, pokud:

- Zdrojový kód aplikace nevlastníte nebo neovládáte, a proto ji nelze programově nakonfigurovat.

- V jednom systému se spouští více instancí aplikace současně a chcete je nakonfigurovat pro optimální výkon.

> [!NOTE]
> Tato dokumentace je probíhající práce. Pokud si všimnete, že zde uvedené informace jsou buď neúplné, nebo nepřesné, buď [otevřete problém](https://github.com/dotnet/docs/issues) , abychom nás věděli, nebo [odešlete žádost](https://github.com/dotnet/docs/pulls) o přijetí změn k vyřešení problému. Informace o odesílání žádostí o přijetí změn pro úložiště dotnet/docs najdete v [příručce pro přispěvatele](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).

.NET Core poskytuje následující mechanismy pro konfiguraci aplikací v době běhu:

- [Soubor runtimeconfig. JSON](#runtimeconfigjson)

- [Proměnné prostředí](#environment-variables)

Články v této části dokumentace jsou uspořádány podle kategorie, například ladění a uvolňování paměti. Pro *runtimeconfig. JSON* se zobrazí dostupné možnosti konfigurace (jenom .NET Core), *App. config* (jenom .NET Framework) a proměnné prostředí.

## <a name="runtimeconfigjson"></a>runtimeconfig. JSON

Zadejte možnosti konfigurace modulu runtime v části **configProperties** souboru *runtimeconfig. JSON* . Tato část obsahuje formulář:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "config-property-name1": "config-value1",
         "config-property-name2": "config-value2"
      }
   }
}
```

Tady je příklad souboru:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": true,
         "System.GC.RetainVM": true,
         "System.Threading.ThreadPool.MinThreads": "4",
         "System.Threading.ThreadPool.MaxThreads": "25"
      }
   }
}
```

Soubor *runtimeconfig. JSON* se automaticky vytvoří v adresáři buildu pomocí příkazu [dotnet Build](../tools/dotnet-build.md) . Vytvoří se také při výběru možnosti nabídky **sestavení** v aplikaci Visual Studio. Po vytvoření můžete soubor upravit.

Některé hodnoty konfigurace lze také nastavit programově voláním metody <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>.

## <a name="environment-variables"></a>Proměnné prostředí

Proměnné prostředí lze použít k poskytnutí některých informací o konfiguraci run-time. Konfigurační ovladače zadané jako proměnné prostředí mají obecně předponu **COMPlus_** .

Můžete definovat proměnné prostředí z ovládacích panelů systému Windows, na příkazovém řádku nebo programově voláním metody <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> v systémech Windows a UNIX.

Následující příklady ukazují, jak nastavit proměnnou prostředí na příkazovém řádku:

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
