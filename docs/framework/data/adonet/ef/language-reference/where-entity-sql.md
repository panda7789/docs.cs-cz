---
title: KDE (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 38d1b7e2b7662ef3b2fedbcce6ac23ce55a5468f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="where-entity-sql"></a>KDE (entita SQL)
Přímo po použití klauzule WHERE [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) klauzule.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Typem logická hodnota.  
  
## <a name="remarks"></a>Poznámky  
 Klauzule WHERE obsahuje stejnou sémantiku, jak je popsáno pro [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]. Omezuje objekty vyprodukované výrazu dotazu omezením elementy kolekcí zdroje na ty, které předat podmínku.  
  
```  
select c from cs as c where e  
```  
  
 Výraz `e` musí být typu logická hodnota.  
  
 Klauzule WHERE se použije přímo po klauzuli FROM a před jakoukoli seskupení, řazení nebo projekce probíhá. Všechny názvy elementů, které jsou definované v klauzuli FROM jsou viditelné pro výraz klauzule WHERE.  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na entitu SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Výrazy dotazů](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
