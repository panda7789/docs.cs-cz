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
ms.openlocfilehash: 404dd848058f7e5c9bc8a74b6d89df18c6c55fad
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004996"
---
# <a name="where-clause-visual-basic"></a>Where – klauzule (Visual Basic)
Určuje podmínku filtrování pro dotaz.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a>Součásti  
 `condition`  
 Požadováno. Výraz, který určuje, zda jsou hodnoty pro aktuální položku v kolekci zahrnuty do výstupní kolekce. Výraz se musí vyhodnotit na hodnotu @no__t 0 nebo ekvivalent hodnoty `Boolean`. Pokud je podmínka vyhodnocena jako `True`, je element zahrnut do výsledku dotazu; v opačném případě je prvek vyloučen z výsledku dotazu.  
  
## <a name="remarks"></a>Poznámky  
 Klauzule `Where` umožňuje filtrovat data dotazu výběrem pouze prvků, které splňují určitá kritéria. Elementy, jejichž hodnoty způsobí, že klauzule `Where`, která má být vyhodnocena jako `True`, je obsažena ve výsledku dotazu; ostatní prvky jsou vyloučeny. Výraz použitý v klauzuli `Where` se musí vyhodnotit na `Boolean` nebo ekvivalent `Boolean`, jako je například celé číslo, které se vyhodnotí jako `False`, pokud je jeho hodnota nulová. Pomocí logických operátorů, jako jsou `And`, `Or`, `AndAlso`, `OrElse`, `Is` a `IsNot`, můžete zkombinovat více výrazů v klauzuli `Where`.  
  
 Ve výchozím nastavení nejsou výrazy dotazů vyhodnoceny, dokud nejsou k dispozici, například pokud jsou vázány na data nebo iterovaná v rámci smyčky `For`. V důsledku toho klauzule `Where` není vyhodnocena, dokud není k dotazu k dispozici. Pokud máte externí hodnoty pro dotaz, které jsou použity v klauzuli `Where`, ujistěte se, že se příslušná hodnota používá v klauzuli `Where` v době spuštění dotazu. Další informace o provádění dotazů naleznete v tématu [zápis prvního dotazu LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
 Můžete volat funkce v rámci klauzule `Where` k provedení výpočtu nebo operace s hodnotou z aktuálního prvku v kolekci. Volání funkce v klauzuli `Where` může způsobit, že dotaz bude proveden ihned při jeho definování namísto při jeho použití. Další informace o provádění dotazů naleznete v tématu [zápis prvního dotazu LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="example"></a>Příklad  
 Následující výraz dotazu používá klauzuli `From` k deklaraci proměnné rozsahu `cust` pro každý objekt `Customer` v kolekci `customers`. Klauzule `Where` používá proměnnou rozsahu k omezení výstupu na zákazníky ze zadané oblasti. Cyklus `For Each` zobrazuje název společnosti pro každého zákazníka ve výsledku dotazu.  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se v klauzuli `Where` používají logické operátory `And` a `Or`.  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a>Viz také:

- [Úvod do jazyka LINQ v Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Příkaz For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
