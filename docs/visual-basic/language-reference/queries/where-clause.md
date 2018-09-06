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
ms.openlocfilehash: de7b4bf3e7dc1145b7e95197c7bd05c66acdabd6
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43859433"
---
# <a name="where-clause-visual-basic"></a>Where – klauzule (Visual Basic)
Určuje podmínku filtrování dotazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Where condition  
```  
  
## <a name="parts"></a>Součásti  
 `condition`  
 Požadováno. Výraz, který určuje, zda hodnoty pro aktuální položku v kolekci jsou zahrnuty v kolekci výstup. Výraz se musí vyhodnotit na `Boolean` hodnotu nebo ekvivalent `Boolean` hodnotu. Pokud je podmínka vyhodnocena jako `True`elementu je zahrnut ve výsledku dotazu; jinak vrátí hodnotu, elementu je vyloučen z výsledku dotazu.  
  
## <a name="remarks"></a>Poznámky  
 `Where` Klauzule umožňuje filtrovat dotaz na data tak, že vyberete pouze prvky, které splňují určitá kritéria. Elementy způsobovat jehož hodnoty `Where` klauzule vyhodnotilo `True` jsou zahrnuty ve výsledku dotazu; další prvky jsou vyloučeny. Výraz, který se používá v `Where` klauzule se musí vyhodnotit na `Boolean` nebo ekvivalent `Boolean`, například celé číslo, které se vyhodnotí jako `False` když jeho hodnota je nula. Můžete zkombinovat více výrazů v `Where` klauzule pomocí logických operátorů `And`, `Or`, `AndAlso`, `OrElse`, `Is`, a `IsNot`.  
  
 Ve výchozím nastavení, se nevyhodnocují – výrazy dotazů, dokud jsou přístupné – například když jsou vázané na data nebo v iterovaném prostřednictvím `For` smyčky. V důsledku toho `Where` klauzule není vyhodnocen, dokud dotaz přistupuje. Pokud máte hodnoty pro dotaz, který se používají v externí `Where` klauzule, zajistit, aby používal odpovídající hodnotu v `Where` klauzule v době spuštění dotazu. Další informace o provádění dotazů, najdete v části [zápis svůj první dotaz LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
 Bude možné volat funkce v rámci `Where` k provedení výpočtu nebo operace na základě hodnot z aktuální prvek v kolekci. Volání funkce `Where` klauzule může způsobit provedení okamžitě, když je definována místo při přístupu k dotazu. Další informace o provádění dotazů, najdete v části [zápis svůj první dotaz LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="example"></a>Příklad  
 Následující dotaz používá výraz `From` klauzule k deklaraci proměnné rozsahu `cust` pro každou `Customer` objekt `customers` kolekce. `Where` Klauzule používá proměnnou rozsahu omezení výstup pro zákazníky ze zadané oblasti. `For Each` Smyčky zobrazuje název společnosti pro každého zákazníka ve výsledku dotazu.  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `And` a `Or` logické operátory při `Where` klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#31](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v JAZYKU Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Dotazy](../../../visual-basic/language-reference/queries/index.md)  
 [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Příkaz For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
