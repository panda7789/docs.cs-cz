---
title: "Postupy: vytvoření služby dat pomocí LINQ ke zdroji dat SQL (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a44498381bc33b6bd418003fbd28fd2fcfca17b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a><span data-ttu-id="50936-102">Postupy: vytvoření služby dat pomocí LINQ ke zdroji dat SQL (služby WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="50936-102">How to: Create a Data Service Using a LINQ to SQL Data Source (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="50936-103">zpřístupní entity data jako datové služby.</span><span class="sxs-lookup"><span data-stu-id="50936-103"> exposes entity data as a data service.</span></span> <span data-ttu-id="50936-104">Zprostředkovatel reflexe umožňuje definovat datového modelu, který je založena na všechny třídy, která zpřístupňuje členy, který vrací <xref:System.Linq.IQueryable%601> implementace.</span><span class="sxs-lookup"><span data-stu-id="50936-104">The reflection provider enables you to define a data model that is based on any class that exposes members that return an <xref:System.Linq.IQueryable%601> implementation.</span></span> <span data-ttu-id="50936-105">Abyste mohli provést aktualizace dat ve zdroji dat, musíte také implementovat tyto třídy <xref:System.Data.Services.IUpdatable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="50936-105">To be able to make updates to data in the data source, these classes must also implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="50936-106">Další informace najdete v tématu [zprostředkovatelé dat služby](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="50936-106">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span> <span data-ttu-id="50936-107">Toto téma ukazuje, jak vytvořit LINQ na SQL třídy, která přistupují k ukázková databáze Northwind pomocí reflexe poskytovatele, jakož i služba dat, která je založena na těchto třídách data vytvoření.</span><span class="sxs-lookup"><span data-stu-id="50936-107">This topic shows you how to create LINQ to SQL classes that access the Northwind sample database by using the reflection provider, as well as how to create the data service that is based on these data classes.</span></span>  
  
### <a name="to-add-linq-to-sql-classes-to-a-project"></a><span data-ttu-id="50936-108">Přidat do třídy SQL do projektu LINQ</span><span class="sxs-lookup"><span data-stu-id="50936-108">To add LINQ to SQL classes to a project</span></span>  
  
1.  <span data-ttu-id="50936-109">Z v rámci aplikace Visual Basic a C#, na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="50936-109">From within a Visual Basic or C# application, on the **Project** menu, click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="50936-110">Klikněte **třídy LINQ to SQL** šablony.</span><span class="sxs-lookup"><span data-stu-id="50936-110">Click the **LINQ to SQL Classes** template.</span></span>  
  
3.  <span data-ttu-id="50936-111">Změňte název **Northwind.dbml**.</span><span class="sxs-lookup"><span data-stu-id="50936-111">Change the name to **Northwind.dbml**.</span></span>  
  
4.  <span data-ttu-id="50936-112">Klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="50936-112">Click **Add**.</span></span>  
  
     <span data-ttu-id="50936-113">Soubor Northwind.dbml je přidán do projektu a otevře Návrhář relací objektů (Návrhář relací objektů).</span><span class="sxs-lookup"><span data-stu-id="50936-113">The Northwind.dbml file is added to the project and the Object Relational Designer (O/R Designer) opens.</span></span>  
  
5.  <span data-ttu-id="50936-114">V **Server**/**Průzkumník databáze**, v části Northwind, rozbalte položku **tabulky** a přetáhněte ji `Customers` tabulky do Návrhář relací objektů (relací objektů Návrhář).</span><span class="sxs-lookup"><span data-stu-id="50936-114">In **Server**/**Database Explorer**, under Northwind, expand **Tables** and drag the `Customers` table onto the Object Relational Designer (O/R Designer).</span></span>  
  
     <span data-ttu-id="50936-115">A `Customer` třídy entita se vytvoří a zobrazí se na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="50936-115">A `Customer` entity class is created and appears on the design surface.</span></span>  
  
6.  <span data-ttu-id="50936-116">Opakujte krok 6 pro `Orders`, `Order_Details`, a `Products` tabulky.</span><span class="sxs-lookup"><span data-stu-id="50936-116">Repeat step 6 for the `Orders`, `Order_Details`, and `Products` tables.</span></span>  
  
7.  <span data-ttu-id="50936-117">Klikněte pravým tlačítkem na nový soubor DBML, který představuje LINQ třídy SQL, klikněte na **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="50936-117">Right-click the new .dbml file that represents the LINQ to SQL classes and click **View Code**.</span></span>  
  
     <span data-ttu-id="50936-118">Tím se vytvoří nová stránka kódu s názvem Northwind.cs, který obsahuje třídu definice pro třídu, která dědí z <xref:System.Data.Linq.DataContext> třída, která v tomto případě je `NorthwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="50936-118">This creates a new code-behind page named Northwind.cs that contains a partial class definition for the class that inherits from the <xref:System.Data.Linq.DataContext> class, which in this case is `NorthwindDataContext`.</span></span>  
  
8.  <span data-ttu-id="50936-119">Obsah souboru Northwind.cs kódu nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="50936-119">Replace the contents of the Northwind.cs code file with the following code.</span></span> <span data-ttu-id="50936-120">Tento kód implementuje zprostředkovatele reflexe tím, že rozšíří <xref:System.Data.Linq.DataContext> a datových tříd, které jsou generované technologie LINQ to SQL:</span><span class="sxs-lookup"><span data-stu-id="50936-120">This code implements the reflection provider by extending the <xref:System.Data.Linq.DataContext> and data classes generated by LINQ to SQL:</span></span>  
  
     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.vb#linq2sqlprovider)]  
  
### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a><span data-ttu-id="50936-121">Vytvoření služby dat pomocí LINQ to SQL na základě datového modelu</span><span class="sxs-lookup"><span data-stu-id="50936-121">To create a data service by using a LINQ to SQL-based data model</span></span>  
  
1.  <span data-ttu-id="50936-122">V **Průzkumníku řešení**, klikněte pravým tlačítkem na název projektu ASP.NET a pak klikněte na tlačítko **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="50936-122">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="50936-123">V **přidat novou položku** dialogové okno, vyberte **služby WCF Data Service**.</span><span class="sxs-lookup"><span data-stu-id="50936-123">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>  
  
3.  <span data-ttu-id="50936-124">Zadejte název pro službu a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="50936-124">Supply a name for the service, and then click **OK**.</span></span>  
  
     <span data-ttu-id="50936-125">Visual Studio vytvoří soubory značek a kódu XML pro novou službu.</span><span class="sxs-lookup"><span data-stu-id="50936-125">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="50936-126">Ve výchozím nastavení otevře se okno editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="50936-126">By default, the code-editor window opens.</span></span>  
  
4.  <span data-ttu-id="50936-127">V kódu pro službu data, nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy, která definuje službu data s typem, který je kontejneru entit datového modelu, který v tomto případě je `NorthwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="50936-127">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindDataContext`.</span></span>  
  
5.  <span data-ttu-id="50936-128">V kódu pro službu data, nahraďte zástupný symbol kód v `InitializeService` funkce následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="50936-128">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.svc.vb#enableaccess)]  
  
     <span data-ttu-id="50936-129">To umožňuje autorizovaným klientům přístup k prostředkům pro tři sady zadané entity.</span><span class="sxs-lookup"><span data-stu-id="50936-129">This enables authorized clients to access resources for the three specified entity sets.</span></span>  
  
6.  <span data-ttu-id="50936-130">Chcete-li otestovat službu Northwind.svc data pomocí webového prohlížeče, postupujte podle pokynů v tématu [přístupu ke službě z webového prohlížeče](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="50936-130">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50936-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="50936-131">See Also</span></span>  
 [<span data-ttu-id="50936-132">Postupy: vytvoření služby Data pomocí zdroje dat ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="50936-132">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)  
 [<span data-ttu-id="50936-133">Postupy: vytvoření služby Data pomocí poskytovatele reflexe</span><span class="sxs-lookup"><span data-stu-id="50936-133">How to: Create a Data Service Using the Reflection Provider</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
 [<span data-ttu-id="50936-134">Zprostředkovatelé dat služby</span><span class="sxs-lookup"><span data-stu-id="50936-134">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
