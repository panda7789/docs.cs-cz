---
title: 'Postupy: Použití uložených procedur, které přijímají parametry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: c2b657f704d072b987578be5520a58d007ecac37
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353017"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a>Postupy: Použití uložených procedur, které přijímají parametry
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapuje výstupní parametry na referenční parametry a pro typy hodnot deklaruje parametr jako Nullable.  
  
 Příklad použití vstupního parametru v dotazu, který vrací sadu řádků, naleznete v tématu [How na: Vrátí sady řádků @ no__t-0.  
  
## <a name="example"></a>Příklad  
 Následující příklad přijímá jeden vstupní parametr (ID zákazníka) a vrací výstupní parametr (celkový prodej tohoto zákazníka).  
  
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
 Tuto uloženou proceduru zavoláte takto:  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Uložené procedury](stored-procedures.md)
- [Stažení ukázkových databází](downloading-sample-databases.md)
- [Použití typů hodnot s možnou hodnotou null](../../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [Typy hodnot s povolenou hodnotou Null](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
