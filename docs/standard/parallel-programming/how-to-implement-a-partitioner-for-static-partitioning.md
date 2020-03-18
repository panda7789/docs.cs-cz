---
title: 'Postupy: Implementace rozdělovače pro statické dělení'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
ms.openlocfilehash: 94fbb681b20b9c920c20df2a9017f75a9aa9a6ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091521"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a>Postupy: Implementace rozdělovače pro statické dělení
Následující příklad ukazuje jeden způsob, jak implementovat jednoduchý vlastní partitioner pro PLINQ, který provádí statické dělení. Vzhledem k tomu, že rozdělovač nepodporuje dynamické <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>oddíly, není spotřební mj. Tento konkrétní rozdělovač může poskytnout zrychlení přes výchozí rozsah partitioner pro zdroje dat, pro které každý prvek vyžaduje rostoucí množství času zpracování.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 Oddíly v tomto příkladu jsou založeny na předpokladu lineární zvýšení doby zpracování pro každý prvek. V reálném světě může být obtížné předpovědět časy zpracování tímto způsobem. Pokud používáte statický rozdělovač s určitým zdrojem dat, můžete optimalizovat vzorec dělení pro zdroj, přidat logiku vyrovnávání zatížení nebo použít přístup dělení bloku, jak je znázorněno v [postupech: Implementace dynamických oddílů](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).  
  
## <a name="see-also"></a>Viz také

- [Vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
