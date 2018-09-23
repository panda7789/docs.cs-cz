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
ms.openlocfilehash: 1ac7e28c3172f2ed68d402e1d04a1664644c7f25
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2018
ms.locfileid: "46705783"
---
# <a name="arrays"></a>Pole
**✓ DO** raději pomocí kolekcí přes pole v veřejná rozhraní API. [Kolekce](../../../docs/standard/design-guidelines/guidelines-for-collections.md) čísti najdete podrobnosti o tom, jak si vybrat mezi kolekcí a polí.  
  
 **X DO NOT** použít pole pouze pro čtení. Vlastní pole je jen pro čtení a nedá se změnit, ale prvky pole mohou být změněny.  
  
 **✓ CONSIDER** pomocí Vícenásobná pole místo vícerozměrná pole.  
  
 Vícenásobné pole je pole s prvky, které jsou také pole. Pole tvořící prvky mohou být různě velká, což vede k menšímu nevyužitému místu u některých sad dat (např. zhuštěný matice) ve srovnání s multidimenzionálními poli. Navíc CLR optimalizuje operace indexu pro vícenásobné pole, proto se může vykazovat lepší běhový výkon v některých scénářích.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Array>  
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
- [Pokyny k používání](../../../docs/standard/design-guidelines/usage-guidelines.md)
