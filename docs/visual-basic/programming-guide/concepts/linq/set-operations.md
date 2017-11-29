---
title: "Množinové operace (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2e30c521635326afeea4aad9ce932d5206d06c6d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="set-operations-visual-basic"></a>Množinové operace (Visual Basic)
Množinové operace v technologii LINQ naleznete v operacích dotazu, které produkují je sada výsledků dotazu, který je založen na přítomnosti nebo absenci ekvivalentní elementů v rámci stejné nebo samostatné kolekce (nebo sady).  
  
 Operátor metody standardní dotazů, které provádět operace set jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka Visual Basic|Další informace|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Distinct|Odebere duplicitní hodnoty z kolekce.|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|S výjimkou|Vrátí množinových rozdílů, což znamená elementy jednu kolekci, která nejsou uvedena v druhé kolekci.|Nelze použít.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|Intersect|Vrátí průnik sady, což znamená elementy, které se zobrazují v každé dvě kolekce.|Nelze použít.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|Unie|Vrátí sjednocení sady, což znamená jedinečný elementy, které se zobrazují v některém z dvě kolekce.|Nelze použít.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a>Porovnání množinové operace  
  
### <a name="distinct"></a>Distinct  
 Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metodu posloupnost znaků. Vrácený pořadí obsahuje jedinečný elementy ze vstupní pořadí.  
  
 ![Obrázek znázorňující chování Distinct &#40; &#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Odlišné")  
  
### <a name="except"></a>S výjimkou  
 Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>. Vrácený pořadí obsahuje pouze elementy z první vstupní pořadí, které nejsou v druhé vstupní pořadí.  
  
 ![Obrázek znázorňující akce s výjimkou &#40; &#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/except.png "s výjimkou")  
  
### <a name="intersect"></a>Intersect  
 Následující obrázek znázorňuje chování <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>. Vrácený pořadí obsahuje prvky, které jsou společné pro objekty vstupních sekvencí.  
  
 ![Obrázek znázorňující průnik dvou sekvencí. ] (../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")  
  
### <a name="union"></a>Unie  
 Následující obrázek znázorňuje sjednocovací operace na dvě sekvence znaků. Vrácený pořadí obsahuje jedinečný prvky z obou vstupních sekvencí.  
  
 ![Obrázek znázorňující sjednocení dvou pořadí. ] (../../../../csharp/programming-guide/concepts/linq/media/union.png "Sjednocení")  
  
## <a name="query-expression-syntax-example"></a>Příklad syntaxe výrazu dotazu  
 Následující příklad používá `Distinct` klauzuli v dotazu LINQ vrácení jedinečná čísla z seznam celých čísel.  
  
 [!code-vb[CsLINQSetOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/set-operations_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq>  
 [Přehled standardních operátorů dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [DISTINCT – klauzule](../../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [Postupy: kombinace a porovnávání kolekcí řetězců (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)  
 [Postupy: hledání množinových rozdílů mezi dvěma seznamy (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
