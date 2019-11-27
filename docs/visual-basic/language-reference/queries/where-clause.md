---
title: Where – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: 60b7ebe96ce0c4580c36675b2e4aa5f9888732c3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349632"
---
# <a name="where-clause-visual-basic"></a>Where – klauzule (Visual Basic)
Určuje podmínku filtrování pro dotaz.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a>Součásti  
 `condition`  
 Požadováno. Výraz, který určuje, zda jsou hodnoty pro aktuální položku v kolekci zahrnuty do výstupní kolekce. Výraz se musí vyhodnotit na `Boolean` hodnotu nebo ekvivalent `Boolean` hodnoty. Pokud je podmínka vyhodnocena jako `True`, je element zahrnut do výsledku dotazu; v opačném případě je prvek vyloučen z výsledku dotazu.  
  
## <a name="remarks"></a>Poznámky  
 Klauzule `Where` umožňuje filtrovat data dotazu výběrem pouze prvků, které splňují určitá kritéria. Elementy, jejichž hodnoty způsobí, že klauzule `Where` má být vyhodnocena jako `True` je obsažena ve výsledku dotazu; ostatní prvky jsou vyloučeny. Výraz použitý v klauzuli `Where` se musí vyhodnotit na `Boolean` nebo ekvivalent `Boolean`, jako je například celé číslo, které se vyhodnotí jako `False`, pokud je jeho hodnota nulová. Můžete zkombinovat více výrazů v klauzuli `Where` pomocí logických operátorů, jako jsou `And`, `Or`, `AndAlso`, `OrElse`, `Is`a `IsNot`.  
  
 Ve výchozím nastavení nejsou výrazy dotazů vyhodnoceny, dokud nejsou k dispozici, například pokud jsou vázány na data nebo iterované prostřednictvím ve `For` smyčce. V důsledku toho není klauzule `Where` vyhodnocena, dokud není k dotazu k dispozici. Pokud máte externí hodnoty pro dotaz, které jsou použity v klauzuli `Where`, zajistěte, aby se příslušná hodnota používala v klauzuli `Where` v době spuštění dotazu. Další informace o provádění dotazů naleznete v tématu [zápis prvního dotazu LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
 Můžete volat funkce v rámci klauzule `Where` k provedení výpočtu nebo operace s hodnotou z aktuálního prvku v kolekci. Volání funkce v klauzuli `Where` může způsobit, že dotaz bude proveden ihned při jeho definování namísto při jeho použití. Další informace o provádění dotazů naleznete v tématu [zápis prvního dotazu LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="example"></a>Příklad  
 Následující výraz dotazu používá klauzuli `From` k deklaraci proměnné rozsahu `cust` pro každý objekt `Customer` v kolekci `customers`. Klauzule `Where` používá proměnnou rozsahu k omezení výstupu na zákazníky ze zadané oblasti. Smyčka `For Each` zobrazuje název společnosti pro každého zákazníka ve výsledku dotazu.  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `And` a `Or` logické operátory v klauzuli `Where`.  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a>Viz také:

- [Úvod do jazyka LINQ v Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Příkaz For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
