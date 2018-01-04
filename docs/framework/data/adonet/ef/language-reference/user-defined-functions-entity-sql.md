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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: bf0592a3e88f4e8142f1fb0aeb1e7364d818d4ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="user-defined-functions-entity-sql"></a>Uživatelem definované funkce (entita SQL)
Entity SQL podporuje volání uživatelem definované funkce v dotazu. Můžete definovat tyto funkce vložením s dotaz (najdete v části [postup: volání funkce definované uživatelem](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02)) nebo jako součást konceptuální model (v tématu [postup: definovat vlastní funkce v konceptuálním modelu](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f)). Funkce konceptuálního modelu jsou definovány jako příkaz Entity SQL v [DefiningExpression](http://msdn.microsoft.com/en-us/d3da8d8b-a048-47ee-8d81-0c2ea3acdd3e) elementu [funkce](http://msdn.microsoft.com/en-us/dc3beca7-55cf-4977-8db0-5064cdbab134) element v konceptuálním modelu.  
  
 Entity SQL umožňuje definovat funkce v příkazu dotazu sám sebe. [Funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) operátor definuje vložené funkce. V příkazu můžete definovat víc funkcí a tyto funkce můžou mít stejný název funkce, tak dlouho, dokud signatury funkce jsou jedinečné. Další informace najdete v tématu [rozlišení přetížení funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
