---
title: "Vytvoření aplikace klienta rozhraní .NET Framework (rychlý start WCF Data Services)"
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
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 25a6666127d16a8245093bdf11ae7d0e76fc8365
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a><span data-ttu-id="336c8-102">Vytvoření aplikace klienta rozhraní .NET Framework (rychlý start WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="336c8-102">Creating the .NET Framework Client Application (WCF Data Services Quickstart)</span></span>
<span data-ttu-id="336c8-103">Toto je poslední úlohy [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] rychlý start.</span><span class="sxs-lookup"><span data-stu-id="336c8-103">This is the final task of the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] quickstart.</span></span> <span data-ttu-id="336c8-104">V této úloze bude konzolovou aplikaci do řešení přidat, přidejte odkaz na [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] kanálu na tuto novou klientskou aplikaci a přístup [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu z klientské aplikace pomocí generovaného klienta datových služba tříd a klienta knihovny.</span><span class="sxs-lookup"><span data-stu-id="336c8-104">In this task, you will add a console application to the solution, add a reference to the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed into this new client application, and access the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed from the client application by using the generated client data service classes and client libraries.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="336c8-105">Aplikace založené na rozhraní .NET Framework klienta není potřeba přístup k datovému kanálu.</span><span class="sxs-lookup"><span data-stu-id="336c8-105">A .NET Framework-based client application is not required to access a data feed.</span></span> <span data-ttu-id="336c8-106">Služba data budou mít přístup všechny součásti aplikace, který využívá [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="336c8-106">The data service can be accessed by any application component that consumes an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.</span></span> <span data-ttu-id="336c8-107">Další informace najdete v tématu [pomocí datové služby v aplikaci klienta](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="336c8-107">For more information, see [Using a Data Service in a Client Application](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).</span></span>  
  
### <a name="to-create-the-client-application-by-using-visual-studio"></a><span data-ttu-id="336c8-108">Chcete-li vytvořit klientskou aplikaci pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="336c8-108">To create the client application by using Visual Studio</span></span>  
  
1.  <span data-ttu-id="336c8-109">V **Průzkumníku řešení**, klikněte pravým tlačítkem na řešení, klikněte na **přidat**a potom klikněte na **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="336c8-109">In **Solution Explorer**, right-click the solution, click **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="336c8-110">V **typy projektů**, klikněte na tlačítko **Windows**a potom vyberte **aplikaci WPF** v **šablony** podokně.</span><span class="sxs-lookup"><span data-stu-id="336c8-110">In **Project types**, click **Windows**, and then select **WPF Application** in the **Templates** pane.</span></span>  
  
3.  <span data-ttu-id="336c8-111">Zadejte `NorthwindClient` název projektu a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="336c8-111">Enter `NorthwindClient` for the project name, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="336c8-112">Otevřete soubor MainWindow.xaml a nahraďte kód XAML následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="336c8-112">Open the file MainWindow.xaml and replace the XAML code with the following code:</span></span>  
  
     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml#window1xaml)]  
  
### <a name="to-add-a-data-service-reference-to-the-project"></a><span data-ttu-id="336c8-113">Chcete-li přidat odkaz na službu do projektu</span><span class="sxs-lookup"><span data-stu-id="336c8-113">To add a data service reference to the project</span></span>  
  
1.  <span data-ttu-id="336c8-114">Klikněte pravým tlačítkem na projekt NorthwindClient, klikněte na tlačítko **přidat odkaz na službu**a potom klikněte na **Discover**.</span><span class="sxs-lookup"><span data-stu-id="336c8-114">Right-click the NorthwindClient project, click **Add Service Reference**, and then click **Discover**.</span></span>  
  
     <span data-ttu-id="336c8-115">Zobrazí se služba Northwind dat, který jste vytvořili v první úloze.</span><span class="sxs-lookup"><span data-stu-id="336c8-115">This displays the Northwind data service that you created in the first task.</span></span>  
  
2.  <span data-ttu-id="336c8-116">V **Namespace** textového pole, typ `Northwind`a potom klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="336c8-116">In the **Namespace** text box, type `Northwind`, and then click **OK**.</span></span>  
  
     <span data-ttu-id="336c8-117">To přidá nový soubor kódu do projektu, který obsahuje datové třídy, které se používají pro přístup a pracovat s prostředky služby data jako objekty.</span><span class="sxs-lookup"><span data-stu-id="336c8-117">This adds a new code file to the project, which contains the data classes that are used to access and interact with data service resources as objects.</span></span> <span data-ttu-id="336c8-118">Datových tříd, které jsou vytvořené v oboru názvů `NorthwindClient.Northwind`.</span><span class="sxs-lookup"><span data-stu-id="336c8-118">The data classes are created in the namespace `NorthwindClient.Northwind`.</span></span>  
  
### <a name="to-access-data-service-data-in-the-wpf-application"></a><span data-ttu-id="336c8-119">Pro přístup k datům služby dat v aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="336c8-119">To access data service data in the WPF application</span></span>  
  
1.  <span data-ttu-id="336c8-120">V **Průzkumníku řešení** pod **NorthwindClient**, klikněte pravým tlačítkem na projekt a klikněte na **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="336c8-120">In **Solution Explorer** under **NorthwindClient**, right-click the project and click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="336c8-121">V dialogovém okně Přidat odkaz klepněte **.NET** vyberte knihovně System.Data.Services.Client.dll sestavení a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="336c8-121">In the Add Reference dialog box, click the **.NET** tab, select the System.Data.Services.Client.dll assembly, and then click **OK**.</span></span> <span data-ttu-id="336c8-122">V **Průzkumníku řešení** pod **NorthwindClient**, otevřete stránku kód pro soubor MainWindow.xaml a přidejte následující `using` – příkaz (`Imports` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="336c8-122">In **Solution Explorer** under **NorthwindClient**, open the code page for the MainWindow.xaml file, and add the following `using` statement (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#using)]
     [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#using)]  
  
3.  <span data-ttu-id="336c8-123">Vložte následující kód, který se dotazuje služby dat a sváže výsledek, který má <xref:System.Data.Services.Client.DataServiceCollection%601> do `MainWindow` třídy:</span><span class="sxs-lookup"><span data-stu-id="336c8-123">Insert the following code that queries that data service and binds the result to a <xref:System.Data.Services.Client.DataServiceCollection%601> into the `MainWindow` class:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="336c8-124">Je třeba nahradit název hostitele `localhost:12345` se serverem a port, který je hostitelem vaší instance služby data Northwind.</span><span class="sxs-lookup"><span data-stu-id="336c8-124">You must replace the host name `localhost:12345` with the server and port that is hosting your instance of the Northwind data service.</span></span>  
  
     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#querycode)]  
  
4.  <span data-ttu-id="336c8-125">Vložte následující kód, který uloží změny do `MainWindow` třídy:</span><span class="sxs-lookup"><span data-stu-id="336c8-125">Insert the following code that saves changes into the `MainWindow` class:</span></span>  
  
     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#savechanges)]  
  
### <a name="to-build-and-run-the-northwindclient-application"></a><span data-ttu-id="336c8-126">Sestavení a spuštění aplikace NorthwindClient</span><span class="sxs-lookup"><span data-stu-id="336c8-126">To build and run the NorthwindClient application</span></span>  
  
1.  <span data-ttu-id="336c8-127">V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt NorthwindClient a vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="336c8-127">In **Solution Explorer**, right-click the NorthwindClient project and select **Set as startup project**.</span></span>  
  
2.  <span data-ttu-id="336c8-128">Stisknutím klávesy F5 a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="336c8-128">Press F5 to start the application.</span></span>  
  
     <span data-ttu-id="336c8-129">Tím se vytvoří řešení a spustí klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="336c8-129">This builds the solution and starts the client application.</span></span> <span data-ttu-id="336c8-130">Data jsou požadovaná ze služby a zobrazovat v konzole.</span><span class="sxs-lookup"><span data-stu-id="336c8-130">Data is requested from the service and displayed in the console.</span></span>  
  
3.  <span data-ttu-id="336c8-131">Úprava hodnoty v **množství** sloupce mřížky dat a pak klikněte na **Uložit**.</span><span class="sxs-lookup"><span data-stu-id="336c8-131">Edit a value in the **Quantity** column of the data grid, and then click **Save**.</span></span>  
  
     <span data-ttu-id="336c8-132">Změny budou uloženy ve službě data.</span><span class="sxs-lookup"><span data-stu-id="336c8-132">Changes are saved to the data service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="336c8-133">Tato verze aplikace NorthwindClient nepodporuje přidávání a odstraňování entit.</span><span class="sxs-lookup"><span data-stu-id="336c8-133">This version of the NorthwindClient application does not support adding and deleting of entities.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="336c8-134">Další kroky</span><span class="sxs-lookup"><span data-stu-id="336c8-134">Next Steps</span></span>  
 <span data-ttu-id="336c8-135">Úspěšně jste vytvořili aplikace klienta, která přistupuje k ukázce Northwind [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="336c8-135">You have successfully created the client application that accesses the sample Northwind [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.</span></span> <span data-ttu-id="336c8-136">Když jste dokončili [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] rychlý start.</span><span class="sxs-lookup"><span data-stu-id="336c8-136">You have also completed the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] quickstart.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="336c8-137">přístup [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikace, najdete v části [WCF Data Services klientské knihovny](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).</span><span class="sxs-lookup"><span data-stu-id="336c8-137"> accessing an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed from a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application, see [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="336c8-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="336c8-138">See Also</span></span>  
 [<span data-ttu-id="336c8-139">Začínáme</span><span class="sxs-lookup"><span data-stu-id="336c8-139">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [<span data-ttu-id="336c8-140">Prostředky</span><span class="sxs-lookup"><span data-stu-id="336c8-140">Resources</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)
