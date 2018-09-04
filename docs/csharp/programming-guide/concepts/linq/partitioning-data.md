---
title: Dělení dat (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: 2e719b3a61b7c42d8ec6afe5fffe88a5bf83f82e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523458"
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq>  
- [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
