---
title: Modul runtime posunout vpřed pro nasazení samostatné aplikaci .NET Core.
description: Další informace o dotnet publikovat změny pro samostatné nasazení.
author: jralexander
ms.author: kdollard
ms.date: 05/31/2018
ms.custom: seodec18
ms.openlocfilehash: dde00cf71f0d67c8c4380748e01a4ef5c17ebb4a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126676"
---
# <a name="self-contained-deployment-runtime-roll-forward"></a>Samostatná nasazení modulu runtime dopředné posunutí

.NET core [nasazení samostatné aplikace](index.md) zahrnout knihovny .NET Core a .NET Core runtime. Počínaje verzí .NET Core 2.1 SDK (verze 2.1.300), nasazení aplikace v místním kontejneru [publikuje nejvyšší oprava runtime na vašem počítači](https://github.com/dotnet/designs/pull/36). Ve výchozím nastavení [ `dotnet publish` ](../tools/dotnet-publish.md) pro samostatné nasazení se vybrala nejnovější verze, nainstalován jako součást sady SDK na počítači pro publikování. To umožňuje nasazené aplikace na spouštění pomocí opravy zabezpečení (a ostatní opravy) k dispozici během `publish`. Aplikace musí být znovu publikovat získání nové opravy. Samostatná aplikace, které jsou vytvořeny tak, že zadáte `-r <RID>` na `dotnet publish` příkazu nebo zadáním [identifikátor modulu runtime (RID)](../rid-catalog.md) v souboru projektu (csproj nebo vbproj) nebo na příkazovém řádku.

## <a name="patch-version-roll-forward-overview"></a>Oprava přehled dopředné posunutí verze

[`restore`](../tools/dotnet-restore.md), [ `build` ](../tools/dotnet-build.md) a [ `publish` ](../tools/dotnet-publish.md) jsou `dotnet` příkazy, které lze spustit samostatně. Modul runtime je součástí `restore` operace, ne `publish` nebo `build`. Při volání `publish`, vybere se nejnovější verze opravy. Při volání `publish` s `--no-restore` argument a potom nelze získat verzi požadované opravy, protože předcházejícího `restore` nemusí provést pomocí nové samostatné aplikace publikování zásad. V takovém případě se generuje chybu sestavení s podobný následujícímu textu:

  "Projektu došlo k obnovení pomocí verze 2.0.0 balíčky Microsoft.NETCore.App, ale s aktuálním nastavením by místo toho použít verze 2.0.6. Chcete-li vyřešit tento problém, ujistěte se, že se používají pro obnovení a pro následné operace, jako je například sestavení se stejným nastavením nebo publikovat. Obvykle tohoto problému může dojít, pokud RuntimeIdentifier je nastavena během vytváření nebo publikovat, ale ne během obnovení."

> [!NOTE]
> `restore` a `build` lze spustit implicitně jako součást jiného příkazu, jako je třeba `publish`. Při spuštění implicitně jako součást jiného příkazu, že jsou k dispozici s další kontext tak, aby se produkují správné artefakty. Když je `publish` pomocí modulu runtime (například `dotnet publish -r linux-x64`), implicitní `restore` obnoví balíčky pro linux x64 runtime. Při volání `restore` explicitně, je ale neobnoví balíčky runtime ve výchozím nastavení, protože nemá tento kontext.

## <a name="how-to-avoid-restore-during-publish"></a>Jak se vyhnout obnovení během publikování

Spuštění `restore` jako součást `publish` operace může nežádoucí pro váš scénář. Aby se zabránilo `restore` během `publish` při vytváření aplikace v místním kontejneru, postupujte takto:

* Nastavte `RuntimeIdentifiers` vlastnost středníkem oddělený seznam všech [identifikátorů RID](../rid-catalog.md) k publikování.
* Nastavte `TargetLatestRuntimePatch` vlastnost `true`.

## <a name="no-restore-argument-with-dotnet-publish-options"></a>Ne – obnovení argument s dotnet možnosti publikování

Pokud chcete vytvořit samostatná aplikace, a [aplikace závisí na architektuře](index.md) do stejného souboru projektu, a chcete použít `--no-restore` argument s `dotnet publish`, pak vyberte jednu z následujících akcí:

1. Preferovat chování závisí na architektuře. Pokud je aplikace závisí na architektuře, toto je výchozí chování. Pokud je samostatná aplikace a můžete použít bez opravy zabezpečení 2.1.0 místní modul runtime, nastavte `TargetLatestRuntimePatch` k `false` v souboru projektu.

2. Preferovat samostatná chování. Pokud je samostatná aplikace, to je výchozí chování. Pokud aplikace závisí na architektuře a vyžaduje nainstalovanou nejnovější opravu, nastavte `TargetLatestRuntimePatch` k `true` v souboru projektu.

3. Explicitní kontrolou verze modulu runtime rozhraní tak, že nastavíte `RuntimeFrameworkVersion` k oprav konkrétní verze v souboru projektu.
