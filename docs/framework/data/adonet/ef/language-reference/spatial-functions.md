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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: acc09f9ea83e42377d0ba633927ecef13d5f46a9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="spatial-functions"></a>Prostorové funkce
Neexistuje žádné literálu formát pro prostorové typy. Můžete však použít kanonický Entity Framework funkce volat pomocí řetězce ve formátu Well-Known Text. Například následující volání funkce vytvoří bod geometrie:  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 [SpatialEdmFunctions metody](http://msdn.microsoft.com/library/hh749531.aspx) stránka obsahuje seznam všech prostorových metod kanonický Entity Framework. Klikněte na metodu pro vás zajímá, zobrazíte, jaké parametry by měla být předána funkci.
