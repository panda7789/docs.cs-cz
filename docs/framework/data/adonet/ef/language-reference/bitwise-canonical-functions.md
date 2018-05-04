---
title: Bitový kanonické funkce
ms.date: 03/30/2017
ms.assetid: 993868ca-16e3-47b6-9915-c29cd63b0a21
ms.openlocfilehash: df3b81a47b8e1202884a5c38f55c7061279b245f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="bitwise-canonical-functions"></a>Bitový kanonické funkce
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] zahrnuje bitové kanonické funkce.  
  
## <a name="remarks"></a>Poznámky  
 V následující tabulce jsou uvedeny bitové hodnotě [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce. Vrátí tyto funkce `Null` Pokud `Null` vstup je k dispozici. Návratový typ funkce je stejný jako typy argumentů. Argumenty musí být stejného typu, pokud funkci trvá víc než jeden argument. K provedení bitové operace do různých typů, musíte explicitně převést do stejného typu.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|`BitWiseAnd (` `value1` `,`  `value2` `)`|Vrátí bitové spojení z `value1` a `value2` jako typ `value1` a `value2`.<br /><br /> **Argumenty**<br /><br /> A `Byte`, `Int16`, `Int32`, a `Int64`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|`BitWiseNot (` `value` `)`|Vrátí bitovou negaci z `value`.<br /><br /> **Argumenty**<br /><br /> A `Byte`, `Int16`, `Int32`, a `Int64`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|`BitWiseOr (` `value1` `,`  `value2` `)`|Vrátí bitovou disjunkci z `value1` a `value2` jako typ `value1` a `value2`.<br /><br /> **Argumenty**<br /><br /> A `Byte`, `Int16`, `Int32` a `Int64`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|`BitWiseXor (` `value1` `,`  `value2` `)`|Vrátí bitový exkluzivní disjunkce z `value1` a `value2` jako typ `value1` a `value2`.<br /><br /> **Argumenty**<br /><br /> A `Byte`, `Int16`, `Int32` a `Int64`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a>Viz také  
 [Kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
