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
# <a name="clr-stored-procedures"></a><span data-ttu-id="180dd-102">Uložené procedury CLR</span><span class="sxs-lookup"><span data-stu-id="180dd-102">CLR Stored Procedures</span></span>
<span data-ttu-id="180dd-103">Uložené procedury jsou rutiny, které nelze použít v skalárních výrazech.</span><span class="sxs-lookup"><span data-stu-id="180dd-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="180dd-104">Mohou vracet tabulkové výsledky a zprávy klientovi, vyvolat příkazy DDL (Data Definition Language) a jazyka DML (data remanipulace Language) a vracet výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="180dd-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="180dd-105">Microsoft Visual Basic nepodporuje výstupní parametry stejným způsobem jako Microsoft Visual C# .</span><span class="sxs-lookup"><span data-stu-id="180dd-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="180dd-106">Musíte určit, že se má parametr předat odkazem a použít \<atribut out () >, který představuje výstupní parametr, jak je uvedeno v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="180dd-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
<span data-ttu-id="180dd-107">Podrobnější informace najdete v [dokumentaci verze SQL Server](/sql) pro verzi SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="180dd-107">For more detailed information, see the version of [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="180dd-108">**Dokumentace k SQL Server**</span><span class="sxs-lookup"><span data-stu-id="180dd-108">**SQL Server documentation**</span></span>

1. [<span data-ttu-id="180dd-109">Uložené procedury CLR</span><span class="sxs-lookup"><span data-stu-id="180dd-109">CLR Stored Procedures</span></span>](https://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a><span data-ttu-id="180dd-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="180dd-110">See also</span></span>

- <span data-ttu-id="180dd-111">[Vytváření objektů SQL Server 2005 ve spravovaném kódu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="180dd-111">[Creating SQL Server 2005 Objects In Managed Code](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span></span>
- [<span data-ttu-id="180dd-112">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="180dd-112">ADO.NET Overview</span></span>](../ado-net-overview.md)
