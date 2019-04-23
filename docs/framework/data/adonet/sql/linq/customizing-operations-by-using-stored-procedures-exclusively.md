---
title: Přizpůsobení operací výhradně pomocí uložených procedur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: 61230ffc5cd055ee64de9d519cdfb4d76c856ca3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59128645"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a><span data-ttu-id="e138e-102">Přizpůsobení operací výhradně pomocí uložených procedur</span><span class="sxs-lookup"><span data-stu-id="e138e-102">Customizing Operations by Using Stored Procedures Exclusively</span></span>
<span data-ttu-id="e138e-103">Přístup k datům s použitím pouze uložené procedury je běžný scénář.</span><span class="sxs-lookup"><span data-stu-id="e138e-103">Access to data by using only stored procedures is a common scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e138e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e138e-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="e138e-105">Popis</span><span class="sxs-lookup"><span data-stu-id="e138e-105">Description</span></span>  
 <span data-ttu-id="e138e-106">Můžete upravit v příkladu v [přizpůsobení operací pomocí pomocí uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) nahrazením volání metody, která obaluje uloženou proceduru i první dotaz (což způsobí, že spuštění dynamické SQL).</span><span class="sxs-lookup"><span data-stu-id="e138e-106">You can modify the example provided in [Customizing Operations By Using Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) by replacing even the first query (which causes dynamic SQL execution) with a method call that wraps a stored procedure.</span></span>  
  
 <span data-ttu-id="e138e-107">Předpokládejme `CustomersByCity` je metoda, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e138e-107">Assume `CustomersByCity` is the method, as in the following example.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e138e-108">Kód</span><span class="sxs-lookup"><span data-stu-id="e138e-108">Code</span></span>  
 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 <span data-ttu-id="e138e-109">Následující kód provede bez jakékoli dynamické SQL.</span><span class="sxs-lookup"><span data-stu-id="e138e-109">The following code executes without any dynamic SQL.</span></span>  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="e138e-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e138e-110">See also</span></span>

- [<span data-ttu-id="e138e-111">Odpovědnosti vývojáře při přepisu výchozího chování</span><span class="sxs-lookup"><span data-stu-id="e138e-111">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
