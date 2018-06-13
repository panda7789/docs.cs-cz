---
title: Nepodporované funkce
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: c4ed52a43fe9cf04c8015aad9247e9f2eb2481e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364487"
---
# <a name="unsupported-functionality"></a>Nepodporované funkce
V technologii LINQ to SQL nelze tyto funkce SQL uvádět na překlad existující common language runtime (CLR) a vytvoří rozhraní .NET Framework:  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     I když `LIKE` nepodporuje prostřednictvím přímé překlad podobné funkce v existuje <xref:System.Data.Linq.SqlClient.SqlMethods> třídy. Další informace naleznete v tématu <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.  
  
-   `DATEDIFF`  
  
     Technologie LINQ to SQL má omezenou podporu pro `DATEDIFF`. Podobné funkce v existuje <xref:System.Data.Linq.SqlClient.SqlMethods> třídy.  
  
-   `ROUND`  
  
     Technologie LINQ to SQL má omezenou podporu pro `ROUND`. Další informace najdete v tématu [System.Math metody](system-math-methods.md).  
  
## <a name="see-also"></a>Viz také  
 [Datové typy a funkce](data-types-and-functions.md)
