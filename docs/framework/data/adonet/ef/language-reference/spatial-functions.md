---
title: "Prostorové funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 935708457c3ebc8257b2495da36886468be1c706
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="spatial-functions"></a>Prostorové funkce
Neexistuje žádné literálu formát pro prostorové typy. Můžete však použít kanonický Entity Framework funkce volat pomocí řetězce ve formátu Well-Known Text. Například následující volání funkce vytvoří bod geometrie:  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 [SpatialEdmFunctions metody](http://msdn.microsoft.com/library/hh749531.aspx) stránka obsahuje seznam všech prostorových metod kanonický Entity Framework. Klikněte na metodu pro vás zajímá, zobrazíte, jaké parametry by měla být předána funkci.
