---
title: 'Postupy: Hostování služby WCF ve spravované aplikaci'
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: e3adcad6ba70aa64b797325cd45a043301d7e680
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320981"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a><span data-ttu-id="a06f6-102">Postupy: hostování služby WCF ve spravované aplikaci</span><span class="sxs-lookup"><span data-stu-id="a06f6-102">How to: Host a WCF service in a managed app</span></span>

<span data-ttu-id="a06f6-103">Chcete-li hostovat službu uvnitř spravované aplikace, vložte kód pro službu do spravovaného kódu aplikace, Definujte koncový bod pro službu buď imperativně v kódu, deklarativně prostřednictvím konfigurace, nebo pomocí výchozích koncových bodů, a pak vytvořte instanci <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a06f6-103">To host a service inside a managed application, embed the code for the service inside the managed application code, define an endpoint for the service either imperatively in code, declaratively through configuration, or using default endpoints, and then create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="a06f6-104">Chcete-li zahájit přijímání zpráv, zavolejte <xref:System.ServiceModel.ICommunicationObject.Open%2A> na <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a06f6-104">To start receiving messages, call <xref:System.ServiceModel.ICommunicationObject.Open%2A> on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="a06f6-105">Tím se vytvoří a otevře se naslouchací proces pro službu.</span><span class="sxs-lookup"><span data-stu-id="a06f6-105">This creates and opens the listener for the service.</span></span> <span data-ttu-id="a06f6-106">Hostování služby tímto způsobem se často označuje jako "samoobslužné hostování", protože spravovaná aplikace provádí hostující práci sama.</span><span class="sxs-lookup"><span data-stu-id="a06f6-106">Hosting a service in this way is often referred to as "self-hosting" because the managed application is doing the hosting work itself.</span></span> <span data-ttu-id="a06f6-107">Chcete-li službu zavřít, zavolejte <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a06f6-107">To close the service, call <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> on <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="a06f6-108">Službu je také možné hostovat ve spravované službě Windows, v Internetová informační služba (IIS) nebo ve službě WAS (Windows Process Activation Service).</span><span class="sxs-lookup"><span data-stu-id="a06f6-108">A service can also be hosted in a managed Windows service, in Internet Information Services (IIS), or in Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="a06f6-109">Další informace o možnostech hostování pro službu najdete v tématu [hostingové služby](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="a06f6-109">For more information about hosting options for a service, see [Hosting Services](hosting-services.md).</span></span>

<span data-ttu-id="a06f6-110">Hostování služby ve spravované aplikaci je nejpružnější možnost, protože pro nasazení vyžaduje minimální infrastrukturu.</span><span class="sxs-lookup"><span data-stu-id="a06f6-110">Hosting a service in a managed application is the most flexible option because it requires the least infrastructure to deploy.</span></span> <span data-ttu-id="a06f6-111">Další informace o hostitelských službách ve spravovaných aplikacích najdete v tématu [hostování ve spravované aplikaci](./feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="a06f6-111">For more information about hosting services in managed applications, see [Hosting in a Managed Application](./feature-details/hosting-in-a-managed-application.md).</span></span>

<span data-ttu-id="a06f6-112">Následující postup ukazuje, jak implementovat samoobslužnou službu v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a06f6-112">The following procedure demonstrates how to implement a self-hosted service in a console application.</span></span>

## <a name="create-a-self-hosted-service"></a><span data-ttu-id="a06f6-113">Vytvoření samoobslužné služby</span><span class="sxs-lookup"><span data-stu-id="a06f6-113">Create a self-hosted service</span></span>

1. <span data-ttu-id="a06f6-114">Vytvořit novou konzolovou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="a06f6-114">Create a new console application:</span></span>

   1. <span data-ttu-id="a06f6-115">Otevřete Visual Studio a v nabídce **soubor** vyberte **Nový** > **projekt** .</span><span class="sxs-lookup"><span data-stu-id="a06f6-115">Open Visual Studio and select **New** > **Project** from the **File** menu.</span></span>

   2. <span data-ttu-id="a06f6-116">V seznamu **Nainstalované šablony** vyberte možnost **Visual C#**  nebo **Visual Basic**a pak vyberte možnost **desktopová plocha systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="a06f6-116">In the **Installed Templates** list, select **Visual C#** or **Visual Basic**, and then select **Windows Desktop**.</span></span>

   3. <span data-ttu-id="a06f6-117">Vyberte šablonu **Konzolová aplikace** .</span><span class="sxs-lookup"><span data-stu-id="a06f6-117">Select the **Console App** template.</span></span> <span data-ttu-id="a06f6-118">Do pole **název** zadejte `SelfHost` a klikněte na **tlačítko OK**.</span><span class="sxs-lookup"><span data-stu-id="a06f6-118">Type `SelfHost` in the **Name** box and then choose **OK**.</span></span>

2. <span data-ttu-id="a06f6-119">V **Průzkumník řešení** klikněte pravým tlačítkem na **SelfHost** a vyberte **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="a06f6-119">Right-click **SelfHost** in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="a06f6-120">Na kartě **.NET** vyberte **System. ServiceModel** a pak zvolte **OK**.</span><span class="sxs-lookup"><span data-stu-id="a06f6-120">Select **System.ServiceModel** from the **.NET** tab and then choose **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="a06f6-121">Pokud není okno **Průzkumník řešení** viditelné, vyberte v nabídce **zobrazení** položku **Průzkumník řešení** .</span><span class="sxs-lookup"><span data-stu-id="a06f6-121">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>

3. <span data-ttu-id="a06f6-122">Poklikejte na **program.cs** nebo **Module1. vb** v **Průzkumník řešení** pro otevření v okně kódu, pokud už není otevřený.</span><span class="sxs-lookup"><span data-stu-id="a06f6-122">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to open it in the code window, if it's not already open.</span></span> <span data-ttu-id="a06f6-123">Na začátek souboru přidejte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="a06f6-123">Add the following statements at the top of the file:</span></span>

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. <span data-ttu-id="a06f6-124">Definování a implementace kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="a06f6-124">Define and implement a service contract.</span></span> <span data-ttu-id="a06f6-125">Tento příklad definuje `HelloWorldService`, který vrátí zprávu na základě vstupu do služby.</span><span class="sxs-lookup"><span data-stu-id="a06f6-125">This example defines a `HelloWorldService` that returns a message based on the input to the service.</span></span>

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > <span data-ttu-id="a06f6-126">Další informace o tom, jak definovat a implementovat rozhraní služby, naleznete v tématu [How to: define](how-to-define-a-wcf-service-contract.md) a Service kontrakt a [How to: Implement kontraktu služby](how-to-implement-a-wcf-contract.md).</span><span class="sxs-lookup"><span data-stu-id="a06f6-126">For more information about how to define and implement a service interface, see [How to: Define a Service Contract](how-to-define-a-wcf-service-contract.md) and [How to: Implement a Service Contract](how-to-implement-a-wcf-contract.md).</span></span>

5. <span data-ttu-id="a06f6-127">V horní části metody `Main` vytvořte instanci <xref:System.Uri> třídy se základní adresou pro službu.</span><span class="sxs-lookup"><span data-stu-id="a06f6-127">At the top of the `Main` method, create an instance of the <xref:System.Uri> class with the base address for the service.</span></span>

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. <span data-ttu-id="a06f6-128">Vytvořte instanci třídy <xref:System.ServiceModel.ServiceHost> a předejte <xref:System.Type>, která představuje typ služby a základní adresu identifikátoru URI (Uniform Resource Identifier) na <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span><span class="sxs-lookup"><span data-stu-id="a06f6-128">Create an instance of the <xref:System.ServiceModel.ServiceHost> class, passing a <xref:System.Type> that represents the service type and the base address Uniform Resource Identifier (URI) to the <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span></span> <span data-ttu-id="a06f6-129">Povolte publikování metadat a potom zavolejte metodu <xref:System.ServiceModel.ICommunicationObject.Open%2A> v <xref:System.ServiceModel.ServiceHost> k inicializaci služby a připravte ji na příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="a06f6-129">Enable metadata publishing, and then call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on the <xref:System.ServiceModel.ServiceHost> to initialize the service and prepare it to receive messages.</span></span>

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > <span data-ttu-id="a06f6-130">Tento příklad používá výchozí koncové body a pro tuto službu není vyžadován žádný konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="a06f6-130">This example uses default endpoints, and no configuration file is required for this service.</span></span> <span data-ttu-id="a06f6-131">Pokud nejsou nakonfigurovány žádné koncové body, modul runtime vytvoří jeden koncový bod pro každou základní adresu pro každý kontrakt služby implementovaný službou.</span><span class="sxs-lookup"><span data-stu-id="a06f6-131">If no endpoints are configured, then the runtime creates one endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="a06f6-132">Další informace o výchozích koncových bodech najdete v tématu [zjednodušená konfigurace](simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a06f6-132">For more information about default endpoints, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>

7. <span data-ttu-id="a06f6-133">Pro sestavení řešení stiskněte **kombinaci kláves Ctrl**+**SHIFT**+**B** .</span><span class="sxs-lookup"><span data-stu-id="a06f6-133">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="test-the-service"></a><span data-ttu-id="a06f6-134">Testování služby</span><span class="sxs-lookup"><span data-stu-id="a06f6-134">Test the service</span></span>

1. <span data-ttu-id="a06f6-135">Stisknutím klávesy **Ctrl**+**F5** službu spusťte.</span><span class="sxs-lookup"><span data-stu-id="a06f6-135">Press **Ctrl**+**F5** to run the service.</span></span>

2. <span data-ttu-id="a06f6-136">Otevřete **testovacího klienta WCF**.</span><span class="sxs-lookup"><span data-stu-id="a06f6-136">Open **WCF Test Client**.</span></span>

    > [!TIP]
    > <span data-ttu-id="a06f6-137">Chcete-li otevřít **klienta služby WCF test**, otevřete Developer Command Prompt pro Visual Studio a spusťte **WcfTestClient. exe**.</span><span class="sxs-lookup"><span data-stu-id="a06f6-137">To open **WCF Test Client**, open Developer Command Prompt for Visual Studio and execute **WcfTestClient.exe**.</span></span>

3. <span data-ttu-id="a06f6-138">V nabídce **soubor** vyberte **Přidat službu** .</span><span class="sxs-lookup"><span data-stu-id="a06f6-138">Select **Add Service** from the **File** menu.</span></span>

4. <span data-ttu-id="a06f6-139">Do pole Adresa zadejte `http://localhost:8080/hello` a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="a06f6-139">Type `http://localhost:8080/hello` into the address box and click **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="a06f6-140">Ujistěte se, že je služba spuštěná, nebo jinak tento krok neproběhne úspěšně.</span><span class="sxs-lookup"><span data-stu-id="a06f6-140">Make sure the service is running or else this step fails.</span></span> <span data-ttu-id="a06f6-141">Pokud jste v kódu změnili základní adresu, použijte v tomto kroku upravenou základní adresu.</span><span class="sxs-lookup"><span data-stu-id="a06f6-141">If you have changed the base address in the code, then use the modified base address in this step.</span></span>

5. <span data-ttu-id="a06f6-142">Dvakrát klikněte na **sayHello** pod uzlem **Moje projekty služeb** .</span><span class="sxs-lookup"><span data-stu-id="a06f6-142">Double-click **SayHello** under the **My Service Projects** node.</span></span> <span data-ttu-id="a06f6-143">Do sloupce **hodnota** v seznamu **požadavků** zadejte své jméno a klikněte na **vyvolat**.</span><span class="sxs-lookup"><span data-stu-id="a06f6-143">Type your name into the **Value** column in the **Request** list, and click **Invoke**.</span></span>

   <span data-ttu-id="a06f6-144">V seznamu **odpovědí** se zobrazí zpráva s odpovědí.</span><span class="sxs-lookup"><span data-stu-id="a06f6-144">A reply message appears in the **Response** list.</span></span>

## <a name="example"></a><span data-ttu-id="a06f6-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="a06f6-145">Example</span></span>

<span data-ttu-id="a06f6-146">Následující příklad vytvoří objekt <xref:System.ServiceModel.ServiceHost> pro hostování služby typu `HelloWorldService`a poté zavolá metodu <xref:System.ServiceModel.ICommunicationObject.Open%2A> na <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a06f6-146">The following example creates a <xref:System.ServiceModel.ServiceHost> object to host a service of type `HelloWorldService`, and then calls the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="a06f6-147">V kódu je uvedena základní adresa, publikování metadat je povoleno a jsou použity výchozí koncové body.</span><span class="sxs-lookup"><span data-stu-id="a06f6-147">A base address is provided in code, metadata publishing is enabled, and default endpoints are used.</span></span>

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="a06f6-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a06f6-148">See also</span></span>

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [<span data-ttu-id="a06f6-149">Postupy: Hostování služby WCF v IIS</span><span class="sxs-lookup"><span data-stu-id="a06f6-149">How to: Host a WCF Service in IIS</span></span>](./feature-details/how-to-host-a-wcf-service-in-iis.md)
- [<span data-ttu-id="a06f6-150">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="a06f6-150">Self-Host</span></span>](./samples/self-host.md)
- [<span data-ttu-id="a06f6-151">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="a06f6-151">Hosting Services</span></span>](hosting-services.md)
- [<span data-ttu-id="a06f6-152">Postupy: Definování kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="a06f6-152">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="a06f6-153">Postupy: Implementace kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="a06f6-153">How to: Implement a Service Contract</span></span>](how-to-implement-a-wcf-contract.md)
- [<span data-ttu-id="a06f6-154">Nástroj metadat modelu služby (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="a06f6-154">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="a06f6-155">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="a06f6-155">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a06f6-156">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="a06f6-156">System-Provided Bindings</span></span>](system-provided-bindings.md)
