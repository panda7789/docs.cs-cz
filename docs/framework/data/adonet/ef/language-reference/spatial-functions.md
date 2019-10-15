---
title: Prostorové funkce
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: eba384e77389f82006479f165178e80fcac244b1
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319305"
---
# <a name="spatial-functions"></a>Prostorové funkce
Pro prostorové typy neexistuje žádný řetězcový formát. Můžete však použít kanonické Entity Framework funkce, které zavoláte pomocí řetězců ve známém formátu textu. Například následující volání funkce vytvoří bod geometrie:  
  
```sql  
GeometryFromText('POINT (43 -73)')  
```  
  
 Metody <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> mají všechny prostorové kanonické Entity Framework metody. Pokud chcete zjistit, jaké parametry by měly být předány funkci, klikněte na metodu, která vás zajímá.
