---
title: Použití příkazů pro změny dat
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: f2e3d162bfbdcb79cfecefa4ddc8e6a0dc46ee3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61875950"
---
# <a name="using-commands-to-modify-data"></a><span data-ttu-id="74a36-102">Použití příkazů pro změny dat</span><span class="sxs-lookup"><span data-stu-id="74a36-102">Using Commands to Modify Data</span></span>
<span data-ttu-id="74a36-103">Pomocí zprostředkovatele dat .NET Framework, může spustit uložené procedury nebo příkazy data definition language (například CREATE TABLE a ALTER COLUMN), provádět manipulace s schématu databáze nebo katalogu.</span><span class="sxs-lookup"><span data-stu-id="74a36-103">Using a .NET Framework data provider, you can execute stored procedures or data definition language statements (for example, CREATE TABLE and ALTER COLUMN) to perform schema manipulation on a database or catalog.</span></span> <span data-ttu-id="74a36-104">Tyto příkazy nevracejí řádky jako dotaz, takže **příkaz** objekt, který poskytuje **metodu ExecuteNonQuery** pro jejich zpracování.</span><span class="sxs-lookup"><span data-stu-id="74a36-104">These commands do not return rows as a query would, so the **Command** object provides an **ExecuteNonQuery** to process them.</span></span>  
  
 <span data-ttu-id="74a36-105">Kromě použití **metodu ExecuteNonQuery** k úpravě schématu, můžete také použít tuto metodu za účelem procesu SQL příkazy, které mění data, ale který vracet řádky, jako jsou INSERT, UPDATE a odstranit.</span><span class="sxs-lookup"><span data-stu-id="74a36-105">In addition to using **ExecuteNonQuery** to modify schema, you can also use this method to process SQL statements that modify data but that do not return rows, such as INSERT, UPDATE, and DELETE.</span></span>  
  
 <span data-ttu-id="74a36-106">I když nejsou řádků vrácených **metodu ExecuteNonQuery** metoda, vstupní a výstupní parametry a návratové hodnoty je možné předaný a vrácena prostřednictvím **parametry** kolekce **příkaz**  objektu.</span><span class="sxs-lookup"><span data-stu-id="74a36-106">Although rows are not returned by the **ExecuteNonQuery** method, input and output parameters and return values can be passed and returned via the **Parameters** collection of the **Command** object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="74a36-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="74a36-107">In This Section</span></span>  
 [<span data-ttu-id="74a36-108">Aktualizace dat ve zdroji dat</span><span class="sxs-lookup"><span data-stu-id="74a36-108">Updating Data in a Data Source</span></span>](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 <span data-ttu-id="74a36-109">Popisuje, jak spustit příkazy nebo uložené procedury, které mění data v databázi.</span><span class="sxs-lookup"><span data-stu-id="74a36-109">Describes how to execute commands or stored procedures that modify data in a database.</span></span>  
  
 [<span data-ttu-id="74a36-110">Provádění operací katalogu</span><span class="sxs-lookup"><span data-stu-id="74a36-110">Performing Catalog Operations</span></span>](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 <span data-ttu-id="74a36-111">Popisuje, jak spouštět příkazy, které upravují schéma databáze.</span><span class="sxs-lookup"><span data-stu-id="74a36-111">Describes how to execute commands that modify database schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74a36-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74a36-112">See also</span></span>

- [<span data-ttu-id="74a36-113">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="74a36-113">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="74a36-114">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="74a36-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="74a36-115">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="74a36-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
