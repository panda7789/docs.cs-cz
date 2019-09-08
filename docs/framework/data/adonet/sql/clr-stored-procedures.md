---
title: Uložené procedury CLR
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: d2fde4fdcd5ab63906256d814256578b9baa9ecd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782497"
---
# <a name="clr-stored-procedures"></a>Uložené procedury CLR
Uložené procedury jsou rutiny, které nelze použít v skalárních výrazech. Mohou vracet tabulkové výsledky a zprávy klientovi, vyvolat příkazy DDL (Data Definition Language) a jazyka DML (data remanipulace Language) a vracet výstupní parametry.  
  
> [!NOTE]
> Microsoft Visual Basic nepodporuje výstupní parametry stejným způsobem jako Microsoft Visual C# . Musíte určit, že se má parametr předat odkazem a použít \<atribut out () >, který představuje výstupní parametr, jak je uvedeno v následujícím seznamu:  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
Podrobnější informace najdete v [dokumentaci verze SQL Server](/sql) pro verzi SQL Server, kterou používáte.
  
 **Dokumentace k SQL Server**

1. [Uložené procedury CLR](https://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a>Viz také:

- [Vytváření objektů SQL Server 2005 ve spravovaném kódu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))
- [Přehled ADO.NET](../ado-net-overview.md)
