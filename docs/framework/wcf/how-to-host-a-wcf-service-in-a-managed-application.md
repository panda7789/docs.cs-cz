---
title: 'Postupy: Hostování služby WCF ve spravované aplikaci'
description: Naučte se, jak hostovat službu WCF ve spravované aplikaci vytvořením samoobslužné služby a její otestování.
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: 7d1d61b683f60a6c643d2a2f03d367a6ae6c6c15
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246165"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a><span data-ttu-id="ae5a3-103">Postupy: hostování služby WCF ve spravované aplikaci</span><span class="sxs-lookup"><span data-stu-id="ae5a3-103">How to: Host a WCF service in a managed app</span></span>

<span data-ttu-id="ae5a3-104">Chcete-li hostovat službu uvnitř spravované aplikace, vložte kód pro službu do spravovaného kódu aplikace, Definujte koncový bod pro službu buď imperativně v kódu, deklarativně prostřednictvím konfigurace, nebo pomocí výchozích koncových bodů, a pak vytvořte instanci <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="ae5a3-104">To host a service inside a managed application, embed the code for the service inside the managed application code, define an endpoint for the service either imperatively in code, declaratively through configuration, or using default endpoints, and then create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="ae5a3-105">Chcete-li zahájit přijímání zpráv, zavolejte <xref:System.ServiceModel.ICommunicationObject.Open%2A> na <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="ae5a3-105">To start receiving messages, call <xref:System.ServiceModel.ICommunicationObject.Open%2A> on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="ae5a3-106">Tím se vytvoří a otevře se naslouchací proces pro službu.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-106">This creates and opens the listener for the service.</span></span> <span data-ttu-id="ae5a3-107">Hostování služby tímto způsobem se často označuje jako "samoobslužné hostování", protože spravovaná aplikace provádí hostující práci sama.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-107">Hosting a service in this way is often referred to as "self-hosting" because the managed application is doing the hosting work itself.</span></span> <span data-ttu-id="ae5a3-108">Chcete-li službu zavřít, zavolejte <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="ae5a3-108">To close the service, call <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> on <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="ae5a3-109">Službu je také možné hostovat ve spravované službě Windows, v Internetová informační služba (IIS) nebo ve službě WAS (Windows Process Activation Service).</span><span class="sxs-lookup"><span data-stu-id="ae5a3-109">A service can also be hosted in a managed Windows service, in Internet Information Services (IIS), or in Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="ae5a3-110">Další informace o možnostech hostování pro službu najdete v tématu [hostingové služby](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="ae5a3-110">For more information about hosting options for a service, see [Hosting Services](hosting-services.md).</span></span>

<span data-ttu-id="ae5a3-111">Hostování služby ve spravované aplikaci je nejpružnější možnost, protože pro nasazení vyžaduje minimální infrastrukturu.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-111">Hosting a service in a managed application is the most flexible option because it requires the least infrastructure to deploy.</span></span> <span data-ttu-id="ae5a3-112">Další informace o hostitelských službách ve spravovaných aplikacích najdete v tématu [hostování ve spravované aplikaci](./feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="ae5a3-112">For more information about hosting services in managed applications, see [Hosting in a Managed Application](./feature-details/hosting-in-a-managed-application.md).</span></span>

<span data-ttu-id="ae5a3-113">Následující postup ukazuje, jak implementovat samoobslužnou službu v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-113">The following procedure demonstrates how to implement a self-hosted service in a console application.</span></span>

## <a name="create-a-self-hosted-service"></a><span data-ttu-id="ae5a3-114">Vytvoření samoobslužné služby</span><span class="sxs-lookup"><span data-stu-id="ae5a3-114">Create a self-hosted service</span></span>

1. <span data-ttu-id="ae5a3-115">Vytvořit novou konzolovou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="ae5a3-115">Create a new console application:</span></span>

   1. <span data-ttu-id="ae5a3-116">Otevřete Visual Studio a v **New**  >  nabídce **soubor** vyberte nový**projekt** .</span><span class="sxs-lookup"><span data-stu-id="ae5a3-116">Open Visual Studio and select **New** > **Project** from the **File** menu.</span></span>

   2. <span data-ttu-id="ae5a3-117">V seznamu **Nainstalované šablony** vyberte **Visual C#** nebo **Visual Basic**a pak vyberte **Desktop Windows**.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-117">In the **Installed Templates** list, select **Visual C#** or **Visual Basic**, and then select **Windows Desktop**.</span></span>

   3. <span data-ttu-id="ae5a3-118">Vyberte šablonu **Konzolová aplikace** .</span><span class="sxs-lookup"><span data-stu-id="ae5a3-118">Select the **Console App** template.</span></span> <span data-ttu-id="ae5a3-119">`SelfHost`Do pole **název** zadejte a klikněte na **tlačítko OK**.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-119">Type `SelfHost` in the **Name** box and then choose **OK**.</span></span>

2. <span data-ttu-id="ae5a3-120">V **Průzkumník řešení** klikněte pravým tlačítkem na **SelfHost** a vyberte **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-120">Right-click **SelfHost** in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="ae5a3-121">Na kartě **.NET** vyberte **System. ServiceModel** a pak zvolte **OK**.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-121">Select **System.ServiceModel** from the **.NET** tab and then choose **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="ae5a3-122">Pokud není okno **Průzkumník řešení** viditelné, vyberte v nabídce **zobrazení** položku **Průzkumník řešení** .</span><span class="sxs-lookup"><span data-stu-id="ae5a3-122">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>

3. <span data-ttu-id="ae5a3-123">Poklikejte na **program.cs** nebo **Module1. vb** v **Průzkumník řešení** pro otevření v okně kódu, pokud už není otevřený.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-123">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to open it in the code window, if it's not already open.</span></span> <span data-ttu-id="ae5a3-124">Na začátek souboru přidejte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="ae5a3-124">Add the following statements at the top of the file:</span></span>

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. <span data-ttu-id="ae5a3-125">Definování a implementace kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-125">Define and implement a service contract.</span></span> <span data-ttu-id="ae5a3-126">Tento příklad definuje a `HelloWorldService` vrátí zprávu na základě vstupu do služby.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-126">This example defines a `HelloWorldService` that returns a message based on the input to the service.</span></span>

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > <span data-ttu-id="ae5a3-127">Další informace o tom, jak definovat a implementovat rozhraní služby, naleznete v tématu [How to: define](how-to-define-a-wcf-service-contract.md) a Service kontrakt a [How to: Implement kontraktu služby](how-to-implement-a-wcf-contract.md).</span><span class="sxs-lookup"><span data-stu-id="ae5a3-127">For more information about how to define and implement a service interface, see [How to: Define a Service Contract](how-to-define-a-wcf-service-contract.md) and [How to: Implement a Service Contract](how-to-implement-a-wcf-contract.md).</span></span>

5. <span data-ttu-id="ae5a3-128">V horní části `Main` metody vytvořte instanci <xref:System.Uri> třídy se základní adresou pro službu.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-128">At the top of the `Main` method, create an instance of the <xref:System.Uri> class with the base address for the service.</span></span>

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. <span data-ttu-id="ae5a3-129">Vytvořte instanci <xref:System.ServiceModel.ServiceHost> třídy, předáním a <xref:System.Type> reprezentujícího typ služby a základní adresu identifikátoru URI (Uniform Resource Identifier) na <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29> .</span><span class="sxs-lookup"><span data-stu-id="ae5a3-129">Create an instance of the <xref:System.ServiceModel.ServiceHost> class, passing a <xref:System.Type> that represents the service type and the base address Uniform Resource Identifier (URI) to the <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span></span> <span data-ttu-id="ae5a3-130">Povolte publikování metadat a pak zavolejte <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodu na <xref:System.ServiceModel.ServiceHost> k inicializaci služby a připravte ji na příjem zpráv.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-130">Enable metadata publishing, and then call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on the <xref:System.ServiceModel.ServiceHost> to initialize the service and prepare it to receive messages.</span></span>

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > <span data-ttu-id="ae5a3-131">Tento příklad používá výchozí koncové body a pro tuto službu není vyžadován žádný konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-131">This example uses default endpoints, and no configuration file is required for this service.</span></span> <span data-ttu-id="ae5a3-132">Pokud nejsou nakonfigurovány žádné koncové body, modul runtime vytvoří jeden koncový bod pro každou základní adresu pro každý kontrakt služby implementovaný službou.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-132">If no endpoints are configured, then the runtime creates one endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="ae5a3-133">Další informace o výchozích koncových bodech najdete v tématu [zjednodušená konfigurace](simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="ae5a3-133">For more information about default endpoints, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>

7. <span data-ttu-id="ae5a3-134">Stisknutím **kombinace kláves CTRL** + **+ SHIFT** + **B** sestavíte řešení.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-134">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="test-the-service"></a><span data-ttu-id="ae5a3-135">Testování služby</span><span class="sxs-lookup"><span data-stu-id="ae5a3-135">Test the service</span></span>

1. <span data-ttu-id="ae5a3-136">Stisknutím klávesy **CTRL** + **F5** spusťte službu.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-136">Press **Ctrl**+**F5** to run the service.</span></span>

2. <span data-ttu-id="ae5a3-137">Otevřete **testovacího klienta WCF**.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-137">Open **WCF Test Client**.</span></span>

    > [!TIP]
    > <span data-ttu-id="ae5a3-138">Chcete-li otevřít **klienta služby WCF test**, otevřete Developer Command Prompt pro Visual Studio a spusťte **WcfTestClient.exe**.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-138">To open **WCF Test Client**, open Developer Command Prompt for Visual Studio and execute **WcfTestClient.exe**.</span></span>

3. <span data-ttu-id="ae5a3-139">V nabídce **soubor** vyberte **Přidat službu** .</span><span class="sxs-lookup"><span data-stu-id="ae5a3-139">Select **Add Service** from the **File** menu.</span></span>

4. <span data-ttu-id="ae5a3-140">`http://localhost:8080/hello`Do pole Adresa zadejte a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-140">Type `http://localhost:8080/hello` into the address box and click **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="ae5a3-141">Ujistěte se, že je služba spuštěná, nebo jinak tento krok neproběhne úspěšně.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-141">Make sure the service is running or else this step fails.</span></span> <span data-ttu-id="ae5a3-142">Pokud jste v kódu změnili základní adresu, použijte v tomto kroku upravenou základní adresu.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-142">If you have changed the base address in the code, then use the modified base address in this step.</span></span>

5. <span data-ttu-id="ae5a3-143">Dvakrát klikněte na **sayHello** pod uzlem **Moje projekty služeb** .</span><span class="sxs-lookup"><span data-stu-id="ae5a3-143">Double-click **SayHello** under the **My Service Projects** node.</span></span> <span data-ttu-id="ae5a3-144">Do sloupce **hodnota** v seznamu **požadavků** zadejte své jméno a klikněte na **vyvolat**.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-144">Type your name into the **Value** column in the **Request** list, and click **Invoke**.</span></span>

   <span data-ttu-id="ae5a3-145">V seznamu **odpovědí** se zobrazí zpráva s odpovědí.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-145">A reply message appears in the **Response** list.</span></span>

## <a name="example"></a><span data-ttu-id="ae5a3-146">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae5a3-146">Example</span></span>

<span data-ttu-id="ae5a3-147">Následující příklad vytvoří <xref:System.ServiceModel.ServiceHost> objekt pro hostování služby typu `HelloWorldService` a poté zavolá <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodu na <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="ae5a3-147">The following example creates a <xref:System.ServiceModel.ServiceHost> object to host a service of type `HelloWorldService`, and then calls the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="ae5a3-148">V kódu je uvedena základní adresa, publikování metadat je povoleno a jsou použity výchozí koncové body.</span><span class="sxs-lookup"><span data-stu-id="ae5a3-148">A base address is provided in code, metadata publishing is enabled, and default endpoints are used.</span></span>

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="ae5a3-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae5a3-149">See also</span></span>

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [<span data-ttu-id="ae5a3-150">Postupy: Hostování služby WCF v IIS</span><span class="sxs-lookup"><span data-stu-id="ae5a3-150">How to: Host a WCF Service in IIS</span></span>](./feature-details/how-to-host-a-wcf-service-in-iis.md)
- [<span data-ttu-id="ae5a3-151">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="ae5a3-151">Self-Host</span></span>](./samples/self-host.md)
- [<span data-ttu-id="ae5a3-152">Služby hostování</span><span class="sxs-lookup"><span data-stu-id="ae5a3-152">Hosting Services</span></span>](hosting-services.md)
- [<span data-ttu-id="ae5a3-153">Postupy: Definování kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="ae5a3-153">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="ae5a3-154">Postupy: Implementace kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="ae5a3-154">How to: Implement a Service Contract</span></span>](how-to-implement-a-wcf-contract.md)
- [<span data-ttu-id="ae5a3-155">Nástroj ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="ae5a3-155">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="ae5a3-156">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="ae5a3-156">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ae5a3-157">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="ae5a3-157">System-Provided Bindings</span></span>](system-provided-bindings.md)
