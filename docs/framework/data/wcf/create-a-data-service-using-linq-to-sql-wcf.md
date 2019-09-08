---
title: 'Postupy: Vytvoření datové služby pomocí LINQ to SQL zdroje dat (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: 7a1075b680ec3310e1bd8d712579872333c6ebed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791049"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a><span data-ttu-id="64f9a-102">Postupy: Vytvoření datové služby pomocí LINQ to SQL zdroje dat (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="64f9a-102">How to: Create a Data Service Using a LINQ to SQL Data Source (WCF Data Services)</span></span>

<span data-ttu-id="64f9a-103">WCF Data Services zpřístupňuje data entit jako datovou službu.</span><span class="sxs-lookup"><span data-stu-id="64f9a-103">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="64f9a-104">Zprostředkovatel reflexe umožňuje definovat datový model, který je založen na jakékoli třídě, která zpřístupňuje členy, které <xref:System.Linq.IQueryable%601> vracejí implementaci.</span><span class="sxs-lookup"><span data-stu-id="64f9a-104">The reflection provider enables you to define a data model that is based on any class that exposes members that return an <xref:System.Linq.IQueryable%601> implementation.</span></span> <span data-ttu-id="64f9a-105">Aby bylo možné provádět aktualizace dat ve zdroji dat, musí tyto třídy implementovat <xref:System.Data.Services.IUpdatable> také rozhraní.</span><span class="sxs-lookup"><span data-stu-id="64f9a-105">To be able to make updates to data in the data source, these classes must also implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="64f9a-106">Další informace najdete v tématu [poskytovatelé Data Services](data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="64f9a-106">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span> <span data-ttu-id="64f9a-107">V tomto tématu se dozvíte, jak vytvořit LINQ to SQL třídy, které přistupují k ukázkové databázi Northwind pomocí poskytovatele reflexe a jak vytvořit datovou službu založenou na těchto třídách dat.</span><span class="sxs-lookup"><span data-stu-id="64f9a-107">This topic shows you how to create LINQ to SQL classes that access the Northwind sample database by using the reflection provider, as well as how to create the data service that is based on these data classes.</span></span>

## <a name="to-add-linq-to-sql-classes-to-a-project"></a><span data-ttu-id="64f9a-108">Přidání tříd LINQ to SQL do projektu</span><span class="sxs-lookup"><span data-stu-id="64f9a-108">To add LINQ to SQL classes to a project</span></span>

1. <span data-ttu-id="64f9a-109">V rámci Visual Basic nebo C# aplikace klikněte v nabídce **projekt** na příkaz **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="64f9a-109">From within a Visual Basic or C# application, on the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="64f9a-110">Klikněte na šablonu **třídy LINQ to SQL** .</span><span class="sxs-lookup"><span data-stu-id="64f9a-110">Click the **LINQ to SQL Classes** template.</span></span>

3. <span data-ttu-id="64f9a-111">Změňte název na **Northwind. dbml**.</span><span class="sxs-lookup"><span data-stu-id="64f9a-111">Change the name to **Northwind.dbml**.</span></span>

4. <span data-ttu-id="64f9a-112">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="64f9a-112">Click **Add**.</span></span>

     <span data-ttu-id="64f9a-113">Soubor Northwind. dbml se přidá do projektu a otevře se Návrhář relací objektů (Návrhář O/R).</span><span class="sxs-lookup"><span data-stu-id="64f9a-113">The Northwind.dbml file is added to the project and the Object Relational Designer (O/R Designer) opens.</span></span>

5. <span data-ttu-id="64f9a-114">V Průzkumníku **serveru**/**databáze**v části Northwind rozbalte **tabulky** a přetáhněte `Customers` tabulku na Návrhář relací objektů (Návrhář O/R).</span><span class="sxs-lookup"><span data-stu-id="64f9a-114">In **Server**/**Database Explorer**, under Northwind, expand **Tables** and drag the `Customers` table onto the Object Relational Designer (O/R Designer).</span></span>

     <span data-ttu-id="64f9a-115">Vytvoří se Třída entity, která se zobrazí na návrhové ploše. `Customer`</span><span class="sxs-lookup"><span data-stu-id="64f9a-115">A `Customer` entity class is created and appears on the design surface.</span></span>

6. <span data-ttu-id="64f9a-116">Opakujte krok 6 pro `Orders`tabulky, `Order_Details`a. `Products`</span><span class="sxs-lookup"><span data-stu-id="64f9a-116">Repeat step 6 for the `Orders`, `Order_Details`, and `Products` tables.</span></span>

7. <span data-ttu-id="64f9a-117">Pravým tlačítkem myši klikněte na nový soubor. dbml, který představuje třídy LINQ to SQL a klikněte na **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="64f9a-117">Right-click the new .dbml file that represents the LINQ to SQL classes and click **View Code**.</span></span>

     <span data-ttu-id="64f9a-118">Tím se vytvoří nová stránka s kódem na pozadí s názvem Northwind.cs, která obsahuje definici částečné třídy pro třídu, která dědí <xref:System.Data.Linq.DataContext> z třídy, která je `NorthwindDataContext`v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="64f9a-118">This creates a new code-behind page named Northwind.cs that contains a partial class definition for the class that inherits from the <xref:System.Data.Linq.DataContext> class, which in this case is `NorthwindDataContext`.</span></span>

8. <span data-ttu-id="64f9a-119">Obsah souboru kódu Northwind.cs nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="64f9a-119">Replace the contents of the Northwind.cs code file with the following code.</span></span> <span data-ttu-id="64f9a-120">Tento kód implementuje poskytovatele reflexe rozšířením <xref:System.Data.Linq.DataContext> tříd a datových tříd vygenerovaných LINQ to SQL:</span><span class="sxs-lookup"><span data-stu-id="64f9a-120">This code implements the reflection provider by extending the <xref:System.Data.Linq.DataContext> and data classes generated by LINQ to SQL:</span></span>

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a><span data-ttu-id="64f9a-121">Vytvoření datové služby pomocí datového modelu založeného na LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="64f9a-121">To create a data service by using a LINQ to SQL-based data model</span></span>

1. <span data-ttu-id="64f9a-122">V **Průzkumník řešení**klikněte pravým tlačítkem na název projektu ASP.NET a pak klikněte na **Přidat** > **novou položku**.</span><span class="sxs-lookup"><span data-stu-id="64f9a-122">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="64f9a-123">V dialogovém okně **Přidat novou položku** vyberte šablonu **WCF Data Service** z kategorie **Web** .</span><span class="sxs-lookup"><span data-stu-id="64f9a-123">In the **Add New Item** dialog box, select the **WCF Data Service** template from the **Web** category.</span></span>

   ![Šablona položky datové služby WCF v aplikaci Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="64f9a-125">Šablona **WCF Data Service** je k dispozici v aplikaci visual Studio 2015, ale ne v aplikaci visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="64f9a-125">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

3. <span data-ttu-id="64f9a-126">Zadejte název služby a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="64f9a-126">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="64f9a-127">Visual Studio vytvoří kód XML a soubory kódu pro novou službu.</span><span class="sxs-lookup"><span data-stu-id="64f9a-127">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="64f9a-128">Ve výchozím nastavení se otevře okno Editor kódu.</span><span class="sxs-lookup"><span data-stu-id="64f9a-128">By default, the code-editor window opens.</span></span>

4. <span data-ttu-id="64f9a-129">V kódu pro datovou službu nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy definující datovou službu typem, který je kontejnerem entit datového modelu, který je v tomto `NorthwindDataContext`případě.</span><span class="sxs-lookup"><span data-stu-id="64f9a-129">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindDataContext`.</span></span>

5. <span data-ttu-id="64f9a-130">V kódu pro datovou službu nahraďte zástupný kód ve `InitializeService` funkci následujícím textem:</span><span class="sxs-lookup"><span data-stu-id="64f9a-130">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.svc.vb#enableaccess)]

     <span data-ttu-id="64f9a-131">To umožňuje autorizovaným klientům získat přístup k prostředkům pro tři zadané sady entit.</span><span class="sxs-lookup"><span data-stu-id="64f9a-131">This enables authorized clients to access resources for the three specified entity sets.</span></span>

6. <span data-ttu-id="64f9a-132">Chcete-li otestovat datovou službu Northwind. svc pomocí webového prohlížeče, postupujte podle pokynů v tématu [přístup ke službě z webového prohlížeče](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="64f9a-132">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="64f9a-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64f9a-133">See also</span></span>

- [<span data-ttu-id="64f9a-134">Postupy: Vytvoření datové služby pomocí zdroje dat Entity Framework ADO.NET</span><span class="sxs-lookup"><span data-stu-id="64f9a-134">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [<span data-ttu-id="64f9a-135">Postupy: Vytvoření datové služby pomocí zprostředkovatele reflexe</span><span class="sxs-lookup"><span data-stu-id="64f9a-135">How to: Create a Data Service Using the Reflection Provider</span></span>](create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="64f9a-136">Zprostředkovatelé datových služeb</span><span class="sxs-lookup"><span data-stu-id="64f9a-136">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
