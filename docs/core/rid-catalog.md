---
title: .NET core Runtime identifikátor (RID) katalogu
description: Další informace o identifikátor modulu Runtime (RID) a používání identifikátorů RID v .NET Core.
ms.date: 02/22/2019
ms.openlocfilehash: 0d03e39c755b43e145edf5efe48422cbae7abcab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663073"
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

- `[additional qualifiers]` dál rozlišit různé platformy. Například: `aot`.

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

.NET core 2.0 SDK zavádí koncepci přenosné identifikátorů RID. Jsou nové hodnoty, které se přidávají do grafu identifikátorů RID, které nejsou vázány na konkrétní verzi nebo distribuce operačního systému a jsou upřednostňované volbou, pokud používáte .NET Core 2.0 a vyšší. Jsou užitečné zejména při práci s více distribuce Linuxu od většina distribuce identifikátorů RID se mapují na přenosné identifikátorů RID.

Následující seznam obsahuje malou podmnožinu nejběžnější identifikátory RID používat pro každý operační systém.

## <a name="windows-rids"></a>Identifikátory RID Windows

Pouze běžné hodnoty jsou uvedeny. Nejnovější a dokončení, najdete v článku [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) souboru v úložišti CoreFX.

- Přenosná (.NET Core 2.0 nebo novější verze)
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

Zobrazit [předpoklady pro .NET Core ve Windows](windows-prerequisites.md) Další informace.

## <a name="linux-rids"></a>Linux identifikátorů RID

Pouze běžné hodnoty jsou uvedeny. Nejnovější a dokončení, najdete v článku [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) souboru v úložišti CoreFX. Zařízení se systémem distribuce není uvedená níže může pracovat s některou z přenosné identifikátorů RID. Například zařízení Raspberry Pi s Linuxová distribuce není uvedená, je možné cílit s `linux-arm`.

- Přenosná (.NET Core 2.0 nebo novější verze)
  - `linux-x64` (Většina klientů distribucí, jako jsou CentOS, Debian, Fedora, Ubuntu nebo odvozené konfigurace)
  - `linux-musl-x64` (Zjednodušené distribuce využívající [musl](https://wiki.musl-libc.org/projects-using-musl.html) Alpine Linuxu, jako je)
  - `linux-arm` (Běžící na ARM Linuxových distribucí, jako je Raspberry Pi)
- Red Hat Enterprise Linux
  - `rhel-x64` (Nahrazena `linux-x64` pro RHEL vyšší než verze 6)
  - `rhel.6-x64` (.NET core 2.0 nebo novější verze)
- Tizen (.NET Core 2.0 nebo novější verze)
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

Zobrazit [předpoklady pro .NET Core v Linuxu](linux-prerequisites.md) Další informace.

## <a name="macos-rids"></a>macOS identifikátorů RID

macOS identifikátory RID používat starší branding "OSX". Pouze běžné hodnoty jsou uvedeny. Nejnovější a dokončení, najdete v článku [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) souboru v úložišti CoreFX.

- Přenosná (.NET Core 2.0 nebo novější verze)
  - `osx-x64` (Minimální verze operačního systému je macOS 10.12 Sierra)
- macOS 10.10  Yosemite
  - `osx.10.10-x64`
- macOS 10.11 El Capitan
  - `osx.10.11-x64`
- macOS 10.12 Sierra (.NET Core 1.1 nebo novější verze)
  - `osx.10.12-x64`
- macOS 10.13 High Sierra (.NET Core 1.1 nebo novější verze)
  - `osx.10.13-x64`
- macOS 10.14 Mojave (.NET Core 1.1 nebo novější verze)
  - `osx.10.14-x64`

Zobrazit [předpoklady pro .NET Core v macOS](macos-prerequisites.md) pro další informace.

## <a name="see-also"></a>Viz také:

- [ID modulu runtime](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
