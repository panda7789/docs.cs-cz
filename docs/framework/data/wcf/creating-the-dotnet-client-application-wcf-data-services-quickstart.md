---
title: Vytvoření klientské aplikace rozhraní .NET Framework (WCF Data Services – rychlý start)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
ms.openlocfilehash: 50e8d24698bd8451b90da05ffe52b473a13b3a20
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583608"
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a><span data-ttu-id="8b166-102">Vytvoření klientské aplikace rozhraní .NET Framework (WCF Data Services – rychlý start)</span><span class="sxs-lookup"><span data-stu-id="8b166-102">Creating the .NET Framework Client Application (WCF Data Services Quickstart)</span></span>

<span data-ttu-id="8b166-103">Toto je poslední úkol rychlého startu služby WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="8b166-103">This is the final task of the WCF Data Services quickstart.</span></span> <span data-ttu-id="8b166-104">V této úloze konzolové aplikace do řešení přidat, přidejte odkaz na [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informačního kanálu do této nové klientské aplikace a přístup k datovému kanálu z klientské aplikace pomocí generovaného klienta datové služby třídy a klientské knihovny OData .</span><span class="sxs-lookup"><span data-stu-id="8b166-104">In this task, you will add a console application to the solution, add a reference to the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed into this new client application, and access the OData feed from the client application by using the generated client data service classes and client libraries.</span></span>

> [!NOTE]
> <span data-ttu-id="8b166-105">Aplikace klienta na základě rozhraní .NET Framework není vyžadován pro přístup k datový kanál.</span><span class="sxs-lookup"><span data-stu-id="8b166-105">A .NET Framework-based client application is not required to access a data feed.</span></span> <span data-ttu-id="8b166-106">Datové služby je přístupný součásti žádné aplikace, která využívá datového kanálu OData.</span><span class="sxs-lookup"><span data-stu-id="8b166-106">The data service can be accessed by any application component that consumes an OData feed.</span></span> <span data-ttu-id="8b166-107">Další informace najdete v tématu [použití datové služby v klientské aplikaci](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="8b166-107">For more information, see [Using a Data Service in a Client Application](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).</span></span>

## <a name="to-create-the-client-application-by-using-visual-studio"></a><span data-ttu-id="8b166-108">Vytvoření klientské aplikace pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8b166-108">To create the client application by using Visual Studio</span></span>

1. <span data-ttu-id="8b166-109">V **Průzkumníka řešení**, klikněte pravým tlačítkem na řešení, klikněte na tlačítko **přidat**a potom klikněte na tlačítko **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="8b166-109">In **Solution Explorer**, right-click the solution, click **Add**, and then click **New Project**.</span></span>

2. <span data-ttu-id="8b166-110">V levém podokně vyberte **nainstalováno** > [**Visual C#**  nebo **jazyka Visual Basic**] > **Windows Desktop**a pak vyberte  **Aplikace WPF** šablony.</span><span class="sxs-lookup"><span data-stu-id="8b166-110">In the left pane, select **Installed** > [**Visual C#** or **Visual Basic**] > **Windows Desktop**, and then select the **WPF App** template.</span></span>

3. <span data-ttu-id="8b166-111">Zadejte `NorthwindClient` pro název projektu a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="8b166-111">Enter `NorthwindClient` for the project name, and then click **OK**.</span></span>

4. <span data-ttu-id="8b166-112">Otevřete soubor MainWindow.xaml a nahraďte kód XAML následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="8b166-112">Open the file MainWindow.xaml and replace the XAML code with the following code:</span></span>

     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml#window1xaml)]

## <a name="to-add-a-data-service-reference-to-the-project"></a><span data-ttu-id="8b166-113">Chcete-li přidat odkaz na službu do projektu</span><span class="sxs-lookup"><span data-stu-id="8b166-113">To add a data service reference to the project</span></span>

1. <span data-ttu-id="8b166-114">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt NorthwindClient, klikněte na tlačítko **přidat** > **odkaz na službu**a potom klikněte na tlačítko **zjišťování** .</span><span class="sxs-lookup"><span data-stu-id="8b166-114">In **Solution Explorer**, right-click the NorthwindClient project, click **Add** > **Service Reference**, and then click **Discover**.</span></span>

     <span data-ttu-id="8b166-115">Zobrazí se datová služba Northwind, kterou jste vytvořili v prvním úkolem.</span><span class="sxs-lookup"><span data-stu-id="8b166-115">This displays the Northwind data service that you created in the first task.</span></span>

2. <span data-ttu-id="8b166-116">V **Namespace** textového pole, typ `Northwind`a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="8b166-116">In the **Namespace** text box, type `Northwind`, and then click **OK**.</span></span>

     <span data-ttu-id="8b166-117">To přidá nový soubor kódu do projektu, který obsahuje data třídy, které se používají pro přístup k interakci s prostředky služby dat jako objektů.</span><span class="sxs-lookup"><span data-stu-id="8b166-117">This adds a new code file to the project, which contains the data classes that are used to access and interact with data service resources as objects.</span></span> <span data-ttu-id="8b166-118">Datové třídy jsou vytvořené v oboru názvů `NorthwindClient.Northwind`.</span><span class="sxs-lookup"><span data-stu-id="8b166-118">The data classes are created in the namespace `NorthwindClient.Northwind`.</span></span>

## <a name="to-access-data-service-data-in-the-wpf-application"></a><span data-ttu-id="8b166-119">Pro přístup k datům služby dat v aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="8b166-119">To access data service data in the WPF application</span></span>

1. <span data-ttu-id="8b166-120">V **Průzkumníka řešení** pod **NorthwindClient**, klikněte pravým tlačítkem na projekt a klikněte na tlačítko **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="8b166-120">In **Solution Explorer** under **NorthwindClient**, right-click the project and click **Add Reference**.</span></span>

2. <span data-ttu-id="8b166-121">V **přidat odkaz** dialogové okno, klikněte na tlačítko **.NET** kartu, vyberte knihovně System.Data.Services.Client.dll sestavení a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="8b166-121">In the **Add Reference** dialog box, click the **.NET** tab, select the System.Data.Services.Client.dll assembly, and then click **OK**.</span></span>

3. <span data-ttu-id="8b166-122">V **Průzkumníka řešení** pod **NorthwindClient**, otevřete stránku kódem pro souboru MainWindow.xaml a přidejte následující `using` – příkaz (`Imports` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="8b166-122">In **Solution Explorer** under **NorthwindClient**, open the code page for the MainWindow.xaml file, and add the following `using` statement (`Imports` in Visual Basic).</span></span>

    [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#using)]
    [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#using)]

4. <span data-ttu-id="8b166-123">Vložte následující kód, který se dotazuje služby data a vytvoří výsledek, který má vazbu <xref:System.Data.Services.Client.DataServiceCollection%601> do `MainWindow` třídy:</span><span class="sxs-lookup"><span data-stu-id="8b166-123">Insert the following code that queries that data service and binds the result to a <xref:System.Data.Services.Client.DataServiceCollection%601> into the `MainWindow` class:</span></span>

    > [!NOTE]
    > <span data-ttu-id="8b166-124">Je třeba nahradit název hostitele `localhost:12345` serveru a port, který je hostitelem vaší instance datová služba Northwind.</span><span class="sxs-lookup"><span data-stu-id="8b166-124">You must replace the host name `localhost:12345` with the server and port that is hosting your instance of the Northwind data service.</span></span>

     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#querycode)]

5. <span data-ttu-id="8b166-125">Vložte následující kód, který ukládá změny do `MainWindow` třídy:</span><span class="sxs-lookup"><span data-stu-id="8b166-125">Insert the following code that saves changes into the `MainWindow` class:</span></span>

     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#savechanges)]

## <a name="to-build-and-run-the-northwindclient-application"></a><span data-ttu-id="8b166-126">Sestavte a spusťte aplikaci NorthwindClient</span><span class="sxs-lookup"><span data-stu-id="8b166-126">To build and run the NorthwindClient application</span></span>

1. <span data-ttu-id="8b166-127">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt NorthwindClient a vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="8b166-127">In **Solution Explorer**, right-click the NorthwindClient project and select **Set as startup project**.</span></span>

2. <span data-ttu-id="8b166-128">Stisknutím klávesy **F5** ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="8b166-128">Press **F5** to start the application.</span></span>

     <span data-ttu-id="8b166-129">Tím se sestaví řešení a spustí klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="8b166-129">This builds the solution and starts the client application.</span></span> <span data-ttu-id="8b166-130">Data se požadované služby a zobrazovat v konzole.</span><span class="sxs-lookup"><span data-stu-id="8b166-130">Data is requested from the service and displayed in the console.</span></span>

3. <span data-ttu-id="8b166-131">Úprava hodnoty v **množství** sloupců datové mřížce a potom klikněte na **Uložit**.</span><span class="sxs-lookup"><span data-stu-id="8b166-131">Edit a value in the **Quantity** column of the data grid, and then click **Save**.</span></span>

     <span data-ttu-id="8b166-132">Změny se uloží do datové služby.</span><span class="sxs-lookup"><span data-stu-id="8b166-132">Changes are saved to the data service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8b166-133">Tato verze aplikace NorthwindClient nepodporuje přidávání a odstraňování entit.</span><span class="sxs-lookup"><span data-stu-id="8b166-133">This version of the NorthwindClient application does not support adding and deleting of entities.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8b166-134">Další kroky</span><span class="sxs-lookup"><span data-stu-id="8b166-134">Next Steps</span></span>

<span data-ttu-id="8b166-135">Úspěšně jste vytvořili klientská aplikace, který přistupuje k ukázkového datového kanálu OData s názvem Northwind.</span><span class="sxs-lookup"><span data-stu-id="8b166-135">You have successfully created the client application that accesses the sample Northwind OData feed.</span></span> <span data-ttu-id="8b166-136">Také jste dokončili rychlé spuštění služeb WCF Data Services!</span><span class="sxs-lookup"><span data-stu-id="8b166-136">You've also completed the WCF Data Services quickstart!</span></span>

<span data-ttu-id="8b166-137">Další informace o přístupu k OData informačního kanálu z aplikace rozhraní .NET Framework, naleznete v tématu [klientské knihovny WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).</span><span class="sxs-lookup"><span data-stu-id="8b166-137">For more information about accessing an OData feed from a .NET Framework application, see [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8b166-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b166-138">See also</span></span>

- [<span data-ttu-id="8b166-139">Začínáme</span><span class="sxs-lookup"><span data-stu-id="8b166-139">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
- [<span data-ttu-id="8b166-140">Prostředky</span><span class="sxs-lookup"><span data-stu-id="8b166-140">Resources</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)
