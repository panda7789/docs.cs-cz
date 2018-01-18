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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 11687b1218c61acde7a68bb8fc112e287e5e1c38
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
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
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Výrazy dotazu](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
