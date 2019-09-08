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
# <a name="systemobject-methods"></a>Metody System.Object
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podporuje následující <xref:System.Object> metody.  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nepodporuje následující <xref:System.Object> metody.  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>`BINARY`pro binární typy, jako například `VARBINARY`, `IMAGE`, `TIMESTAMP`a.||  
  
## <a name="differences-from-net"></a>Rozdíly od .NET  
 Výstup <xref:System.Object.ToString?displayProperty=nameWithType> pro Double používá SQL `CONVERT`(nvarchar (30), @x, 2) v SQL. SQL vždycky v tomto případě používá 16 číslic a vědecký zápis (například "0.000000000000000 e + 000" pro 0). V důsledku toho <xref:System.Object.ToString?displayProperty=nameWithType> převod nevytvoří stejný řetězec jako <xref:System.Convert.ToString%2A?displayProperty=nameWithType> v .NET Framework.  
  
## <a name="see-also"></a>Viz také:

- [Datové typy a funkce](data-types-and-functions.md)
