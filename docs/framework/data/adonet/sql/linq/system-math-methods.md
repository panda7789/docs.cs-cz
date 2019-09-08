---
title: Metody System.Math
ms.date: 03/30/2017
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
ms.openlocfilehash: 0b113cefa6be040924134f9d2d0cb0c9d334feef
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792388"
---
# <a name="systemmath-methods"></a>Metody System.Math
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nepodporuje následující <xref:System.Math> metody.  
  
- <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a>Rozdíly od .NET  
 .NET Framework má odlišnou sémantiku zaokrouhlení z SQL Server. Metoda v .NET Framework provádí *zaokrouhlování bank*, kde čísla, která končí od 0,5 do nejbližší sudé číslice namísto na další vyšší číslici. <xref:System.Math.Round%2A> Například 2,5 se zaokrouhlí na 2, zatímco 3,5 zaokrouhlí na 4. (Tato technika pomáhá vyhnout se systematickému posunu směrem k vyšším hodnotám ve velkých transakcích dat.)  
  
 `ROUND` Funkce v SQL místo toho vždycky zaokrouhlí na 0. Proto 2,5 zaokrouhlí na 3, v porovnání s jeho zaokrouhlením na 2 v .NET Framework.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]projde sémantikou SQL `ROUND` a nepokusí se implementovat zaokrouhlování bank.  
  
## <a name="see-also"></a>Viz také:

- [Datové typy a funkce](data-types-and-functions.md)
