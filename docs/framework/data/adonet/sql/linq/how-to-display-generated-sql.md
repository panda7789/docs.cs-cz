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
# <a name="how-to-display-generated-sql"></a>Postupy: zobrazení vygenerovaných SQL
Můžete zobrazit kód SQL generovaný pro dotazy a změnit zpracování pomocí vlastnosti <xref:System.Data.Linq.DataContext.Log%2A>. Tento přístup může být užitečný pro porozumění funkcím [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a k ladění specifických problémů.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá vlastnost <xref:System.Data.Linq.DataContext.Log%2A> k zobrazení kódu SQL v okně konzoly před provedením kódu.  Tuto vlastnost můžete použít s příkazy Query, INSERT, Update a DELETE.  
  
 Řádky z okna konzoly jsou to, co vidíte při spuštění Visual Basic nebo C# kódu, který následuje.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Podpora ladění](debugging-support.md)
