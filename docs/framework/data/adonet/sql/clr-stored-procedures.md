---
title: Uložené procedury CLR
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: 1f8aa6fb9243706d07caa4527af0c4c880aa70a6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503108"
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

1. [Uložené procedury CLR](https://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a>Viz také  
 [Vytváření objektů serveru SQL Server 2005 ve spravovaném kódu](https://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
