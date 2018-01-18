---
title: "Nepodporované funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b54bac0c9ce0b473ef8d86b039ef638b79af784f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="unsupported-functionality"></a><span data-ttu-id="7a4d3-102">Nepodporované funkce</span><span class="sxs-lookup"><span data-stu-id="7a4d3-102">Unsupported Functionality</span></span>
<span data-ttu-id="7a4d3-103">V technologii LINQ to SQL nelze tyto funkce SQL uvádět na překlad existující common language runtime (CLR) a vytvoří rozhraní .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="7a4d3-103">In LINQ to SQL, the following SQL functionality cannot be exposed through translation of existing common language runtime (CLR) and .NET Framework constructs:</span></span>  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     <span data-ttu-id="7a4d3-104">I když `LIKE` nepodporuje prostřednictvím přímé překlad podobné funkce v existuje <xref:System.Data.Linq.SqlClient.SqlMethods> třídy.</span><span class="sxs-lookup"><span data-stu-id="7a4d3-104">Although `LIKE` is not supported through direct translation, similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span> <span data-ttu-id="7a4d3-105">Další informace naleznete v tématu <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7a4d3-105">For more information, see <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span></span>  
  
-   `DATEDIFF`  
  
     <span data-ttu-id="7a4d3-106">Technologie LINQ to SQL má omezenou podporu pro `DATEDIFF`.</span><span class="sxs-lookup"><span data-stu-id="7a4d3-106">LINQ to SQL has limited support for `DATEDIFF`.</span></span> <span data-ttu-id="7a4d3-107">Podobné funkce v existuje <xref:System.Data.Linq.SqlClient.SqlMethods> třídy.</span><span class="sxs-lookup"><span data-stu-id="7a4d3-107">Similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span>  
  
-   `ROUND`  
  
     <span data-ttu-id="7a4d3-108">Technologie LINQ to SQL má omezenou podporu pro `ROUND`.</span><span class="sxs-lookup"><span data-stu-id="7a4d3-108">LINQ to SQL has limited support for `ROUND`.</span></span> <span data-ttu-id="7a4d3-109">Další informace najdete v tématu [System.Math metody](system-math-methods.md).</span><span class="sxs-lookup"><span data-stu-id="7a4d3-109">For more information, see [System.Math Methods](system-math-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a4d3-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a4d3-110">See Also</span></span>  
 [<span data-ttu-id="7a4d3-111">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="7a4d3-111">Data Types and Functions</span></span>](data-types-and-functions.md)
