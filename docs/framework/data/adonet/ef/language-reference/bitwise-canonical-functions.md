---
title: Bitové kanonické funkce
ms.date: 03/30/2017
ms.assetid: 993868ca-16e3-47b6-9915-c29cd63b0a21
ms.openlocfilehash: 3c1f32acc7a035658198b807646c1ceb95dfed0b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251302"
---
# <a name="bitwise-canonical-functions"></a>Bitové kanonické funkce
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsahuje bitové kanonické funkce.  
  
## <a name="remarks"></a>Poznámky  
 V následující tabulce jsou uvedeny bitové [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce. `Null` Pokud`Null` je zadaný vstup, vrátí tyto funkce. Návratový typ funkcí je stejný jako typ argumentu (y). Argumenty musí být stejného typu, pokud funkce přijímá více než jeden argument. Chcete-li provádět bitové operace v různých typech, je nutné přetypování na stejný typ explicitně.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|`BitWiseAnd (` `value1` `,`  `value2` `)`|Vrátí `value1` bitové spojení `value2` typu `value1` a jako typ a `value2`.<br /><br /> **Argumenty**<br /><br /> A `Byte` ,`Int16`, a`Int64`. `Int32`<br /><br /> **Příklad**<br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|`BitWiseNot (` `value` `)`|Vrátí logickou negaci `value`.<br /><br /> **Argumenty**<br /><br /> A `Byte` ,`Int16`, a`Int64`. `Int32`<br /><br /> **Příklad**<br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|`BitWiseOr (` `value1` `,`  `value2` `)`|Vrátí bitovou disjunkci `value1` a `value2` jako typ `value1` a `value2`.<br /><br /> **Argumenty**<br /><br /> A`Int32` , a`Int16` .`Int64` `Byte`<br /><br /> **Příklad**<br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|`BitWiseXor (` `value1` `,`  `value2` `)`|Vrátí bitovou exkluzivní disjunkci `value1` a `value2` jako typ `value1` a `value2`.<br /><br /> **Argumenty**<br /><br /> A`Int32` , a`Int16` .`Int64` `Byte`<br /><br /> **Příklad**<br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a>Viz také:

- [Kanonické funkce](canonical-functions.md)
