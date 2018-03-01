---
title: "Distinct – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6ed92d5d601c1ec329728346ac881c4fa2bad8aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="distinct-clause-visual-basic"></a>Distinct – klauzule (Visual Basic)
Omezuje hodnoty aktuální proměnnou rozsahu eliminovat duplicitní hodnoty v klauzulích následné dotazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Distinct  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `Distinct` klauzule, která vrátí seznam jedinečných položek. `Distinct` Klauzule způsobí, že dotaz ignoroval výsledky duplicitní dotazu. `Distinct` Klauzule platí pro duplicitní hodnoty pro všechny vrátí pole určeného `Select` klauzule. Pokud žádné `Select` je zadána klauzule, `Distinct` klauzule se použije pro proměnnou rozsahu pro dotaz v identifikovat `From` klauzule. Pokud proměnná rozsahu není typ nedá změnit, dotaz pouze ignorovat výsledku dotazu, pokud všechny členy typu odpovídají stávající výsledek dotazu.  
  
## <a name="example"></a>Příklad  
 Následující výraz dotazu spojí seznamu zákazníků a seznamu objednávek zákazníků. `Distinct` Klauzule je součástí vrátí seznam jedinečných zákaznických názvy a pořadí kalendářní data.  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v jazyku Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Dotazy](../../../visual-basic/language-reference/queries/queries.md)  
 [From – klauzule](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Select – klauzule](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Kde – klauzule](../../../visual-basic/language-reference/queries/where-clause.md)
