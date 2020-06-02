---
title: 'Postupy: Implementace rozdělovače pro statické dělení'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
ms.openlocfilehash: 22d2cf788d4726488512703356a75f84efd04250
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278503"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a>Postupy: Implementace rozdělovače pro statické dělení
Následující příklad ukazuje jeden ze způsobů implementace jednoduchého vlastního rozdělovače pro PLINQ, který provádí statické dělení. Protože dělicí metoda nepodporuje dynamické oddíly, není z nich spotřební <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> . Tento konkrétní rozdělovač může poskytovat zrychlení prostřednictvím výchozího dělicího oddílu rozsahu pro zdroje dat, pro které každý prvek vyžaduje větší množství času zpracování.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 Oddíly v tomto příkladu jsou založeny na předpokladu lineárního nárůstu doby zpracování každého prvku. V reálném světě může být obtížné odhadnout dobu zpracování tímto způsobem. Pokud používáte statický dělicí modul s konkrétním zdrojem dat, můžete optimalizovat vzorec dělení zdroje, přidat logiku vyrovnávání zatížení nebo použít přístup k dělení bloků dat, jak je znázorněno v tématu [Postupy: Implementace dynamických oddílů](how-to-implement-dynamic-partitions.md).  
  
## <a name="see-also"></a>Viz také

- [Vlastní dělicí metody pro PLINQ a TPL](custom-partitioners-for-plinq-and-tpl.md)
