---
title: Aggregate – klauzule
ms.date: 08/28/2018
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: 326c3306368ceca2122e912556efd84e4bfef1f1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84412998"
---
# <a name="aggregate-clause-visual-basic"></a>Aggregate – klauzule (Visual Basic)
Aplikuje jednu nebo více agregačních funkcí na kolekci.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a>Součásti  
  
|Pojem|Definice|  
|---|---|  
|`element`|Povinná hodnota. Proměnná použitá pro iteraci prvků kolekce.|  
|`type`|Nepovinný parametr. Typ `element` . Pokud není zadán žádný typ, typ `element` je odvozen z `collection` .|  
|`collection`|Povinná hodnota. Odkazuje na kolekci, na které se má pracovat.|  
|`clause`|Nepovinný parametr. Jedna nebo více klauzulí dotazu, jako je například `Where` klauzule, pro upřesnění výsledku dotazu pro použití agregační klauzule nebo klauzule na.|  
|`expressionList`|Povinná hodnota. Jeden nebo více výrazů oddělených čárkami, které identifikují agregační funkci, která se má použít pro kolekci. Můžete použít alias pro agregační funkci a zadat název člena pro výsledek dotazu. Pokud není zadán žádný alias, je použit název agregační funkce. Příklady najdete v části o agregačních funkcích dále v tomto tématu.|  
  
## <a name="remarks"></a>Poznámky  
 `Aggregate`Klauzuli lze použít k zahrnutí agregačních funkcí do dotazů. Agregační funkce provádějí kontroly a výpočty přes sadu hodnot a vracejí jedinou hodnotu. K vypočtené hodnotě můžete přistupovat pomocí členu typu výsledku dotazu. Standardní agregační funkce, které lze použít, jsou `All` funkce, `Any` , `Average` , `Count` , `LongCount` , `Max` , `Min` a `Sum` . Tyto funkce jsou známé vývojářům, kteří jsou obeznámeni s agregacemi v SQL. Jsou popsány v následující části tohoto tématu.  
  
 Výsledek agregační funkce je zahrnut ve výsledku dotazu jako pole typu výsledku dotazu. Můžete zadat alias pro výsledek agregační funkce pro určení názvu člena typu výsledku dotazu, který bude obsahovat agregovanou hodnotu. Pokud není zadán žádný alias, je použit název agregační funkce.  
  
 `Aggregate`Klauzule může spustit dotaz nebo může být obsažena jako další klauzule v dotazu. Pokud `Aggregate` klauzule zahájí dotaz, výsledkem je jediná hodnota, která je výsledkem agregační funkce zadané v `Into` klauzuli. Je-li v klauzuli zadána více než jedna agregační funkce `Into` , dotaz vrátí jeden typ s samostatnou vlastností, aby odkazoval na výsledek každé agregační funkce v `Into` klauzuli. Pokud `Aggregate` je klauzule obsažena v dotazu jako další klauzule, typ vrácený v kolekci dotazů bude mít samostatnou vlastnost, která bude odkazovat na výsledek každé agregační funkce v `Into` klauzuli.  
  
## <a name="aggregate-functions"></a>Agregační funkce

Níže jsou uvedené standardní agregační funkce, které lze použít s `Aggregate` klauzulí.  
  
### <a name="all"></a>Vše

Vrátí, `true` zda všechny prvky v kolekci odpovídají zadané podmínce. v opačném případě vrátí `false` . Například:

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a>Všechny

Vrátí `true` , zda kterýkoli prvek v kolekci splňuje zadanou podmínku. v opačném případě vrátí `false` . Například:

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a>Průměr

Vypočítá průměr všech prvků v kolekci nebo vypočítá zadaný výraz pro všechny prvky v kolekci. Například:

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a>Počet

Spočítá počet prvků v kolekci. Můžete zadat volitelný výraz, který bude `Boolean` počítat pouze počet prvků v kolekci, které splní podmínku. Například:

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a>Skupina

Odkazuje na výsledky dotazu, které jsou seskupeny jako výsledek `Group By` klauzule OR `Group Join` . `Group`Funkce je platná pouze v `Into` klauzuli `Group By` `Group Join` klauzule OR. Další informace a příklady najdete v tématu [klauzule GROUP by](group-by-clause.md) a [Group Join](group-join-clause.md).

### <a name="longcount"></a>LongCount

Spočítá počet prvků v kolekci. Můžete zadat volitelný výraz, který bude `Boolean` počítat pouze počet prvků v kolekci, které splní podmínku. Vrátí výsledek jako `Long` . Příklad naleznete v `Count` agregační funkci.

### <a name="max"></a>Maximum

Vypočítá maximální hodnotu z kolekce nebo vypočítá zadaný výraz pro všechny prvky v kolekci. Například:

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a>Minimum

Vypočítá minimální hodnotu z kolekce nebo vypočítá zadaný výraz pro všechny prvky v kolekci. Například:

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a>Součet

Vypočítá součet všech prvků v kolekci nebo vypočítá zadaný výraz pro všechny prvky v kolekci. Například:

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a>Příklad  

Následující příklad ukazuje, jak použít `Aggregate` klauzuli pro použití agregačních funkcí pro výsledek dotazu.  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>Vytváření agregačních funkcí definovaných uživatelem

 Do výrazu dotazu můžete přidat vlastní agregační funkce přidáním rozšiřujících metod do <xref:System.Collections.Generic.IEnumerable%601> typu. Vaše vlastní metoda potom může provést výpočet nebo operaci na vyčíslitelné kolekci, která odkazovala na agregační funkci. Další informace o metodách rozšíření naleznete v tématu [metody rozšíření](../../programming-guide/language-features/procedures/extension-methods.md).  
  
 Například následující příklad ukazuje vlastní agregační funkci, která vypočítá medián hodnoty kolekce čísel. Existují dvě přetížení `Median` metody rozšíření. První přetížení akceptuje jako vstup kolekci typu `IEnumerable(Of Double)` . Pokud `Median` je agregační funkce volána pro pole dotazu typu `Double` , bude tato metoda volána. Druhé přetížení `Median` metody může být předáno libovolným obecným typem. Obecné přetížení `Median` metody přebírá druhý parametr, který odkazuje na `Func(Of T, Double)` výraz lambda, aby prokáže hodnotu pro typ (z kolekce) jako odpovídající hodnotu typu `Double` . Poté deleguje výpočet střední hodnoty k druhé přetížení `Median` metody. Další informace o výrazech lambda naleznete v tématu [lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 Následující příklad ukazuje Ukázkové dotazy, které volají `Median` agregační funkci na kolekci typu `Integer` a kolekci typu `Double` . Dotaz, který volá `Median` agregační funkci na kolekci typu `Double` volá přetížení `Median` metody, která přijímá jako vstup, kolekci typu `Double` . Dotaz, který volá `Median` agregační funkci na kolekci typu, `Integer` volá obecné přetížení `Median` metody.  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a>Viz také

- [Představení technologie LINQ v jazyce Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](index.md)
- [Klauzule SELECT](select-clause.md)
- [Klauzule FROM](from-clause.md)
- [Klauzule WHERE](where-clause.md)
- [Group By – klauzule](group-by-clause.md)
