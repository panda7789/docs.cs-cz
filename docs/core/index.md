---
title: Průvodce platformou .NET Core
description: .NET Core je modulární a vysoce výkonná implementace .NET pro vytváření aplikací pro Windows, Linux a Mac. Seznamte se s .NET Core, abyste mohli začít.
author: richlander
ms.date: 09/23/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 95f18ca09852ce139a4b99ed7aef4802d4883e13
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216219"
---
# <a name="net-core-guide"></a>Průvodce platformou .NET Core

[.NET Core](about.md) je [Open Source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT)vývojová platforma pro obecné účely udržovaná Microsoftem a komunitou .NET na [GitHubu](https://github.com/dotnet/core). Je to pro různé platformy (podporující Windows, macOS a Linux) a dá se použít k sestavování aplikací pro zařízení, Cloud a IoT.

Další informace o .NET Core, včetně jeho vlastností, podporovaných jazycích a architektur a klíčových rozhraní API, najdete v tématu [o .NET Core](about.md) .

V [kurzech pro .NET Core](tutorials/index.md) se dozvíte, jak vytvořit jednoduchou aplikaci .NET Core. Vaše první aplikace je možné začít používat jenom pár minut. Pokud chcete v prohlížeči vyzkoušet .NET Core, podívejte se na [čísla v C# ](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online kurzu.

## <a name="download-net-core"></a>Stáhnout .NET Core

Stáhněte si [.NET Core SDK](https://www.microsoft.com/net/download) a vyzkoušejte .NET Core na počítači s Windows, MacOS nebo Linux. A pokud upřednostňujete použití kontejnerů Docker, navštivte web [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).

Pokud hledáte jinou verzi rozhraní .NET Core, jsou všechny verze .NET Core k dispozici na webu [soubory ke stažení pro .NET](https://dotnet.microsoft.com/download/dotnet-core) Core.

## <a name="net-core-30"></a>.NET Core 3.0

Nejnovější verze je .NET Core 3,0. Mezi nové funkce patří podpora stolních počítačů s Windows pomocí Windows Presentation Foundation (WPF) a C# model Windows Forms, úplného vytváření zásobníku pro web s Blazor, nová vylepšení pro signál a službu C# Azure Signal Service C# , nové funkce jazyka s 8 a mnoho dalšího. Úplný seznam nových funkcí v rozhraní .NET Core 3,0 najdete v tématu [co je nového v rozhraní .NET core 3,0](./whats-new/dotnet-core-3-0.md).

## <a name="create-your-first-application"></a>Vytvoření první aplikace

Po instalaci .NET Core SDK otevřete příkazový řádek. Zadáním následujících `dotnet` příkazů vytvořte a spusťte C# aplikaci:

```dotnetcli
dotnet new console
dotnet run
```

Měl by se zobrazit následující výstup:

```output
Hello World!
```

## <a name="support"></a>Podpora

.NET Core [podporuje Microsoft](https://dotnet.microsoft.com/platform/support/policy), ve Windows, MacOS a Linux. Je aktualizovaná z hlediska zabezpečení a kvality několikrát ročně, obvykle měsíčně.

Binární distribuce .NET Core se sestavují a testují na serverech spravovaných Microsoftem v Azure a podporují se stejně jako u jakéhokoli produktu společnosti Microsoft.

[Red Hat podporuje .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL). Red Hat sestaví .NET Core ze zdroje a zpřístupňuje je v [kolekcích softwaru Red Hat](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat a Microsoft spolupracují, aby se zajistilo, že .NET Core dobře funguje na RHEL.
