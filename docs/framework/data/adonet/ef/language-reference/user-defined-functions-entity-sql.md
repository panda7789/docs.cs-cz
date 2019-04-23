---
title: Uživatelem definované funkce (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: 4922e7fada676a6c26042236ccdb6315d6d455ae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104621"
---
# <a name="user-defined-functions-entity-sql"></a>Uživatelem definované funkce (Entity SQL)
Entita SQL podporuje volání uživatelem definované funkce v dotazu. Můžete definovat tyto vložené funkce s dotazem (viz [jak: Volání uživatelem definované funkce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) nebo v rámci koncepčního modelu (viz [jak: Definování vlastních funkcí v konceptuálním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))). Konceptuální model funkce jsou definované jako příkazu k Entity SQL v [DefiningExpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) prvek [funkce](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) element v konceptuálním modelu.  
  
 Entita SQL vám umožní definovat funkce v dotazu příkazu samého. [Funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) operátor definuje vložených funkcí. Můžete definovat více funkcí stačí jediný příkaz, a tyto funkce může mít stejný název funkce, jako signatur funkce jsou jedinečné. Další informace najdete v tématu [rozlišení přetížení funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Viz také:

- [Funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
