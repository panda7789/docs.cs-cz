---
title: Runtime roll vpřed pro nasazení samostatných aplikací .NET Core.
description: Další informace o dotnet publikovat změny pro samostatná nasazení.
author: KathleenDollard
ms.date: 05/31/2018
ms.openlocfilehash: 22385c7b5d2bf87755fd51cd6268d21fe3431c74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75740793"
---
# <a name="self-contained-deployment-runtime-roll-forward"></a>Samostatné nasazení – dopředné posunutí modulu runtime

[Samostatná nasazení aplikací](index.md) .NET Core zahrnují knihovny .NET Core i runtime .NET Core. Počínaje .NET Core 2.1 SDK (verze 2.1.300) samostatné nasazení aplikace [publikuje nejvyšší čas běhu opravy na vašem počítači](https://github.com/dotnet/designs/pull/36). Ve výchozím [`dotnet publish`](../tools/dotnet-publish.md) nastavení pro samostatné nasazení vybere nejnovější verzi nainstalovanou jako součást sady SDK v počítači pro publikování. To umožňuje nasazené aplikace spustit s opravami zabezpečení `publish`(a další opravy) k dispozici během . Aplikace musí být znovu publikována, aby bylo možné získat novou opravu. Samostatné aplikace jsou vytvářeny zadáním `-r <RID>` `dotnet publish` příkazu nebo zadáním [identifikátoru runtime (RID)](../rid-catalog.md) v souboru projektu (csproj / vbproj) nebo na příkazovém řádku.

## <a name="patch-version-roll-forward-overview"></a>Přehled posunu verze opravy vpřed

[`restore`](../tools/dotnet-restore.md)a [`build`](../tools/dotnet-build.md) [`publish`](../tools/dotnet-publish.md) jsou `dotnet` příkazy, které lze spustit samostatně. Volba runtime je součástí `restore` operace, `publish` `build`nikoli nebo . Pokud zavoláte `publish`, bude vybrána nejnovější verze opravy. Pokud voláte `publish` `--no-restore` s argumentem, pak nemusí získat požadovanou `restore` verzi opravy, protože předchozí nemusí být provedeny s novou zásadu publikování samostatné aplikace. V tomto případě je generována chyba sestavení s textem podobným následujícímu:

  "Projekt byl obnoven pomocí Microsoft.NETCore.App verze 2.0.0, ale s aktuálním nastavením by se místo toho použila verze 2.0.6. Chcete-li tento problém vyřešit, ujistěte se, že stejná nastavení se používají pro obnovení a pro následné operace, jako je například sestavení nebo publikování. Obvykle k tomuto problému může dojít, pokud runtimeidentifier vlastnost je nastavena během sestavení nebo publikovat, ale ne během obnovení."

> [!NOTE]
> `restore`a `build` lze jej spustit implicitně jako `publish`součást jiného příkazu, například . Při spuštění implicitně jako součást jiného příkazu jsou k dispozici další kontext tak, aby byly vytvořeny správné artefakty. Když `publish` s runtime (například `dotnet publish -r linux-x64`), `restore` implicitní obnoví balíčky pro linux-x64 runtime. Pokud voláte `restore` explicitně, neobnoví balíčky za běhu ve výchozím nastavení, protože nemá tento kontext.

## <a name="how-to-avoid-restore-during-publish"></a>Jak se vyhnout obnovení během publikování

Spuštění `restore` jako součást `publish` operace může být nežádoucí pro váš scénář. Chcete-li se vyhnout `restore` při `publish` vytváření samostatných aplikací, postupujte takto:

- Nastavte `RuntimeIdentifiers` vlastnost na středník-oddělený seznam všech [IDs, které](../rid-catalog.md) mají být publikovány.
- Nastavte `TargetLatestRuntimePatch` vlastnost `true`na .

## <a name="no-restore-argument-with-dotnet-publish-options"></a>Argument bez obnovení s možnostmi publikování dotnet

Pokud chcete vytvořit samostatné aplikace i [aplikace závislé na rámci](index.md) se stejným souborem projektu `--no-restore` a `dotnet publish`chcete použít argument s , zvolte jednu z následujících možností:

1. Preferují chování závislé na rámci. Pokud je aplikace závislá na rámci, toto je výchozí chování. Pokud je aplikace samostatná a může použít neopravený místní runtime 2.1.0, nastavte `TargetLatestRuntimePatch` do `false` v souboru projektu.

2. Preferujte samostatné chování. Pokud je aplikace samostatná, jedná se o výchozí chování. Pokud je aplikace závislá na rozhraní a vyžaduje `TargetLatestRuntimePatch` nainstalovanou nejnovější opravu, nastavte ji `true` v souboru projektu.

3. Převzít explicitní kontrolu verze rozhraní `RuntimeFrameworkVersion` runtime rozhraní nastavením na konkrétní verzi opravy v souboru projektu.
