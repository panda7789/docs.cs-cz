---
title: Prostorové funkce
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: ad6b722e84aae40354e30434b107752d02352645
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44266385"
---
# <a name="spatial-functions"></a>Prostorové funkce
Neexistuje žádný literál formát pro prostorové typy. Můžete však použít kanonické funkce Entity Framework volání pomocí řetězce ve formátu Well-Known Text. Například následující volání funkce vytvoří geometrie bodu:  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 [SpatialEdmFunctions metody](https://msdn.microsoft.com/library/hh749531.aspx) stránce uvedeny všechny prostorových canonical metody rozhraní Entity Framework. Klikněte na metodu vás zajímá, zobrazíte, jaké parametry by měly být předány funkci.
