---
title: "Postupy: pomocí uložených procedur, které provést parametry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 28f389d7128283501291bc3220cfde3815cc0713
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a>Postupy: pomocí uložených procedur, které provést parametry
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]mapuje výstupní parametry tak, aby odkazovaly parametry a u typů hodnot deklaruje parametr jako s možnou hodnotou Null.  
  
 Příklad použití vstupní parametr v dotazu, který vrací sadu řádků, naleznete v části [postupy: vrácení sady řádků](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu má jeden vstupní parametr (ID zákazníka) a vrátí parametr typu out (celkový prodej tohoto zákazníka).  
  
```  
CREATE PROCEDURE [dbo].[CustOrderTotal]   
@CustomerID nchar(5),  
@TotalSales money OUTPUT  
AS  
SELECT @TotalSales = SUM(OD.UNITPRICE*(1-OD.DISCOUNT) * OD.QUANTITY)  
FROM ORDERS O, "ORDER DETAILS" OD  
where O.CUSTOMERID = @CustomerID AND O.ORDERID = OD.ORDERID  
```  
  
 [!code-csharp[DLinqSprox#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#2)]
 [!code-vb[DLinqSprox#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#2)]  
  
## <a name="example"></a>Příklad  
 Tuto uloženou proceduru by volání následujícím způsobem:  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 [Uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 [Stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [Použití typů s povolenou hodnotou Null](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md)  
 [Typy hodnot s povolenou hodnotou Null](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
