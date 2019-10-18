---
title: Běhové prostředí pro nasazení samoobslužných aplikací v rozhraní .NET Core
description: Přečtěte si o dotnet publish změnách pro samostatná nasazení.
author: KathleenDollard
ms.date: 05/31/2018
ms.custom: seodec18
ms.openlocfilehash: 6a0cdfb34973822c2f40cdb37d4038d3b7ad8e2a
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522098"
---
# <a name="self-contained-deployment-runtime-roll-forward"></a>Samostatné nasazení – dopředné posunutí modulu runtime

[Nasazení samostatně obsažených aplikací](index.md) .NET Core zahrnuje i knihovny .NET Core i modul runtime .NET Core. Počínaje rozhraním .NET Core 2,1 SDK (verze 2.1.300) publikovaná samostatná nasazení aplikace [publikuje na vašem počítači nejvyšší modul opravy](https://github.com/dotnet/designs/pull/36). Ve výchozím nastavení [`dotnet publish`](../tools/dotnet-publish.md) pro samostatné nasazení vybere nejnovější verzi nainstalovanou jako součást sady SDK na počítači pro publikování. Tím umožníte, aby se nasazená aplikace spouštěla s opravami zabezpečení (a dalšími opravami), které jsou dostupné během `publish`. Aby bylo možné získat novou opravu, je nutné aplikaci znovu publikovat. Samostatné aplikace jsou vytvořeny zadáním `-r <RID>` v příkazu `dotnet publish` nebo zadáním [identifikátoru modulu runtime (RID)](../rid-catalog.md) v souboru projektu (csproj/vbproj) nebo na příkazovém řádku.

## <a name="patch-version-roll-forward-overview"></a>Přehled aktualizace verze posunutí – přehled

[`restore`](../tools/dotnet-restore.md), [`build`](../tools/dotnet-build.md) a [`publish`](../tools/dotnet-publish.md) , jsou `dotnet` příkazy, které se dají spouštět samostatně. Volba modulu runtime je součástí operace `restore`, nikoli `publish` nebo `build`. Pokud zavoláte `publish`, bude zvolena nejnovější verze patch. Pokud zavoláte `publish` s argumentem `--no-restore`, pak nebudete mít k dispozici požadovanou verzi opravy, protože předchozí `restore` pravděpodobně nebyla provedena s novou zásadou pro publikování aplikací, která je samostatnou součástí. V tomto případě se chyba sestavení generuje s textem podobným následujícímu:

  "Projekt se obnovil pomocí Microsoft. NETCore. app verze 2.0.0, ale s aktuálním nastavením se místo toho použije verze 2.0.6. Chcete-li tento problém vyřešit, zajistěte, aby se pro obnovení používalo stejné nastavení a pro následné operace, jako je například sestavení nebo publikování. K tomuto problému obvykle dochází, pokud je vlastnost RuntimeIdentifier nastavena během sestavování nebo publikování, ale nikoli během obnovení. "

> [!NOTE]
> `restore` a `build` lze spustit implicitně jako součást jiného příkazu, jako je `publish`. Při implicitním spuštění jako součást jiného příkazu jsou k dispozici s dalším kontextem, aby byly vytvořeny správné artefakty. Když `publish`te s modulem runtime (například `dotnet publish -r linux-x64`), implicitní `restore` obnoví balíčky pro modul runtime pro Linux-x64. Pokud `restore` explicitně zavoláte, neobnoví běhové balíčky ve výchozím nastavení, protože nemá daný kontext.

## <a name="how-to-avoid-restore-during-publish"></a>Jak se vyhnout obnovení během publikování

Spuštění `restore` jako součást operace `publish` může být pro váš scénář nežádoucí. Abyste se vyhnuli `restore` během `publish` při vytváření samostatných aplikací, udělejte toto:

- Nastavte vlastnost `RuntimeIdentifiers` na seznam oddělený středníkem všech [identifikátorů RID](../rid-catalog.md) , které se mají publikovat.
- Vlastnost `TargetLatestRuntimePatch` nastavte na hodnotu `true`.

## <a name="no-restore-argument-with-dotnet-publish-options"></a>Argument No-Restore s možnostmi dotnet publish

Pokud chcete vytvořit samostatně používané aplikace i [aplikace závislé na architektuře](index.md) se stejným souborem projektu a chcete použít argument `--no-restore` s `dotnet publish` a pak zvolte jednu z následujících možností:

1. Preferovat chování závislé na rozhraní. Pokud je aplikace závislá na rozhraní, jedná se o výchozí chování. Pokud je aplikace samostatná a může použít neopravený místní modul runtime 2.1.0, nastavte `TargetLatestRuntimePatch` na `false` v souboru projektu.

2. Preferovat chování samostatně obsaženého. Pokud je aplikace samostatná, jedná se o výchozí chování. Pokud je aplikace závislá na rozhraní a vyžaduje nainstalovanou nejnovější opravu, nastavte `TargetLatestRuntimePatch` na `true` v souboru projektu.

3. Převezměte explicitní řízení verze rozhraní Runtime nastavením `RuntimeFrameworkVersion` na konkrétní verzi opravy v souboru projektu.
