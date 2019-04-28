---
title: Vytvoří balíček NuGet s nástroji .NET Core rozhraní příkazového řádku (CLI)
description: Zjistěte, jak vytvořit balíček NuGet pomocí příkazu "balíčku dotnet".
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: 1add3470799b75ebb92c67eed3509523e510ab6c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650892"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a>Jak vytvořit balíček NuGet s nástroji .NET Core rozhraní příkazového řádku (CLI)

> [!NOTE]
> Následující obrázek znázorňuje ukázky příkazového řádku s použitím systému Unix. `dotnet pack` Příkaz, jak je znázorněno zde funguje stejným způsobem jako na Windows.

Knihovny .NET standard a .NET Core se očekává distribuována jako balíčky NuGet. Toto je ve skutečnosti jak všech knihoven .NET Standard jsou distribuované a využívat. Snadno to provádí pomocí `dotnet pack` příkazu.

Představte si, že jste napsali úžasnou novou knihovnu, která chcete distribuovat přes NuGet. Můžete vytvořit balíček NuGet pomocí nástrojů pro různé platformy k tomu přesně! V následujícím příkladu se předpokládá knihovnu s názvem **SuperAwesomeLibrary** cíle, které `netstandard1.0`.

Pokud máte přechodné závislosti; To znamená, že projekt, který závisí na jiném balíčku, budete muset Ujistěte se, že k obnovení balíčků pro celé řešení s `dotnet restore` příkaz před vytvořením balíčku NuGet. Pokud tak neučiníte způsobí `dotnet pack` příkaz nebude správně fungovat.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Až se ujistíte, obnovení balíčků, můžete přejít k adresáři, kde se nachází knihovny:

```console
cd src/SuperAwesomeLibrary
```

Pak je pouze jediný příkaz z příkazového řádku:

```console
dotnet pack
```

Vaše `/bin/Debug` složky se teď měl vypadat takto:

```console
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Mějte na paměti, vznikne balíčku, který je schopen právě laděny. Pokud chcete vytvořit balíček NuGet s binárními soubory verze, všechno, co potřebujete udělat je přidat `--configuration` (nebo `-c`) přepněte a použít `release` jako argument.

```console
dotnet pack --configuration release
```

Vaše `/bin` složky budou mít `release` složku, která obsahuje váš balíček NuGet s binárními soubory verze:

```console
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

A teď máte soubory potřebné k publikování balíčku NuGet.

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>Nepleťte si `dotnet pack` s `dotnet publish`

Je důležité si uvědomit, že v žádném bodě `dotnet publish` příkaz nepodílí. `dotnet publish` Příkaz slouží k nasazení aplikace se všemi jejich závislosti ve stejné sadě – ne pro generování balíčku NuGet k distribuci a spotřebované prostřednictvím balíčku NuGet.

## <a name="see-also"></a>Viz také:

- [Rychlý start: Vytvoření a publikování balíčku](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)