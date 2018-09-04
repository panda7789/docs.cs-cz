---
title: Uživatelem definované funkce (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: 03146d895c6ca780692228937fafcf25b24902aa
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43564945"
---
# <a name="user-defined-functions-entity-sql"></a>Uživatelem definované funkce (Entity SQL)
Entita SQL podporuje volání uživatelem definované funkce v dotazu. Můžete definovat tyto vložené funkce s dotazem (naleznete v tématu [postupy: volání funkce definovaná uživatelem](https://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02)) nebo v rámci koncepčního modelu (naleznete v tématu [jak: definovat vlastní funkce v konceptuálním modelu](https://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)). Konceptuální model funkce jsou definované jako příkazu k Entity SQL v [DefiningExpression](https://msdn.microsoft.com/library/d3da8d8b-a048-47ee-8d81-0c2ea3acdd3e) prvek [funkce](https://msdn.microsoft.com/library/dc3beca7-55cf-4977-8db0-5064cdbab134) element v konceptuálním modelu.  
  
 Entita SQL vám umožní definovat funkce v dotazu příkazu samého. [Funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) operátor definuje vložených funkcí. Můžete definovat více funkcí stačí jediný příkaz, a tyto funkce může mít stejný název funkce, jako signatur funkce jsou jedinečné. Další informace najdete v tématu [rozlišení přetížení funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
