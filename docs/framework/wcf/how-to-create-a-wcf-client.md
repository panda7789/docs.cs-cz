---
title: 'Kurz: Vytvoření klienta Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: bfa4cbacc5a947cb51d577503b5e46f9a5f8de39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184104"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a><span data-ttu-id="f33c1-102">Kurz: Vytvoření klienta Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f33c1-102">Tutorial: Create a Windows Communication Foundation client</span></span>

<span data-ttu-id="f33c1-103">Tento kurz popisuje čtvrtý z pěti úloh potřebných k vytvoření základní aplikace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f33c1-103">This tutorial describes the fourth of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="f33c1-104">Přehled výukových programů najdete v [tématu Výuka: Začínáme s aplikacemi Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="f33c1-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="f33c1-105">Dalším úkolem pro vytvoření aplikace WCF je vytvoření klienta načtením metadat ze služby WCF.</span><span class="sxs-lookup"><span data-stu-id="f33c1-105">The next task for creating a WCF application is to create a client by retrieving metadata from a WCF service.</span></span> <span data-ttu-id="f33c1-106">Pomocí sady Visual Studio přidáte odkaz na službu, která získá metadata z koncového bodu MEX služby.</span><span class="sxs-lookup"><span data-stu-id="f33c1-106">You use Visual Studio to add a service reference, which gets the metadata from the service’s MEX endpoint.</span></span> <span data-ttu-id="f33c1-107">Visual Studio pak generuje soubor spravovaného zdrojového kódu pro klientský proxy server v jazyce, který jste vybrali.</span><span class="sxs-lookup"><span data-stu-id="f33c1-107">Visual Studio then generates a managed source code file for a client proxy in the language you've chosen.</span></span> <span data-ttu-id="f33c1-108">Vytvoří také konfigurační soubor klienta (*App.config*).</span><span class="sxs-lookup"><span data-stu-id="f33c1-108">It also creates a client configuration file (*App.config*).</span></span> <span data-ttu-id="f33c1-109">Tento soubor umožňuje klientské aplikaci připojit ke službě v koncovém bodě.</span><span class="sxs-lookup"><span data-stu-id="f33c1-109">This file enables the client application to connect to the service at an endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="f33c1-110">Pokud voláte službu WCF z projektu knihovny tříd v sadě Visual Studio, použijte funkci **Přidat odkaz na službu** k automatickému generování proxy a přidruženého konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="f33c1-110">If you call a WCF service from a class library project in Visual Studio, use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="f33c1-111">Protože však projekty knihovny tříd tento konfigurační soubor nepoužívají, je třeba přidat nastavení v generovaném konfiguračním souboru do souboru *App.config* pro spustitelný soubor, který volá knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="f33c1-111">However, because class library projects don't use this configuration file, you need to add the settings in the generated configuration file to the *App.config* file for the executable that calls the class library.</span></span>

> [!NOTE]
> <span data-ttu-id="f33c1-112">Alternativně použijte [nástroj ServiceModel Metadata Utility](#servicemodel-metadata-utility-tool) namísto Visual Studia ke generování třídy proxy a konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="f33c1-112">As an alternative, use the [ServiceModel Metadata Utility tool](#servicemodel-metadata-utility-tool) instead of Visual Studio to generate the proxy class and configuration file.</span></span>

<span data-ttu-id="f33c1-113">Klientská aplikace používá vygenerované proxy třídy ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="f33c1-113">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="f33c1-114">Tento postup je popsán v [kurzu: Použití klienta](how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="f33c1-114">This procedure is described in [Tutorial: Use a client](how-to-use-a-wcf-client.md).</span></span>

<span data-ttu-id="f33c1-115">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="f33c1-115">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="f33c1-116">Vytvořte a nakonfigurujte projekt konzolové aplikace pro klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="f33c1-116">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="f33c1-117">Přidejte odkaz na službu WCF pro generování třídy proxy a konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="f33c1-117">Add a service reference to the WCF service to generate the proxy class and configuration files.</span></span>

## <a name="create-a-windows-communication-foundation-client"></a><span data-ttu-id="f33c1-118">Vytvoření klienta Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f33c1-118">Create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="f33c1-119">Vytvoření projektu konzolové aplikace v Sadě Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="f33c1-119">Create a console app project in Visual Studio:</span></span>

    1. <span data-ttu-id="f33c1-120">V nabídce **Soubor** vyberte **Otevřít** > **projekt/řešení** a přejděte k řešení **GettingStarted,** které jste dříve vytvořili (*GettingStarted.sln*).</span><span class="sxs-lookup"><span data-stu-id="f33c1-120">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="f33c1-121">Vyberte **Open** (Otevřít).</span><span class="sxs-lookup"><span data-stu-id="f33c1-121">Select **Open**.</span></span>

    2. <span data-ttu-id="f33c1-122">V nabídce **Zobrazení** vyberte **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="f33c1-122">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="f33c1-123">V okně **Průzkumník řešení** vyberte řešení **GettingStarted** (horní uzel) a pak v místní nabídce vyberte **Přidat** > **nový projekt.**</span><span class="sxs-lookup"><span data-stu-id="f33c1-123">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span>

    4. <span data-ttu-id="f33c1-124">V okně **Přidat nový projekt** na levé straně vyberte kategorii Plocha **systému Windows** v části Visual **C#** nebo **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="f33c1-124">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span>

    5. <span data-ttu-id="f33c1-125">Vyberte šablonu **Konzolové aplikace (.NET Framework)** a zadejte Pro **název** *příkaz GettingStartedClient* .</span><span class="sxs-lookup"><span data-stu-id="f33c1-125">Select the **Console App (.NET Framework)** template, and enter *GettingStartedClient* for the **Name**.</span></span> <span data-ttu-id="f33c1-126">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="f33c1-126">Select **OK**.</span></span>

2. <span data-ttu-id="f33c1-127">Přidejte odkaz v projektu **GettingStartedClient** do <xref:System.ServiceModel> sestavení:</span><span class="sxs-lookup"><span data-stu-id="f33c1-127">Add a reference in the **GettingStartedClient** project to the <xref:System.ServiceModel> assembly:</span></span>

    1. <span data-ttu-id="f33c1-128">V okně **Průzkumník řešení** vyberte složku **Reference v** projektu **GettingStartedClient** a pak v místní nabídce vyberte **Přidat odkaz.**</span><span class="sxs-lookup"><span data-stu-id="f33c1-128">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="f33c1-129">V okně **Přidat odkaz** vyberte v části **Sestavení** na levé straně okna **možnost Framework**.</span><span class="sxs-lookup"><span data-stu-id="f33c1-129">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>

    3. <span data-ttu-id="f33c1-130">Najděte a vyberte **System.ServiceModel**a pak zvolte **OK**.</span><span class="sxs-lookup"><span data-stu-id="f33c1-130">Find and select **System.ServiceModel**, and then choose **OK**.</span></span>

    4. <span data-ttu-id="f33c1-131">Uložte řešení výběrem **možnosti Uložit** > **vše**.</span><span class="sxs-lookup"><span data-stu-id="f33c1-131">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="f33c1-132">Přidejte odkaz na službu kalkulačky:</span><span class="sxs-lookup"><span data-stu-id="f33c1-132">Add a service reference to the calculator service:</span></span>

   1. <span data-ttu-id="f33c1-133">V okně **Průzkumník řešení** vyberte složku **Reference v** projektu **GettingStartedClient** a pak v místní nabídce vyberte **Přidat odkaz na službu.**</span><span class="sxs-lookup"><span data-stu-id="f33c1-133">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Service Reference** from the shortcut menu.</span></span>

   2. <span data-ttu-id="f33c1-134">V okně **Přidat odkaz na službu** vyberte **Zjistit**.</span><span class="sxs-lookup"><span data-stu-id="f33c1-134">In the **Add Service Reference** window, select **Discover**.</span></span>

      <span data-ttu-id="f33c1-135">Spustí se služba CalculatorService a Visual Studio ji zobrazí v poli **Služby.**</span><span class="sxs-lookup"><span data-stu-id="f33c1-135">The CalculatorService service starts and Visual Studio displays it in the **Services** box.</span></span>

   3. <span data-ttu-id="f33c1-136">Vyberte **CalculatorService** rozbalit a zobrazit servisní smlouvy implementované službou.</span><span class="sxs-lookup"><span data-stu-id="f33c1-136">Select **CalculatorService** to expand it and display the service contracts implemented by the service.</span></span> <span data-ttu-id="f33c1-137">Ponechte výchozí **obor názvů a** zvolte **OK**.</span><span class="sxs-lookup"><span data-stu-id="f33c1-137">Leave the default **Namespace** and choose **OK**.</span></span>

      <span data-ttu-id="f33c1-138">Visual Studio přidá novou položku do složky **Připojené služby** v projektu **GettingStartedClient.**</span><span class="sxs-lookup"><span data-stu-id="f33c1-138">Visual Studio adds a new item under the **Connected Services** folder in the **GettingStartedClient** project.</span></span>

### <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="f33c1-139">Nástroj metadat ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f33c1-139">ServiceModel Metadata Utility tool</span></span>

<span data-ttu-id="f33c1-140">Následující příklady ukazují, jak volitelně použít [nástroj ServiceModel Metadata Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování souboru třídy proxy.</span><span class="sxs-lookup"><span data-stu-id="f33c1-140">The following examples show how to optionally use the [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy class file.</span></span> <span data-ttu-id="f33c1-141">Tento nástroj generuje soubor třídy proxy a soubor *App.config.*</span><span class="sxs-lookup"><span data-stu-id="f33c1-141">This tool generates the proxy class file and the *App.config* file.</span></span> <span data-ttu-id="f33c1-142">Následující příklady ukazují, jak generovat proxy server v jazyce C# a visual basicu:</span><span class="sxs-lookup"><span data-stu-id="f33c1-142">The following examples show how to generate the proxy in C# and Visual Basic, respectively:</span></span>

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a><span data-ttu-id="f33c1-143">Konfigurační soubor klienta</span><span class="sxs-lookup"><span data-stu-id="f33c1-143">Client configuration file</span></span>

<span data-ttu-id="f33c1-144">Po vytvoření klienta vytvoří Visual Studio konfigurační soubor **App.config** v projektu **GettingStartedClient,** který by měl být podobný následujícímu příkladu:</span><span class="sxs-lookup"><span data-stu-id="f33c1-144">After you've created the client, Visual Studio creates the **App.config** configuration file in the **GettingStartedClient** project, which should be similar to the following example:</span></span>

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

<span data-ttu-id="f33c1-145">V části [ \<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) si všimněte prvku [ \<koncového bodu>.](../configure-apps/file-schema/wcf/endpoint-element.md)</span><span class="sxs-lookup"><span data-stu-id="f33c1-145">Under the [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notice the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="f33c1-146">Prvek \*\* &lt;koncového bodu&gt; \*\* definuje koncový bod, který klient používá pro přístup ke službě takto:</span><span class="sxs-lookup"><span data-stu-id="f33c1-146">The **&lt;endpoint&gt;** element defines the endpoint that the client uses to access the service as follows:</span></span>

- <span data-ttu-id="f33c1-147">Adresa: `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="f33c1-147">Address: `http://localhost:8000/GettingStarted/CalculatorService`.</span></span> <span data-ttu-id="f33c1-148">Adresa koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="f33c1-148">The address of the endpoint.</span></span>
- <span data-ttu-id="f33c1-149">Smlouva o `ServiceReference1.ICalculator`poskytování služeb: .</span><span class="sxs-lookup"><span data-stu-id="f33c1-149">Service contract: `ServiceReference1.ICalculator`.</span></span> <span data-ttu-id="f33c1-150">Servisní smlouva zpracovává komunikaci mezi klientem WCF a službou.</span><span class="sxs-lookup"><span data-stu-id="f33c1-150">The service contract handles communication between the WCF client and the service.</span></span> <span data-ttu-id="f33c1-151">Visual Studio vygenerovalo tuto smlouvu při použití funkce **Přidat odkaz na službu.**</span><span class="sxs-lookup"><span data-stu-id="f33c1-151">Visual Studio generated this contract when you used its **Add Service Reference** function.</span></span> <span data-ttu-id="f33c1-152">Je to v podstatě kopie smlouvy, kterou jste definovali v projektu GettingStartedLib.</span><span class="sxs-lookup"><span data-stu-id="f33c1-152">It's essentially a copy of the contract that you defined in the GettingStartedLib project.</span></span>
- <span data-ttu-id="f33c1-153">Vazba: <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="f33c1-153">Binding: <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="f33c1-154">Vazba určuje protokol HTTP jako přenos, interoperabilní zabezpečení a další podrobnosti o konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="f33c1-154">The binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f33c1-155">Další kroky</span><span class="sxs-lookup"><span data-stu-id="f33c1-155">Next steps</span></span>

<span data-ttu-id="f33c1-156">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="f33c1-156">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="f33c1-157">Vytvořte a nakonfigurujte projekt konzolové aplikace pro klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="f33c1-157">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="f33c1-158">Přidejte odkaz na službu WCF pro generování třídy proxy a konfiguračních souborů pro klientskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f33c1-158">Add a service reference to the WCF service to generate the proxy class and configuration files for the client application.</span></span>

<span data-ttu-id="f33c1-159">Přejdete k dalšímu kurzu, kde se dozvíte, jak používat generovaného klienta.</span><span class="sxs-lookup"><span data-stu-id="f33c1-159">Advance to the next tutorial to learn how to use the generated client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f33c1-160">Kurz: Použití klienta WCF</span><span class="sxs-lookup"><span data-stu-id="f33c1-160">Tutorial: Use a WCF client</span></span>](how-to-use-a-wcf-client.md)
