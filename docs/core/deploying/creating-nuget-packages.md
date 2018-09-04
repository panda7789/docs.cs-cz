---
title: Vytvoření balíčku NuGet pomocí nástrojů pro různé platformy
description: Zjistěte, jak vytvořit balíček NuGet pomocí příkazu "balíčku dotnet".
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: 6be94c2e2cef443f69b2d6df7c2d490cb1fb629d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43536018"
---
# <a name="how-to-create-a-nuget-package-with-cross-platform-tools"></a>Vytvoření balíčku NuGet pomocí nástrojů pro různé platformy

> [!NOTE]
> Následující obrázek znázorňuje ukázky příkazového řádku s použitím systému Unix.  `dotnet pack` Příkaz, jak je znázorněno zde funguje stejným způsobem jako na Windows.

Pro .NET Core 1.0 se očekává distribuována jako balíčky NuGet knihoven.  Toto je ve skutečnosti jak všech knihoven .NET Standard jsou distribuované a využívat.  Snadno to provádí pomocí `dotnet pack` příkazu.

Představte si, že jste napsali úžasnou novou knihovnu, která chcete distribuovat přes NuGet.  Můžete vytvořit balíček NuGet pomocí nástrojů pro různé platformy k tomu přesně!  V následujícím příkladu se předpokládá knihovnu s názvem **SuperAwesomeLibrary** cíle, které `netstandard1.0`.

Pokud máte přechodné závislosti; To znamená, že projekt, který závisí na jiný projekt, budete muset Ujistěte se, že k obnovení balíčků pro celé řešení s `dotnet restore` příkaz před vytvořením balíčku NuGet.  Pokud tak neučiníte způsobí `dotnet pack` příkaz nebude správně fungovat.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]


Až se ujistíte, obnovení balíčků, můžete přejít k adresáři, kde se nachází knihovny:

`$ cd src/SuperAwesomeLibrary`

Pak je pouze jediný příkaz z příkazového řádku:
    
`$ dotnet pack`

Vaše `/bin/Debug` složky se teď měl vypadat takto:

```
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Mějte na paměti, vznikne balíčku, který je schopen právě laděny.  Pokud chcete vytvořit balíček NuGet s binárními soubory verze, všechno, co potřebujete udělat je přidat `-c` / `--configuration` přepnutí a použít `release` jako argument.

`$ dotnet pack --configuration release`

Vaše `/bin` složky budou mít `release` složku, která obsahuje váš balíček NuGet s binárními soubory verze:

```
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

A teď máte soubory potřebné k publikování balíčku NuGet.

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>Nepleťte si `dotnet pack` s `dotnet publish`

Je důležité si uvědomit, že v žádném bodě `dotnet publish` příkaz nepodílí.  `dotnet publish` Příkaz slouží k nasazení aplikace se všemi jejich závislosti ve stejné sadě – ne pro generování balíčku NuGet k distribuci a spotřebované prostřednictvím balíčku NuGet.
