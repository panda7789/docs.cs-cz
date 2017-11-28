---
title: Segmentace dat (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0ea305a67765e1b11ceebbf65c48a685024a41f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="partitioning-data-visual-basic"></a>Segmentace dat (Visual Basic)
Vytváření oddílů v technologii LINQ odkazuje na operaci dělení vstupní pořadí na dva oddíly bez Změna uspořádání elementy a potom vrátí jeden z oddílů.  
  
 Následující obrázek znázorňuje výsledky tři různé rozdělení operace na posloupnost znaků. První operace vrátí první tři elementy v pořadí. Druhá operace přeskočí první tři elementy a vrátí zbývající elementy. Třetí operaci přeskočí první dva elementy v pořadí a vrátí následující tři elementy.  
  
 ![LINQ dělení Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")  
  
 V následující části jsou uvedené metody operátor standardní dotazů, které oddílu pořadí.  
  
## <a name="operators"></a>Operátory  
  
|Název operátoru|Popis|Syntaxe výrazu dotazu jazyka Visual Basic|Další informace|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|Skip|Přeskočí elementy až zadané pozici v pořadí.|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile|Vynechá prvky podle funkce predikátu, dokud element nesplňuje podmínky.|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Získá prvků až zadané pozici v pořadí.|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile|Získá prvků podle funkce predikátu, dokud element nesplňuje podmínky.|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazu dotazu  
  
### <a name="skip"></a>Skip  
 Následující příklad kódu používá `Skip` klauzuli v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] přeskočit přes první čtyři řetězců v pole řetězců před vrácením zbývající řetězce v poli.  
  
 [!code-vb[CsLINQPartitioning#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]  
  
### <a name="skipwhile"></a>SkipWhile  
 Následující příklad kódu používá `Skip While` klauzuli v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] přeskočit řetězců v pole při první písmeno řetězce je "a". Zbývající řetězce v poli, jsou vráceny.  
  
 [!code-vb[CsLINQPartitioning#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]  
  
### <a name="take"></a>Take  
 Následující příklad kódu používá `Take` klauzuli v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] vracet první dva řetězce na pole řetězců.  
  
 [!code-vb[CsLINQPartitioning#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]  
  
### <a name="takewhile"></a>TakeWhile  
 Následující příklad kódu používá `Take While` klauzuli v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] vrácení řetězce z pole Délka řetězce je pět nebo méně.  
  
 [!code-vb[CsLINQPartitioning#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq>  
 [Přehled standardních operátorů dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Skip – klauzule](../../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Skip While – klauzule](../../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Take – klauzule](../../../../visual-basic/language-reference/queries/take-clause.md)  
 [Take While – klauzule](../../../../visual-basic/language-reference/queries/take-while-clause.md)
