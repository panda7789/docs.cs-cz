---
title: 'Postupy: Implementace rozdělovače pro statické dělení'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
ms.openlocfilehash: 94fbb681b20b9c920c20df2a9017f75a9aa9a6ea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091521"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a>Postupy: Implementace rozdělovače pro statické dělení
Následující příklad ukazuje jeden ze způsobů implementace jednoduchého vlastního rozdělovače pro PLINQ, který provádí statické dělení. Protože dělicí metoda nepodporuje dynamické oddíly, nemusíte mít <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Tento konkrétní rozdělovač může poskytovat zrychlení prostřednictvím výchozího dělicího oddílu rozsahu pro zdroje dat, pro které každý prvek vyžaduje větší množství času zpracování.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 Oddíly v tomto příkladu jsou založeny na předpokladu lineárního nárůstu doby zpracování každého prvku. V reálném světě může být obtížné odhadnout dobu zpracování tímto způsobem. Pokud používáte statický dělicí modul s konkrétním zdrojem dat, můžete optimalizovat vzorec dělení zdroje, přidat logiku vyrovnávání zatížení nebo použít přístup k dělení bloků dat, jak je znázorněno v tématu [Postupy: Implementace dynamických oddílů](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).  
  
## <a name="see-also"></a>Viz také:

- [Vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
