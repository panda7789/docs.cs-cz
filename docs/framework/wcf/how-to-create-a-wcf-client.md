---
title: 'Kurz: Vytvoření klienta Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: ddb5167c7f71a263377fb465ec44ee21057fbf4a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928896"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a><span data-ttu-id="58867-102">Kurz: Vytvoření klienta Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="58867-102">Tutorial: Create a Windows Communication Foundation client</span></span>

<span data-ttu-id="58867-103">Tento kurz popisuje čtvrtý z pěti úkolů potřebných k vytvoření aplikace Basic Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="58867-103">This tutorial describes the fourth of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="58867-104">Přehled kurzů najdete v tématu [kurz: Začněte s Windows Communication Foundation aplikacemi](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="58867-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="58867-105">Další úlohou pro vytvoření aplikace WCF je vytvoření klienta načtením metadat ze služby WCF.</span><span class="sxs-lookup"><span data-stu-id="58867-105">The next task for creating a WCF application is to create a client by retrieving metadata from a WCF service.</span></span> <span data-ttu-id="58867-106">Pomocí sady Visual Studio můžete přidat odkaz na službu, který získá metadata z koncového bodu služby MEX.</span><span class="sxs-lookup"><span data-stu-id="58867-106">You use Visual Studio to add a service reference, which gets the metadata from the service’s MEX endpoint.</span></span> <span data-ttu-id="58867-107">Visual Studio potom vygeneruje spravovaný soubor zdrojového kódu pro proxy klienta v jazyce, který jste zvolili.</span><span class="sxs-lookup"><span data-stu-id="58867-107">Visual Studio then generates a managed source code file for a client proxy in the language you've chosen.</span></span> <span data-ttu-id="58867-108">Zároveň vytvoří konfigurační soubor klienta (*App. config*).</span><span class="sxs-lookup"><span data-stu-id="58867-108">It also creates a client configuration file (*App.config*).</span></span> <span data-ttu-id="58867-109">Tento soubor umožňuje klientské aplikaci připojit se ke službě na koncovém bodu.</span><span class="sxs-lookup"><span data-stu-id="58867-109">This file enables the client application to connect to the service at an endpoint.</span></span> 

> [!NOTE]
> <span data-ttu-id="58867-110">Pokud voláte službu WCF z projektu knihovny tříd v aplikaci Visual Studio, použijte funkci **Přidat odkaz na službu** k automatickému vygenerování proxy a přidruženého konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="58867-110">If you call a WCF service from a class library project in Visual Studio, use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="58867-111">Nicméně vzhledem k tomu, že projekty knihovny tříd nepoužívají tento konfigurační soubor, je nutné přidat nastavení do generovaného konfiguračního souboru do souboru *App. config* pro spustitelný soubor, který volá knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="58867-111">However, because class library projects don't use this configuration file, you need to add the settings in the generated configuration file to the *App.config* file for the executable that calls the class library.</span></span>

> [!NOTE]
> <span data-ttu-id="58867-112">K vygenerování třídy proxy a konfiguračního souboru místo sady Visual Studio můžete použít také nástroj pro použití [metadat ServiceModel](#servicemodel-metadata-utility-tool) .</span><span class="sxs-lookup"><span data-stu-id="58867-112">As an alternative, use the [ServiceModel Metadata Utility tool](#servicemodel-metadata-utility-tool) instead of Visual Studio to generate the proxy class and configuration file.</span></span>

<span data-ttu-id="58867-113">Klientská aplikace používá vygenerovanou třídu proxy ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="58867-113">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="58867-114">Tento postup je popsaný [v tomto kurzu: Použijte klienta](how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="58867-114">This procedure is described in [Tutorial: Use a client](how-to-use-a-wcf-client.md).</span></span>

<span data-ttu-id="58867-115">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="58867-115">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="58867-116">Vytvořte a nakonfigurujte projekt konzolové aplikace pro klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="58867-116">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="58867-117">Přidejte odkaz na službu služby WCF, který vygeneruje proxy třídu a konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="58867-117">Add a service reference to the WCF service to generate the proxy class and configuration files.</span></span>

## <a name="create-a-windows-communication-foundation-client"></a><span data-ttu-id="58867-118">Vytvoření klienta Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="58867-118">Create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="58867-119">Vytvoření projektu konzolové aplikace v aplikaci Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="58867-119">Create a console app project in Visual Studio:</span></span> 

    1. <span data-ttu-id="58867-120">V nabídce **soubor** vyberte **otevřít** > **projekt/řešení** a přejděte k **soubor GettingStarted** řešení, které jste dříve vytvořili (*soubor GettingStarted. sln*).</span><span class="sxs-lookup"><span data-stu-id="58867-120">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="58867-121">Vyberte **Open** (Otevřít).</span><span class="sxs-lookup"><span data-stu-id="58867-121">Select **Open**.</span></span>

    2. <span data-ttu-id="58867-122">V nabídce **zobrazení** vyberte **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="58867-122">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="58867-123">V okně **Průzkumník řešení** vyberte řešení **soubor GettingStarted** (nejvyšší uzel) a pak v místní nabídce vyberte **Přidat** > **Nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="58867-123">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span> 
    
    4. <span data-ttu-id="58867-124">V okně **Přidat nový projekt** na levé straně vyberte kategorii **Desktop systému Windows** pod položkou  **C# Visual** nebo **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="58867-124">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> 

    5. <span data-ttu-id="58867-125">Vyberte šablonu **Konzolová aplikace (.NET Framework)** a jako **název**zadejte *GettingStartedClient* .</span><span class="sxs-lookup"><span data-stu-id="58867-125">Select the **Console App (.NET Framework)** template, and enter *GettingStartedClient* for the **Name**.</span></span> <span data-ttu-id="58867-126">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="58867-126">Select **OK**.</span></span>

2. <span data-ttu-id="58867-127">Přidejte odkaz do projektu **GettingStartedClient** do <xref:System.ServiceModel> sestavení:</span><span class="sxs-lookup"><span data-stu-id="58867-127">Add a reference in the **GettingStartedClient** project to the <xref:System.ServiceModel> assembly:</span></span> 

    1. <span data-ttu-id="58867-128">V okně **Průzkumník řešení** vyberte složku **odkazy** v projektu **GettingStartedClient** a pak vyberte **Přidat odkaz** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="58867-128">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Reference** from the shortcut menu.</span></span> 

    2. <span data-ttu-id="58867-129">V okně **Přidat odkaz** v části **sestavení** na levé straně okna vyberte možnost **Architektura**.</span><span class="sxs-lookup"><span data-stu-id="58867-129">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>
    
    3. <span data-ttu-id="58867-130">Vyhledejte a vyberte **System. ServiceModel**a pak zvolte **OK**.</span><span class="sxs-lookup"><span data-stu-id="58867-130">Find and select **System.ServiceModel**, and then choose **OK**.</span></span> 

    4. <span data-ttu-id="58867-131">Uložte řešení tak, že vyberete **soubor** > **Uložit vše**.</span><span class="sxs-lookup"><span data-stu-id="58867-131">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="58867-132">Přidejte do služby kalkulačky odkaz na službu:</span><span class="sxs-lookup"><span data-stu-id="58867-132">Add a service reference to the calculator service:</span></span>

   1. <span data-ttu-id="58867-133">V okně **Průzkumník řešení** vyberte složku **odkazy** v projektu **GettingStartedClient** a potom v místní nabídce vyberte **Přidat odkaz na službu** .</span><span class="sxs-lookup"><span data-stu-id="58867-133">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Service Reference** from the shortcut menu.</span></span>

   2. <span data-ttu-id="58867-134">V okně **Přidat odkaz na službu** vyberte **zjistit**.</span><span class="sxs-lookup"><span data-stu-id="58867-134">In the **Add Service Reference** window, select **Discover**.</span></span>

      <span data-ttu-id="58867-135">Služba CalculatorService se spustí a aplikace Visual Studio je zobrazí v poli **služby** .</span><span class="sxs-lookup"><span data-stu-id="58867-135">The CalculatorService service starts and Visual Studio displays it in the **Services** box.</span></span>

   3. <span data-ttu-id="58867-136">Vyberte **CalculatorService** a rozbalte ji a zobrazte kontrakty služeb implementované službou.</span><span class="sxs-lookup"><span data-stu-id="58867-136">Select **CalculatorService** to expand it and display the service contracts implemented by the service.</span></span> <span data-ttu-id="58867-137">Ponechte výchozí **obor názvů** a klikněte na **tlačítko OK**.</span><span class="sxs-lookup"><span data-stu-id="58867-137">Leave the default **Namespace** and choose **OK**.</span></span>

      <span data-ttu-id="58867-138">Visual Studio přidá novou položku do složky **připojené služby** v projektu **GettingStartedClient** .</span><span class="sxs-lookup"><span data-stu-id="58867-138">Visual Studio adds a new item under the **Connected Services** folder in the **GettingStartedClient** project.</span></span> 

### <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="58867-139">Nástroj pro metadata ServiceModel</span><span class="sxs-lookup"><span data-stu-id="58867-139">ServiceModel Metadata Utility tool</span></span>

<span data-ttu-id="58867-140">V následujících příkladech se dozvíte, jak volitelně pomocí nástroje pro vygenerování souboru proxy třídy [(Svcutil. exe) použít nástroj](servicemodel-metadata-utility-tool-svcutil-exe.md) pro dodané metadata.</span><span class="sxs-lookup"><span data-stu-id="58867-140">The following examples show how to optionally use the [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy class file.</span></span> <span data-ttu-id="58867-141">Tento nástroj generuje soubor třídy proxy a soubor *App. config* .</span><span class="sxs-lookup"><span data-stu-id="58867-141">This tool generates the proxy class file and the *App.config* file.</span></span> <span data-ttu-id="58867-142">Následující příklady ukazují, jak vygenerovat proxy server v C# a Visual Basic v uvedeném pořadí:</span><span class="sxs-lookup"><span data-stu-id="58867-142">The following examples show how to generate the proxy in C# and Visual Basic, respectively:</span></span>

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a><span data-ttu-id="58867-143">Konfigurační soubor klienta</span><span class="sxs-lookup"><span data-stu-id="58867-143">Client configuration file</span></span>

<span data-ttu-id="58867-144">Po vytvoření klienta Visual Studio vytvoří konfigurační soubor **App. config** v projektu **GettingStartedClient** , který by měl být podobný následujícímu příkladu:</span><span class="sxs-lookup"><span data-stu-id="58867-144">After you've created the client, Visual Studio creates the **App.config** configuration file in the **GettingStartedClient** project, which should be similar to the following example:</span></span>

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

<span data-ttu-id="58867-145">V části [ \<](../configure-apps/file-schema/wcf/endpoint-element.md) System. [ServiceModel > si všimněte > elementu koncového bodu. \<](../configure-apps/file-schema/wcf/system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="58867-145">Under the [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notice the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="58867-146">Element **Endpoint&gt;definuje koncový bod, který klient používá pro přístup ke službě, následovně: &lt;**</span><span class="sxs-lookup"><span data-stu-id="58867-146">The **&lt;endpoint&gt;** element defines the endpoint that the client uses to access the service as follows:</span></span>

- <span data-ttu-id="58867-147">Adresa: `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="58867-147">Address: `http://localhost:8000/GettingStarted/CalculatorService`.</span></span> <span data-ttu-id="58867-148">Adresa koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="58867-148">The address of the endpoint.</span></span>
- <span data-ttu-id="58867-149">Kontrakt služby: `ServiceReference1.ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="58867-149">Service contract: `ServiceReference1.ICalculator`.</span></span> <span data-ttu-id="58867-150">Kontrakt služby zajišťuje komunikaci mezi klientem WCF a službou.</span><span class="sxs-lookup"><span data-stu-id="58867-150">The service contract handles communication between the WCF client and the service.</span></span> <span data-ttu-id="58867-151">Aplikace Visual Studio vygenerovala tento kontrakt při použití funkce **Přidat odkaz na službu** .</span><span class="sxs-lookup"><span data-stu-id="58867-151">Visual Studio generated this contract when you used its **Add Service Reference** function.</span></span> <span data-ttu-id="58867-152">Je v podstatě kopie smlouvy, kterou jste definovali v projektu GettingStartedLib.</span><span class="sxs-lookup"><span data-stu-id="58867-152">It's essentially a copy of the contract that you defined in the GettingStartedLib project.</span></span> 
- <span data-ttu-id="58867-153">Vazba: <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="58867-153">Binding: <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="58867-154">Vazba určí protokol HTTP jako přenos, prointeroperabilní zabezpečení a další podrobnosti o konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="58867-154">The binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="58867-155">Další kroky</span><span class="sxs-lookup"><span data-stu-id="58867-155">Next steps</span></span>

<span data-ttu-id="58867-156">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="58867-156">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="58867-157">Vytvořte a nakonfigurujte projekt konzolové aplikace pro klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="58867-157">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="58867-158">Přidejte odkaz na službu služby WCF, který vygeneruje proxy třídu a konfigurační soubory pro klientskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="58867-158">Add a service reference to the WCF service to generate the proxy class and configuration files for the client application.</span></span>

<span data-ttu-id="58867-159">Přejděte k dalšímu kurzu, kde se dozvíte, jak používat vygenerovaný klient.</span><span class="sxs-lookup"><span data-stu-id="58867-159">Advance to the next tutorial to learn how to use the generated client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="58867-160">Kurz: Použití klienta WCF</span><span class="sxs-lookup"><span data-stu-id="58867-160">Tutorial: Use a WCF client</span></span>](how-to-use-a-wcf-client.md)
