---
title: 'Postupy: zobrazení generované SQL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 626492c0-5ee3-4675-88e8-8c40379510b6
ms.openlocfilehash: edc0f8fea2768391a47e12940cbe083e41852f1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361705"
---
# <a name="how-to-display-generated-sql"></a><span data-ttu-id="90327-102">Postupy: zobrazení generované SQL</span><span class="sxs-lookup"><span data-stu-id="90327-102">How to: Display Generated SQL</span></span>
<span data-ttu-id="90327-103">Můžete zobrazit kód SQL vygenerované dotazy a zpracování pomocí změny <xref:System.Data.Linq.DataContext.Log%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="90327-103">You can view the SQL code generated for queries and change processing by using the <xref:System.Data.Linq.DataContext.Log%2A> property.</span></span> <span data-ttu-id="90327-104">Tento přístup může být užitečné při hledání [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] funkcí a pro ladění konkrétních problémů.</span><span class="sxs-lookup"><span data-stu-id="90327-104">This approach can be useful for understanding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] functionality and for debugging specific problems.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90327-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="90327-105">Example</span></span>  
 <span data-ttu-id="90327-106">Následující příklad používá <xref:System.Data.Linq.DataContext.Log%2A> vlastnost k zobrazení SQL kódu v okně konzoly, před provedením kód.</span><span class="sxs-lookup"><span data-stu-id="90327-106">The following example uses the <xref:System.Data.Linq.DataContext.Log%2A> property to display SQL code in the console window before the code is executed.</span></span>  <span data-ttu-id="90327-107">Můžete tuto vlastnost použít s dotazu, vložení, aktualizace a odstranění příkazy.</span><span class="sxs-lookup"><span data-stu-id="90327-107">You can use this property with query, insert, update, and delete commands.</span></span>  
  
 <span data-ttu-id="90327-108">Co se zobrazí při spuštění kódu Visual Basic a C#, který následuje jsou řádky z okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="90327-108">The lines from the console window are what you see when you execute the Visual Basic or C# code that follows.</span></span>  
  
```  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
-- @p0: Input String (Size = 6; Prec = 0; Scale = 0) [London]  
-- Context: SqlProvider(Sql2005) Model: AttributedMetaModel Build: 3.5.20810.0  
```  
  
```  
AROUT  
BSBEV  
CONSH  
EASTC  
NORTS  
SEVES  
```  
  
 [!code-csharp[DLinqDebuggingSupport#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#1)]
 [!code-vb[DLinqDebuggingSupport#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="90327-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="90327-109">See Also</span></span>  
 [<span data-ttu-id="90327-110">Podpora ladění</span><span class="sxs-lookup"><span data-stu-id="90327-110">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
