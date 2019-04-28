---
title: . (Přístup ke členu) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 6ebedd2b381d035d199e151f64632acf7d502ff5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760620"
---
# <a name="-member-access-entity-sql"></a>. (Přístup ke členu) (Entity SQL)
Tečka (.) je [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátor přístupu členů. Operátor přístupu členů použijete k získání hodnoty vlastnosti nebo pole instance typu strukturální koncepčního modelu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Instance typu strukturální koncepčního modelu.  
  
 `identifier`  
 Vlastnost nebo pole, které patří do instance objektu.  
  
## <a name="remarks"></a>Poznámky  
 Tečka (.) slouží k extrakci polí ze záznamu, podobně jako extrahování vlastnosti typu složitá nebo entity. Například pokud n název typu je členem typu osoba, a p je instance typu osoba, pak p.n je právní člen přístup Výraz vracející hodnotu zadejte název.  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
