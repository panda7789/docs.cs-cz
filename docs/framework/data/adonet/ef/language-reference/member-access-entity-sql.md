---
title: . (Přístup ke členu) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 1db6be632da90eaa7a761bb213e395182ae42347
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250298"
---
# <a name="-member-access-entity-sql"></a>. (Přístup ke členu) (Entity SQL)
Operátor tečka (.) je [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátor přístupu členů. Operátor přístupu členů slouží k získání hodnoty vlastnosti nebo pole instance strukturálního koncepčního modelu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Instance strukturálního typu koncepčního modelu.  
  
 `identifier`  
 Vlastnost nebo pole, které patří do instance objektu.  
  
## <a name="remarks"></a>Poznámky  
 Operátor tečka (.) se dá použít k extrakci polí ze záznamu, podobně jako extrakce vlastností komplexního typu nebo typu entity. Například pokud n typu názvu je členem typu Person a p je instance typu person, pak p. n je platným výrazem přístupu člena, který je výsledkem hodnoty typu název.  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
