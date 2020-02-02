---
title: Vytvoření balíčku NuGet pomocí .NET Core CLI
description: Naučte se vytvořit balíček NuGet pomocí příkazu dotnet Pack.
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: 3f8e75a501cfc48e1c416f71e91290cab1a4ffae
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920923"
---
# <a name="how-to-create-a-nuget-package-with-the-net-core-cli"></a>Postup vytvoření balíčku NuGet pomocí .NET Core CLI

> [!NOTE]
> Následující příklad ukazuje ukázky příkazového řádku v systému UNIX. Příkaz `dotnet pack`, jak je znázorněno zde, funguje stejně jako v systému Windows.

Očekává se, že jsou knihovny .NET Standard a .NET Core distribuované jako balíčky NuGet. To je fakt, jak jsou distribuovány a spotřebovány všechny knihovny .NET Standard. Tato možnost je nejsnáze hotová pomocí příkazu `dotnet pack`.

Představte si, že jste právě napsali Super novou knihovnu, kterou byste chtěli distribuovat přes NuGet. Můžete vytvořit balíček NuGet pomocí nástrojů pro různé platformy, aby to přesně odpovídalo! Následující příklad předpokládá knihovnu s názvem **SuperAwesomeLibrary** , která cílí na `netstandard1.0`.

Pokud máte přenosné závislosti, tedy projekt, který závisí na jiném balíčku, nezapomeňte obnovit balíčky pro celé řešení pomocí příkazu `dotnet restore` před vytvořením balíčku NuGet. Pokud to neuděláte, dojde k tomu, že příkaz `dotnet pack` nefunguje správně.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Po obnovení balíčků můžete přejít do adresáře, kde je knihovna umístěná:

```console
cd src/SuperAwesomeLibrary
```

Pak se jedná jenom o jediný příkaz z příkazového řádku:

```dotnetcli
dotnet pack
```

Vaše složka */bin/Debug* bude nyní vypadat takto:

```console
$ ls bin/Debug
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Tím se vytvoří balíček, který je schopný ladit. Pokud chcete vytvořit balíček NuGet s binárními soubory vydání, stačí přidat přepínač `--configuration` (nebo `-c`) a jako argument použít `release`.

```dotnetcli
dotnet pack --configuration release
```

Složka */bin* nyní bude obsahovat složku pro *vydání* obsahující balíček NuGet s binárními soubory vydání:

```console
$ ls bin/release
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

A teď máte potřebné soubory pro publikování balíčku NuGet!

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>Nezaměňujte `dotnet pack` s `dotnet publish`

Je důležité si uvědomit, že v žádném okamžiku se jedná o `dotnet publish` příkaz. Příkaz `dotnet publish` slouží k nasazení aplikací se všemi jejich závislostmi ve stejné sadě – ne pro vygenerování balíčku NuGet, který se má distribuovat a spotřebovat přes NuGet.

## <a name="see-also"></a>Viz také:

- [Rychlý Start: vytvoření a publikování balíčku](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
