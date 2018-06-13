---
title: CLR uložené procedury
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: c0a318d2d11788d274da637cd1846f72159cd013
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358586"
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="09271-102">CLR uložené procedury</span><span class="sxs-lookup"><span data-stu-id="09271-102">CLR Stored Procedures</span></span>
<span data-ttu-id="09271-103">Uložené procedury jsou rutiny, které nelze použít v skalární výrazy.</span><span class="sxs-lookup"><span data-stu-id="09271-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="09271-104">Můžete vrátit tabulkové výsledky a zprávy do klienta, vyvolání jazyk definice dat (DDL) a příkazy jazyka (DML) manipulaci dat a vrátí výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="09271-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09271-105">Microsoft Visual Basic nepodporuje výstupní parametry stejným způsobem, jakým Microsoft Visual C# nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="09271-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="09271-106">Je nutné zadat parametr předání odkazem a použít \<Out() > atribut představují výstupní parametr, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="09271-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```  
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```  
  
 <span data-ttu-id="09271-107">Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="09271-107">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="09271-108">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="09271-108">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="09271-109">Uložené procedury CLR</span><span class="sxs-lookup"><span data-stu-id="09271-109">CLR Stored Procedures</span></span>](http://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a><span data-ttu-id="09271-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="09271-110">See Also</span></span>  
 [<span data-ttu-id="09271-111">Vytváření objektů serveru SQL Server 2005 ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="09271-111">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="09271-112">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="09271-112">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
