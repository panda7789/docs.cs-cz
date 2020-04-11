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
ms.openlocfilehash: 8a1a0c2c55267940463e2c9ab82bb52345269260
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121604"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a><span data-ttu-id="753a7-102">Postup: Vývoj datové služby WCF spuštěné ve službě IIS</span><span class="sxs-lookup"><span data-stu-id="753a7-102">How to: Develop a WCF data service running on IIS</span></span>

<span data-ttu-id="753a7-103">Tento článek ukazuje, jak pomocí služby WCF Data Services vytvořit datovou službu založenou na ukázkové databázi Northwind, která je hostovaná ASP.NET webovou aplikaci spuštěnou v Internetové informační službě (IIS).</span><span class="sxs-lookup"><span data-stu-id="753a7-103">This article shows how to use WCF Data Services to create a data service that's based on the Northwind sample database that's hosted by an ASP.NET Web app running on Internet Information Services (IIS).</span></span> <span data-ttu-id="753a7-104">Příklad, jak vytvořit stejnou datovou službu Northwind jako ASP.NET webovou aplikaci, která běží na ASP.NET vývojovém serveru, naleznete v [rychlém startu služby WCF Data Services](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="753a7-104">For an example of how to create the same Northwind data service as an ASP.NET Web app that runs on the ASP.NET Development Server, see the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="753a7-105">Chcete-li vytvořit datovou službu Northwind, nejprve nainstalujte ukázkovou databázi Northwind do místního počítače.</span><span class="sxs-lookup"><span data-stu-id="753a7-105">To create the Northwind data service, first install the Northwind sample database on the local computer.</span></span> <span data-ttu-id="753a7-106">Chcete-li databázi nainstalovat, spusťte skript Transact-SQL z [ukázkových databází Northwind a pubs pro microsoft sql server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span><span class="sxs-lookup"><span data-stu-id="753a7-106">To install the database, run the Transact-SQL script from [Northwind and pubs sample databases for Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>

<span data-ttu-id="753a7-107">Tento článek ukazuje, jak vytvořit datovou službu pomocí zprostředkovatele Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="753a7-107">This article shows how to create a data service by using the Entity Framework provider.</span></span> <span data-ttu-id="753a7-108">K dispozici jsou i další poskytovatelé datových služeb.</span><span class="sxs-lookup"><span data-stu-id="753a7-108">Other data services providers are available.</span></span> <span data-ttu-id="753a7-109">Další informace naleznete v tématu [Poskytovatelé datových služeb](data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="753a7-109">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>

<span data-ttu-id="753a7-110">Po vytvoření služby je nutné explicitně poskytnout přístup k prostředkům datové služby.</span><span class="sxs-lookup"><span data-stu-id="753a7-110">After you create the service, you must explicitly provide access to data service resources.</span></span> <span data-ttu-id="753a7-111">Další informace naleznete v [tématu How to: Enable Access to the Data Service](how-to-enable-access-to-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="753a7-111">For more information, see [How to: Enable Access to the Data Service](how-to-enable-access-to-the-data-service-wcf-data-services.md).</span></span>

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a><span data-ttu-id="753a7-112">Vytvoření ASP.NET webové aplikace spuštěné ve službě IIS</span><span class="sxs-lookup"><span data-stu-id="753a7-112">Create the ASP.NET web application that runs on IIS</span></span>

1. <span data-ttu-id="753a7-113">V sadě Visual Studio vyberte v nabídce **Soubor** **položku Nový** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="753a7-113">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

2. <span data-ttu-id="753a7-114">V dialogovém okně **Nový projekt** vyberte > **kategorii Web** **nainstalované** > [**Visual C#** nebo **Visual Basic].**</span><span class="sxs-lookup"><span data-stu-id="753a7-114">In the **New Project** dialog box, select the **Installed** > [**Visual C#** or **Visual Basic**] > **Web** category.</span></span>

3. <span data-ttu-id="753a7-115">Vyberte šablonu **webové aplikace ASP.NET.**</span><span class="sxs-lookup"><span data-stu-id="753a7-115">Select the **ASP.NET Web Application** template.</span></span>

4. <span data-ttu-id="753a7-116">Zadejte `NorthwindService` jako název projektu.</span><span class="sxs-lookup"><span data-stu-id="753a7-116">Enter `NorthwindService` as the name of the project.</span></span>

5. <span data-ttu-id="753a7-117">Klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="753a7-117">Click **OK**.</span></span>

6. <span data-ttu-id="753a7-118">V nabídce **Project** vyberte **možnost NorthwindService Properties**.</span><span class="sxs-lookup"><span data-stu-id="753a7-118">On the **Project** menu, select **NorthwindService Properties**.</span></span>

7. <span data-ttu-id="753a7-119">Vyberte kartu **Web** a potom vyberte **Použít místní webový server služby IIS**.</span><span class="sxs-lookup"><span data-stu-id="753a7-119">Select the **Web** tab, and then select **Use Local IIS Web Server**.</span></span>

8. <span data-ttu-id="753a7-120">Klepněte na tlačítko **Vytvořit virtuální adresář** a potom klepněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="753a7-120">Click **Create Virtual Directory** and then click **OK**.</span></span>

9. <span data-ttu-id="753a7-121">Z příkazového řádku s oprávněními správce spusťte jeden z následujících příkazů (v závislosti na operačním systému):</span><span class="sxs-lookup"><span data-stu-id="753a7-121">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="753a7-122">32bitové systémy:</span><span class="sxs-lookup"><span data-stu-id="753a7-122">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    - <span data-ttu-id="753a7-123">64bitové systémy:</span><span class="sxs-lookup"><span data-stu-id="753a7-123">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     <span data-ttu-id="753a7-124">Tím zajistíte, že windows communication foundation (WCF) je registrována v počítači.</span><span class="sxs-lookup"><span data-stu-id="753a7-124">This makes sure that Windows Communication Foundation (WCF) is registered on the computer.</span></span>

10. <span data-ttu-id="753a7-125">Z příkazového řádku s oprávněními správce spusťte jeden z následujících příkazů (v závislosti na operačním systému):</span><span class="sxs-lookup"><span data-stu-id="753a7-125">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="753a7-126">32bitové systémy:</span><span class="sxs-lookup"><span data-stu-id="753a7-126">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    - <span data-ttu-id="753a7-127">64bitové systémy:</span><span class="sxs-lookup"><span data-stu-id="753a7-127">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     <span data-ttu-id="753a7-128">Tím zajistíte, že iis běží správně po wcf byl nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="753a7-128">This makes sure that IIS runs correctly after WCF has been installed on the computer.</span></span> <span data-ttu-id="753a7-129">Bude pravděpodobně nutné restartovat službu IIS.</span><span class="sxs-lookup"><span data-stu-id="753a7-129">You might have to also restart IIS.</span></span>

11. <span data-ttu-id="753a7-130">Při spuštění ASP.NET aplikace v systému IIS7 je nutné provést také následující kroky:</span><span class="sxs-lookup"><span data-stu-id="753a7-130">When the ASP.NET application runs on IIS7, you must also perform the following steps:</span></span>

    1. <span data-ttu-id="753a7-131">Otevřete Správce služby IIS a přejděte do aplikace PhotoService v části **Výchozí web**.</span><span class="sxs-lookup"><span data-stu-id="753a7-131">Open IIS Manager and navigate to the PhotoService application under **Default Web Site**.</span></span>

    2. <span data-ttu-id="753a7-132">V **zobrazení funkcí**poklepejte na **položku Ověřování**.</span><span class="sxs-lookup"><span data-stu-id="753a7-132">In **Features View**, double-click **Authentication**.</span></span>

    3. <span data-ttu-id="753a7-133">Na stránce **Ověřování** vyberte **možnost Anonymní ověřování**.</span><span class="sxs-lookup"><span data-stu-id="753a7-133">On the **Authentication** page, select **Anonymous Authentication**.</span></span>

    4. <span data-ttu-id="753a7-134">V podokně **Akce** klikněte na **Upravit** a nastavte zaregistrovaný objekt zabezpečení, pod kterým se anonymní uživatelé připojí k webu.</span><span class="sxs-lookup"><span data-stu-id="753a7-134">In the **Actions** pane, click **Edit** to set the security principal under which anonymous users will connect to the site.</span></span>

    5. <span data-ttu-id="753a7-135">V dialogovém okně **Upravit anonymní ověřovací pověření** vyberte **identitu fondu aplikací**.</span><span class="sxs-lookup"><span data-stu-id="753a7-135">In the **Edit Anonymous Authentication Credentials** dialog box, select **Application pool identity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="753a7-136">Používáte-li účet síťové služby, udělíte anonymním uživatelům veškerý interní přístup k síti přidružený k tomuto účtu.</span><span class="sxs-lookup"><span data-stu-id="753a7-136">When you use the Network Service account, you grant anonymous users all the internal network access associated with that account.</span></span>

12. <span data-ttu-id="753a7-137">Pomocí SQL Server Management Studio, sqlcmd.exe nástroj nebo Transact-SQL Editor v sadě Visual Studio, spusťte následující příkaz Transact-SQL proti instanci SQL Server, který má připojenou databázi Northwind:</span><span class="sxs-lookup"><span data-stu-id="753a7-137">By using SQL Server Management Studio, the sqlcmd.exe utility, or the Transact-SQL Editor in Visual Studio, execute the following Transact-SQL command against the instance of SQL Server that has the Northwind database attached:</span></span>

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    <span data-ttu-id="753a7-138">Tím se vytvoří přihlášení v instanci serveru SQL Server pro účet systému Windows používaný ke spuštění služby IIS.</span><span class="sxs-lookup"><span data-stu-id="753a7-138">This creates a login in the SQL Server instance for the Windows account used to run IIS.</span></span> <span data-ttu-id="753a7-139">To umožňuje službě IIS připojit se k instanci serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="753a7-139">This enables IIS to connect to the SQL Server instance.</span></span>

13. <span data-ttu-id="753a7-140">S připojenou databází Northwind proveďte následující příkazy Transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="753a7-140">With the Northwind database attached, execute the following Transact-SQL commands:</span></span>

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

    <span data-ttu-id="753a7-141">To uděluje práva na nové přihlášení, které umožňuje službě IIS číst data z databáze Northwind a zapisovat je.</span><span class="sxs-lookup"><span data-stu-id="753a7-141">This grants rights to the new login, which enables IIS to read data from and write data to the Northwind database.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="753a7-142">Definování datového modelu</span><span class="sxs-lookup"><span data-stu-id="753a7-142">Define the data model</span></span>

1. <span data-ttu-id="753a7-143">V **Průzkumníku řešení**klikněte pravým tlačítkem myši na název projektu ASP.NET a potom klikněte na **přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="753a7-143">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="753a7-144">V dialogovém okně **Přidat novou položku** vyberte **ADO.NET datový model entity**.</span><span class="sxs-lookup"><span data-stu-id="753a7-144">In the **Add New Item** dialog box, select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="753a7-145">Pro název datového modelu `Northwind.edmx`zadejte .</span><span class="sxs-lookup"><span data-stu-id="753a7-145">For the name of the data model, type `Northwind.edmx`.</span></span>

4. <span data-ttu-id="753a7-146">V Průvodci datovým modelem entity vyberte **Generovat z databáze**a klepněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="753a7-146">In the Entity Data Model Wizard, select **Generate from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="753a7-147">Připojte datový model k databázi jedním z následujících kroků a potom klepněte na tlačítko **Další**:</span><span class="sxs-lookup"><span data-stu-id="753a7-147">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="753a7-148">Pokud již nemáte nakonfigurované připojení k databázi, klepněte na tlačítko **Nové připojení** a vytvořte nové připojení.</span><span class="sxs-lookup"><span data-stu-id="753a7-148">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="753a7-149">Další informace naleznete v [tématu How to: Create Connections to SQL Server Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="753a7-149">For more information, see [How to: Create Connections to SQL Server Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span></span> <span data-ttu-id="753a7-150">Tato instance serveru SQL Server musí mít připojenu ukázkovou databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="753a7-150">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="753a7-151">\-nebo -</span><span class="sxs-lookup"><span data-stu-id="753a7-151">\- or -</span></span>

    - <span data-ttu-id="753a7-152">Pokud máte již nakonfigurované připojení k databázi Northwind, vyberte toto připojení ze seznamu připojení.</span><span class="sxs-lookup"><span data-stu-id="753a7-152">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="753a7-153">Na poslední stránce průvodce zaškrtněte políčka pro všechny tabulky v databázi a zrušte zaškrtnutí políček pro zobrazení a uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="753a7-153">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="753a7-154">Chcete-li průvodce zavřít, klepněte na tlačítko **Dokončit.**</span><span class="sxs-lookup"><span data-stu-id="753a7-154">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-data-service"></a><span data-ttu-id="753a7-155">Vytvoření datové služby</span><span class="sxs-lookup"><span data-stu-id="753a7-155">Create the data service</span></span>

1. <span data-ttu-id="753a7-156">V **Průzkumníku řešení**klikněte pravým tlačítkem myši na název projektu ASP.NET a potom klikněte na **přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="753a7-156">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="753a7-157">V dialogovém okně **Přidat novou položku** vyberte **datovou službu WCF**.</span><span class="sxs-lookup"><span data-stu-id="753a7-157">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>

   ![Šablona položky datové služby WCF v Sadě Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="753a7-159">Šablona **WCF Data Service** je k dispozici ve Visual Studiu 2015, ale ne v Visual Studiu 2017 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="753a7-159">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

3. <span data-ttu-id="753a7-160">Pro název služby zadejte `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="753a7-160">For the name of the service, enter `Northwind`.</span></span>

     <span data-ttu-id="753a7-161">Visual Studio vytvoří xml značky a soubory kódu pro novou službu.</span><span class="sxs-lookup"><span data-stu-id="753a7-161">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="753a7-162">Ve výchozím nastavení se otevře okno editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="753a7-162">By default, the code-editor window opens.</span></span> <span data-ttu-id="753a7-163">V **Průzkumníku řešení**má služba název Northwind a rozšíření .svc.cs nebo .svc.vb.</span><span class="sxs-lookup"><span data-stu-id="753a7-163">In **Solution Explorer**, the service has the name, Northwind, and the extension .svc.cs or .svc.vb.</span></span>

4. <span data-ttu-id="753a7-164">V kódu datové služby nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy, která definuje datovou službu typem, který je `NorthwindEntities`kontejnerem entity datového modelu, což je v tomto případě .</span><span class="sxs-lookup"><span data-stu-id="753a7-164">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="753a7-165">Definice třídy by měla vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="753a7-165">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a><span data-ttu-id="753a7-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="753a7-166">See also</span></span>

- [<span data-ttu-id="753a7-167">Vystavení dat jako služby</span><span class="sxs-lookup"><span data-stu-id="753a7-167">Exposing Your Data as a Service</span></span>](exposing-your-data-as-a-service-wcf-data-services.md)
