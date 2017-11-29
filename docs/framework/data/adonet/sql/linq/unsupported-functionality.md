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
ms.openlocfilehash: 6dd8ccebd278fdc36c536c49f7f1d4262b2de8c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
