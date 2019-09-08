---
title: Metody System.Object
ms.date: 03/30/2017
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
ms.openlocfilehash: d1a36798ef789bbc44f581dfc631feee19e1f66b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781073"
---
# <a name="systemobject-methods"></a><span data-ttu-id="8392d-102">Metody System.Object</span><span class="sxs-lookup"><span data-stu-id="8392d-102">System.Object Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="8392d-103">podporuje následující <xref:System.Object> metody.</span><span class="sxs-lookup"><span data-stu-id="8392d-103">supports the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="8392d-104">nepodporuje následující <xref:System.Object> metody.</span><span class="sxs-lookup"><span data-stu-id="8392d-104">does not support the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<span data-ttu-id="8392d-105"><xref:System.Object.ToString?displayProperty=nameWithType>`BINARY`pro binární typy, jako například `VARBINARY`, `IMAGE`, `TIMESTAMP`a.</span><span class="sxs-lookup"><span data-stu-id="8392d-105"><xref:System.Object.ToString?displayProperty=nameWithType> for binary types such as `BINARY`, `VARBINARY`, `IMAGE`, and `TIMESTAMP`.</span></span>||  
  
## <a name="differences-from-net"></a><span data-ttu-id="8392d-106">Rozdíly od .NET</span><span class="sxs-lookup"><span data-stu-id="8392d-106">Differences from .NET</span></span>  
 <span data-ttu-id="8392d-107">Výstup <xref:System.Object.ToString?displayProperty=nameWithType> pro Double používá SQL `CONVERT`(nvarchar (30), @x, 2) v SQL.</span><span class="sxs-lookup"><span data-stu-id="8392d-107">The output of <xref:System.Object.ToString?displayProperty=nameWithType> for double uses SQL `CONVERT`(NVARCHAR(30), @x, 2) on SQL.</span></span> <span data-ttu-id="8392d-108">SQL vždycky v tomto případě používá 16 číslic a vědecký zápis (například "0.000000000000000 e + 000" pro 0).</span><span class="sxs-lookup"><span data-stu-id="8392d-108">SQL always uses 16 digits and scientific notation in this case (for example, "0.000000000000000e+000" for 0).</span></span> <span data-ttu-id="8392d-109">V důsledku toho <xref:System.Object.ToString?displayProperty=nameWithType> převod nevytvoří stejný řetězec jako <xref:System.Convert.ToString%2A?displayProperty=nameWithType> v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8392d-109">As a result, <xref:System.Object.ToString?displayProperty=nameWithType> conversion does not produce the same string as <xref:System.Convert.ToString%2A?displayProperty=nameWithType> in the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8392d-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8392d-110">See also</span></span>

- [<span data-ttu-id="8392d-111">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="8392d-111">Data Types and Functions</span></span>](data-types-and-functions.md)
