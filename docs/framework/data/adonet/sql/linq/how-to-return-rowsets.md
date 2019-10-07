---
title: 'Postupy: vrácení sad řádků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
ms.openlocfilehash: b853a6f2175009cbcbc01c14a6732b98e37e1a7f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003058"
---
# <a name="how-to-return-rowsets"></a>Postupy: vrácení sad řádků
Tento příklad vrátí sadu řádků z databáze a obsahuje vstupní parametr pro filtrování výsledku.  
  
 Když spustíte uloženou proceduru, která vrací sadu řádků, použijete *výslednou* třídu, která ukládá návraty z uložené procedury. Další informace najdete v tématu [analýza zdrojového kódu LINQ to SQL](analyzing-linq-to-sql-source-code.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad představuje uloženou proceduru, která vrací řádky zákazníků, a používá vstupní parametr, který vrátí pouze řádky, které uvádějí "Londýn" jako město zákazníka. Příklad předpokládá vyčíslitelné třídy `CustomersByCityResult`.  
  
```sql  
CREATE PROCEDURE [dbo].[Customers By City]  
    (@param1 NVARCHAR(20))  
AS  
BEGIN  
    -- SET NOCOUNT ON added to prevent extra result sets from  
    -- interfering with SELECT statements.  
    SET NOCOUNT ON;  
    SELECT CustomerID, ContactName, CompanyName, City from Customers  
        as c where c.City=@param1  
END  
```  
  
 [!code-csharp[DLinqSprox#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#1)]
 [!code-vb[DLinqSprox#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Uložené procedury](stored-procedures.md)
- [Stažení ukázkových databází](downloading-sample-databases.md)
