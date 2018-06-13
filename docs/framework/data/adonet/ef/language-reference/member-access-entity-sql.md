---
title: . (Přístup ke členu) (Entita SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: fdcd026d245b3f6d6ecaccc0f828f3d77fd6ce1a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764629"
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
