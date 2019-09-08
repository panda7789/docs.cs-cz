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
# <a name="systemmath-methods"></a><span data-ttu-id="02b47-102">Metody System.Math</span><span class="sxs-lookup"><span data-stu-id="02b47-102">System.Math Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="02b47-103">nepodporuje následující <xref:System.Math> metody.</span><span class="sxs-lookup"><span data-stu-id="02b47-103">does not support the following <xref:System.Math> methods.</span></span>  
  
- <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a><span data-ttu-id="02b47-104">Rozdíly od .NET</span><span class="sxs-lookup"><span data-stu-id="02b47-104">Differences from .NET</span></span>  
 <span data-ttu-id="02b47-105">.NET Framework má odlišnou sémantiku zaokrouhlení z SQL Server.</span><span class="sxs-lookup"><span data-stu-id="02b47-105">The .NET Framework has different rounding semantics from SQL Server.</span></span> <span data-ttu-id="02b47-106">Metoda v .NET Framework provádí *zaokrouhlování bank*, kde čísla, která končí od 0,5 do nejbližší sudé číslice namísto na další vyšší číslici. <xref:System.Math.Round%2A></span><span class="sxs-lookup"><span data-stu-id="02b47-106">The <xref:System.Math.Round%2A> method in the .NET Framework performs *Banker's rounding*, where numbers that ends in .5 round to the nearest even digit instead of to the next higher digit.</span></span> <span data-ttu-id="02b47-107">Například 2,5 se zaokrouhlí na 2, zatímco 3,5 zaokrouhlí na 4.</span><span class="sxs-lookup"><span data-stu-id="02b47-107">For example, 2.5 rounds to 2, while 3.5 rounds to 4.</span></span> <span data-ttu-id="02b47-108">(Tato technika pomáhá vyhnout se systematickému posunu směrem k vyšším hodnotám ve velkých transakcích dat.)</span><span class="sxs-lookup"><span data-stu-id="02b47-108">(This technique helps avoid systematic bias toward higher values in large data transactions.)</span></span>  
  
 <span data-ttu-id="02b47-109">`ROUND` Funkce v SQL místo toho vždycky zaokrouhlí na 0.</span><span class="sxs-lookup"><span data-stu-id="02b47-109">In SQL, the `ROUND` function instead always rounds away from 0.</span></span> <span data-ttu-id="02b47-110">Proto 2,5 zaokrouhlí na 3, v porovnání s jeho zaokrouhlením na 2 v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="02b47-110">Therefore 2.5 rounds to 3, contrasted with its rounding to 2 in the .NET Framework.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="02b47-111">projde sémantikou SQL `ROUND` a nepokusí se implementovat zaokrouhlování bank.</span><span class="sxs-lookup"><span data-stu-id="02b47-111">passes through to the SQL `ROUND` semantics and does not try to implement Banker's rounding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02b47-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02b47-112">See also</span></span>

- [<span data-ttu-id="02b47-113">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="02b47-113">Data Types and Functions</span></span>](data-types-and-functions.md)
