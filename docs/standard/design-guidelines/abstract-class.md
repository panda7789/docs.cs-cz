---
title: Abstraktní třída návrhu
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28052cc6848d77acbdf8e9381146ca6fb06c15d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="abstract-class-design"></a>Abstraktní třída návrhu
**X nesmí** definice veřejných nebo chráněného interní konstruktorů v abstraktních typech.  
  
 Konstruktory by měly být veřejné pouze v případě, že uživatelé budou potřebovat pro vytvoření instance typu. Protože nelze vytvořit instanci abstraktního typu, s veřejný konstruktor abstraktní typ je nesprávně navrženou a zavádějící uživatelům.  
  
 **PROVEĎTE ✓** definice s chráněným nebo interní konstruktor v abstraktní třídy.  
  
 Chráněný konstruktor je dnes běžné a jednoduše umožňuje udělat vlastní inicializaci, když se vytvoří podtypů základní třídy.  
  
 Interní konstruktor lze použít k omezení konkrétní implementace abstraktní třídu pro sestavení definice třídy.  
  
 **PROVEĎTE ✓** zadejte alespoň jeden konkrétní typ, který dědí z každé abstraktní třída, která můžete dodávat.  
  
 Díky této pomáhá ověření návrhu abstraktní třídy. Například <xref:System.IO.FileStream?displayProperty=nameWithType> je implementací <xref:System.IO.Stream?displayProperty=nameWithType> abstraktní třídy.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu typu](../../../docs/standard/design-guidelines/type.md)  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
