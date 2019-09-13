---
title: Podpora klienta SqlClient pro LocalDB
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: d02524cd5901adeca7bc36d6fd13c7abdc46c69b
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894400"
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="dd42c-102">Podpora klienta SqlClient pro LocalDB</span><span class="sxs-lookup"><span data-stu-id="dd42c-102">SqlClient Support for LocalDB</span></span>
<span data-ttu-id="dd42c-103">Počínaje SQL Server název kódu Denali bude k dispozici zjednodušená verze SQL Server s názvem LocalDB.</span><span class="sxs-lookup"><span data-stu-id="dd42c-103">Beginning in SQL Server code name Denali, a lightweight version of SQL Server, called LocalDB, will be available.</span></span> <span data-ttu-id="dd42c-104">Toto téma popisuje, jak se připojit k databázi LocalDB.</span><span class="sxs-lookup"><span data-stu-id="dd42c-104">This topic discusses how to connect to a LocalDB database.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd42c-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dd42c-105">Remarks</span></span>  
 <span data-ttu-id="dd42c-106">Další informace o LocalDB, včetně toho, jak nainstalovat LocalDB a nakonfigurovat instanci LocalDB, najdete v tématu SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="dd42c-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="dd42c-107">Sumarizace toho, co můžete s LocalDB provádět:</span><span class="sxs-lookup"><span data-stu-id="dd42c-107">To summarize what you can do with LocalDB:</span></span>  
  
- <span data-ttu-id="dd42c-108">Vytvořte a spusťte instance LocalDB pomocí sqllocaldb. exe nebo souboru App. config.</span><span class="sxs-lookup"><span data-stu-id="dd42c-108">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
- <span data-ttu-id="dd42c-109">K přidávání a úpravám databází v instanci LocalDB použijte Sqlcmd. exe.</span><span class="sxs-lookup"><span data-stu-id="dd42c-109">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="dd42c-110">Například, `sqlcmd -S (localdb)\myinst`.</span><span class="sxs-lookup"><span data-stu-id="dd42c-110">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
- <span data-ttu-id="dd42c-111">K přidání databáze do instance LocalDB použijte klíčové slovo připojovacíhořetězce.`AttachDBFilename`</span><span class="sxs-lookup"><span data-stu-id="dd42c-111">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="dd42c-112">Pokud při `AttachDBFilename`použití nezadáte název databáze `Database` pomocí klíčového slova připojovacího řetězce, databáze bude při zavření aplikace odebrána z instance LocalDB.</span><span class="sxs-lookup"><span data-stu-id="dd42c-112">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
- <span data-ttu-id="dd42c-113">V připojovacím řetězci zadejte instanci LocalDB.</span><span class="sxs-lookup"><span data-stu-id="dd42c-113">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="dd42c-114">Například název instance je `myInstance`, připojovací řetězec by měl obsahovat:</span><span class="sxs-lookup"><span data-stu-id="dd42c-114">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    `server=(localdb)\\myInstance`  
  
 <span data-ttu-id="dd42c-115">`User Instance=True`není povolený při připojování k databázi LocalDB.</span><span class="sxs-lookup"><span data-stu-id="dd42c-115">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
 <span data-ttu-id="dd42c-116">LocalDB můžete stáhnout z [balíčku funkcí Microsoft SQL Server 2012](https://www.microsoft.com/download/en/details.aspx?id=29065).</span><span class="sxs-lookup"><span data-stu-id="dd42c-116">You can download LocalDB from [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065).</span></span> <span data-ttu-id="dd42c-117">Pokud budete pomocí nástroje Sqlcmd. exe upravovat data v instanci LocalDB, budete potřebovat Sqlcmd z SQL Server 2012, který můžete také získat ze sady SQL Server 2012 Feature Pack.</span><span class="sxs-lookup"><span data-stu-id="dd42c-117">If you will use sqlcmd.exe to modify data in your LocalDB instance, you will need sqlcmd from SQL Server 2012, which you can also get from the SQL Server 2012 Feature Pack.</span></span>  
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="dd42c-118">Programové vytvoření pojmenované instance</span><span class="sxs-lookup"><span data-stu-id="dd42c-118">Programmatically Create a Named Instance</span></span>  
 <span data-ttu-id="dd42c-119">Aplikace může vytvořit pojmenovanou instanci a zadat databázi následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="dd42c-119">An application can create a named instance and specify a database as follows:</span></span>  
  
- <span data-ttu-id="dd42c-120">Následujícím způsobem zadejte instance LocalDB, které se mají vytvořit v souboru App. config.</span><span class="sxs-lookup"><span data-stu-id="dd42c-120">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="dd42c-121">Číslo verze instance by mělo být stejné jako číslo verze vaší instalace LocalDB.</span><span class="sxs-lookup"><span data-stu-id="dd42c-121">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <configSections>  
        <section  
        name="system.data.localdb"  
        type="System.Data.LocalDBConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>  
      </configSections>  
      <system.data.localdb>  
        <localdbinstances>  
          <add name="myInstance" version="11.0" />  
        </localdbinstances>  
      </system.data.localdb>  
    </configuration>  
    ```  
  
- <span data-ttu-id="dd42c-122">Zadejte název instance pomocí `server` klíčového slova připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="dd42c-122">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="dd42c-123">Název instance zadaný v `server` klíčovém slově připojovacího řetězce se musí shodovat s názvem zadaným v souboru App. config.</span><span class="sxs-lookup"><span data-stu-id="dd42c-123">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
- <span data-ttu-id="dd42c-124">Pomocí klíčového slova připojovacího řetězce určete. `AttachDBFilename` Soubor MDF.</span><span class="sxs-lookup"><span data-stu-id="dd42c-124">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd42c-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd42c-125">See also</span></span>

- [<span data-ttu-id="dd42c-126">Funkce SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="dd42c-126">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)
- [<span data-ttu-id="dd42c-127">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="dd42c-127">ADO.NET Overview</span></span>](../ado-net-overview.md)
