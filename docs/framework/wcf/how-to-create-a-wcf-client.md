---
title: 'Kurz: Vytvoření klienta Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: a16a0ccabfd0f9fbe69db1ea88d4613185f3c1da
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174366"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a><span data-ttu-id="6af7d-102">Kurz: Vytvoření klienta Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="6af7d-102">Tutorial: Create a Windows Communication Foundation client</span></span>

<span data-ttu-id="6af7d-103">Tento kurz popisuje čtvrté pět úloh potřebných k vytvoření základní aplikace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6af7d-103">This tutorial describes the fourth of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="6af7d-104">Přehled v kurzech, naleznete v tématu [kurzu: Začínáme s aplikacemi Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="6af7d-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="6af7d-105">Dalším úkolem pro vytvoření aplikace WCF je vytvoření klienta načtením metadata ze služby WCF.</span><span class="sxs-lookup"><span data-stu-id="6af7d-105">The next task for creating a WCF application is to create a client by retrieving metadata from a WCF service.</span></span> <span data-ttu-id="6af7d-106">Přidání odkazu na službu, která načte metadata z koncového bodu MEX služby pomocí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6af7d-106">You use Visual Studio to add a service reference, which gets the metadata from the service’s MEX endpoint.</span></span> <span data-ttu-id="6af7d-107">Visual Studio poté vygeneruje soubor spravovaném zdrojovém kódu pro proxy server klienta v jazyce, který jste zvolili.</span><span class="sxs-lookup"><span data-stu-id="6af7d-107">Visual Studio then generates a managed source code file for a client proxy in the language you've chosen.</span></span> <span data-ttu-id="6af7d-108">Také vytvoří soubor konfigurace klienta (*App.config*).</span><span class="sxs-lookup"><span data-stu-id="6af7d-108">It also creates a client configuration file (*App.config*).</span></span> <span data-ttu-id="6af7d-109">Tento soubor umožňuje klientské aplikaci připojení ke službě na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="6af7d-109">This file enables the client application to connect to the service at an endpoint.</span></span> 

> [!NOTE]
> <span data-ttu-id="6af7d-110">Při volání služby WCF z projektu knihovny tříd v sadě Visual Studio, použijte **přidat odkaz na službu** funkci, která automaticky generovat proxy serveru a související konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="6af7d-110">If you call a WCF service from a class library project in Visual Studio, use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="6af7d-111">Ale protože projekty knihovny tříd nepoužívejte tento konfigurační soubor, budete muset přidat nastavení v generované konfiguračního souboru k *App.config* soubor pro spustitelný soubor, který volá knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="6af7d-111">However, because class library projects don't use this configuration file, you need to add the settings in the generated configuration file to the *App.config* file for the executable that calls the class library.</span></span>

> [!NOTE]
> <span data-ttu-id="6af7d-112">Jako alternativu použijte [nástroj ServiceModel Metadata Utility](#servicemodel-metadata-utility-tool) místo sady Visual Studio ke generování třídy a konfigurační soubor proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="6af7d-112">As an alternative, use the [ServiceModel Metadata Utility tool](#servicemodel-metadata-utility-tool) instead of Visual Studio to generate the proxy class and configuration file.</span></span>

<span data-ttu-id="6af7d-113">Klientská aplikace používá třídu proxy generovaný ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="6af7d-113">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="6af7d-114">Tento postup je popsaný v [kurzu: Používání klienta](how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="6af7d-114">This procedure is described in [Tutorial: Use a client](how-to-use-a-wcf-client.md).</span></span>

<span data-ttu-id="6af7d-115">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="6af7d-115">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="6af7d-116">Vytvořte a nakonfigurujte projekt konzolové aplikace pro klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="6af7d-116">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="6af7d-117">Přidání odkazu na službu ve službě WCF pro vygenerování souborů třídy a konfiguraci proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="6af7d-117">Add a service reference to the WCF service to generate the proxy class and configuration files.</span></span>

## <a name="create-a-windows-communication-foundation-client"></a><span data-ttu-id="6af7d-118">Vytvoření klienta Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="6af7d-118">Create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="6af7d-119">Vytvořte projekt konzolové aplikace v sadě Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="6af7d-119">Create a console app project in Visual Studio:</span></span> 

    1. <span data-ttu-id="6af7d-120">Z **souboru** nabídce vyberte možnost **otevřít** > **projekt či řešení** a přejděte do **GettingStarted** řešení můžete vytvořené (*GettingStarted.sln*).</span><span class="sxs-lookup"><span data-stu-id="6af7d-120">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="6af7d-121">Vyberte **Open** (Otevřít).</span><span class="sxs-lookup"><span data-stu-id="6af7d-121">Select **Open**.</span></span>

    2. <span data-ttu-id="6af7d-122">Z **zobrazení** nabídce vyberte možnost **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="6af7d-122">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="6af7d-123">V **Průzkumníka řešení** okna, vyberte **GettingStarted** řešení (nejvyšší uzel) a pak vyberte **přidat** > **nový projekt** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="6af7d-123">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span> 
    
    4. <span data-ttu-id="6af7d-124">V **přidat nový projekt** na levé straně vyberte okno **Windows Desktop** kategorie v části **Visual C#**  nebo **jazyka Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="6af7d-124">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> 

    5. <span data-ttu-id="6af7d-125">Vyberte **Konzolová aplikace (.NET Framework)** šablony a zadejte *GettingStartedClient* pro **název**.</span><span class="sxs-lookup"><span data-stu-id="6af7d-125">Select the **Console App (.NET Framework)** template, and enter *GettingStartedClient* for the **Name**.</span></span> <span data-ttu-id="6af7d-126">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="6af7d-126">Select **OK**.</span></span>

2. <span data-ttu-id="6af7d-127">Přidat odkaz **GettingStartedClient** projektu <xref:System.ServiceModel> sestavení:</span><span class="sxs-lookup"><span data-stu-id="6af7d-127">Add a reference in the **GettingStartedClient** project to the <xref:System.ServiceModel> assembly:</span></span> 

    1.  <span data-ttu-id="6af7d-128">V **Průzkumníka řešení** okna, vyberte **odkazy** ve složce **GettingStartedClient** projektu a pak vyberte **přidat odkaz** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="6af7d-128">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Reference** from the shortcut menu.</span></span> 

    2. <span data-ttu-id="6af7d-129">V **přidat odkaz** okně v části **sestavení** v levé části okna vyberte **Framework**.</span><span class="sxs-lookup"><span data-stu-id="6af7d-129">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>
    
    3. <span data-ttu-id="6af7d-130">Vyhledejte a vyberte **System.ServiceModel**a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="6af7d-130">Find and select **System.ServiceModel**, and then choose **OK**.</span></span> 

    4. <span data-ttu-id="6af7d-131">Uložte řešení tak, že vyberete **souboru** > **Uložit vše**.</span><span class="sxs-lookup"><span data-stu-id="6af7d-131">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="6af7d-132">Přidání odkazu na službu do kalkulačky služby:</span><span class="sxs-lookup"><span data-stu-id="6af7d-132">Add a service reference to the calculator service:</span></span>

   1. <span data-ttu-id="6af7d-133">V **Průzkumníka řešení** okna, vyberte **odkazy** ve složce **GettingStartedClient** projektu a pak vyberte **přidat odkaz na službu**  z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="6af7d-133">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Service Reference** from the shortcut menu.</span></span>

   2. <span data-ttu-id="6af7d-134">V **přidat odkaz na službu** okně **Discover**.</span><span class="sxs-lookup"><span data-stu-id="6af7d-134">In the **Add Service Reference** window, select **Discover**.</span></span>

      <span data-ttu-id="6af7d-135">Spuštění služby CalculatorService a sady Visual Studio zobrazí ho v **služby** pole.</span><span class="sxs-lookup"><span data-stu-id="6af7d-135">The CalculatorService service starts and Visual Studio displays it in the **Services** box.</span></span>

   3. <span data-ttu-id="6af7d-136">Vyberte **CalculatorService** se rozbalí a zobrazí služba kontraktů implementovaných službou.</span><span class="sxs-lookup"><span data-stu-id="6af7d-136">Select **CalculatorService** to expand it and display the service contracts implemented by the service.</span></span> <span data-ttu-id="6af7d-137">Ponechte výchozí nastavení **Namespace** a zvolte **OK**.</span><span class="sxs-lookup"><span data-stu-id="6af7d-137">Leave the default **Namespace** and choose **OK**.</span></span>

      <span data-ttu-id="6af7d-138">Přidá novou položku v sadě Visual Studio **připojené služby** složky **GettingStartedClient** projektu.</span><span class="sxs-lookup"><span data-stu-id="6af7d-138">Visual Studio adds a new item under the **Connected Services** folder in the **GettingStartedClient** project.</span></span> 

### <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="6af7d-139">Nástroj ServiceModel Metadata Utility</span><span class="sxs-lookup"><span data-stu-id="6af7d-139">ServiceModel Metadata Utility tool</span></span>

<span data-ttu-id="6af7d-140">Následující příklady ukazují, jak volitelně použít [nástroj ServiceModel Metadata Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování souboru třídy proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="6af7d-140">The following examples show how to optionally use the [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy class file.</span></span> <span data-ttu-id="6af7d-141">Tento nástroj generuje soubor třídy proxy a *App.config* souboru.</span><span class="sxs-lookup"><span data-stu-id="6af7d-141">This tool generates the proxy class file and the *App.config* file.</span></span> <span data-ttu-id="6af7d-142">Následující příklady ukazují, jak generovat proxy serverem v C# a Visual Basic, v uvedeném pořadí:</span><span class="sxs-lookup"><span data-stu-id="6af7d-142">The following examples show how to generate the proxy in C# and Visual Basic, respectively:</span></span>

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a><span data-ttu-id="6af7d-143">Soubor konfigurace klienta</span><span class="sxs-lookup"><span data-stu-id="6af7d-143">Client configuration file</span></span>

<span data-ttu-id="6af7d-144">Po vytvoření klienta, vytvoří Visual Studio **App.config** v konfiguračním souboru **GettingStartedClient** projekt, který by měl vypadat přibližně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="6af7d-144">After you've created the client, Visual Studio creates the **App.config** configuration file in the **GettingStartedClient** project, which should be similar to the following example:</span></span>

```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup>
            <!-- specifies the version of WCF to use-->
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <system.serviceModel>
            <bindings>
                <!-- Uses wsHttpBinding-->
                <wsHttpBinding>
                    <binding name="WSHttpBinding_ICalculator" />
                </wsHttpBinding>
            </bindings>
            <client>
                <!-- specifies the endpoint to use when calling the service -->
                <endpoint address="http://localhost:8000/GettingStarted/CalculatorService"
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">
                    <identity>
                        <dns value="localhost" />
                    </identity>
                </endpoint>
            </client>
        </system.serviceModel>
    </configuration>
```

<span data-ttu-id="6af7d-145">V části [ \<system.serviceModel >](../configure-apps/file-schema/wcf/system-servicemodel.md) části, Všimněte si, že [ \<koncový bod >](../configure-apps/file-schema/wcf/endpoint-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="6af7d-145">Under the [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notice the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="6af7d-146">**&lt;Koncový bod&gt;** definuje element koncového bodu, který klient používá pro přístup ke službě následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="6af7d-146">The **&lt;endpoint&gt;** element defines the endpoint that the client uses to access the service as follows:</span></span>
- <span data-ttu-id="6af7d-147">Adresa: `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="6af7d-147">Address: `http://localhost:8000/GettingStarted/CalculatorService`.</span></span> <span data-ttu-id="6af7d-148">Adresa koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="6af7d-148">The address of the endpoint.</span></span>
- <span data-ttu-id="6af7d-149">Kontrakt služby: `ServiceReference1.ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="6af7d-149">Service contract: `ServiceReference1.ICalculator`.</span></span> <span data-ttu-id="6af7d-150">Kontrakt služby zpracovává vnitřní komunikaci mezi klienta WCF a službou.</span><span class="sxs-lookup"><span data-stu-id="6af7d-150">The service contract handles communication between the WCF client and the service.</span></span> <span data-ttu-id="6af7d-151">Visual Studio vygeneruje tuto smlouvu, když jste použili jeho **přidat odkaz na službu** funkce.</span><span class="sxs-lookup"><span data-stu-id="6af7d-151">Visual Studio generated this contract when you used its **Add Service Reference** function.</span></span> <span data-ttu-id="6af7d-152">Je v podstatě kopií kontrakt, který jste definovali v projektu GettingStartedLib.</span><span class="sxs-lookup"><span data-stu-id="6af7d-152">It's essentially a copy of the contract that you defined in the GettingStartedLib project.</span></span> 
- <span data-ttu-id="6af7d-153">Vazba: <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="6af7d-153">Binding: <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="6af7d-154">Vazba určuje HTTP jako přenosu, interoperabilní zabezpečení a další podrobnosti o konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="6af7d-154">The binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6af7d-155">Další kroky</span><span class="sxs-lookup"><span data-stu-id="6af7d-155">Next steps</span></span>

<span data-ttu-id="6af7d-156">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="6af7d-156">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="6af7d-157">Vytvořte a nakonfigurujte projekt konzolové aplikace pro klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="6af7d-157">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="6af7d-158">Přidání odkazu na službu ve službě WCF ke generování proxy třída a konfigurační soubory pro klientskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6af7d-158">Add a service reference to the WCF service to generate the proxy class and configuration files for the client application.</span></span>

<span data-ttu-id="6af7d-159">Přejděte k dalšímu kurzu, kde se naučíte, jak pomocí generovaného klienta.</span><span class="sxs-lookup"><span data-stu-id="6af7d-159">Advance to the next tutorial to learn how to use the generated client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6af7d-160">Kurz: Pomocí klienta WCF</span><span class="sxs-lookup"><span data-stu-id="6af7d-160">Tutorial: Use a WCF client</span></span>](how-to-use-a-wcf-client.md)
