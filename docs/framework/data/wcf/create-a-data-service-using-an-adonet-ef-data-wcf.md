---
title: 'Postupy: Vytvoření datové služby pomocí zdroje dat Entity Framework ADO.NET (WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: 1d3c3628a32439d4847505e234b12b084b47ba3d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854119"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a><span data-ttu-id="94ca8-102">Postupy: Vytvoření datové služby pomocí zdroje dat Entity Framework ADO.NET (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="94ca8-102">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source (WCF Data Services)</span></span>

<span data-ttu-id="94ca8-103">WCF Data Services zpřístupňuje data entit jako datovou službu.</span><span class="sxs-lookup"><span data-stu-id="94ca8-103">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="94ca8-104">Tato data entity poskytuje rozhraní ADO. NETEntity, pokud je zdrojem dat relační databáze.</span><span class="sxs-lookup"><span data-stu-id="94ca8-104">This entity data is provided by the ADO.NETEntity Framework when the data source is a relational database.</span></span> <span data-ttu-id="94ca8-105">V tomto tématu se dozvíte, jak vytvořit datový model založený Entity Framework ve webové aplikaci Visual Studio, která je založena na stávající databázi a pomocí tohoto datového modelu vytvořit novou datovou službu.</span><span class="sxs-lookup"><span data-stu-id="94ca8-105">This topic shows you how to create an Entity Framework-based data model in a Visual Studio Web application that is based on an existing database and use this data model to create a new data service.</span></span>

<span data-ttu-id="94ca8-106">Entity Framework také poskytuje nástroj příkazového řádku, který může vygenerovat Entity Framework model mimo projekt sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="94ca8-106">The Entity Framework also provides a command line tool that can generate an Entity Framework model outside of a Visual Studio project.</span></span> <span data-ttu-id="94ca8-107">Další informace najdete v tématu [jak: K vygenerování modelu a mapování souborů](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)použijte EdmGen. exe.</span><span class="sxs-lookup"><span data-stu-id="94ca8-107">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>

## <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a><span data-ttu-id="94ca8-108">Přidání modelu Entity Framework, který je založen na existující databázi, do existující webové aplikace</span><span class="sxs-lookup"><span data-stu-id="94ca8-108">To add an Entity Framework model that is based on an existing database to an existing Web application</span></span>

1. <span data-ttu-id="94ca8-109">V nabídce **projekt** klikněte na příkaz **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="94ca8-109">On the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="94ca8-110">V podokně **šablony** klikněte na kategorii **dat** a pak vyberte **ADO.NET model EDM (Entity Data Model)** .</span><span class="sxs-lookup"><span data-stu-id="94ca8-110">In the **Templates** pane, click the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="94ca8-111">Zadejte název modelu a pak klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="94ca8-111">Enter the model name and then click **Add**.</span></span>

     <span data-ttu-id="94ca8-112">Zobrazí se první stránka průvodce model EDM (Entity Data Model).</span><span class="sxs-lookup"><span data-stu-id="94ca8-112">The first page of the Entity Data Model Wizard is displayed.</span></span>

4. <span data-ttu-id="94ca8-113">V dialogovém okně **Vybrat obsah modelu** vyberte možnost **Generovat z databáze**.</span><span class="sxs-lookup"><span data-stu-id="94ca8-113">In the **Choose Model Contents** dialog box, select **Generate from database**.</span></span> <span data-ttu-id="94ca8-114">Pak klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="94ca8-114">Then click **Next**.</span></span>

5. <span data-ttu-id="94ca8-115">Klikněte na tlačítko **nové připojení** .</span><span class="sxs-lookup"><span data-stu-id="94ca8-115">Click the **New Connection** button.</span></span>

6. <span data-ttu-id="94ca8-116">V dialogovém okně **Vlastnosti připojení** zadejte název serveru, vyberte metodu ověřování, zadejte název databáze a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="94ca8-116">In the **Connection Properties** dialog box, type your server name, select the authentication method, type the database name, and then click **OK**.</span></span>

     <span data-ttu-id="94ca8-117">Dialogové okno **zvolit datové připojení** je aktualizováno nastavením připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="94ca8-117">The **Choose Your Data Connection** dialog box is updated with your database connection settings.</span></span>

7. <span data-ttu-id="94ca8-118">Ujistěte se, že je zaškrtnuté políčko **Uložit nastavení připojení entity v App. config jako:** .</span><span class="sxs-lookup"><span data-stu-id="94ca8-118">Ensure that the **Save entity connection settings in App.Config as:** checkbox is checked.</span></span> <span data-ttu-id="94ca8-119">Pak klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="94ca8-119">Then click **Next**.</span></span>

8. <span data-ttu-id="94ca8-120">V dialogovém okně **Zvolte objekty databáze** vyberte všechny databázové objekty, které chcete zpřístupnit v datové službě.</span><span class="sxs-lookup"><span data-stu-id="94ca8-120">In the **Choose Your Database Objects** dialog box, select all of database objects that you plan to expose in the data service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="94ca8-121">Objekty zahrnuté v datovém modelu nejsou automaticky zpřístupněny datovou službou.</span><span class="sxs-lookup"><span data-stu-id="94ca8-121">Objects included in the data model are not automatically exposed by the data service.</span></span> <span data-ttu-id="94ca8-122">Musí být výslovně vystaveny samotným službám.</span><span class="sxs-lookup"><span data-stu-id="94ca8-122">They must be explicitly exposed by the service itself.</span></span> <span data-ttu-id="94ca8-123">Další informace najdete v tématu [konfigurace datové služby](configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="94ca8-123">For more information, see [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).</span></span>

9. <span data-ttu-id="94ca8-124">Kliknutím na **Dokončit** dokončete průvodce.</span><span class="sxs-lookup"><span data-stu-id="94ca8-124">Click **Finish** to complete the wizard.</span></span>

     <span data-ttu-id="94ca8-125">Tím se vytvoří výchozí datový model založený na konkrétní databázi.</span><span class="sxs-lookup"><span data-stu-id="94ca8-125">This creates a default data model based on the specific database.</span></span> <span data-ttu-id="94ca8-126">Entity Framework umožňuje přizpůsobit datový model.</span><span class="sxs-lookup"><span data-stu-id="94ca8-126">The Entity Framework enables to customize the data model.</span></span> <span data-ttu-id="94ca8-127">Další informace najdete v tématu [úlohy nástroje model EDM (Entity Data Model) Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="94ca8-127">For more information, see [Entity Data Model Tools Tasks](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100)).</span></span>

## <a name="to-create-the-data-service-by-using-the-new-data-model"></a><span data-ttu-id="94ca8-128">Vytvoření datové služby pomocí nového datového modelu</span><span class="sxs-lookup"><span data-stu-id="94ca8-128">To create the data service by using the new data model</span></span>

1. <span data-ttu-id="94ca8-129">V aplikaci Visual Studio otevřete soubor. edmx, který představuje datový model.</span><span class="sxs-lookup"><span data-stu-id="94ca8-129">In Visual Studio, open the .edmx file that represents the data model.</span></span>

2. <span data-ttu-id="94ca8-130">V **prohlížeči modelů**klikněte pravým tlačítkem na model, klikněte na **vlastnosti**a potom si poznamenejte název kontejneru entity.</span><span class="sxs-lookup"><span data-stu-id="94ca8-130">In the **Model Browser**, right-click the model, click **Properties**, and then note the name of the entity container.</span></span>

3. <span data-ttu-id="94ca8-131">V **Průzkumník řešení**klikněte pravým tlačítkem na název projektu ASP.NET a pak klikněte na **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="94ca8-131">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

4. <span data-ttu-id="94ca8-132">V dialogovém okně **Přidat novou položku** vyberte šablonu **Služba WCF Data Service** ve **webové** kategorii.</span><span class="sxs-lookup"><span data-stu-id="94ca8-132">In the **Add New Item** dialog box, select the **WCF Data Service** template in the **Web** category.</span></span>

   ![Šablona položky datové služby WCF v aplikaci Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="94ca8-134">Šablona **WCF Data Service** je k dispozici v aplikaci visual Studio 2015, ale ne v aplikaci visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="94ca8-134">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

5. <span data-ttu-id="94ca8-135">Zadejte název služby a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="94ca8-135">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="94ca8-136">Visual Studio vytvoří kód XML a soubory kódu pro novou službu.</span><span class="sxs-lookup"><span data-stu-id="94ca8-136">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="94ca8-137">Ve výchozím nastavení se otevře okno Editor kódu.</span><span class="sxs-lookup"><span data-stu-id="94ca8-137">By default, the code-editor window opens.</span></span>

6. <span data-ttu-id="94ca8-138">V kódu pro datovou službu nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy definující datovou službu typem, který dědí <xref:System.Data.Objects.ObjectContext> z třídy a který je kontejner entit datového modelu, který byl zaznamenán v kroku 2.</span><span class="sxs-lookup"><span data-stu-id="94ca8-138">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that inherits from the <xref:System.Data.Objects.ObjectContext> class and that is the entity container of the data model, which was noted in step 2.</span></span>

7. <span data-ttu-id="94ca8-139">V kódu pro datovou službu povolte autorizovaným klientům přístup k sadám entit, které datová služba zpřístupňuje.</span><span class="sxs-lookup"><span data-stu-id="94ca8-139">In the code for the data service, enable authorized clients to access the entity sets that the data service exposes.</span></span> <span data-ttu-id="94ca8-140">Další informace najdete v tématu [Vytvoření datové služby](creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="94ca8-140">For more information, see [Creating the Data Service](creating-the-data-service.md).</span></span>

8. <span data-ttu-id="94ca8-141">Chcete-li otestovat datovou službu Northwind. svc pomocí webového prohlížeče, postupujte podle pokynů v tématu [přístup ke službě z webového prohlížeče](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="94ca8-141">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="94ca8-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94ca8-142">See also</span></span>

- [<span data-ttu-id="94ca8-143">Definování datových služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="94ca8-143">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
- [<span data-ttu-id="94ca8-144">Zprostředkovatelé datových služeb</span><span class="sxs-lookup"><span data-stu-id="94ca8-144">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="94ca8-145">Postupy: Vytvoření datové služby pomocí zprostředkovatele reflexe</span><span class="sxs-lookup"><span data-stu-id="94ca8-145">How to: Create a Data Service Using the Reflection Provider</span></span>](create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="94ca8-146">Postupy: Vytvoření datové služby pomocí LINQ to SQL zdroje dat</span><span class="sxs-lookup"><span data-stu-id="94ca8-146">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](create-a-data-service-using-linq-to-sql-wcf.md)
