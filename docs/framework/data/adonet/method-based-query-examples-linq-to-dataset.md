---
title: "Příklady dotazů – metoda (LINQ na DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d340775c-7f39-4087-a290-5cbec6cfa68e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 313364f71c463a320816bb92113f3b720146fe25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="method-based-query-examples-linq-to-dataset"></a>Příklady dotazů – metoda (LINQ na DataSet)
Tato část obsahuje [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] programování příklady v syntaxe dotazu na základě metod, které používají standardní operátory dotazu. <xref:System.Data.DataSet> Použít v těchto příkladech je vyplněný pomocí `FillDataSet` metoda, která je určena v [načítání dat do datové sady](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md). Další informace najdete v tématu [standardní přehled operátory dotazu](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Projekce](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-projection.md)  
 V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Select%2A> a <xref:System.Linq.Enumerable.SelectMany%2A> metody pro dotazování <xref:System.Data.DataSet>.  
  
 [Segmentace](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-partitioning-linq.md)  
 V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Skip%2A> a <xref:System.Linq.Enumerable.Take%2A> metody pro dotazování <xref:System.Data.DataSet> a rozdělit na oddíly výsledky.  
  
 [Řazení](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
 V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, a <xref:System.Linq.Enumerable.ThenByDescending%2A> metody pro dotazování <xref:System.Data.DataSet> a řazení výsledků.  
  
 [Množinové operátory](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-set-operators.md)  
 V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, a <xref:System.Linq.Enumerable.Union%2A> operátory provádět operace porovnání hodnota založená na sady řádků data.  
  
 [Operátory převodu](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-conversion-operators.md)  
 V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, a <xref:System.Linq.Enumerable.ToList%2A> metody okamžitě provést výrazu dotazu.  
  
 [Operátory elementů](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-element-operators.md)  
 V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.First%2A> a <xref:System.Linq.Enumerable.ElementAt%2A> metod k získání <xref:System.Data.DataRow> elementy z <xref:System.Data.DataSet>.  
  
 [Agregační operátory](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-aggregate-operators.md)  
 V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, a <xref:System.Linq.Enumerable.Sum%2A> metody pro dotazování <xref:System.Data.DataSet> a agregovat data.  
  
 [Spojení](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-join-linq-to-dataset.md)  
 V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.GroupJoin%2A> a <xref:System.Linq.Enumerable.Join%2A> metody pro dotazování <xref:System.Data.DataSet>.  
  
## <a name="see-also"></a>Viz také  
 [Příklady výrazů dotazů](../../../../docs/framework/data/adonet/query-expression-examples-linq-to-dataset.md)  
 [Příklady operátorů specifických pro datovou sadu](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)  
 [Příklady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
