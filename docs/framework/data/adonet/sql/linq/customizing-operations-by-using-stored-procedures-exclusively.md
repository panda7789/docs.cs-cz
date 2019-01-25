---
title: Přizpůsobení operací pomocí uložených procedur komponentami TableAdapter výhradně
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: 0dd8687bac8aa8ce046fb89c109debd91409aca8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573540"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a><span data-ttu-id="8e01b-102">Přizpůsobení operací pomocí uložených procedur komponentami TableAdapter výhradně</span><span class="sxs-lookup"><span data-stu-id="8e01b-102">Customizing Operations by Using Stored Procedures Exclusively</span></span>
<span data-ttu-id="8e01b-103">Přístup k datům s použitím pouze uložené procedury je běžný scénář.</span><span class="sxs-lookup"><span data-stu-id="8e01b-103">Access to data by using only stored procedures is a common scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e01b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e01b-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="8e01b-105">Popis</span><span class="sxs-lookup"><span data-stu-id="8e01b-105">Description</span></span>  
 <span data-ttu-id="8e01b-106">Můžete upravit v příkladu v [přizpůsobení operací pomocí pomocí uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) nahrazením volání metody, která obaluje uloženou proceduru i první dotaz (což způsobí, že spuštění dynamické SQL).</span><span class="sxs-lookup"><span data-stu-id="8e01b-106">You can modify the example provided in [Customizing Operations By Using Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) by replacing even the first query (which causes dynamic SQL execution) with a method call that wraps a stored procedure.</span></span>  
  
 <span data-ttu-id="8e01b-107">Předpokládejme `CustomersByCity` je metoda, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8e01b-107">Assume `CustomersByCity` is the method, as in the following example.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8e01b-108">Kód</span><span class="sxs-lookup"><span data-stu-id="8e01b-108">Code</span></span>  
 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 <span data-ttu-id="8e01b-109">Následující kód provede bez jakékoli dynamické SQL.</span><span class="sxs-lookup"><span data-stu-id="8e01b-109">The following code executes without any dynamic SQL.</span></span>  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="8e01b-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e01b-110">See also</span></span>
- [<span data-ttu-id="8e01b-111">Odpovědnosti vývojáře při přepisu výchozího chování</span><span class="sxs-lookup"><span data-stu-id="8e01b-111">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
