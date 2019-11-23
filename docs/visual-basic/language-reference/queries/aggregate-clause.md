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
ms.openlocfilehash: 5aa4b9afea4b6b26b853d4f4f6d4c8db08554e19
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350874"
---
# <a name="aggregate-clause-visual-basic"></a>Aggregate – klauzule (Visual Basic)
Applies one or more aggregate functions to a collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`element`|Požadováno. Variable used to iterate through the elements of the collection.|  
|`type`|Volitelné. The type of `element`. If no type is specified, the type of `element` is inferred from `collection`.|  
|`collection`|Požadováno. Refers to the collection to operate on.|  
|`clause`|Volitelné. One or more query clauses, such as a `Where` clause, to refine the query result to apply the aggregate clause or clauses to.|  
|`expressionList`|Požadováno. One or more comma-delimited expressions that identify an aggregate function to apply to the collection. You can apply an alias to an aggregate function to specify a member name for the query result. If no alias is supplied, the name of the aggregate function is used. For examples, see the section about aggregate functions later in this topic.|  
  
## <a name="remarks"></a>Poznámky  
 The `Aggregate` clause can be used to include aggregate functions in your queries. Aggregate functions perform checks and computations over a set of values and return a single value. You can access the computed value by using a member of the query result type. The standard aggregate functions that you can use are the `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, and `Sum` functions. These functions are familiar to developers who are familiar with aggregates in SQL. They are described in the following section of this topic.  
  
 The result of an aggregate function is included in the query result as a field of the query result type. You can supply an alias for the aggregate function result to specify the name of the member of the query result type that will hold the aggregate value. If no alias is supplied, the name of the aggregate function is used.  
  
 The `Aggregate` clause can begin a query, or it can be included as an additional clause in a query. If the `Aggregate` clause begins a query, the result is a single value that is the result of the aggregate function specified in the `Into` clause. If more than one aggregate function is specified in the `Into` clause, the query returns a single type with a separate property to reference the result of each aggregate function in the `Into` clause. If the `Aggregate` clause is included as an additional clause in a query, the type returned in the query collection will have a separate property to reference the result of each aggregate function in the `Into` clause.  
  
## <a name="aggregate-functions"></a>Agregační funkce

The following are the standard aggregate functions that can be used with the `Aggregate` clause.  
  
### <a name="all"></a>Všechny

Returns `true` if all elements in the collection satisfy a specified condition; otherwise returns `false`. The following is an example:

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a>Any

Returns `true` if any element in the collection satisfies a specified condition; otherwise returns `false`. The following is an example:

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a>Average

Computes the average of all elements in the collection, or computes a supplied expression for all elements in the collection. The following is an example:

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a>Count

Counts the number of elements in the collection. You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition. The following is an example:

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a>Skupina

Refers to query results that are grouped as a result of a `Group By` or `Group Join` clause. The `Group` function is valid only in the `Into` clause of a `Group By` or `Group Join` clause. For more information and examples, see [Group By Clause](../../../visual-basic/language-reference/queries/group-by-clause.md) and [Group Join Clause](../../../visual-basic/language-reference/queries/group-join-clause.md).

### <a name="longcount"></a>LongCount

Counts the number of elements in the collection. You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition. Returns the result as a `Long`. For an example, see the `Count` aggregate function.

### <a name="max"></a>Max

Computes the maximum value from the collection, or computes a supplied expression for all elements in the collection. The following is an example:

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a>Min

Computes the minimum value from the collection, or computes a supplied expression for all elements in the collection. The following is an example:

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a>Sum

Computes the sum of all elements in the collection, or computes a supplied expression for all elements in the collection. The following is an example:

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a>Příklad  

The following example shows how to use the `Aggregate` clause to apply aggregate functions to a query result.  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>Creating User-Defined Aggregate Functions

 You can include your own custom aggregate functions in a query expression by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> type. Your custom method can then perform a calculation or operation on the enumerable collection that has referenced your aggregate function. For more information about extension methods, see [Extension Methods](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
 For example, the following example shows a custom aggregate function that calculates the median value of a collection of numbers. There are two overloads of the `Median` extension method. The first overload accepts, as input, a collection of type `IEnumerable(Of Double)`. If the `Median` aggregate function is called for a query field of type `Double`, this method will be called. The second overload of the `Median` method can be passed any generic type. The generic overload of the `Median` method takes a second parameter that references the `Func(Of T, Double)` lambda expression to project a value for a type (from a collection) as the corresponding value of type `Double`. It then delegates the calculation of the median value to the other overload of the `Median` method. For more information about lambda expressions, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 The following example shows sample queries that call the `Median` aggregate function on a collection of type `Integer`, and a collection of type `Double`. The query that calls the `Median` aggregate function on the collection of type `Double` calls the overload of the `Median` method that accepts, as input, a collection of type `Double`. The query that calls the `Median` aggregate function on the collection of type `Integer` calls the generic overload of the `Median` method.  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a>Viz také:

- [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
- [Klauzule Group By](../../../visual-basic/language-reference/queries/group-by-clause.md)
