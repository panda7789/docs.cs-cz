---
title: "Příkazy ke změně dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5c574a5e880dd838397b35df48138079cb58e2cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-commands-to-modify-data"></a><span data-ttu-id="e03bf-102">Příkazy ke změně dat</span><span class="sxs-lookup"><span data-stu-id="e03bf-102">Using Commands to Modify Data</span></span>
<span data-ttu-id="e03bf-103">Pomocí zprostředkovatele dat .NET Framework, můžete spustit uložené procedury nebo příkazy data definition language (například CREATE TABLE a ALTER COLUMN) k provedení manipulaci schématu v databázi nebo katalogu.</span><span class="sxs-lookup"><span data-stu-id="e03bf-103">Using a .NET Framework data provider, you can execute stored procedures or data definition language statements (for example, CREATE TABLE and ALTER COLUMN) to perform schema manipulation on a database or catalog.</span></span> <span data-ttu-id="e03bf-104">Tyto příkazy nevrátí řádky jako dotaz způsobem, proto **příkaz** objekt poskytuje **ExecuteNonQuery** pro jejich zpracování.</span><span class="sxs-lookup"><span data-stu-id="e03bf-104">These commands do not return rows as a query would, so the **Command** object provides an **ExecuteNonQuery** to process them.</span></span>  
  
 <span data-ttu-id="e03bf-105">Kromě používání **ExecuteNonQuery** k úpravě schématu, můžete také použít tuto metodu za účelem proces příkazy SQL, který měnit data, ale které nejsou vrátí řádky, jako je například vložení, aktualizace a odstranit.</span><span class="sxs-lookup"><span data-stu-id="e03bf-105">In addition to using **ExecuteNonQuery** to modify schema, you can also use this method to process SQL statements that modify data but that do not return rows, such as INSERT, UPDATE, and DELETE.</span></span>  
  
 <span data-ttu-id="e03bf-106">I když nejsou vrácených řádků **ExecuteNonQuery** metoda, vstupní a výstupní parametry a návratové hodnoty můžete být předán a vrácených prostřednictvím **parametry** kolekce **příkaz**  objektu.</span><span class="sxs-lookup"><span data-stu-id="e03bf-106">Although rows are not returned by the **ExecuteNonQuery** method, input and output parameters and return values can be passed and returned via the **Parameters** collection of the **Command** object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e03bf-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e03bf-107">In This Section</span></span>  
 [<span data-ttu-id="e03bf-108">Aktualizace dat ve zdroji dat</span><span class="sxs-lookup"><span data-stu-id="e03bf-108">Updating Data in a Data Source</span></span>](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 <span data-ttu-id="e03bf-109">Popisuje, jak spustit příkazy nebo uložené procedury, které upravují data v databázi.</span><span class="sxs-lookup"><span data-stu-id="e03bf-109">Describes how to execute commands or stored procedures that modify data in a database.</span></span>  
  
 [<span data-ttu-id="e03bf-110">Provádění operací katalogu</span><span class="sxs-lookup"><span data-stu-id="e03bf-110">Performing Catalog Operations</span></span>](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 <span data-ttu-id="e03bf-111">Popisuje, jak provést příkazy, které upravují schématu databáze.</span><span class="sxs-lookup"><span data-stu-id="e03bf-111">Describes how to execute commands that modify database schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e03bf-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="e03bf-112">See Also</span></span>  
 [<span data-ttu-id="e03bf-113">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e03bf-113">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="e03bf-114">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="e03bf-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="e03bf-115">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="e03bf-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
