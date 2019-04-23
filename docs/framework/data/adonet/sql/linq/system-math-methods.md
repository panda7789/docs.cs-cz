---
title: Metody System.Math
ms.date: 03/30/2017
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
ms.openlocfilehash: 1dae31b30962505c07c198f3bd35fceb8f400efb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141710"
---
# <a name="systemmath-methods"></a><span data-ttu-id="2b9ca-102">Metody System.Math</span><span class="sxs-lookup"><span data-stu-id="2b9ca-102">System.Math Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="2b9ca-103">nepodporuje následující <xref:System.Math> metody.</span><span class="sxs-lookup"><span data-stu-id="2b9ca-103">does not support the following <xref:System.Math> methods.</span></span>  
  
-   <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a><span data-ttu-id="2b9ca-104">Rozdíl oproti .NET</span><span class="sxs-lookup"><span data-stu-id="2b9ca-104">Differences from .NET</span></span>  
 <span data-ttu-id="2b9ca-105">Rozhraní .NET Framework má odlišnou sémantiku zaokrouhlení z SQL serveru.</span><span class="sxs-lookup"><span data-stu-id="2b9ca-105">The .NET Framework has different rounding semantics from SQL Server.</span></span> <span data-ttu-id="2b9ca-106"><xref:System.Math.Round%2A> Provádí metoda v rozhraní .NET Framework *je bankovní zaokrouhlení*, kde čísla, která končí v.5 zaokrouhlit na nejbližší sudé číslice místo na další vyšší číslo.</span><span class="sxs-lookup"><span data-stu-id="2b9ca-106">The <xref:System.Math.Round%2A> method in the .NET Framework performs *Banker's rounding*, where numbers that ends in .5 round to the nearest even digit instead of to the next higher digit.</span></span> <span data-ttu-id="2b9ca-107">Například 2.5 zaokrouhlí na 2, zatímco 3.5 zaokrouhlí na 4.</span><span class="sxs-lookup"><span data-stu-id="2b9ca-107">For example, 2.5 rounds to 2, while 3.5 rounds to 4.</span></span> <span data-ttu-id="2b9ca-108">(Tento postup pomáhá zabránit systematické Posun směrem k vyšší hodnoty ve velkých objemů dat transakcí.)</span><span class="sxs-lookup"><span data-stu-id="2b9ca-108">(This technique helps avoid systematic bias toward higher values in large data transactions.)</span></span>  
  
 <span data-ttu-id="2b9ca-109">V SQL `ROUND` funkce místo toho vždy zaokrouhlí směrem od 0.</span><span class="sxs-lookup"><span data-stu-id="2b9ca-109">In SQL, the `ROUND` function instead always rounds away from 0.</span></span> <span data-ttu-id="2b9ca-110">Proto 2.5 zaokrouhlí na 3, rozdíly s jeho zaokrouhluje se směrem 2 v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2b9ca-110">Therefore 2.5 rounds to 3, contrasted with its rounding to 2 in the .NET Framework.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="2b9ca-111">prochází na SQL `ROUND` sémantiku a nepokusí se implementovat bankovní zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="2b9ca-111">passes through to the SQL `ROUND` semantics and does not try to implement Banker's rounding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b9ca-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b9ca-112">See also</span></span>

- [<span data-ttu-id="2b9ca-113">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="2b9ca-113">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
