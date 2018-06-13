---
title: Distinct – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 4b0ce12f6361d3dc6e5cc3601e96fc3a9bcf3841
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603974"
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
 [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
