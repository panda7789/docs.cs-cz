---
title: Množinové operace (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 45b828f89b380b2649ab5ee80f5438d822de9443
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334409"
---
# <a name="set-operations-c"></a>Množinové operace (C#)
Množinové operace v technologii LINQ naleznete v operacích dotazu, které produkují je sada výsledků dotazu, který je založen na přítomnosti nebo absenci ekvivalentní elementů v rámci stejné nebo samostatné kolekce (nebo sady).  
  
 Operátor metody standardní dotazů, které provádět operace set jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Distinct|Odebere duplicitní hodnoty z kolekce.|Nelze použít.|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|S výjimkou|Vrátí množinových rozdílů, což znamená elementy jednu kolekci, která nejsou uvedena v druhé kolekci.|Nelze použít.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|Intersect|Vrátí průnik sady, což znamená elementy, které se zobrazují v každé dvě kolekce.|Nelze použít.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|Unie|Vrátí sjednocení sady, což znamená jedinečný elementy, které se zobrazují v některém z dvě kolekce.|Nelze použít.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a>Porovnání množinové operace  
  
### <a name="distinct"></a>Distinct  
 Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metodu posloupnost znaků. Vrácený pořadí obsahuje jedinečný elementy ze vstupní pořadí.  
  
 ![Obrázek znázorňující chování Distinct&#40;&#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Odlišné")  
  
### <a name="except"></a>S výjimkou  
 Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>. Vrácený pořadí obsahuje pouze elementy z první vstupní pořadí, které nejsou v druhé vstupní pořadí.  
  
 ![Obrázek znázorňující akce s výjimkou&#40;&#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/except.png "s výjimkou")  
  
### <a name="intersect"></a>Intersect  
 Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>. Vrácený pořadí obsahuje prvky, které jsou společné pro objekty vstupních sekvencí.  
  
 ![Obrázek znázorňující průnik dvou sekvencí. ] (../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")  
  
### <a name="union"></a>Unie  
 Následující obrázek znázorňuje sjednocovací operace na dvě sekvence znaků. Vrácený pořadí obsahuje jedinečný prvky z obou vstupních sekvencí.  
  
 ![Obrázek znázorňující sjednocení dvou pořadí. ] (../../../../csharp/programming-guide/concepts/linq/media/union.png "Sjednocení")  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq>  
 [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Postupy: kombinace a porovnávání kolekcí řetězců (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)  
 [Postupy: hledání množinových rozdílů mezi dvěma seznamy (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
