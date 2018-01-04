---
title: "Přizpůsobení operace pomocí uložené procedury výhradně"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: eba9e4462c1a71708173994dfb3efaf4199248c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a><span data-ttu-id="d0d68-102">Přizpůsobení operace pomocí uložené procedury výhradně</span><span class="sxs-lookup"><span data-stu-id="d0d68-102">Customizing Operations by Using Stored Procedures Exclusively</span></span>
<span data-ttu-id="d0d68-103">Přístup k datům s použitím pouze uložené procedury je běžný scénář.</span><span class="sxs-lookup"><span data-stu-id="d0d68-103">Access to data by using only stored procedures is a common scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0d68-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d0d68-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="d0d68-105">Popis</span><span class="sxs-lookup"><span data-stu-id="d0d68-105">Description</span></span>  
 <span data-ttu-id="d0d68-106">Můžete upravit v příkladu v [přizpůsobení Operations podle pomocí uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) nahrazením i první dotaz, (což způsobí, že dynamické provedení SQL) volání metody, která zabalí uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="d0d68-106">You can modify the example provided in [Customizing Operations By Using Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) by replacing even the first query (which causes dynamic SQL execution) with a method call that wraps a stored procedure.</span></span>  
  
 <span data-ttu-id="d0d68-107">Předpokládejme `CustomersByCity` je metoda, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d0d68-107">Assume `CustomersByCity` is the method, as in the following example.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d0d68-108">Kód</span><span class="sxs-lookup"><span data-stu-id="d0d68-108">Code</span></span>  
 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 <span data-ttu-id="d0d68-109">Následující kód spustí bez žádné dynamické SQL.</span><span class="sxs-lookup"><span data-stu-id="d0d68-109">The following code executes without any dynamic SQL.</span></span>  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="d0d68-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0d68-110">See Also</span></span>  
 [<span data-ttu-id="d0d68-111">Odpovědnosti vývojáře při přepisu výchozího chování</span><span class="sxs-lookup"><span data-stu-id="d0d68-111">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
