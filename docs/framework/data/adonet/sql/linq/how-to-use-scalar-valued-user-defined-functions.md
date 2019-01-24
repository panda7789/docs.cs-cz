---
title: 'Postupy: Použití funkce vracející skalární uživatelem definované'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: 33c6ae89184b90ba69cc9c3c01f0b1ec9d7ff1cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661682"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a>Postupy: Použití funkce vracející skalární uživatelem definované
Můžete namapovat metodu klienta definované na třídu pro uživatelem definované funkce s použitím <xref:System.Data.Linq.Mapping.FunctionAttribute> atribut. Všimněte si, že tělo metody vytvoří výraz, který zachycuje cílem volání metody a předá tento výraz, který se <xref:System.Data.Linq.DataContext> pro překlad a spuštění.  
  
> [!NOTE]
>  Přímé provádění dojde pouze v případě, že funkce je volána mimo dotazu. Další informace najdete v tématu [jak: Volat uživatelsky definovaných funkcí](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md).  
  
## <a name="example"></a>Příklad  
 Následující kód SQL představuje funkce vracející skalární uživatelem definované `ReverseCustName()`.  
  
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
  
 Umožní mapování pro tento kód metodu klienta například následující:  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a>Viz také:
- [Uživatelem definované funkce](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
