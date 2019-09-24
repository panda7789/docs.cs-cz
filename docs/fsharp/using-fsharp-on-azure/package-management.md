---
title: Použití Správa balíčků s F# pro Azure
description: Správa F# závislostí Azure pomocí paket nebo NuGet
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 4aa32ace91f30d0e43b9c40067f5f0f456cc4069
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214223"
---
# <a name="package-management-for-f-azure-dependencies"></a>Správa balíčků pro závislosti Azure F#

Získání balíčků pro vývoj pro Azure je snadné, když použijete Správce balíčků. Tyto dvě možnosti jsou [paket](https://fsprojects.github.io/Paket/) a [NuGet](https://www.nuget.org/).

## <a name="using-paket"></a>Použití paket

Pokud jako správce závislostí používáte [paket](https://fsprojects.github.io/Paket/) , můžete použít `paket.exe` nástroj k přidání závislostí Azure. Příklad:

```console
> paket add nuget WindowsAzure.Storage
```

Nebo, pokud používáte [mono](https://www.mono-project.com/) pro vývoj pro různé platformy .NET:

```console
> mono paket.exe add nuget WindowsAzure.Storage
```

Tato akce přidá `WindowsAzure.Storage` do sady závislostí balíčku pro projekt v aktuálním adresáři, `paket.dependencies` upraví soubor a stáhne balíček. Pokud jste dříve nastavili závislosti nebo pracujete s projektem, kde závislosti byly nastaveny jiným vývojářem, můžete závislosti v místním prostředí vyřešit a nainstalovat následujícím způsobem:

```console
> paket install
```

Nebo pro vývoj mono:

```console
> mono paket.exe install
```

Všechny závislosti balíčků můžete aktualizovat na nejnovější verzi, například:

```console
> paket update
```

Nebo pro vývoj mono:

```console
> mono paket.exe update
```

## <a name="using-nuget"></a>Použití NuGet

Pokud jako správce závislostí používáte [NuGet](https://www.nuget.org/) , můžete k přidání závislostí Azure `nuget.exe` použít tento nástroj. Příklad:

```console
> nuget install WindowsAzure.Storage -ExcludeVersion
```

Nebo pro vývoj mono:

```console
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

Tím se přidá `WindowsAzure.Storage` do sady závislostí balíčku pro projekt v aktuálním adresáři a stáhne se balíček. Pokud jste dříve nastavili závislosti nebo pracujete s projektem, kde závislosti byly nastaveny jiným vývojářem, můžete závislosti v místním prostředí vyřešit a nainstalovat následujícím způsobem:

```console
> nuget restore
```

Nebo pro vývoj mono:

```console
> mono nuget.exe restore
```

Všechny závislosti balíčků můžete aktualizovat na nejnovější verzi, například:

```console
> nuget update
```

Nebo pro vývoj mono:

```console
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a>Odkazování na sestavení

Aby bylo možné používat balíčky ve F# skriptu, je nutné odkazovat na sestavení zahrnutá v balíčcích pomocí `#r` direktivy. Příklad:

```fsharp
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

Jak vidíte, budete muset zadat relativní cestu k souboru DLL a úplný název knihovny DLL, který nemusí být přesně stejný jako název balíčku. Cesta bude obsahovat verzi rozhraní a případně číslo verze balíčku. Chcete-li najít všechna nainstalovaná sestavení, můžete použít něco podobného na příkazovém řádku systému Windows:

```console
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

Nebo v prostředí UNIX něco podobného:

```console
> find packages/WindowsAzure.Storage -name "*.dll"
```

To vám poskytne cesty k nainstalovaným sestavením. Odtud můžete vybrat správnou cestu k vaší verzi rozhraní .NET Framework.
