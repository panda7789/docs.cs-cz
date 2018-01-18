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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: cfcbf915703c72211fc9d958abfda7ffac8aafdc
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="systemmath-methods"></a><span data-ttu-id="75e6b-102">System.Math metody</span><span class="sxs-lookup"><span data-stu-id="75e6b-102">System.Math Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="75e6b-103">nepodporuje následující <xref:System.Math> metody.</span><span class="sxs-lookup"><span data-stu-id="75e6b-103"> does not support the following <xref:System.Math> methods.</span></span>  
  
-   <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a><span data-ttu-id="75e6b-104">Rozdíl oproti rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="75e6b-104">Differences from .NET</span></span>  
 <span data-ttu-id="75e6b-105">Rozhraní .NET Framework má jiný zaokrouhlení sémantiku ze serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="75e6b-105">The .NET Framework has different rounding semantics from SQL Server.</span></span> <span data-ttu-id="75e6b-106"><xref:System.Math.Round%2A> Metoda v rozhraní .NET Framework provádí *Banker je zaokrouhlení*, kde čísla, které končí v.5 zaokrouhlit na nejbližší i číslice místo pro další vyšší číslice.</span><span class="sxs-lookup"><span data-stu-id="75e6b-106">The <xref:System.Math.Round%2A> method in the .NET Framework performs *Banker's rounding*, where numbers that ends in .5 round to the nearest even digit instead of to the next higher digit.</span></span> <span data-ttu-id="75e6b-107">Například 2.5 zaokrouhlí na 2, zatímco 3.5 zaokrouhlí na 4.</span><span class="sxs-lookup"><span data-stu-id="75e6b-107">For example, 2.5 rounds to 2, while 3.5 rounds to 4.</span></span> <span data-ttu-id="75e6b-108">(Tento postup umožňuje vyhnout se systematické odchylka směrem k vyšší hodnoty ve velkých objemů dat transakce.)</span><span class="sxs-lookup"><span data-stu-id="75e6b-108">(This technique helps avoid systematic bias toward higher values in large data transactions.)</span></span>  
  
 <span data-ttu-id="75e6b-109">V systému SQL `ROUND` funkce místo vždy zaokrouhlí směrem od 0.</span><span class="sxs-lookup"><span data-stu-id="75e6b-109">In SQL, the `ROUND` function instead always rounds away from 0.</span></span> <span data-ttu-id="75e6b-110">Proto 2.5 zaokrouhlí do 3, rozdíl od aktualizovaného zaokrouhlení 2 v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="75e6b-110">Therefore 2.5 rounds to 3, contrasted with its rounding to 2 in the .NET Framework.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="75e6b-111">předá prostřednictvím SQL `ROUND` sémantiku a nepokusí implementovat bankovní zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="75e6b-111"> passes through to the SQL `ROUND` semantics and does not try to implement Banker's rounding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75e6b-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="75e6b-112">See Also</span></span>  
 [<span data-ttu-id="75e6b-113">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="75e6b-113">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
