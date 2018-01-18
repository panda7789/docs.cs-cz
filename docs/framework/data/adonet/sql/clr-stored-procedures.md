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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: aebc681482482c364f762b12065cf041f4976be9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
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
