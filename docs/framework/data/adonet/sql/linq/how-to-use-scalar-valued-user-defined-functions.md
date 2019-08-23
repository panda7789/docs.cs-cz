---
title: 'Postupy: Použití uživatelem definovaných funkcí se skalárními hodnotami'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: 0d757e3c37f347014eb2ef90b4e61ddd205dd012
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938671"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a>Postupy: Použití uživatelem definovaných funkcí se skalárními hodnotami
Metodu klienta definovanou pro třídu lze namapovat na uživatelsky definovanou funkci pomocí <xref:System.Data.Linq.Mapping.FunctionAttribute> atributu. Všimněte si, že tělo metody vytvoří výraz, který zachycuje záměr volání metody, a předá tento výraz <xref:System.Data.Linq.DataContext> pro účely překladu a provedení.  
  
> [!NOTE]
> K přímému provedení dojde pouze v případě, že je funkce volána mimo dotaz. Další informace najdete v tématu [jak: Volání uživatelsky definovaných funkcí je](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)vloženo.  
  
## <a name="example"></a>Příklad  
 Následující kód SQL prezentuje uživatelsky definovanou funkci `ReverseCustName()`s skalární hodnotou.  
  
```  
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

- [Uživatelem definované funkce](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
