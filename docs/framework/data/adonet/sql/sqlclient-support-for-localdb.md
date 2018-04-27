---
title: Podpora SqlClient LocalDB
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: e2564e49a90a1c8fd9fe2cc000ebf648cf90b4e7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="5de8b-102">Podpora SqlClient LocalDB</span><span class="sxs-lookup"><span data-stu-id="5de8b-102">SqlClient Support for LocalDB</span></span>
<span data-ttu-id="5de8b-103">Od systému SQL Server s kódovým názvem Denali, bude k dispozici Odlehčená verze systému SQL Server, názvem databáze LocalDB.</span><span class="sxs-lookup"><span data-stu-id="5de8b-103">Beginning in SQL Server code name Denali, a lightweight version of SQL Server, called LocalDB, will be available.</span></span> <span data-ttu-id="5de8b-104">Toto téma popisuje, jak se připojit k databázi LocalDB.</span><span class="sxs-lookup"><span data-stu-id="5de8b-104">This topic discusses how to connect to a LocalDB database.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5de8b-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5de8b-105">Remarks</span></span>  
 <span data-ttu-id="5de8b-106">Další informace o LocalDB, včetně toho, jak k LocalDB instalaci a konfiguraci vaší instanci LocalDB, najdete v části SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="5de8b-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="5de8b-107">Chcete-li shrnout, co můžete dělat s LocalDB:</span><span class="sxs-lookup"><span data-stu-id="5de8b-107">To summarize what you can do with LocalDB:</span></span>  
  
-   <span data-ttu-id="5de8b-108">Vytvořte a spusťte LocalDB instancí s sqllocaldb.exe nebo souboru app.config.</span><span class="sxs-lookup"><span data-stu-id="5de8b-108">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
-   <span data-ttu-id="5de8b-109">Pomocí sqlcmd.exe přidání a změna databáze v instanci LocalDB.</span><span class="sxs-lookup"><span data-stu-id="5de8b-109">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="5de8b-110">Například `sqlcmd -S (localdb)\myinst`.</span><span class="sxs-lookup"><span data-stu-id="5de8b-110">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
-   <span data-ttu-id="5de8b-111">Použití `AttachDBFilename` klíčové slovo připojovacího řetězce pro přidání do databáze k vaší instanci LocalDB.</span><span class="sxs-lookup"><span data-stu-id="5de8b-111">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="5de8b-112">Při použití `AttachDBFilename`, pokud není zadán název databáze s `Database` klíčové slovo připojovacího řetězce databáze bude odebrána z instanci LocalDB, až se aplikace zavře.</span><span class="sxs-lookup"><span data-stu-id="5de8b-112">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
-   <span data-ttu-id="5de8b-113">V připojovacím řetězci zadejte instanci LocalDB.</span><span class="sxs-lookup"><span data-stu-id="5de8b-113">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="5de8b-114">Například je název vaší instance `myInstance`, by mělo zahrnovat připojovací řetězec:</span><span class="sxs-lookup"><span data-stu-id="5de8b-114">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 <span data-ttu-id="5de8b-115">`User Instance=True` Při připojení k databázi LocalDB není povolen.</span><span class="sxs-lookup"><span data-stu-id="5de8b-115">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
 <span data-ttu-id="5de8b-116">Můžete si stáhnout LocalDB z [Microsoft SQL Server 2012 Feature Pack](http://www.microsoft.com/download/en/details.aspx?id=29065).</span><span class="sxs-lookup"><span data-stu-id="5de8b-116">You can download LocalDB from [Microsoft SQL Server 2012 Feature Pack](http://www.microsoft.com/download/en/details.aspx?id=29065).</span></span> <span data-ttu-id="5de8b-117">Pokud budete používat sqlcmd.exe ke změně dat ve vaší instanci LocalDB, budete potřebovat sqlcmd z SQL serveru 2012, který můžete získat z SQL Server 2012 Feature Pack.</span><span class="sxs-lookup"><span data-stu-id="5de8b-117">If you will use sqlcmd.exe to modify data in your LocalDB instance, you will need sqlcmd from SQL Server 2012, which you can also get from the SQL Server 2012 Feature Pack.</span></span>  
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="5de8b-118">Vytváření pojmenovanou instanci prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="5de8b-118">Programmatically Create a Named Instance</span></span>  
 <span data-ttu-id="5de8b-119">Aplikace můžete vytvořit pojmenovanou instanci a zadejte databázi, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5de8b-119">An application can create a named instance and specify a database as follows:</span></span>  
  
-   <span data-ttu-id="5de8b-120">Zadejte instance LocalDB vytvořit v souboru app.config takto.</span><span class="sxs-lookup"><span data-stu-id="5de8b-120">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="5de8b-121">Číslo verze instance by měla být stejná jako číslo verze instalace LocalDB.</span><span class="sxs-lookup"><span data-stu-id="5de8b-121">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
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
  
-   <span data-ttu-id="5de8b-122">Zadejte název instance pomocí `server` klíčové slovo připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="5de8b-122">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="5de8b-123">Název instance zadané v `server` klíčové slovo připojovacího řetězce musí odpovídat názvu zadaná v souboru app.config.</span><span class="sxs-lookup"><span data-stu-id="5de8b-123">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
-   <span data-ttu-id="5de8b-124">Použití `AttachDBFilename` klíčové slovo připojovacího řetězce k určení. Soubor MDF.</span><span class="sxs-lookup"><span data-stu-id="5de8b-124">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5de8b-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="5de8b-125">See Also</span></span>  
 [<span data-ttu-id="5de8b-126">Funkce SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5de8b-126">SQL Server Features and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 [<span data-ttu-id="5de8b-127">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="5de8b-127">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
