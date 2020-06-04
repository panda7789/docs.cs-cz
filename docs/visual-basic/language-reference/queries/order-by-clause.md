---
title: Order By – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
ms.openlocfilehash: 63f454064e88bc18f252940f3abd8e59b8900e5b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359745"
---
# <a name="order-by-clause-visual-basic"></a>Order By – klauzule (Visual Basic)
Určuje pořadí řazení pro výsledek dotazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>Součásti  
 `orderExp1`  
 Povinná hodnota. Jedno nebo více polí z aktuálního výsledku dotazu, které identifikují způsob řazení vrácených hodnot. Názvy polí musí být odděleny čárkami (,). Jednotlivá pole můžete identifikovat ve vzestupném nebo sestupném pořadí pomocí `Ascending` `Descending` klíčových slov nebo. Pokud `Ascending` `Descending` není zadáno klíčové slovo or, výchozí pořadí řazení je vzestupné. V poli pořadí řazení se předává přednost zleva doprava.  
  
## <a name="remarks"></a>Poznámky  
 `Order By`K řazení výsledků dotazu můžete použít klauzuli. `Order By`Klauzule může řadit výsledek jenom na základě proměnné rozsahu pro aktuální obor. `Select`Klauzule například zavádí nový obor ve výrazu dotazu s novými proměnnými iterace pro tento obor. Proměnné rozsahu definované před `Select` klauzulí v dotazu nejsou k dispozici za `Select` klauzulí. Proto pokud chcete výsledky seřadit podle pole, které není v klauzuli k dispozici `Select` , je nutné `Order By` před klauzulí Vložit klauzuli `Select` . Příkladem toho, kdy byste to museli udělat, je, že chcete dotaz seřadit podle polí, která se nevrací jako součást výsledku.  
  
 Vzestupné a sestupné řazení pro pole je určeno implementací <xref:System.IComparable> rozhraní pro datový typ pole. Pokud datový typ neimplementuje <xref:System.IComparable> rozhraní, pořadí řazení se ignoruje.  
  
## <a name="example"></a>Příklad  
 Následující výraz dotazu používá `From` klauzuli pro deklaraci proměnné rozsahu `book` pro `books` kolekci. `Order By`Klauzule seřadí výsledek dotazu podle ceny ve vzestupném pořadí (výchozí nastavení). Knihy se stejnou cenou jsou seřazené podle názvu ve vzestupném pořadí. `Select`Klauzule vybere `Title` `Price` vlastnosti a jako hodnoty vrácené dotazem.  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a>Příklad  
 Následující výraz dotazu používá `Order By` klauzuli pro řazení výsledků dotazu podle ceny v sestupném pořadí. Knihy se stejnou cenou jsou seřazené podle názvu ve vzestupném pořadí.  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a>Příklad  
 Následující výraz dotazu používá `Select` klauzuli pro výběr názvu knihy, ceny, data publikování a autora. Následně naplní `Title` `Price` pole,, `PublishDate` a `Author` proměnné rozsahu pro nový obor. `Order By`Klauzule seřadí novou proměnnou rozsahu podle jména autora, názvu knihy a ceny. Jednotlivé sloupce jsou seřazené ve výchozím pořadí (vzestupně).  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a>Viz také

- [Představení technologie LINQ v jazyce Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](index.md)
- [Klauzule SELECT](select-clause.md)
- [Klauzule FROM](from-clause.md)
