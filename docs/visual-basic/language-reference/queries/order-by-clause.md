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
ms.openlocfilehash: a7104e3dd82ff2dde2911861ce98a7367faf3b25
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350415"
---
# <a name="order-by-clause-visual-basic"></a>Order By – klauzule (Visual Basic)
Určuje pořadí řazení pro výsledek dotazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>Součásti  
 `orderExp1`  
 Požadováno. Jedno nebo více polí z aktuálního výsledku dotazu, které identifikují způsob řazení vrácených hodnot. Názvy polí musí být odděleny čárkami (,). Jednotlivá pole můžete identifikovat ve vzestupném nebo sestupném pořadí pomocí klíčových slov `Ascending` nebo `Descending`. Pokud není zadané žádné `Ascending` ani klíčové slovo `Descending`, výchozí pořadí řazení je vzestupné. V poli pořadí řazení se předává přednost zleva doprava.  
  
## <a name="remarks"></a>Poznámky  
 K řazení výsledků dotazu můžete použít klauzuli `Order By`. Klauzule `Order By` může řadit výsledek jenom na základě proměnné rozsahu pro aktuální obor. Například klauzule `Select` zavádí nový obor ve výrazu dotazu s novými proměnnými iterace pro tento obor. Proměnné rozsahu definované před klauzulí `Select` v dotazu nejsou k dispozici po klauzuli `Select`. Proto pokud chcete výsledky seřadit podle pole, které není k dispozici v klauzuli `Select`, je nutné před klauzulí `Select` Vložit klauzuli `Order By`. Příkladem toho, kdy byste to museli udělat, je, že chcete dotaz seřadit podle polí, která se nevrací jako součást výsledku.  
  
 Vzestupné a sestupné řazení pro pole je určeno implementací rozhraní <xref:System.IComparable> pro datový typ pole. Pokud datový typ neimplementuje rozhraní <xref:System.IComparable>, pořadí řazení se ignoruje.  
  
## <a name="example"></a>Příklad  
 Následující výraz dotazu používá klauzuli `From` k deklaraci proměnné rozsahu `book` pro kolekci `books`. Klauzule `Order By` seřadí výsledek dotazu podle ceny ve vzestupném pořadí (výchozí nastavení). Knihy se stejnou cenou jsou seřazené podle názvu ve vzestupném pořadí. Klauzule `Select` vybere `Title` a `Price` vlastnosti jako hodnoty vrácené dotazem.  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a>Příklad  
 Následující výraz dotazu používá klauzuli `Order By` pro řazení výsledků dotazu podle ceny v sestupném pořadí. Knihy se stejnou cenou jsou seřazené podle názvu ve vzestupném pořadí.  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a>Příklad  
 Následující výraz dotazu používá klauzuli `Select` pro výběr názvu knihy, ceny, data publikování a autora. Poté naplní pole `Title`, `Price`, `PublishDate`a `Author` proměnné rozsahu pro nový obor. Klauzule `Order By` seřadí novou proměnnou rozsahu podle jména autora, názvu knihy a ceny. Jednotlivé sloupce jsou seřazené ve výchozím pořadí (vzestupně).  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a>Viz také:

- [Úvod do jazyka LINQ v Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
