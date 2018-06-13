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
# <a name="how-to-display-generated-sql"></a>Postupy: zobrazení generované SQL
Můžete zobrazit kód SQL vygenerované dotazy a zpracování pomocí změny <xref:System.Data.Linq.DataContext.Log%2A> vlastnost. Tento přístup může být užitečné při hledání [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] funkcí a pro ladění konkrétních problémů.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Data.Linq.DataContext.Log%2A> vlastnost k zobrazení SQL kódu v okně konzoly, před provedením kód.  Můžete tuto vlastnost použít s dotazu, vložení, aktualizace a odstranění příkazy.  
  
 Co se zobrazí při spuštění kódu Visual Basic a C#, který následuje jsou řádky z okna konzoly.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Podpora ladění](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
