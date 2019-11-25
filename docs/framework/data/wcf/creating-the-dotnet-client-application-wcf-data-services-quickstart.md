---
title: Vytvoření klientské aplikace .NET Framework (WCF Data Services rychlý Start)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
ms.openlocfilehash: 4beaba24e42b15ebc45ece6e5319a2b14df54ab6
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975385"
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a><span data-ttu-id="8fe7b-102">Vytvoření klientské aplikace .NET Framework (WCF Data Services rychlý Start)</span><span class="sxs-lookup"><span data-stu-id="8fe7b-102">Creating the .NET Framework Client Application (WCF Data Services Quickstart)</span></span>

<span data-ttu-id="8fe7b-103">Toto je konečný úkol pro rychlý Start WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="8fe7b-103">This is the final task of the WCF Data Services quickstart.</span></span> <span data-ttu-id="8fe7b-104">V této úloze přidáte konzolovou aplikaci do řešení, přidáte odkaz na informační kanál OData (Open Data Protocol) do této nové klientské aplikace a získáte přístup k datovému kanálu OData z klientské aplikace pomocí generovaných tříd klientských datových služeb a klienta. Knihovna.</span><span class="sxs-lookup"><span data-stu-id="8fe7b-104">In this task, you will add a console application to the solution, add a reference to the Open Data Protocol (OData) feed into this new client application, and access the OData feed from the client application by using the generated client data service classes and client libraries.</span></span>

> [!NOTE]
> <span data-ttu-id="8fe7b-105">Klientská aplikace založená na .NET Framework není nutná pro přístup k datovému kanálu.</span><span class="sxs-lookup"><span data-stu-id="8fe7b-105">A .NET Framework-based client application is not required to access a data feed.</span></span> <span data-ttu-id="8fe7b-106">Datová služba je k dispozici pro libovolnou komponentu aplikace, která využívá datový kanál OData.</span><span class="sxs-lookup"><span data-stu-id="8fe7b-106">The data service can be accessed by any application component that consumes an OData feed.</span></span> <span data-ttu-id="8fe7b-107">Další informace najdete v tématu [použití datové služby v klientské aplikaci](using-a-data-service-in-a-client-application-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="8fe7b-107">For more information, see [Using a Data Service in a Client Application](using-a-data-service-in-a-client-application-wcf-data-services.md).</span></span>

## <a name="to-create-the-client-application-by-using-visual-studio"></a><span data-ttu-id="8fe7b-108">Vytvoření klientské aplikace pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8fe7b-108">To create the client application by using Visual Studio</span></span>

1. <span data-ttu-id="8fe7b-109">V **Průzkumník řešení**klikněte pravým tlačítkem myši na řešení, klikněte na tlačítko **Přidat**a poté klikněte na možnost **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="8fe7b-109">In **Solution Explorer**, right-click the solution, click **Add**, and then click **New Project**.</span></span>

2. <span data-ttu-id="8fe7b-110">V levém podokně vyberte **nainstalované** > [ **C# Visual** nebo **Visual Basic**] > **Windows Desktop**a pak vyberte šablonu **aplikace WPF** .</span><span class="sxs-lookup"><span data-stu-id="8fe7b-110">In the left pane, select **Installed** > [**Visual C#** or **Visual Basic**] > **Windows Desktop**, and then select the **WPF App** template.</span></span>

3. <span data-ttu-id="8fe7b-111">Jako název projektu zadejte `NorthwindClient` a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="8fe7b-111">Enter `NorthwindClient` for the project name, and then click **OK**.</span></span>

4. <span data-ttu-id="8fe7b-112">Otevřete soubor MainWindow. XAML a nahraďte kód XAML následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="8fe7b-112">Open the file MainWindow.xaml and replace the XAML code with the following code:</span></span>

     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml#window1xaml)]

## <a name="to-add-a-data-service-reference-to-the-project"></a><span data-ttu-id="8fe7b-113">Přidání odkazu na datovou službu do projektu</span><span class="sxs-lookup"><span data-stu-id="8fe7b-113">To add a data service reference to the project</span></span>

1. <span data-ttu-id="8fe7b-114">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt NorthwindClient, klikněte na **Přidat** > **odkaz na službu**a pak klikněte na **zjistit**.</span><span class="sxs-lookup"><span data-stu-id="8fe7b-114">In **Solution Explorer**, right-click the NorthwindClient project, click **Add** > **Service Reference**, and then click **Discover**.</span></span>

     <span data-ttu-id="8fe7b-115">Tím se zobrazí datová služba Northwind, kterou jste vytvořili v prvním úkolu.</span><span class="sxs-lookup"><span data-stu-id="8fe7b-115">This displays the Northwind data service that you created in the first task.</span></span>

2. <span data-ttu-id="8fe7b-116">Do textového pole **obor názvů** zadejte `Northwind`a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="8fe7b-116">In the **Namespace** text box, type `Northwind`, and then click **OK**.</span></span>

     <span data-ttu-id="8fe7b-117">Tím se do projektu přidá nový soubor kódu, který obsahuje datové třídy, které slouží k přístupu k prostředkům datové služby a k interakci s nimi.</span><span class="sxs-lookup"><span data-stu-id="8fe7b-117">This adds a new code file to the project, which contains the data classes that are used to access and interact with data service resources as objects.</span></span> <span data-ttu-id="8fe7b-118">Datové třídy jsou vytvořeny v oboru názvů `NorthwindClient.Northwind`.</span><span class="sxs-lookup"><span data-stu-id="8fe7b-118">The data classes are created in the namespace `NorthwindClient.Northwind`.</span></span>

## <a name="to-access-data-service-data-in-the-wpf-application"></a><span data-ttu-id="8fe7b-119">Přístup k datům datové služby v aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="8fe7b-119">To access data service data in the WPF application</span></span>

1. <span data-ttu-id="8fe7b-120">V **Průzkumník řešení** v části **NorthwindClient**klikněte pravým tlačítkem na projekt a klikněte na **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="8fe7b-120">In **Solution Explorer** under **NorthwindClient**, right-click the project and click **Add Reference**.</span></span>

2. <span data-ttu-id="8fe7b-121">V dialogovém okně **Přidat odkaz** klikněte na kartu **.NET** , vyberte sestavení System. data. Services. Client. dll a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="8fe7b-121">In the **Add Reference** dialog box, click the **.NET** tab, select the System.Data.Services.Client.dll assembly, and then click **OK**.</span></span>

3. <span data-ttu-id="8fe7b-122">V **Průzkumník řešení** v části **NorthwindClient**otevřete znakovou stránku souboru MainWindow. XAML a přidejte následující příkaz `using` (`Imports` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="8fe7b-122">In **Solution Explorer** under **NorthwindClient**, open the code page for the MainWindow.xaml file, and add the following `using` statement (`Imports` in Visual Basic).</span></span>

    [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#using)]
    [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#using)]

4. <span data-ttu-id="8fe7b-123">Vložte následující kód, který odešle dotaz na datovou službu a vytvoří vazby výsledku k <xref:System.Data.Services.Client.DataServiceCollection%601> do `MainWindow` třídy:</span><span class="sxs-lookup"><span data-stu-id="8fe7b-123">Insert the following code that queries that data service and binds the result to a <xref:System.Data.Services.Client.DataServiceCollection%601> into the `MainWindow` class:</span></span>

    > [!NOTE]
    > <span data-ttu-id="8fe7b-124">Název hostitele musíte nahradit `localhost:12345` serverem a portem, který je hostitelem vaší instance datové služby Northwind.</span><span class="sxs-lookup"><span data-stu-id="8fe7b-124">You must replace the host name `localhost:12345` with the server and port that is hosting your instance of the Northwind data service.</span></span>

     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#querycode)]

5. <span data-ttu-id="8fe7b-125">Vložte následující kód, který ukládá změny do `MainWindow` třídy:</span><span class="sxs-lookup"><span data-stu-id="8fe7b-125">Insert the following code that saves changes into the `MainWindow` class:</span></span>

     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#savechanges)]

## <a name="to-build-and-run-the-northwindclient-application"></a><span data-ttu-id="8fe7b-126">Sestavení a spuštění aplikace NorthwindClient</span><span class="sxs-lookup"><span data-stu-id="8fe7b-126">To build and run the NorthwindClient application</span></span>

1. <span data-ttu-id="8fe7b-127">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt NorthwindClient a vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="8fe7b-127">In **Solution Explorer**, right-click the NorthwindClient project and select **Set as startup project**.</span></span>

2. <span data-ttu-id="8fe7b-128">Stisknutím klávesy **F5** spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8fe7b-128">Press **F5** to start the application.</span></span>

     <span data-ttu-id="8fe7b-129">Tím se vytvoří řešení a spustí se klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="8fe7b-129">This builds the solution and starts the client application.</span></span> <span data-ttu-id="8fe7b-130">Služba požaduje data, která se zobrazí v konzole nástroje.</span><span class="sxs-lookup"><span data-stu-id="8fe7b-130">Data is requested from the service and displayed in the console.</span></span>

3. <span data-ttu-id="8fe7b-131">Upravte hodnotu ve sloupci **množství** datové mřížky a pak klikněte na **Uložit**.</span><span class="sxs-lookup"><span data-stu-id="8fe7b-131">Edit a value in the **Quantity** column of the data grid, and then click **Save**.</span></span>

     <span data-ttu-id="8fe7b-132">Změny se uloží do datové služby.</span><span class="sxs-lookup"><span data-stu-id="8fe7b-132">Changes are saved to the data service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8fe7b-133">Tato verze aplikace NorthwindClient nepodporuje přidávání a odstraňování entit.</span><span class="sxs-lookup"><span data-stu-id="8fe7b-133">This version of the NorthwindClient application does not support adding and deleting of entities.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8fe7b-134">Další kroky</span><span class="sxs-lookup"><span data-stu-id="8fe7b-134">Next Steps</span></span>

<span data-ttu-id="8fe7b-135">Úspěšně jste vytvořili klientskou aplikaci, která přistupuje k ukázkovému informačnímu kanálu OData Northwind.</span><span class="sxs-lookup"><span data-stu-id="8fe7b-135">You have successfully created the client application that accesses the sample Northwind OData feed.</span></span> <span data-ttu-id="8fe7b-136">Dokončili jste také rychlý Start WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="8fe7b-136">You've also completed the WCF Data Services quickstart!</span></span>

<span data-ttu-id="8fe7b-137">Další informace o přístupu k datovému kanálu OData z .NET Framework aplikace najdete v tématu [WCF Data Services Klientská knihovna](wcf-data-services-client-library.md).</span><span class="sxs-lookup"><span data-stu-id="8fe7b-137">For more information about accessing an OData feed from a .NET Framework application, see [WCF Data Services Client Library](wcf-data-services-client-library.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8fe7b-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8fe7b-138">See also</span></span>

- [<span data-ttu-id="8fe7b-139">Začínáme</span><span class="sxs-lookup"><span data-stu-id="8fe7b-139">Getting Started</span></span>](getting-started-with-wcf-data-services.md)
- [<span data-ttu-id="8fe7b-140">Prostředky</span><span class="sxs-lookup"><span data-stu-id="8fe7b-140">Resources</span></span>](wcf-data-services-resources.md)
