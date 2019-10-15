---
title: Prostorové funkce
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: eba384e77389f82006479f165178e80fcac244b1
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319305"
---
# <a name="spatial-functions"></a><span data-ttu-id="fe5c6-102">Prostorové funkce</span><span class="sxs-lookup"><span data-stu-id="fe5c6-102">Spatial Functions</span></span>
<span data-ttu-id="fe5c6-103">Pro prostorové typy neexistuje žádný řetězcový formát.</span><span class="sxs-lookup"><span data-stu-id="fe5c6-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="fe5c6-104">Můžete však použít kanonické Entity Framework funkce, které zavoláte pomocí řetězců ve známém formátu textu.</span><span class="sxs-lookup"><span data-stu-id="fe5c6-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="fe5c6-105">Například následující volání funkce vytvoří bod geometrie:</span><span class="sxs-lookup"><span data-stu-id="fe5c6-105">For example, the following function call creates a geometry point:</span></span>  
  
```sql  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="fe5c6-106">Metody <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> mají všechny prostorové kanonické Entity Framework metody.</span><span class="sxs-lookup"><span data-stu-id="fe5c6-106">The <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> methods have all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="fe5c6-107">Pokud chcete zjistit, jaké parametry by měly být předány funkci, klikněte na metodu, která vás zajímá.</span><span class="sxs-lookup"><span data-stu-id="fe5c6-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
