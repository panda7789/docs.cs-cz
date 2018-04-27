---
title: Pole
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
caps.latest.revision: 18
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 54f5d68a343f473c67484e9e806551eb115bac36
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="arrays"></a>Pole
**PROVEĎTE ✓** raději pomocí kolekcí přes pole v veřejná rozhraní API. [Kolekce](../../../docs/standard/design-guidelines/guidelines-for-collections.md) oddíl obsahuje podrobné informace o tom, jak si vybrat mezi kolekcí a pole.  
  
 **X nesmí** použít pole pouze pro čtení. Vlastní pole je jen pro čtení a nelze změnit, ale lze změnit prvků v poli.  
  
 **✓ ZVAŽTE** pomocí Vícenásobná pole místo vícerozměrná pole.  
  
 Vícenásobná pole je pole s prvky, které jsou také pole. Pole, které tvoří elementy lze různých velikostí, což méně nevyužité místo pro některé sady dat (např. zhuštěný matice) ve srovnání s vícerozměrná pole. Navíc modulu CLR optimalizuje operace indexu na Vícenásobná pole, takže se mohou vykazovat lepší běhový výkon v některých scénářích.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Array>  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
 [Pokyny k používání](../../../docs/standard/design-guidelines/usage-guidelines.md)
