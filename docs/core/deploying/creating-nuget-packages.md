---
title: Vytvoření balíčku NuGet se pro různé platformy nástroje
description: Naučte se vytvořit balíček NuGet příkazem 'dotnet pack'.
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: 6be94c2e2cef443f69b2d6df7c2d490cb1fb629d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33219453"
---
# <a name="how-to-create-a-nuget-package-with-cross-platform-tools"></a>Postup vytvoření balíčku NuGet se pro různé platformy nástroje

> [!NOTE]
> Následující obrázek znázorňuje příkazového řádku vzorků použití systému Unix.  `dotnet pack` Příkaz, jak je vidět tady funguje stejným způsobem jako v systému Windows.

Pro rozhraní .NET Core 1.0 knihovny budou distribuována jako balíčky NuGet.  Toto je ve skutečnosti jak všech knihoven .NET Standard jsou distribuované a využívat.  Snadno to provádí pomocí `dotnet pack` příkaz.

Představte si, že jste napsali Super novou knihovnu, která chcete distribuovat přes NuGet.  Můžete vytvořit balíček NuGet se mezi nástrojů platformy provedete přesně to!  Následující příklad předpokládá knihovnu volat **SuperAwesomeLibrary** které cíle `netstandard1.0`.

Pokud máte přenositelné závislosti; To znamená, projektu, což závisí na jiného projektu, budete muset nezapomeňte obnovení balíčků pro celé řešení pomocí `dotnet restore` příkazu před vytvořením balíčku NuGet.  Tak neučiníte bude mít za následek `dotnet pack` příkaz nebude správně fungovat.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]


Po zajištění obnovení balíčků, můžete přejít k adresáři, kde je umístěn knihovny:

`$ cd src/SuperAwesomeLibrary`

Pak je jenom jeden příkaz z příkazového řádku:
    
`$ dotnet pack`

Vaše `/bin/Debug` složky bude nyní vypadat například takto:

```
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Všimněte si, že vznikne balíčku, který je schopen laděné.  Pokud chcete vytvořit balíček NuGet s verzi binárních souborů, všechny musíte udělat je přidat `-c` / `--configuration` přepínače a používat `release` jako argument.

`$ dotnet pack --configuration release`

Vaše `/bin` složky teď bude mít `release` složku obsahující váš balíček NuGet s verzi binárních souborů:

```
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

A teď máte potřebné soubory pro publikování balíčku NuGet!

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>Nepleťte si `dotnet pack` s `dotnet publish`

Je důležité si uvědomit, že v žádný bod se `dotnet publish` příkaz zahrnuta.  `dotnet publish` Je určen pro nasazení aplikací s všechny závislé položky v sadě stejné - není pro generování balíčku NuGet pro distribuované a využívat prostřednictvím balíčku NuGet.
