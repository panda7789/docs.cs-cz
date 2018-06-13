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
# <a name="systemobject-methods"></a>System.Object metody
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje následující <xref:System.Object> metody.  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nepodporuje následující <xref:System.Object> metody.  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType> pro binární typy, jako `BINARY`, `VARBINARY`, `IMAGE`, a `TIMESTAMP`.||  
  
## <a name="differences-from-net"></a>Rozdíl oproti rozhraní .NET  
 Výstup <xref:System.Object.ToString?displayProperty=nameWithType> pro dvojitou používá SQL `CONVERT`(NVARCHAR(30), @x, 2) na SQL. SQL vždy používá 16 číslic a vědecká notace v tomto případě (například "0.000000000000000e + 000" 0). V důsledku toho <xref:System.Object.ToString?displayProperty=nameWithType> převod nevytváří stejné řetězec jako <xref:System.Convert.ToString%2A?displayProperty=nameWithType> v rozhraní .NET Framework.  
  
## <a name="see-also"></a>Viz také  
 [Datové typy a funkce](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
