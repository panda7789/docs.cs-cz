---
title: Operace set (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: cea0c0ba4dd6c7f874f69e3ec4a179248397b67d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591114"
---
# <a name="set-operations-c"></a>Operace set (C#)
Operace s nastavením v LINQ odkazují na operace dotazů, které tvoří sadu výsledků dotazu založenou na přítomnosti nebo nepřítomnosti ekvivalentních prvků v rámci stejné nebo samostatné kolekce (nebo sady).  
  
 Standardní metody operátoru dotazu, které provádějí operace set, jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|C#Syntaxe výrazu dotazu|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Distinct|Odebere z kolekce duplicitní hodnoty.|Není k dispozici.|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|Výjimk|Vrátí množinu rozdílů, což znamená prvky jedné kolekce, které se nezobrazují v druhé kolekci.|Není k dispozici.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|Krývají|Vrátí průnik sady, což znamená prvky, které se zobrazují v každé ze dvou kolekcí.|Není k dispozici.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|Unie|Vrátí sjednocení set, což znamená jedinečné prvky, které se zobrazí v obou dvou kolekcích.|Není k dispozici.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a>Porovnání operací set  
  
### <a name="distinct"></a>Distinct  
 Následující ilustrace znázorňuje chování <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metody v sekvenci znaků. Vrácená sekvence obsahuje jedinečné prvky ze vstupní sekvence.  
  
 ![Obrázek znázorňující chování samostatného&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)  
  
### <a name="except"></a>Výjimk  
 Následující ilustrace znázorňuje chování <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>nástroje. Vrácená sekvence obsahuje pouze prvky z první vstupní sekvence, které nejsou ve druhé vstupní sekvenci.  
  
 ![Obrázek znázorňující akci s výjimkou&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Zobrazuje chování s výjimkou.")  
  
### <a name="intersect"></a>Krývají  
 Následující ilustrace znázorňuje chování <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>nástroje. Vrácená sekvence obsahuje prvky, které jsou společné pro obě vstupní sekvence.  
  
 ![Obrázek znázorňující průnik dvou sekvencí](./media/set-operations/intersection-two-sequences.png)  
 
### <a name="union"></a>Unie  
 Následující ilustrace znázorňuje operaci sjednocení na dvou sekvencích znaků. Vrácená sekvence obsahuje jedinečné prvky z obou vstupních sekvencí.  
  
 ![Obrázek znázorňující sjednocení dvou sekvencí.](./media/set-operations/union-operation-two-sequences.png)  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazůC#()](./standard-query-operators-overview.md)
- [Postupy: Kombinování a porovnávání kolekcí řetězců (LINQ)C#()](./how-to-combine-and-compare-string-collections-linq.md)
- [Postupy: Najde množinu rozdílů mezi dvěma seznamy (LINQ)C#().](./how-to-find-the-set-difference-between-two-lists-linq.md)
