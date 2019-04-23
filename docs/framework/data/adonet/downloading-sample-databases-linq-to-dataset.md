---
title: Stažení ukázkových databází (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: 1ef5a5ceac6a7f819551f6221b63197786ab4f09
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59339707"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a><span data-ttu-id="7cfaa-102">Stažení ukázkových databází (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="7cfaa-102">Downloading Sample Databases (LINQ to DataSet)</span></span>
<span data-ttu-id="7cfaa-103">Ukázky a návody v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dokumentaci použít ukázkovou databází AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-103">The samples and walkthroughs in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] documentation use the AdventureWorks sample database.</span></span> <span data-ttu-id="7cfaa-104">Tento produkt zdarma si můžete stáhnout z webu společnosti Microsoft ke stažení.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-104">You can download this product free of charge from the Microsoft download site.</span></span> <span data-ttu-id="7cfaa-105">Ukázky a návody v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dokumentace ke službě použít jako úložiště dat serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-105">The samples and walkthroughs in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] documentation use SQL Server as the data store.</span></span> <span data-ttu-id="7cfaa-106">SQL Server Express Edition, která je k dispozici bez poplatků, může také sloužit jako úložiště dat místo SQL serveru.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-106">SQL Server Express Edition, which is available without charge, can also be used as the data store instead of SQL Server.</span></span>  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a><span data-ttu-id="7cfaa-107">Stažení a instalace databáze AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="7cfaa-107">Downloading and Installing the AdventureWorks Database</span></span>  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="7cfaa-108">Ke stažení a instalaci ukázkové databáze AdventureWorks pro SQL Server</span><span class="sxs-lookup"><span data-stu-id="7cfaa-108">To download and install the AdventureWorks sample database for SQL Server</span></span>  
  
1. <span data-ttu-id="7cfaa-109">Spusťte aplikaci Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-109">Open Internet Explorer.</span></span>  
  
2. <span data-ttu-id="7cfaa-110">Přejděte [SQL Server 2005 ukázky a ukázkových databází](https://go.microsoft.com/fwlink/?linkid=31046) webu.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-110">Go to the [SQL Server 2005 Samples and Sample Databases](https://go.microsoft.com/fwlink/?linkid=31046) Web site.</span></span>  
  
3. <span data-ttu-id="7cfaa-111">Postupujte podle pokynů ke stahování ukázkovou databází AdventureWorks pro váš typ procesoru (například AdventureWorksDB.msi) a uložte. Soubor MSI do místního počítače.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-111">Follow the instructions for downloading the AdventureWorks sample database for your processor type (such as AdventureWorksDB.msi), and save the .MSI file to your local computer.</span></span>  
  
4. <span data-ttu-id="7cfaa-112">Pokud máte předchozí verzi AdventureWorks nainstalovat z položky ke stažení nebo během instalace systému SQL Server, musíte ho odebrat před spuštěním AdventureWorks.msi.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-112">If you have a previous version of AdventureWorks installed from the download or during the SQL Server setup, you must remove it before running AdventureWorks.msi.</span></span>  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a><span data-ttu-id="7cfaa-113">Chcete-li odebrat předchozí stahování ukázkovou databázi AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="7cfaa-113">To remove a previous download of an AdventureWorks sample database</span></span>  
  
1. <span data-ttu-id="7cfaa-114">Odpojení databáze AdventureWorks nebo AdventureWorksDW.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-114">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2. <span data-ttu-id="7cfaa-115">Z **přidat nebo odebrat programy**vyberte **AdventureWorksDB** nebo **AdventureWorksBI** a klikněte na tlačítko **odebrat**.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-115">From **Add or Remove Programs**, select **AdventureWorksDB** or **AdventureWorksBI** and click **Remove**.</span></span>  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a><span data-ttu-id="7cfaa-116">Chcete-li odebrat ukázkovou databázi AdventureWorks dříve nainstalovali pomocí instalačního programu</span><span class="sxs-lookup"><span data-stu-id="7cfaa-116">To remove an AdventureWorks sample database previously installed using Setup</span></span>  
  
1. <span data-ttu-id="7cfaa-117">Odpojení databáze AdventureWorks nebo AdventureWorksDW.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-117">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2. <span data-ttu-id="7cfaa-118">Z **přidat nebo odebrat programy**vyberte **Microsoft SQL Server 2005** a klikněte na tlačítko **změnu**.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-118">From **Add or Remove Programs**, select **Microsoft SQL Server 2005** and click **Change**.</span></span>  
  
3. <span data-ttu-id="7cfaa-119">Z **výběr součásti**vyberte **komponenty pracovní stanice** a potom klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-119">From **Component Selection**, select **Workstation Components** and then click **Next**.</span></span>  
  
4. <span data-ttu-id="7cfaa-120">Z **Vítá vás Průvodce instalací SQL serveru**, klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-120">From **Welcome to the SQL Server Installation Wizard**, click **Next**.</span></span>  
  
5. <span data-ttu-id="7cfaa-121">Z **kontroly konfigurace systému**, klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-121">From **System Configuration Check**, click **Next**.</span></span>  
  
6. <span data-ttu-id="7cfaa-122">Z **změnit nebo odebrat Instance**, klikněte na tlačítko **změnit nainstalované komponenty**.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-122">From **Change or Remove Instance**, click **Change Installed Components**.</span></span>  
  
7. <span data-ttu-id="7cfaa-123">Z **výběr součástí**, rozbalte **dokumentaci, ukázky a ukázkových databází** uzlu.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-123">From **Feature Selection**, expand the **Documentation, Samples, and Sample Databases** node.</span></span>  
  
8. <span data-ttu-id="7cfaa-124">Vyberte **ukázkový kód a aplikace**.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-124">Select **Sample Code and Applications**.</span></span> <span data-ttu-id="7cfaa-125">Rozbalte **ukázkových databází**, vybrat ukázkovou databázi chcete odebrat, vyberte **celé funkce bude k dispozici**.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-125">Expand **Sample Databases**, select the sample database to be removed, and select **Entire feature will be unavailable**.</span></span> <span data-ttu-id="7cfaa-126">Klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-126">Click **Next**.</span></span>  
  
9. <span data-ttu-id="7cfaa-127">Klikněte na tlačítko **nainstalovat** a dokončení Průvodce instalací.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-127">Click **Install** and finish the installation wizard.</span></span>  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a><span data-ttu-id="7cfaa-128">Připojit soubory ukázkové databáze AdventureWorks do instance systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="7cfaa-128">To attach the AdventureWorks sample database files to an instance of SQL Server</span></span>  
  
1. <span data-ttu-id="7cfaa-129">Po stažení ukázkové databáze instalačního programu soubor dvakrát klikněte **AdventureWorksDB.msi** souboru (nebo jste si stáhli) pro instalaci databáze.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-129">After the file sample database installer file has downloaded, double-click the **AdventureWorksDB.msi** file (or the file you downloaded) to install the database.</span></span> <span data-ttu-id="7cfaa-130">Ve výchozím nastavení je databáze nainstaloval do c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-130">By default, the database is installed at c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.</span></span>  
  
2. <span data-ttu-id="7cfaa-131">Spuštěním následujícího skriptu SQLCMD nebo SQL Server Management Studio připojte soubory databáze AdventureWorks do instance systému SQL Server:</span><span class="sxs-lookup"><span data-stu-id="7cfaa-131">Attach the AdventureWorks database files to an instance of SQL Server by executing the following script SQLCMD or SQL Server Management Studio:</span></span>  
  
    ```sql
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     <span data-ttu-id="7cfaa-132">Pokud jste nainstalovali tyto soubory na jinou jednotku nebo adresář, musí cesty odpovídajícím způsobem upravit, ještě před spuštěním `sp_attach_db` uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-132">If you have installed these files to a different drive or directory, you must revise the paths appropriately before you execute the `sp_attach_db` stored procedure.</span></span>  
  
## <a name="downloading-sql-server-express-edition"></a><span data-ttu-id="7cfaa-133">Stahuje se SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="7cfaa-133">Downloading SQL Server Express Edition</span></span>  
 <span data-ttu-id="7cfaa-134">Ukázky a návody v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] část používat jako úložiště dat serveru SQL Server 2005, ale můžete upravit tak, aby místo toho použít SQL Server Express Edition.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-134">The samples and walkthroughs in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] section use SQL Server 2005 as the data store but can be modified to use SQL Server Express Edition, instead.</span></span> <span data-ttu-id="7cfaa-135">SQL Server Express Edition je k dispozici bez poplatků a je možné znovu distribuovat ji s aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-135">SQL Server Express Edition is available without charge, and you can redistribute it with applications.</span></span> <span data-ttu-id="7cfaa-136">Pokud používáte Visual Studio, SQL Server Express Edition je součástí verze Pro a vyšší.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-136">If you are using Visual Studio, SQL Server Express Edition is included in the Pro and higher editions.</span></span>  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a><span data-ttu-id="7cfaa-137">Stáhněte si a nainstalujte SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="7cfaa-137">To download and install SQL Server Express Edition</span></span>  
  
1. <span data-ttu-id="7cfaa-138">Spusťte aplikaci Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-138">Start Internet Explorer.</span></span>  
  
2. <span data-ttu-id="7cfaa-139">Přejděte [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) stránce pro stažení.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-139">Go to the  [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) download page.</span></span>  
  
3. <span data-ttu-id="7cfaa-140">Postupujte podle pokynů k instalaci na webové stránce.</span><span class="sxs-lookup"><span data-stu-id="7cfaa-140">Follow the installation instructions on the Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cfaa-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7cfaa-141">See also</span></span>

- [<span data-ttu-id="7cfaa-142">Začínáme</span><span class="sxs-lookup"><span data-stu-id="7cfaa-142">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
