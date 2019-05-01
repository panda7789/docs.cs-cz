---
title: 'Postupy: Použití uživatelem definovaných funkcí se skalárními hodnotami'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: ffb24468c81cb4ec9f41645f8888c2c4ba021609
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033576"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a>Postupy: Použití uživatelem definovaných funkcí se skalárními hodnotami
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
