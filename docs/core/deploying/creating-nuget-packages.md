---
title: Vytvoření balíčku NuGet pomocí nástrojů rozhraní příkazového řádku (CLI) .NET Core
description: Naučte se vytvořit balíček NuGet pomocí příkazu dotnet Pack.
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: d36a6ee7d524933577928daa9993fba8ce62f6c7
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116699"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a>Vytvoření balíčku NuGet pomocí nástrojů rozhraní příkazového řádku (CLI) .NET Core

> [!NOTE]
> Následující příklad ukazuje ukázky příkazového řádku v systému UNIX. `dotnet pack` Příkaz, jak je znázorněno zde, funguje stejně jako v systému Windows.

Očekává se, že jsou knihovny .NET Standard a .NET Core distribuované jako balíčky NuGet. To je fakt, jak jsou distribuovány a spotřebovány všechny knihovny .NET Standard. To je nejsnáze hotové `dotnet pack` pomocí příkazu.

Představte si, že jste právě napsali Super novou knihovnu, kterou byste chtěli distribuovat přes NuGet. Můžete vytvořit balíček NuGet s nástroji pro různé platformy, abyste ho mohli přesně dělat. Následující příklad předpokládá, že knihovna s názvem **SuperAwesomeLibrary** , `netstandard1.0`která cílí na.

Pokud máte přenosné závislosti; To znamená, že projekt, který závisí na jiném balíčku, budete muset před vytvořením balíčku NuGet ověřit balíčky pro celé řešení pomocí `dotnet restore` příkazu. Pokud to neuděláte, nebudou mít `dotnet pack` příkaz správně fungovat.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Po obnovení balíčků můžete přejít do adresáře, kde je knihovna umístěná:

```console
cd src/SuperAwesomeLibrary
```

Pak se jedná jenom o jediný příkaz z příkazového řádku:

```dotnetcli
dotnet pack
```

Vaše `/bin/Debug` složka bude nyní vypadat takto:

```console
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Všimněte si, že se tím vytvoří balíček, který je schopný ladit. Pokud chcete vytvořit balíček NuGet s binárními soubory vydání, stačí přidat `--configuration` přepínač (nebo `-c`) a použít `release` ho jako argument.

```dotnetcli
dotnet pack --configuration release
```

Vaše `/bin` složka teď bude `release` obsahovat složku obsahující balíček NuGet s binárními soubory vydání:

```console
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

A teď máte potřebné soubory pro publikování balíčku NuGet!

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>Nepleťte `dotnet pack` si s`dotnet publish`

Je důležité si uvědomit, že v žádném okamžiku není `dotnet publish` zahrnutý příkaz. `dotnet publish` Příkaz slouží k nasazení aplikací se všemi jejich závislostmi ve stejné sadě, a ne pro vygenerování balíčku NuGet, který se má distribuovat a spotřebovat přes NuGet.

## <a name="see-also"></a>Viz také:

- [Rychlý start: Vytvoření a publikování balíčku](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
