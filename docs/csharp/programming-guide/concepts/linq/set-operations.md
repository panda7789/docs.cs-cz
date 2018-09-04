---
title: Množinové operace (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: c91ec399e7c3bccd4ef937d5f7f3f871f86f00be
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530056"
---
# <a name="set-operations-c"></a>Množinové operace (C#)
Množinové operace LINQ naleznete operace dotazů, které vytvářejí sadu výsledků dotazu, který je založen na přítomnosti nebo nepřítomnosti ekvivalentních prvků ve stejném nebo různém kolekcí (nebo sady).  
  
 Standardní metody operátoru dotazu, které provádějí operace sady jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Distinct|Odebere duplicitní hodnoty z kolekce.|Nelze použít.|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|S výjimkou|Vrátí množinových rozdílů, což znamená, že prvky jednu kolekci, která není uvedena v druhé kolekci.|Nelze použít.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|Intersect|Vrátí průnik set, což znamená, že prvky, které se zobrazují v každé dvě kolekce.|Nelze použít.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|Unie|Vrátí sjednocení, což znamená, že jedinečných prvků, které se zobrazují v některém z dvě kolekce.|Nelze použít.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a>Porovnání množinové operace  
  
### <a name="distinct"></a>Distinct  
 Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metodu na posloupnost znaků. Vrácená sekvence obsahuje jedinečných prvků ze vstupní sekvence.  
  
 ![Obrázek znázorňující chování Distinct&#40;&#41;. ](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")  
  
### <a name="except"></a>S výjimkou  
 Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>. Vrácená sekvence obsahuje pouze elementy z první vstupní sekvence, které nejsou v druhé vstupní sekvence.  
  
 ![Obrázek znázorňující akce s výjimkou&#40;&#41;. ](../../../../csharp/programming-guide/concepts/linq/media/except.png "s výjimkou")  
  
### <a name="intersect"></a>Intersect  
 Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>. Vrácená sekvence obsahuje prvky, které jsou společné pro vstupní sekvence.  
  
 ![Obrázek znázorňující průniku množin mezi dvěma sekvencemi. ](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")  
  
### <a name="union"></a>Unie  
 Následující ilustrace znázorňuje operaci s sjednocení dvou sekvencí znaků. Vrácená sekvence obsahuje jedinečných prvků z obou vstupních sekvencí.  
  
 ![Obrázek znázorňující sjednocení množin mezi dvěma sekvencemi. ](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq>  
- [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [Postupy: kombinace a porovnávání kolekcí řetězců (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)  
- [Postupy: hledání množinových rozdílů mezi dvěma seznamy (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
