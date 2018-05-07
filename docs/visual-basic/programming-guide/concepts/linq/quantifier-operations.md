---
title: Operace kvantifikátoru (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: 0a0a5fae35a14ab6451f2f56fb2eedd92ac437e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="quantifier-operations-visual-basic"></a>Operace kvantifikátoru (Visual Basic)
Operace kvantifikátoru vrátit <xref:System.Boolean> hodnotu, která určuje, zda některé nebo všechny elementy v pořadí splňují podmínku.  
  
 Následující obrázek znázorňuje dvě různé kvantifikátoru operace na dva různé zdroje pořadí. První operace požádá, pokud jedna nebo více elementů je znak "A" a výsledkem je `true`. Druhá operace požádá, pokud jsou všechny prvky znak "A" a výsledkem je `true`.  
  
 ![Operace kvantifikátoru LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")  
  
 Metody operátor standardní dotazu, které provádějí operace kvantifikátoru jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka Visual Basic|Další informace|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Všechny|Určuje, zda všechny elementy v pořadí splňují podmínku.|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|všechny|Určuje, zda všechny elementy v pořadí splňují podmínku.|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|Obsahuje|Určuje, zda sekvence obsahuje zadaný element.|Nelze použít.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazu dotazu  
 Pomocí těchto příkladech `Aggregate` klauzule v jazyce Visual Basic v rámci podmínku filtrování v dotazu LINQ.  
  
 Následující příklad používá `Aggregate` klauzule a <xref:System.Linq.Enumerable.All%2A> rozšíření metodu pro návrat z kolekce tyto osoby, jejíž mazlíčků jsou všechny starší než zadaná stáří.  
  
 [!code-vb[CsLINQAnyAll#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]  
  
 Další příklad používá `Aggregate` klauzule a <xref:System.Linq.Enumerable.Any%2A> rozšíření metodu pro návrat z kolekce domácími uživatelé, kteří mají alespoň jednu, která je starší než zadaná stáří.  
  
 [!code-vb[CsLINQAnyAll#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq>  
 [Přehled standardních operátorů dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Klauzule Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Postupy: dotazu na věty obsahující zadanou množinu slov (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
