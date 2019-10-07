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
ms.openlocfilehash: e8d3e38261a04c4d29faab351d24d6710413b09a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004800"
---
# <a name="distinct-clause-visual-basic"></a>Distinct – klauzule (Visual Basic)
Omezuje hodnoty aktuální proměnné rozsahu tak, aby v následných klauzulích dotazu vyloučily duplicitní hodnoty.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a>Poznámky  
 Pomocí klauzule `Distinct` můžete vracet seznam jedinečných položek. Klauzule `Distinct` způsobí, že dotaz ignoruje výsledky duplicitních dotazů. Klauzule `Distinct` se vztahuje na duplicitní hodnoty všech vrácených polí určených klauzulí `Select`. Pokud není zadána žádná klauzule `Select`, použije se klauzule `Distinct` na proměnnou rozsahu pro dotaz identifikovaný v klauzuli `From`. Pokud proměnná rozsahu není neměnný typ, dotaz bude ignorovat výsledek dotazu pouze v případě, že všichni členové typu odpovídají existujícímu výsledku dotazu.  
  
## <a name="example"></a>Příklad  
 Následující výraz dotazu spojuje seznam zákazníků a seznam objednávek zákazníků. Klauzule `Distinct` je obsažena k vrácení seznamu jedinečných názvů zákazníků a data objednávky.  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a>Viz také:

- [Úvod do jazyka LINQ v Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
