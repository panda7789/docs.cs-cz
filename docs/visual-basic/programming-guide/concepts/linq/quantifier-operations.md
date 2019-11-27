---
title: Operace kvantifikátoru
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: f5b98ec09405ca4b8c715dc7da342e66a5d434d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346585"
---
# <a name="quantifier-operations-visual-basic"></a>Operace kvantifikátoru (Visual Basic)
Operace kvantifikátoru vrací <xref:System.Boolean> hodnotu, která označuje, zda některé nebo všechny prvky v sekvenci splní podmínku.  
  
 Následující ilustrace znázorňuje dvě různé operace kvantifikátoru ve dvou různých zdrojových sekvencích. První operace se zeptá, zda je jeden nebo více prvků znaku A a výsledek je `true`. Druhá operace se zeptá, jestli jsou všechny prvky znakem A a výsledek je `true`.  
  
 ![Operace kvantifikátoru LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 Standardní metody operátoru dotazu, které provádějí operace kvantifikátoru, jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Visual Basic syntaxe výrazu dotazu|Další informace|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Všechny|Určuje, zda všechny prvky v sekvenci splní podmínku.|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|Vše|Určuje, zda některé prvky v sekvenci splní podmínku.|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|Obsahuje|Určuje, zda sekvence obsahuje zadaný element.|Není k dispozici.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazů dotazů  
 Tyto příklady používají klauzuli `Aggregate` v Visual Basic jako součást podmínky filtrování v dotazu LINQ.  
  
 V následujícím příkladu je použita klauzule `Aggregate` a metoda rozšíření <xref:System.Linq.Enumerable.All%2A>, která se má vrátit z kolekce, které jsou všichni lidé, jejichž domácí skupina je starší než zadané stáří.  
  
 [!code-vb[CsLINQAnyAll#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#1)]  
  
 V dalším příkladu se používá klauzule `Aggregate` a metoda rozšíření <xref:System.Linq.Enumerable.Any%2A>, která se má vrátit z kolekce pro uživatele, kteří mají alespoň jednu PET, která je starší než určený věk.  
  
 [!code-vb[CsLINQAnyAll#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Klauzule Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Postupy: vytvoření dotazu na věty obsahující zadanou množinu slov (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
