---
title: CLR uložené procedury
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: c0a318d2d11788d274da637cd1846f72159cd013
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="clr-stored-procedures"></a>CLR uložené procedury
Uložené procedury jsou rutiny, které nelze použít v skalární výrazy. Můžete vrátit tabulkové výsledky a zprávy do klienta, vyvolání jazyk definice dat (DDL) a příkazy jazyka (DML) manipulaci dat a vrátí výstupní parametry.  
  
> [!NOTE]
>  Microsoft Visual Basic nepodporuje výstupní parametry stejným způsobem, jakým Microsoft Visual C# nepodporuje. Je nutné zadat parametr předání odkazem a použít \<Out() > atribut představují výstupní parametr, jako v následujícím příkladu:  
  
```  
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```  
  
 Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.  
  
 **SQL Server Books Online**  
  
1.  [Uložené procedury CLR](http://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a>Viz také  
 [Vytváření objektů serveru SQL Server 2005 ve spravovaném kódu](http://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
