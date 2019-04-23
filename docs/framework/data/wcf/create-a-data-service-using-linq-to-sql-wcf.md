---
title: 'Postupy: Vytvoření datové služby pomocí LINQ ke zdroji dat SQL (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: b33eb8f470fc8ce3851c7843de992b39e86ce018
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59518217"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a><span data-ttu-id="d42cc-102">Postupy: Vytvoření datové služby pomocí LINQ ke zdroji dat SQL (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="d42cc-102">How to: Create a Data Service Using a LINQ to SQL Data Source (WCF Data Services)</span></span>

<span data-ttu-id="d42cc-103">Služby WCF Data Services zpřístupňuje entity data jako datové služby.</span><span class="sxs-lookup"><span data-stu-id="d42cc-103">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="d42cc-104">Zprostředkovatel reflexe umožňuje definovat datový model, který je založen na jakoukoli třídu, která zveřejňuje členy který vrací <xref:System.Linq.IQueryable%601> implementace.</span><span class="sxs-lookup"><span data-stu-id="d42cc-104">The reflection provider enables you to define a data model that is based on any class that exposes members that return an <xref:System.Linq.IQueryable%601> implementation.</span></span> <span data-ttu-id="d42cc-105">Aby bylo možné provést aktualizace dat ve zdroji dat, musíte také implementovat tyto třídy <xref:System.Data.Services.IUpdatable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d42cc-105">To be able to make updates to data in the data source, these classes must also implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="d42cc-106">Další informace najdete v tématu [zprostředkovatelé dat služby](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d42cc-106">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span> <span data-ttu-id="d42cc-107">Toto téma ukazuje, jak vytvořit LINQ na třídy SQL, které přístup k ukázkové databázi Northwind pomocí zprostředkovatel reflexe, jakož i jak vytvořit datovou službu, která je založena na těchto datových tříd.</span><span class="sxs-lookup"><span data-stu-id="d42cc-107">This topic shows you how to create LINQ to SQL classes that access the Northwind sample database by using the reflection provider, as well as how to create the data service that is based on these data classes.</span></span>

## <a name="to-add-linq-to-sql-classes-to-a-project"></a><span data-ttu-id="d42cc-108">Chcete-li přidat LINQ na třídy SQL do projektu</span><span class="sxs-lookup"><span data-stu-id="d42cc-108">To add LINQ to SQL classes to a project</span></span>

1. <span data-ttu-id="d42cc-109">Z v rámci aplikace Visual Basic nebo C# na **projektu** nabídky, klikněte na tlačítko **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="d42cc-109">From within a Visual Basic or C# application, on the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="d42cc-110">Klikněte na tlačítko **třídy LINQ to SQL** šablony.</span><span class="sxs-lookup"><span data-stu-id="d42cc-110">Click the **LINQ to SQL Classes** template.</span></span>

3. <span data-ttu-id="d42cc-111">Změňte název na **Northwind.dbml**.</span><span class="sxs-lookup"><span data-stu-id="d42cc-111">Change the name to **Northwind.dbml**.</span></span>

4. <span data-ttu-id="d42cc-112">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="d42cc-112">Click **Add**.</span></span>

     <span data-ttu-id="d42cc-113">Do projektu se přidá soubor Northwind.dbml a otevře se Návrhář relací objektů (O/R Designer).</span><span class="sxs-lookup"><span data-stu-id="d42cc-113">The Northwind.dbml file is added to the project and the Object Relational Designer (O/R Designer) opens.</span></span>

5. <span data-ttu-id="d42cc-114">V **Server**/**Průzkumník databáze**, v části Northwind, rozbalte položku **tabulky** a přetáhněte ji `Customers` tabulky do Návrháře relací objektů (O/R Návrhář).</span><span class="sxs-lookup"><span data-stu-id="d42cc-114">In **Server**/**Database Explorer**, under Northwind, expand **Tables** and drag the `Customers` table onto the Object Relational Designer (O/R Designer).</span></span>

     <span data-ttu-id="d42cc-115">A `Customer` třídy entita se vytvoří a zobrazí na návrhové ploše.</span><span class="sxs-lookup"><span data-stu-id="d42cc-115">A `Customer` entity class is created and appears on the design surface.</span></span>

6. <span data-ttu-id="d42cc-116">Opakujte krok 6 pro `Orders`, `Order_Details`, a `Products` tabulky.</span><span class="sxs-lookup"><span data-stu-id="d42cc-116">Repeat step 6 for the `Orders`, `Order_Details`, and `Products` tables.</span></span>

7. <span data-ttu-id="d42cc-117">Klikněte pravým tlačítkem na nový soubor .dbml, který představuje LINQ na třídy SQL a klikněte na **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="d42cc-117">Right-click the new .dbml file that represents the LINQ to SQL classes and click **View Code**.</span></span>

     <span data-ttu-id="d42cc-118">Tím se vytvoří nová stránka použití modelu code-behind Northwind.cs, který obsahuje definici částečnou třídu, která dědí z třídy s názvem <xref:System.Data.Linq.DataContext> třídu, která v tomto případě je `NorthwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="d42cc-118">This creates a new code-behind page named Northwind.cs that contains a partial class definition for the class that inherits from the <xref:System.Data.Linq.DataContext> class, which in this case is `NorthwindDataContext`.</span></span>

8. <span data-ttu-id="d42cc-119">Nahraďte obsah souboru Northwind.cs kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="d42cc-119">Replace the contents of the Northwind.cs code file with the following code.</span></span> <span data-ttu-id="d42cc-120">Tento kód implementuje zprostředkovatel reflexe tím, že rozšíří <xref:System.Data.Linq.DataContext> a datových tříd, které jsou generovány pomocí LINQ to SQL:</span><span class="sxs-lookup"><span data-stu-id="d42cc-120">This code implements the reflection provider by extending the <xref:System.Data.Linq.DataContext> and data classes generated by LINQ to SQL:</span></span>

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a><span data-ttu-id="d42cc-121">Vytvoření datové služby pomocí LINQ to SQL na základě datového modelu</span><span class="sxs-lookup"><span data-stu-id="d42cc-121">To create a data service by using a LINQ to SQL-based data model</span></span>

1. <span data-ttu-id="d42cc-122">V **Průzkumníka řešení**, klikněte pravým tlačítkem na název projektu ASP.NET a potom klikněte na **přidat** > **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="d42cc-122">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="d42cc-123">V **přidat novou položku** dialogové okno, vyberte **službu WCF Data Service** šablonu z **webové** kategorie.</span><span class="sxs-lookup"><span data-stu-id="d42cc-123">In the **Add New Item** dialog box, select the **WCF Data Service** template from the **Web** category.</span></span>

   ![Služby WCF Data Service šablony položky v sadě Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="d42cc-125">**Službu WCF Data Service** šablona je k dispozici v sadě Visual Studio 2015, ale ne v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="d42cc-125">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

3. <span data-ttu-id="d42cc-126">Zadejte název pro službu a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="d42cc-126">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="d42cc-127">Visual Studio vytvoří soubory značek a kódu XML pro novou službu.</span><span class="sxs-lookup"><span data-stu-id="d42cc-127">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="d42cc-128">Ve výchozím nastavení otevře se okno editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="d42cc-128">By default, the code-editor window opens.</span></span>

4. <span data-ttu-id="d42cc-129">V kódu pro datovou službu, nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy, která definuje datové služby s typem, který je kontejner entit datového modelu, který v tomto případě je `NorthwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="d42cc-129">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindDataContext`.</span></span>

5. <span data-ttu-id="d42cc-130">V kódu pro datovou službu, nahraďte zástupný symbol kód v `InitializeService` funkce následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="d42cc-130">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.svc.vb#enableaccess)]

     <span data-ttu-id="d42cc-131">To umožňuje autorizovaným klientům přístup k prostředkům tři určené sady entit.</span><span class="sxs-lookup"><span data-stu-id="d42cc-131">This enables authorized clients to access resources for the three specified entity sets.</span></span>

6. <span data-ttu-id="d42cc-132">Pokud chcete testovat službu Northwind.svc dat pomocí webového prohlížeče, postupujte podle pokynů v tématu [přístupu ke službě z webového prohlížeče](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="d42cc-132">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d42cc-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d42cc-133">See also</span></span>

- [<span data-ttu-id="d42cc-134">Postupy: Vytvoření datové služby pomocí zdroje dat rozhraní ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="d42cc-134">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [<span data-ttu-id="d42cc-135">Postupy: Vytvoření datové služby pomocí zprostředkovatel reflexe</span><span class="sxs-lookup"><span data-stu-id="d42cc-135">How to: Create a Data Service Using the Reflection Provider</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="d42cc-136">Zprostředkovatelé datových služeb</span><span class="sxs-lookup"><span data-stu-id="d42cc-136">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)