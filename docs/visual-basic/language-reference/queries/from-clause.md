---
title: "From – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0ecdc8b70fb1ae164a6c78998ce11db9938fbb56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="from-clause-visual-basic"></a>From – klauzule (Visual Basic)
Určuje jeden nebo více proměnných rozsahu a kolekce dotazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`element`|Požadováno. A *proměnnou rozsahu* použít k iteraci v rámci prvků kolekce. Proměnná rozsahu slouží k odkazování na každý člen `collection` jako iteruje dotaz `collection`. Musí být typu vyčíslitelná.|  
|`type`|Volitelné. Typ `element`. Pokud žádné `type` je zadaný typ `element` je odvozeno z `collection`.|  
|`collection`|Požadováno. Odkazuje na kolekci má být dotazován. Musí být typu vyčíslitelná.|  
  
## <a name="remarks"></a>Poznámky  
 `From` Klauzule slouží k identifikaci zdroje dat pro dotaz a proměnné, které slouží k odkazování na element z kolekce zdroje. Tyto proměnné se nazývají *rozsahu proměnné*. `From` Klauzule se vyžaduje pro daný dotaz, s výjimkou případů, kdy `Aggregate` klauzule slouží k identifikaci vrátí pouze agregovat výsledky dotazu. Další informace najdete v tématu [Aggregate – klauzule](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Můžete určit více `From` klauzule v dotazu k identifikaci více kolekcí, který se má spojit. Jsou-li více kolekcí, že jsou vstupní přes nezávisle nebo je můžete připojit, pokud se vztahují. Kolekce lze propojit implicitně pomocí `Select` klauzuli, nebo explicitně pomocí `Join` nebo `Group Join` klauzule. Jako alternativu, můžete určit více proměnné rozsahu a kolekcí v jediném `From` klauzule s každou proměnnou související rozsahu a do čárkami oddělených z jiné kolekce. Následující příklad kódu ukazuje obě možnosti syntaxe pro `From` klauzule.  
  
 [!code-vb[VbSimpleQuerySamples#21](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_1.vb)]  
  
 `From` Klauzule definuje obor dotazu, který je podobný oboru `For` smyčky. Proto každý `element` proměnnou rozsahu v oboru dotazu musí mít jedinečný název. Protože můžete určit více `From` klauzule pro daný dotaz, následných `From` klauzule mohou odkazovat na proměnné rozsahu v `From` klauzuli, nebo se mohou odkazovat na proměnné rozsahu v předchozím `From` klauzule. Například následující příklad ukazuje vnořený `From` klauzule, kde je kolekce v druhé založena na vlastnost proměnnou rozsahu v klauzuli první.  
  
 [!code-vb[VbSimpleQuerySamples#22](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_2.vb)]  
  
 Každý `From` klauzule může následovat libovolnou kombinaci klauzule další dotazu pro upřesnění dotazu. Dotaz můžete upřesnit následujícími způsoby:  
  
-   Implicitně kombinovat více kolekcí pomocí `From` a `Select` klauzule, nebo explicitně pomocí `Join` nebo `Group Join` klauzule.  
  
-   Použití `Where` klauzule filtrování výsledků dotazu.  
  
-   Řazení výsledek pomocí `Order By` klauzule.  
  
-   Seskupit podobné výsledky pomocí `Group By` klauzule.  
  
-   Použití `Aggregate` klauzule k identifikaci agregační funkce vyhodnotit výsledek celý dotaz.  
  
-   Použití `Let` klauzule zavádět proměnné iterace, jehož hodnota je určena pomocí výrazu místo kolekce.  
  
-   Použití `Distinct` klauzule ignorovat výsledky duplicitní dotazu.  
  
-   Identifikaci částí výsledek určený k vrácení pomocí `Skip`, `Take`, `Skip While`, a `Take While` klauzule.  
  
## <a name="example"></a>Příklad  
 Následující dotaz výraz používá `From` klauzule deklarovat proměnnou rozsahu `cust` pro každou `Customer` objekt v `customers` kolekce. `Where` Klauzule používá proměnnou rozsahu omezit výstupu na zákazníky ze zadané oblasti. `For Each` Smyčky zobrazuje název společnosti pro každého zákazníka ve výsledku dotazu.  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_3.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Dotazy](../../../visual-basic/language-reference/queries/queries.md)  
 [Úvod do LINQ v jazyku Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Pro každou... Next – příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [Pro... Next – příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Select – klauzule](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Kde – klauzule](../../../visual-basic/language-reference/queries/where-clause.md)  
 [AGGREGATE – klauzule](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [DISTINCT – klauzule](../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [JOIN – klauzule](../../../visual-basic/language-reference/queries/join-clause.md)  
 [Group Join – klauzule](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [Order By – klauzule](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Let – klauzule](../../../visual-basic/language-reference/queries/let-clause.md)  
 [Skip – klauzule](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Take – klauzule](../../../visual-basic/language-reference/queries/take-clause.md)  
 [Skip While – klauzule](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Take While – klauzule](../../../visual-basic/language-reference/queries/take-while-clause.md)
