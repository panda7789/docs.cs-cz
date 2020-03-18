---
title: Načítání závislostí - jádro .NET Core
description: Přehled načítání spravovaných a nespravovaných závislostí v jádru rozhraní .NET
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: f6b5fc1f92171b61dcab162b782ca7212c602d76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73416669"
---
# <a name="dependency-loading-in-net-core"></a>Načítání závislostí v jádru rozhraní .NET

Každá aplikace .NET Core má závislosti. I jednoduchá `hello world` aplikace má závislosti na částech knihoven tříd .NET Core.

Principy logiky načítání výchozího sestavení jádra .NET mohou pomoci pochopit a ladit typické problémy s nasazením.

V některých aplikacích jsou závislosti dynamicky určeny za běhu. V těchto situacích je důležité pochopit, jak jsou načtena spravovaná sestavení a nespravované závislosti.

## <a name="understanding-assemblyloadcontext"></a>Vysvětlení používání třídy AssemblyLoadContext

Rozhraní <xref:System.Runtime.Loader.AssemblyLoadContext> API je centrální pro návrh načítání jádra .NET. [Principy AssemblyLoadContext](understanding-assemblyloadcontext.md) článek poskytuje koncepční přehled návrhu.

## <a name="loading-details"></a>Podrobné informace o načítání

Podrobnosti algoritmu načítání jsou stručně popsány v několika článcích:

- [Algoritmus načítání spravovaného sestavení](loading-managed.md)
- [Algoritmus satelitního nakládacího systému](loading-resources.md)
- [Algoritmus načítání nespravované (nativní) knihovny](loading-unmanaged.md)
- [Výchozí zjišťování](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a>Vytvoření aplikace .NET Core pomocí modulů plug-in

Kurz [Vytvoření aplikace .NET Core s pluginy](../tutorials/creating-app-with-plugin-support.md) popisuje, jak vytvořit vlastní AssemblyLoadContext. Používá k <xref:System.Runtime.Loader.AssemblyDependencyResolver> vyřešení závislosti pluginu. Výukový program správně izoluje závislosti pluginu z hostitelské aplikace.

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>Jak se používá a ladí funkce zrušení načtení sestavení v .NET Core

[Použití a ladění sestavení uvolnitelnost v](../../standard/assembly/unloadability.md) článku .NET Core je podrobný kurz. Ukazuje, jak načíst aplikaci .NET Core, spustit a potom ji uvolnit. Článek také obsahuje tipy pro ladění.
