---
title: From – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: a63fb41fc2b0ad885acf76ad5d56e446922f5b90
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343782"
---
# <a name="from-clause-visual-basic"></a>From – klauzule (Visual Basic)
Určuje jednu nebo více proměnných rozsahu a kolekci pro dotaz.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`element`|Požadováno. *Proměnná rozsahu* používaná k iterování prostřednictvím prvků kolekce. Proměnná rozsahu se používá pro odkazování na každého člena `collection`, protože dotaz prochází `collection`. Musí se jednat o vyčíslitelného typu.|  
|`type`|Volitelná. Typ připojení `element`. Pokud není zadán žádný `type`, typ `element` je odvozen z `collection`.|  
|`collection`|Požadováno. Odkazuje na kolekci, do které se má dotazovat. Musí se jednat o vyčíslitelného typu.|  
  
## <a name="remarks"></a>Poznámky  
 Klauzule `From` slouží k identifikaci zdrojových dat pro dotaz a proměnné, které se používají k odkazování na prvek ze zdrojové kolekce. Tyto proměnné se nazývají *proměnné rozsahu*. Klauzule `From` je vyžadována pro dotaz s výjimkou případů, kdy je použita klauzule `Aggregate` k identifikaci dotazu, který vrací pouze agregované výsledky. Další informace naleznete v tématu [klauzule Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 V dotazu můžete zadat více klauzulí `From` pro identifikaci více kolekcí, které mají být spojeny. Pokud je zadáno více kolekcí, jsou iterované na nezávisle, nebo se k nim můžete připojit, pokud jsou v relaci. Kolekce můžete spojit implicitně pomocí klauzule `Select`, nebo explicitně pomocí klauzule `Join` nebo `Group Join`. Alternativně můžete zadat více proměnných rozsahu a kolekcí v rámci jedné klauzule `From`, přičemž každou související proměnnou rozsahu a kolekci od sebe budou oddělené čárkou. Následující příklad kódu ukazuje obě možnosti syntaxe pro klauzuli `From`.  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 Klauzule `From` definuje rozsah dotazu, který je podobný rozsahu `For` smyčky. Proto musí každá proměnná rozsahu `element` v oboru dotazu mít jedinečný název. Vzhledem k tomu, že lze zadat více klauzulí `From` pro dotaz, následné `From` klauzule mohou odkazovat na proměnné rozsahu v klauzuli `From` nebo mohou odkazovat na proměnné rozsahu v předchozí klauzuli `From`. Například následující příklad ukazuje vnořenou klauzuli `From`, kde kolekce v druhé klauzuli je založena na vlastnosti proměnné rozsahu v první klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 U každé klauzule `From` může následovat jakákoli kombinace dalších klauzulí dotazu pro upřesnění dotazu. Dotaz můžete upřesnit následujícími způsoby:  
  
- Použijte implicitně kombinaci více kolekcí pomocí klauzulí `From` a `Select` nebo explicitně pomocí klauzule `Join` nebo `Group Join`.  
  
- K filtrování výsledků dotazu použijte klauzuli `Where`.  
  
- Seřaďte výsledek pomocí klauzule `Order By`.  
  
- Seskupte podobné výsledky společně pomocí klauzule `Group By`.  
  
- Použijte klauzuli `Aggregate` k identifikaci agregačních funkcí pro vyhodnocení celého výsledku dotazu.  
  
- Použijte klauzuli `Let` k představení proměnné iterace, jejíž hodnota je určena výrazem namísto kolekce.  
  
- K ignorování duplicitních výsledků dotazu použijte klauzuli `Distinct`.  
  
- Identifikujte části výsledku, které se mají vrátit, pomocí klauzulí `Skip`, `Take`, `Skip While`a `Take While`.  
  
## <a name="example"></a>Příklad  
 Následující výraz dotazu používá klauzuli `From` k deklaraci proměnné rozsahu `cust` pro každý objekt `Customer` v kolekci `customers`. Klauzule `Where` používá proměnnou rozsahu k omezení výstupu na zákazníky ze zadané oblasti. Smyčka `For Each` zobrazuje název společnosti pro každého zákazníka ve výsledku dotazu.  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a>Viz také:

- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Úvod do jazyka LINQ v Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Příkaz For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
- [Klauzule Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Klauzule Distinct](../../../visual-basic/language-reference/queries/distinct-clause.md)
- [Klauzule Join](../../../visual-basic/language-reference/queries/join-clause.md)
- [Klauzule Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [Klauzule Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Klauzule Let](../../../visual-basic/language-reference/queries/let-clause.md)
- [Klauzule Skip](../../../visual-basic/language-reference/queries/skip-clause.md)
- [Klauzule Take](../../../visual-basic/language-reference/queries/take-clause.md)
- [Klauzule Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Klauzule Take While](../../../visual-basic/language-reference/queries/take-while-clause.md)
