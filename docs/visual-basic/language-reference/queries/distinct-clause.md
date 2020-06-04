---
title: Distinct – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 5aecffbce036500d294d03a925798d51f1269af6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401391"
---
# <a name="distinct-clause-visual-basic"></a>Distinct – klauzule (Visual Basic)
Omezuje hodnoty aktuální proměnné rozsahu tak, aby v následných klauzulích dotazu vyloučily duplicitní hodnoty.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a>Poznámky  
 Pomocí `Distinct` klauzule můžete vracet seznam jedinečných položek. `Distinct`Klauzule způsobí, že dotaz ignoruje výsledky duplicitních dotazů. `Distinct`Klauzule se vztahuje na duplicitní hodnoty všech vrácených polí určených `Select` klauzulí. Pokud `Select` není zadána žádná klauzule, `Distinct` klauzule je použita na proměnnou rozsahu pro dotaz identifikovaný v `From` klauzuli. Pokud proměnná rozsahu není neměnný typ, dotaz bude ignorovat výsledek dotazu pouze v případě, že všichni členové typu odpovídají existujícímu výsledku dotazu.  
  
## <a name="example"></a>Příklad  
 Následující výraz dotazu spojuje seznam zákazníků a seznam objednávek zákazníků. `Distinct`K dispozici je klauzule, která vrátí seznam jedinečných názvů zákazníků a data objednávky.  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a>Viz také

- [Představení technologie LINQ v jazyce Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](index.md)
- [Klauzule FROM](from-clause.md)
- [Klauzule SELECT](select-clause.md)
- [Klauzule WHERE](where-clause.md)
