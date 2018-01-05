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
# <a name="spatial-functions"></a><span data-ttu-id="d29d0-102">Prostorové funkce</span><span class="sxs-lookup"><span data-stu-id="d29d0-102">Spatial Functions</span></span>
<span data-ttu-id="d29d0-103">Neexistuje žádné literálu formát pro prostorové typy.</span><span class="sxs-lookup"><span data-stu-id="d29d0-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="d29d0-104">Můžete však použít kanonický Entity Framework funkce volat pomocí řetězce ve formátu Well-Known Text.</span><span class="sxs-lookup"><span data-stu-id="d29d0-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="d29d0-105">Například následující volání funkce vytvoří bod geometrie:</span><span class="sxs-lookup"><span data-stu-id="d29d0-105">For example, the following function call creates a geometry point:</span></span>  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="d29d0-106">[SpatialEdmFunctions metody](http://msdn.microsoft.com/library/hh749531.aspx) stránka obsahuje seznam všech prostorových metod kanonický Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="d29d0-106">The [SpatialEdmFunctions Methods](http://msdn.microsoft.com/library/hh749531.aspx) page lists all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="d29d0-107">Klikněte na metodu pro vás zajímá, zobrazíte, jaké parametry by měla být předána funkci.</span><span class="sxs-lookup"><span data-stu-id="d29d0-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
