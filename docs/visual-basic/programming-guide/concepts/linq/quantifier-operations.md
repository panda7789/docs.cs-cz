---
title: Operace kvantifikátoru
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: 9a2e35e0511915cb17b99550a8bf382bd9d46526
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396308"
---
# <a name="quantifier-operations-visual-basic"></a>Operace kvantifikátoru (Visual Basic)
Operace kvantifikátoru vrací <xref:System.Boolean> hodnotu, která označuje, zda některé nebo všechny prvky v sekvenci splní podmínku.  
  
 Následující ilustrace znázorňuje dvě různé operace kvantifikátoru ve dvou různých zdrojových sekvencích. První operace se zeptá, zda je jeden nebo více prvků znaku A a výsledek je `true` . Druhá operace se zeptá, jestli jsou všechny prvky znakem A a výsledek je `true` .  
  
 ![Operace kvantifikátoru LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 Standardní metody operátoru dotazu, které provádějí operace kvantifikátoru, jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Description|Visual Basic syntaxe výrazu dotazu|Další informace|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Vše|Určuje, zda všechny prvky v sekvenci splní podmínku.|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|Všechny|Určuje, zda některé prvky v sekvenci splní podmínku.|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|Contains|Určuje, zda sekvence obsahuje zadaný element.|Neužívá se.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazů dotazů  
 Tyto příklady používají `Aggregate` klauzuli v Visual Basic jako součást podmínky filtrování v dotazu LINQ.  
  
 V následujícím příkladu je použita `Aggregate` klauzule a <xref:System.Linq.Enumerable.All%2A> metoda rozšíření pro návrat z kolekce, které jsou pro uživatele, jejichž domácí skupina jsou starší než zadané stáří.  
  
 [!code-vb[CsLINQAnyAll#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#1)]  
  
 V dalším příkladu se používá `Aggregate` klauzule a <xref:System.Linq.Enumerable.Any%2A> metoda rozšíření pro návrat z kolekce pro uživatele, kteří mají alespoň jednu PET, která je starší než zadané stáří.  
  
 [!code-vb[CsLINQAnyAll#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#2)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq>
- [Přehled standardních operátorů dotazů (Visual Basic)](standard-query-operators-overview.md)
- [Aggregate – klauzule](../../../language-reference/queries/aggregate-clause.md)
- [Postupy: vytvoření dotazu na věty obsahující zadanou množinu slov (LINQ) (Visual Basic)](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
