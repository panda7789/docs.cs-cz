---
title: From – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: 67f395069c98d8b60eca8c3663fb180a8dd5a2be
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978160"
---
# <a name="from-clause-visual-basic"></a>From – klauzule (Visual Basic)
Určuje jednu nebo více proměnných rozsahu a kolekce pro dotaz.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`element`|Povinný parametr. A *proměnnou rozsahu* použít k iteraci prvků kolekce. Proměnná rozsahu se používá k odkazování na každý člen `collection` podle dotazu se Iteruje přes `collection`. Musí být typu výčtu.|  
|`type`|Volitelné. Typ `element`. Pokud ne `type` je zadán typ `element` je odvozen z `collection`.|  
|`collection`|Povinný parametr. Odkazuje na kolekci, aby se dalo dotazovat. Musí být typu výčtu.|  
  
## <a name="remarks"></a>Poznámky  
 `From` Klauzule slouží k identifikaci zdrojová data pro dotaz a proměnné, které se používají k odkazování na prvek ze zdrojové kolekce. Tyto proměnné jsou volány *proměnné v rozsahu*. `From` Vyžádáním klauzule dotazu, kromě případů, kdy `Aggregate` klauzule slouží k identifikaci dotaz vrátí pouze agregovat výsledky. Další informace najdete v tématu [Aggregate – klauzule](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Lze zadat více `From` klauzule v dotazu k identifikaci více kolekcí, který se má spojit. Pokud jsou zadány více kolekcí, se vyhodnocují přes nezávisle na sobě nebo je můžete spojit, když se vztahují. Kolekce lze implicitně propojit pomocí `Select` klauzuli, nebo explicitně pomocí `Join` nebo `Group Join` klauzule. Jako alternativu můžete zadat více proměnných rozsahu a kolekce v jediném `From` klauzule s každou proměnnou rozsahu související a kolekce od ostatních oddělené čárkou. Následující příklad kódu ukazuje obě možnosti syntaxe pro `From` klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 `From` Klauzule definuje rozsah dotazu, který je podobný oboru `For` smyčky. Proto se každá `element` proměnnou rozsahu v rámci dotazu musí mít jedinečný název. Vzhledem k tomu, že lze zadat více `From` klauzule dotazu, následné `From` klauzule mohou odkazovat na rozsah proměnné ve `From` klauzuli, nebo mohou odkazovat na proměnné rozsahu v předchozím `From` klauzuli. Například následující příklad ukazuje vnořený `From` klauzule kde kolekce do druhé klauzule je založena na vlastnost proměnnou rozsahu v první klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 Každý `From` klauzule může být následován libovolnou kombinací další klauzule dotazu pro upřesnění dotazu. Dotaz můžete upřesnit následujícími způsoby:  
  
-   Kombinace více kolekcí implicitně pomocí `From` a `Select` klauzule, nebo explicitně pomocí `Join` nebo `Group Join` klauzule.  
  
-   Použití `Where` klauzule můžete filtrovat výsledku dotazu.  
  
-   Řazení výsledků pomocí `Order By` klauzuli.  
  
-   Seskupit podobné výsledky pomocí `Group By` klauzuli.  
  
-   Použití `Aggregate` klauzule k identifikaci agregační funkce má vyhodnotit pro výsledek celého dotazu.  
  
-   Použití `Let` klauzule zavést proměnnou iterace, jehož hodnota je určena výrazem místo kolekce.  
  
-   Použití `Distinct` klauzule ignorovat duplicitní dotaz výsledky.  
  
-   Identifikovat části výsledek určený k vrácení pomocí `Skip`, `Take`, `Skip While`, a `Take While` klauzule.  
  
## <a name="example"></a>Příklad  
 Následující dotaz používá výraz `From` klauzule k deklaraci proměnné rozsahu `cust` pro každou `Customer` objekt `customers` kolekce. `Where` Klauzule používá proměnnou rozsahu omezení výstup pro zákazníky ze zadané oblasti. `For Each` Smyčky zobrazuje název společnosti pro každého zákazníka ve výsledku dotazu.  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a>Viz také:
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Úvod do LINQ v JAZYKU Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Příkaz For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
- [Klauzule Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Klauzule Distinct](../../../visual-basic/language-reference/queries/distinct-clause.md)
- [Klauzule Join](../../../visual-basic/language-reference/queries/join-clause.md)
- [Klauzule Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [Klauzule Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Klauzule Let](../../../visual-basic/language-reference/queries/let-clause.md)
- [Klauzule Skip](../../../visual-basic/language-reference/queries/skip-clause.md)
- [Klauzule Take](../../../visual-basic/language-reference/queries/take-clause.md)
- [Klauzule Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Klauzule Take While](../../../visual-basic/language-reference/queries/take-while-clause.md)
