---
title: 'Postupy: použití uložených procedur, které přijímají parametry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: faf4ea9c52b91c3fc0f2f775e7bd5dfe039c53a8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738109"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a>Postupy: použití uložených procedur, které přijímají parametry
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapuje výstupní parametry na referenční parametry a pro typy hodnot deklaruje parametr jako Nullable.  
  
 Příklad použití vstupního parametru v dotazu, který vrací sadu řádků, naleznete v tématu [How to: Return sady řádků](how-to-return-rowsets.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad přijímá jeden vstupní parametr (ID zákazníka) a vrací výstupní parametr (celkový prodej tohoto zákazníka).  
  
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
 Tuto uloženou proceduru zavoláte takto:  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Uložené procedury](stored-procedures.md)
- [Stažení ukázkových databází](downloading-sample-databases.md)
- [Typy hodnot s možnou hodnotou null (C#)](../../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
- [Typy hodnot s možnou hodnotou null (Visual Basic)](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
