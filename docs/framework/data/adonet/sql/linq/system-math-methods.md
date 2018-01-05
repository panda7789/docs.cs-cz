---
title: System.Math metody
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8c5f19918ca1c80daffab482436ab6ce018321f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="systemmath-methods"></a>System.Math metody
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nepodporuje následující <xref:System.Math> metody.  
  
-   <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a>Rozdíl oproti rozhraní .NET  
 Rozhraní .NET Framework má jiný zaokrouhlení sémantiku ze serveru SQL Server. <xref:System.Math.Round%2A> Metoda v rozhraní .NET Framework provádí *Banker je zaokrouhlení*, kde čísla, které končí v.5 zaokrouhlit na nejbližší i číslice místo pro další vyšší číslice. Například 2.5 zaokrouhlí na 2, zatímco 3.5 zaokrouhlí na 4. (Tento postup umožňuje vyhnout se systematické odchylka směrem k vyšší hodnoty ve velkých objemů dat transakce.)  
  
 V systému SQL `ROUND` funkce místo vždy zaokrouhlí směrem od 0. Proto 2.5 zaokrouhlí do 3, rozdíl od aktualizovaného zaokrouhlení 2 v rozhraní .NET Framework.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]předá prostřednictvím SQL `ROUND` sémantiku a nepokusí implementovat bankovní zaokrouhlení.  
  
## <a name="see-also"></a>Viz také  
 [Datové typy a funkce](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
