---
title: . (Přístup ke členu) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: e2874e5bff8d8c34f700a81bf52c6729df49aca5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626666"
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
