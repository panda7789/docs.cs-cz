---
title: "Vytváření datové služby"
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
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57e305fd8b03e8d46c1fdcb7dd551f32062a1009
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="creating-the-data-service"></a><span data-ttu-id="b9a63-102">Vytváření datové služby</span><span class="sxs-lookup"><span data-stu-id="b9a63-102">Creating the Data Service</span></span>
<span data-ttu-id="b9a63-103">V této úloze se vytvoří služba ukázková data, která využívá [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vystavit [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informačního kanálu, který je založen na ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="b9a63-103">In this task, you will create a sample data service that uses [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] to expose an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed that is based on the Northwind sample database.</span></span> <span data-ttu-id="b9a63-104">Úloha zahrnuje následující základní kroky:</span><span class="sxs-lookup"><span data-stu-id="b9a63-104">The task involves the following basic steps:</span></span>  
  
1.  <span data-ttu-id="b9a63-105">Vytvoření [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="b9a63-105">Create an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web application.</span></span>  
  
2.  <span data-ttu-id="b9a63-106">Definují model dat pomocí [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] nástroje.</span><span class="sxs-lookup"><span data-stu-id="b9a63-106">Define the data model by using the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] tools.</span></span>  
  
3.  <span data-ttu-id="b9a63-107">Přidáte službu data do webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="b9a63-107">Add the data service to the Web application.</span></span>  
  
4.  <span data-ttu-id="b9a63-108">Povolte přístup ke službě data.</span><span class="sxs-lookup"><span data-stu-id="b9a63-108">Enable access to the data service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9a63-109">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Spuštění webové aplikace, který vytvoříte po dokončení této úlohy [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] vývojový Server poskytované [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b9a63-109">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web application that you create when you complete this task runs on the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Development Server provided by [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span> [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="b9a63-110">Vývojový Server podporuje pouze přístup z místního počítače.</span><span class="sxs-lookup"><span data-stu-id="b9a63-110"> Development Server only supports access from the local computer.</span></span> <span data-ttu-id="b9a63-111">Chcete-li také usnadňují testování a řešení potíží s službu data během vývoje, zvažte spuštění aplikace, který je hostitelem služby data pomocí Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="b9a63-111">To also make it easier to test and troubleshoot the data service during development, consider running the application that hosts the data service by using Internet Information Services (IIS).</span></span> <span data-ttu-id="b9a63-112">Další informace najdete v tématu [postup: vývoj WCF Data Service spuštěna ve službě IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).</span><span class="sxs-lookup"><span data-stu-id="b9a63-112">For more information, see [How to: Develop a WCF Data Service Running on IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).</span></span>  
  
### <a name="to-create-the-aspnet-web-application"></a><span data-ttu-id="b9a63-113">K vytvoření aplikace technologie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b9a63-113">To create the ASP.NET Web application</span></span>  
  
1.  <span data-ttu-id="b9a63-114">V [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]na **soubor** nabídce vyberte možnost **nový**a potom vyberte **projektu**.</span><span class="sxs-lookup"><span data-stu-id="b9a63-114">In [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], on the **File** menu, select **New**, and then select **Project**.</span></span>  
  
2.  <span data-ttu-id="b9a63-115">V **nový projekt** dialogové okno, v části buď [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] vyberte **webové** šablony a potom vyberte **webové aplikace ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="b9a63-115">In the **New Project** dialog box, under either [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] select the **Web** template, and then select **ASP.NET Web Application**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b9a63-116">Pokud používáte [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Web Developer, musíte vytvořit nový web místo novou webovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b9a63-116">If you use [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Web Developer, you must create a new Web site instead of a new Web application.</span></span>  
  
3.  <span data-ttu-id="b9a63-117">Typ `NorthwindService` jako název projektu.</span><span class="sxs-lookup"><span data-stu-id="b9a63-117">Type `NorthwindService` as the name of the project.</span></span>  
  
4.  <span data-ttu-id="b9a63-118">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="b9a63-118">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="b9a63-119">(Volitelné) Zadejte číslo portu specifické pro vaši webovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b9a63-119">(Optional) Specify a specific port number for your Web application.</span></span> <span data-ttu-id="b9a63-120">Poznámka: číslo portu `12345` se používá ve zbývající části rychlý start.</span><span class="sxs-lookup"><span data-stu-id="b9a63-120">Note: the port number `12345` is used in the rest of the quickstart.</span></span>  
  
    1.  <span data-ttu-id="b9a63-121">V **Průzkumníku řešení**, klikněte pravým tlačítkem [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu, že jste právě vytvořili a potom klikněte na **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="b9a63-121">In **Solution Explorer**, right-click the name of the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project that you just created, and then click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="b9a63-122">Vyberte **webové** kartě a nastavte hodnotu **specifického portu** textové pole k `12345`.</span><span class="sxs-lookup"><span data-stu-id="b9a63-122">Select the **Web** tab, and set the value of the **Specific port** text box to `12345`.</span></span>  
  
### <a name="to-define-the-data-model"></a><span data-ttu-id="b9a63-123">Chcete-li definovat datový model</span><span class="sxs-lookup"><span data-stu-id="b9a63-123">To define the data model</span></span>  
  
1.  <span data-ttu-id="b9a63-124">V **Průzkumníku řešení**, klikněte pravým tlačítkem [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu a pak klikněte na tlačítko **přidat novou položku.**</span><span class="sxs-lookup"><span data-stu-id="b9a63-124">In **Solution Explorer**, right-click the name of the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project, and then click **Add New Item.**</span></span>  
  
2.  <span data-ttu-id="b9a63-125">V **přidat novou položku** dialogové okno, klikněte **Data** šablony a potom vyberte **ADO.NET Entity Data Model**.</span><span class="sxs-lookup"><span data-stu-id="b9a63-125">In the **Add New Item** dialog box, click the **Data** template and then select **ADO.NET Entity Data Model**.</span></span>  
  
3.  <span data-ttu-id="b9a63-126">Zadejte název datového modelu, `Northwind.edmx`.</span><span class="sxs-lookup"><span data-stu-id="b9a63-126">For the name of the data model, type `Northwind.edmx`.</span></span>  
  
4.  <span data-ttu-id="b9a63-127">V [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] průvodce vyberte **generování z databáze**a potom klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="b9a63-127">In the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Wizard, select **Generate from Database**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="b9a63-128">Datový model připojení k databázi pomocí jedné z následujících kroků a potom klikněte na **Další**:</span><span class="sxs-lookup"><span data-stu-id="b9a63-128">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>  
  
    -   <span data-ttu-id="b9a63-129">Pokud jste připojení k databázi již nakonfigurována, klikněte na tlačítko **nové připojení** a vytvořit nové připojení.</span><span class="sxs-lookup"><span data-stu-id="b9a63-129">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="b9a63-130">Další informace najdete v tématu [postupy: vytvoření připojení databáze serveru SQL Server](http://go.microsoft.com/fwlink/?LinkId=123631).</span><span class="sxs-lookup"><span data-stu-id="b9a63-130">For more information, see [How to: Create Connections to SQL Server Databases](http://go.microsoft.com/fwlink/?LinkId=123631).</span></span> <span data-ttu-id="b9a63-131">To [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] instance musí mít ukázková databáze Northwind připojen.</span><span class="sxs-lookup"><span data-stu-id="b9a63-131">This [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] instance must have the Northwind sample database attached.</span></span>  
  
         <span data-ttu-id="b9a63-132">\-nebo –</span><span class="sxs-lookup"><span data-stu-id="b9a63-132">\- or -</span></span>  
  
    -   <span data-ttu-id="b9a63-133">Pokud máte připojení k databázi již byla konfigurována pro připojení k databázi Northwind, vyberte ze seznamu připojení toto připojení.</span><span class="sxs-lookup"><span data-stu-id="b9a63-133">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>  
  
6.  <span data-ttu-id="b9a63-134">Na poslední stránce průvodce zaškrtněte políčka pro všechny tabulky v databázi a zrušte zaškrtnutí políčka pro zobrazení a uložených procedur.</span><span class="sxs-lookup"><span data-stu-id="b9a63-134">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>  
  
7.  <span data-ttu-id="b9a63-135">Klikněte na tlačítko **Dokončit** zavřete průvodce.</span><span class="sxs-lookup"><span data-stu-id="b9a63-135">Click **Finish** to close the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b9a63-136">Tento model generované datové zpřístupní vlastnosti cizího klíče v typech entit.</span><span class="sxs-lookup"><span data-stu-id="b9a63-136">This generated data model exposes foreign key properties on entity types.</span></span> <span data-ttu-id="b9a63-137">Datové modely, které jsou vytvořené pomocí [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 nezahrnují tyto vlastnosti cizího klíče.</span><span class="sxs-lookup"><span data-stu-id="b9a63-137">Data models created using [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 do not include these foreign key properties.</span></span> <span data-ttu-id="b9a63-138">Z toho důvodu je nutné také aktualizovat klienta dat služby třídy klienta aplikace, které byly vytvořeny pro přístup ke službě Northwind data, která byla vytvořena pomocí [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 před pokusem o přístup k této verzi datové služby Northwind.</span><span class="sxs-lookup"><span data-stu-id="b9a63-138">Because of this, you must update the client data service classes of any client applications that were created to access the Northwind data service that was created using [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 before attempting to access this version of the Northwind data service.</span></span>  
  
### <a name="to-create-the-data-service"></a><span data-ttu-id="b9a63-139">Vytvoření datové služby</span><span class="sxs-lookup"><span data-stu-id="b9a63-139">To create the data service</span></span>  
  
1.  <span data-ttu-id="b9a63-140">V **Průzkumníku řešení**, klikněte pravým tlačítkem na název vaší [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu a pak klikněte na **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="b9a63-140">In **Solution Explorer**, right-click the name of your [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project, and then click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="b9a63-141">V **přidat novou položku** dialogové okno, vyberte **služby WCF Data Service**.</span><span class="sxs-lookup"><span data-stu-id="b9a63-141">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>  
  
3.  <span data-ttu-id="b9a63-142">Název služby, zadejte `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="b9a63-142">For the name of the service, type `Northwind`.</span></span>  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]<span data-ttu-id="b9a63-143">Visual Studio vytvoří soubory značek a kódu XML pro novou službu.</span><span class="sxs-lookup"><span data-stu-id="b9a63-143">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="b9a63-144">Ve výchozím nastavení otevře se okno editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="b9a63-144">By default, the code-editor window opens.</span></span> <span data-ttu-id="b9a63-145">V **Průzkumníku**, služba bude mít název, Northwind, s příponou. svc.cs nebo. svc.vb.</span><span class="sxs-lookup"><span data-stu-id="b9a63-145">In **Solution Explorer**, the service will have the name, Northwind, with the extension .svc.cs or .svc.vb.</span></span>  
  
4.  <span data-ttu-id="b9a63-146">V kódu pro službu data, nahraďte komentář `/* TODO: put your data source class name here */` v definici třídy, která definuje službu data s typem, který je kontejneru entit datového modelu, který v tomto případě je `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="b9a63-146">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="b9a63-147">Definice třídy by měl vypadat to následující:</span><span class="sxs-lookup"><span data-stu-id="b9a63-147">The class definition should look this the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
### <a name="to-enable-access-to-data-service-resources"></a><span data-ttu-id="b9a63-148">Chcete-li povolit přístup k datovým prostředkům služby</span><span class="sxs-lookup"><span data-stu-id="b9a63-148">To enable access to data service resources</span></span>  
  
1.  <span data-ttu-id="b9a63-149">V kódu pro službu data, nahraďte zástupný symbol kód v `InitializeService` funkce následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="b9a63-149">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="b9a63-150">To umožňuje autorizovaným klientům ke čtení a zápisu přístup k prostředkům pro zadanou entitu sady.</span><span class="sxs-lookup"><span data-stu-id="b9a63-150">This enables authorized clients to have read and write access to resources for the specified entity sets.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b9a63-151">Libovolného klienta, kterému mají přístup [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace může také přístup k prostředkům vystavené službu data.</span><span class="sxs-lookup"><span data-stu-id="b9a63-151">Any client that can access the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="b9a63-152">V produkčním datové služby aby se zabránilo neoprávněnému přístupu k prostředkům byste měli také zabezpečit vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="b9a63-152">In a production data service, to prevent unauthorized access to resources you should also secure the application itself.</span></span> <span data-ttu-id="b9a63-153">Další informace najdete v tématu [zabezpečení služby WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="b9a63-153">For more information, see [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b9a63-154">Další kroky</span><span class="sxs-lookup"><span data-stu-id="b9a63-154">Next Steps</span></span>  
 <span data-ttu-id="b9a63-155">Úspěšně jste vytvořili novou službu data, která zveřejňuje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu, který je založen na ukázková databáze Northwind a jste povolili přístup k informačnímu kanálu pro klienty, kteří mají oprávnění na [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="b9a63-155">You have successfully created a new data service that exposes an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed that is based on the Northwind sample database, and you have enabled access to the feed for clients that have permissions on the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web application.</span></span> <span data-ttu-id="b9a63-156">V dalším kroku se spustí službu data z [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] a budou přistupovat [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu odesláním požadavky HTTP GET prostřednictvím webového prohlížeče:</span><span class="sxs-lookup"><span data-stu-id="b9a63-156">Next, you will start the data service from [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] and you will access the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed by submitting HTTP GET requests through a Web browser:</span></span>  
  
 [<span data-ttu-id="b9a63-157">Přístup ke službě z webového prohlížeče</span><span class="sxs-lookup"><span data-stu-id="b9a63-157">Accessing the Service from a Web Browser</span></span>](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a><span data-ttu-id="b9a63-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9a63-158">See Also</span></span>  
 [<span data-ttu-id="b9a63-159">Nástroje modelu ADO.NET Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="b9a63-159">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)
