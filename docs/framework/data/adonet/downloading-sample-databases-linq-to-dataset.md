---
title: "Stažení ukázkové databáze (LINQ na DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6450e683f51abe0bdd4eb7f45089f04d11660d5d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="downloading-sample-databases-linq-to-dataset"></a><span data-ttu-id="29c7a-102">Stažení ukázkové databáze (LINQ na DataSet)</span><span class="sxs-lookup"><span data-stu-id="29c7a-102">Downloading Sample Databases (LINQ to DataSet)</span></span>
<span data-ttu-id="29c7a-103">Ukázky a návody v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dokumentace použít ukázkovou databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="29c7a-103">The samples and walkthroughs in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] documentation use the AdventureWorks sample database.</span></span> <span data-ttu-id="29c7a-104">Tento produkt zdarma si můžete stáhnout z webu Microsoft download.</span><span class="sxs-lookup"><span data-stu-id="29c7a-104">You can download this product free of charge from the Microsoft download site.</span></span> <span data-ttu-id="29c7a-105">Ukázky a návody v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dokumentace použít jako úložiště dat serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="29c7a-105">The samples and walkthroughs in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] documentation use SQL Server as the data store.</span></span> <span data-ttu-id="29c7a-106">SQL Server Express Edition, která je k dispozici bezplatně, můžete také použít jako úložiště dat místo systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="29c7a-106">SQL Server Express Edition, which is available without charge, can also be used as the data store instead of SQL Server.</span></span>  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a><span data-ttu-id="29c7a-107">Stažení a instalaci databázi AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="29c7a-107">Downloading and Installing the AdventureWorks Database</span></span>  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="29c7a-108">Chcete-li stáhnout a nainstalovat ukázkovou databázi AdventureWorks pro SQL Server</span><span class="sxs-lookup"><span data-stu-id="29c7a-108">To download and install the AdventureWorks sample database for SQL Server</span></span>  
  
1.  <span data-ttu-id="29c7a-109">Otevřete Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="29c7a-109">Open Internet Explorer.</span></span>  
  
2.  <span data-ttu-id="29c7a-110">Přejděte na [SQL Server 2005 ukázky a ukázkové databáze](http://go.microsoft.com/fwlink/?linkid=31046) webu.</span><span class="sxs-lookup"><span data-stu-id="29c7a-110">Go to the [SQL Server 2005 Samples and Sample Databases](http://go.microsoft.com/fwlink/?linkid=31046) Web site.</span></span>  
  
3.  <span data-ttu-id="29c7a-111">Postupujte podle pokynů pro stahování ukázkovou databázi AdventureWorks pro váš typ procesoru (například AdventureWorksDB.msi) a uložte. Soubor MSI do místního počítače.</span><span class="sxs-lookup"><span data-stu-id="29c7a-111">Follow the instructions for downloading the AdventureWorks sample database for your processor type (such as AdventureWorksDB.msi), and save the .MSI file to your local computer.</span></span>  
  
4.  <span data-ttu-id="29c7a-112">Pokud máte předchozí verzi AdventureWorks nainstalovat z stahování nebo během instalace systému SQL Server, je nutné ji odebrat před spuštěním AdventureWorks.msi.</span><span class="sxs-lookup"><span data-stu-id="29c7a-112">If you have a previous version of AdventureWorks installed from the download or during the SQL Server setup, you must remove it before running AdventureWorks.msi.</span></span>  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a><span data-ttu-id="29c7a-113">Chcete-li odebrat předchozí stahování ukázkovou databázi AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="29c7a-113">To remove a previous download of an AdventureWorks sample database</span></span>  
  
1.  <span data-ttu-id="29c7a-114">Vyřaďte databázi AdventureWorks nebo AdventureWorksDW.</span><span class="sxs-lookup"><span data-stu-id="29c7a-114">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2.  <span data-ttu-id="29c7a-115">Z **přidat nebo odebrat programy**, vyberte **AdventureWorksDB** nebo **AdventureWorksBI** a klikněte na tlačítko **odebrat**.</span><span class="sxs-lookup"><span data-stu-id="29c7a-115">From **Add or Remove Programs**, select **AdventureWorksDB** or **AdventureWorksBI** and click **Remove**.</span></span>  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a><span data-ttu-id="29c7a-116">Chcete-li odebrat dříve pomocí instalačního programu nainstalovat ukázkovou databázi AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="29c7a-116">To remove an AdventureWorks sample database previously installed using Setup</span></span>  
  
1.  <span data-ttu-id="29c7a-117">Vyřaďte databázi AdventureWorks nebo AdventureWorksDW.</span><span class="sxs-lookup"><span data-stu-id="29c7a-117">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2.  <span data-ttu-id="29c7a-118">Z **přidat nebo odebrat programy**, vyberte **Microsoft SQL Server 2005** a klikněte na tlačítko **změnu**.</span><span class="sxs-lookup"><span data-stu-id="29c7a-118">From **Add or Remove Programs**, select **Microsoft SQL Server 2005** and click **Change**.</span></span>  
  
3.  <span data-ttu-id="29c7a-119">Z **výběr součásti**, vyberte **součásti pracovní stanice** a pak klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="29c7a-119">From **Component Selection**, select **Workstation Components** and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="29c7a-120">Z **Vítá vás Průvodce instalací serveru SQL**, klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="29c7a-120">From **Welcome to the SQL Server Installation Wizard**, click **Next**.</span></span>  
  
5.  <span data-ttu-id="29c7a-121">Z **kontroly konfigurace systému**, klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="29c7a-121">From **System Configuration Check**, click **Next**.</span></span>  
  
6.  <span data-ttu-id="29c7a-122">Z **změnit nebo odebrat instanci**, klikněte na tlačítko **změnit nainstalované komponenty**.</span><span class="sxs-lookup"><span data-stu-id="29c7a-122">From **Change or Remove Instance**, click **Change Installed Components**.</span></span>  
  
7.  <span data-ttu-id="29c7a-123">Z **výběr funkce**, rozbalte **dokumentace, ukázky a ukázkové databáze** uzlu.</span><span class="sxs-lookup"><span data-stu-id="29c7a-123">From **Feature Selection**, expand the **Documentation, Samples, and Sample Databases** node.</span></span>  
  
8.  <span data-ttu-id="29c7a-124">Vyberte **ukázkový kód a aplikace**.</span><span class="sxs-lookup"><span data-stu-id="29c7a-124">Select **Sample Code and Applications**.</span></span> <span data-ttu-id="29c7a-125">Rozbalte položku **ukázkové databáze**, vyberte v ukázkové databázi odebrat, a vyberte **celá funkce nedostupná**.</span><span class="sxs-lookup"><span data-stu-id="29c7a-125">Expand **Sample Databases**, select the sample database to be removed, and select **Entire feature will be unavailable**.</span></span> <span data-ttu-id="29c7a-126">Klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="29c7a-126">Click **Next**.</span></span>  
  
9. <span data-ttu-id="29c7a-127">Klikněte na tlačítko **nainstalovat** a dokončete Průvodce instalací.</span><span class="sxs-lookup"><span data-stu-id="29c7a-127">Click **Install** and finish the installation wizard.</span></span>  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a><span data-ttu-id="29c7a-128">Připojit soubory AdventureWorks ukázkové databáze na instanci systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="29c7a-128">To attach the AdventureWorks sample database files to an instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="29c7a-129">Po souboru ukázkové databáze instalačního souboru stáhl, dvakrát klikněte **AdventureWorksDB.msi** souboru (nebo soubor, který jste stáhli) pro instalaci databáze.</span><span class="sxs-lookup"><span data-stu-id="29c7a-129">After the file sample database installer file has downloaded, double-click the **AdventureWorksDB.msi** file (or the file you downloaded) to install the database.</span></span> <span data-ttu-id="29c7a-130">Ve výchozím nastavení je databáze nainstalována na c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.</span><span class="sxs-lookup"><span data-stu-id="29c7a-130">By default, the database is installed at c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.</span></span>  
  
2.  <span data-ttu-id="29c7a-131">Připojte soubory databáze AdventureWorks do instance systému SQL Server, a to spuštěním následujícího skriptu SQLCMD nebo SQL Server Management Studio:</span><span class="sxs-lookup"><span data-stu-id="29c7a-131">Attach the AdventureWorks database files to an instance of SQL Server by executing the following script SQLCMD or SQL Server Management Studio:</span></span>  
  
    ```  
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     <span data-ttu-id="29c7a-132">Pokud jste nainstalovali tyto soubory na jinou jednotku nebo adresář, musíte cesty změnit správně před spuštěním `sp_attach_db` uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="29c7a-132">If you have installed these files to a different drive or directory, you must revise the paths appropriately before you execute the `sp_attach_db` stored procedure.</span></span>  
  
## <a name="downloading-sql-server-express-edition"></a><span data-ttu-id="29c7a-133">Stahování systému SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="29c7a-133">Downloading SQL Server Express Edition</span></span>  
 <span data-ttu-id="29c7a-134">Ukázky a návody v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] části používat SQL Server 2005 jako úložiště dat ale můžete upravit tak, aby místo toho použít SQL Server Express Edition.</span><span class="sxs-lookup"><span data-stu-id="29c7a-134">The samples and walkthroughs in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] section use SQL Server 2005 as the data store but can be modified to use SQL Server Express Edition, instead.</span></span> <span data-ttu-id="29c7a-135">SQL Server Express Edition je k dispozici bezplatně a je možné znovu distribuovat ji s aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="29c7a-135">SQL Server Express Edition is available without charge, and you can redistribute it with applications.</span></span> <span data-ttu-id="29c7a-136">Pokud používáte [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], SQL Server Express Edition je součástí verze Pro a vyšší.</span><span class="sxs-lookup"><span data-stu-id="29c7a-136">If you are using [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], SQL Server Express Edition is included in the Pro and higher editions.</span></span>  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a><span data-ttu-id="29c7a-137">Stáhněte a nainstalujte SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="29c7a-137">To download and install SQL Server Express Edition</span></span>  
  
1.  <span data-ttu-id="29c7a-138">Spusťte Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="29c7a-138">Start Internet Explorer.</span></span>  
  
2.  <span data-ttu-id="29c7a-139">Přejděte na [Microsoft SQL Server 2005 Express Edition](http://go.microsoft.com/fwlink/?LinkID=31070) stránce pro stažení.</span><span class="sxs-lookup"><span data-stu-id="29c7a-139">Go to the  [Microsoft SQL Server 2005 Express Edition](http://go.microsoft.com/fwlink/?LinkID=31070) download page.</span></span>  
  
3.  <span data-ttu-id="29c7a-140">Postupujte podle pokynů k instalaci na webu.</span><span class="sxs-lookup"><span data-stu-id="29c7a-140">Follow the installation instructions on the Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29c7a-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="29c7a-141">See Also</span></span>  
 [<span data-ttu-id="29c7a-142">Začínáme</span><span class="sxs-lookup"><span data-stu-id="29c7a-142">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
