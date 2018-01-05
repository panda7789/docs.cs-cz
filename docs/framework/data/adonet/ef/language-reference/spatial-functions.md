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
ms.workload: dotnet
ms.openlocfilehash: c482c2f79c6416a4e748599c896280b426d31ce2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="spatial-functions"></a>Prostorové funkce
Neexistuje žádné literálu formát pro prostorové typy. Můžete však použít kanonický Entity Framework funkce volat pomocí řetězce ve formátu Well-Known Text. Například následující volání funkce vytvoří bod geometrie:  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 [SpatialEdmFunctions metody](http://msdn.microsoft.com/library/hh749531.aspx) stránka obsahuje seznam všech prostorových metod kanonický Entity Framework. Klikněte na metodu pro vás zajímá, zobrazíte, jaké parametry by měla být předána funkci.
