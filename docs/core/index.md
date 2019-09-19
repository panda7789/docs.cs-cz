---
title: Průvodce platformou .NET Core
description: .NET Core je modulární a vysoce výkonná implementace .NET pro vytváření aplikací pro Windows, Linux a Mac. Seznamte se s .NET Core, abyste mohli začít.
author: richlander
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: a6112851a3d9b46f02c26313e6537170786df10b
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117074"
---
# <a name="net-core-guide"></a>Průvodce platformou .NET Core

[.NET Core](about.md) je [Open Source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT)vývojová platforma pro obecné účely udržovaná Microsoftem a komunitou .NET na [GitHubu](https://github.com/dotnet/core). Je to pro různé platformy (podporující Windows, macOS a Linux) a dá se použít k sestavování aplikací pro zařízení, Cloud a IoT.

Další informace o .NET Core, včetně jeho vlastností, podporovaných jazycích a architektur a klíčových rozhraní API, najdete v tématu [o .NET Core](about.md) .

V [kurzech pro .NET Core](tutorials/index.md) se dozvíte, jak vytvořit jednoduchou aplikaci .NET Core. Vaše první aplikace je možné začít používat jenom pár minut. Pokud chcete v prohlížeči vyzkoušet .NET Core, podívejte se na [čísla v C# ](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online kurzu.

## <a name="download-net-core-22"></a>Stáhnout .NET Core 2,2

Stáhněte si [sadu .NET core 2,2 SDK](https://dotnet.microsoft.com/download) a vyzkoušejte .NET Core na počítači s Windows, MacOS nebo Linux. Pokud upřednostňujete použití kontejnerů Docker, přejděte na [dotnet/Core](https://hub.docker.com/_/microsoft-dotnet-core/) .

Pokud hledáte jinou verzi rozhraní .NET Core, jsou všechny verze .NET Core k dispozici na webu [soubory ke stažení pro .NET](https://dotnet.microsoft.com/download/dotnet-core) Core.

## <a name="net-core-22"></a>.NET Core 2,2

Nejnovější verze je [.NET Core 2,2](whats-new/dotnet-core-2-2.md). Mezi nové funkce patří: nasazení závislá na rozhraní, spouštěcí háky, ověřování AAD s Azure SQL a podpora pro Windows ARM32.

## <a name="create-your-first-application"></a>Vytvoření první aplikace

Po instalaci .NET Core SDK otevřete příkazový řádek. Zadáním následujících `dotnet` příkazů vytvořte a spusťte C# aplikaci.

```dotnetcli
dotnet new console
dotnet run
```

Měl by se zobrazit následující výstup:

```output
Hello World!
```

## <a name="support"></a>Podpora

.NET Core [podporuje Microsoft](https://dotnet.microsoft.com/platform/support/policy), v systémech Windows, MacOS a Linux. Je aktualizovaná z hlediska zabezpečení a kvality několikrát ročně, obvykle měsíčně.

Binární distribuce .NET Core se sestavují a testují na serverech spravovaných Microsoftem v Azure a podporují se stejně jako u jakéhokoli produktu společnosti Microsoft.

[Red Hat podporuje .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL). Red Hat sestaví .NET Core ze zdroje a zpřístupňuje je v [kolekcích softwaru Red Hat](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat a Microsoft spolupracují, aby se zajistilo, že .NET Core dobře funguje na RHEL.
