---
title: Publikování .NET Core aplikací pomocí rozhraní příkazového řádku
description: Zjistěte, jak publikovat aplikaci .NET Core s nástroji .NET Core SDK rozhraní příkazového řádku (CLI).
author: thraka
ms.author: adegeo
ms.date: 01/16/2019
dev_langs:
- csharp
- vb
ms.custom: seodec18
ms.openlocfilehash: 22494a87b4f6aaa6bd1a57873493f64df3b1ecb8
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359728"
---
# <a name="publish-net-core-apps-with-the-cli"></a>Publikování .NET Core aplikací pomocí rozhraní příkazového řádku

Tento článek ukazuje, jak publikovat aplikaci .NET Core z příkazového řádku. .NET core nabízí tři způsoby, jak publikovat aplikace. Nasazení závisí na architektuře vytvoří soubor .dll napříč platformami, která používá místně nainstalovaný modul runtime .NET Core. Vytvoří spustitelný soubor závisí na architektuře specifické pro platformu spustitelný soubor, který používá místně nainstalovaný modul runtime .NET Core. Samostatný spustitelný soubor vytvoří spustitelný soubor pro konkrétní platformu a obsahuje místní kopie modulu runtime .NET Core.

Přehled těchto publikování režimech najdete v tématu [nasazení aplikace .NET Core](index.md).

Hledáte rychlý pomoc pomocí rozhraní příkazového řádku? Následující tabulka ukazuje několik příkladů toho, jak publikovat aplikaci. Můžete určit cílovou architekturu s `-f <TFM>` parametr nebo úpravou souboru projektu. Další informace najdete v tématu [publikování Základy](#publishing-basics).

| Režim publikování | Verze sady SDK | Příkaz |
| ------------ | ----------- | ------- |
| Nasazení závisí na architektuře | 2.x | `dotnet publish -c Release` |
| Spustitelný soubor závisí na architektuře | 2.2 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3.0* | `dotnet publish -c Release` |
| Samostatná nasazení      | 2.1 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 2.2 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained true` |

> [!IMPORTANT]
> \*Při použití sady SDK verze 3.0, závisí na architektuře spustitelný soubor to je výchozí režim publikování při spuštění na úrovni basic `dotnet publish` příkazu. To platí jenom pro projekty, které se zaměřují **.NET Core 2.1** nebo **.NET Core 3.0**.

## <a name="publishing-basics"></a>Základní informace o publikování

`<TargetFramework>` Nastavení souboru projektu určuje výchozí Cílová architektura, která při publikování vaší aplikace. Můžete změnit cílovou architekturu na libovolný platný [cílové rozhraní Framework Moniker (TFM)](../../standard/frameworks.md). Například, pokud váš projekt používá `<TargetFramework>netcoreapp2.2</TargetFramework>`, se vytvoří binární soubor, který cílí na .NET Core 2.2. TFM zadané v tomto nastavení je výchozí cíl používané [ `dotnet publish` ](../tools/dotnet-publish.md) příkazu.

Pokud chcete cílit na více než jedno rozhraní, můžete nastavit `<TargetFrameworks>` nastavení k více než jednu hodnotu TFM oddělené středníkem. Jedno z rozhraní s publikováním `dotnet publish -f <TFM>` příkazu. Pokud máte například `<TargetFrameworks>netcoreapp2.1;netcoreapp2.2</TargetFrameworks>` a spusťte `dotnet publish -f netcoreapp2.1`, se vytvoří binární soubor, který cílí na .NET Core 2.1.

Není-li jinak nastavit výstupní adresář [ `dotnet publish` ](../tools/dotnet-publish.md) příkaz je `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/`. Výchozí hodnota **konfiguraci sestavení** režim je **ladění** není-li změnit `-c` parametr. Například `dotnet publish -c Release -f netcoreapp2.1` publikuje do `myfolder/bin/Release/netcoreapp2.1/publish/`.

Pokud používáte .NET Core SDK 3.0, výchozí režim pro aplikace, že cílová verze .NET Core 2.1, 2.2 nebo 3.0 je spustitelný soubor závisí na architektuře publikování.

Pokud používáte .NET Core SDK 2.1, výchozí režim pro aplikace, že je verze cílového rozhraní .NET Core 2.1, 2.2 nasazení závisí na architektuře publikování.

### <a name="native-dependencies"></a>Nativní závislosti

Pokud vaše aplikace obsahuje nativní závislosti, nebude fungovat v různých operačních systémů. Například pokud vaše aplikace používá nativní rozhraní API systému Win32, nebude fungovat v systému macOS nebo Linux. Je třeba zadat kód specifický pro platformu a kompilace spustitelný soubor pro každou platformu.

Zvažte také, pokud má knihovna odkazujete nativní závislost, vaše aplikace se možná nespustí na všech platformách. Ale je možné, který se odkazuje na balíček NuGet je součástí verze specifické pro platformu pro zpracování požadované závislosti nativního za vás.

Při distribuci aplikace s nativní závislosti, budete možná muset použít `dotnet publish -r <RID>` přepínač tak, aby zadejte cílovou platformu, kterou chcete publikovat pro. Seznam identifikátorů modulů runtime, naleznete v tématu [identifikátor modulu Runtime (RID) katalogu](../rid-catalog.md).

Další informace o specifických pro platformu binárních souborů se věnuje [spustitelného souboru závisí na architektuře](#framework-dependent-executable) a [samostatná nasazení](#self-contained-deployment) oddíly.

## <a name="sample-app"></a>Ukázková aplikace

Tyto aplikace můžete použít k prozkoumání příkazy pro publikování. Vytvoření aplikace spuštěním následujících příkazů v terminálu:

```dotnetcli
mkdir apptest1
cd apptest1
dotnet new console
dotnet add package Figgle
```

`Program.cs` Nebo `Program.vb` souboru, který je generován šablonou konzoly musí změnit tak, aby následující:

```csharp
using System;

namespace apptest1
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"));
        }
    }
}
```

```vb
Imports System

Module Program
    Sub Main(args As String())
        Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"))
    End Sub
End Module
```

Při spuštění aplikace ([`dotnet run`](../tools/dotnet-run.md)), se zobrazí následující výstup:

```terminal
  _   _      _ _         __        __         _     _ _
 | | | | ___| | | ___    \ \      / /__  _ __| | __| | |
 | |_| |/ _ \ | |/ _ \    \ \ /\ / / _ \| '__| |/ _` | |
 |  _  |  __/ | | (_) |    \ V  V / (_) | |  | | (_| |_|
 |_| |_|\___|_|_|\___( )    \_/\_/ \___/|_|  |_|\__,_(_)
                     |/
```

## <a name="framework-dependent-deployment"></a>Nasazení závisí na architektuře

Pro .NET Core SDK 2.x rozhraní příkazového řádku, závisí na architektuře nasazení (chyba) je výchozí režim pro základní `dotnet publish` příkazu.

Při publikování aplikací tak, jak disketové jednotky, `<PROJECT-NAME>.dll` ve vytvoří soubor `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` složky. Ke spuštění vaší aplikace, přejděte do složky výstupu a použít `dotnet <PROJECT-NAME>.dll` příkazu.

Vaše aplikace je nakonfigurovaná k cílení na konkrétní verzi .NET Core. Která je určená .NET Core runtime musí být na počítači, ve kterém chcete spustit vaši aplikaci. Například pokud vaše aplikace cílí na .NET Core 2.2, musí mít všechny počítače, které vaše aplikace běží na modulu runtime .NET Core 2.2 nainstalované. Jak je uvedeno v [publikování Základy](#publishing-basics) oddílu, můžete upravit váš soubor projektu, chcete-li změnit výchozí Cílová architektura nebo cílit na více než jedno rozhraní.

Publikování disketové jednotky vytvoří aplikaci, která automaticky zobrazí souhrn po dopředné nejnovější .NET Core opravy dostupné v systému, na kterém běží aplikace. Další informace o vázání verze v době kompilace, naleznete v tématu [vyberte verzi .NET Core používat](../versions/selection.md#framework-dependent-apps-roll-forward).

## <a name="framework-dependent-executable"></a>Spustitelný soubor závisí na architektuře

Pro .NET Core SDK 3.x rozhraní příkazového řádku, závisí na architektuře spustitelný soubor (FDE) výchozí režim pro základní `dotnet publish` příkazu. Není nutné k určení dalších parametrů jako cílových aktuálního operačního systému.

V tomto režimu se vytvoří spustitelný soubor hostitele specifické pro platformu pro hostování vaší aplikace pro různé platformy. Tento režim je podobný disketové jednotky, protože vyžaduje disketové jednotky hostitele ve formě `dotnet` příkazu. Hostitel spustitelného souboru se liší podle platformy a s názvem podobný `<PROJECT-FILE>.exe`. Můžete spustit tento spustitelný soubor přímo, bez volání `dotnet <PROJECT-FILE>.dll` což je stále přijatelné způsob, jak spustit aplikaci.

Vaše aplikace je nakonfigurovaná k cílení na konkrétní verzi .NET Core. Která je určená .NET Core runtime musí být na počítači, ve kterém chcete spustit vaši aplikaci. Například pokud vaše aplikace cílí na .NET Core 2.2, musí mít všechny počítače, které vaše aplikace běží na modulu runtime .NET Core 2.2 nainstalované. Jak je uvedeno v [publikování Základy](#publishing-basics) oddílu, můžete upravit váš soubor projektu, chcete-li změnit výchozí Cílová architektura nebo cílit na více než jedno rozhraní.

Publikování FDE vytvoří aplikaci, která automaticky zobrazí souhrn po dopředné nejnovější .NET Core opravy dostupné v systému, na kterém běží aplikace. Další informace o vázání verze v době kompilace, naleznete v tématu [vyberte verzi .NET Core používat](../versions/selection.md#framework-dependent-apps-roll-forward).

Je nutné (s výjimkou .NET Core 3.x, pokud cílíte na platformu aktuální) použijte následující přepínače s `dotnet publish` příkaz pro publikování FDE:

- `-r <RID>` Tento přepínač identifikátor (RID) používá k určení cílové platformy. Seznam identifikátorů modulů runtime, naleznete v tématu [identifikátor modulu Runtime (RID) katalogu](../rid-catalog.md).

- `--self-contained false` Tento přepínač říká .NET Core SDK k vytvoření spustitelného souboru jako FDE.

Vždy, když použijete `-r` přepínače, cesta ke složce výstupu se změní na: `./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/`

Pokud používáte [ukázkovou aplikaci](#sample-app)spuštěním `dotnet publish -f netcoreapp2.2 -r win10-x64 --self-contained false`. Tento příkaz vytvoří následující spustitelný soubor: `./bin/Debug/netcoreapp2.2/win10-x64/publish/apptest1.exe`

> [!NOTE]
> Můžete snížit celkovou velikost vašeho nasazení tím, že **invariantní režimu globalizace**. Tento režim je užitečný pro aplikace, které nejsou globální a které používají konvence formátování, konvence malých a velkých písmen a řetězec porovnání a řazení pořadí [invariantní jazyková verze](xref:System.Globalization.CultureInfo.InvariantCulture). Další informace o **invariantní režimu globalizace** a jak ho chcete povolit, najdete v článku [invariantní režimu globalizace rozhraní .NET Core](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md)

## <a name="self-contained-deployment"></a>Samostatná nasazení

Když publikujete samostatná nasazení (SCD), .NET Core SDK vytvoří spustitelný soubor pro konkrétní platformu. Publikování SCD zahrnuje všechny požadované soubory .NET Core ke spouštění vaší aplikace, ale neobsahuje [nativní závislosti .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md). Tyto závislosti musí být k dispozici v systému před spuštěním aplikace.

Publikování SCD vytvoří aplikaci, která není vpřed na nejnovější dostupné .NET Core opravu zabezpečení. Další informace o vázání verze v době kompilace, naleznete v tématu [vyberte verzi .NET Core používat](../versions/selection.md#self-contained-deployments-include-the-selected-runtime).

Je nutné použít následující přepínače s `dotnet publish` příkaz pro publikování SCD:

- `-r <RID>` Tento přepínač identifikátor (RID) používá k určení cílové platformy. Seznam identifikátorů modulů runtime, naleznete v tématu [identifikátor modulu Runtime (RID) katalogu](../rid-catalog.md).

- `--self-contained true` Tento přepínač říká .NET Core SDK k vytvoření spustitelného souboru jako SCD.

> [!NOTE]
> Můžete snížit celkovou velikost vašeho nasazení tím, že **invariantní režimu globalizace**. Tento režim je užitečný pro aplikace, které nejsou globální a které používají konvence formátování, konvence malých a velkých písmen a řetězec porovnání a řazení pořadí [invariantní jazyková verze](xref:System.Globalization.CultureInfo.InvariantCulture). Další informace o **invariantní režimu globalizace** a jak ho chcete povolit, najdete v článku [invariantní režimu globalizace rozhraní .NET Core](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md)


## <a name="see-also"></a>Viz také:

- [Přehled nasazení aplikací .NET core](index.md)
- [.NET core Runtime identifikátor (RID) katalogu](../rid-catalog.md)
