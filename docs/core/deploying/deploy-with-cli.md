---
title: Publikování aplikací pomocí rozhraní CLI jádra .NET
description: Naučte se publikovat aplikaci .NET Core pomocí příkazů rozhraní PŘÍKAZU .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/12/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: f4c2a4ccf551c53e4aa4e125cb5720d6f1cc9601
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399068"
---
# <a name="publish-net-core-apps-with-the-net-core-cli"></a>Publikování aplikací .NET Core pomocí rozhraní CLI jádra ROZHRANÍ .NET

Tento článek ukazuje, jak můžete publikovat aplikaci .NET Core z příkazového řádku. .NET Core poskytuje tři způsoby publikování aplikací. Nasazení závislé na rozhraní vytváří soubor DLL napříč platformami, který používá místně nainstalovaný runtime .NET Core. Spustitelný soubor závislý na rozhraní vytváří spustitelný soubor specifický pro platformu, který používá místně nainstalovaný modul runtime .NET Core. Samostatný spustitelný soubor vytvoří spustitelný soubor specifický pro platformu a obsahuje místní kopii modulu runtime jádra .NET.

Přehled těchto režimů publikování naleznete v tématu [.NET Core Application Deployment](index.md).

Hledáte nějakou rychlou pomoc při používání CLI? V následující tabulce jsou uvedeny některé příklady publikování aplikace. Cílovou architekturu můžete `-f <TFM>` určit pomocí parametru nebo úpravou souboru projektu. Další informace naleznete v [tématu Základy publikování](#publishing-basics).

| Režim publikování | Verze SDK | Příkaz |
| ------------ | ----------- | ------- |
| Nasazení závislé na rámci | 2.x | `dotnet publish -c Release` |
| Spustitelný soubor závislý na rámci | 2,2 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3.0* | `dotnet publish -c Release` |
| Samostatné nasazení      | 2.1 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 2,2 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained true` |

\*Při použití sady SDK verze 3.0 je spustitelný soubor závislý `dotnet publish` na rozhraní výchozím režimem publikování při spuštění základního příkazu. To platí pouze v případě, že projekt cílí na **rozhraní .NET Core 2.1** nebo **.NET Core 3.0**.

## <a name="publishing-basics"></a>Základy publikování

Nastavení `<TargetFramework>` souboru projektu určuje výchozí cílové rozhraní při publikování aplikace. Můžete změnit cílové rozhraní na libovolný platný [zástupný název cílového rozhraní (TFM).](../../standard/frameworks.md) Například pokud váš `<TargetFramework>netcoreapp2.2</TargetFramework>`projekt používá , je vytvořen binární soubor, který cíle .NET Core 2.2. TfM zadaná v tomto nastavení je [`dotnet publish`](../tools/dotnet-publish.md) výchozím cílem používaným příkazem.

Pokud chcete cílit na více než jednu architekturu, `<TargetFrameworks>` můžete nastavit nastavení na více než jednu hodnotu TFM oddělenou středníkem. Můžete publikovat jeden z rámců `dotnet publish -f <TFM>` pomocí příkazu. Například pokud máte `<TargetFrameworks>netcoreapp2.1;netcoreapp2.2</TargetFrameworks>` a `dotnet publish -f netcoreapp2.1`spustit , je vytvořen binární soubor, který se zaměřuje na .NET Core 2.1.

Pokud není nastaveno jinak, [`dotnet publish`](../tools/dotnet-publish.md) je `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/`výstupní adresář příkazu . Výchozí režim **BUILD-CONFIGURATION** je **Ladění,** `-c` pokud se nezmění s parametrem. Například `dotnet publish -c Release -f netcoreapp2.1` publikuje `myfolder/bin/Release/netcoreapp2.1/publish/`na .

Pokud používáte .NET Core SDK 3.0 nebo novější, výchozí režim publikování pro aplikace, které cílí na .NET Core verze 2.1, 2.2, 3.0 nebo novější verze, je spustitelný soubor závislý na rámci.

Pokud používáte .NET Core SDK 2.1, výchozí režim publikování pro aplikace, které cílí na .NET Core verze 2.1 a 2.2 je nasazení závislé na rámci.

### <a name="native-dependencies"></a>Nativní závislosti

Pokud má vaše aplikace nativní závislosti, nemusí běžet v jiném operačním systému. Pokud například vaše aplikace používá nativní rozhraní API systému Windows, nebude fungovat na macOS nebo Linuxu. Budete muset poskytnout kód specifický pro platformu a zkompilovat spustitelný soubor pro každou platformu.

Zvažte také, pokud knihovna, na kterou odkazujete, má nativní závislost, vaše aplikace nemusí běžet na všech platformách. Je však možné, že balíček NuGet, na který odkazujete, obsahuje verze specifické pro platformu, které pro vás zpracovávají požadované nativní závislosti.

Při distribuci aplikace s nativní závislosti, budete `dotnet publish -r <RID>` muset použít přepínač k určení cílové platformy, kterou chcete publikovat. Seznam identifikátorů modulu runtime naleznete v [katalogu identifikátorů modulu runtime (RID).](../rid-catalog.md)

Další informace o binárních souborech specifických pro platformu jsou popsány v [oddílech spustitelného](#framework-dependent-executable) a [samostatného nasazení](#self-contained-deployment) závislé na rozhraní Framework.

## <a name="sample-app"></a>Ukázková aplikace

Příkazy pro publikování můžete prozkoumat pomocí následující aplikace. Aplikace je vytvořena spuštěním následujících příkazů ve vašem terminálu:

```dotnetcli
mkdir apptest1
cd apptest1
dotnet new console
dotnet add package Figgle
```

Soubor `Program.cs` `Program.vb` nebo, který je generován šablonou konzoly, je třeba změnit na následující:

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

Při spuštění aplikace[`dotnet run`](../tools/dotnet-run.md)( ) se zobrazí následující výstup:

```terminal
  _   _      _ _         __        __         _     _ _
 | | | | ___| | | ___    \ \      / /__  _ __| | __| | |
 | |_| |/ _ \ | |/ _ \    \ \ /\ / / _ \| '__| |/ _` | |
 |  _  |  __/ | | (_) |    \ V  V / (_) | |  | | (_| |_|
 |_| |_|\___|_|_|\___( )    \_/\_/ \___/|_|  |_|\__,_(_)
                     |/
```

## <a name="framework-dependent-deployment"></a>Nasazení závislé na rámci

Pro rozhraní PŘÍKAZOVÉHO NASTAVENÍ .NET Core SDK 2.x je nasazení závislé na `dotnet publish` rámci (FDD) výchozím režimem pro základní příkaz.

Když publikujete aplikaci jako FDD, vytvoří `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` se ve složce `<PROJECT-NAME>.dll` soubor. Chcete-li aplikaci spustit, přejděte `dotnet <PROJECT-NAME>.dll` do výstupní složky a použijte příkaz.

Vaše aplikace je nakonfigurovaná tak, aby cílila na konkrétní verzi jádra .NET. Tento cílový běh .NET Core je nutné být na libovolném počítači, kde vaše aplikace běží. Pokud například vaše aplikace cílí na rozhraní .NET Core 2.2, musí mít mít nainstalovaný runtime .NET Core 2.2. Jak je uvedeno v části [Základy publikování,](#publishing-basics) můžete upravit soubor projektu a změnit výchozí cílovou architekturu nebo cílit na více než jednu architekturu.

Publikování FDD vytvoří aplikaci, která automaticky předává vpřed na nejnovější opravu zabezpečení .NET Core, která je k dispozici v systému, ve které je aplikace spuštěna. Další informace o vazbě verze v době kompilace naleznete v [tématu Vyberte verzi .NET Core, která se má použít](../versions/selection.md#framework-dependent-apps-roll-forward).

## <a name="framework-dependent-executable"></a>Spustitelný soubor závislý na rámci

Pro rozhraní PŘÍKAZOVÉHO NASTAVENÍ .NET Core SDK 3.x je spustitelný soubor fde závislý na rozhraní framework výchozím režimem. `dotnet publish` Není nutné zadávat žádné další parametry, pokud chcete cílit na aktuální operační systém.

V tomto režimu je vytvořen spustitelný hostitel specifický pro platformu, který bude hostovat vaši aplikaci pro různé platformy. Tento režim je podobný FDD, protože FDD vyžaduje `dotnet` hostitele ve formě příkazu. Název souboru spustitelného souboru hostitele se `<PROJECT-FILE>.exe`liší podle platformy a je pojmenován podobně jako . Tento spustitelný soubor můžete spustit `dotnet <PROJECT-FILE>.dll`přímo namísto volání , což je stále přijatelný způsob spuštění aplikace.

Vaše aplikace je nakonfigurovaná tak, aby cílila na konkrétní verzi jádra .NET. Tento cílový běh .NET Core je nutné být na libovolném počítači, kde vaše aplikace běží. Pokud například vaše aplikace cílí na rozhraní .NET Core 2.2, musí mít mít nainstalovaný runtime .NET Core 2.2. Jak je uvedeno v části [Základy publikování,](#publishing-basics) můžete upravit soubor projektu a změnit výchozí cílovou architekturu nebo cílit na více než jednu architekturu.

Publikování FDE vytvoří aplikaci, která automaticky předává vpřed na nejnovější opravu zabezpečení .NET Core, která je k dispozici v systému, ve které je aplikace spuštěna. Další informace o vazbě verze v době kompilace naleznete v [tématu Vyberte verzi .NET Core, která se má použít](../versions/selection.md#framework-dependent-apps-roll-forward).

Pro rozhraní .NET Core 2.2 a starší je `dotnet publish` nutné k publikování fde použít následující přepínače s příkazem:

- `-r <RID>`Tento přepínač používá identifikátor (RID) k určení cílové platformy. Seznam identifikátorů modulu runtime naleznete v [katalogu identifikátorů modulu runtime (RID).](../rid-catalog.md)

- `--self-contained false`Tento přepínač sděluje spoje jádra .NET k vytvoření spustitelného souboru jako fde.

Při každém `-r` použití přepínače se cesta k výstupní složce změní na:`./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/`

Pokud používáte [ukázkovou aplikaci](#sample-app), spusťte aplikaci `dotnet publish -f netcoreapp2.2 -r win10-x64 --self-contained false`. Tento příkaz vytvoří následující spustitelný soubor:`./bin/Debug/netcoreapp2.2/win10-x64/publish/apptest1.exe`

> [!NOTE]
> Celkovou velikost nasazení můžete zmenšit povolením **invariantního režimu globalizace**. Tento režim je užitečný pro aplikace, které nejsou globálně vědomi a které můžete použít konvence formátování, konvencí písmen a porovnání řetězců a pořadí řazení [invariantní jazykové verze](xref:System.Globalization.CultureInfo.InvariantCulture). Další informace o **invariantním režimu globalizace** a o jeho povolení naleznete [v tématu .NET Core Globalization Invariant Mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).

## <a name="self-contained-deployment"></a>Samostatné nasazení

Při publikování samostatné nasazení (SCD), .NET Core SDK vytvoří spustitelný soubor specifický pro platformu. Publikování scd obsahuje všechny požadované soubory .NET Core pro spuštění aplikace, ale neobsahuje [nativní závislosti .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md). Tyto závislosti musí být k dispozici v systému před spuštěním aplikace.

Publikování scd vytvoří aplikaci, která není převést dopředu na nejnovější dostupné .NET Základní oprava zabezpečení. Další informace o vazbě verze v době kompilace naleznete v [tématu Vyberte verzi .NET Core, která se má použít](../versions/selection.md#self-contained-deployments-include-the-selected-runtime).

K publikování scd je `dotnet publish` nutné pomocí následujících přepínačů pomocí příkazu použít následující přepínače:

- `-r <RID>`Tento přepínač používá identifikátor (RID) k určení cílové platformy. Seznam identifikátorů modulu runtime naleznete v [katalogu identifikátorů modulu runtime (RID).](../rid-catalog.md)

- `--self-contained true`Tento přepínač sděluje spoře .NET Core SDK k vytvoření spustitelného souboru jako scd.

> [!NOTE]
> Celkovou velikost nasazení můžete zmenšit povolením **invariantního režimu globalizace**. Tento režim je užitečný pro aplikace, které nejsou globálně vědomi a které můžete použít konvence formátování, konvencí písmen a porovnání řetězců a pořadí řazení [invariantní jazykové verze](xref:System.Globalization.CultureInfo.InvariantCulture). Další informace o **invariantním režimu globalizace** a o jeho povolení naleznete [v tématu .NET Core Globalization Invariant Mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).

## <a name="see-also"></a>Viz také

- [Přehled nasazení základní aplikace .NET](index.md)
- [Katalog IDentifier (RID) modulu .NET Core Runtime](../rid-catalog.md)
