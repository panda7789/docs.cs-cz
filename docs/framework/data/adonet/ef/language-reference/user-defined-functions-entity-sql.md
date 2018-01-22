---
title: "Uživatelem definované funkce (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4e5cfc9685c1e088722b24b54b4a0368d52fda29
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="user-defined-functions-entity-sql"></a>Uživatelem definované funkce (entita SQL)
Entity SQL podporuje volání uživatelem definované funkce v dotazu. Můžete definovat tyto funkce vložením s dotaz (najdete v části [postup: volání funkce definované uživatelem](http://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02)) nebo jako součást konceptuální model (v tématu [postup: definovat vlastní funkce v konceptuálním modelu](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)). Funkce konceptuálního modelu jsou definovány jako příkaz Entity SQL v [DefiningExpression](http://msdn.microsoft.com/library/d3da8d8b-a048-47ee-8d81-0c2ea3acdd3e) elementu [funkce](http://msdn.microsoft.com/library/dc3beca7-55cf-4977-8db0-5064cdbab134) element v konceptuálním modelu.  
  
 Entity SQL umožňuje definovat funkce v příkazu dotazu sám sebe. [Funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) operátor definuje vložené funkce. V příkazu můžete definovat víc funkcí a tyto funkce můžou mít stejný název funkce, tak dlouho, dokud signatury funkce jsou jedinečné. Další informace najdete v tématu [rozlišení přetížení funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
