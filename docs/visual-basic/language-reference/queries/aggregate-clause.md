---
title: Aggregate – klauzule (Visual Basic)
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
ms.openlocfilehash: a26ea220a807d3158d6874e2127db9a2f280a10c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547089"
---
# <a name="aggregate-clause-visual-basic"></a>Aggregate – klauzule (Visual Basic)
Použije jeden nebo více agregačních funkcí na kolekci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`element`|Povinný parametr. Proměnné použité k iteraci v rámci elementů kolekce.|  
|`type`|Volitelné. Typ `element`. Pokud není zadán žádný typ. typ `element` je odvozen z `collection`.|  
|`collection`|Povinný parametr. Odkazuje na kolekci, které se má operace provést.|  
|`clause`|Volitelné. Jeden nebo více klauzulemi dotazu, například `Where` klauzule, pro upřesnění výsledků dotazu použití klauzule aggregate nebo klauzule.|  
|`expressionList`|Povinný parametr. Jeden nebo více oddělených čárkou výrazů, které identifikují agregační funkce má být použita ke kolekci. Agregační funkce k určení názvu členu výsledku dotazu, můžete použít jako alias. Pokud žádný alias je zadaný, použije se název agregační funkce. Příklady najdete v části o agregačních funkcích dále v tomto tématu.|  
  
## <a name="remarks"></a>Poznámky  
 `Aggregate` Klauzule je možné zahrnout agregačních funkcí v dotazech. Agregační funkce provádět kontroly a výpočty v rámci sady hodnoty a vrátí jednu hodnotu. Vypočítaná hodnota můžete přistupovat pomocí členem typ výsledku dotazu. Jsou standardní agregační funkce, které můžete použít `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, a `Sum` funkce. Tyto funkce jsou zkušenosti vývojáře, kteří znají agregace v SQL. Jsou popsány v následující části tohoto tématu.  
  
 Výsledek agregační funkce je zahrnutá ve výsledku dotazu. jako pole s typem výsledku dotazu. Můžete zadat jako alias pro výsledek agregační funkce k zadání názvu členem typu výsledku dotazu, která bude obsahovat agregovanou hodnotu. Pokud žádný alias je zadaný, použije se název agregační funkce.  
  
 `Aggregate` Začít klauzule dotazu, nebo může být zahrnut jako další klauzule v dotazu. Pokud `Aggregate` začíná klauzulí dotazu, výsledkem je jediná hodnota, která je výsledkem zadanou v agregační funkci `Into` klauzuli. Pokud je zadán více než jeden agregační funkci v `Into` klauzule, dotaz vrátí jeden typ s samostatné vlastností odkazují na výsledek každého agregační funkce `Into` klauzuli. Pokud `Aggregate` klauzule je dostupná jako další klauzule dotazu, typ vrácený v kolekci dotazu bude mít samostatné vlastnosti a odkazují na výsledek každého agregační funkce `Into` klauzuli.  
  
## <a name="aggregate-functions"></a>Agregační funkce

Toto jsou standardní agregační funkce, které lze použít s `Aggregate` klauzuli.  
  
### <a name="all"></a>Všechny

Vrátí `true` Pokud všechny prvky v kolekci splňují zadanou podmínku; v opačném případě vrátí `false`. Následuje příklad:

[!code-vb[VbSimpleQuerySamples#5](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_1.vb)]

### <a name="any"></a>Jakýkoli

Vrátí `true` Pokud libovolný prvek v kolekci splňuje zadanou podmínku; v opačném případě vrátí `false`. Následuje příklad:

[!code-vb[VbSimpleQuerySamples#6](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_2.vb)]

### <a name="average"></a>Průměr

Vypočítá průměr všech prvků v kolekci nebo vypočítá zadaný výraz pro všechny elementy v kolekci. Následuje příklad:

[!code-vb[VbSimpleQuerySamples#7](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_3.vb)]

### <a name="count"></a>Počet

Vrátí počet prvků v kolekci. Můžete zadat volitelný `Boolean` výraz ke zjištění počtu prvků v kolekci, které splňují podmínku. Následuje příklad:

[!code-vb[VbSimpleQuerySamples#8](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_4.vb)]

### <a name="group"></a>Skupina

Odkazuje na výsledky dotazu, které jsou seskupeny kvůli `Group By` nebo `Group Join` klauzuli. `Group` Funkce je platná pouze v `Into` klauzuli `Group By` nebo `Group Join` klauzuli. Další informace a příklady najdete v tématu [klauzule Group](../../../visual-basic/language-reference/queries/group-by-clause.md) a [Group Join – klauzule](../../../visual-basic/language-reference/queries/group-join-clause.md).

### <a name="longcount"></a>LongCount

Vrátí počet prvků v kolekci. Můžete zadat volitelný `Boolean` výraz ke zjištění počtu prvků v kolekci, které splňují podmínku. Vrátí výsledek jako `Long`. Příklad najdete v tématu `Count` agregační funkce.

### <a name="max"></a>Maximum

Vypočítá maximální hodnotu z kolekce nebo vypočítá zadaný výraz pro všechny elementy v kolekci. Následuje příklad:

[!code-vb[VbSimpleQuerySamples#9](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_5.vb)]

### <a name="min"></a>Minimum

Vypočítá minimální hodnotu z kolekce nebo vypočítá zadaný výraz pro všechny elementy v kolekci. Následuje příklad:

[!code-vb[VbSimpleQuerySamples#10](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_6.vb)]

### <a name="sum"></a>Součet

Vypočítá součet všech prvků v kolekci nebo vypočítá zadaný výraz pro všechny elementy v kolekci. Následuje příklad:

[!code-vb[VbSimpleQuerySamples#15](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_7.vb)]

## <a name="example"></a>Příklad  

Následující příklad ukazuje způsob použití `Aggregate` klauzule k aplikaci agregačních funkcí na výsledek dotazu.  
  
 [!code-vb[VbSimpleQuerySamples#4](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_8.vb)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>Vytvoření uživatelsky definované agregační funkce

 Přidáním rozšiřující metody, které můžete zahrnout vlastní agregační funkce ve výrazu dotazu <xref:System.Collections.Generic.IEnumerable%601> typu. Vlastní metoda pak můžete provádět operaci vyčíslitelné kolekce, která je popsána agregační funkce nebo výpočtu. Další informace o metodách rozšíření naleznete v tématu [rozšiřující metody](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
 Například následující příklad ukazuje vlastní agregační funkce, která vypočítá Medián kolekci čísel. Existují dvě přetížení `Median` – metoda rozšíření. První přetížení přijímá jako vstup, kolekci typu `IEnumerable(Of Double)`. Pokud `Median` agregační funkce se volá pro pole dotazu s typem `Double`, tato metoda bude volána. Druhé přetížení `Median` metody mohou být předány žádné obecného typu. Obecné přetížení `Median` metoda přijímá druhý parametr, který odkazuje `Func(Of T, Double)` výraz lambda definoval se projekt hodnota pro typ (z kolekce) jako odpovídající hodnotu typu `Double`. Potom postoupí výpočtu střední hodnotu do jiné přetížení `Median` metody. Další informace o výrazech lambda naleznete v tématu [výrazy Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbSimpleQuerySamples#18](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_9.vb)]  
  
 Následující příklad ukazuje ukázkové dotazy, které volají `Median` agregační funkce na kolekci typu `Integer`a kolekce typu `Double`. Dotaz, který volá `Median` agregační funkce na kolekci typu `Double` volá přetížení `Median` metody, která přijímá jako vstup, kolekci typu `Double`. Dotaz, který volá `Median` agregační funkce na kolekci typu `Integer` volá obecné přetížení `Median` metody.  
  
 [!code-vb[VbSimpleQuerySamples#19](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_10.vb)]  
  
## <a name="see-also"></a>Viz také:

- [Úvod do LINQ v JAZYKU Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
- [Klauzule Group By](../../../visual-basic/language-reference/queries/group-by-clause.md)
