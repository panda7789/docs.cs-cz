---
title: 'Postupy: Implementace rozdělovače pro statické dělení'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 302d7d98d04e528d205edf38c3fa13bb3f2b2252
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863070"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a>Postupy: Implementace rozdělovače pro statické dělení
Následující příklad ukazuje jeden způsob, jak implementovat jednoduché vlastní dělicí metody pro PLINQ, který provádí statické dělení. Vzhledem k tomu dělicí metoda nepodporuje dynamické oddíly, není použitelné z <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Tento konkrétní rozdělovač může být rychlejší nad výchozí rozdělovač pro zdroje dat, u kterých každý prvek vyžaduje zvýšení množství času procesoru.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 Oddíly v tomto příkladu jsou založeny na předpokladu lineární zvýšení doba zpracování pro každý prvek. V praxi může být obtížné odhadnout časy zpracování tímto způsobem. Pokud používáte statické dělicí metody s konkrétnímu zdroji dat, můžete optimalizovat dělení vzorce pro zdroj, přidejte logiku pro vyrovnávání zatížení nebo použít blok dělení přístup, jak je ukázáno v [postupy: implementace dynamických oddílů](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).  
  
## <a name="see-also"></a>Viz také:

- [Vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
