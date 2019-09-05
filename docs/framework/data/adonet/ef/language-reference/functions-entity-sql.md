---
title: Funkce (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: ec94a0f16fb3b836297f6675cc938a711816555b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250908"
---
# <a name="functions-entity-sql"></a>Funkce (Entity SQL)
Entity SQL podporuje uživatelsky definované funkce, kanonické funkce a funkce specifické pro poskytovatele. Uživatelsky definované funkce jsou zadány v koncepčním modelu nebo vloženém v dotazu. Další informace najdete v tématu [uživatelsky definované funkce](user-defined-functions-entity-sql.md).  
  
 Kanonické funkce jsou předdefinované v Entity Framework a měly by být podporovány poskytovateli dat. Entity SQL příkazy selžou, pokud uživatel zavolá funkci, která není zprostředkovatelem podporována. Kanonické funkce jsou proto obecně doporučovány přes funkce specifické pro úložiště, které jsou v oboru názvů specifického pro konkrétního zprostředkovatele. Další informace najdete v tématu [kanonické funkce](canonical-functions.md).  
  
 Spravovaný zprostředkovatel klienta Microsoft SQL nabízí sadu funkcí specifických pro poskytovatele. Další informace najdete v tématu [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Uživatelem definované funkce](user-defined-functions-entity-sql.md)  
  
 [Řešení přetížení funkce](function-overload-resolution-entity-sql.md)  
  
 [Agregační funkce](../aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](entity-sql-overview.md)
