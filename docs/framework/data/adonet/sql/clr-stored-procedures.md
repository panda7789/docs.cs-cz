---
title: Uložené procedury CLR
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: a1a37ac1257594913c6d06cb08df2882e8773da8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554631"
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="65597-102">Uložené procedury CLR</span><span class="sxs-lookup"><span data-stu-id="65597-102">CLR Stored Procedures</span></span>
<span data-ttu-id="65597-103">Uložené procedury jsou rutiny, které nelze použít v skalární výrazy.</span><span class="sxs-lookup"><span data-stu-id="65597-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="65597-104">Můžete vrácena klientovi tabulkové výsledky a zprávy, vyvolání jazyka pro definici dat (DDL) a příkazy jazyka (DML) zpracování dat a vrátí výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="65597-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65597-105">Microsoft Visual Basic nepodporuje výstupní parametry stejným způsobem, který Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="65597-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="65597-106">Je nutné zadat předat parametr odkazem a aplikovat \<Out() > atribut pro výstupní parametr, stejně jako v následující reprezentaci:</span><span class="sxs-lookup"><span data-stu-id="65597-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
<span data-ttu-id="65597-107">Další informace najdete v tématu verzi [dokumentaci k SQL serveru](/sql) pro verzi systému SQL Server používáte.</span><span class="sxs-lookup"><span data-stu-id="65597-107">For more detailed information, see the version of [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="65597-108">**Dokumentaci k SQL serveru**</span><span class="sxs-lookup"><span data-stu-id="65597-108">**SQL Server documentation**</span></span>

1. [<span data-ttu-id="65597-109">Uložené procedury CLR</span><span class="sxs-lookup"><span data-stu-id="65597-109">CLR Stored Procedures</span></span>](https://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a><span data-ttu-id="65597-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65597-110">See also</span></span>
- [<span data-ttu-id="65597-111">Vytváření objektů serveru SQL Server 2005 ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="65597-111">Creating SQL Server 2005 Objects In Managed Code</span></span>](https://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)
- [<span data-ttu-id="65597-112">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="65597-112">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
