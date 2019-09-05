---
title: Přizpůsobení operací výhradně pomocí uložených procedur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: a242ecdc774d67721aee640e75847317c1b815d6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247549"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a><span data-ttu-id="91606-102">Přizpůsobení operací výhradně pomocí uložených procedur</span><span class="sxs-lookup"><span data-stu-id="91606-102">Customizing Operations by Using Stored Procedures Exclusively</span></span>
<span data-ttu-id="91606-103">Přístup k datům pomocí uložených procedur je běžným scénářem.</span><span class="sxs-lookup"><span data-stu-id="91606-103">Access to data by using only stored procedures is a common scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91606-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="91606-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="91606-105">Popis</span><span class="sxs-lookup"><span data-stu-id="91606-105">Description</span></span>  
 <span data-ttu-id="91606-106">Můžete upravit příklad poskytnutý v části [přizpůsobení operací pomocí uložených procedur](customizing-operations-by-using-stored-procedures.md) tak, že nahradíte i první dotaz (což způsobí dynamické provádění SQL) s voláním metody, která zabalí uloženou proceduru.</span><span class="sxs-lookup"><span data-stu-id="91606-106">You can modify the example provided in [Customizing Operations By Using Stored Procedures](customizing-operations-by-using-stored-procedures.md) by replacing even the first query (which causes dynamic SQL execution) with a method call that wraps a stored procedure.</span></span>  
  
 <span data-ttu-id="91606-107">Přepokládejme `CustomersByCity` je metoda, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="91606-107">Assume `CustomersByCity` is the method, as in the following example.</span></span>  
  
### <a name="code"></a><span data-ttu-id="91606-108">Kód</span><span class="sxs-lookup"><span data-stu-id="91606-108">Code</span></span>  
 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 <span data-ttu-id="91606-109">Následující kód se provede bez dynamického SQL.</span><span class="sxs-lookup"><span data-stu-id="91606-109">The following code executes without any dynamic SQL.</span></span>  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="91606-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91606-110">See also</span></span>

- [<span data-ttu-id="91606-111">Odpovědnosti vývojáře při přepisu výchozího chování</span><span class="sxs-lookup"><span data-stu-id="91606-111">Responsibilities of the Developer In Overriding Default Behavior</span></span>](responsibilities-of-the-developer-in-overriding-default-behavior.md)
