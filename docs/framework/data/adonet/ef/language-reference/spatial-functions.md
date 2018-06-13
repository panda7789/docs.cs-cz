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
# <a name="spatial-functions"></a><span data-ttu-id="9fe35-102">Prostorové funkce</span><span class="sxs-lookup"><span data-stu-id="9fe35-102">Spatial Functions</span></span>
<span data-ttu-id="9fe35-103">Neexistuje žádné literálu formát pro prostorové typy.</span><span class="sxs-lookup"><span data-stu-id="9fe35-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="9fe35-104">Můžete však použít kanonický Entity Framework funkce volat pomocí řetězce ve formátu Well-Known Text.</span><span class="sxs-lookup"><span data-stu-id="9fe35-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="9fe35-105">Například následující volání funkce vytvoří bod geometrie:</span><span class="sxs-lookup"><span data-stu-id="9fe35-105">For example, the following function call creates a geometry point:</span></span>  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="9fe35-106">[SpatialEdmFunctions metody](http://msdn.microsoft.com/library/hh749531.aspx) stránka obsahuje seznam všech prostorových metod kanonický Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="9fe35-106">The [SpatialEdmFunctions Methods](http://msdn.microsoft.com/library/hh749531.aspx) page lists all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="9fe35-107">Klikněte na metodu pro vás zajímá, zobrazíte, jaké parametry by měla být předána funkci.</span><span class="sxs-lookup"><span data-stu-id="9fe35-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
