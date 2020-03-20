---
title: 'Postupy: Převzetí parametrů pomocí uložených procedur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: 05ecc467f75fbeda785b4bac1c3b8b1ceeb173b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174326"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a>Postupy: Převzetí parametrů pomocí uložených procedur
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]mapuje výstupní parametry na referenční parametry a pro typy hodnot deklaruje parametr jako hodnotitelný.  
  
 Příklad použití vstupního parametru v dotazu, který vrací sadu řádků, najdete v tématu [How to: Return Rowsets](how-to-return-rowsets.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad přebírá jeden vstupní parametr (ID zákazníka) a vrátí out parametr (celkový prodej pro tohoto zákazníka).  
  
```sql
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
 Tuto uloženou proceduru byste nazvali takto:  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Viz také

- [Uložené procedury](stored-procedures.md)
- [Stažení ukázkových databází](downloading-sample-databases.md)
- [Typy hodnot s hodnotou s hodnotou null (C#)](../../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
- [Typy hodnot s povolenou hodnotou Null (Visual Basic)](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
