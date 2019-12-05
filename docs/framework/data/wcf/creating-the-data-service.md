---
title: Vytvoření datové služby WCF v aplikaci Visual Studio
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: 72e3b35465968674a20aa48262d3425a2190ff74
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802276"
---
# <a name="create-the-data-service"></a><span data-ttu-id="4b84c-102">Vytvoření datové služby</span><span class="sxs-lookup"><span data-stu-id="4b84c-102">Create the data service</span></span>

<span data-ttu-id="4b84c-103">V tomto tématu vytvoříte ukázkovou datovou službu, která používá WCF Data Services k vystavení informačního kanálu OData (Open Data Protocol), který je založen na ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="4b84c-103">In this topic, you create a sample data service that uses WCF Data Services to expose an Open Data Protocol (OData) feed that's based on the Northwind sample database.</span></span> <span data-ttu-id="4b84c-104">Úkol zahrnuje následující základní kroky:</span><span class="sxs-lookup"><span data-stu-id="4b84c-104">The task involves the following basic steps:</span></span>

1. <span data-ttu-id="4b84c-105">Vytvoření webové aplikace v ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4b84c-105">Create an ASP.NET Web application.</span></span>

2. <span data-ttu-id="4b84c-106">Definujte datový model pomocí model EDM (Entity Data Model)ch nástrojů.</span><span class="sxs-lookup"><span data-stu-id="4b84c-106">Define the data model by using the Entity Data Model tools.</span></span>

3. <span data-ttu-id="4b84c-107">Přidejte datovou službu do webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="4b84c-107">Add the data service to the Web application.</span></span>

4. <span data-ttu-id="4b84c-108">Povolte přístup k datové službě.</span><span class="sxs-lookup"><span data-stu-id="4b84c-108">Enable access to the data service.</span></span>

## <a name="create-the-aspnet-web-app"></a><span data-ttu-id="4b84c-109">Vytvoření webové aplikace v ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4b84c-109">Create the ASP.NET web app</span></span>

1. <span data-ttu-id="4b84c-110">V aplikaci Visual Studio v nabídce **soubor** vyberte **Nový** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="4b84c-110">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

1. <span data-ttu-id="4b84c-111">V dialogovém okně **Nový projekt** v části buď Visual Basic nebo Visual C# vyberte kategorii **Web** a pak vyberte **ASP.NET webová aplikace**.</span><span class="sxs-lookup"><span data-stu-id="4b84c-111">In the **New Project** dialog box, under either Visual Basic or Visual C# select the **Web** category, and then select **ASP.NET Web Application**.</span></span>

1. <span data-ttu-id="4b84c-112">Jako název projektu zadejte `NorthwindService` a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="4b84c-112">Enter `NorthwindService` as the name of the project and then select **OK**.</span></span>

1. <span data-ttu-id="4b84c-113">V dialogovém okně **Nová webová aplikace ASP.NET** vyberte **prázdné** a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="4b84c-113">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

1. <span data-ttu-id="4b84c-114">Volitelné Zadejte konkrétní číslo portu pro vaši webovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4b84c-114">(Optional) Specify a specific port number for your Web application.</span></span> <span data-ttu-id="4b84c-115">Poznámka: číslo portu `12345` se používá v této řadě témat pro rychlý Start.</span><span class="sxs-lookup"><span data-stu-id="4b84c-115">Note: the port number `12345` is used in this series of quickstart topics.</span></span>

    1. <span data-ttu-id="4b84c-116">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt ASP.NET, který jste právě vytvořili, a pak zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="4b84c-116">In **Solution Explorer**, right-click on the ASP.NET project that you just created, and then choose **Properties**.</span></span>

    2. <span data-ttu-id="4b84c-117">Vyberte kartu **Web** a nastavte hodnotu textového pole **konkrétní port** na `12345`.</span><span class="sxs-lookup"><span data-stu-id="4b84c-117">Select the **Web** tab, and set the value of the **Specific port** text box to `12345`.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="4b84c-118">Definování datového modelu</span><span class="sxs-lookup"><span data-stu-id="4b84c-118">Define the data model</span></span>

1. <span data-ttu-id="4b84c-119">V **Průzkumník řešení**klikněte pravým tlačítkem myši na název projektu ASP.NET a potom klikněte na **Přidat** > **Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="4b84c-119">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="4b84c-120">V dialogovém okně **Přidat novou položku** vyberte kategorii **dat** a pak vyberte **ADO.NET model EDM (Entity Data Model)** .</span><span class="sxs-lookup"><span data-stu-id="4b84c-120">In the **Add New Item** dialog box, select the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="4b84c-121">Jako název datového modelu zadejte `Northwind.edmx`.</span><span class="sxs-lookup"><span data-stu-id="4b84c-121">For the name of the data model, enter `Northwind.edmx`.</span></span>

4. <span data-ttu-id="4b84c-122">V **průvodci model EDM (Entity Data Model)** vyberte **EF Designer z databáze**a pak klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="4b84c-122">In the **Entity Data Model Wizard**, select **EF Designer from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="4b84c-123">Pomocí jednoho z následujících kroků připojte datový model k databázi a potom klikněte na tlačítko **Další**:</span><span class="sxs-lookup"><span data-stu-id="4b84c-123">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="4b84c-124">Pokud nemáte připojení databáze již nakonfigurováno, klikněte na tlačítko **nové připojení** a vytvořte nové připojení.</span><span class="sxs-lookup"><span data-stu-id="4b84c-124">If you don't have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="4b84c-125">Další informace naleznete v tématu [How to: Create Connections to SQL Server databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="4b84c-125">For more information, see [How to: Create Connections to SQL Server Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span></span> <span data-ttu-id="4b84c-126">Tato instance SQL Server musí mít připojenou ukázkovou databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="4b84c-126">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="4b84c-127">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="4b84c-127">\- or -</span></span>

    - <span data-ttu-id="4b84c-128">Pokud máte připojení k databázi, které je už nakonfigurované pro připojení k databázi Northwind, vyberte toto připojení ze seznamu připojení.</span><span class="sxs-lookup"><span data-stu-id="4b84c-128">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="4b84c-129">Na poslední stránce průvodce zaškrtněte políčka pro všechny tabulky v databázi a zrušte zaškrtnutí políček u zobrazení a uložených procedur.</span><span class="sxs-lookup"><span data-stu-id="4b84c-129">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="4b84c-130">Kliknutím na tlačítko **Dokončit** zavřete průvodce.</span><span class="sxs-lookup"><span data-stu-id="4b84c-130">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-wcf-data-service"></a><span data-ttu-id="4b84c-131">Vytvoření datové služby WCF</span><span class="sxs-lookup"><span data-stu-id="4b84c-131">Create the WCF data service</span></span>

1. <span data-ttu-id="4b84c-132">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt ASP.NET a pak zvolte **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="4b84c-132">In **Solution Explorer**, right-click on the ASP.NET project, and then choose **Add** > **New Item**.</span></span>

2. <span data-ttu-id="4b84c-133">V dialogovém okně **Přidat novou položku** vyberte v kategorii **Web** šablonu položky **datové služby WCF** .</span><span class="sxs-lookup"><span data-stu-id="4b84c-133">In the **Add New Item** dialog box, select the **WCF Data Service** item template from the **Web** category.</span></span>

   ![Šablona položky datové služby WCF v aplikaci Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="4b84c-135">Šablona **WCF Data Service** je k dispozici v aplikaci visual Studio 2015, ale ne v aplikaci visual Studio 2017 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="4b84c-135">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

3. <span data-ttu-id="4b84c-136">Jako název služby zadejte `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="4b84c-136">For the name of the service, type `Northwind`.</span></span>

     <span data-ttu-id="4b84c-137">Visual Studio vytvoří kód XML a soubory kódu pro novou službu.</span><span class="sxs-lookup"><span data-stu-id="4b84c-137">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="4b84c-138">Ve výchozím nastavení se otevře okno Editor kódu.</span><span class="sxs-lookup"><span data-stu-id="4b84c-138">By default, the code-editor window opens.</span></span> <span data-ttu-id="4b84c-139">V **Průzkumník řešení**služba má název Northwind s příponou *. svc.cs* nebo *. svc. vb*.</span><span class="sxs-lookup"><span data-stu-id="4b84c-139">In **Solution Explorer**, the service has the name Northwind with the extension *.svc.cs* or *.svc.vb*.</span></span>

4. <span data-ttu-id="4b84c-140">V kódu pro datovou službu nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy definující datovou službu s typem, který je kontejnerem entit datového modelu, který je v tomto případě `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="4b84c-140">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="4b84c-141">Definice třídy by měla vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="4b84c-141">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a><span data-ttu-id="4b84c-142">Povolit přístup k prostředkům datové služby</span><span class="sxs-lookup"><span data-stu-id="4b84c-142">Enable access to data service resources</span></span>

1. <span data-ttu-id="4b84c-143">V kódu pro datovou službu nahraďte zástupný kód ve funkci `InitializeService` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="4b84c-143">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]

     <span data-ttu-id="4b84c-144">To umožňuje autorizovaným klientům mít přístup pro čtení a zápis k prostředkům pro zadané sady entit.</span><span class="sxs-lookup"><span data-stu-id="4b84c-144">This enables authorized clients to have read and write access to resources for the specified entity sets.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4b84c-145">Každý klient, který má přístup k aplikaci ASP.NET, může také přistupovat k prostředkům vystaveným datovou službou.</span><span class="sxs-lookup"><span data-stu-id="4b84c-145">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="4b84c-146">V provozní datové službě, abyste zabránili neoprávněnému přístupu k prostředkům, měli byste také zabezpečit samotnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4b84c-146">In a production data service, to prevent unauthorized access to resources you should also secure the application itself.</span></span> <span data-ttu-id="4b84c-147">Další informace najdete v tématu [zabezpečení WCF Data Services](securing-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="4b84c-147">For more information, see [Securing WCF Data Services](securing-wcf-data-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="4b84c-148">Další kroky</span><span class="sxs-lookup"><span data-stu-id="4b84c-148">Next steps</span></span>

<span data-ttu-id="4b84c-149">Úspěšně jste vytvořili novou datovou službu, která zveřejňuje kanál OData založený na ukázkové databázi Northwind a povolili jste přístup k informačnímu kanálu pro klienty, kteří mají oprávnění k webové aplikaci ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4b84c-149">You have successfully created a new data service that exposes an OData feed that is based on the Northwind sample database, and you have enabled access to the feed for clients that have permissions on the ASP.NET Web application.</span></span> <span data-ttu-id="4b84c-150">V dalším kroku spustíte datovou službu ze sady Visual Studio a získáte přístup k datovému kanálu OData odesláním požadavků HTTP GET přes webový prohlížeč:</span><span class="sxs-lookup"><span data-stu-id="4b84c-150">Next, you'll start the data service from Visual Studio and access the OData feed by submitting HTTP GET requests through a Web browser:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4b84c-151">Přístup ke službě z webového prohlížeče</span><span class="sxs-lookup"><span data-stu-id="4b84c-151">Access the service from a web browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="4b84c-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b84c-152">See also</span></span>

- <span data-ttu-id="4b84c-153">[ADO.NET model EDM (Entity Data Model) nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4b84c-153">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
