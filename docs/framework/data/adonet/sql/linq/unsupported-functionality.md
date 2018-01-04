---
title: "Nepodporované funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 244d9ee7accd3686729542d0f0a15966bcde7b78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
