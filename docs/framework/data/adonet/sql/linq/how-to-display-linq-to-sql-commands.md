---
title: 'Postupy: zobrazení LINQ to SQLch příkazů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1decb05e-37ad-4ed6-ab2f-071eb4c4f628
ms.openlocfilehash: ec5010a42980e2d7a1a03c31d396cac6b6934a58
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002934"
---
# <a name="how-to-display-linq-to-sql-commands"></a><span data-ttu-id="b6cd3-102">Postupy: zobrazení LINQ to SQLch příkazů</span><span class="sxs-lookup"><span data-stu-id="b6cd3-102">How to: Display LINQ to SQL Commands</span></span>
<span data-ttu-id="b6cd3-103">Pomocí <xref:System.Data.Linq.DataContext.GetCommand%2A> můžete zobrazit příkazy SQL a další informace.</span><span class="sxs-lookup"><span data-stu-id="b6cd3-103">Use <xref:System.Data.Linq.DataContext.GetCommand%2A> to display SQL commands and other information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6cd3-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b6cd3-104">Example</span></span>  
 <span data-ttu-id="b6cd3-105">V následujícím příkladu okno konzoly zobrazí výstup z dotazu následovaný příkazy SQL, které jsou vygenerovány, typem příkazů a typem připojení.</span><span class="sxs-lookup"><span data-stu-id="b6cd3-105">In the following example, the console window displays the output from the query, followed by the SQL commands that are generated, the type of commands, and the type of connection.</span></span>  
  
 [!code-csharp[DLinqDebuggingSupport#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#3)]
 [!code-vb[DLinqDebuggingSupport#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#3)]  
  
 <span data-ttu-id="b6cd3-106">Výstup se zobrazí takto:</span><span class="sxs-lookup"><span data-stu-id="b6cd3-106">Output appears as follows:</span></span>  
  
```console  
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
  
```console  
Command Text:  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
  
Command Type: Text  
  
Connection: System.Data.SqlClient.SqlConnection  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6cd3-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6cd3-107">See also</span></span>

- [<span data-ttu-id="b6cd3-108">Podpora ladění</span><span class="sxs-lookup"><span data-stu-id="b6cd3-108">Debugging Support</span></span>](debugging-support.md)
