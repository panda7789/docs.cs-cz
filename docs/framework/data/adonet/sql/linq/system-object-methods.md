---
title: Metody System.Object
ms.date: 03/30/2017
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
ms.openlocfilehash: 3a52f081f1c0c6e6c5218550009c736d0ed60514
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097665"
---
# <a name="systemobject-methods"></a><span data-ttu-id="5f22a-102">Metody System.Object</span><span class="sxs-lookup"><span data-stu-id="5f22a-102">System.Object Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="5f22a-103">podporuje následující <xref:System.Object> metody.</span><span class="sxs-lookup"><span data-stu-id="5f22a-103">supports the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="5f22a-104">nepodporuje následující <xref:System.Object> metody.</span><span class="sxs-lookup"><span data-stu-id="5f22a-104">does not support the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType> <span data-ttu-id="5f22a-105">pro binární typy, jako `BINARY`, `VARBINARY`, `IMAGE`, a `TIMESTAMP`.</span><span class="sxs-lookup"><span data-stu-id="5f22a-105">for binary types such as `BINARY`, `VARBINARY`, `IMAGE`, and `TIMESTAMP`.</span></span>||  
  
## <a name="differences-from-net"></a><span data-ttu-id="5f22a-106">Rozdíl oproti .NET</span><span class="sxs-lookup"><span data-stu-id="5f22a-106">Differences from .NET</span></span>  
 <span data-ttu-id="5f22a-107">Výstup <xref:System.Object.ToString?displayProperty=nameWithType> pro double používá SQL `CONVERT`(NVARCHAR(30), @x, 2) na SQL.</span><span class="sxs-lookup"><span data-stu-id="5f22a-107">The output of <xref:System.Object.ToString?displayProperty=nameWithType> for double uses SQL `CONVERT`(NVARCHAR(30), @x, 2) on SQL.</span></span> <span data-ttu-id="5f22a-108">SQL vždy používá 16 číslic a vědeckého zápisu v tomto případě (například "0.000000000000000e + 000" 0).</span><span class="sxs-lookup"><span data-stu-id="5f22a-108">SQL always uses 16 digits and scientific notation in this case (for example, "0.000000000000000e+000" for 0).</span></span> <span data-ttu-id="5f22a-109">V důsledku toho <xref:System.Object.ToString?displayProperty=nameWithType> výsledkem konverze není stejný řetězec jako <xref:System.Convert.ToString%2A?displayProperty=nameWithType> v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5f22a-109">As a result, <xref:System.Object.ToString?displayProperty=nameWithType> conversion does not produce the same string as <xref:System.Convert.ToString%2A?displayProperty=nameWithType> in the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f22a-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f22a-110">See also</span></span>

- [<span data-ttu-id="5f22a-111">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="5f22a-111">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
