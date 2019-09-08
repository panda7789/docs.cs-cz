---
title: Stahování ukázkových databází (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: c67ee699cf594f476a728c7345b47b0c32dea7ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795176"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a><span data-ttu-id="7d519-102">Stahování ukázkových databází (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="7d519-102">Downloading Sample Databases (LINQ to DataSet)</span></span>
<span data-ttu-id="7d519-103">Ukázky a návody v dokumentaci LINQ to DataSet používají ukázkovou databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="7d519-103">The samples and walkthroughs in the LINQ to DataSet documentation use the AdventureWorks sample database.</span></span> <span data-ttu-id="7d519-104">Zdarma si můžete stáhnout tento produkt z webu služby Stažení softwaru společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7d519-104">You can download this product free of charge from the Microsoft download site.</span></span> <span data-ttu-id="7d519-105">Ukázky a návody v dokumentaci LINQ to DataSet používají SQL Server jako úložiště dat.</span><span class="sxs-lookup"><span data-stu-id="7d519-105">The samples and walkthroughs in the LINQ to DataSet documentation use SQL Server as the data store.</span></span> <span data-ttu-id="7d519-106">SQL Server Express edice, která je k dispozici bezplatně, se dá použít také jako úložiště dat místo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7d519-106">SQL Server Express Edition, which is available without charge, can also be used as the data store instead of SQL Server.</span></span>  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a><span data-ttu-id="7d519-107">Stažení a instalace databáze AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="7d519-107">Downloading and Installing the AdventureWorks Database</span></span>  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="7d519-108">Stažení a instalace ukázkové databáze AdventureWorks pro SQL Server</span><span class="sxs-lookup"><span data-stu-id="7d519-108">To download and install the AdventureWorks sample database for SQL Server</span></span>  
  
1. <span data-ttu-id="7d519-109">Otevřete Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="7d519-109">Open Internet Explorer.</span></span>  
  
2. <span data-ttu-id="7d519-110">Přejít na web [SQL Server 2005 Samples a vzorové databáze](https://go.microsoft.com/fwlink/?linkid=31046) .</span><span class="sxs-lookup"><span data-stu-id="7d519-110">Go to the [SQL Server 2005 Samples and Sample Databases](https://go.microsoft.com/fwlink/?linkid=31046) Web site.</span></span>  
  
3. <span data-ttu-id="7d519-111">Postupujte podle pokynů pro stažení ukázkové databáze AdventureWorks pro typ procesoru (například AdventureWorksDB. msi) a uložte soubor. Soubor MSI do místního počítače.</span><span class="sxs-lookup"><span data-stu-id="7d519-111">Follow the instructions for downloading the AdventureWorks sample database for your processor type (such as AdventureWorksDB.msi), and save the .MSI file to your local computer.</span></span>  
  
4. <span data-ttu-id="7d519-112">Pokud máte nainstalovanou předchozí verzi AdventureWorks ze souboru ke stažení nebo během instalace SQL Server, je nutné ji před spuštěním souboru AdventureWorks. msi odebrat.</span><span class="sxs-lookup"><span data-stu-id="7d519-112">If you have a previous version of AdventureWorks installed from the download or during the SQL Server setup, you must remove it before running AdventureWorks.msi.</span></span>  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a><span data-ttu-id="7d519-113">Odebrání předchozího stažení ukázkové databáze AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="7d519-113">To remove a previous download of an AdventureWorks sample database</span></span>  
  
1. <span data-ttu-id="7d519-114">Přetáhněte databázi AdventureWorks nebo AdventureWorksDW.</span><span class="sxs-lookup"><span data-stu-id="7d519-114">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2. <span data-ttu-id="7d519-115">V nabídce **Přidat nebo odebrat programy**vyberte **AdventureWorksDB** nebo **AdventureWorksBI** a klikněte na **Odebrat**.</span><span class="sxs-lookup"><span data-stu-id="7d519-115">From **Add or Remove Programs**, select **AdventureWorksDB** or **AdventureWorksBI** and click **Remove**.</span></span>  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a><span data-ttu-id="7d519-116">Odebrání ukázkové databáze AdventureWorks, která byla dříve nainstalována pomocí instalačního programu</span><span class="sxs-lookup"><span data-stu-id="7d519-116">To remove an AdventureWorks sample database previously installed using Setup</span></span>  
  
1. <span data-ttu-id="7d519-117">Přetáhněte databázi AdventureWorks nebo AdventureWorksDW.</span><span class="sxs-lookup"><span data-stu-id="7d519-117">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2. <span data-ttu-id="7d519-118">V nabídce **Přidat nebo odebrat programy**vyberte **Microsoft SQL Server 2005** a klikněte na **změnit**.</span><span class="sxs-lookup"><span data-stu-id="7d519-118">From **Add or Remove Programs**, select **Microsoft SQL Server 2005** and click **Change**.</span></span>  
  
3. <span data-ttu-id="7d519-119">V části **Výběr součástí**vyberte **komponenty pracovní stanice** a pak klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="7d519-119">From **Component Selection**, select **Workstation Components** and then click **Next**.</span></span>  
  
4. <span data-ttu-id="7d519-120">V **okně Vítá vás Průvodce instalací SQL Server**klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="7d519-120">From **Welcome to the SQL Server Installation Wizard**, click **Next**.</span></span>  
  
5. <span data-ttu-id="7d519-121">V případě **kontroly konfigurace systému**klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="7d519-121">From **System Configuration Check**, click **Next**.</span></span>  
  
6. <span data-ttu-id="7d519-122">V části **změnit nebo odebrat instanci**klikněte na **změnit nainstalované součásti**.</span><span class="sxs-lookup"><span data-stu-id="7d519-122">From **Change or Remove Instance**, click **Change Installed Components**.</span></span>  
  
7. <span data-ttu-id="7d519-123">V části **Výběr funkcí**rozbalte uzel **dokumentace, ukázky a ukázkové databáze** .</span><span class="sxs-lookup"><span data-stu-id="7d519-123">From **Feature Selection**, expand the **Documentation, Samples, and Sample Databases** node.</span></span>  
  
8. <span data-ttu-id="7d519-124">Vyberte **vzorový kód a aplikace**.</span><span class="sxs-lookup"><span data-stu-id="7d519-124">Select **Sample Code and Applications**.</span></span> <span data-ttu-id="7d519-125">Rozbalte položku **ukázkové**databáze, vyberte ukázkovou databázi, kterou chcete odebrat, a vyberte možnost **Celá součást nebude k dispozici**.</span><span class="sxs-lookup"><span data-stu-id="7d519-125">Expand **Sample Databases**, select the sample database to be removed, and select **Entire feature will be unavailable**.</span></span> <span data-ttu-id="7d519-126">Klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="7d519-126">Click **Next**.</span></span>  
  
9. <span data-ttu-id="7d519-127">Klikněte na **instalovat** a dokončete Průvodce instalací.</span><span class="sxs-lookup"><span data-stu-id="7d519-127">Click **Install** and finish the installation wizard.</span></span>  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a><span data-ttu-id="7d519-128">Připojení ukázkových databázových souborů AdventureWorks k instanci SQL Server</span><span class="sxs-lookup"><span data-stu-id="7d519-128">To attach the AdventureWorks sample database files to an instance of SQL Server</span></span>  
  
1. <span data-ttu-id="7d519-129">Po stažení souboru instalačního programu ukázkové databáze dvakrát klikněte na soubor **AdventureWorksDB. msi** (nebo na soubor, který jste stáhli) pro instalaci databáze.</span><span class="sxs-lookup"><span data-stu-id="7d519-129">After the file sample database installer file has downloaded, double-click the **AdventureWorksDB.msi** file (or the file you downloaded) to install the database.</span></span> <span data-ttu-id="7d519-130">Ve výchozím nastavení je databáze nainstalovaná ve složce c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.</span><span class="sxs-lookup"><span data-stu-id="7d519-130">By default, the database is installed at c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.</span></span>  
  
2. <span data-ttu-id="7d519-131">Připojte soubory databáze AdventureWorks k instanci SQL Server spuštěním následujícího skriptu Script SQLCMD nebo SQL Server Management Studio:</span><span class="sxs-lookup"><span data-stu-id="7d519-131">Attach the AdventureWorks database files to an instance of SQL Server by executing the following script SQLCMD or SQL Server Management Studio:</span></span>  
  
    ```sql
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     <span data-ttu-id="7d519-132">Pokud jste tyto soubory nainstalovali na jinou jednotku nebo adresář, musíte je před `sp_attach_db` spuštěním uložené procedury upravit.</span><span class="sxs-lookup"><span data-stu-id="7d519-132">If you have installed these files to a different drive or directory, you must revise the paths appropriately before you execute the `sp_attach_db` stored procedure.</span></span>  
  
## <a name="downloading-sql-server-express-edition"></a><span data-ttu-id="7d519-133">Stahuje se edice SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="7d519-133">Downloading SQL Server Express Edition</span></span>  
 <span data-ttu-id="7d519-134">Ukázky a návody v části LINQ to DataSet jako úložiště dat používají SQL Server 2005, ale dají se místo toho upravit tak, aby používala SQL Server Express Edition.</span><span class="sxs-lookup"><span data-stu-id="7d519-134">The samples and walkthroughs in the LINQ to DataSet section use SQL Server 2005 as the data store but can be modified to use SQL Server Express Edition, instead.</span></span> <span data-ttu-id="7d519-135">Edice SQL Server Express je k dispozici bez poplatků a je možné ji znovu distribuovat s aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="7d519-135">SQL Server Express Edition is available without charge, and you can redistribute it with applications.</span></span> <span data-ttu-id="7d519-136">Pokud používáte sadu Visual Studio, je SQL Server Express edice součástí edice sady pro a vyšší.</span><span class="sxs-lookup"><span data-stu-id="7d519-136">If you are using Visual Studio, SQL Server Express Edition is included in the Pro and higher editions.</span></span>  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a><span data-ttu-id="7d519-137">Stažení a instalace edice SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="7d519-137">To download and install SQL Server Express Edition</span></span>  
  
1. <span data-ttu-id="7d519-138">Spusťte aplikaci Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="7d519-138">Start Internet Explorer.</span></span>  
  
2. <span data-ttu-id="7d519-139">Přejít na stránku pro stažení [edice Microsoft SQL Server 2005 Express](https://go.microsoft.com/fwlink/?LinkID=31070) .</span><span class="sxs-lookup"><span data-stu-id="7d519-139">Go to the  [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) download page.</span></span>  
  
3. <span data-ttu-id="7d519-140">Postupujte podle pokynů k instalaci na webu.</span><span class="sxs-lookup"><span data-stu-id="7d519-140">Follow the installation instructions on the Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d519-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d519-141">See also</span></span>

- [<span data-ttu-id="7d519-142">Začínáme</span><span class="sxs-lookup"><span data-stu-id="7d519-142">Getting Started</span></span>](getting-started-linq-to-dataset.md)
