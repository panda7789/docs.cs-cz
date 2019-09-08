---
title: Použití příkazů pro změny dat
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: 34c73549f18cd4bebb8caf842b252828b7f0a185
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780563"
---
# <a name="using-commands-to-modify-data"></a><span data-ttu-id="38575-102">Použití příkazů pro změny dat</span><span class="sxs-lookup"><span data-stu-id="38575-102">Using Commands to Modify Data</span></span>
<span data-ttu-id="38575-103">Pomocí poskytovatele .NET Framework dat můžete spustit uložené procedury nebo příkazy jazyka definice dat (například CREATE TABLE a ALTER COLUMN) a provádět tak manipulaci se schématem v databázi nebo katalogu.</span><span class="sxs-lookup"><span data-stu-id="38575-103">Using a .NET Framework data provider, you can execute stored procedures or data definition language statements (for example, CREATE TABLE and ALTER COLUMN) to perform schema manipulation on a database or catalog.</span></span> <span data-ttu-id="38575-104">Tyto příkazy nevrací řádky jako dotaz, takže objekt **Command** poskytuje **ExecuteNonQuery** pro jejich zpracování.</span><span class="sxs-lookup"><span data-stu-id="38575-104">These commands do not return rows as a query would, so the **Command** object provides an **ExecuteNonQuery** to process them.</span></span>  
  
 <span data-ttu-id="38575-105">Kromě použití **ExecuteNonQuery** ke změně schématu můžete také použít tuto metodu ke zpracování příkazů SQL, které mění data, ale nevrací řádky, jako je například vložení, aktualizace a odstranění.</span><span class="sxs-lookup"><span data-stu-id="38575-105">In addition to using **ExecuteNonQuery** to modify schema, you can also use this method to process SQL statements that modify data but that do not return rows, such as INSERT, UPDATE, and DELETE.</span></span>  
  
 <span data-ttu-id="38575-106">I když řádky nejsou vraceny metodou **ExecuteNonQuery** , vstupní a výstupní parametry a návratové hodnoty mohou být předány a vráceny prostřednictvím kolekce **Parameters** objektu **příkazu** .</span><span class="sxs-lookup"><span data-stu-id="38575-106">Although rows are not returned by the **ExecuteNonQuery** method, input and output parameters and return values can be passed and returned via the **Parameters** collection of the **Command** object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="38575-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="38575-107">In This Section</span></span>  
 [<span data-ttu-id="38575-108">Aktualizace dat ve zdroji dat</span><span class="sxs-lookup"><span data-stu-id="38575-108">Updating Data in a Data Source</span></span>](updating-data-in-a-data-source.md)  
 <span data-ttu-id="38575-109">Popisuje, jak spustit příkazy nebo uložené procedury, které upravují data v databázi.</span><span class="sxs-lookup"><span data-stu-id="38575-109">Describes how to execute commands or stored procedures that modify data in a database.</span></span>  
  
 [<span data-ttu-id="38575-110">Provádění operací katalogu</span><span class="sxs-lookup"><span data-stu-id="38575-110">Performing Catalog Operations</span></span>](performing-catalog-operations.md)  
 <span data-ttu-id="38575-111">Popisuje, jak provést příkazy, které mění schéma databáze.</span><span class="sxs-lookup"><span data-stu-id="38575-111">Describes how to execute commands that modify database schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38575-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38575-112">See also</span></span>

- [<span data-ttu-id="38575-113">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="38575-113">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="38575-114">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="38575-114">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="38575-115">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="38575-115">ADO.NET Overview</span></span>](ado-net-overview.md)
