---
title: Publikování aplikací pomocí .NET Core CLI
description: Naučte se publikovat aplikaci .NET Core pomocí příkazů .NET Core CLI.
author: adegeo
ms.author: adegeo
ms.date: 12/12/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: a592b397d1ffee5b224638a8d17ce6fa9e44eea2
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325023"
---
# <a name="publish-net-core-apps-with-the-net-core-cli"></a>Publikování aplikací .NET Core pomocí .NET Core CLI

Tento článek ukazuje, jak můžete publikovat aplikaci .NET Core z příkazového řádku. .NET Core nabízí tři způsoby, jak publikovat aplikace. Nasazení závislé na rozhraní vytvoří soubor. dll pro více platforem, který používá místně instalovaný modul runtime .NET Core. Spustitelný soubor závislý na rozhraní vytvoří spustitelný soubor specifický pro platformu, který používá místně instalovaný modul runtime .NET Core. Samostatně obsažený spustitelný soubor vytvoří spustitelný soubor specifický pro platformu a obsahuje místní kopii modulu runtime .NET Core.

Přehled těchto režimů publikování najdete v tématu [nasazení aplikace .NET Core](index.md).

Hledáte nějakou rychlou nápovědu k používání rozhraní příkazového řádku? V následující tabulce jsou uvedeny některé příklady publikování aplikace. Můžete zadat cílové rozhraní s `-f <TFM>` parametrem nebo úpravou souboru projektu. Další informace najdete v tématu [základy publikování](#publishing-basics).

| Režim publikování | Verze SDK | Příkaz |
| ------------ | ----------- | ------- |
| Nasazení závislé na rozhraní | 2.x | `dotnet publish -c Release` |
| Spustitelný soubor závislý na rozhraní | 2,2 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3,0 * | `dotnet publish -c Release` |
| Samostatně zahrnuté nasazení      | 2.1 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 2,2 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained true` |

\*Při použití sady SDK verze 3,0 je spustitelný soubor závislý na architektuře výchozím režimem publikování při spuštění `dotnet publish` příkazu Basic. To platí pouze v případě, že projekt cílí na **rozhraní .NET core 2,1** nebo **.NET Core 3,0**.

## <a name="publishing-basics"></a>Základy publikování

`<TargetFramework>`Nastavení soubor projektu určuje výchozí cílové rozhraní při publikování aplikace. Můžete změnit cílovou architekturu na libovolný platný [cílový moniker rozhraní (TFM)](../../standard/frameworks.md). Například pokud váš projekt používá `<TargetFramework>netcoreapp2.2</TargetFramework>` , je vytvořen binární soubor, který cílí na .NET Core 2,2. TFM zadané v tomto nastavení je výchozí cíl používaný [`dotnet publish`](../tools/dotnet-publish.md) příkazem.

Pokud chcete cílit na více než jedno rozhraní, můžete nastavit `<TargetFrameworks>` nastavení na více než jednu hodnotu TFM oddělenou středníkem. Můžete publikovat jednu z architektur pomocí `dotnet publish -f <TFM>` příkazu. Například pokud máte `<TargetFrameworks>netcoreapp2.1;netcoreapp2.2</TargetFrameworks>` a spustíte, vytvoří se `dotnet publish -f netcoreapp2.1` binární soubor, který cílí na .net Core 2,1.

Není-li jinak nastaveno, je výstupní adresář [`dotnet publish`](../tools/dotnet-publish.md) příkazu `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` . Výchozí režim **konfigurace sestavení** je **ladění** , pokud se nezmění s `-c` parametrem. Například `dotnet publish -c Release -f netcoreapp2.1` publikování na `myfolder/bin/Release/netcoreapp2.1/publish/` .

Použijete-li .NET Core SDK 3,0 nebo novější, je výchozím režimem publikování pro aplikace, které jsou určeny pro .NET Core verze 2,1, 2,2, 3,0 nebo pozdější verze, spustitelný soubor závislý na rozhraní.

Pokud používáte .NET Core SDK 2,1, výchozím režimem publikování pro aplikace, které cílí na .NET Core verze 2,1 a 2,2, je nasazení závislé na rozhraní.

### <a name="native-dependencies"></a>Nativní závislosti

Pokud má vaše aplikace nativní závislosti, nemusí běžet v jiném operačním systému. Pokud vaše aplikace například používá nativní rozhraní API systému Windows, nebude spuštěna na macOS nebo Linux. Je nutné zadat kód specifický pro platformu a zkompilovat spustitelný soubor pro každou platformu.

V případě, že knihovna, na kterou jste odkazovali, má nativní závislost, vaše aplikace nemusí běžet na všech platformách. Je však možné, že balíček NuGet, na který odkazujete, obsahuje verze specifické pro platformu, které pro vás pořídí požadované nativní závislosti.

Při distribuci aplikace s nativními závislostmi možná budete muset použít `dotnet publish -r <RID>` přepínač a zadat cílovou platformu, pro kterou chcete publikovat. Seznam identifikátorů modulu runtime naleznete v [katalogu identifikátorů modulu runtime (RID)](../rid-catalog.md).

Další informace o binárních souborech specifických pro konkrétní platformu jsou pokryté [spustitelnými soubory závislými na rozhraní](#framework-dependent-executable) a oddíly [pro nasazení samostatného nasazení](#self-contained-deployment) .

## <a name="sample-app"></a>Ukázková aplikace

Pomocí následující aplikace můžete prozkoumat příkazy pro publikování. Aplikaci vytvoříte spuštěním následujících příkazů v terminálu:

```dotnetcli
mkdir apptest1
cd apptest1
dotnet new console
dotnet add package Figgle
```

`Program.cs`Soubor nebo `Program.vb` , který je generován šablonou konzoly, je třeba změnit na následující:

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
Module Program
    Sub Main(args As String())
        Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"))
    End Sub
End Module
```

Při spuštění aplikace () se [`dotnet run`](../tools/dotnet-run.md) zobrazí následující výstup:

```terminal
  _   _      _ _         __        __         _     _ _
 | | | | ___| | | ___    \ \      / /__  _ __| | __| | |
 | |_| |/ _ \ | |/ _ \    \ \ /\ / / _ \| '__| |/ _` | |
 |  _  |  __/ | | (_) |    \ V  V / (_) | |  | | (_| |_|
 |_| |_|\___|_|_|\___( )    \_/\_/ \___/|_|  |_|\__,_(_)
                     |/
```

## <a name="framework-dependent-deployment"></a>Nasazení závislé na rozhraní

Pro .NET Core SDK 2. x CLI, nasazení závislé na rozhraní (FDD) je výchozí režim pro základní `dotnet publish` příkaz.

Při publikování aplikace jako FDD se `<PROJECT-NAME>.dll` ve složce vytvoří soubor `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` . Chcete-li spustit aplikaci, přejděte do výstupní složky a použijte `dotnet <PROJECT-NAME>.dll` příkaz.

Vaše aplikace je nakonfigurovaná tak, aby byla cílena na konkrétní verzi .NET Core. Cílový modul runtime .NET Core musí být na jakémkoli počítači, na kterém je vaše aplikace spuštěná. Například pokud vaše aplikace cílí na .NET Core 2,2, musí mít každý počítač, na kterém je aplikace spuštěná, nainstalovaný modul .NET Core 2,2 Runtime. Jak je uvedeno v části [základy publikování](#publishing-basics) , můžete upravit soubor projektu pro změnu výchozí cílové architektury nebo pro cílení na více než jedno rozhraní.

Publikováním FDD se vytvoří aplikace, která se automaticky přenese do nejnovější opravy zabezpečení .NET Core, která je dostupná v systému, ve kterém je spuštěná aplikace. Další informace o vazbách verzí v době kompilace naleznete v tématu [Vyberte verzi rozhraní .NET Core, která se má použít](../versions/selection.md#framework-dependent-apps-roll-forward).

## <a name="framework-dependent-executable"></a>Spustitelný soubor závislý na rozhraní

Pro .NET Core SDK 3. x CLI, spustitelný soubor závislý na rozhraní (FDE) je výchozím režimem pro základní `dotnet publish` příkaz. Nemusíte zadávat žádné další parametry, pokud chcete cílit na aktuální operační systém.

V tomto režimu se pro hostování aplikace pro různé platformy vytvoří spustitelný hostitel specifický pro platformu. Tento režim je podobný jako FDD, protože FDD vyžaduje hostitele ve formě `dotnet` příkazu. Název spustitelného souboru hostitele se liší podle platformy a má název podobný `<PROJECT-FILE>.exe` . Tento spustitelný soubor můžete spustit přímo místo volání `dotnet <PROJECT-FILE>.dll` , což je stále přijatelný způsob, jak aplikaci spustit.

Vaše aplikace je nakonfigurovaná tak, aby byla cílena na konkrétní verzi .NET Core. Cílový modul runtime .NET Core musí být na jakémkoli počítači, na kterém je vaše aplikace spuštěná. Například pokud vaše aplikace cílí na .NET Core 2,2, musí mít každý počítač, na kterém je aplikace spuštěná, nainstalovaný modul .NET Core 2,2 Runtime. Jak je uvedeno v části [základy publikování](#publishing-basics) , můžete upravit soubor projektu pro změnu výchozí cílové architektury nebo pro cílení na více než jedno rozhraní.

Publikováním FDE se vytvoří aplikace, která se automaticky přenese na nejnovější aktualizaci zabezpečení .NET Core dostupnou v systému, ve kterém je aplikace spuštěná. Další informace o vazbách verzí v době kompilace naleznete v tématu [Vyberte verzi rozhraní .NET Core, která se má použít](../versions/selection.md#framework-dependent-apps-roll-forward).

U .NET Core 2,2 a starší verze je potřeba k publikování FDE použít následující přepínače s `dotnet publish` příkazem:

- `-r <RID>`Tento přepínač pomocí identifikátoru (RID) určí cílovou platformu. Seznam identifikátorů modulu runtime naleznete v [katalogu identifikátorů modulu runtime (RID)](../rid-catalog.md).

- `--self-contained false`Tento přepínač oznamuje .NET Core SDK, aby se jako FDE vytvořil spustitelný soubor.

Vždy, když použijete `-r` přepínač, cesta výstupní složky se změní na:`./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/`

Pokud používáte [ukázkovou aplikaci](#sample-app), spusťte příkaz `dotnet publish -f netcoreapp2.2 -r win10-x64 --self-contained false` . Tento příkaz vytvoří následující spustitelný soubor:`./bin/Debug/netcoreapp2.2/win10-x64/publish/apptest1.exe`

> [!NOTE]
> Celkovou velikost nasazení můžete snížit povolením **režimu invariantování globalizace**. Tento režim je vhodný pro aplikace, které nejsou globálně závislé a které mohou použít konvence formátování, konvence velikosti písmen a pořadí řazení [neutrální jazykové verze](xref:System.Globalization.CultureInfo.InvariantCulture). Další informace o **invariantní režimu globalizace** a o tom, jak ho povolit, najdete v tématu [Nevariantní režim globalizace .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).

## <a name="self-contained-deployment"></a>Samostatně zahrnuté nasazení

Při publikování samostatného nasazení (SCD) vytvoří .NET Core SDK spustitelný soubor specifický pro platformu. Publikování SCD zahrnuje všechny požadované soubory .NET Core ke spuštění vaší aplikace, ale nezahrnuje [nativní závislosti rozhraní .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md). Tyto závislosti musí být v systému před spuštěním aplikace přítomny.

Publikování SCD vytvoří aplikaci, která se nevrátí k nejnovější dostupné opravě zabezpečení .NET Core. Další informace o vazbách verzí v době kompilace naleznete v tématu [Vyberte verzi rozhraní .NET Core, která se má použít](../versions/selection.md#self-contained-deployments-include-the-selected-runtime).

K publikování SCD je nutné použít následující přepínače s `dotnet publish` příkazem:

- `-r <RID>`Tento přepínač pomocí identifikátoru (RID) určí cílovou platformu. Seznam identifikátorů modulu runtime naleznete v [katalogu identifikátorů modulu runtime (RID)](../rid-catalog.md).

- `--self-contained true`Tento přepínač informuje .NET Core SDK a vytvoří spustitelný soubor jako SCD.

> [!NOTE]
> Celkovou velikost nasazení můžete snížit povolením **režimu invariantování globalizace**. Tento režim je vhodný pro aplikace, které nejsou globálně závislé a které mohou použít konvence formátování, konvence velikosti písmen a pořadí řazení [neutrální jazykové verze](xref:System.Globalization.CultureInfo.InvariantCulture). Další informace o **invariantní režimu globalizace** a o tom, jak ho povolit, najdete v tématu [Nevariantní režim globalizace .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).

## <a name="see-also"></a>Viz také

- [Přehled nasazení aplikace .NET Core](index.md)
- [Katalog identifikátorů runtime .NET Core (RID)](../rid-catalog.md)
