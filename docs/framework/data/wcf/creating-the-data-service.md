---
title: Vytvoření datové služby WCF v sadě Visual Studio
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: e8d82ff8958af12842366911b6633ea6b2e0efbb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765847"
---
# <a name="create-the-data-service"></a><span data-ttu-id="ba819-102">Vytvoření datové služby</span><span class="sxs-lookup"><span data-stu-id="ba819-102">Create the data service</span></span>

<span data-ttu-id="ba819-103">V tomto tématu vytvoříte ukázkové datových služeb WCF Data Services využívá k tomu, [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informační kanál, který je založen na ukázkovou databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="ba819-103">In this topic, you create a sample data service that uses WCF Data Services to expose an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed that's based on the Northwind sample database.</span></span> <span data-ttu-id="ba819-104">Úloha zahrnuje následující základní kroky:</span><span class="sxs-lookup"><span data-stu-id="ba819-104">The task involves the following basic steps:</span></span>

1. <span data-ttu-id="ba819-105">Vytvoření webové aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ba819-105">Create an ASP.NET Web application.</span></span>

2. <span data-ttu-id="ba819-106">Definování datového modelu s použitím nástroje modelu Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="ba819-106">Define the data model by using the Entity Data Model tools.</span></span>

3. <span data-ttu-id="ba819-107">Přidáte datové služby na webovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ba819-107">Add the data service to the Web application.</span></span>

4. <span data-ttu-id="ba819-108">Povolení přístupu k datové službě.</span><span class="sxs-lookup"><span data-stu-id="ba819-108">Enable access to the data service.</span></span>

## <a name="create-the-aspnet-web-app"></a><span data-ttu-id="ba819-109">Vytvoření webové aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ba819-109">Create the ASP.NET web app</span></span>

1. <span data-ttu-id="ba819-110">V sadě Visual Studio na **souboru** nabídce vyberte možnost **nový** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="ba819-110">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

1. <span data-ttu-id="ba819-111">V **nový projekt** dialogové okno, v rámci jazyka Visual Basic nebo Visual C# vyberte **webové** kategorie a pak vyberte **webová aplikace ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="ba819-111">In the **New Project** dialog box, under either Visual Basic or Visual C# select the **Web** category, and then select **ASP.NET Web Application**.</span></span>

1. <span data-ttu-id="ba819-112">Zadejte `NorthwindService` jako název projektu a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="ba819-112">Enter `NorthwindService` as the name of the project and then select **OK**.</span></span>

1. <span data-ttu-id="ba819-113">V **nová webová aplikace ASP.NET** dialogového okna, vyberte **prázdný** a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="ba819-113">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

1. <span data-ttu-id="ba819-114">(Volitelné) Zadejte číslo portu specifické pro vaši webovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ba819-114">(Optional) Specify a specific port number for your Web application.</span></span> <span data-ttu-id="ba819-115">Poznámka: číslo portu `12345` slouží v této sérii témat rychlý start.</span><span class="sxs-lookup"><span data-stu-id="ba819-115">Note: the port number `12345` is used in this series of quickstart topics.</span></span>

    1. <span data-ttu-id="ba819-116">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt ASP.NET, který jste právě vytvořili a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="ba819-116">In **Solution Explorer**, right-click on the ASP.NET project that you just created, and then choose **Properties**.</span></span>

    2. <span data-ttu-id="ba819-117">Vyberte **webové** kartu a nastavte hodnotu **specifického portu** textové pole pro `12345`.</span><span class="sxs-lookup"><span data-stu-id="ba819-117">Select the **Web** tab, and set the value of the **Specific port** text box to `12345`.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="ba819-118">Definování datového modelu</span><span class="sxs-lookup"><span data-stu-id="ba819-118">Define the data model</span></span>

1. <span data-ttu-id="ba819-119">V **Průzkumníka řešení**, klikněte pravým tlačítkem na název projektu technologie ASP.NET a potom klikněte na tlačítko **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="ba819-119">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="ba819-120">V **přidat novou položku** dialogové okno, vyberte **Data** kategorie a pak vyberte **datový Model Entity ADO.NET**.</span><span class="sxs-lookup"><span data-stu-id="ba819-120">In the **Add New Item** dialog box, select the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="ba819-121">Název datového modelu, zadejte `Northwind.edmx`.</span><span class="sxs-lookup"><span data-stu-id="ba819-121">For the name of the data model, enter `Northwind.edmx`.</span></span>

4. <span data-ttu-id="ba819-122">V **Průvodce datovým modelem Entity**vyberte **EF designeru z databáze**a potom klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="ba819-122">In the **Entity Data Model Wizard**, select **EF Designer from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="ba819-123">Datový model připojení k databázi pomocí jedné z následujících kroků a potom klikněte na tlačítko **Další**:</span><span class="sxs-lookup"><span data-stu-id="ba819-123">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="ba819-124">Pokud nemáte připojení k databázi, která jsou už nakonfigurovaná, klikněte na tlačítko **nové připojení** a vytvořit nové připojení.</span><span class="sxs-lookup"><span data-stu-id="ba819-124">If you don't have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="ba819-125">Další informace najdete v tématu [jak: Vytvoření připojení k databázím serveru SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="ba819-125">For more information, see [How to: Create Connections to SQL Server Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span></span> <span data-ttu-id="ba819-126">Tato instance systému SQL Server musí mít připojené ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="ba819-126">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="ba819-127">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="ba819-127">\- or -</span></span>

    - <span data-ttu-id="ba819-128">Pokud máte připojení k databázi již byla konfigurována pro připojení k databázi Northwind, vyberte v seznamu připojení toto připojení.</span><span class="sxs-lookup"><span data-stu-id="ba819-128">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="ba819-129">Na poslední stránce průvodce zaškrtněte políčka pro všechny tabulky v databázi a zrušte zaškrtnutí políček pro zobrazení a uložených procedur.</span><span class="sxs-lookup"><span data-stu-id="ba819-129">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="ba819-130">Klikněte na tlačítko **Dokončit** zavřete průvodce.</span><span class="sxs-lookup"><span data-stu-id="ba819-130">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-wcf-data-service"></a><span data-ttu-id="ba819-131">Vytvoření datové služby WCF</span><span class="sxs-lookup"><span data-stu-id="ba819-131">Create the WCF data service</span></span>

1. <span data-ttu-id="ba819-132">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt ASP.NET a klikněte na tlačítko **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="ba819-132">In **Solution Explorer**, right-click on the ASP.NET project, and then choose **Add** > **New Item**.</span></span>

2. <span data-ttu-id="ba819-133">V **přidat novou položku** dialogové okno, vyberte **službu WCF Data Service** šablony položky z **webové** kategorie.</span><span class="sxs-lookup"><span data-stu-id="ba819-133">In the **Add New Item** dialog box, select the **WCF Data Service** item template from the **Web** category.</span></span>

   ![Služby WCF Data Service šablony položky v sadě Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="ba819-135">**Službu WCF Data Service** šablona je k dispozici v sadě Visual Studio 2015, ale ne v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="ba819-135">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

3. <span data-ttu-id="ba819-136">Název služby zadáte `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="ba819-136">For the name of the service, type `Northwind`.</span></span>

     <span data-ttu-id="ba819-137">Visual Studio vytvoří soubory značek a kódu XML pro novou službu.</span><span class="sxs-lookup"><span data-stu-id="ba819-137">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="ba819-138">Ve výchozím nastavení otevře se okno editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="ba819-138">By default, the code-editor window opens.</span></span> <span data-ttu-id="ba819-139">V **Průzkumníka řešení**, službu s názvem Northwind s příponou *. svc.cs* nebo *. svc.vb*.</span><span class="sxs-lookup"><span data-stu-id="ba819-139">In **Solution Explorer**, the service has the name Northwind with the extension *.svc.cs* or *.svc.vb*.</span></span>

4. <span data-ttu-id="ba819-140">V kódu pro datovou službu, nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy, která definuje datové služby s typem, který je kontejner entit datového modelu, který v tomto případě je `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="ba819-140">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="ba819-141">Definice třídy by měl vypadat to následující:</span><span class="sxs-lookup"><span data-stu-id="ba819-141">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a><span data-ttu-id="ba819-142">Povolení přístupu k prostředkům datové služby</span><span class="sxs-lookup"><span data-stu-id="ba819-142">Enable access to data service resources</span></span>

1. <span data-ttu-id="ba819-143">V kódu pro datovou službu, nahraďte zástupný symbol kód v `InitializeService` funkce následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="ba819-143">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]

     <span data-ttu-id="ba819-144">To umožňuje autorizovaným klientům ke čtení a zápis k prostředkům určené sady entit.</span><span class="sxs-lookup"><span data-stu-id="ba819-144">This enables authorized clients to have read and write access to resources for the specified entity sets.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ba819-145">Libovolného klienta, který má přístup k aplikaci technologie ASP.NET můžete také přístup k prostředkům vystavené datové služby.</span><span class="sxs-lookup"><span data-stu-id="ba819-145">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="ba819-146">V produkčním datové služby chcete-li zabránit neoprávněnému přístupu k prostředkům byste měli také zabezpečit samotná aplikace.</span><span class="sxs-lookup"><span data-stu-id="ba819-146">In a production data service, to prevent unauthorized access to resources you should also secure the application itself.</span></span> <span data-ttu-id="ba819-147">Další informace najdete v tématu [zabezpečení služeb WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="ba819-147">For more information, see [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="ba819-148">Další kroky</span><span class="sxs-lookup"><span data-stu-id="ba819-148">Next steps</span></span>

<span data-ttu-id="ba819-149">Úspěšně jste vytvořili novou službu data, která vystavuje kanál OData, která je založena na ukázkovou databázi Northwind a povolíte přístup ke kanálu pro klienty, kteří mají oprávnění na webovou aplikaci ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ba819-149">You have successfully created a new data service that exposes an OData feed that is based on the Northwind sample database, and you have enabled access to the feed for clients that have permissions on the ASP.NET Web application.</span></span> <span data-ttu-id="ba819-150">Teď se spustit službu data ze sady Visual Studio a přístup, odešlete požadavky HTTP GET přes webový prohlížeč datového kanálu OData:</span><span class="sxs-lookup"><span data-stu-id="ba819-150">Next, you'll start the data service from Visual Studio and access the OData feed by submitting HTTP GET requests through a Web browser:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ba819-151">Přístup ke službě z webového prohlížeče</span><span class="sxs-lookup"><span data-stu-id="ba819-151">Access the service from a web browser</span></span>](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="ba819-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba819-152">See also</span></span>

- <span data-ttu-id="ba819-153">[Datový Model Entity ADO.NET nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ba819-153">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>