---
title: Order By – klauzule (Visual Basic)
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
ms.openlocfilehash: d4abb5f0b75ae4069c1dbe695a5c810b1f7aa6e1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482594"
---
# <a name="order-by-clause-visual-basic"></a>Order By – klauzule (Visual Basic)
Určuje pořadí řazení výsledku dotazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>Součásti  
 `orderExp1`  
 Požadováno. Nejméně jedno pole z aktuální výsledek dotazu, které určují způsob řazení vrácených hodnot. Názvy polí musí být odděleny čárkou (,). Každé pole můžete určit, jak seřadit ve vzestupném nebo sestupném pořadí pomocí `Ascending` nebo `Descending` klíčová slova. Pokud ne `Ascending` nebo `Descending` – klíčové slovo je zadán, je výchozí pořadí řazení vzestupně. Pole pořadí řazení přednost zleva doprava.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `Order By` klauzule řazení výsledků dotazu. `Order By` Klauzule můžete řadit pouze výsledek založený na proměnnou rozsahu aktuálního oboru. Například `Select` klauzule zavádí nový obor ve výrazu dotazu s nové proměnné iterace pro tento obor. Proměnné definované před v rozsahu `Select` klauzule v dotazu nejsou k dispozici po `Select` klauzuli. Proto pokud chcete vaše výsledky podle pole, která není k dispozici v pořadí `Select` klauzule, je nutné umístit `Order By` klauzule před `Select` klauzuli. Jeden příklad, kdy budete muset udělat při chcete seřadit podle polí, které nebudou zobrazeny jako součást výsledku dotazu.  
  
 Vzestupném a sestupném pořadí pro pole je dáno provádění <xref:System.IComparable> rozhraní pro datový typ pole. Pokud datový typ neimplementuje <xref:System.IComparable> rozhraní, pořadí řazení se ignoruje.  
  
## <a name="example"></a>Příklad  
 Následující dotaz používá výraz `From` klauzule k deklaraci proměnné rozsahu `book` pro `books` kolekce. `Order By` Klauzule výsledku dotazu seřadí podle cena ve vzestupném pořadí (výchozí). Knihy se stejnou cenu jsou seřazeny podle názvu ve vzestupném pořadí. `Select` Klauzule vybere `Title` a `Price` vlastnosti jako hodnoty vrácené dotazem.  
  
 [!code-vb[VbSimpleQuerySamples#24](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující dotaz výraz používá `Order By` klauzule výsledku dotazu seřadit cena v sestupném pořadí. Knihy se stejnou cenu jsou seřazeny podle názvu ve vzestupném pořadí.  
  
 [!code-vb[VbSimpleQuerySamples#25](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_2.vb)]  
  
## <a name="example"></a>Příklad  
 Následující dotaz používá výraz `Select` klauzule vyberte název knihy, ceny, datum publikování a vytvářet. Pak naplní `Title`, `Price`, `PublishDate`, a `Author` pole proměnné rozsahu nového oboru. `Order By` Klauzule orders nové proměnné rozsahu jméno autora, název knihy a ceny. Každý sloupec je seřazen v pořadí, výchozí (vzestupně).  
  
 [!code-vb[VbSimpleQuerySamples#26](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_3.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v JAZYKU Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Dotazy](../../../visual-basic/language-reference/queries/index.md)  
 [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
