---
title: "Where – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8c2572f513d00bc72e869cf28d382be799f7a303
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="where-clause-visual-basic"></a>Where – klauzule (Visual Basic)
Určuje podmínku filtrování pro dotaz.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Where condition  
```  
  
## <a name="parts"></a>Součásti  
 `condition`  
 Požadováno. Výraz, který určuje, zda hodnoty pro aktuální položku v kolekci jsou zahrnuty v kolekci výstup. Výraz se musí vyhodnotit `Boolean` hodnotu nebo ekvivalent `Boolean` hodnotu. Pokud je podmínka vyhodnocena jako `True`elementu je zahrnutý ve výsledku dotazu jinak, element je vyloučen z výsledku dotazu.  
  
## <a name="remarks"></a>Poznámky  
 `Where` Klauzule vám umožní filtrovat dotaz na data tak, že vyberete pouze elementy, které splňují určitá kritéria. Elementy, jejichž hodnoty způsobit `Where` klauzule vyhodnocení `True` jsou zahrnuty do výsledku dotazu; další elementy jsou vyloučeny. Výraz, který se používá v `Where` klauzule se musí vyhodnotit `Boolean` nebo ekvivalent `Boolean`, například celé číslo, jehož výsledkem `False` při jeho hodnota může být nula. Můžete kombinovat více výrazů v `Where` klauzule pomocí logických operátorů, například `And`, `Or`, `AndAlso`, `OrElse`, `Is`, a `IsNot`.  
  
 Ve výchozím nastavení, nejsou vyhodnotí výrazy dotazu, dokud jsou přístupná – například když jsou vázané na data nebo vstupní prostřednictvím `For` smyčky. V důsledku toho `Where` klauzule není vyhodnocen, dokud dotaz přistupuje. Pokud máte hodnoty externí do dotazu, které se používají v `Where` klauzule, ujistěte se, že příslušná hodnota se používá `Where` klauzule v době spustit dotaz. Další informace o provádění dotazů najdete v tématu [zápis vaše první dotaz LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
 Můžete volat funkce v rámci `Where` klauzule k provedení výpočtu nebo operaci na hodnotu z aktuálního elementu v kolekci. Volání funkce v `Where` klauzule může způsobit dotaz spustit okamžitě, když je definována místo při přístupu. Další informace o provádění dotazů najdete v tématu [zápis vaše první dotaz LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="example"></a>Příklad  
 Následující dotaz výraz používá `From` klauzule deklarovat proměnnou rozsahu `cust` pro každou `Customer` objekt v `customers` kolekce. `Where` Klauzule používá proměnnou rozsahu omezit výstupu na zákazníky ze zadané oblasti. `For Each` Smyčky zobrazuje název společnosti pro každého zákazníka ve výsledku dotazu.  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `And` a `Or` logické operátory při `Where` klauzule.  
  
 [!code-vb[VbSimpleQuerySamples#31](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v jazyku Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Dotazy](../../../visual-basic/language-reference/queries/queries.md)  
 [From – klauzule](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Select – klauzule](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Pro každou... Next – příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
