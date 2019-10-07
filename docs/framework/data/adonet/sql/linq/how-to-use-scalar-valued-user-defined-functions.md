---
title: 'Postupy: použití uživatelem definovaných funkcí s skalární hodnotou'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: dfe82fd50eb3eedeaff9082a4288901f72197795
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003234"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a>Postupy: použití uživatelem definovaných funkcí s skalární hodnotou
Metodu klienta definovanou pro třídu lze namapovat na uživatelsky definovanou funkci pomocí atributu <xref:System.Data.Linq.Mapping.FunctionAttribute>. Všimněte si, že tělo metody vytvoří výraz, který zachycuje záměr volání metody, a předá tento výraz <xref:System.Data.Linq.DataContext> pro účely překladu a provedení.  
  
> [!NOTE]
> K přímému provedení dojde pouze v případě, že je funkce volána mimo dotaz. Další informace naleznete v tématu [How to: Calling User-Defined Functions inline](how-to-call-user-defined-functions-inline.md).  
  
## <a name="example"></a>Příklad  
 Následující kód SQL prezentuje uživatelem definovanou funkci `ReverseCustName()`.  
  
```sql  
CREATE FUNCTION ReverseCustName(@string varchar(100))  
RETURNS varchar(100)  
AS  
BEGIN  
    DECLARE @custName varchar(100)  
    -- Implementation left as exercise for users.  
    RETURN @custName  
END  
```  
  
 Namapujete metodu klienta, například následující pro tento kód:  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Uživatelem definované funkce](user-defined-functions.md)
