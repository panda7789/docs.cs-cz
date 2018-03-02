---
title: "Pomocí správy balíčků F # pro Azure."
description: "Ke správě závislosti F # Azure použijte stáhnout nebo Nuget"
keywords: "Visual f #, f #, funkční programování, .NET, .NET Core, Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: dd32ef9c-5416-467e-9fa3-c9ee3bb08456
ms.openlocfilehash: d1a807053f5c4c45492f206739922aacdf6d4122
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2018
---
# <a name="package-management-for-f-azure-dependencies"></a>Balíček správy pro závislosti Azure F #

Získání balíčky pro vývoj pro Azure je snadný při použití Správce balíčků. Dvě možnosti jsou [Stáhnout](https://fsprojects.github.io/Paket/) a [NuGet](https://www.nuget.org/).

## <a name="using-paket"></a>Pomocí stáhnout

Pokud používáte [Stáhnout](https://fsprojects.github.io/Paket/) jako závislost nadřízeného, můžete použít `paket.exe` nástroje pro přidání Azure závislosti. Příklad:

    > paket add nuget WindowsAzure.Storage

Nebo, pokud používáte [Mono](https://www.mono-project.com/) pro vývoj pro různé platformy .NET:

    > mono paket.exe add nuget WindowsAzure.Storage

Bude přidáno `WindowsAzure.Storage` množina závislosti balíčků pro projekt v aktuálním adresáři, upravte `paket.dependencies` souboru a stáhněte si balíček. Pokud jste dříve nastavili závislosti nebo práci s projektem kde závislosti již byly vytvořeny pomocí jiné vývojáře, můžete vyřešit a instalaci závislostí místně takto:

    > paket install

Nebo pro Mono vývoj:

    > mono paket.exe install

Všechny závislosti balíčků můžete aktualizovat na nejnovější verzi takto:

    > paket update

Nebo pro Mono vývoj:

    > mono paket.exe update

## <a name="using-nuget"></a>Pomocí nástroje Nuget

Pokud používáte [NuGet](https://www.nuget.org/) jako závislost nadřízeného, můžete použít `nuget.exe` nástroje pro přidání Azure závislosti. Příklad:

    > nuget install WindowsAzure.Storage -ExcludeVersion

Nebo pro Mono vývoj:

    > mono nuget.exe install WindowsAzure.Storage -ExcludeVersion

Bude přidáno `WindowsAzure.Storage` množina závislosti balíčků pro projekt v aktuálním adresáři a stažení balíčku. Pokud jste dříve nastavili závislosti nebo práci s projektem kde závislosti již byly vytvořeny pomocí jiné vývojáře, můžete vyřešit a instalaci závislostí místně takto:

    > nuget restore 

Nebo pro Mono vývoj:

    > mono nuget.exe restore

Všechny závislosti balíčků můžete aktualizovat na nejnovější verzi takto:

    > nuget update

Nebo pro Mono vývoj:

    > mono nuget.exe update

## <a name="referencing-assemblies"></a>Odkazování na sestavení

Chcete-li použít vlastních balíčků ve vašem skriptu F #, je třeba odkazovat sestavení součástí balíčků pomocí `#r` – direktiva. Příklad:

    > #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"

Jak vidíte, budete muset zadat relativní cestu k knihovnu DLL a úplný název knihovny DLL, která nemusí být přesně stejný jako název balíčku. Cesta bude obsahovat framework verze a případně číslo verze balíčku. Pokud chcete vyhledat všechny nainstalované sestavení, můžete použít přibližně takto na příkazovém řádku Windows:

    > cd packages/WindowsAzure.Storage
    > dir /s/b *.dll

Nebo v prostředí Unix něco podobné výjimky:

    > find packages/WindowsAzure.Storage -name "*.dll"

Tím získáte cesty na nainstalovaných sestavení. Odtud můžete vybrat správnou cestu pro vaši verzi framework.
