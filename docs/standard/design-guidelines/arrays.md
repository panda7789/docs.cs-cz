---
title: Pole
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2945ead7c22b759ce88f6585e2254e9bc540a7ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570392"
---
# <a name="arrays"></a>Pole
**✓ DO** raději pomocí kolekcí přes pole v veřejná rozhraní API. [Kolekce](../../../docs/standard/design-guidelines/guidelines-for-collections.md) oddíl obsahuje podrobné informace o tom, jak si vybrat mezi kolekcí a pole.  
  
 **X DO NOT** použít pole pouze pro čtení. Vlastní pole je jen pro čtení a nelze změnit, ale lze změnit prvků v poli.  
  
 **✓ CONSIDER** pomocí Vícenásobná pole místo vícerozměrná pole.  
  
 Vícenásobná pole je pole s prvky, které jsou také pole. Pole, které tvoří elementy lze různých velikostí, což méně nevyužité místo pro některé sady dat (např. zhuštěný matice) ve srovnání s vícerozměrná pole. Navíc modulu CLR optimalizuje operace indexu na Vícenásobná pole, takže se mohou vykazovat lepší běhový výkon v některých scénářích.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Array>  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
 [Pokyny k používání](../../../docs/standard/design-guidelines/usage-guidelines.md)
