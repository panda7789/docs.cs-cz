---
title: Katalog identifikátorů runtime .NET Core (RID)
description: Přečtěte si o identifikátoru modulu runtime (RID) a způsobu použití identifikátorů RID v .NET Core.
ms.date: 02/22/2019
ms.openlocfilehash: d401cf3a8a147a16c1aea0ba7d5e799cf182583e
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740574"
---
# <a name="net-core-rid-catalog"></a>Katalog identifikátorů RID .NET Core

Identifikátor RID je pro *identifikátor modulu runtime*krátký. Hodnoty RID slouží k identifikaci cílových platforem, ve kterých se aplikace spouští.
Jsou používány balíčky .NET k reprezentaci prostředků specifických pro platformu v balíčcích NuGet. Následující hodnoty jsou příklady identifikátorů RID: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`nebo `osx.10.12-x64`.
U balíčků s nativními závislostmi Určuje identifikátor RID na kterých platformách se balíček dá obnovit.

Jeden identifikátor RID lze nastavit v prvku `<RuntimeIdentifier>` souboru projektu. Více identifikátorů RID lze definovat jako seznam středníkem oddělených v `<RuntimeIdentifiers>` elementu souboru projektu. Používají se taky prostřednictvím možnosti `--runtime` s následujícími [.NET Core CLI příkazy](./tools/index.md):

- [dotnet build](./tools/dotnet-build.md)
- [dotnet clean](./tools/dotnet-clean.md)
- [dotnet pack](./tools/dotnet-pack.md)
- [dotnet publish](./tools/dotnet-publish.md)
- [dotnet restore](./tools/dotnet-restore.md)
- [dotnet run](./tools/dotnet-run.md)
- [dotnet restore](./tools/dotnet-store.md)

Identifikátorů RID, které reprezentují konkrétní operační systémy, se obvykle řídí tímto vzorem: `[os].[version]-[architecture]-[additional qualifiers]`, kde:

- `[os]` je moniker operačního systému nebo platformy. Například `ubuntu`.

- `[version]` je verze operačního systému ve formě čísla verze odděleného tečkou (`.`). Například `15.10`.

  - Verze **by neměla** být marketingová verze, protože často představují více diskrétních verzí operačního systému s různou oblastí rozhraní API platformy.

- `[architecture]` je architektura procesoru. Například: `x86`, `x64`, `arm`nebo `arm64`.

- `[additional qualifiers]` dále odlišit různé platformy. Například: `aot`.

## <a name="rid-graph"></a>Graf RID

Graf RID nebo modul runtime Fallback za běhu je seznam identifikátorů ridů, které jsou vzájemně kompatibilní. Identifikátorů RID jsou definované v balíčku [Microsoft. NETCore. Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) . Můžete se podívat na seznam podporovaných identifikátorů RID a grafu RID v souboru [*runtime. JSON*](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) , který se nachází v úložišti CoreFX. V tomto souboru vidíte, že všechny identifikátorů RID, s výjimkou základní třídy, obsahují příkaz `"#import"`. Tyto příkazy označují kompatibilní identifikátorů RID.

Když NuGet obnoví balíčky, pokusí se najít přesnou shodu pro zadaný modul runtime.
Pokud se nenajde přesná shoda, NuGet se vrátí do grafu, dokud nenajde nejbližší kompatibilní systém podle grafu RID.

V následujícím příkladu je aktuální položka pro `osx.10.12-x64` RID:

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

Výše uvedené identifikátory RID určuje, že `osx.10.12-x64` import `osx.10.11-x64`. Takže když NuGet obnoví balíčky, pokusí se najít přesnou shodu pro `osx.10.12-x64` v balíčku. Pokud NuGet nemůže najít konkrétní modul runtime, může obnovit balíčky, které určují `osx.10.11-x64` modul runtime, například.

Následující příklad ukazuje trochu větší graf RID, který je definován také v souboru *runtime. JSON* :

```
    win7-x64    win7-x86
       |   \   /    |
       |   win7     |
       |     |      |
    win-x64  |  win-x86
          \  |  /
            win
             |
            any
```

Všechny identifikátorů RID nakonec mapují zpátky na kořenový `any` identifikátor RID.

Existují některé okolnosti týkající se identifikátorů RID, které je třeba vzít v úvahu při práci s nimi:

- Identifikátorů RID jsou **neprůhledné řetězce** a měly by se považovat za černé čtverečky.
- Nevytvářejte identifikátorů RID programově.
- Použijte identifikátorů RID, které už jsou pro platformu definované.
- Identifikátorů RID musí být konkrétní, takže nemusíte nic od skutečné hodnoty RID předpokládat.

## <a name="using-rids"></a>Použití identifikátorů RID

Aby bylo možné používat identifikátorů RID, musíte zjistit, které identifikátorů RID existují. K platformě se pravidelně přidávají nové hodnoty.
Nejnovější a kompletní verzi najdete v souboru [runtime. JSON](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) v úložišti CoreFX.

Sada .NET Core 2,0 SDK zavádí koncept přenosných identifikátorů RID. Jsou to nové hodnoty přidané do grafu RID, které nejsou vázané na konkrétní verzi nebo distribuci operačního systému, a jsou upřednostňovanou volbou při použití .NET Core 2,0 a vyšší. Jsou zvláště užitečné při práci s více Linux distribuce, protože většina distribučních identifikátorů RID je mapována na přenosné identifikátorů RID.

Následující seznam obsahuje malou podmnožinu nejběžnějších identifikátorů RID používaných pro každý operační systém.

## <a name="windows-rids"></a>Identifikátorů RID Windows

Jsou uvedeny pouze běžné hodnoty. Nejnovější a kompletní verzi najdete v souboru [runtime. JSON](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) v úložišti CoreFX.

- Přenosná verze (.NET Core 2,0 nebo novější)
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- Windows 7 / Windows Server 2008 R2
  - `win7-x64`
  - `win7-x86`
- Windows 8.1/Windows Server 2012 R2
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- Windows 10/Windows Server 2016
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

Další informace najdete v tématu [závislosti a požadavky .NET Core](install/dependencies.md?tabs=netcore30&pivots=os-windows) .

## <a name="linux-rids"></a>Linux identifikátorů RID

Jsou uvedeny pouze běžné hodnoty. Nejnovější a kompletní verzi najdete v souboru [runtime. JSON](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) v úložišti CoreFX. Zařízení s distribucí, která nejsou uvedená níže, můžou fungovat s jedním z přenosných identifikátorů RID. Například zařízení maliny PI, na kterých běží distribuce systému Linux, nejsou uvedená v seznamu mohou být cílem `linux-arm`.

- Přenosná verze (.NET Core 2,0 nebo novější)
  - `linux-x64` (Většina distribucí počítačů, jako jsou CentOS, Debian, Fedora, Ubuntu a deriváty)
  - `linux-musl-x64` (prosté distribuce pomocí [MUSL](https://wiki.musl-libc.org/projects-using-musl.html) jako Alpine Linux)
  - `linux-arm` (distribuce systému Linux spuštěná na ARM, jako je například Malina PI)
- Red Hat Enterprise Linux
  - `rhel-x64` (nahrazeno `linux-x64` pro RHEL nad verzí 6)
  - `rhel.6-x64` (.NET Core 2,0 nebo novější verze)
- Tizen (.NET Core 2,0 nebo novější verze)
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

Další informace najdete v tématu [závislosti a požadavky .NET Core](install/dependencies.md?tabs=netcore30&pivots=os-linux) .

## <a name="macos-rids"></a>macOS identifikátorů RID

macOS identifikátorů RID používá starší značku "OSX". Jsou uvedeny pouze běžné hodnoty. Nejnovější a kompletní verzi najdete v souboru [runtime. JSON](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) v úložišti CoreFX.

- Přenosná verze (.NET Core 2,0 nebo novější)
  - `osx-x64` (minimální verze operačního systému je macOS 10,12 Sierra)
- macOS 10.10  Yosemite
  - `osx.10.10-x64`
- macOS 10,11 El Capitan
  - `osx.10.11-x64`
- macOS 10,12 Sierra (.NET Core 1,1 nebo novější verze)
  - `osx.10.12-x64`
- macOS 10,13 High Sierra (.NET Core 1,1 nebo novější verze)
  - `osx.10.13-x64`
- macOS 10,14 Mojave (.NET Core 1,1 nebo novější verze)
  - `osx.10.14-x64`

Další informace najdete v tématu [závislosti a požadavky .NET Core](install/dependencies.md?tabs=netcore30&pivots=os-macos) .

## <a name="see-also"></a>Viz také:

- [ID modulu runtime](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/readme.md)
