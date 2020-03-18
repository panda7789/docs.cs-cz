---
title: Průvodce platformou .NET Core
description: .NET Core je modulární, vysoce výkonná implementace rozhraní .NET pro vytváření aplikací pro Windows, Linux a macOS. Další informace o .NET Core pro started a) začínáme.
author: richlander
ms.date: 12/04/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 3db98d21a7cdc80d8a98b23782a81ffa37520937
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75740755"
---
# <a name="net-core-guide"></a>Průvodce platformou .NET Core

[.NET Core](about.md) je [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), univerzální vývojová platforma spravovaná společností Microsoft a komunitou .NET na [GitHubu](https://github.com/dotnet/core). Je to multiplatformní (podporující Windows, macOS a Linux) a dá se použít k vytváření aplikací pro zařízení, cloud a IoT.

Další informace o jádru .NET Core, včetně jeho charakteristik, podporovaných jazyků a architektur a klíčových rozhraní API, najdete v tématu [O .NET Core.](about.md)

Podívejte se na [.NET Core Návody se dozvíte,](tutorials/index.md) jak vytvořit jednoduchou aplikaci .NET Core. Spuštění první aplikace trvá jen několik minut. Pokud chcete vyzkoušet .NET Core ve vašem prohlížeči, podívejte se na [čísla v c#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online kurzu.

## <a name="download-net-core"></a>Stáhnout jádro rozhraní .NET

Stáhněte si [sdk .NET Core SDK](https://www.microsoft.com/net/download) a vyzkoušejte .NET Core na počítači se systémem Windows, macOS nebo Linux. A pokud dáváte přednost použití kontejnerů Dockeru, navštivte [centrum .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).

Všechny verze .NET Core jsou k dispozici na [.NET Core ke stažení,](https://dotnet.microsoft.com/download/dotnet-core) pokud hledáte jinou verzi .NET Core.

## <a name="net-core-31"></a>.NET Jádro 3.1

Nejnovější verze je .NET Core 3.1. 3.1 zahrnuje drobná vylepšení oproti .NET Core 3.0, ale .NET Core 3.1 je [dlouhodobě podporovaná verze](https://dotnet.microsoft.com/platform/support/policy/dotnet-core). Další informace o verzi .NET Core 3.1 naleznete [v tématu Co je nového v rozhraní .NET Core 3.1](./whats-new/dotnet-core-3-1.md).

## <a name="create-your-first-application"></a>Vytvoření první aplikace

Po instalaci sady .NET Core SDK otevřete příkazový řádek. Chcete-li `dotnet` vytvořit a spustit aplikaci jazyka C#, zadejte následující příkazy:

```dotnetcli
dotnet new console
dotnet run
```

Měl by se zobrazit následující výstup:

```output
Hello World!
```

## <a name="support"></a>Podpora

.NET Core je [podporován společností Microsoft](https://dotnet.microsoft.com/platform/support/policy), ve Windows, macOS a Linuxu. Je aktualizován pro zabezpečení a kvalitu několikrát do roka, obvykle měsíčně.

Binární distribuce .NET Core jsou sestavené a testované na serverech spravovaných společností Microsoft v Azure a podporované stejně jako všechny produkty společnosti Microsoft.

[Red Hat podporuje .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL). Red Hat staví .NET Core ze zdroje a zpřístupňuje jej v [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat a Microsoft spolupracují, aby zajistily, že .NET Core funguje dobře na RHEL.
