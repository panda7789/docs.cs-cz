---
title: Uložené procedury CLR
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: df323e2d1b50dcd1b2087141deefa1c86723b346
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930109"
---
# <a name="clr-stored-procedures"></a>Uložené procedury CLR
Uložené procedury jsou rutiny, které nelze použít v skalární výrazy. Můžete vrácena klientovi tabulkové výsledky a zprávy, vyvolání jazyka pro definici dat (DDL) a příkazy jazyka (DML) zpracování dat a vrátí výstupní parametry.  
  
> [!NOTE]
>  Microsoft Visual Basic nepodporuje výstupní parametry stejným způsobem, který Microsoft Visual C#. Je nutné zadat předat parametr odkazem a aplikovat \<Out() > atribut pro výstupní parametr, stejně jako v následující reprezentaci:  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
Další informace najdete v tématu verzi [dokumentaci k SQL serveru](/sql) pro verzi systému SQL Server používáte.
  
 **Dokumentaci k SQL serveru**

1. [Uložené procedury CLR](http://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a>Viz také  
 [Vytváření objektů serveru SQL Server 2005 ve spravovaném kódu](http://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](http://go.microsoft.com/fwlink/?LinkId=217917)
