---
title: 'Postupy: Vývoj datové služby WCF ve službě IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: 74c31c748dd3483aa87afb2c9a7d926965c9f1ed
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64755606"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a><span data-ttu-id="7d594-102">Postupy: Vývoj datové služby WCF ve službě IIS</span><span class="sxs-lookup"><span data-stu-id="7d594-102">How to: Develop a WCF data service running on IIS</span></span>

<span data-ttu-id="7d594-103">Toto téma ukazuje, jak pomocí služeb WCF Data Services k vytvoření datové služby, který je založen na ukázkové databáze Northwind, která je hostována ve webové aplikaci ASP.NET, na kterém běží v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="7d594-103">This topic shows how to use WCF Data Services to create a data service that is based on the Northwind sample database that is hosted by an ASP.NET Web application that is running on Internet Information Services (IIS).</span></span> <span data-ttu-id="7d594-104">Příklad toho, jak vytvořit stejný datová služba Northwind jako webovou aplikaci ASP.NET, která běží na serveru ASP.NET Development Server, najdete v článku [rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="7d594-104">For an example of how to create the same Northwind data service as an ASP.NET Web application that runs on the ASP.NET Development Server, see the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="7d594-105">Pokud chcete vytvořit datová služba Northwind, jste na místním počítači nainstalovali ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="7d594-105">To create the Northwind data service, you must have installed the Northwind sample database on the local computer.</span></span> <span data-ttu-id="7d594-106">Stáhněte si tuto ukázkovou databázi, naleznete na stránce stahování [ukázkové databáze systému SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="7d594-106">To download this sample database, see the download page, [Sample Databases for SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span></span>

<span data-ttu-id="7d594-107">Toto téma ukazuje, jak vytvořit datové služby pomocí zprostředkovatele Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="7d594-107">This topic shows how to create a data service by using the Entity Framework provider.</span></span> <span data-ttu-id="7d594-108">Ostatní zprostředkovatelé dat služby jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="7d594-108">Other data services providers are available.</span></span> <span data-ttu-id="7d594-109">Další informace najdete v tématu [zprostředkovatelé dat služby](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="7d594-109">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span>

<span data-ttu-id="7d594-110">Po vytvoření služby, je nutné explicitně zadat přístup k prostředkům datové služby.</span><span class="sxs-lookup"><span data-stu-id="7d594-110">After you create the service, you must explicitly provide access to data service resources.</span></span> <span data-ttu-id="7d594-111">Další informace najdete v tématu [jak: Povolení přístupu k datové službě](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="7d594-111">For more information, see [How to: Enable Access to the Data Service](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).</span></span>

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a><span data-ttu-id="7d594-112">Vytvoření webové aplikace ASP.NET, která běží ve službě IIS</span><span class="sxs-lookup"><span data-stu-id="7d594-112">Create the ASP.NET web application that runs on IIS</span></span>

1. <span data-ttu-id="7d594-113">V sadě Visual Studio na **souboru** nabídce vyberte možnost **nový** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="7d594-113">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

2. <span data-ttu-id="7d594-114">V **nový projekt** dialogové okno, vyberte **nainstalováno** > [**Visual C#**  nebo **jazyka Visual Basic**] > **Web**  kategorie.</span><span class="sxs-lookup"><span data-stu-id="7d594-114">In the **New Project** dialog box, select the **Installed** > [**Visual C#** or **Visual Basic**] > **Web** category.</span></span>

3. <span data-ttu-id="7d594-115">Vyberte **webová aplikace ASP.NET** šablony.</span><span class="sxs-lookup"><span data-stu-id="7d594-115">Select the **ASP.NET Web Application** template.</span></span>

4. <span data-ttu-id="7d594-116">Zadejte `NorthwindService` jako název projektu.</span><span class="sxs-lookup"><span data-stu-id="7d594-116">Enter `NorthwindService` as the name of the project.</span></span>

5. <span data-ttu-id="7d594-117">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="7d594-117">Click **OK**.</span></span>

6. <span data-ttu-id="7d594-118">Na **projektu** nabídce vyberte možnost **NorthwindService vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="7d594-118">On the **Project** menu, select **NorthwindService Properties**.</span></span>

7. <span data-ttu-id="7d594-119">Vyberte **webové** kartu a potom vyberte **použití místní webový Server IIS**.</span><span class="sxs-lookup"><span data-stu-id="7d594-119">Select the **Web** tab, and then select **Use Local IIS Web Server**.</span></span>

8. <span data-ttu-id="7d594-120">Klikněte na tlačítko **vytvořit virtuální adresář** a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="7d594-120">Click **Create Virtual Directory** and then click **OK**.</span></span>

9. <span data-ttu-id="7d594-121">Z příkazového řádku s oprávněními správce proveďte jednu z následujících příkazů (v závislosti na operačním systému):</span><span class="sxs-lookup"><span data-stu-id="7d594-121">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="7d594-122">32bitové systémy:</span><span class="sxs-lookup"><span data-stu-id="7d594-122">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    - <span data-ttu-id="7d594-123">64bitové systémy:</span><span class="sxs-lookup"><span data-stu-id="7d594-123">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     <span data-ttu-id="7d594-124">Tím zajistíte, že je v počítači registrována Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7d594-124">This makes sure that Windows Communication Foundation (WCF) is registered on the computer.</span></span>

10. <span data-ttu-id="7d594-125">Z příkazového řádku s oprávněními správce proveďte jednu z následujících příkazů (v závislosti na operačním systému):</span><span class="sxs-lookup"><span data-stu-id="7d594-125">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="7d594-126">32bitové systémy:</span><span class="sxs-lookup"><span data-stu-id="7d594-126">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    - <span data-ttu-id="7d594-127">64bitové systémy:</span><span class="sxs-lookup"><span data-stu-id="7d594-127">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     <span data-ttu-id="7d594-128">Tím je zajištěno, že služba IIS běží správně po instalaci WCF v počítači.</span><span class="sxs-lookup"><span data-stu-id="7d594-128">This makes sure that IIS runs correctly after WCF has been installed on the computer.</span></span> <span data-ttu-id="7d594-129">Budete muset také restartovat službu IIS.</span><span class="sxs-lookup"><span data-stu-id="7d594-129">You might have to also restart IIS.</span></span>

11. <span data-ttu-id="7d594-130">Když je spuštěná aplikace ASP.NET ve službě IIS7, je třeba provést následující kroky:</span><span class="sxs-lookup"><span data-stu-id="7d594-130">When the ASP.NET application runs on IIS7, you must also perform the following steps:</span></span>

    1. <span data-ttu-id="7d594-131">Otevřete Správce služby IIS a přejděte do aplikace PhotoService v rámci **výchozí webový server**.</span><span class="sxs-lookup"><span data-stu-id="7d594-131">Open IIS Manager and navigate to the PhotoService application under **Default Web Site**.</span></span>

    2. <span data-ttu-id="7d594-132">V **zobrazení funkcí**, dvakrát klikněte na panel **ověřování**.</span><span class="sxs-lookup"><span data-stu-id="7d594-132">In **Features View**, double-click **Authentication**.</span></span>

    3. <span data-ttu-id="7d594-133">Na **ověřování** stránce **anonymní ověřování**.</span><span class="sxs-lookup"><span data-stu-id="7d594-133">On the **Authentication** page, select **Anonymous Authentication**.</span></span>

    4. <span data-ttu-id="7d594-134">V **akce** podokně klikněte na tlačítko **upravit** nastavení zabezpečení objektu zabezpečení, pod které anonymní uživatele se připojí k lokalitě.</span><span class="sxs-lookup"><span data-stu-id="7d594-134">In the **Actions** pane, click **Edit** to set the security principal under which anonymous users will connect to the site.</span></span>

    5. <span data-ttu-id="7d594-135">V **upravit pověření anonymního ověřování** dialogu **identita fondu aplikací**.</span><span class="sxs-lookup"><span data-stu-id="7d594-135">In the **Edit Anonymous Authentication Credentials** dialog box, select **Application pool identity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="7d594-136">Pokud používáte účet Network Service, udělíte anonymním uživatelům všechna přístup k interní síti přidružené k tomuto účtu.</span><span class="sxs-lookup"><span data-stu-id="7d594-136">When you use the Network Service account, you grant anonymous users all the internal network access associated with that account.</span></span>

12. <span data-ttu-id="7d594-137">Pomocí SQL Server Management Studio, nástroje sqlcmd.exe nebo editoru jazyka Transact-SQL v sadě Visual Studio, spusťte následující příkaz jazyka Transact-SQL pro instanci systému SQL Server, který má připojené databázi Northwind:</span><span class="sxs-lookup"><span data-stu-id="7d594-137">By using SQL Server Management Studio, the sqlcmd.exe utility, or the Transact-SQL Editor in Visual Studio, execute the following Transact-SQL command against the instance of SQL Server that has the Northwind database attached:</span></span>

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    <span data-ttu-id="7d594-138">Tím se vytvoří přihlášení v instanci systému SQL Server pro účet Windows použitý ke spuštění služby IIS.</span><span class="sxs-lookup"><span data-stu-id="7d594-138">This creates a login in the SQL Server instance for the Windows account used to run IIS.</span></span> <span data-ttu-id="7d594-139">To umožňuje službě IIS pro připojení k instanci systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7d594-139">This enables IIS to connect to the SQL Server instance.</span></span>

13. <span data-ttu-id="7d594-140">S databází Northwind, připojit spusťte následující příkazy jazyka Transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="7d594-140">With the Northwind database attached, execute the following Transact-SQL commands:</span></span>

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

    <span data-ttu-id="7d594-141">Tím udělíte práva k nové přihlašovací údaje, které umožňuje službě IIS čtení dat z a zapisovat data do databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="7d594-141">This grants rights to the new login, which enables IIS to read data from and write data to the Northwind database.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="7d594-142">Definování datového modelu</span><span class="sxs-lookup"><span data-stu-id="7d594-142">Define the data model</span></span>

1. <span data-ttu-id="7d594-143">V **Průzkumníka řešení**, klikněte pravým tlačítkem na název projektu technologie ASP.NET a potom klikněte na tlačítko **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="7d594-143">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="7d594-144">V **přidat novou položku** dialogu **datový Model Entity ADO.NET**.</span><span class="sxs-lookup"><span data-stu-id="7d594-144">In the **Add New Item** dialog box, select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="7d594-145">Název datového modelu, zadejte `Northwind.edmx`.</span><span class="sxs-lookup"><span data-stu-id="7d594-145">For the name of the data model, type `Northwind.edmx`.</span></span>

4. <span data-ttu-id="7d594-146">V Průvodci modelem Entity Data vyberte **Generovat z databáze**a potom klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="7d594-146">In the Entity Data Model Wizard, select **Generate from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="7d594-147">Datový model připojení k databázi pomocí jedné z následujících kroků a potom klikněte na tlačítko **Další**:</span><span class="sxs-lookup"><span data-stu-id="7d594-147">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="7d594-148">Pokud nemáte připojení k databázi, která jsou už nakonfigurovaná, klikněte na tlačítko **nové připojení** a vytvořit nové připojení.</span><span class="sxs-lookup"><span data-stu-id="7d594-148">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="7d594-149">Další informace najdete v tématu [jak: Vytvoření připojení k databázím serveru SQL](https://go.microsoft.com/fwlink/?LinkId=123631).</span><span class="sxs-lookup"><span data-stu-id="7d594-149">For more information, see [How to: Create Connections to SQL Server Databases](https://go.microsoft.com/fwlink/?LinkId=123631).</span></span> <span data-ttu-id="7d594-150">Tato instance systému SQL Server musí mít připojené ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="7d594-150">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="7d594-151">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="7d594-151">\- or -</span></span>

    - <span data-ttu-id="7d594-152">Pokud máte připojení k databázi již byla konfigurována pro připojení k databázi Northwind, vyberte v seznamu připojení toto připojení.</span><span class="sxs-lookup"><span data-stu-id="7d594-152">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="7d594-153">Na poslední stránce průvodce zaškrtněte políčka pro všechny tabulky v databázi a zrušte zaškrtnutí políček pro zobrazení a uložených procedur.</span><span class="sxs-lookup"><span data-stu-id="7d594-153">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="7d594-154">Klikněte na tlačítko **Dokončit** zavřete průvodce.</span><span class="sxs-lookup"><span data-stu-id="7d594-154">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-data-service"></a><span data-ttu-id="7d594-155">Vytvoření datové služby</span><span class="sxs-lookup"><span data-stu-id="7d594-155">Create the data service</span></span>

1. <span data-ttu-id="7d594-156">V **Průzkumníka řešení**, klikněte pravým tlačítkem na název projektu ASP.NET a potom klikněte na **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="7d594-156">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="7d594-157">V **přidat novou položku** dialogu **službu WCF Data Service**.</span><span class="sxs-lookup"><span data-stu-id="7d594-157">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>

   ![Služby WCF Data Service šablony položky v sadě Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="7d594-159">**Službu WCF Data Service** šablona je k dispozici v sadě Visual Studio 2015, ale ne v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="7d594-159">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

3. <span data-ttu-id="7d594-160">Název služby, zadejte `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="7d594-160">For the name of the service, enter `Northwind`.</span></span>

     <span data-ttu-id="7d594-161">Visual Studio vytvoří soubory značek a kódu XML pro novou službu.</span><span class="sxs-lookup"><span data-stu-id="7d594-161">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="7d594-162">Ve výchozím nastavení otevře se okno editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="7d594-162">By default, the code-editor window opens.</span></span> <span data-ttu-id="7d594-163">V **Průzkumníka řešení**, služba má název, Northwind a rozšíření. svc.cs nebo. svc.vb.</span><span class="sxs-lookup"><span data-stu-id="7d594-163">In **Solution Explorer**, the service has the name, Northwind, and the extension .svc.cs or .svc.vb.</span></span>

4. <span data-ttu-id="7d594-164">V kódu pro datovou službu, nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy, která definuje datové služby s typem, který je kontejner entit datového modelu, který v tomto případě je `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="7d594-164">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="7d594-165">Definice třídy by měl vypadat to následující:</span><span class="sxs-lookup"><span data-stu-id="7d594-165">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a><span data-ttu-id="7d594-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d594-166">See also</span></span>

- [<span data-ttu-id="7d594-167">Vystavení dat jako služby</span><span class="sxs-lookup"><span data-stu-id="7d594-167">Exposing Your Data as a Service</span></span>](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
