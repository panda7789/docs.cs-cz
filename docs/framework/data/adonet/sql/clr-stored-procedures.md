---
title: Uložené procedury CLR
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: 1459ebc9c24875bcd7e8b0d711d710c514df0dd4
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56093863"
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
  
## <a name="see-also"></a>Viz také:
- [Vytváření objektů serveru SQL Server 2005 ve spravovaném kódu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
