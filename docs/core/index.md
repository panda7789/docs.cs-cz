---
title: Průvodce platformou .NET Core
description: .NET core je modulární a vysoce výkonnou implementace .NET pro vytváření aplikací pro Windows, Linux a Mac. Další informace o .NET Core, abyste mohli začít.
author: richlander
ms.author: mairaw
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 448edabf624f04311695e8b8c224f653b9939966
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199458"
---
# <a name="net-core-guide"></a>Průvodce platformou .NET Core

[.NET core](about.md) je [open source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), pro obecné účely Vývojová platforma udržuje od Microsoftu a komunity .NET na [Githubu](https://github.com/dotnet/core). Je multiplatformní (podporují Windows, macOS a Linux) a je možné vytvářet zařízení, cloud a aplikace IoT.

Zobrazit [o .NET Core](about.md) získat další informace o .NET Core, včetně jeho vlastnosti, podporované jazyky a platformy a klíč rozhraní API.

Podívejte se na [kurzy k .NET Core](tutorials/index.md) se naučíte vytvořit jednoduchou aplikaci .NET Core. Trvá jenom pár minut a zprovoznění svoji první aplikaci. Pokud chcete vyzkoušet .NET Core v prohlížeči, podívejte se na [čísla ve C# ](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online kurz ke službě.

## <a name="download-net-core-21"></a>Stáhnout .NET Core 2.1

Stáhněte si [sady SDK .NET Core 2.1](https://www.microsoft.com/net/download) vyzkoušet .NET Core na počítači Windows, macOS nebo Linux. Navštivte [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) Pokud byste radši chtěli použít kontejnery Dockeru.

Všechny verze .NET Core najdete na adrese [soubory ke stažení rozhraní .NET Core](https://www.microsoft.com/net/download/archives) Pokud potřebujete jinou verzi .NET Core.

## <a name="net-core-21"></a>.NET core 2.1

Nejnovější verze je [.NET Core 2.1](whats-new/dotnet-core-2-1.md). Mezi nové funkce patří: globální nástroje, výkonné rozhraní API (například <xref:System.Span%601?displayProperty=nameWithType>), vrstvené kompilace JIT [sestavení](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) a [vylepšení výkonu modulu runtime](https://blogs.msdn.microsoft.com/dotnet/2018/04/18/performance-improvements-in-net-core-2-1/)a podpora pro Alpine a ARM32.

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
