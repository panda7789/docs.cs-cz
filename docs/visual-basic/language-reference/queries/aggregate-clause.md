---
title: Aggregate – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: 1db4b7fdcf9c8a38c2c49eca9d874eccea90ab1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="aggregate-clause-visual-basic"></a>Aggregate – klauzule (Visual Basic)
Jeden nebo více agregační funkce se vztahuje na kolekci.  
  
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
|`element`|Požadováno. Proměnná použít k iteraci v rámci prvků kolekce.|  
|`type`|Volitelné. Typ `element`. Pokud není zadán žádný typ., typ `element` je odvozeno z `collection`.|  
|`collection`|Požadováno. Odkazuje na kolekci má být použito.|  
|`clause`|Volitelné. Nejméně jeden dotaz klauzule, například `Where` klauzule upřesněte touto aggregate – klauzule nebo klauzule do výsledku dotazu.|  
|`expressionList`|Požadováno. Jeden nebo více oddělených čárkou výrazů identifikují agregační funkci chcete použít pro kolekci. Alias můžete použít pro agregační funkci zadat jméno člena pro výsledek dotazu. Pokud je zadaný žádný alias se používá název agregační funkci. Příklady najdete v části o agregační funkce později v tomto tématu.|  
  
## <a name="remarks"></a>Poznámky  
 `Aggregate` Klauzule lze zahrnout agregačních funkcí v dotazech. Agregační funkce provádět kontroly a výpočtů v rámci sady hodnot a vrátí jednu hodnotu. Vypočtená hodnota můžete přistupovat pomocí členem výsledný typ dotazu. Jsou standardní agregační funkce, které můžete použít `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, a `Sum` funkce. Tyto funkce jsou pro vývojáře, kteří mají zkušenosti se agregace v systému SQL. Jsou popsány v následující části tohoto tématu.  
  
 Výsledek agregační funkci je součástí výsledek dotazu jako pole výsledný typ dotazu. Můžete zadat alias pro výsledek agregační funkce zadat název člena výsledný typ dotazu, který bude obsahovat celkovou hodnotu. Pokud je zadaný žádný alias se používá název agregační funkci.  
  
 `Aggregate` Klauzule můžete začít dotazu, nebo může být zahrnuta jako další klauzuli v dotazu. Pokud `Aggregate` klauzule začne dotazu, výsledkem je jediná hodnota, která je výsledkem zadanou v agregační funkci `Into` klauzule. Pokud je zadán více než jeden agregační funkci v `Into` klauzule, dotaz vrátí jeden typ s samostatné vlastností tak, aby odkazovaly výsledek každé agregační funkci v `Into` klauzule. Pokud `Aggregate` klauzule je zahrnuta jako další klauzuli v dotazu, typ vrácený v kolekci dotazu bude mít samostatné vlastnost, která má odkazovat na výsledek každé agregační funkci v `Into` klauzule.  
  
## <a name="aggregate-functions"></a>Agregační funkce  
 Následující seznam popisuje standardní agregační funkce, které lze použít s `Aggregate` klauzule.  
  
|Funkce|Popis|  
|---|---|  
|`All`|Vrátí `true` Pokud všechny elementy v kolekci splňují zadanou podmínku; v opačném případě vrátí `false`. Tady je příklad:<br /><br /> [!code-vb[VbSimpleQuerySamples#5](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_1.vb)]|  
|`Any`|Vrátí `true` Pokud libovolný element v kolekci splňuje zadanou podmínku; v opačném případě vrátí `false`. Tady je příklad:<br /><br /> [!code-vb[VbSimpleQuerySamples#6](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_2.vb)]|  
|`Average`|Vypočítá průměrnou hodnotu všechny elementy v kolekci nebo ve výrazu výpočtů zadaný pro všechny elementy v kolekci. Tady je příklad:<br /><br /> [!code-vb[VbSimpleQuerySamples#7](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_3.vb)]|  
|`Count`|Spočítá počet elementů v kolekci. Můžete zadat volitelný `Boolean` výraz, který má určený počet elementů v kolekci, které splňují podmínku. Tady je příklad:<br /><br /> [!code-vb[VbSimpleQuerySamples#8](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_4.vb)]|  
|`Group`|Odkazuje na výsledky dotazu, které jsou seskupeny na základě těchto `Group By` nebo `Group Join` klauzule. `Group` Funkce je platná pouze v `Into` klauzuli `Group By` nebo `Group Join` klauzule. Další informace a příklady naleznete v tématu [skupiny pomocí klauzule](../../../visual-basic/language-reference/queries/group-by-clause.md) a [Group Join – klauzule](../../../visual-basic/language-reference/queries/group-join-clause.md).|  
|`LongCount`|Spočítá počet elementů v kolekci. Můžete zadat volitelný `Boolean` výraz, který má určený počet elementů v kolekci, které splňují podmínku. Vrátí výsledek jako `Long`. Příklad, naleznete v části `Count` agregační funkce.|  
|`Max`|Vypočítá maximální hodnota z kolekce nebo vypočítá zadaný výraz pro všechny elementy v kolekci. Tady je příklad:<br /><br /> [!code-vb[VbSimpleQuerySamples#9](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_5.vb)]|  
|`Min`|Vypočítá minimální hodnota z kolekce nebo vypočítá zadaný výraz pro všechny elementy v kolekci. Tady je příklad:<br /><br /> [!code-vb[VbSimpleQuerySamples#10](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_6.vb)]|  
|`Sum`|Vypočítá součet všech elementů v kolekci nebo vypočítá zadaný výraz pro všechny elementy v kolekci. Tady je příklad:<br /><br /> [!code-vb[VbSimpleQuerySamples#15](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_7.vb)]|  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak používat `Aggregate` klauzule pro použití agregační funkce výsledku dotazu.  
  
 [!code-vb[VbSimpleQuerySamples#4](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_8.vb)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>Vytváření vlastní agregační funkce  
 Přidáním rozšiřující metody, které můžete zahrnout vlastní agregační funkce ve výrazu dotazu <xref:System.Collections.Generic.IEnumerable%601> typu. Vlastní metoda pak můžete provádět výpočtu nebo operace na vyčíslitelná kolekci, která má odkazovat na agregační funkci. Další informace o metodách rozšíření najdete v tématu [rozšiřující metody](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
 Například následující příklad kódu ukazuje vlastní agregační funkce pro výpočet Medián kolekce čísel. Existují dvě přetížení `Median` metoda rozšíření. První přetížení přijme jako vstup, kolekci typu `IEnumerable(Of Double)`. Pokud `Median` agregační funkce je volána pro dotaz pole typu `Double`, tato metoda bude volána. Druhý přetížení `Median` metoda se dá předat všechny obecného typu. Obecné přetížení `Median` metoda přebírá druhý parametr, který odkazuje `Func(Of T, Double)` výrazu lambda do projektu typ (z kolekce) na hodnotu jako odpovídající hodnota typu `Double`. Potom postoupí výpočtu Medián další přetížení `Median` metoda. Další informace o výrazy lambda najdete v tématu [výrazy Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbSimpleQuerySamples#18](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_9.vb)]  
  
 Následující příklad ukazuje ukázkové dotazy, které volají kód `Median` agregační funkce na kolekci typu `Integer`a kolekci typu `Double`. Dotaz, který volá `Median` agregační funkce na kolekci typu `Double` volá přetížení `Median` metodu, která přijímá jako vstup, kolekci typu `Double`. Dotaz, který volá `Median` agregační funkce na kolekci typu `Integer` volá obecné přetížení `Median` metoda.  
  
 [!code-vb[VbSimpleQuerySamples#19](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_10.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v jazyku Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Dotazy](../../../visual-basic/language-reference/queries/queries.md)  
 [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Klauzule Group By](../../../visual-basic/language-reference/queries/group-by-clause.md)
