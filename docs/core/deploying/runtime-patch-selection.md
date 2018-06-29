---
title: Samostatná nasazení runtime dopředné posunutí
description: Další informace o dotnet publikování změn pro samostatný nasazení.
author: jralexander
ms.author: kdollard
ms.date: 05/31/2018
ms.openlocfilehash: 39a23917dec1aba5142839265c555da5c1e6f09c
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37071029"
---
# <a name="self-contained-deployment-runtime-roll-forward"></a>Samostatná nasazení runtime dopředné posunutí

.NET core [nasazení nezávislý aplikací](index.md) zahrnují knihovny .NET Core a na .NET Core runtime. Od verze rozhraní .NET Core SDK 2.1.300 (.NET Core 2.1), k nasazení aplikace nezávislý na [publikuje nejvyšší runtime opravy na váš počítač](https://github.com/dotnet/designs/pull/36). Ve výchozím nastavení [ `dotnet publish` ](../tools/dotnet-publish.md) pro samostatný nasazení vybere jako součást sady SDK na publikování počítači nainstalovanou nejnovější verzi. To umožňuje nasazené aplikace na spouštění pomocí oprav zabezpečení (a ostatní opravy) k dispozici během `publish`. Aplikace musí být znovu publikován získání nového opravy. Samostatná aplikace, které jsou vytvořené tak, že zadáte `-r <RID>` na `dotnet publish` příkazu nebo zadáním [runtime identifikátorů (RID)](../rid-catalog.md) v souboru projektu (csproj nebo vbproj) nebo na příkazovém řádku.

## <a name="patch-version-roll-forward-overview"></a>Oprava verze kumulativní dopředného přehled

[`restore`](../tools/dotnet-restore.md), [ `build` ](../tools/dotnet-build.md) a [ `publish` ](../tools/dotnet-publish.md) jsou `dotnet` příkazy, které můžete spustit odděleně. Volba runtime je součástí `restore` operaci, není `publish` nebo `build`. Když zavoláte `publish`, bude vybrána na nejnovější verzi opravy. Když zavoláte `publish` s `--no-restore` argument a potom nelze získat požadovaný oprav verze, protože před `restore` nebyla spuštěna s Nová samostatná aplikace publikování zásady. V takovém případě je generována chyba sestavení s textem podobný následujícímu:

  "Projektu se obnovil pomocí Microsoft.NETCore.App verze 2.0.0, ale s aktuální nastavení, bude místo toho použít verzi 2.0.6. Chcete-li vyřešit tento problém, ujistěte se, že stejné nastavení se používají pro obnovení a pro následující operace, jako je například sestavení nebo publikování. Obvykle tomuto problému může dojít, pokud RuntimeIdentifier vlastnost se nastavuje během sestavení nebo publikovat, ale ne během obnovení."

> [!NOTE]
> `restore` a `build` lze spustit implicitně jako součást jiného příkazu, jako je třeba `publish`. Při spuštění implicitně jako součást jiného příkazu, že jsou k dispozici s další kontext tak, aby vytváří správné artefakty. Při jste `publish` s runtime (například `dotnet publish -r linux-x64`), implicitní `restore` obnoví balíčky pro linux x64 runtime. Když zavoláte `restore` explicitně, se neobnoví runtime balíčků ve výchozím nastavení, protože nemá tohoto kontextu.

## <a name="how-to-avoid-restore-during-publish"></a>Jak se vyhnout obnovení během publikování

Spuštění `restore` jako součást `publish` operace může být žádoucí pro váš scénář. Aby se zabránilo `restore` během `publish` při vytváření samostatná aplikace, postupujte takto:

* Nastavte `RuntimeIdentifiers` vlastnost středníky oddělený seznam všech [identifikátorů RID](../rid-catalog.md) k publikování.
* Nastavte `TargetLatestRuntimePatch` vlastnost `true`.

## <a name="no-restore-argument-with-dotnet-publish-options"></a>Možnosti publikování ne – obnovení argument dotnet.

Pokud chcete vytvořit samostatná aplikace, a [framework závislé aplikace](index.md) s ke stejnému souboru projektu, a chcete použít `--no-restore` argument s `dotnet publish`, pak vyberte jednu z následujících akcí:

1. Dáváte přednost chování framework závislé. Pokud aplikace je závislá na framework, což je výchozí chování. Pokud je samostatná aplikace a můžete použít neopravené 2.1.0 místní modul runtime, nastavte `TargetLatestRuntimePatch` k `false` v souboru projektu.

2. Dáváte přednost nezávislý chování. Pokud je samostatná aplikace, což je výchozí chování. Pokud je aplikace závislé na framework a vyžaduje instalace nejnovější opravy, nastavte `TargetLatestRuntimePatch` k `true` v souboru projektu.

3. Převzetí řízení explicitní framework verze modulu runtime nastavením `RuntimeFrameworkVersion` na verzi konkrétní opravy v souboru projektu.
