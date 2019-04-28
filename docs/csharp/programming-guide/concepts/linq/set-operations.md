---
title: Množinové operace (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 9e507bbaa39bf040a8ce1564630fb5fbb8c0dbe4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61712193"
---
# <a name="set-operations-c"></a>Množinové operace (C#)
Množinové operace LINQ naleznete operace dotazů, které vytvářejí sadu výsledků dotazu, který je založen na přítomnosti nebo nepřítomnosti ekvivalentních prvků ve stejném nebo různém kolekcí (nebo sady).  
  
 Standardní metody operátoru dotazu, které provádějí operace sady jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Distinct|Odebere duplicitní hodnoty z kolekce.|Není k dispozici.|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|S výjimkou|Vrátí množinových rozdílů, což znamená, že prvky jednu kolekci, která není uvedena v druhé kolekci.|Není k dispozici.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|Intersect|Vrátí průnik set, což znamená, že prvky, které se zobrazují v každé dvě kolekce.|Není k dispozici.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|Unie|Vrátí sjednocení, což znamená, že jedinečných prvků, které se zobrazují v některém z dvě kolekce.|Není k dispozici.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a>Porovnání množinové operace  
  
### <a name="distinct"></a>Distinct  
 Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metodu na posloupnost znaků. Vrácená sekvence obsahuje jedinečných prvků ze vstupní sekvence.  
  
 ![Obrázek znázorňující chování Distinct&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)  
  
### <a name="except"></a>S výjimkou  
 Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>. Vrácená sekvence obsahuje pouze elementy z první vstupní sekvence, které nejsou v druhé vstupní sekvence.  
  
 ![Obrázek znázorňující akce s výjimkou&#40;&#41;. ](./media/set-operations/except-behavior-graphic.png "Ukazuje chování s výjimkou.")  
  
### <a name="intersect"></a>Intersect  
 Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>. Vrácená sekvence obsahuje prvky, které jsou společné pro vstupní sekvence.  
  
 ![Obrázek znázorňující průniku množin mezi dvěma sekvencemi.](./media/set-operations/intersection-two-sequences.png)  
 
### <a name="union"></a>Unie  
 Následující ilustrace znázorňuje operaci s sjednocení dvou sekvencí znaků. Vrácená sekvence obsahuje jedinečných prvků z obou vstupních sekvencí.  
  
 ![Obrázek znázorňující sjednocení množin mezi dvěma sekvencemi.](./media/set-operations/union-operation-two-sequences.png)  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Postupy: Kombinace a porovnávání kolekcí řetězců (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)
- [Postupy: Hledání množinových rozdílů mezi dvěma seznamy (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
