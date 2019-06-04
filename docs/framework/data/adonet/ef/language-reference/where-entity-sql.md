---
title: KDE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 939d4c0ec2c30bc71b22fb65ab36644e063f97de
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489851"
---
# <a name="where-entity-sql"></a>KDE (Entity SQL)
Přímo po použití klauzule WHERE [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) klauzuli.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Typ Boolean.  
  
## <a name="remarks"></a>Poznámky  
 Klauzule WHERE má stejnou sémantiku, jak je popsáno příkazů jazyka Transact-SQL. Omezuje objekty vytvořený podle výrazu dotazu tím, že omezíte prvků zdrojové kolekce na ty, které předávají podmínku.  
  
```  
select c from cs as c where e  
```  
  
 Výraz `e` musí být typu logická hodnota.  
  
 Použití klauzule WHERE přímo po klauzuli FROM a před všechny seskupení, řazení nebo projekce probíhá. Všechny názvy elementů, které jsou definovány v klauzuli FROM jsou viditelné pro výraz v klauzuli WHERE.  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Výrazy dotazu](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
