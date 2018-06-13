---
title: Prostorové funkce
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: 7b78cbf4dc53ba1bc4148fa0077615e43cc8f9f9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763927"
---
# <a name="spatial-functions"></a>Prostorové funkce
Neexistuje žádné literálu formát pro prostorové typy. Můžete však použít kanonický Entity Framework funkce volat pomocí řetězce ve formátu Well-Known Text. Například následující volání funkce vytvoří bod geometrie:  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 [SpatialEdmFunctions metody](http://msdn.microsoft.com/library/hh749531.aspx) stránka obsahuje seznam všech prostorových metod kanonický Entity Framework. Klikněte na metodu pro vás zajímá, zobrazíte, jaké parametry by měla být předána funkci.
