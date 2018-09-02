---
title: Prostorové funkce
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: ad6b722e84aae40354e30434b107752d02352645
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43395645"
---
# <a name="spatial-functions"></a><span data-ttu-id="20340-102">Prostorové funkce</span><span class="sxs-lookup"><span data-stu-id="20340-102">Spatial Functions</span></span>
<span data-ttu-id="20340-103">Neexistuje žádný literál formát pro prostorové typy.</span><span class="sxs-lookup"><span data-stu-id="20340-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="20340-104">Můžete však použít kanonické funkce Entity Framework volání pomocí řetězce ve formátu Well-Known Text.</span><span class="sxs-lookup"><span data-stu-id="20340-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="20340-105">Například následující volání funkce vytvoří geometrie bodu:</span><span class="sxs-lookup"><span data-stu-id="20340-105">For example, the following function call creates a geometry point:</span></span>  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="20340-106">[SpatialEdmFunctions metody](https://msdn.microsoft.com/library/hh749531.aspx) stránce uvedeny všechny prostorových canonical metody rozhraní Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="20340-106">The [SpatialEdmFunctions Methods](https://msdn.microsoft.com/library/hh749531.aspx) page lists all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="20340-107">Klikněte na metodu vás zajímá, zobrazíte, jaké parametry by měly být předány funkci.</span><span class="sxs-lookup"><span data-stu-id="20340-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
