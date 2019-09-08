---
title: 'Postupy: Použití uživatelem definovaných funkcí se skalárními hodnotami'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: da4e5e8fe4682191a0c8e2b0ce6a7b945fe63deb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781470"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a>Postupy: Použití uživatelem definovaných funkcí se skalárními hodnotami
Metodu klienta definovanou pro třídu lze namapovat na uživatelsky definovanou funkci pomocí <xref:System.Data.Linq.Mapping.FunctionAttribute> atributu. Všimněte si, že tělo metody vytvoří výraz, který zachycuje záměr volání metody, a předá tento výraz <xref:System.Data.Linq.DataContext> pro účely překladu a provedení.  
  
> [!NOTE]
> K přímému provedení dojde pouze v případě, že je funkce volána mimo dotaz. Další informace najdete v tématu [jak: Volání uživatelsky definovaných funkcí je](how-to-call-user-defined-functions-inline.md)vloženo.  
  
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

- [Uživatelem definované funkce](user-defined-functions.md)
