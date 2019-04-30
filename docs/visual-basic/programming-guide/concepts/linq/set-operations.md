---
title: Množinové operace (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: 59ab09607462c762758e6a246ec218a92e01f5de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786841"
---
# <a name="set-operations-visual-basic"></a>Množinové operace (Visual Basic)
Množinové operace LINQ naleznete operace dotazů, které vytvářejí sadu výsledků dotazu, který je založen na přítomnosti nebo nepřítomnosti ekvivalentních prvků ve stejném nebo různém kolekcí (nebo sady).  
  
 Standardní metody operátoru dotazu, které provádějí operace sady jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka Visual Basic|Další informace|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Distinct|Odebere duplicitní hodnoty z kolekce.|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
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
## <a name="query-expression-syntax-example"></a>Příklad syntaxe výrazu dotazu  
 V následujícím příkladu `Distinct` klauzuli v LINQ dotaz, který vrací jedinečný čísla ze seznamu celých čísel.  
  
 [!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Klauzule Distinct](../../../../visual-basic/language-reference/queries/distinct-clause.md)
- [Postupy: Kombinace a porovnávání kolekcí řetězců (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)
- [Postupy: Hledání množinových rozdílů mezi dvěma seznamy (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
