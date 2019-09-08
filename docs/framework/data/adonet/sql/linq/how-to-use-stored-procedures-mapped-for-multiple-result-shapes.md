---
title: 'Postupy: Použití uložených procedur mapovaných pro vícečetné tvary výsledků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: d32faf026789923ca4343271c9fd1b6bbdb068df
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793089"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a>Postupy: Použití uložených procedur mapovaných pro vícečetné tvary výsledků
Pokud uložená procedura může vracet více tvarů výsledků, nemůže být návratový typ silným typem pro jeden obrazec projekce. I [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] když může generovat všechny možné typy projekce, nemůže znát pořadí, ve kterém se budou vracet.  
  
 Porovnejte tento scénář s uloženými procedurami, které vydávají více výsledných tvarů postupně. Další informace najdete v tématu [jak: Použijte uložené procedury mapované pro obrazce](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)sekvenčních výsledků.  
  
 <xref:System.Data.Linq.Mapping.ResultTypeAttribute> Atribut je použit pro uložené procedury, které vracejí více výsledků typů pro určení sady typů, které může procedura vracet.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu kódu SQL závisí obrazec výsledek na vstupu (`shape =1` nebo `shape = 2`). Nevíte, které projekce se budou vracet jako první.  
  
```  
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a>Příklad  
 Chcete-li provést tuto uloženou proceduru, použijte kód podobný následujícímu.  
  
> [!NOTE]
> Je nutné použít <xref:System.Data.Linq.IMultipleResults.GetResult%2A> vzor pro získání výčtu správného typu na základě vaší znalosti uložené procedury.  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Uložené procedury](stored-procedures.md)
