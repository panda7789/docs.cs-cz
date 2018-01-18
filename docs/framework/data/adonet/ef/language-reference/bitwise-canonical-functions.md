---
title: "Bitový kanonické funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 993868ca-16e3-47b6-9915-c29cd63b0a21
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1d703b2467d508324f3eb39b822c239484ac1c6e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="bitwise-canonical-functions"></a>Bitový kanonické funkce
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]zahrnuje bitové kanonické funkce.  
  
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
