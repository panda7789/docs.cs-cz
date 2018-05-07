---
title: Katalog .NET core Runtime identifikátor (RID)
description: Další informace o identifikátoru Runtime (RID) a použití identifikátorů RID v .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 09/07/2017
ms.openlocfilehash: 81f9e5f65385bbd81c7fdae7f75c62d11b6f6319
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="net-core-rid-catalog"></a>.NET core identifikátorů RID katalogu

Identifikátorů RID je zkratka pro *Runtime identifikátor*. Hodnoty identifikátorů RID se používají k identifikaci cílové platformy, kde je aplikace spuštěná.
Balíčky .NET jejich se používá k reprezentování specifické pro platformu prostředky do balíčků NuGet. Následující hodnoty jsou příklady identifikátorů RID: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, nebo `osx.10.12-x64`.
Pro balíčky s nativní závislosti identifikátor RID označí, na kterých platformách lze obnovit balíček.

Jediný identifikátorů RID, může být nastavena v `<RuntimeIdentifier>` element souboru projektu. Více identifikátorů RID, může být definováno jako seznam oddělený středníkem v souboru projektu `<RuntimeIdentifiers>` elementu. Používají se také prostřednictvím `--runtime` možnost s následující [.NET Core rozhraní příkazového řádku](./tools/index.md):

- [dotnet build](./tools/dotnet-build.md)
- [dotnet clean](./tools/dotnet-clean.md)
- [dotnet pack](./tools/dotnet-pack.md)
- [dotnet publish](./tools/dotnet-publish.md)
- [dotnet restore](./tools/dotnet-restore.md)
- [dotnet run](./tools/dotnet-run.md)
- [dotnet restore](./tools/dotnet-store.md)

Identifikátory RID, představují konkrétní operační systémy obvykle podívejte se na tento vzor: `[os].[version]-[architecture]-[additional qualifiers]` kde:

- `[os]` je přezdívka systému operační/platformy. Například `ubuntu`.

- `[version]` verze operačního systému ve formě oddělené tečkou (`.`) číslo verze. Například `15.10`.

  - Verze **by neměl** být marketingové verze, protože často představují více diskrétní verzí operačního systému s použitím různých útoku na platformě rozhraní API.

- `[architecture]` je na architektuře procesoru. Příklad: `x86`, `x64`, `arm`, nebo `arm64`.

- `[additional qualifiers]` dál rozlišit různých platformách. Příklad: `aot` nebo `corert`.

## <a name="rid-graph"></a>Graf identifikátorů RID

Graf identifikátorů RID nebo modul runtime záložní grafu je seznam identifikátorů RID, které jsou vzájemně kompatibilní. Identifikátory RID, které jsou definovány v [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) balíčku. Můžete zobrazit seznam podporovaných identifikátorů RID a grafu identifikátorů RID ve [ *runtime.json* ](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) souboru, který se nachází v úložišti CoreFX. V tomto souboru, uvidíte, že všechny identifikátory RID, s výjimkou toho, jaké základní obsahovat `"#import"` příkaz. Tyto příkazy označují kompatibilní identifikátorů RID.

Když NuGet obnoví balíčky, pokusí se najít přesnou shodu pro zadaný modulu runtime.
Pokud není nalezena přesná shoda, NuGet provede zpět grafu dokud nenajde nejbližší kompatibilní systém podle grafu identifikátorů RID.

Následující příklad je skutečný položku `osx.10.12-x64` identifikátorů RID:

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

Výše uvedené identifikátorů RID Určuje, že `osx.10.12-x64` importuje `osx.10.11-x64`. Ano, když NuGet obnoví balíčky, pokusí se najít přesnou shodu pro `osx.10.12-x64` v balíčku. Pokud NuGet nemůže najít konkrétní modul runtime, ho můžete obnovit balíčky, které určují `osx.10.11-x64` moduly runtime, např.

Následující příklad ukazuje mírně větší identifikátorů RID graf také definovat v *runtime.json* souboru:

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

Všechny identifikátory RID se nakonec mapování zpátky ke kořenové `any` identifikátorů RID.

Existují některé aspekty o identifikátorů RID, které je třeba při práci s nimi mějte na paměti:

- Jsou identifikátorů RID **neprůhledného řetězce** a by měl být považován za černé polí.
- Nemáte prostřednictvím kódu programu sestavení identifikátorů RID.
- Použijte identifikátory RID, které jsou již definováni pro platformu.
- Identifikátory RID musí být konkrétní, takže Nepředpokládejte, že je vše od skutečné hodnoty identifikátorů RID.

## <a name="using-rids"></a>Pomocí identifikátorů RID

Abyste mohli použít identifikátorů RID, budete muset vědět, které existují identifikátorů RID. Pro platformu jsou pravidelně přidávány nové hodnoty.
Nejnovější a kompletní verze, najdete v článku [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) souboru v úložišti CoreFX.

.NET core 2.0 SDK zavádí koncepci přenosné identifikátorů RID. Jsou nové hodnoty přidány do grafu, identifikátorů RID, které nejsou vázáno na konkrétní verzi nebo distribuce operačního systému. Jsou zvláště užitečné při plánování práce s více distribucích systému Linux.

V následujícím seznamu jsou nejběžnější identifikátorů RID, použít pro každý operační systém. Ho nezahrnuje `arm` nebo `corert` hodnoty.

## <a name="windows-rids"></a>Windows identifikátorů RID

- Přenositelností
  - `win-x86`
  - `win-x64`
- Windows 7 / Windows Server 2008 R2
  - `win7-x64`
  - `win7-x86`
- Windows 8 nebo Windows Server 2012
  - `win8-x64`
  - `win8-x86`
  - `win8-arm`
- Windows 8.1 nebo Windows Server 2012 R2
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- Windows 10 nebo Windows Server 2016
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

V tématu [požadavky pro .NET Core v systému Windows](windows-prerequisites.md) Další informace.

## <a name="linux-rids"></a>Linux identifikátorů RID

- Přenositelností
  - `linux-x64`
- CentOS
  - `centos-x64`
  - `centos.7-x64`
- Debian
  - `debian-x64`
  - `debian.8-x64`
- Fedora
  - `fedora-x64`
  - `fedora.24-x64`
  - `fedora.25-x64` (.NET core 2.0 nebo novější verze)
  - `fedora.26-x64` (.NET core 2.0 nebo novější verze)
- Gentoo (.NET Core 2.0 nebo novější verze)
  - `gentoo-x64`
- openSUSE
  - `opensuse-x64`
  - `opensuse.42.1-x64`
- Oracle Linux
  - `ol-x64`
  - `ol.7-x64`
  - `ol.7.0-x64`
  - `ol.7.1-x64`
  - `ol.7.2-x64`
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
- Ubuntu
  - `ubuntu-x64`
  - `ubuntu.14.04-x64`
  - `ubuntu.14.10-x64`
  - `ubuntu.15.04-x64`
  - `ubuntu.15.10-x64`
  - `ubuntu.16.04-x64`
  - `ubuntu.16.10-x64`
- Ubuntu odvozené konfigurace
  - `linuxmint.17-x64`
  - `linuxmint.17.1-x64`
  - `linuxmint.17.2-x64`
  - `linuxmint.17.3-x64`
  - `linuxmint.18-x64`
  - `linuxmint.18.1-x64` (.NET core 2.0 nebo novější verze)

V tématu [požadavky pro .NET Core v systému Linux](linux-prerequisites.md) Další informace.

## <a name="macos-rids"></a>systému macOS identifikátorů RID

systému macOS RID použijte starší branding "OSX".

- `osx-x64` (.NET core 2.0 nebo novější verze, minimální verze je `osx.10.12-x64`)
- `osx.10.10-x64`
- `osx.10.11-x64`
- `osx.10.12-x64` (.NET core 1.1 nebo novější verze)
- `osx.10.13-x64`

V tématu [požadavky pro .NET Core v systému macOS](macos-prerequisites.md) Další informace.

## <a name="android-rids-net-core-20-or-later-versions"></a>Android identifikátorů RID (.NET Core 2.0 nebo novější verze)

- `android`
- `android.21`

## <a name="see-also"></a>Viz také

[ID modulu runtime](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
