---
title: 'Postupy: Použití uložených procedur, které přijímají parametry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: 8dd463c895efcddfe288fe1dc8571981872d9d80
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033603"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a>Postupy: Použití uložených procedur, které přijímají parametry
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapuje výstupní parametry k odkazování parametrů a typů hodnot deklaruje parametr jako s možnou hodnotou Null.  
  
 Příklad použití jako vstupní parametr v dotazu, který vrátí sadu řádků, naleznete v tématu [jak: Vrácení sad řádků](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu má jeden vstupní parametr (ID zákazníka) a vrátí parametr out (celkový prodej daného zákazníka).  
  
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
 Tuto uloženou proceduru by volat následujícím způsobem:  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
- [Stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [Použití typů s povolenou hodnotou Null](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md)
- [Typy hodnot s povolenou hodnotou Null](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
