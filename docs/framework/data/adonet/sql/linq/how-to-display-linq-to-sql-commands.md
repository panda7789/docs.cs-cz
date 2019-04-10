---
title: 'Postupy: Zobrazení příkazů LINQ to SQL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1decb05e-37ad-4ed6-ab2f-071eb4c4f628
ms.openlocfilehash: d71eaf834ebf36d462f8581f0074b2f6a90bae17
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211605"
---
# <a name="how-to-display-linq-to-sql-commands"></a><span data-ttu-id="77a6e-102">Postupy: Zobrazení příkazů LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="77a6e-102">How to: Display LINQ to SQL Commands</span></span>
<span data-ttu-id="77a6e-103">Použití <xref:System.Data.Linq.DataContext.GetCommand%2A> zobrazit příkazy jazyka SQL a další informace.</span><span class="sxs-lookup"><span data-stu-id="77a6e-103">Use <xref:System.Data.Linq.DataContext.GetCommand%2A> to display SQL commands and other information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77a6e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="77a6e-104">Example</span></span>  
 <span data-ttu-id="77a6e-105">V následujícím příkladu se v okně konzoly se zobrazí výstup z dotazu, za nímž následuje příkazy SQL, které jsou generovány, typ příkazů a typ připojení.</span><span class="sxs-lookup"><span data-stu-id="77a6e-105">In the following example, the console window displays the output from the query, followed by the SQL commands that are generated, the type of commands, and the type of connection.</span></span>  
  
 [!code-csharp[DLinqDebuggingSupport#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#3)]
 [!code-vb[DLinqDebuggingSupport#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#3)]  
  
 <span data-ttu-id="77a6e-106">Zobrazí se následující výstup:</span><span class="sxs-lookup"><span data-stu-id="77a6e-106">Output appears as follows:</span></span>  
  
```  
Customers from London:  
    Thomas Hardy  
    Victoria Ashworth  
    Elizabeth Brown  
    Ann Devon  
    Simon Crowther  
    Marie Bertrand  
    Hari Kumar  
    Dominique Perrier  
```  
  
```  
Command Text:  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
  
Command Type: Text  
  
Connection: System.Data.SqlClient.SqlConnection  
```  
  
## <a name="see-also"></a><span data-ttu-id="77a6e-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77a6e-107">See also</span></span>

- [<span data-ttu-id="77a6e-108">Podpora ladění</span><span class="sxs-lookup"><span data-stu-id="77a6e-108">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
