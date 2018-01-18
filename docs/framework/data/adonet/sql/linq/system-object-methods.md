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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 319dc7ceae191de417bbdd33a5e234b42f3454de
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="systemobject-methods"></a><span data-ttu-id="ab14e-102">System.Object metody</span><span class="sxs-lookup"><span data-stu-id="ab14e-102">System.Object Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="ab14e-103">podporuje následující <xref:System.Object> metody.</span><span class="sxs-lookup"><span data-stu-id="ab14e-103"> supports the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="ab14e-104">nepodporuje následující <xref:System.Object> metody.</span><span class="sxs-lookup"><span data-stu-id="ab14e-104"> does not support the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<span data-ttu-id="ab14e-105"><xref:System.Object.ToString?displayProperty=nameWithType>pro binární typy, jako `BINARY`, `VARBINARY`, `IMAGE`, a `TIMESTAMP`.</span><span class="sxs-lookup"><span data-stu-id="ab14e-105"><xref:System.Object.ToString?displayProperty=nameWithType> for binary types such as `BINARY`, `VARBINARY`, `IMAGE`, and `TIMESTAMP`.</span></span>||  
  
## <a name="differences-from-net"></a><span data-ttu-id="ab14e-106">Rozdíl oproti rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="ab14e-106">Differences from .NET</span></span>  
 <span data-ttu-id="ab14e-107">Výstup <xref:System.Object.ToString?displayProperty=nameWithType> pro dvojitou používá SQL `CONVERT`(NVARCHAR(30), @x, 2) na SQL.</span><span class="sxs-lookup"><span data-stu-id="ab14e-107">The output of <xref:System.Object.ToString?displayProperty=nameWithType> for double uses SQL `CONVERT`(NVARCHAR(30), @x, 2) on SQL.</span></span> <span data-ttu-id="ab14e-108">SQL vždy používá 16 číslic a vědecká notace v tomto případě (například "0.000000000000000e + 000" 0).</span><span class="sxs-lookup"><span data-stu-id="ab14e-108">SQL always uses 16 digits and scientific notation in this case (for example, "0.000000000000000e+000" for 0).</span></span> <span data-ttu-id="ab14e-109">V důsledku toho <xref:System.Object.ToString?displayProperty=nameWithType> převod nevytváří stejné řetězec jako <xref:System.Convert.ToString%2A?displayProperty=nameWithType> v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ab14e-109">As a result, <xref:System.Object.ToString?displayProperty=nameWithType> conversion does not produce the same string as <xref:System.Convert.ToString%2A?displayProperty=nameWithType> in the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab14e-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab14e-110">See Also</span></span>  
 [<span data-ttu-id="ab14e-111">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="ab14e-111">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
