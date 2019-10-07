---
title: From – klauzule (Visual Basic)
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
ms.openlocfilehash: 781902f1bf28bd029c8d9825aee155a6691cbae9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004777"
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
|`element`|Požadováno. *Proměnná rozsahu* používaná k iterování prostřednictvím prvků kolekce. Proměnná rozsahu se používá pro odkazování na každého člena `collection`, protože dotaz prochází pomocí `collection`. Musí se jednat o vyčíslitelného typu.|  
|`type`|Volitelné. Typ `element`. Pokud není zadán žádný `type`, typ `element` je odvozen z `collection`.|  
|`collection`|Požadováno. Odkazuje na kolekci, do které se má dotazovat. Musí se jednat o vyčíslitelného typu.|  
  
## <a name="remarks"></a>Poznámky  
 Klauzule `From` slouží k identifikaci zdrojových dat pro dotaz a proměnné, které se používají k odkazování na element ze zdrojové kolekce. Tyto proměnné se nazývají *proměnné rozsahu*. Klauzule `From` je vyžadována pro dotaz s výjimkou případů, kdy je použita klauzule `Aggregate` k identifikaci dotazu, který vrací pouze agregované výsledky. Další informace naleznete v tématu [klauzule Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 V dotazu můžete zadat více klauzulí `From` pro identifikaci více kolekcí, které mají být spojeny. Pokud je zadáno více kolekcí, jsou iterované na nezávisle, nebo se k nim můžete připojit, pokud jsou v relaci. Kolekce můžete spojit implicitně pomocí klauzule `Select` nebo explicitně pomocí klauzulí `Join` nebo `Group Join`. Alternativně můžete v jedné klauzuli `From` zadat více proměnných a kolekcí rozsahu s každou příslušnou proměnnou rozsahu a kolekci oddělenou od ostatních po čárku. Následující příklad kódu ukazuje obě možnosti syntaxe pro klauzuli `From`.  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 Klauzule `From` definuje obor dotazu, který je podobný oboru smyčky `For`. Proto každá proměnná rozsahu `element` v oboru dotazu musí mít jedinečný název. Vzhledem k tomu, že pro dotaz lze zadat více klauzulí `From`, mohou další klauzule `From` odkazovat na proměnné rozsahu v klauzuli `From` nebo mohou odkazovat na proměnné rozsahu v předchozí klauzuli `From`. Například následující příklad ukazuje vnořenou klauzuli `From`, kde kolekce v druhé klauzuli je založena na vlastnosti proměnné rozsahu v první klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 Každou klauzuli `From` můžete za účelem upřesnění dotazu zadat libovolnou kombinaci dalších klauzulí dotazu. Dotaz můžete upřesnit následujícími způsoby:  
  
- Pomocí klauzulí `From` a `Select`, nebo explicitně pomocí klauzulí `Join` nebo `Group Join`, je několik kolekcí implicitně zkombinovat.  
  
- K filtrování výsledku dotazu použijte klauzuli `Where`.  
  
- Seřaďte výsledek pomocí klauzule `Order By`.  
  
- Seskupte podobné výsledky společně pomocí klauzule `Group By`.  
  
- Použijte klauzuli `Aggregate` k identifikaci agregačních funkcí pro vyhodnocení celého výsledku dotazu.  
  
- Pomocí klauzule `Let` zaveďte proměnnou iterace, jejíž hodnota je určena výrazem namísto kolekce.  
  
- K ignorování duplicitních výsledků dotazu použijte klauzuli `Distinct`.  
  
- Identifikujte části výsledku, které se mají vrátit, pomocí klauzulí `Skip`, `Take`, `Skip While` a `Take While`.  
  
## <a name="example"></a>Příklad  
 Následující výraz dotazu používá klauzuli `From` k deklaraci proměnné rozsahu `cust` pro každý objekt `Customer` v kolekci `customers`. Klauzule `Where` používá proměnnou rozsahu k omezení výstupu na zákazníky ze zadané oblasti. Cyklus `For Each` zobrazuje název společnosti pro každého zákazníka ve výsledku dotazu.  
  
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
