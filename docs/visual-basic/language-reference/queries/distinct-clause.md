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
ms.openlocfilehash: fbca9fa8aa227d8d5b6488bef179f4bda08bb38c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830055"
---
# <a name="distinct-clause-visual-basic"></a>Distinct – klauzule (Visual Basic)
Omezí hodnoty aktuální proměnnou rozsahu eliminovaly duplicitní hodnoty v klauzulích následné dotazování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Distinct  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `Distinct` klauzule, která vrátí seznam jedinečných položek. `Distinct` Klauzule způsobí, že dotaz ignorovat duplicitní dotaz výsledky. `Distinct` Klauzule platí pro duplicitní hodnoty pro všechny vrátí pole určená `Select` klauzuli. Pokud ne `Select` není zadána klauzule `Distinct` klauzule platí pro proměnnou rozsahu uvedené v dotazu `From` klauzuli. Pokud proměnná rozsahu není neumlčitelným typem, dotaz pouze ignorovat výsledku dotazu, pokud všechny členy typu odpovídají existující výsledku dotazu.  
  
## <a name="example"></a>Příklad  
 Následující výraz dotaz spojí seznam zákazníků a seznam objednávek zákazníků. `Distinct` Klauzule je součástí a vrátí seznam jedinečných zákaznických názvy a pořadí data.  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a>Viz také:

- [Úvod do LINQ v JAZYKU Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
