---
title: Dělení dat (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 2da63a1f6b73c8592d6036a90fa374a0d4385f4c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839571"
---
# <a name="partitioning-data-visual-basic"></a>Dělení dat (Visual Basic)
Vytváření oddílů v technologii LINQ odkazuje na operaci dělení vstupní sekvence na dva oddíly bez uspořádání prvků a vrácení jednoho z částí.  
  
 Následující obrázek znázorňuje výsledky tři různé dělení operace na sekvenci znaků. První operace vrátí první tři prvky v sekvenci. Druhou operaci přeskočí první tři prvky a vrátí zbývající prvky. Třetí operace přeskočí první dva prvky v pořadí a vrátí následující tři elementy.  
  
 ![Obrázek, který ukazuje tři operace dělení LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 V následující části jsou uvedeny standardní metody operátoru dotazu, které oddílu pořadí.  
  
## <a name="operators"></a>Operátory  
  
|Název operátoru|Popis|Syntaxe výrazu dotazu jazyka Visual Basic|Další informace|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|Skip|Přeskočí elementy až do zadané pozice v pořadí.|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile –|Vynechává prvky podle funkce predikátu, dokud element nesplňuje podmínku.|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Získá prvků až do zadané pozice v pořadí.|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile –|Přijímá prvky podle funkce predikátu, dokud element nesplňuje podmínku.|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazů dotazů  
  
### <a name="skip"></a>Skip  
 Následující příklad kódu používá `Skip` klauzule v jazyce Visual Basic mají přeskočit první čtyři řetězce v poli řetězců před vrácením zbývající řetězce v poli.  
  
 [!code-vb[CsLINQPartitioning#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#1)]  
  
### <a name="skipwhile"></a>SkipWhile –  
 Následující příklad kódu používá `Skip While` klauzule v jazyce Visual Basic mají přeskočit řetězce v poli je první písmeno řetězce "a". Zbývající řetězce v poli jsou vráceny.  
  
 [!code-vb[CsLINQPartitioning#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#2)]  
  
### <a name="take"></a>Take  
 Následující příklad kódu používá `Take` klauzule v jazyce Visual Basic se vraťte na první dva řetězce v poli řetězců.  
  
 [!code-vb[CsLINQPartitioning#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#3)]  
  
### <a name="takewhile"></a>TakeWhile –  
 Následující příklad kódu používá `Take While` klauzuli v jazyce Visual Basic k vrácení řetězce z pole Délka řetězce je pět nebo méně.  
  
 [!code-vb[CsLINQPartitioning#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#4)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Klauzule Skip](../../../../visual-basic/language-reference/queries/skip-clause.md)
- [Klauzule Skip While](../../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Klauzule Take](../../../../visual-basic/language-reference/queries/take-clause.md)
- [Klauzule Take While](../../../../visual-basic/language-reference/queries/take-while-clause.md)
