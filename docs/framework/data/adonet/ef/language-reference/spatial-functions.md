---
title: Prostorové funkce
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: 09402633c5e7f591a534992fc92655e6a2d1d88d
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904478"
---
# <a name="spatial-functions"></a><span data-ttu-id="440e6-102">Prostorové funkce</span><span class="sxs-lookup"><span data-stu-id="440e6-102">Spatial Functions</span></span>
<span data-ttu-id="440e6-103">Neexistuje žádný literál formát pro prostorové typy.</span><span class="sxs-lookup"><span data-stu-id="440e6-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="440e6-104">Můžete však použít kanonické funkce Entity Framework volání pomocí řetězce ve formátu Well-Known Text.</span><span class="sxs-lookup"><span data-stu-id="440e6-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="440e6-105">Například následující volání funkce vytvoří geometrie bodu:</span><span class="sxs-lookup"><span data-stu-id="440e6-105">For example, the following function call creates a geometry point:</span></span>  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="440e6-106"><xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> Metody mají prostorových canonical metody rozhraní Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="440e6-106">The <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> methods have all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="440e6-107">Klikněte na metodu vás zajímá, zobrazíte, jaké parametry by měly být předány funkci.</span><span class="sxs-lookup"><span data-stu-id="440e6-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
