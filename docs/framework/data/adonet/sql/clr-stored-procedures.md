---
title: "CLR uložené procedury"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: dfed0124c33c90427c9b888f5aa7bb191aea0400
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
 [Vytváření objektů serveru SQL Server 2005 ve spravovaném kódu](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
