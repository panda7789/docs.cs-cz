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
ms.openlocfilehash: 33680f49247b3b2a6082b3a6b27ca64f8401e42d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396178"
---
# <a name="from-clause-visual-basic"></a>From – klauzule (Visual Basic)
Určuje jednu nebo více proměnných rozsahu a kolekci pro dotaz.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a>Součásti  
  
|Pojem|Definice|  
|---|---|  
|`element`|Povinná hodnota. *Proměnná rozsahu* používaná k iterování prostřednictvím prvků kolekce. Proměnná rozsahu se používá pro odkazování na každého člena v, `collection` protože dotaz prochází pomocí `collection` . Musí se jednat o vyčíslitelného typu.|  
|`type`|Nepovinný parametr. Typ `element` . Pokud `type` není zadán, typ `element` je odvozen z `collection` .|  
|`collection`|Povinná hodnota. Odkazuje na kolekci, do které se má dotazovat. Musí se jednat o vyčíslitelného typu.|  
  
## <a name="remarks"></a>Poznámky  
 `From`Klauzule slouží k identifikaci zdrojových dat pro dotaz a proměnné, které se používají k odkazování na element ze zdrojové kolekce. Tyto proměnné se nazývají *proměnné rozsahu*. `From`Klauzule je vyžadována pro dotaz s výjimkou případů, kdy `Aggregate` je použita klauzule k identifikaci dotazu, který vrací pouze agregované výsledky. Další informace naleznete v tématu [klauzule Aggregate](aggregate-clause.md).  
  
 V dotazu můžete zadat více `From` klauzulí k identifikaci více kolekcí, které mají být spojeny. Pokud je zadáno více kolekcí, jsou iterované na nezávisle, nebo se k nim můžete připojit, pokud jsou v relaci. Kolekce můžete spojit implicitně pomocí `Select` klauzule nebo explicitně pomocí `Join` `Group Join` klauzulí or. Alternativně můžete zadat více proměnných rozsahu a kolekcí v rámci jedné `From` klauzule, přičemž každá související proměnná rozsahu a kolekce je oddělená od ostatních o čárku. Následující příklad kódu ukazuje obě možnosti syntaxe `From` klauzule.  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 `From`Klauzule definuje rozsah dotazu, který je podobný oboru `For` smyčky. Proto musí každá `element` Proměnná rozsahu v oboru dotazu mít jedinečný název. Vzhledem k tomu, že lze zadat více `From` klauzulí pro dotaz, následné `From` klauzule mohou odkazovat na proměnné rozsahu v `From` klauzuli nebo mohou odkazovat na proměnné rozsahu v předchozí `From` klauzuli. Například následující příklad ukazuje vnořenou `From` klauzuli, kde kolekce v druhé klauzuli je založena na vlastnosti proměnné rozsahu v první klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 `From`U každé klauzule může následovat jakákoli kombinace dalších klauzulí dotazu pro upřesnění dotazu. Dotaz můžete upřesnit následujícími způsoby:  
  
- Použijte implicitně kombinaci více kolekcí pomocí `From` klauzulí a `Select` nebo explicitně pomocí `Join` `Group Join` klauzulí or.  
  
- Pomocí `Where` klauzule můžete filtrovat výsledek dotazu.  
  
- Seřaďte výsledek pomocí `Order By` klauzule.  
  
- Seskupte podobné výsledky společně pomocí `Group By` klauzule.  
  
- Použijte `Aggregate` klauzuli k identifikaci agregačních funkcí pro vyhodnocení celého výsledku dotazu.  
  
- Použijte `Let` klauzuli pro představení proměnné iterace, jejíž hodnota je určena výrazem namísto kolekce.  
  
- Použijte `Distinct` klauzuli pro ignorování duplicitních výsledků dotazu.  
  
- Identifikujte části výsledku, které mají být vráceny pomocí `Skip` `Take` klauzulí,, `Skip While` a `Take While` .  
  
## <a name="example"></a>Příklad  
 Následující výraz dotazu používá `From` klauzuli pro deklaraci proměnné rozsahu `cust` pro každý `Customer` objekt v `customers` kolekci. `Where`Klauzule používá proměnnou rozsahu k omezení výstupu na zákazníky ze zadané oblasti. `For Each`Smyčka zobrazí název společnosti pro každého zákazníka ve výsledku dotazu.  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a>Viz také

- [Dotazy](index.md)
- [Představení technologie LINQ v jazyce Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [For Each...Next – příkaz](../statements/for-each-next-statement.md)
- [For...Next – příkaz](../statements/for-next-statement.md)
- [Klauzule SELECT](select-clause.md)
- [Klauzule WHERE](where-clause.md)
- [Aggregate – klauzule](aggregate-clause.md)
- [Distinct – klauzule](distinct-clause.md)
- [Klauzule JOIN](join-clause.md)
- [Group Join – klauzule](group-join-clause.md)
- [Order By – klauzule](order-by-clause.md)
- [Let – klauzule](let-clause.md)
- [Skip – klauzule](skip-clause.md)
- [Take – klauzule](take-clause.md)
- [Skip While – klauzule](skip-while-clause.md)
- [Take While – klauzule](take-while-clause.md)
