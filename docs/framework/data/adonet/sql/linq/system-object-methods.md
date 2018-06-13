---
title: System.Object metody
ms.date: 03/30/2017
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
ms.openlocfilehash: bd4b30a65e7ad9391d9b867884d1c909491344bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355172"
---
# <a name="systemobject-methods"></a><span data-ttu-id="a7489-102">System.Object metody</span><span class="sxs-lookup"><span data-stu-id="a7489-102">System.Object Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="a7489-103"> podporuje následující <xref:System.Object> metody.</span><span class="sxs-lookup"><span data-stu-id="a7489-103"> supports the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="a7489-104"> nepodporuje následující <xref:System.Object> metody.</span><span class="sxs-lookup"><span data-stu-id="a7489-104"> does not support the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<span data-ttu-id="a7489-105"><xref:System.Object.ToString?displayProperty=nameWithType> pro binární typy, jako `BINARY`, `VARBINARY`, `IMAGE`, a `TIMESTAMP`.</span><span class="sxs-lookup"><span data-stu-id="a7489-105"><xref:System.Object.ToString?displayProperty=nameWithType> for binary types such as `BINARY`, `VARBINARY`, `IMAGE`, and `TIMESTAMP`.</span></span>||  
  
## <a name="differences-from-net"></a><span data-ttu-id="a7489-106">Rozdíl oproti rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="a7489-106">Differences from .NET</span></span>  
 <span data-ttu-id="a7489-107">Výstup <xref:System.Object.ToString?displayProperty=nameWithType> pro dvojitou používá SQL `CONVERT`(NVARCHAR(30), @x, 2) na SQL.</span><span class="sxs-lookup"><span data-stu-id="a7489-107">The output of <xref:System.Object.ToString?displayProperty=nameWithType> for double uses SQL `CONVERT`(NVARCHAR(30), @x, 2) on SQL.</span></span> <span data-ttu-id="a7489-108">SQL vždy používá 16 číslic a vědecká notace v tomto případě (například "0.000000000000000e + 000" 0).</span><span class="sxs-lookup"><span data-stu-id="a7489-108">SQL always uses 16 digits and scientific notation in this case (for example, "0.000000000000000e+000" for 0).</span></span> <span data-ttu-id="a7489-109">V důsledku toho <xref:System.Object.ToString?displayProperty=nameWithType> převod nevytváří stejné řetězec jako <xref:System.Convert.ToString%2A?displayProperty=nameWithType> v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a7489-109">As a result, <xref:System.Object.ToString?displayProperty=nameWithType> conversion does not produce the same string as <xref:System.Convert.ToString%2A?displayProperty=nameWithType> in the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7489-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7489-110">See Also</span></span>  
 [<span data-ttu-id="a7489-111">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="a7489-111">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
