---
title: Uživatelsky definované funkce (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: 9ddafb18a10ff2313fd27eab453907054a35218a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248774"
---
# <a name="user-defined-functions-entity-sql"></a>Uživatelsky definované funkce (Entity SQL)
Entity SQL podporuje volání uživatelsky definovaných funkcí v dotazu. Tyto funkce můžete definovat jako vložené společně s dotazem ( [viz How to: Zavolejte uživatelsky definovanou funkci](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) nebo jako součást koncepčního modelu (viz [How to: Definujte vlastní funkce v koncepčním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))). Funkce koncepčního modelu jsou definovány jako Entity SQL příkaz v elementu [DefiningExpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) elementu [Function](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) v koncepčním modelu.  
  
 Entity SQL umožňuje definovat funkce v samotném příkazu dotazu. Operátor [funkce](function-entity-sql.md) definuje vložené funkce. V jednom příkazu můžete definovat více funkcí a tyto funkce mohou mít stejný název funkce, pokud jsou signatury funkcí jedinečné. Další informace najdete v tématu [řešení přetížení funkce](function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Viz také:

- [Funkce](functions-entity-sql.md)
