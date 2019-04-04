---
title: Průvodce platformou .NET Core
description: .NET core je modulární a vysoce výkonnou implementace .NET pro vytváření aplikací pro Windows, Linux a Mac. Další informace o .NET Core, abyste mohli začít.
author: richlander
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 79a0c09074159160dd01b0c7970612f7058cc3fc
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920620"
---
# <a name="net-core-guide"></a>Průvodce platformou .NET Core

[.NET core](about.md) je [open source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), pro obecné účely Vývojová platforma udržuje od Microsoftu a komunity .NET na [Githubu](https://github.com/dotnet/core). Je multiplatformní (podporují Windows, macOS a Linux) a je možné vytvářet zařízení, cloud a aplikace IoT.

Zobrazit [o .NET Core](about.md) získat další informace o .NET Core, včetně jeho vlastnosti, podporované jazyky a platformy a klíč rozhraní API.

Podívejte se na [kurzy k .NET Core](tutorials/index.md) se naučíte vytvořit jednoduchou aplikaci .NET Core. Trvá jenom pár minut a zprovoznění svoji první aplikaci. Pokud chcete vyzkoušet .NET Core v prohlížeči, podívejte se na [čísla ve C# ](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online kurz ke službě.

## <a name="download-net-core-22"></a>Stáhnout .NET Core 2.2

Stáhněte si [.NET Core 2.2 SDK](https://www.microsoft.com/net/download) vyzkoušet .NET Core na počítači Windows, macOS nebo Linux. Navštivte [dotnet/jádro](https://hub.docker.com/_/microsoft-dotnet-core/) Pokud byste radši chtěli použít kontejnery Dockeru.

Všechny verze .NET Core najdete na adrese [soubory ke stažení rozhraní .NET Core](https://www.microsoft.com/net/download/archives) Pokud potřebujete jinou verzi .NET Core.

## <a name="net-core-22"></a>.NET Core 2.2

Nejnovější verze je [.NET Core 2.2](whats-new/dotnet-core-2-2.md). Mezi nové funkce patří: závisí na architektuře nasazení, spuštění háky, ověřování AAD s Azure SQL a podpora Windows ARM32.

## <a name="create-your-first-application"></a>Vytvoření první aplikace

Po instalaci rozhraní .NET Core SDK, otevřete příkazový řádek. Zadejte následující příkaz `dotnet` příkazy k vytvoření a spuštění aplikace v jazyce C#.

```console
dotnet new console
dotnet run
```

Byste měli vidět následující výstup:

```console
Hello World!
```

## <a name="support"></a>Podpora

.NET core je [společnost Microsoft podporuje](https://www.microsoft.com/net/support/policy), ve Windows, macOS a Linuxu. To je aktualizována o zabezpečení a kvalitní několikrát za rok, obvykle měsíčně.

Binární distribuce .NET core jsou integrované a otestovali na Microsoft udržuje serverů v Azure a podporované stejně jako libovolný produkt společnosti Microsoft.

[Red Hat podporuje .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL). Red Hat sestavení .NET Core ze zdroje a zpřístupňuje je v [kolekce softwaru Red Hat](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat a Microsoft spolupracují na Ujistěte se, že v RHEL dobře funguje .NET Core.
