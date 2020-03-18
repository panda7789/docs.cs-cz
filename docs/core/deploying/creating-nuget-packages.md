---
title: Vytvoření balíčku NuGet pomocí rozhraní CLI jádra .NET
description: Zjistěte, jak vytvořit balíček NuGet pomocí příkazu 'dotnet pack'.
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: 3f8e75a501cfc48e1c416f71e91290cab1a4ffae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920923"
---
# <a name="how-to-create-a-nuget-package-with-the-net-core-cli"></a>Jak vytvořit balíček NuGet s rozhraním .NET Core CLI

> [!NOTE]
> Následující text ukazuje ukázky příkazového řádku pomocí Unixu. Příkaz, `dotnet pack` jak je zde uvedeno, funguje stejným způsobem v systému Windows.

Očekává se, že knihovny .NET Standard a .NET Core budou distribuovány jako balíčky NuGet. To je ve skutečnosti, jak jsou distribuovány a spotřebovány všechny knihovny .NET Standard. To se nejsnadněji `dotnet pack` provádí pomocí příkazu.

Představte si, že jste právě napsali úžasnou novou knihovnu, kterou chcete distribuovat přes NuGet. Můžete vytvořit balíček NuGet s nástroji pro různé platformy k tomu přesně to! Následující příklad předpokládá knihovnu s názvem `netstandard1.0` **SuperAwesomeLibrary,** která cílí .

Pokud máte přenosné závislosti, to znamená projekt, který závisí na jiném balíčku, ujistěte se, že obnovit balíčky pro celé řešení s `dotnet restore` příkazem před vytvořením balíčku NuGet. Pokud tak neučiníte, `dotnet pack` příkaz nebude fungovat správně.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Po obnovení balíčků můžete přejít do adresáře, kde knihovna žije:

```console
cd src/SuperAwesomeLibrary
```

Pak je to jen jeden příkaz z příkazového řádku:

```dotnetcli
dotnet pack
```

Složka */bin/Debug* bude nyní vypadat takto:

```console
$ ls bin/Debug
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Tím se vytvoří balíček, který je možné ladit. Pokud chcete vytvořit balíček NuGet s binárními soubory verze, `--configuration` stačí `-c`přidat (nebo `release` ) přepínač a použít jako argument.

```dotnetcli
dotnet pack --configuration release
```

Složka */bin* bude nyní obsahovat složku *vydání* obsahující balíček NuGet s binárními soubory verzí:

```console
$ ls bin/release
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

A nyní máte potřebné soubory pro publikování balíčku NuGet!

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>Nepleťte si `dotnet pack` s`dotnet publish`

Je důležité si uvědomit, že `dotnet publish` v žádném okamžiku je příkaz zapojen. Příkaz `dotnet publish` je určen pro nasazení aplikací se všemi jejich závislostmi ve stejném balíčku – ne pro generování balíčku NuGet, který má být distribuován a spotřebován prostřednictvím NuGet.

## <a name="see-also"></a>Viz také

- [Úvodní příručka: Vytvoření a publikování balíčku](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
