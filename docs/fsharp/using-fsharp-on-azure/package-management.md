---
title: Pomocí správy balíčků s F# pro Azure
description: Umožňuje spravovat stáhnout nebo Nuget F# Azure závislosti
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: b180024e2276a2fd7786f35cb922b1aa1d91f0ad
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880022"
---
# <a name="package-management-for-f-azure-dependencies"></a>Správa balíčků pro závislosti Azure F#

Získání balíčky pro vývoj pro Azure je jednoduché, když pomocí Správce balíčků. Jsou dvě možnosti [Stáhnout](https://fsprojects.github.io/Paket/) a [NuGet](https://www.nuget.org/).

## <a name="using-paket"></a>Použití stáhnout

Pokud používáte [Stáhnout](https://fsprojects.github.io/Paket/) jako správce závislostí můžete použít `paket.exe` nástroj Přidat závislosti Azure. Příklad:

```
> paket add nuget WindowsAzure.Storage
```

Nebo v případě, že používáte [Mono](https://www.mono-project.com/) pro vývoj pro různé platformy .NET:

```
> mono paket.exe add nuget WindowsAzure.Storage
```

Tato možnost přidá `WindowsAzure.Storage` sady závislosti balíčků pro projekt v aktuálním adresáři, chcete-li upravit `paket.dependencies` souboru a stáhněte balíček. Pokud jste dříve nastavili závislosti nebo jsou práci s projektem, ve kterém byly nastaveny závislosti jiný vývojář, můžete vyřešit a nainstalujte závislosti místně takto:

```
> paket install
```

Nebo pro Mono vývoj:

```
> mono paket.exe install
```

Všechny závislosti balíčků můžete aktualizovat na nejnovější verzi takto:

```
> paket update
```

Nebo pro Mono vývoj:

```
> mono paket.exe update
```

## <a name="using-nuget"></a>Pomocí nástroje Nuget

Pokud používáte [NuGet](https://www.nuget.org/) jako správce závislostí můžete použít `nuget.exe` nástroj Přidat závislosti Azure. Příklad:

```
> nuget install WindowsAzure.Storage -ExcludeVersion
```

Nebo pro Mono vývoj:

```
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

Tato možnost přidá `WindowsAzure.Storage` do sady závislosti balíčků pro projekt v aktuálním adresáři a stažení balíčku. Pokud jste dříve nastavili závislosti nebo jsou práci s projektem, ve kterém byly nastaveny závislosti jiný vývojář, můžete vyřešit a nainstalujte závislosti místně takto:

```
> nuget restore
```

Nebo pro Mono vývoj:

```
> mono nuget.exe restore
```

Všechny závislosti balíčků můžete aktualizovat na nejnovější verzi takto:

```
> nuget update
```

Nebo pro Mono vývoj:

```
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a>Odkazování na sestavení

Chcete-li použít své balíčky do vašeho F# skriptu, musíte odkazovat sestavení součástí balíčků pomocí `#r` – direktiva. Příklad:

```
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

Jak je vidět, bude nutné zadat relativní cestu knihovny DLL a úplný název knihovny DLL, která nemusí být přesně stejný jako název balíčku. Verze rozhraní framework a případně číslo verze balíčku, bude obsahovat cestu. Najít nainstalovaná sestavení, můžete použít asi takhle nějak. na příkazovém řádku Windows:

```
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

Nebo v prostředí systému Unix, přibližně takto:

```
> find packages/WindowsAzure.Storage -name "*.dll"
```

Tím získáte cesty k nainstalovaná sestavení. Odtud můžete vybrat správnou cestu pro vaši verzi rozhraní framework.
