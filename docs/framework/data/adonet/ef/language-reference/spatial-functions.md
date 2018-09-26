---
title: Prostorové funkce
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: ad6b722e84aae40354e30434b107752d02352645
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47202884"
---
# <a name="spatial-functions"></a>Prostorové funkce
Neexistuje žádný literál formát pro prostorové typy. Můžete však použít kanonické funkce Entity Framework volání pomocí řetězce ve formátu Well-Known Text. Například následující volání funkce vytvoří geometrie bodu:  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 [SpatialEdmFunctions metody](https://msdn.microsoft.com/library/hh749531.aspx) stránce uvedeny všechny prostorových canonical metody rozhraní Entity Framework. Klikněte na metodu vás zajímá, zobrazíte, jaké parametry by měly být předány funkci.
