---
title: 'Postupy: zobrazení vygenerovaných SQL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 626492c0-5ee3-4675-88e8-8c40379510b6
ms.openlocfilehash: 15fc6a50d232ea12b229b7b2790c0398bc1c370d
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002977"
---
# <a name="how-to-display-generated-sql"></a><span data-ttu-id="92540-102">Postupy: zobrazení vygenerovaných SQL</span><span class="sxs-lookup"><span data-stu-id="92540-102">How to: Display Generated SQL</span></span>
<span data-ttu-id="92540-103">Můžete zobrazit kód SQL generovaný pro dotazy a změnit zpracování pomocí vlastnosti <xref:System.Data.Linq.DataContext.Log%2A>.</span><span class="sxs-lookup"><span data-stu-id="92540-103">You can view the SQL code generated for queries and change processing by using the <xref:System.Data.Linq.DataContext.Log%2A> property.</span></span> <span data-ttu-id="92540-104">Tento přístup může být užitečný pro porozumění funkcím [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a k ladění specifických problémů.</span><span class="sxs-lookup"><span data-stu-id="92540-104">This approach can be useful for understanding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] functionality and for debugging specific problems.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92540-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="92540-105">Example</span></span>  
 <span data-ttu-id="92540-106">Následující příklad používá vlastnost <xref:System.Data.Linq.DataContext.Log%2A> k zobrazení kódu SQL v okně konzoly před provedením kódu.</span><span class="sxs-lookup"><span data-stu-id="92540-106">The following example uses the <xref:System.Data.Linq.DataContext.Log%2A> property to display SQL code in the console window before the code is executed.</span></span>  <span data-ttu-id="92540-107">Tuto vlastnost můžete použít s příkazy Query, INSERT, Update a DELETE.</span><span class="sxs-lookup"><span data-stu-id="92540-107">You can use this property with query, insert, update, and delete commands.</span></span>  
  
 <span data-ttu-id="92540-108">Řádky z okna konzoly jsou to, co vidíte při spuštění Visual Basic nebo C# kódu, který následuje.</span><span class="sxs-lookup"><span data-stu-id="92540-108">The lines from the console window are what you see when you execute the Visual Basic or C# code that follows.</span></span>  
  
```console  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
-- @p0: Input String (Size = 6; Prec = 0; Scale = 0) [London]  
-- Context: SqlProvider(Sql2005) Model: AttributedMetaModel Build: 3.5.20810.0  
```  
  
```console  
AROUT  
BSBEV  
CONSH  
EASTC  
NORTS  
SEVES  
```  
  
 [!code-csharp[DLinqDebuggingSupport#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#1)]
 [!code-vb[DLinqDebuggingSupport#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="92540-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92540-109">See also</span></span>

- [<span data-ttu-id="92540-110">Podpora ladění</span><span class="sxs-lookup"><span data-stu-id="92540-110">Debugging Support</span></span>](debugging-support.md)
