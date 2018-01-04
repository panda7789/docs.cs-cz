---
title: System.Object metody
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 98a1d690dbd059574098b044dd1d94b1f8792e75
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="systemobject-methods"></a><span data-ttu-id="f7ab4-102">System.Object metody</span><span class="sxs-lookup"><span data-stu-id="f7ab4-102">System.Object Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f7ab4-103">podporuje následující <xref:System.Object> metody.</span><span class="sxs-lookup"><span data-stu-id="f7ab4-103"> supports the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f7ab4-104">nepodporuje následující <xref:System.Object> metody.</span><span class="sxs-lookup"><span data-stu-id="f7ab4-104"> does not support the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<span data-ttu-id="f7ab4-105"><xref:System.Object.ToString?displayProperty=nameWithType>pro binární typy, jako `BINARY`, `VARBINARY`, `IMAGE`, a `TIMESTAMP`.</span><span class="sxs-lookup"><span data-stu-id="f7ab4-105"><xref:System.Object.ToString?displayProperty=nameWithType> for binary types such as `BINARY`, `VARBINARY`, `IMAGE`, and `TIMESTAMP`.</span></span>||  
  
## <a name="differences-from-net"></a><span data-ttu-id="f7ab4-106">Rozdíl oproti rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="f7ab4-106">Differences from .NET</span></span>  
 <span data-ttu-id="f7ab4-107">Výstup <xref:System.Object.ToString?displayProperty=nameWithType> pro dvojitou používá SQL `CONVERT`(NVARCHAR(30), @x, 2) na SQL.</span><span class="sxs-lookup"><span data-stu-id="f7ab4-107">The output of <xref:System.Object.ToString?displayProperty=nameWithType> for double uses SQL `CONVERT`(NVARCHAR(30), @x, 2) on SQL.</span></span> <span data-ttu-id="f7ab4-108">SQL vždy používá 16 číslic a vědecká notace v tomto případě (například "0.000000000000000e + 000" 0).</span><span class="sxs-lookup"><span data-stu-id="f7ab4-108">SQL always uses 16 digits and scientific notation in this case (for example, "0.000000000000000e+000" for 0).</span></span> <span data-ttu-id="f7ab4-109">V důsledku toho <xref:System.Object.ToString?displayProperty=nameWithType> převod nevytváří stejné řetězec jako <xref:System.Convert.ToString%2A?displayProperty=nameWithType> v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f7ab4-109">As a result, <xref:System.Object.ToString?displayProperty=nameWithType> conversion does not produce the same string as <xref:System.Convert.ToString%2A?displayProperty=nameWithType> in the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7ab4-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7ab4-110">See Also</span></span>  
 [<span data-ttu-id="f7ab4-111">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="f7ab4-111">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
