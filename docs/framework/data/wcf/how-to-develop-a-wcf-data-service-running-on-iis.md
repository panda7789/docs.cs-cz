---
title: 'Postupy: vývoj WCF Data Service spuštěna ve službě IIS'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f9df38d200be864ab24efdb0d002fe7b75cfc3e4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a><span data-ttu-id="574c8-102">Postupy: vývoj WCF Data Service spuštěna ve službě IIS</span><span class="sxs-lookup"><span data-stu-id="574c8-102">How to: Develop a WCF Data Service Running on IIS</span></span>
<span data-ttu-id="574c8-103">Toto téma ukazuje, jak používat [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] k vytvoření služby data, která je založena na ukázková databáze Northwind, který je hostitelem aplikace technologie ASP.NET, která běží na Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="574c8-103">This topic shows how to use [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] to create a data service that is based on the Northwind sample database that is hosted by an ASP.NET Web application that is running on Internet Information Services (IIS).</span></span> <span data-ttu-id="574c8-104">Příklad vytvoření stejnou službu data Northwind jako aplikace technologie ASP.NET, která běží na vývojový Server ASP.NET naleznete v části [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="574c8-104">For an example of how to create the same Northwind data service as an ASP.NET Web application that runs on the ASP.NET Development Server, see the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="574c8-105">Pokud chcete vytvořit službu Northwind data, musíte instalaci ukázková databáze Northwind v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="574c8-105">To create the Northwind data service, you must have installed the Northwind sample database on the local computer.</span></span> <span data-ttu-id="574c8-106">Stažení této ukázkové databáze, najdete v článku stránce pro stažení [ukázkové databáze systému SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="574c8-106">To download this sample database, see the download page, [Sample Databases for SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span></span>  
  
 <span data-ttu-id="574c8-107">Toto téma ukazuje, jak vytvořit službu dat pomocí zprostředkovatele Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="574c8-107">This topic shows how to create a data service by using the Entity Framework provider.</span></span> <span data-ttu-id="574c8-108">Jiných poskytovatelů služeb dat jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="574c8-108">Other data services providers are available.</span></span> <span data-ttu-id="574c8-109">Další informace najdete v tématu [zprostředkovatelé dat služby](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="574c8-109">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="574c8-110">Po vytvoření služby, je nutné explicitně zadat přístup k datovým prostředkům služby.</span><span class="sxs-lookup"><span data-stu-id="574c8-110">After you create the service, you must explicitly provide access to data service resources.</span></span> <span data-ttu-id="574c8-111">Další informace najdete v tématu [postup: Povolit přístup ke službě Data](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="574c8-111">For more information, see [How to: Enable Access to the Data Service](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).</span></span>  
  
### <a name="to-create-the-aspnet-web-application-that-runs-on-iis"></a><span data-ttu-id="574c8-112">Chcete-li vytvořit aplikaci ASP.NET, který běží ve službě IIS</span><span class="sxs-lookup"><span data-stu-id="574c8-112">To create the ASP.NET Web application that runs on IIS</span></span>  
  
1.  <span data-ttu-id="574c8-113">V sadě Visual Studio na **soubor** nabídce vyberte možnost **nový**a potom vyberte **projektu**.</span><span class="sxs-lookup"><span data-stu-id="574c8-113">In Visual Studio, on the **File** menu, select **New**, and then select **Project**.</span></span>  
  
2.  <span data-ttu-id="574c8-114">V **nový projekt** dialogovém okně vyberte jako programovací jazyk Visual Basic a Visual C#.</span><span class="sxs-lookup"><span data-stu-id="574c8-114">In the **New Project** dialog box, select either Visual Basic or Visual C# as the programming language.</span></span>  
  
3.  <span data-ttu-id="574c8-115">V **šablony** podokně, vyberte **webové aplikace ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="574c8-115">In the **Templates** pane, select **ASP.NET Web Application**.</span></span> <span data-ttu-id="574c8-116">Poznámka: Pokud používáte Visual Studio Web Developer, musíte vytvořit nový web místo novou webovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="574c8-116">Note: If you use Visual Studio Web Developer, you must create a new Web site instead of a new Web application.</span></span>  
  
4.  <span data-ttu-id="574c8-117">Typ `NorthwindService` jako název projektu.</span><span class="sxs-lookup"><span data-stu-id="574c8-117">Type `NorthwindService` as the name of the project.</span></span>  
  
5.  <span data-ttu-id="574c8-118">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="574c8-118">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="574c8-119">Na **projektu** nabídce vyberte možnost **NorthwindService vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="574c8-119">On the **Project** menu, select **NorthwindService Properties**.</span></span>  
  
7.  <span data-ttu-id="574c8-120">Vyberte **webové** a pak vyberte **použití místního webového serveru IIS**.</span><span class="sxs-lookup"><span data-stu-id="574c8-120">Select the **Web** tab, and then select **Use Local IIS Web Server**.</span></span>  
  
8.  <span data-ttu-id="574c8-121">Klikněte na tlačítko **vytvořit virtuální adresář** a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="574c8-121">Click **Create Virtual Directory** and then click **OK**.</span></span>  
  
9. <span data-ttu-id="574c8-122">Z příkazového řádku s oprávněními správce spusťte jeden z následujících příkazů (v závislosti na operační systém):</span><span class="sxs-lookup"><span data-stu-id="574c8-122">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>  
  
    -   <span data-ttu-id="574c8-123">32bitové systémy:</span><span class="sxs-lookup"><span data-stu-id="574c8-123">32-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
    -   <span data-ttu-id="574c8-124">64bitové systémy:</span><span class="sxs-lookup"><span data-stu-id="574c8-124">64-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
     <span data-ttu-id="574c8-125">Tím je zajištěno, že Windows Communication Foundation (WCF) je zaregistrován v počítači.</span><span class="sxs-lookup"><span data-stu-id="574c8-125">This makes sure that Windows Communication Foundation (WCF) is registered on the computer.</span></span>  
  
10. <span data-ttu-id="574c8-126">Z příkazového řádku s oprávněními správce spusťte jeden z následujících příkazů (v závislosti na operační systém):</span><span class="sxs-lookup"><span data-stu-id="574c8-126">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>  
  
    -   <span data-ttu-id="574c8-127">32bitové systémy:</span><span class="sxs-lookup"><span data-stu-id="574c8-127">32-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
    -   <span data-ttu-id="574c8-128">64bitové systémy:</span><span class="sxs-lookup"><span data-stu-id="574c8-128">64-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
     <span data-ttu-id="574c8-129">Tím je zajištěno, že služba IIS běží správně po instalaci WCF v počítači.</span><span class="sxs-lookup"><span data-stu-id="574c8-129">This makes sure that IIS runs correctly after WCF has been installed on the computer.</span></span> <span data-ttu-id="574c8-130">Může mít také restartovat službu IIS.</span><span class="sxs-lookup"><span data-stu-id="574c8-130">You might have to also restart IIS.</span></span>  
  
11. <span data-ttu-id="574c8-131">Když je spuštěná aplikace ASP.NET ve službě IIS7, je třeba provést následující kroky:</span><span class="sxs-lookup"><span data-stu-id="574c8-131">When the ASP.NET application runs on IIS7, you must also perform the following steps:</span></span>  
  
    1.  <span data-ttu-id="574c8-132">Otevřete Správce služby IIS a přejděte do aplikace PhotoService pod **Default Web Site**.</span><span class="sxs-lookup"><span data-stu-id="574c8-132">Open IIS Manager and navigate to the PhotoService application under **Default Web Site**.</span></span>  
  
    2.  <span data-ttu-id="574c8-133">V **zobrazení funkcí**, dvakrát klikněte na **ověřování**.</span><span class="sxs-lookup"><span data-stu-id="574c8-133">In **Features View**, double-click **Authentication**.</span></span>  
  
    3.  <span data-ttu-id="574c8-134">Na **ověřování** vyberte **anonymní ověřování**.</span><span class="sxs-lookup"><span data-stu-id="574c8-134">On the **Authentication** page, select **Anonymous Authentication**.</span></span>  
  
    4.  <span data-ttu-id="574c8-135">V **akce** podokně klikněte na tlačítko **upravit** nastavení zabezpečení hlavní, pod které anonymní uživatelé se budou připojovat k webu.</span><span class="sxs-lookup"><span data-stu-id="574c8-135">In the **Actions** pane, click **Edit** to set the security principal under which anonymous users will connect to the site.</span></span>  
  
    5.  <span data-ttu-id="574c8-136">V **upravit pověření anonymního ověřování** dialogové okno, vyberte **identita fondu aplikací**.</span><span class="sxs-lookup"><span data-stu-id="574c8-136">In the **Edit Anonymous Authentication Credentials** dialog box, select **Application pool identity**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="574c8-137">Pokud používáte účet Network Service, udělíte anonymním uživatelům všechna přístupová práva interní síti přidružená tohoto účtu.</span><span class="sxs-lookup"><span data-stu-id="574c8-137">When you use the Network Service account, you grant anonymous users all the internal network access associated with that account.</span></span>  
  
12. <span data-ttu-id="574c8-138">Pomocí SQL Server Management Studio, pomocí nástroje sqlcmd.exe nebo editoru jazyka Transact-SQL v sadě Visual Studio, spusťte následující příkaz Transact-SQL pro instanci systému SQL Server, který má databáze Northwind připojené:</span><span class="sxs-lookup"><span data-stu-id="574c8-138">By using SQL Server Management Studio, the sqlcmd.exe utility, or the Transact-SQL Editor in Visual Studio, execute the following Transact-SQL command against the instance of SQL Server that has the Northwind database attached:</span></span>  
  
    ```sql  
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;  
    GO   
    ```  
  
     <span data-ttu-id="574c8-139">Tím se vytvoří přihlášení v instanci serveru SQL pro účet Windows použitý ke spuštění služby IIS.</span><span class="sxs-lookup"><span data-stu-id="574c8-139">This creates a login in the SQL Server instance for the Windows account used to run IIS.</span></span> <span data-ttu-id="574c8-140">To umožňuje službě IIS pro připojení k instanci systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="574c8-140">This enables IIS to connect to the SQL Server instance.</span></span>  
  
13. <span data-ttu-id="574c8-141">S připojit databázi Northwind spusťte následující příkazy jazyka Transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="574c8-141">With the Northwind database attached, execute the following Transact-SQL commands:</span></span>  
  
    ```sql  
    USE Northwind  
    GO  
    CREATE USER [NT AUTHORITY\NETWORK SERVICE]   
    FOR LOGIN [NT AUTHORITY\NETWORK SERVICE] WITH DEFAULT_SCHEMA=[dbo];  
    GO  
    ALTER LOGIN [NT AUTHORITY\NETWORK SERVICE]   
    WITH DEFAULT_DATABASE=[Northwind];   
    GO  
    EXEC sp_addrolemember 'db_datareader', 'NT AUTHORITY\NETWORK SERVICE'  
    GO  
    EXEC sp_addrolemember 'db_datawriter', 'NT AUTHORITY\NETWORK SERVICE'  
    GO   
    ```  
  
     <span data-ttu-id="574c8-142">Tím udělíte oprávnění k nové přihlašovací údaje, které umožňuje službě IIS ke čtení dat z a zapisovat data do databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="574c8-142">This grants rights to the new login, which enables IIS to read data from and write data to the Northwind database.</span></span>  
  
### <a name="to-define-the-data-model"></a><span data-ttu-id="574c8-143">Chcete-li definovat datový model</span><span class="sxs-lookup"><span data-stu-id="574c8-143">To define the data model</span></span>  
  
1.  <span data-ttu-id="574c8-144">V **Průzkumníku řešení**, klikněte pravým tlačítkem na název projektu ASP.NET a pak klikněte na tlačítko **přidat novou položku.**</span><span class="sxs-lookup"><span data-stu-id="574c8-144">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add New Item.**</span></span>  
  
2.  <span data-ttu-id="574c8-145">V **přidat novou položku** dialogové okno, vyberte **ADO.NET Entity Data Model**.</span><span class="sxs-lookup"><span data-stu-id="574c8-145">In the **Add New Item** dialog box, select **ADO.NET Entity Data Model**.</span></span>  
  
3.  <span data-ttu-id="574c8-146">Zadejte název datového modelu, `Northwind.edmx`.</span><span class="sxs-lookup"><span data-stu-id="574c8-146">For the name of the data model, type `Northwind.edmx`.</span></span>  
  
4.  <span data-ttu-id="574c8-147">V průvodci Entity Data Model vyberte **generování z databáze**a potom klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="574c8-147">In the Entity Data Model Wizard, select **Generate from Database**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="574c8-148">Datový model připojení k databázi pomocí jedné z následujících kroků a potom klikněte na **Další**:</span><span class="sxs-lookup"><span data-stu-id="574c8-148">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>  
  
    -   <span data-ttu-id="574c8-149">Pokud jste připojení k databázi již nakonfigurována, klikněte na tlačítko **nové připojení** a vytvořit nové připojení.</span><span class="sxs-lookup"><span data-stu-id="574c8-149">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="574c8-150">Další informace najdete v tématu [postupy: vytvoření připojení databáze serveru SQL Server](http://go.microsoft.com/fwlink/?LinkId=123631).</span><span class="sxs-lookup"><span data-stu-id="574c8-150">For more information, see [How to: Create Connections to SQL Server Databases](http://go.microsoft.com/fwlink/?LinkId=123631).</span></span> <span data-ttu-id="574c8-151">Tato instance systému SQL Server musí mít ukázková databáze Northwind připojen.</span><span class="sxs-lookup"><span data-stu-id="574c8-151">This SQL Server instance must have the Northwind sample database attached.</span></span>  
  
         <span data-ttu-id="574c8-152">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="574c8-152">\- or -</span></span>  
  
    -   <span data-ttu-id="574c8-153">Pokud máte připojení k databázi již byla konfigurována pro připojení k databázi Northwind, vyberte ze seznamu připojení toto připojení.</span><span class="sxs-lookup"><span data-stu-id="574c8-153">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>  
  
6.  <span data-ttu-id="574c8-154">Na poslední stránce průvodce zaškrtněte políčka pro všechny tabulky v databázi a zrušte zaškrtnutí políčka pro zobrazení a uložených procedur.</span><span class="sxs-lookup"><span data-stu-id="574c8-154">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>  
  
7.  <span data-ttu-id="574c8-155">Klikněte na tlačítko **Dokončit** zavřete průvodce.</span><span class="sxs-lookup"><span data-stu-id="574c8-155">Click **Finish** to close the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="574c8-156">Tento model generované datové zpřístupní vlastnosti cizího klíče v typech entit.</span><span class="sxs-lookup"><span data-stu-id="574c8-156">This generated data model exposes foreign key properties on entity types.</span></span> <span data-ttu-id="574c8-157">Datové modely, které jsou vytvořené pomocí sady Visual Studio 2008 nezahrnují tyto vlastnosti cizího klíče.</span><span class="sxs-lookup"><span data-stu-id="574c8-157">Data models created using Visual Studio 2008 do not include these foreign key properties.</span></span> <span data-ttu-id="574c8-158">Z toho důvodu je třeba aktualizovat třídy klienta služby data všech klientských aplikací, které byly vytvořeny pro přístup ke službě Northwind data, která byla vytvořena pomocí sady Visual Studio 2008 před pokusem o přístup k této verzi datové služby Northwind.</span><span class="sxs-lookup"><span data-stu-id="574c8-158">Because of this, you must update the client data service classes of any client applications that were created to access the Northwind data service that was created using Visual Studio 2008 before attempting to access this version of the Northwind data service.</span></span>  
  
### <a name="to-create-the-data-service"></a><span data-ttu-id="574c8-159">Vytvoření datové služby</span><span class="sxs-lookup"><span data-stu-id="574c8-159">To create the data service</span></span>  
  
1.  <span data-ttu-id="574c8-160">V **Průzkumníku řešení**, klikněte pravým tlačítkem na název projektu ASP.NET a pak klikněte na tlačítko **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="574c8-160">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="574c8-161">V **přidat novou položku** dialogové okno, vyberte **služby ADO.NET Data**.</span><span class="sxs-lookup"><span data-stu-id="574c8-161">In the **Add New Item** dialog box, select **ADO.NET Data Service**.</span></span>  
  
3.  <span data-ttu-id="574c8-162">Název služby, zadejte `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="574c8-162">For the name of the service, type `Northwind`.</span></span>  
  
     <span data-ttu-id="574c8-163">Visual Studio vytvoří soubory značek a kódu XML pro novou službu.</span><span class="sxs-lookup"><span data-stu-id="574c8-163">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="574c8-164">Ve výchozím nastavení otevře se okno editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="574c8-164">By default, the code-editor window opens.</span></span> <span data-ttu-id="574c8-165">V **Průzkumníku**, služba bude mít název, Northwind, s příponou. svc.cs nebo. svc.vb.</span><span class="sxs-lookup"><span data-stu-id="574c8-165">In **Solution Explorer**, the service will have the name, Northwind, with the extension .svc.cs or .svc.vb.</span></span>  
  
4.  <span data-ttu-id="574c8-166">V kódu pro službu data, nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy, která definuje službu data s typem, který je kontejneru entit datového modelu, který v tomto případě je `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="574c8-166">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="574c8-167">Definice třídy by měl vypadat to následující:</span><span class="sxs-lookup"><span data-stu-id="574c8-167">The class definition should look this the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
## <a name="see-also"></a><span data-ttu-id="574c8-168">Viz také</span><span class="sxs-lookup"><span data-stu-id="574c8-168">See Also</span></span>  
 [<span data-ttu-id="574c8-169">Vystavení dat jako služby</span><span class="sxs-lookup"><span data-stu-id="574c8-169">Exposing Your Data as a Service</span></span>](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
