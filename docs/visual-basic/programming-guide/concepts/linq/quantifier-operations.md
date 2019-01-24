---
title: Operace kvantifikátoru (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: 0f732cdb51ed4e26039fc8c1d02b95ad32f901e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551924"
---
# <a name="quantifier-operations-visual-basic"></a>Operace kvantifikátoru (Visual Basic)
Operace kvantifikátoru vrátit <xref:System.Boolean> hodnotu, která určuje, jestli některé nebo všechny prvky v sekvenci splňují podmínku.  
  
 Následující obrázek znázorňuje dvě různé kvantifikátor operace na dvou sekvencí jiného zdroje. První operace požádá, pokud jeden nebo více elementů jsou znaky "A" a výsledkem je `true`. Druhou operaci požádá, pokud jsou všechny prvky znaků "A" a výsledkem je `true`.  
  
 ![Operace kvantifikátoru LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")  
  
 Standardní metody operátoru dotazu, které provádějí operace kvantifikátoru jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka Visual Basic|Další informace|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Všechny|Určuje, zda všechny prvky v sekvenci splňují podmínku.|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|Jakýkoli|Určuje, zda všechny prvky v sekvenci splňují podmínku.|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|Obsahuje|Určuje, zda sekvence obsahuje zadaný prvek.|Nelze použít.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazů dotazů  
 Tyto příklady používají `Aggregate` klauzule v jazyce Visual Basic jako součást podmínku filtrování v dotazu LINQ.  
  
 V následujícím příkladu `Aggregate` klauzule a <xref:System.Linq.Enumerable.All%2A> metodu rozšíření k vrácení z kolekce osoby, jejíž mazlíčci jsou všechny starší než starší než zadaný limit.  
  
 [!code-vb[CsLINQAnyAll#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]  
  
 Následující příklad používá `Aggregate` klauzule a <xref:System.Linq.Enumerable.Any%2A> metodu rozšíření k vrácení z kolekce domácími tito uživatelé, kteří mají alespoň jednu, která je starší než starší než zadaný limit.  
  
 [!code-vb[CsLINQAnyAll#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Linq>
- [Přehled standardních operátorů dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Klauzule Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Postupy: Dotazu na věty obsahující zadanou množinu slov (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
