---
title: Načítání závislostí – .NET Core
description: Přehled spravovaného a nespravovaného načítání závislostí v .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: 0388bd1fa29ce1caad93c917503dac9eed8974e1
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926397"
---
# <a name="dependency-loading-in-net-core"></a>Načítání závislostí v .NET Core

Každá aplikace .NET Core má závislosti. I jednoduchá `hello world` aplikace má závislosti na částech knihoven tříd .NET Core.

Porozumění logice načítání výchozích sestavení .NET Core vám může pomáhat pochopit a ladit běžné problémy s nasazením.

V některých aplikacích se závislosti dynamicky určují za běhu. V těchto situacích je důležité pochopit, jak jsou načtena spravovaná sestavení a nespravované závislosti.

## <a name="understanding-assemblyloadcontext"></a>Vysvětlení používání třídy AssemblyLoadContext

<xref:System.Runtime.Loader.AssemblyLoadContext> Rozhraní API je centrální pro návrh načítání .NET Core. Článek [Princip porozumění AssemblyLoadContext](understanding-assemblyloadcontext.md) poskytuje koncepční přehled návrhu.

## <a name="loading-details"></a>Podrobné informace o načítání

Podrobnosti o zkušebním algoritmu jsou stručně uvedeny v několika článcích:

- [Algoritmus načítání spravovaného sestavení](loading-managed.md)
- [Algoritmus načítání satelitních sestavení](loading-resources.md)
- [Algoritmus načítání nespravované (nativní) knihovny](loading-unmanaged.md)
- [Výchozí zjišťování](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a>Vytvoření aplikace .NET Core pomocí modulů plug-in

Kurz [Vytvoření aplikace .NET Core s moduly plug-in](../tutorials/creating-app-with-plugin-support.md) popisuje, jak vytvořit vlastní AssemblyLoadContext. Používá <xref:System.Runtime.Loader.AssemblyDependencyResolver> k vyřešení závislostí modulu plug-in. Kurz správně izoluje závislosti modulu plug-in z hostující aplikace.

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>Jak se používá a ladí funkce zrušení načtení sestavení v .NET Core

Podrobný kurz, [Jak používat a ladit nevytížení sestavení v článku .NET Core](../../standard/assembly/unloadability-howto.md) , je podrobný postup. Ukazuje, jak načíst aplikaci .NET Core, provést a poté ji uvolnit. Článek také poskytuje tipy pro ladění.
