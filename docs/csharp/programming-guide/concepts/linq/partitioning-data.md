---
title: Dělení dat (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: 184d9d34e087a06ca3fad9b0a8dad571253b225d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702363"
---
# <a name="partitioning-data-c"></a>Dělení dat (C#)
Vytváření oddílů v technologii LINQ odkazuje na operaci dělení vstupní sekvence na dva oddíly bez uspořádání prvků a vrácení jednoho z částí.  
  
 Následující obrázek znázorňuje výsledky tři různé dělení operace na sekvenci znaků. První operace vrátí první tři prvky v sekvenci. Druhou operaci přeskočí první tři prvky a vrátí zbývající prvky. Třetí operace přeskočí první dva prvky v pořadí a vrátí následující tři elementy.  
  
 ![Dělení operace LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")  
  
 V následující části jsou uvedeny standardní metody operátoru dotazu, které oddílu pořadí.  
  
## <a name="operators"></a>Operátory  
  
|Název operátoru|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-------------------|-----------------|---------------------------------|----------------------|  
|Skip|Přeskočí elementy až do zadané pozice v pořadí.|Nelze použít.|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile –|Vynechává prvky podle funkce predikátu, dokud element nesplňuje podmínku.|Nelze použít.|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Získá prvků až do zadané pozice v pořadí.|Nelze použít.|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile –|Přijímá prvky podle funkce predikátu, dokud element nesplňuje podmínku.|Nelze použít.|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
