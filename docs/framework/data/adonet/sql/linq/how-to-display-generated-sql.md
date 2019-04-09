---
title: 'Postupy: Zobrazení generovaného SQL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 626492c0-5ee3-4675-88e8-8c40379510b6
ms.openlocfilehash: 8a69b3ae83d7f701428b3183f2b80e0d44a06537
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103620"
---
# <a name="how-to-display-generated-sql"></a>Postupy: Zobrazení generovaného SQL
Můžete zobrazit SQL kód generovaný pro dotazy a zpracování pomocí změny <xref:System.Data.Linq.DataContext.Log%2A> vlastnost. Tento přístup může být užitečné pro porozumění [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] funkce a pro specifické problémy ladění.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Data.Linq.DataContext.Log%2A> vlastnosti k zobrazení kódu SQL v okně konzoly předtím, než je kód spuštěn.  Můžete tuto vlastnost použít dotazování, vložení, aktualizace a odstranění příkazů.  
  
 Co se zobrazí po spuštění jazyka Visual Basic jsou řádky z okna konzoly nebo C# kód, který následuje.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Podpora ladění](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
