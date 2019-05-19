---
title: 'Postupy: Vytvoření datové služby pomocí zdroji dat ADO.NET Entity Framework (WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: 78286cde925a4583a3610ce100d23e16adcefe49
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878078"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a><span data-ttu-id="818bd-102">Postupy: Vytvoření datové služby pomocí zdroji dat ADO.NET Entity Framework (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="818bd-102">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source (WCF Data Services)</span></span>

<span data-ttu-id="818bd-103">Služby WCF Data Services zpřístupňuje entity data jako datové služby.</span><span class="sxs-lookup"><span data-stu-id="818bd-103">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="818bd-104">Poskytuje tato data entity ADO.NET[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Pokud zdroj dat je relační databáze.</span><span class="sxs-lookup"><span data-stu-id="818bd-104">This entity data is provided by the ADO.NET[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] when the data source is a relational database.</span></span> <span data-ttu-id="818bd-105">V tomto tématu se dozvíte, jak vytvořit [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]– na základě datového modelu v aplikaci Visual Studio Web, který je založený na existující databáze a tento model dat slouží k vytvoření nové datové služby.</span><span class="sxs-lookup"><span data-stu-id="818bd-105">This topic shows you how to create an [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]-based data model in a Visual Studio Web application that is based on an existing database and use this data model to create a new data service.</span></span>

<span data-ttu-id="818bd-106">[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Poskytuje nástroj příkazového řádku, který můžete vygenerovat také [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] model mimo projekt sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="818bd-106">The [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] also provides a command line tool that can generate an [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] model outside of a Visual Studio project.</span></span> <span data-ttu-id="818bd-107">Další informace najdete v tématu [jak: Použití EdmGen.exe pro generování modelu a souborů mapování](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="818bd-107">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>

## <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a><span data-ttu-id="818bd-108">Chcete-li přidat model Entity Framework, která je založena na existující databázi do existující webové aplikace</span><span class="sxs-lookup"><span data-stu-id="818bd-108">To add an Entity Framework model that is based on an existing database to an existing Web application</span></span>

1. <span data-ttu-id="818bd-109">Na **projektu** nabídky, klikněte na tlačítko **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="818bd-109">On the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="818bd-110">V **šablony** podokně klikněte na tlačítko **Data** kategorie a pak vyberte **datový Model Entity ADO.NET**.</span><span class="sxs-lookup"><span data-stu-id="818bd-110">In the **Templates** pane, click the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="818bd-111">Zadejte název modelu a poté klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="818bd-111">Enter the model name and then click **Add**.</span></span>

     <span data-ttu-id="818bd-112">První stránka [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] průvodce se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="818bd-112">The first page of the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Wizard is displayed.</span></span>

4. <span data-ttu-id="818bd-113">V **výběr obsahu modelu** dialogu **Generovat z databáze**.</span><span class="sxs-lookup"><span data-stu-id="818bd-113">In the **Choose Model Contents** dialog box, select **Generate from database**.</span></span> <span data-ttu-id="818bd-114">Pak klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="818bd-114">Then click **Next**.</span></span>

5. <span data-ttu-id="818bd-115">Klikněte na tlačítko **nové připojení** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="818bd-115">Click the **New Connection** button.</span></span>

6. <span data-ttu-id="818bd-116">V **vlastnosti připojení** dialogové okno, zadejte název vašeho serveru, vyberte metodu ověřování, zadejte název databáze a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="818bd-116">In the **Connection Properties** dialog box, type your server name, select the authentication method, type the database name, and then click **OK**.</span></span>

     <span data-ttu-id="818bd-117">**Vyberte datové připojení** dialogové okno se aktualizuje se nastavení připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="818bd-117">The **Choose Your Data Connection** dialog box is updated with your database connection settings.</span></span>

7. <span data-ttu-id="818bd-118">Ujistěte se, že **uložit nastavení připojení v souboru App.Config jako entity:** je zaškrtnuté políčko.</span><span class="sxs-lookup"><span data-stu-id="818bd-118">Ensure that the **Save entity connection settings in App.Config as:** checkbox is checked.</span></span> <span data-ttu-id="818bd-119">Pak klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="818bd-119">Then click **Next**.</span></span>

8. <span data-ttu-id="818bd-120">V **zvolte vaše databázové objekty** dialogové okno, vyberte všechny databáze objekty chcete vystavit v datové služby.</span><span class="sxs-lookup"><span data-stu-id="818bd-120">In the **Choose Your Database Objects** dialog box, select all of database objects that you plan to expose in the data service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="818bd-121">Objektů obsažených v datovém modelu nejsou datovou službou vystavena automaticky.</span><span class="sxs-lookup"><span data-stu-id="818bd-121">Objects included in the data model are not automatically exposed by the data service.</span></span> <span data-ttu-id="818bd-122">Musí být explicitně vystavené samotné služby.</span><span class="sxs-lookup"><span data-stu-id="818bd-122">They must be explicitly exposed by the service itself.</span></span> <span data-ttu-id="818bd-123">Další informace najdete v tématu [konfigurace datové služby](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="818bd-123">For more information, see [Configuring the Data Service](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span></span>

9. <span data-ttu-id="818bd-124">Klikněte na tlačítko **Dokončit** kroky průvodce dokončete.</span><span class="sxs-lookup"><span data-stu-id="818bd-124">Click **Finish** to complete the wizard.</span></span>

     <span data-ttu-id="818bd-125">Tím se vytvoří výchozí datový model založený na konkrétní databáze.</span><span class="sxs-lookup"><span data-stu-id="818bd-125">This creates a default data model based on the specific database.</span></span> <span data-ttu-id="818bd-126">[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Umožňuje Přizpůsobte si datový model.</span><span class="sxs-lookup"><span data-stu-id="818bd-126">The [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] enables to customize the data model.</span></span> <span data-ttu-id="818bd-127">Další informace najdete v tématu [úlohy nástroje modelu Entity Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="818bd-127">For more information, see [Entity Data Model Tools Tasks](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100)).</span></span>

## <a name="to-create-the-data-service-by-using-the-new-data-model"></a><span data-ttu-id="818bd-128">Vytvoření datové služby s použitím nového datového modelu</span><span class="sxs-lookup"><span data-stu-id="818bd-128">To create the data service by using the new data model</span></span>

1. <span data-ttu-id="818bd-129">V sadě Visual Studio otevřete soubor EDMX, který představuje datový model.</span><span class="sxs-lookup"><span data-stu-id="818bd-129">In Visual Studio, open the .edmx file that represents the data model.</span></span>

2. <span data-ttu-id="818bd-130">V **prohlížeč modelu**, klikněte pravým tlačítkem na model, klikněte na tlačítko **vlastnosti**a potom si poznamenejte název kontejneru entity.</span><span class="sxs-lookup"><span data-stu-id="818bd-130">In the **Model Browser**, right-click the model, click **Properties**, and then note the name of the entity container.</span></span>

3. <span data-ttu-id="818bd-131">V **Průzkumníka řešení**, klikněte pravým tlačítkem na název projektu ASP.NET a potom klikněte na **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="818bd-131">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

4. <span data-ttu-id="818bd-132">V **přidat novou položku** dialogové okno, vyberte **službu WCF Data Service** šablony **webové** kategorie.</span><span class="sxs-lookup"><span data-stu-id="818bd-132">In the **Add New Item** dialog box, select the **WCF Data Service** template in the **Web** category.</span></span>

   ![Služby WCF Data Service šablony položky v sadě Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="818bd-134">**Službu WCF Data Service** šablona je k dispozici v sadě Visual Studio 2015, ale ne v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="818bd-134">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

5. <span data-ttu-id="818bd-135">Zadejte název pro službu a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="818bd-135">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="818bd-136">Visual Studio vytvoří soubory značek a kódu XML pro novou službu.</span><span class="sxs-lookup"><span data-stu-id="818bd-136">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="818bd-137">Ve výchozím nastavení otevře se okno editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="818bd-137">By default, the code-editor window opens.</span></span>

6. <span data-ttu-id="818bd-138">V kódu pro datovou službu, nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy, která definuje datové služby s typem, který dědí z <xref:System.Data.Objects.ObjectContext> třídy, který je kontejner entit datového modelu, který byl jste si poznamenali v kroku 2.</span><span class="sxs-lookup"><span data-stu-id="818bd-138">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that inherits from the <xref:System.Data.Objects.ObjectContext> class and that is the entity container of the data model, which was noted in step 2.</span></span>

7. <span data-ttu-id="818bd-139">V kódu pro datovou službu povolte autorizovaným klientům přístup k sady entit, které služba data zpřístupňuje.</span><span class="sxs-lookup"><span data-stu-id="818bd-139">In the code for the data service, enable authorized clients to access the entity sets that the data service exposes.</span></span> <span data-ttu-id="818bd-140">Další informace najdete v tématu [vytvoření datové služby](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="818bd-140">For more information, see [Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>

8. <span data-ttu-id="818bd-141">Pokud chcete testovat službu Northwind.svc dat pomocí webového prohlížeče, postupujte podle pokynů v tématu [přístupu ke službě z webového prohlížeče](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="818bd-141">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="818bd-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="818bd-142">See also</span></span>

- [<span data-ttu-id="818bd-143">Definování datových služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="818bd-143">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [<span data-ttu-id="818bd-144">Zprostředkovatelé datových služeb</span><span class="sxs-lookup"><span data-stu-id="818bd-144">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="818bd-145">Postupy: Vytvoření datové služby pomocí zprostředkovatel reflexe</span><span class="sxs-lookup"><span data-stu-id="818bd-145">How to: Create a Data Service Using the Reflection Provider</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="818bd-146">Postupy: Vytvoření datové služby pomocí LINQ ke zdroji dat SQL</span><span class="sxs-lookup"><span data-stu-id="818bd-146">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
