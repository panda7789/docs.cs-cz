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
ms.openlocfilehash: 1e55222c16d223a86e1e11ce2b985ec0f4d8eaa3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="740ca-102">CLR uložené procedury</span><span class="sxs-lookup"><span data-stu-id="740ca-102">CLR Stored Procedures</span></span>
<span data-ttu-id="740ca-103">Uložené procedury jsou rutiny, které nelze použít v skalární výrazy.</span><span class="sxs-lookup"><span data-stu-id="740ca-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="740ca-104">Můžete vrátit tabulkové výsledky a zprávy do klienta, vyvolání jazyk definice dat (DDL) a příkazy jazyka (DML) manipulaci dat a vrátí výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="740ca-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="740ca-105">Microsoft Visual Basic nepodporuje výstupní parametry stejným způsobem, jakým Microsoft Visual C# nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="740ca-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="740ca-106">Je nutné zadat parametr předání odkazem a použít \<Out() > atribut představují výstupní parametr, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="740ca-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```  
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```  
  
 <span data-ttu-id="740ca-107">Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="740ca-107">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="740ca-108">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="740ca-108">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="740ca-109">CLR uložené procedury</span><span class="sxs-lookup"><span data-stu-id="740ca-109">CLR Stored Procedures</span></span>](http://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a><span data-ttu-id="740ca-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="740ca-110">See Also</span></span>  
 [<span data-ttu-id="740ca-111">Vytváření objektů serveru SQL Server 2005 ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="740ca-111">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="740ca-112">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="740ca-112">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
