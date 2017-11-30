---
title: "Abstraktní třída návrhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d7b680c3377cbfa40734a57f9408d9487dbf3769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Typ pokynů pro návrh](../../../docs/standard/design-guidelines/type.md)  
 [Pokyny pro návrh Framework](../../../docs/standard/design-guidelines/index.md)
