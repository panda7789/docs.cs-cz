---
title: . (Přístup ke členu) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 8e63caba9e9efb91d5c4629b9da0b1feca905ace
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319652"
---
# <a name="-member-access-entity-sql"></a>. (Přístup ke členu) (Entity SQL)
Operátor tečka (.) je operátor přístupu člena [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Operátor přístupu členů slouží k získání hodnoty vlastnosti nebo pole instance strukturálního koncepčního modelu.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
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
