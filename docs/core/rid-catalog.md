---
title: Katalog IDentifier (RID) modulu .NET Core Runtime
description: Další informace o runtime IDentifier (RID) a jak ridy se používají v .NET Core.
ms.date: 02/22/2019
ms.openlocfilehash: feb19632f16a047ecfb2dcb697a9b837824a1929
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451730"
---
# <a name="net-core-rid-catalog"></a>Katalog RID jádra rozhraní .NET

RID je zkratka pro *Runtime IDentifier*. Hodnoty RID se používají k identifikaci cílových platforem, na kterých je aplikace spuštěna.
Používají je balíčky .NET k reprezentaci prostředků specifických pro platformu v balíčcích NuGet. Následující hodnoty jsou příklady `linux-x64`ridů: , `ubuntu.14.04-x64`, `win7-x64`, nebo `osx.10.12-x64`.
Pro balíčky s nativní závislosti RID určuje, na kterých platformách balíček lze obnovit.

V prvku souboru `<RuntimeIdentifier>` projektu lze nastavit jeden rid. Více RIdů lze definovat jako seznam oddělený středníkem v `<RuntimeIdentifiers>` prvku souboru projektu. Používají se také prostřednictvím možnosti `--runtime` s [následujícími příkazy .NET Core CLI](./tools/index.md):

- [dotnet build](./tools/dotnet-build.md)
- [dotnet clean](./tools/dotnet-clean.md)
- [dotnet pack](./tools/dotnet-pack.md)
- [dotnet publish](./tools/dotnet-publish.md)
- [dotnet restore](./tools/dotnet-restore.md)
- [dotnet run](./tools/dotnet-run.md)
- [dotnet restore](./tools/dotnet-store.md)

Ridy, které představují konkrétní operační `[os].[version]-[architecture]-[additional qualifiers]` systémy, obvykle postupujte podle tohoto vzoru: kde:

- `[os]`je zástupný název systému nebo platformy. Například, `ubuntu`.

- `[version]`je verze operačního systému ve formě čísla`.`verze oddělené tečkou ( ). Například, `15.10`.

  - Verze **by neměla** být marketingové verze, protože často představují více diskrétníverze operačního systému s různou plochou rozhraní API platformy.

- `[architecture]`je architektura procesoru. Například: `x86` `x64`, `arm`, `arm64`, nebo .

- `[additional qualifiers]`dále odlišují různé platformy. Například: `aot`.

## <a name="rid-graph"></a>Graf RID

Graf RID nebo záložní graf runtime je seznam ridů, které jsou vzájemně kompatibilní. Rids jsou definovány v balíčku [Microsoft.NETCore.Platforms.](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) Seznam podporovaných ridů a graf RID můžete zobrazit v souboru [*runtime.json,*](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) který je umístěn v `dotnet/runtime` úložišti. V tomto souboru můžete vidět, že všechny RIDs, `"#import"` s výjimkou základní jeden, obsahují příkaz. Tyto příkazy označují kompatibilní ids.

Když NuGet obnoví balíčky, pokusí se najít přesnou shodu pro zadaný běh.
Pokud není nalezena přesná shoda, NuGet přejde zpět grafu, dokud nenajde nejbližší kompatibilní systém podle grafu RID.

Následující příklad je skutečná položka `osx.10.12-x64` pro RID:

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

Výše uvedený rid `osx.10.12-x64` určuje, `osx.10.11-x64`že importy . Takže když NuGet obnoví balíčky, pokusí se `osx.10.12-x64` najít přesnou shodu v balíčku. Pokud NuGet nemůže najít konkrétní runtime, může `osx.10.11-x64` obnovit balíčky, které určují runtime, například.

Následující příklad ukazuje mírně větší graf RID definovaný také v souboru *runtime.json:*

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

Všechny RID nakonec mapovat zpět `any` do kořenového RID.

Existují některé důležité informace o RIDs, které musíte mít na paměti při práci s nimi:

- Rids jsou **neprůhledné řetězce** a měly by být považovány za černé skříňky.
- Nevytvářejte RIDs programově.
- Použijte RIDs, které jsou již definovány pro platformu.
- Rids musí být konkrétní, takže nepředpokládejte nic ze skutečné hodnoty RID.

## <a name="using-rids"></a>Použití ridů

Abyste mohli používat RIDs, musíte vědět, které RIDs existují. Na platformu se pravidelně přidávají nové hodnoty.
Nejnovější a úplnou verzi naleznete v souboru [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) v `dotnet/runtime` úložišti.

Sada .NET Core 2.0 SDK představuje koncept přenosných RIDů. Jedná se o nové hodnoty přidané do grafu RID, které nejsou vázány na konkrétní verzi nebo distribuci operačního systému a jsou upřednostňovanou volbou při použití rozhraní .NET Core 2.0 a vyšší. Jsou obzvláště užitečné při práci s více distribucí Linuxu, protože většina distribučních RIDů je mapována na přenosné RIDs.

V následujícím seznamu je uvedena malá podmnožina nejběžnějších kontrolních disteorů používaných pro každý operační tým.

## <a name="windows-rids"></a>Windows RIDs

Jsou uvedeny pouze běžné hodnoty. Nejnovější a úplnou verzi najdete v souboru `dotnet/runtime` [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) v úložišti.

- Přenosné (.NET Core 2.0 nebo novější verze)
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- Windows 7 / Windows Server 2008 R2
  - `win7-x64`
  - `win7-x86`
- Windows 8.1 / Windows Server 2012 R2
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- Windows 10 / Windows Server 2016
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

Další informace naleznete v tématu [.NET Core závislosti a požadavky](install/dependencies.md?pivots=os-windows).

## <a name="linux-rids"></a>Linuxové RID

Jsou uvedeny pouze běžné hodnoty. Nejnovější a úplnou verzi naleznete v souboru [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) v `dotnet/runtime` úložišti. Zařízení s distribucí, která není uvedena níže, mohou pracovat s jedním z přenosných zařízení ID. Například zařízení Raspberry Pi se systémem linuxové `linux-arm`distribuce, která není uvedena, mohou být cílena pomocí aplikace .

- Přenosné (.NET Core 2.0 nebo novější verze)
  - `linux-x64`(Většina desktopových distribucí jako CentOS, Debian, Fedora, Ubuntu a deriváty)
  - `linux-musl-x64`(Lehké distribuce pomocí [musl](https://wiki.musl-libc.org/projects-using-musl.html) jako Alpine Linux)
  - `linux-arm`(Linuxové distribuce běžící na ARM jako Raspberry Pi)
- Red Hat Enterprise Linux
  - `rhel-x64`(Nahrazeno `linux-x64` pro RHEL nad verzí 6)
  - `rhel.6-x64`(.NET Core 2.0 nebo novější verze)
- Tizen (.NET Core 2.0 nebo novější verze)
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

Další informace naleznete v tématu [.NET Core závislosti a požadavky](install/dependencies.md?pivots=os-linux).

## <a name="macos-rids"></a>MacOS RIDs

MacOS RID s použitím starší značky "OSX". Jsou uvedeny pouze běžné hodnoty. Nejnovější a úplnou verzi naleznete v souboru [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) v `dotnet/runtime` úložišti.

- Přenosné (.NET Core 2.0 nebo novější verze)
  - `osx-x64`(Minimální verze operačního systému je macOS 10.12 Sierra)
- macOS 10.10 Yosemite
  - `osx.10.10-x64`
- macOS 10.11 El Capitan
  - `osx.10.11-x64`
- macOS 10.12 Sierra (verze.NET Core 1.1 nebo novější)
  - `osx.10.12-x64`
- macOS 10.13 High Sierra (.NET Core 1.1 nebo novější verze)
  - `osx.10.13-x64`
- macOS 10.14 Mojave (verze.NET Core 1.1 nebo novější)
  - `osx.10.14-x64`

Další informace naleznete v tématu [.NET Core závislosti a požadavky](install/dependencies.md?pivots=os-macos).

## <a name="see-also"></a>Viz také

- [ID běhu](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/readme.md)
