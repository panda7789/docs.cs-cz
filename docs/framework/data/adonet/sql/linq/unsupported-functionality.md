---
title: Nepodporované funkce
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: 18a1a8f33a9360b4299648bcd329f4c5f2e7de88
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097870"
---
# <a name="unsupported-functionality"></a><span data-ttu-id="ea241-102">Nepodporované funkce</span><span class="sxs-lookup"><span data-stu-id="ea241-102">Unsupported Functionality</span></span>
<span data-ttu-id="ea241-103">V technologii LINQ to SQL následující funkci SQL nemůže být vystavená prostřednictvím překladu stávajících common language runtime (CLR) a rozhraní .NET Framework vytvoří:</span><span class="sxs-lookup"><span data-stu-id="ea241-103">In LINQ to SQL, the following SQL functionality cannot be exposed through translation of existing common language runtime (CLR) and .NET Framework constructs:</span></span>  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     <span data-ttu-id="ea241-104">I když `LIKE` nepodporuje prostřednictvím přímé překladu, podobné funkce v existuje <xref:System.Data.Linq.SqlClient.SqlMethods> třídy.</span><span class="sxs-lookup"><span data-stu-id="ea241-104">Although `LIKE` is not supported through direct translation, similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span> <span data-ttu-id="ea241-105">Další informace naleznete v tématu <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ea241-105">For more information, see <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span></span>  
  
-   `DATEDIFF`  
  
     <span data-ttu-id="ea241-106">Technologie LINQ to SQL má omezenou podporu pro `DATEDIFF`.</span><span class="sxs-lookup"><span data-stu-id="ea241-106">LINQ to SQL has limited support for `DATEDIFF`.</span></span> <span data-ttu-id="ea241-107">Podobné funkce existuje ve <xref:System.Data.Linq.SqlClient.SqlMethods> třídy.</span><span class="sxs-lookup"><span data-stu-id="ea241-107">Similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span>  
  
-   `ROUND`  
  
     <span data-ttu-id="ea241-108">Technologie LINQ to SQL má omezenou podporu pro `ROUND`.</span><span class="sxs-lookup"><span data-stu-id="ea241-108">LINQ to SQL has limited support for `ROUND`.</span></span> <span data-ttu-id="ea241-109">Další informace najdete v tématu [metody System.Math](system-math-methods.md).</span><span class="sxs-lookup"><span data-stu-id="ea241-109">For more information, see [System.Math Methods](system-math-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea241-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea241-110">See also</span></span>

- [<span data-ttu-id="ea241-111">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="ea241-111">Data Types and Functions</span></span>](data-types-and-functions.md)
