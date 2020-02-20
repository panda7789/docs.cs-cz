---
title: Uložené procedury CLR
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: ca0fd2d33f0ad56c96fb63530e6ba3f7f7890f81
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450359"
---
# <a name="clr-stored-procedures"></a>Uložené procedury CLR
Uložené procedury jsou rutiny, které nelze použít v skalárních výrazech. Mohou vracet tabulkové výsledky a zprávy klientovi, vyvolat příkazy DDL (Data Definition Language) a jazyka DML (data remanipulace Language) a vracet výstupní parametry.  
  
> [!NOTE]
> Microsoft Visual Basic nepodporuje výstupní parametry stejným způsobem jako Microsoft Visual C# . Musíte určit, že se má parametr předat odkazem a použít atribut \<out () >, který představuje výstupní parametr, jak je uvedeno v následujícím seznamu:  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
Podrobnější informace najdete v [dokumentaci verze SQL Server](/sql) pro verzi SQL Server, kterou používáte.
  
 **Dokumentace SQL Serveru**

1. [Uložené procedury CLR](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms131094(v=sql.100))  
  
## <a name="see-also"></a>Viz také

- [Vytváření objektů SQL Server 2005 ve spravovaném kódu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))
- [Přehled ADO.NET](../ado-net-overview.md)
