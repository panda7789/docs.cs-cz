---
title: .NET core Runtime identifikátor (RID) katalogu
description: Další informace o identifikátor modulu Runtime (RID) a používání identifikátorů RID v .NET Core.
ms.date: 07/19/2018
ms.openlocfilehash: 5a6dda260b4be85e54f4075f3edf12210b385289
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534539"
---
# <a name="net-core-rid-catalog"></a>Katalog identifikátorů RID .NET core

Je zkratka pro identifikátorů RID *identifikátor modulu Runtime*. Identifikátor RID hodnoty se používají k identifikaci cílové platformy, kde je aplikace spuštěná.
Balíčky .NET, se používá k reprezentování specifické pro platformu prostředky v balíčcích NuGet. Následující hodnoty jsou příklady identifikátorů RID: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, nebo `osx.10.12-x64`.
Pro balíčky s nativní závislosti označí RID, na kterých platformách lze obnovit balíček.

Jediný identifikátorů RID je možné nastavit v `<RuntimeIdentifier>` prvek souboru projektu. Více identifikátorů RID je definovat jako seznam oddělený středníkem v souboru projektu `<RuntimeIdentifiers>` elementu. Používají se také prostřednictvím `--runtime` možnost následujícím [příkazy rozhraní příkazového řádku .NET Core](./tools/index.md):

- [dotnet build](./tools/dotnet-build.md)
- [dotnet clean](./tools/dotnet-clean.md)
- [dotnet pack](./tools/dotnet-pack.md)
- [dotnet publish](./tools/dotnet-publish.md)
- [dotnet restore](./tools/dotnet-restore.md)
- [dotnet run](./tools/dotnet-run.md)
- [dotnet restore](./tools/dotnet-store.md)

Identifikátory RID, představující konkrétní operační systémy obvykle podle tohoto vzoru: `[os].[version]-[architecture]-[additional qualifiers]` kde:

- `[os]` je moniker provozní/platform system. Například, `ubuntu`.

- `[version]` verze operačního systému ve formě oddělené tečkou (`.`) číslo verze. Například, `15.10`.

  - Verze **by neměl** být marketingové verze, jak často představují více samostatných verzí operačního systému s použitím různých styčné plochy rozhraní API platformy.

- `[architecture]` je na architektuře procesoru. Příklad: `x86`, `x64`, `arm`, nebo `arm64`.

- `[additional qualifiers]` dál rozlišit různé platformy. Příklad: `aot` nebo `corert`.

## <a name="rid-graph"></a>Identifikátor RID grafu

Graf identifikátorů RID nebo záložní grafu modulu runtime je seznam identifikátorů RID, které jsou vzájemně kompatibilní. Identifikátory RID, které jsou definovány v [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) balíčku. Můžete zobrazit seznam podporovaných identifikátorů RID a graf identifikátorů RID [ *runtime.json* ](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) soubor, který se nachází v úložišti CoreFX. V tomto souboru, uvidíte, že všechny identifikátory RID, s výjimkou je základní obsahovat `"#import"` příkazu. Tyto příkazy označují kompatibilní identifikátorů RID.

Když NuGet obnoví balíčky, pokusí se vyhledat přesnou shodu zadaného modulu runtime.
Pokud se najde přesná shoda, NuGet vás zpět grafu dokud vyhledá nejbližší kompatibilní systému podle identifikátorů RID grafu.

V následujícím příkladu je skutečná položku `osx.10.12-x64` identifikátorů RID:

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

Výše uvedené identifikátorů RID, který určuje `osx.10.12-x64` importuje `osx.10.11-x64`. Proto když NuGet obnoví balíčky, pokusí se vyhledat přesnou shodu pro `osx.10.12-x64` v balíčku. Pokud NuGet nemůžete najít konkrétní modulu runtime, můžete obnovit balíčky, které určují `osx.10.11-x64` moduly runtime, například.

Následující příklad ukazuje mírně větší identifikátorů RID graf také definováno v *runtime.json* souboru:

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

Všechny identifikátory RID se nakonec mapování zpět do kořenového adresáře `any` identifikátorů RID.

Zde jsou některé důležité informace o identifikátorech RID, které je třeba vzít v úvahu při práci s nimi:

- Jsou identifikátory RID **neprůhledné řetězce** a by měl být považován za černé skříňky.
- Nezačleňujte identifikátorů RID prostřednictvím kódu programu.
- Použijte identifikátory RID, které jsou již definovány pro platformu.
- Identifikátory RID musí mít konkrétní, takže Nepředpokládejte, že je vše od skutečné hodnoty identifikátorů RID.

## <a name="using-rids"></a>Pomocí identifikátorů RID

Aby bylo možné používat identifikátory RID, budete muset vědět, které existují identifikátorů RID. Na platformu jsou pravidelně přidávat nové hodnoty.
Nejnovější a dokončení, najdete v článku [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) souboru v úložišti CoreFX.

.NET core 2.0 SDK zavádí koncepci přenosné identifikátorů RID. Jsou nové hodnoty, které se přidávají do grafu identifikátorů RID, které nejsou vázány na konkrétní verzi nebo distribuce operačního systému. Jsou užitečné zejména při práci s více distribuce Linuxu.

Následující seznam uvádí nejběžnější identifikátory RID používat pro každý operační systém. Nezahrnuje `arm` nebo `corert` hodnoty.

## <a name="windows-rids"></a>Identifikátory RID Windows

- Přenosná
  - `win-x86`
  - `win-x64`
- Windows 7 / Windows Server 2008 R2
  - `win7-x64`
  - `win7-x86`
- Windows 8 nebo Windows Server 2012
  - `win8-x64`
  - `win8-x86`
  - `win8-arm`
- Windows 8.1 / Windows Server 2012 R2
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- Windows 10 / Windows Server 2016
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

Zobrazit [předpoklady pro .NET Core ve Windows](windows-prerequisites.md) Další informace.

## <a name="linux-rids"></a>Linux identifikátorů RID

- Přenosná
  - `linux-x64`
- CentOS
  - `centos-x64`
  - `centos.7-x64`
- Debian
  - `debian-x64`
  - `debian.8-x64`
  - `debian.9-x64` (.NET core 1.1 nebo novější verze)
- Fedora
  - `fedora-x64`
  - `fedora.27-x64`
  - `fedora.28-x64` (.NET core 1.1 nebo novější verze)
- Gentoo (.NET Core 2.0 nebo novější verze)
  - `gentoo-x64`
- openSUSE
  - `opensuse-x64`
  - `opensuse.42.3-x64`
- Oracle Linux
  - `ol-x64`
  - `ol.7-x64`
  - `ol.7.0-x64`
  - `ol.7.1-x64`
  - `ol.7.2-x64`
  - `ol.7.3-x64`
  - `ol.7.4-x64`
- Red Hat Enterprise Linux
  - `rhel-x64`
  - `rhel.6-x64` (.NET core 2.0 nebo novější verze)
  - `rhel.7-x64`
  - `rhel.7.1-x64`
  - `rhel.7.2-x64`
  - `rhel.7.3-x64` (.NET core 2.0 nebo novější verze)
  - `rhel.7.4-x64` (.NET core 2.0 nebo novější verze)
- Tizen (.NET Core 2.0 nebo novější verze)
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`
- Ubuntu
  - `ubuntu-x64`
  - `ubuntu.14.04-x64`
  - `ubuntu.16.04-x64`
  - `ubuntu.17.10-x64`
  - `ubuntu.18.04-x64`
- Odvozené Ubuntu
  - `linuxmint.17-x64`
  - `linuxmint.17.1-x64`
  - `linuxmint.17.2-x64`
  - `linuxmint.17.3-x64`
  - `linuxmint.18-x64` (.NET core 2.0 nebo novější verze)
  - `linuxmint.18.1-x64` (.NET core 2.0 nebo novější verze)
  - `linuxmint.18.2-x64` (.NET core 2.0 nebo novější verze)
  - `linuxmint.18.3-x64` (.NET core 2.0 nebo novější verze)
- SUSE Enterprise Linux (SLES) (.NET Core 2.0 nebo novější verze)
  - `sles-x64`
  - `sles.12-x64`
  - `sles.12.1-x64`
  - `sles.12.2-x64`
  - `sles.12.3-x64`
- Nástroj Alpine Linuxu (.NET Core 2.1 nebo novější verze)
  - `alpine-x64`
  - `alpine.3.7-x64`

Zobrazit [předpoklady pro .NET Core v Linuxu](linux-prerequisites.md) Další informace.

## <a name="macos-rids"></a>macOS identifikátorů RID

macOS identifikátory RID používat starší branding "OSX".

- `osx-x64` (.NET core 2.0 nebo novější verze, minimální verze je `osx.10.12-x64`)
- `osx.10.10-x64`
- `osx.10.11-x64`
- `osx.10.12-x64` (.NET core 1.1 nebo novější verze)
- `osx.10.13-x64`

Zobrazit [předpoklady pro .NET Core v macOS](macos-prerequisites.md) pro další informace.

## <a name="android-rids-net-core-20-or-later-versions"></a>Android identifikátorů RID (.NET Core 2.0 nebo novější verze)

- `android`
- `android.21`

## <a name="see-also"></a>Viz také:

- [ID modulu runtime](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
