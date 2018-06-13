---
title: 'Postupy: Implementace rozdělovače pro statické dělení'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8de4884c43b99c50313d33f683d8634d12043c59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580494"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a>Postupy: Implementace rozdělovače pro statické dělení
Následující příklad ukazuje jeden způsob, jak implementovat jednoduchý vlastní dělicí metody pro PLINQ, který provádí statické dělení. Protože dělicí metody nepodporuje dynamických oddílů, není použití z <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Tato konkrétní rozdělovač může být rychlejší přes výchozí rozdělovač zdroje dat, pro které každý prvek vyžaduje roste množství doba zpracování.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 Oddíly v tomto příkladu jsou založené na předpokladu lineární nárůst doba zpracování pro jednotlivé elementy. V praxi může být obtížné odhadnout časy zpracování tímto způsobem. Pokud používáte statické dělicí metody s konkrétní zdroj dat., můžete optimalizovat rozdělení vzorec pro zdroj, přidejte logiku vyrovnávání zatížení nebo použijte dělení způsob, jak je předvedeno v bloku dat [postupy: implementace dynamických oddílů](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).  
  
## <a name="see-also"></a>Viz také  
 [Vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
