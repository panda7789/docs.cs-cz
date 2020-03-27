---
title: Úvod a přehled .NET Core
description: .NET Core je modulární, vysoce výkonná implementace rozhraní .NET pro vytváření aplikací pro Windows, Linux a macOS. Další informace o .NET Core pro started a) začínáme.
author: richlander
ms.date: 03/25/2020
ms.custom: updateeachrelease
ms.openlocfilehash: edd3864d3c3c5c0e9fd8c26ee806ffc9e100423d
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80351699"
---
# <a name="introduction-to-net-core"></a>Úvod do rozhraní .NET Core

[.NET Core](about.md) je [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), univerzální vývojová platforma spravovaná společností Microsoft a komunitou .NET na [GitHubu](https://github.com/dotnet/core). Je to multiplatformní (podporující Windows, macOS a Linux) a dá se použít k vytváření aplikací pro zařízení, cloud a IoT.

## <a name="download-net-core"></a>Stáhnout jádro rozhraní .NET

Stáhněte si [sdk .NET Core SDK](https://dotnet.microsoft.com/download) a vyzkoušejte .NET Core na počítači se systémem Windows, macOS nebo Linux. Pokud dáváte přednost použití kontejnerů Dockeru, navštivte [centrum .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).

## <a name="net-core-31"></a>.NET Jádro 3.1

Nejnovější verze je .NET Core 3.1. 3.1 zahrnuje drobná vylepšení oproti .NET Core 3.0, ale .NET Core 3.1 je [dlouhodobě podporovaná verze](https://dotnet.microsoft.com/platform/support/policy/dotnet-core). Další informace o verzi .NET Core 3.1 naleznete [v tématu Co je nového v rozhraní .NET Core 3.1](./whats-new/dotnet-core-3-1.md).

Pokud hledáte jinou verzi rozhraní .NET Core, všechny verze jsou k dispozici na [.NET Core ke stažení](https://dotnet.microsoft.com/download/dotnet-core).

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

.NET Core je [podporován společností Microsoft](https://dotnet.microsoft.com/platform/support/policy) v systémech Windows, macOS a Linux. Je aktualizován pro zabezpečení a kvalitu několikrát do roka, obvykle měsíčně.

Binární distribuce .NET Core jsou sestavené a testované na serverech spravovaných společností Microsoft v Azure a podporované stejně jako všechny produkty společnosti Microsoft.

[Red Hat podporuje .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL). Red Hat staví .NET Core ze zdroje a zpřístupňuje jej v [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat a Microsoft spolupracují, aby zajistily, že .NET Core funguje dobře na RHEL.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Kurzy jádra .NET](tutorials/index.md)

> [!div class="nextstepaction"]
> [Vyzkoušejte v prohlížeči rozhraní .NET Core](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
