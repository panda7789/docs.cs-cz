---
title: ". (Přístup ke členu) (Entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c90c908e567ac05f344292411978ff0c80919a65
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="-member-access-entity-sql"></a>. (Přístup ke členu) (Entita SQL)
Operátor tečky (.) je [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátor přístupu členů. Operátor přístupu členů pomůže yield hodnotu vlastnost nebo pole instance typu strukturální konceptuálního modelu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Instance typu strukturální konceptuálního modelu.  
  
 `identifier`  
 Vlastnost nebo pole, které patří k instanci objektu.  
  
## <a name="remarks"></a>Poznámky  
 Operátor tečky (.) slouží k extrakci polí ze záznamu, podobně jako extrahování vlastnosti komplexní nebo entity typu. Například pokud n název typu je členem typu osoba, a p je instance typu osoba, p.n je výraz přístup právní člena, jehož výsledkem hodnota typu název.  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
