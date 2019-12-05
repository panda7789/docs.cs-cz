---
title: 'Postupy: vývoj datové služby WCF běžící v rámci služby IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: 684361dbb97e70296a3061f71102662023f88d9a
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800510"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a><span data-ttu-id="dab6c-102">Postupy: vývoj datové služby WCF běžící v rámci služby IIS</span><span class="sxs-lookup"><span data-stu-id="dab6c-102">How to: Develop a WCF data service running on IIS</span></span>

<span data-ttu-id="dab6c-103">V tomto tématu se dozvíte, jak pomocí WCF Data Services vytvořit datovou službu založenou na ukázkové databázi Northwind, jejímž hostitelem je webová aplikace ASP.NET, která běží na Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="dab6c-103">This topic shows how to use WCF Data Services to create a data service that is based on the Northwind sample database that is hosted by an ASP.NET Web application that is running on Internet Information Services (IIS).</span></span> <span data-ttu-id="dab6c-104">Příklad toho, jak vytvořit stejnou datovou službu Northwind jako ASP.NET webovou aplikaci, která běží na vývojovém serveru ASP.NET, najdete v tématu [rychlý start WCF Data Services](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="dab6c-104">For an example of how to create the same Northwind data service as an ASP.NET Web application that runs on the ASP.NET Development Server, see the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="dab6c-105">Chcete-li vytvořit datovou službu Northwind, je nutné mít nainstalovanou ukázkovou databázi Northwind na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="dab6c-105">To create the Northwind data service, you must have installed the Northwind sample database on the local computer.</span></span> <span data-ttu-id="dab6c-106">Pokud si chcete stáhnout tuto ukázkovou databázi, přečtěte si část [databáze pro stahování a ukázkové databáze pro SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="dab6c-106">To download this sample database, see the download page, [Sample Databases for SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span></span>

<span data-ttu-id="dab6c-107">V tomto tématu se dozvíte, jak vytvořit datovou službu pomocí poskytovatele Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="dab6c-107">This topic shows how to create a data service by using the Entity Framework provider.</span></span> <span data-ttu-id="dab6c-108">Další poskytovatelé datových služeb jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="dab6c-108">Other data services providers are available.</span></span> <span data-ttu-id="dab6c-109">Další informace najdete v tématu [poskytovatelé Data Services](data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="dab6c-109">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>

<span data-ttu-id="dab6c-110">Po vytvoření služby je nutné výslovně poskytnout přístup k prostředkům datové služby.</span><span class="sxs-lookup"><span data-stu-id="dab6c-110">After you create the service, you must explicitly provide access to data service resources.</span></span> <span data-ttu-id="dab6c-111">Další informace najdete v tématu [Postup: povolení přístupu k datové službě](how-to-enable-access-to-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="dab6c-111">For more information, see [How to: Enable Access to the Data Service](how-to-enable-access-to-the-data-service-wcf-data-services.md).</span></span>

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a><span data-ttu-id="dab6c-112">Vytvoření webové aplikace v ASP.NET, která běží na službě IIS</span><span class="sxs-lookup"><span data-stu-id="dab6c-112">Create the ASP.NET web application that runs on IIS</span></span>

1. <span data-ttu-id="dab6c-113">V aplikaci Visual Studio v nabídce **soubor** vyberte **Nový** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="dab6c-113">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

2. <span data-ttu-id="dab6c-114">V dialogovém okně **Nový projekt** vyberte > **Webová** kategorie **instalované** > [**Visual C#**  nebo **Visual Basic**].</span><span class="sxs-lookup"><span data-stu-id="dab6c-114">In the **New Project** dialog box, select the **Installed** > [**Visual C#** or **Visual Basic**] > **Web** category.</span></span>

3. <span data-ttu-id="dab6c-115">Vyberte šablonu **webové aplikace ASP.NET** .</span><span class="sxs-lookup"><span data-stu-id="dab6c-115">Select the **ASP.NET Web Application** template.</span></span>

4. <span data-ttu-id="dab6c-116">Jako název projektu zadejte `NorthwindService`.</span><span class="sxs-lookup"><span data-stu-id="dab6c-116">Enter `NorthwindService` as the name of the project.</span></span>

5. <span data-ttu-id="dab6c-117">Klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="dab6c-117">Click **OK**.</span></span>

6. <span data-ttu-id="dab6c-118">V nabídce **projekt** vyberte **vlastnosti NorthwindService**.</span><span class="sxs-lookup"><span data-stu-id="dab6c-118">On the **Project** menu, select **NorthwindService Properties**.</span></span>

7. <span data-ttu-id="dab6c-119">Vyberte kartu **Web** a pak vyberte **použít místní webový server služby IIS**.</span><span class="sxs-lookup"><span data-stu-id="dab6c-119">Select the **Web** tab, and then select **Use Local IIS Web Server**.</span></span>

8. <span data-ttu-id="dab6c-120">Klikněte na **vytvořit virtuální adresář** a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="dab6c-120">Click **Create Virtual Directory** and then click **OK**.</span></span>

9. <span data-ttu-id="dab6c-121">Z příkazového řádku s oprávněními správce spusťte jeden z následujících příkazů (v závislosti na operačním systému):</span><span class="sxs-lookup"><span data-stu-id="dab6c-121">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="dab6c-122">32bitové systémy:</span><span class="sxs-lookup"><span data-stu-id="dab6c-122">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    - <span data-ttu-id="dab6c-123">64bitové systémy:</span><span class="sxs-lookup"><span data-stu-id="dab6c-123">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     <span data-ttu-id="dab6c-124">Tím se zajistí, že se v počítači zaregistruje Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="dab6c-124">This makes sure that Windows Communication Foundation (WCF) is registered on the computer.</span></span>

10. <span data-ttu-id="dab6c-125">Z příkazového řádku s oprávněními správce spusťte jeden z následujících příkazů (v závislosti na operačním systému):</span><span class="sxs-lookup"><span data-stu-id="dab6c-125">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="dab6c-126">32bitové systémy:</span><span class="sxs-lookup"><span data-stu-id="dab6c-126">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    - <span data-ttu-id="dab6c-127">64bitové systémy:</span><span class="sxs-lookup"><span data-stu-id="dab6c-127">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     <span data-ttu-id="dab6c-128">Tím se zajistí, aby služba IIS běžela správně po instalaci WCF do počítače.</span><span class="sxs-lookup"><span data-stu-id="dab6c-128">This makes sure that IIS runs correctly after WCF has been installed on the computer.</span></span> <span data-ttu-id="dab6c-129">Možná budete muset restartovat taky službu IIS.</span><span class="sxs-lookup"><span data-stu-id="dab6c-129">You might have to also restart IIS.</span></span>

11. <span data-ttu-id="dab6c-130">Když je aplikace ASP.NET spuštěna v IIS7, je nutné provést také následující kroky:</span><span class="sxs-lookup"><span data-stu-id="dab6c-130">When the ASP.NET application runs on IIS7, you must also perform the following steps:</span></span>

    1. <span data-ttu-id="dab6c-131">Otevřete Správce služby IIS a v části **výchozí webový server**přejděte na aplikaci inSlužba.</span><span class="sxs-lookup"><span data-stu-id="dab6c-131">Open IIS Manager and navigate to the PhotoService application under **Default Web Site**.</span></span>

    2. <span data-ttu-id="dab6c-132">V **zobrazení funkcí**poklikejte na **ověřování**.</span><span class="sxs-lookup"><span data-stu-id="dab6c-132">In **Features View**, double-click **Authentication**.</span></span>

    3. <span data-ttu-id="dab6c-133">Na stránce **ověřování** vyberte **anonymní ověřování**.</span><span class="sxs-lookup"><span data-stu-id="dab6c-133">On the **Authentication** page, select **Anonymous Authentication**.</span></span>

    4. <span data-ttu-id="dab6c-134">V podokně **Akce** klikněte na **Upravit** a nastavte objekt zabezpečení, pod kterým se budou anonymní uživatelé připojovat k webu.</span><span class="sxs-lookup"><span data-stu-id="dab6c-134">In the **Actions** pane, click **Edit** to set the security principal under which anonymous users will connect to the site.</span></span>

    5. <span data-ttu-id="dab6c-135">V dialogovém okně **Upravit pověření anonymního ověřování** vyberte možnost **identita fondu aplikací**.</span><span class="sxs-lookup"><span data-stu-id="dab6c-135">In the **Edit Anonymous Authentication Credentials** dialog box, select **Application pool identity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="dab6c-136">Když použijete účet síťové služby, udělíte anonymním uživatelům všechna přístupová práva k interní síti, která jsou přidružená k tomuto účtu.</span><span class="sxs-lookup"><span data-stu-id="dab6c-136">When you use the Network Service account, you grant anonymous users all the internal network access associated with that account.</span></span>

12. <span data-ttu-id="dab6c-137">Pomocí SQL Server Management Studio, nástroje Sqlcmd. exe nebo editoru Transact-SQL v aplikaci Visual Studio spusťte následující příkaz Transact-SQL pro instanci SQL Server s připojenou databází Northwind:</span><span class="sxs-lookup"><span data-stu-id="dab6c-137">By using SQL Server Management Studio, the sqlcmd.exe utility, or the Transact-SQL Editor in Visual Studio, execute the following Transact-SQL command against the instance of SQL Server that has the Northwind database attached:</span></span>

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    <span data-ttu-id="dab6c-138">Tím se vytvoří přihlášení v instanci SQL Server pro účet systému Windows, který se používá ke spouštění služby IIS.</span><span class="sxs-lookup"><span data-stu-id="dab6c-138">This creates a login in the SQL Server instance for the Windows account used to run IIS.</span></span> <span data-ttu-id="dab6c-139">To umožňuje službě IIS připojit se k instanci SQL Server.</span><span class="sxs-lookup"><span data-stu-id="dab6c-139">This enables IIS to connect to the SQL Server instance.</span></span>

13. <span data-ttu-id="dab6c-140">S připojenou databází Northwind spusťte následující příkazy jazyka Transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="dab6c-140">With the Northwind database attached, execute the following Transact-SQL commands:</span></span>

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

    <span data-ttu-id="dab6c-141">Tím se uděluje oprávnění k novému přihlášení, které službě IIS umožňuje číst data a zapisovat data do databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="dab6c-141">This grants rights to the new login, which enables IIS to read data from and write data to the Northwind database.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="dab6c-142">Definování datového modelu</span><span class="sxs-lookup"><span data-stu-id="dab6c-142">Define the data model</span></span>

1. <span data-ttu-id="dab6c-143">V **Průzkumník řešení**klikněte pravým tlačítkem myši na název projektu ASP.NET a potom klikněte na **Přidat** > **Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="dab6c-143">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="dab6c-144">V dialogovém okně **Přidat novou položku** vyberte **ADO.NET model EDM (Entity Data Model)** .</span><span class="sxs-lookup"><span data-stu-id="dab6c-144">In the **Add New Item** dialog box, select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="dab6c-145">Pro název datového modelu zadejte `Northwind.edmx`.</span><span class="sxs-lookup"><span data-stu-id="dab6c-145">For the name of the data model, type `Northwind.edmx`.</span></span>

4. <span data-ttu-id="dab6c-146">V průvodci model EDM (Entity Data Model) vyberte **Generovat z databáze**a pak klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="dab6c-146">In the Entity Data Model Wizard, select **Generate from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="dab6c-147">Pomocí jednoho z následujících kroků připojte datový model k databázi a potom klikněte na tlačítko **Další**:</span><span class="sxs-lookup"><span data-stu-id="dab6c-147">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="dab6c-148">Pokud již nemáte nakonfigurované připojení k databázi, klikněte na tlačítko **nové připojení** a vytvořte nové připojení.</span><span class="sxs-lookup"><span data-stu-id="dab6c-148">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="dab6c-149">Další informace naleznete v tématu [How to: Create Connections to SQL Server databases](https://go.microsoft.com/fwlink/?LinkId=123631).</span><span class="sxs-lookup"><span data-stu-id="dab6c-149">For more information, see [How to: Create Connections to SQL Server Databases](https://go.microsoft.com/fwlink/?LinkId=123631).</span></span> <span data-ttu-id="dab6c-150">Tato instance SQL Server musí mít připojenou ukázkovou databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="dab6c-150">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="dab6c-151">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="dab6c-151">\- or -</span></span>

    - <span data-ttu-id="dab6c-152">Pokud máte připojení k databázi, které je už nakonfigurované pro připojení k databázi Northwind, vyberte toto připojení ze seznamu připojení.</span><span class="sxs-lookup"><span data-stu-id="dab6c-152">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="dab6c-153">Na poslední stránce průvodce zaškrtněte políčka pro všechny tabulky v databázi a zrušte zaškrtnutí políček u zobrazení a uložených procedur.</span><span class="sxs-lookup"><span data-stu-id="dab6c-153">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="dab6c-154">Kliknutím na tlačítko **Dokončit** zavřete průvodce.</span><span class="sxs-lookup"><span data-stu-id="dab6c-154">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-data-service"></a><span data-ttu-id="dab6c-155">Vytvoření datové služby</span><span class="sxs-lookup"><span data-stu-id="dab6c-155">Create the data service</span></span>

1. <span data-ttu-id="dab6c-156">V **Průzkumník řešení**klikněte pravým tlačítkem myši na název projektu ASP.NET a potom klikněte na **Přidat** > **Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="dab6c-156">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="dab6c-157">V dialogovém okně **Přidat novou položku** vyberte **WCF Data Service**.</span><span class="sxs-lookup"><span data-stu-id="dab6c-157">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>

   ![Šablona položky datové služby WCF v aplikaci Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="dab6c-159">Šablona **WCF Data Service** je k dispozici v aplikaci visual Studio 2015, ale ne v aplikaci visual Studio 2017 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="dab6c-159">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

3. <span data-ttu-id="dab6c-160">Jako název služby zadejte `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="dab6c-160">For the name of the service, enter `Northwind`.</span></span>

     <span data-ttu-id="dab6c-161">Visual Studio vytvoří kód XML a soubory kódu pro novou službu.</span><span class="sxs-lookup"><span data-stu-id="dab6c-161">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="dab6c-162">Ve výchozím nastavení se otevře okno Editor kódu.</span><span class="sxs-lookup"><span data-stu-id="dab6c-162">By default, the code-editor window opens.</span></span> <span data-ttu-id="dab6c-163">V **Průzkumník řešení**má služba název, Northwind a příponu. svc.cs nebo. svc. vb.</span><span class="sxs-lookup"><span data-stu-id="dab6c-163">In **Solution Explorer**, the service has the name, Northwind, and the extension .svc.cs or .svc.vb.</span></span>

4. <span data-ttu-id="dab6c-164">V kódu pro datovou službu nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy definující datovou službu s typem, který je kontejnerem entit datového modelu, který je v tomto případě `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="dab6c-164">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="dab6c-165">Definice třídy by měla vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="dab6c-165">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a><span data-ttu-id="dab6c-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dab6c-166">See also</span></span>

- [<span data-ttu-id="dab6c-167">Vystavení dat jako služby</span><span class="sxs-lookup"><span data-stu-id="dab6c-167">Exposing Your Data as a Service</span></span>](exposing-your-data-as-a-service-wcf-data-services.md)
