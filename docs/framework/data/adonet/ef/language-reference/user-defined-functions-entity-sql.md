---
title: Uživatelem definované funkce (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: 86b7d26e7959be954b4ddd7404f3a3ad6c76c1c5
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904497"
---
# <a name="user-defined-functions-entity-sql"></a>Uživatelem definované funkce (Entity SQL)
Entita SQL podporuje volání uživatelem definované funkce v dotazu. Můžete definovat tyto vložené funkce s dotazem (viz [jak: Volání uživatelem definované funkce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) nebo v rámci koncepčního modelu (viz [jak: Definování vlastních funkcí v konceptuálním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))). Konceptuální model funkce jsou definované jako příkazu k Entity SQL v [DefiningExpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) prvek [funkce](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) element v konceptuálním modelu.  
  
 Entita SQL vám umožní definovat funkce v dotazu příkazu samého. [Funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) operátor definuje vložených funkcí. Můžete definovat více funkcí stačí jediný příkaz, a tyto funkce může mít stejný název funkce, jako signatur funkce jsou jedinečné. Další informace najdete v tématu [rozlišení přetížení funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Viz také:
- [Funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
