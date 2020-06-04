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
ms.openlocfilehash: b80bb047551dee8ab23cfac06b961996992d69b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359538"
---
# <a name="where-clause-visual-basic"></a>Where – klauzule (Visual Basic)
Určuje podmínku filtrování pro dotaz.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a>Součásti  
 `condition`  
 Povinná hodnota. Výraz, který určuje, zda jsou hodnoty pro aktuální položku v kolekci zahrnuty do výstupní kolekce. Výraz se musí vyhodnotit na `Boolean` hodnotu nebo ekvivalent `Boolean` hodnoty. Pokud je podmínka vyhodnocena jako `True` , je prvek zahrnut do výsledku dotazu; v opačném případě je prvek vyloučen z výsledku dotazu.  
  
## <a name="remarks"></a>Poznámky  
 `Where`Klauzule umožňuje filtrovat data dotazu výběrem pouze prvků, které splňují určitá kritéria. Prvky, jejichž hodnoty způsobí, že klauzule, která `Where` má být vyhodnocena, `True` je zahrnuta do výsledku dotazu; ostatní prvky jsou vyloučeny. Výraz použitý v `Where` klauzuli musí vyhodnotit na `Boolean` nebo ekvivalent `Boolean` , jako je například celé číslo, které se vyhodnotí, `False` Pokud je jeho hodnota nulová. Můžete zkombinovat více výrazů v `Where` klauzuli pomocí logických operátorů `And` , jako jsou, `Or` , `AndAlso` , `OrElse` , a `Is` `IsNot` .  
  
 Ve výchozím nastavení nejsou výrazy dotazů vyhodnoceny, dokud nejsou k dispozici, například pokud jsou vázány na data nebo iterované prostřednictvím `For` smyčky. V důsledku toho není `Where` klauzule vyhodnocena, dokud není k dotazu k dispozici. Pokud máte externí hodnoty pro dotaz, které jsou použity v `Where` klauzuli, zajistěte, aby byla v `Where` klauzuli v okamžiku provedení dotazu použita příslušná hodnota. Další informace o provádění dotazů naleznete v tématu [zápis prvního dotazu LINQ](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
 Můžete volat funkce v rámci `Where` klauzule k provedení výpočtu nebo operace s hodnotou z aktuálního prvku v kolekci. Volání funkce v `Where` klauzuli může způsobit, že dotaz bude proveden ihned při jeho definování namísto při jeho použití. Další informace o provádění dotazů naleznete v tématu [zápis prvního dotazu LINQ](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="example"></a>Příklad  
 Následující výraz dotazu používá `From` klauzuli pro deklaraci proměnné rozsahu `cust` pro každý `Customer` objekt v `customers` kolekci. `Where`Klauzule používá proměnnou rozsahu k omezení výstupu na zákazníky ze zadané oblasti. `For Each`Smyčka zobrazí název společnosti pro každého zákazníka ve výsledku dotazu.  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `And` a `Or` logické operátory v `Where` klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a>Viz také

- [Představení technologie LINQ v jazyce Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](index.md)
- [Klauzule FROM](from-clause.md)
- [Klauzule SELECT](select-clause.md)
- [For Each...Next – příkaz](../statements/for-each-next-statement.md)
