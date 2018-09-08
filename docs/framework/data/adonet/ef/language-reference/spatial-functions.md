---
title: Prostorové funkce
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: ad6b722e84aae40354e30434b107752d02352645
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44202086"
---
# <a name="spatial-functions"></a><span data-ttu-id="28dfe-102">Prostorové funkce</span><span class="sxs-lookup"><span data-stu-id="28dfe-102">Spatial Functions</span></span>
<span data-ttu-id="28dfe-103">Neexistuje žádný literál formát pro prostorové typy.</span><span class="sxs-lookup"><span data-stu-id="28dfe-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="28dfe-104">Můžete však použít kanonické funkce Entity Framework volání pomocí řetězce ve formátu Well-Known Text.</span><span class="sxs-lookup"><span data-stu-id="28dfe-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="28dfe-105">Například následující volání funkce vytvoří geometrie bodu:</span><span class="sxs-lookup"><span data-stu-id="28dfe-105">For example, the following function call creates a geometry point:</span></span>  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="28dfe-106">[SpatialEdmFunctions metody](https://msdn.microsoft.com/library/hh749531.aspx) stránce uvedeny všechny prostorových canonical metody rozhraní Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="28dfe-106">The [SpatialEdmFunctions Methods](https://msdn.microsoft.com/library/hh749531.aspx) page lists all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="28dfe-107">Klikněte na metodu vás zajímá, zobrazíte, jaké parametry by měly být předány funkci.</span><span class="sxs-lookup"><span data-stu-id="28dfe-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
