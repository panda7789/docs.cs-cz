---
title: 'Postupy: Zobrazení generovaného SQL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 626492c0-5ee3-4675-88e8-8c40379510b6
ms.openlocfilehash: 9c293757b642f0a945097c4ea4299d97cadddbcc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725685"
---
# <a name="how-to-display-generated-sql"></a><span data-ttu-id="feedf-102">Postupy: Zobrazení generovaného SQL</span><span class="sxs-lookup"><span data-stu-id="feedf-102">How to: Display Generated SQL</span></span>
<span data-ttu-id="feedf-103">Můžete zobrazit SQL kód generovaný pro dotazy a zpracování pomocí změny <xref:System.Data.Linq.DataContext.Log%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="feedf-103">You can view the SQL code generated for queries and change processing by using the <xref:System.Data.Linq.DataContext.Log%2A> property.</span></span> <span data-ttu-id="feedf-104">Tento přístup může být užitečné pro porozumění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] funkce a pro specifické problémy ladění.</span><span class="sxs-lookup"><span data-stu-id="feedf-104">This approach can be useful for understanding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] functionality and for debugging specific problems.</span></span>  
  
## <a name="example"></a><span data-ttu-id="feedf-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="feedf-105">Example</span></span>  
 <span data-ttu-id="feedf-106">V následujícím příkladu <xref:System.Data.Linq.DataContext.Log%2A> vlastnosti k zobrazení kódu SQL v okně konzoly předtím, než je kód spuštěn.</span><span class="sxs-lookup"><span data-stu-id="feedf-106">The following example uses the <xref:System.Data.Linq.DataContext.Log%2A> property to display SQL code in the console window before the code is executed.</span></span>  <span data-ttu-id="feedf-107">Můžete tuto vlastnost použít dotazování, vložení, aktualizace a odstranění příkazů.</span><span class="sxs-lookup"><span data-stu-id="feedf-107">You can use this property with query, insert, update, and delete commands.</span></span>  
  
 <span data-ttu-id="feedf-108">Co se zobrazí po spuštění jazyka Visual Basic jsou řádky z okna konzoly nebo C# kód, který následuje.</span><span class="sxs-lookup"><span data-stu-id="feedf-108">The lines from the console window are what you see when you execute the Visual Basic or C# code that follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="feedf-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="feedf-109">See also</span></span>
- [<span data-ttu-id="feedf-110">Podpora ladění</span><span class="sxs-lookup"><span data-stu-id="feedf-110">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
