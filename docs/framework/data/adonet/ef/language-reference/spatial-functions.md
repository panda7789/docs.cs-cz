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
# <a name="spatial-functions"></a><span data-ttu-id="f42f3-102">Prostorové funkce</span><span class="sxs-lookup"><span data-stu-id="f42f3-102">Spatial Functions</span></span>
<span data-ttu-id="f42f3-103">Neexistuje žádné literálu formát pro prostorové typy.</span><span class="sxs-lookup"><span data-stu-id="f42f3-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="f42f3-104">Můžete však použít kanonický Entity Framework funkce volat pomocí řetězce ve formátu Well-Known Text.</span><span class="sxs-lookup"><span data-stu-id="f42f3-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="f42f3-105">Například následující volání funkce vytvoří bod geometrie:</span><span class="sxs-lookup"><span data-stu-id="f42f3-105">For example, the following function call creates a geometry point:</span></span>  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="f42f3-106">[SpatialEdmFunctions metody](http://msdn.microsoft.com/library/hh749531.aspx) stránka obsahuje seznam všech prostorových metod kanonický Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="f42f3-106">The [SpatialEdmFunctions Methods](http://msdn.microsoft.com/library/hh749531.aspx) page lists all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="f42f3-107">Klikněte na metodu pro vás zajímá, zobrazíte, jaké parametry by měla být předána funkci.</span><span class="sxs-lookup"><span data-stu-id="f42f3-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
