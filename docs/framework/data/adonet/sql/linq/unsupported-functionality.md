---
title: Nepodporované funkce
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: 18a1a8f33a9360b4299648bcd329f4c5f2e7de88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61917555"
---
# <a name="unsupported-functionality"></a>Nepodporované funkce
V technologii LINQ to SQL následující funkci SQL nemůže být vystavená prostřednictvím překladu stávajících common language runtime (CLR) a rozhraní .NET Framework vytvoří:  
  
- `STDDEV`  
  
- `LIKE`  
  
     I když `LIKE` nepodporuje prostřednictvím přímé překladu, podobné funkce v existuje <xref:System.Data.Linq.SqlClient.SqlMethods> třídy. Další informace naleznete v tématu <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.  
  
- `DATEDIFF`  
  
     Technologie LINQ to SQL má omezenou podporu pro `DATEDIFF`. Podobné funkce existuje ve <xref:System.Data.Linq.SqlClient.SqlMethods> třídy.  
  
- `ROUND`  
  
     Technologie LINQ to SQL má omezenou podporu pro `ROUND`. Další informace najdete v tématu [metody System.Math](system-math-methods.md).  
  
## <a name="see-also"></a>Viz také:

- [Datové typy a funkce](data-types-and-functions.md)
