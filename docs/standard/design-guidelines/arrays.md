---
title: Pole
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c957d4336527de8c11b763c31c1fdf0015b675b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="arrays"></a>Pole
**PROVEĎTE ✓** raději pomocí kolekcí přes pole v veřejná rozhraní API. [Kolekce](../../../docs/standard/design-guidelines/guidelines-for-collections.md) oddíl obsahuje podrobné informace o tom, jak si vybrat mezi kolekcí a pole.  
  
 **X nesmí** použít pole pouze pro čtení. Vlastní pole je jen pro čtení a nelze změnit, ale lze změnit prvků v poli.  
  
 **✓ ZVAŽTE** pomocí Vícenásobná pole místo vícerozměrná pole.  
  
 Vícenásobná pole je pole s prvky, které jsou také pole. Pole, které tvoří elementy lze různých velikostí, což méně nevyužité místo pro některé sady dat (např. zhuštěný matice) ve srovnání s vícerozměrná pole. Navíc modulu CLR optimalizuje operace indexu na Vícenásobná pole, takže se mohou vykazovat lepší běhový výkon v některých scénářích.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Array>  
 [Pokyny pro návrh Framework](../../../docs/standard/design-guidelines/index.md)  
 [Pokyny týkající se používání](../../../docs/standard/design-guidelines/usage-guidelines.md)
