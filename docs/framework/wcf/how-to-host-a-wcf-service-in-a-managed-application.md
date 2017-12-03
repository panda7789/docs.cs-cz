---
title: "Postupy: Hostování služby WCF ve spravované aplikaci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ddbf0df6e4fbf62ab0e7ec8c741a0f3be01c35ef
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-host-a-wcf-service-in-a-managed-application"></a><span data-ttu-id="63922-102">Postupy: Hostování služby WCF ve spravované aplikaci</span><span class="sxs-lookup"><span data-stu-id="63922-102">How to: Host a WCF Service in a Managed Application</span></span>
<span data-ttu-id="63922-103">K hostování služby ve spravované aplikaci, vkládat kód pro službu uvnitř kódu spravované aplikace, definujte koncový bod služby buď imperativní v kódu deklarativně prostřednictvím konfigurace, nebo pomocí výchozí koncové body a pak vytvořte instance <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="63922-103">To host a service inside a managed application, embed the code for the service inside the managed application code, define an endpoint for the service either imperatively in code, declaratively through configuration, or using default endpoints, and then create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
 <span data-ttu-id="63922-104">Chcete-li začít přijímat zprávy, volejte <xref:System.ServiceModel.ICommunicationObject.Open%2A> na <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="63922-104">To start receiving messages, call <xref:System.ServiceModel.ICommunicationObject.Open%2A> on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="63922-105">Tím se vytvoří a otevře naslouchací proces pro danou službu.</span><span class="sxs-lookup"><span data-stu-id="63922-105">This creates and opens the listener for the service.</span></span> <span data-ttu-id="63922-106">Hostitelská služba tímto způsobem se často označuje jako "vlastní hostování" protože spravované aplikace provádí hostování práce sám sebe.</span><span class="sxs-lookup"><span data-stu-id="63922-106">Hosting a service in this way is often referred to as "self-hosting" because the managed application is doing the hosting work itself.</span></span> <span data-ttu-id="63922-107">Službu zavřete volání <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="63922-107">To close the service, call <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> on <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
 <span data-ttu-id="63922-108">Služba může být hostovaný také ve spravované službě Windows, v Internetové informační služby (IIS) nebo v procesu aktivace služby WAS (Windows).</span><span class="sxs-lookup"><span data-stu-id="63922-108">A service can also be hosted in a managed Windows service, in Internet Information Services (IIS), or in Windows Process Activation Service (WAS).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="63922-109">hostování možnosti pro služby, najdete v části [hostování služeb](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="63922-109"> hosting options for a service, see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
 <span data-ttu-id="63922-110">Hostování ve spravované aplikaci služby je nejvíce flexibilní možnost, protože vyžaduje minimálně infrastrukturu pro nasazování.</span><span class="sxs-lookup"><span data-stu-id="63922-110">Hosting a service in a managed application is the most flexible option because it requires the least infrastructure to deploy.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="63922-111">hostování služeb ve spravovaných aplikacích, najdete v části [hostování ve spravované aplikaci](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="63922-111"> hosting services in managed applications, see [Hosting in a Managed Application](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span></span>  
  
 <span data-ttu-id="63922-112">Následující postup ukazuje, jak implementovat samoobslužné hostovanou službu v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="63922-112">The following procedure demonstrates how to implement a self-hosted service in a console application.</span></span>  
  
### <a name="to-create-a-self-hosted-service"></a><span data-ttu-id="63922-113">Chcete-li vytvořit služba s vlastním hostováním</span><span class="sxs-lookup"><span data-stu-id="63922-113">To create a self-hosted service</span></span>  
  
1.  <span data-ttu-id="63922-114">Otevřete [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] a vyberte **nový**, **projektu...**  z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="63922-114">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and select **New**, **Project...** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="63922-115">V **nainstalovaných šablonách** seznamu, vyberte **Visual C#**, **Windows** nebo **jazyka Visual Basic**, **Windows**.</span><span class="sxs-lookup"><span data-stu-id="63922-115">In the **Installed Templates** list, select **Visual C#**, **Windows** or **Visual Basic**, **Windows**.</span></span> <span data-ttu-id="63922-116">V závislosti na vaší [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] nastavení, jednu nebo obě tyto může být v rámci **jiné jazyky** uzel v **nainstalovaných šablonách** seznamu.</span><span class="sxs-lookup"><span data-stu-id="63922-116">Depending on your [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] settings, one or both of these may be under the **Other Languages** node in the **Installed Templates** list.</span></span>  
  
3.  <span data-ttu-id="63922-117">Vyberte **konzolové aplikace** z **Windows** seznamu.</span><span class="sxs-lookup"><span data-stu-id="63922-117">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="63922-118">Typ `SelfHost` v **název** pole a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="63922-118">Type `SelfHost` in the **Name** box and click **OK**.</span></span>  
  
4.  <span data-ttu-id="63922-119">Klikněte pravým tlačítkem na **SelfHost** v **Průzkumníku řešení** a vyberte **přidat odkaz na...** . Vyberte **System.ServiceModel** z **.NET** a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="63922-119">Right-click **SelfHost** in **Solution Explorer** and select **Add Reference...**. Select **System.ServiceModel** from the **.NET** tab and click **OK**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="63922-120">Pokud **Průzkumníku řešení** okno není viditelná, vyberte **Průzkumníku řešení** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="63922-120">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="63922-121">Klikněte dvakrát na **Program.cs** nebo **Module1.vb** v **Průzkumníku řešení** a otevře se v okně kód, pokud ještě není otevřené.</span><span class="sxs-lookup"><span data-stu-id="63922-121">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to open it in the code window if it is not already open.</span></span> <span data-ttu-id="63922-122">V horní části souboru přidejte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="63922-122">Add the following statements at the top of the file.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]  
  
6.  <span data-ttu-id="63922-123">Definování a implementace kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="63922-123">Define and implement a service contract.</span></span> <span data-ttu-id="63922-124">Tento příklad definuje `HelloWorldService` , vrátí se mu zpráva, na základě zadání ke službě.</span><span class="sxs-lookup"><span data-stu-id="63922-124">This example defines a `HelloWorldService` that returns a message based on the input to the service.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]  
  
    > [!NOTE]
    >  [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="63922-125">definování a implementovat rozhraní služby naleznete v tématu [postupy: definování kontraktu služby](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) a [postupy: implementace kontraktu služby](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).</span><span class="sxs-lookup"><span data-stu-id="63922-125"> how to define and implement a service interface, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) and [How to: Implement a Service Contract](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).</span></span>  
  
7.  <span data-ttu-id="63922-126">V horní části `Main` metody vytvoření instance <xref:System.Uri> se základní adresa pro službu.</span><span class="sxs-lookup"><span data-stu-id="63922-126">At the top of the `Main` method, create an instance of the <xref:System.Uri> class with the base address for the service.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]  
  
8.  <span data-ttu-id="63922-127">Vytvoření instance <xref:System.ServiceModel.ServiceHost> třídy a předejte <xref:System.Type> této představuje typ služby a základní adres identifikátor URI (Uniform Resource) k <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span><span class="sxs-lookup"><span data-stu-id="63922-127">Create an instance of the <xref:System.ServiceModel.ServiceHost> class, passing a <xref:System.Type> that represents the service type and the base address Uniform Resource Identifier (URI) to the <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span></span> <span data-ttu-id="63922-128">Povolit publikování metadat a pak zavolají <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodu <xref:System.ServiceModel.ServiceHost> k inicializaci služby a příprava přijímat zprávy.</span><span class="sxs-lookup"><span data-stu-id="63922-128">Enable metadata publishing, and then call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on the <xref:System.ServiceModel.ServiceHost> to initialize the service and prepare it to receive messages.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]       
  
    > [!NOTE]
    >  <span data-ttu-id="63922-129">Tento příklad používá výchozí koncové body a žádný konfigurační soubor je vyžadovaný pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="63922-129">This example uses default endpoints, and no configuration file is required for this service.</span></span> <span data-ttu-id="63922-130">Pokud jsou nakonfigurované žádné koncové body, modul runtime vytvoří jeden koncový bod pro každou základní adresu pro každý kontrakt služby implementované službu.</span><span class="sxs-lookup"><span data-stu-id="63922-130">If no endpoints are configured, then the runtime creates one endpoint for each base address for each service contract implemented by the service.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="63922-131">výchozí koncové body, najdete v části [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="63922-131"> default endpoints, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
9. <span data-ttu-id="63922-132">Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.</span><span class="sxs-lookup"><span data-stu-id="63922-132">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
### <a name="to-test-the-service"></a><span data-ttu-id="63922-133">K testování služby</span><span class="sxs-lookup"><span data-stu-id="63922-133">To test the service</span></span>  
  
1.  <span data-ttu-id="63922-134">Stiskněte kombinaci kláves Ctrl + F5 ke spouštění služby.</span><span class="sxs-lookup"><span data-stu-id="63922-134">Press Ctrl + F5 to run the service.</span></span>  
  
2.  <span data-ttu-id="63922-135">Otevřete **testovacího klienta WCF**.</span><span class="sxs-lookup"><span data-stu-id="63922-135">Open **WCF Test Client**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="63922-136">Chcete-li otevřít **testovacího klienta WCF**, otevřete [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] příkazový řádek a spusťte **WcfTestClient.exe**.</span><span class="sxs-lookup"><span data-stu-id="63922-136">To open **WCF Test Client**, open a [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] command prompt and execute **WcfTestClient.exe**.</span></span>  
  
3.  <span data-ttu-id="63922-137">Vyberte **přidat službu...**  z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="63922-137">Select **Add Service...** from the **File** menu.</span></span>  
  
4.  <span data-ttu-id="63922-138">Typ `http://localhost:8080/hello` do pole Adresa a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="63922-138">Type `http://localhost:8080/hello` into the address box and click **OK**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="63922-139">Ujistěte se, že je služba spuštěná, jinak tento krok nezdaří.</span><span class="sxs-lookup"><span data-stu-id="63922-139">Make sure the service is running or else this step fails.</span></span> <span data-ttu-id="63922-140">Pokud jste změnili základní adresa ve kód, pomocí upravené základní adresy v tomto kroku.</span><span class="sxs-lookup"><span data-stu-id="63922-140">If you have changed the base address in the code, then use the modified base address in this step.</span></span>  
  
5.  <span data-ttu-id="63922-141">Klikněte dvakrát na **SayHello** pod **Moje projekty služeb** uzlu.</span><span class="sxs-lookup"><span data-stu-id="63922-141">Double-click **SayHello** under the **My Service Projects** node.</span></span> <span data-ttu-id="63922-142">Zadejte název do **hodnotu** sloupec v **požadavku** seznamu a klikněte na tlačítko **Invoke**.</span><span class="sxs-lookup"><span data-stu-id="63922-142">Type your name into the **Value** column in the **Request** list, and click **Invoke**.</span></span> <span data-ttu-id="63922-143">Zobrazí se zpráva odpovědi v **odpovědi** seznamu.</span><span class="sxs-lookup"><span data-stu-id="63922-143">A reply message appears in the **Response** list.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63922-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="63922-144">Example</span></span>  
 <span data-ttu-id="63922-145">Následující příklad vytvoří <xref:System.ServiceModel.ServiceHost> objektu k hostování služby typu `HelloWorldService`a potom zavolá <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodu <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="63922-145">The following example creates a <xref:System.ServiceModel.ServiceHost> object to host a service of type `HelloWorldService`, and then calls the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="63922-146">Základní adresa je uvedené v kódu, je povoleno publikování metadat a používají výchozí koncové body.</span><span class="sxs-lookup"><span data-stu-id="63922-146">A base address is provided in code, metadata publishing is enabled, and default endpoints are used.</span></span>  
  
 [!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
 [!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="63922-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="63922-147">See Also</span></span>  
 <xref:System.Uri>  
 <xref:System.Configuration.ConfigurationManager.AppSettings%2A>  
 <xref:System.Configuration.ConfigurationManager>  
 [<span data-ttu-id="63922-148">Postupy: hostování služby WCF ve službě IIS</span><span class="sxs-lookup"><span data-stu-id="63922-148">How to: Host a WCF Service in IIS</span></span>](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)  
 [<span data-ttu-id="63922-149">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="63922-149">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)  
 [<span data-ttu-id="63922-150">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="63922-150">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="63922-151">Postupy: definování kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="63922-151">How to: Define a Service Contract</span></span>](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [<span data-ttu-id="63922-152">Postupy: implementace kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="63922-152">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [<span data-ttu-id="63922-153">Nástroj ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="63922-153">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="63922-154">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="63922-154">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="63922-155">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="63922-155">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)
