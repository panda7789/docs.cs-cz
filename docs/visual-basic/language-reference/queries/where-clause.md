---
title: Where – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: 0b61a52a366fb37a0834c9223bc8b7f099354d16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604039"
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
 [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Příkaz For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
