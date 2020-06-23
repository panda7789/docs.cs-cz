---
title: 'Kurz: Vytvoření klienta Windows Communication Foundation'
description: Naučte se, jak vytvořit klienta načtením metadat ze služby WCF jako součást série článků, které vám pomůžou začít vytvářet aplikace WCF.
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: d5a2a2b5175c9e34eaf1dbaff20ac57f34117c4e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246321"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a><span data-ttu-id="443f4-103">Kurz: Vytvoření klienta Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="443f4-103">Tutorial: Create a Windows Communication Foundation client</span></span>

<span data-ttu-id="443f4-104">Tento kurz popisuje čtvrtý z pěti úkolů potřebných k vytvoření aplikace Basic Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="443f4-104">This tutorial describes the fourth of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="443f4-105">Přehled kurzů najdete v tématu [kurz: Začínáme s Windows Communication Foundation aplikacemi](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="443f4-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="443f4-106">Další úlohou pro vytvoření aplikace WCF je vytvoření klienta načtením metadat ze služby WCF.</span><span class="sxs-lookup"><span data-stu-id="443f4-106">The next task for creating a WCF application is to create a client by retrieving metadata from a WCF service.</span></span> <span data-ttu-id="443f4-107">Pomocí sady Visual Studio můžete přidat odkaz na službu, který získá metadata z koncového bodu služby MEX.</span><span class="sxs-lookup"><span data-stu-id="443f4-107">You use Visual Studio to add a service reference, which gets the metadata from the service’s MEX endpoint.</span></span> <span data-ttu-id="443f4-108">Visual Studio potom vygeneruje spravovaný soubor zdrojového kódu pro proxy klienta v jazyce, který jste zvolili.</span><span class="sxs-lookup"><span data-stu-id="443f4-108">Visual Studio then generates a managed source code file for a client proxy in the language you've chosen.</span></span> <span data-ttu-id="443f4-109">Zároveň vytvoří konfigurační soubor klienta (*App.config*).</span><span class="sxs-lookup"><span data-stu-id="443f4-109">It also creates a client configuration file (*App.config*).</span></span> <span data-ttu-id="443f4-110">Tento soubor umožňuje klientské aplikaci připojit se ke službě na koncovém bodu.</span><span class="sxs-lookup"><span data-stu-id="443f4-110">This file enables the client application to connect to the service at an endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="443f4-111">Pokud voláte službu WCF z projektu knihovny tříd v aplikaci Visual Studio, použijte funkci **Přidat odkaz na službu** k automatickému vygenerování proxy a přidruženého konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="443f4-111">If you call a WCF service from a class library project in Visual Studio, use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="443f4-112">Nicméně vzhledem k tomu, že projekty knihovny tříd nepoužívají tento konfigurační soubor, je nutné přidat nastavení do generovaného konfiguračního souboru do souboru *App.config* pro spustitelný soubor, který volá knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="443f4-112">However, because class library projects don't use this configuration file, you need to add the settings in the generated configuration file to the *App.config* file for the executable that calls the class library.</span></span>

> [!NOTE]
> <span data-ttu-id="443f4-113">K vygenerování třídy proxy a konfiguračního souboru místo sady Visual Studio můžete použít také nástroj pro použití [metadat ServiceModel](#servicemodel-metadata-utility-tool) .</span><span class="sxs-lookup"><span data-stu-id="443f4-113">As an alternative, use the [ServiceModel Metadata Utility tool](#servicemodel-metadata-utility-tool) instead of Visual Studio to generate the proxy class and configuration file.</span></span>

<span data-ttu-id="443f4-114">Klientská aplikace používá vygenerovanou třídu proxy ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="443f4-114">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="443f4-115">Tento postup je popsaný v tématu [kurz: použití klienta](how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="443f4-115">This procedure is described in [Tutorial: Use a client](how-to-use-a-wcf-client.md).</span></span>

<span data-ttu-id="443f4-116">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="443f4-116">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="443f4-117">Vytvořte a nakonfigurujte projekt konzolové aplikace pro klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="443f4-117">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="443f4-118">Přidejte odkaz na službu služby WCF, který vygeneruje proxy třídu a konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="443f4-118">Add a service reference to the WCF service to generate the proxy class and configuration files.</span></span>

## <a name="create-a-windows-communication-foundation-client"></a><span data-ttu-id="443f4-119">Vytvoření klienta Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="443f4-119">Create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="443f4-120">Vytvoření projektu konzolové aplikace v aplikaci Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="443f4-120">Create a console app project in Visual Studio:</span></span>

    1. <span data-ttu-id="443f4-121">V nabídce **soubor** vyberte **otevřít**  >  **projekt/řešení** a přejděte k **soubor GettingStarted** řešení, které jste dříve vytvořili (*soubor GettingStarted. sln*).</span><span class="sxs-lookup"><span data-stu-id="443f4-121">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="443f4-122">Vyberte **Open** (Otevřít).</span><span class="sxs-lookup"><span data-stu-id="443f4-122">Select **Open**.</span></span>

    2. <span data-ttu-id="443f4-123">V nabídce **zobrazení** vyberte **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="443f4-123">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="443f4-124">V okně **Průzkumník řešení** vyberte řešení **soubor GettingStarted** (nejvyšší uzel) a pak v místní nabídce vyberte **Přidat**  >  **Nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="443f4-124">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span>

    4. <span data-ttu-id="443f4-125">V okně **Přidat nový projekt** na levé straně vyberte kategorii **Desktop systému Windows** v části **Visual C#** nebo **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="443f4-125">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span>

    5. <span data-ttu-id="443f4-126">Vyberte šablonu **Konzolová aplikace (.NET Framework)** a jako **název**zadejte *GettingStartedClient* .</span><span class="sxs-lookup"><span data-stu-id="443f4-126">Select the **Console App (.NET Framework)** template, and enter *GettingStartedClient* for the **Name**.</span></span> <span data-ttu-id="443f4-127">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="443f4-127">Select **OK**.</span></span>

2. <span data-ttu-id="443f4-128">Přidejte odkaz do projektu **GettingStartedClient** do <xref:System.ServiceModel> sestavení:</span><span class="sxs-lookup"><span data-stu-id="443f4-128">Add a reference in the **GettingStartedClient** project to the <xref:System.ServiceModel> assembly:</span></span>

    1. <span data-ttu-id="443f4-129">V okně **Průzkumník řešení** vyberte složku **odkazy** v projektu **GettingStartedClient** a pak vyberte **Přidat odkaz** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="443f4-129">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="443f4-130">V okně **Přidat odkaz** v části **sestavení** na levé straně okna vyberte možnost **Architektura**.</span><span class="sxs-lookup"><span data-stu-id="443f4-130">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>

    3. <span data-ttu-id="443f4-131">Vyhledejte a vyberte **System. ServiceModel**a pak zvolte **OK**.</span><span class="sxs-lookup"><span data-stu-id="443f4-131">Find and select **System.ServiceModel**, and then choose **OK**.</span></span>

    4. <span data-ttu-id="443f4-132">Uložte řešení tak, že vyberete **soubor**  >  **Uložit vše**.</span><span class="sxs-lookup"><span data-stu-id="443f4-132">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="443f4-133">Přidejte do služby kalkulačky odkaz na službu:</span><span class="sxs-lookup"><span data-stu-id="443f4-133">Add a service reference to the calculator service:</span></span>

   1. <span data-ttu-id="443f4-134">V okně **Průzkumník řešení** vyberte složku **odkazy** v projektu **GettingStartedClient** a potom v místní nabídce vyberte **Přidat odkaz na službu** .</span><span class="sxs-lookup"><span data-stu-id="443f4-134">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Service Reference** from the shortcut menu.</span></span>

   2. <span data-ttu-id="443f4-135">V okně **Přidat odkaz na službu** vyberte **zjistit**.</span><span class="sxs-lookup"><span data-stu-id="443f4-135">In the **Add Service Reference** window, select **Discover**.</span></span>

      <span data-ttu-id="443f4-136">Služba CalculatorService se spustí a aplikace Visual Studio je zobrazí v poli **služby** .</span><span class="sxs-lookup"><span data-stu-id="443f4-136">The CalculatorService service starts and Visual Studio displays it in the **Services** box.</span></span>

   3. <span data-ttu-id="443f4-137">Vyberte **CalculatorService** a rozbalte ji a zobrazte kontrakty služeb implementované službou.</span><span class="sxs-lookup"><span data-stu-id="443f4-137">Select **CalculatorService** to expand it and display the service contracts implemented by the service.</span></span> <span data-ttu-id="443f4-138">Ponechte výchozí **obor názvů** a klikněte na **tlačítko OK**.</span><span class="sxs-lookup"><span data-stu-id="443f4-138">Leave the default **Namespace** and choose **OK**.</span></span>

      <span data-ttu-id="443f4-139">Visual Studio přidá novou položku do složky **připojené služby** v projektu **GettingStartedClient** .</span><span class="sxs-lookup"><span data-stu-id="443f4-139">Visual Studio adds a new item under the **Connected Services** folder in the **GettingStartedClient** project.</span></span>

### <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="443f4-140">Nástroj pro metadata ServiceModel</span><span class="sxs-lookup"><span data-stu-id="443f4-140">ServiceModel Metadata Utility tool</span></span>

<span data-ttu-id="443f4-141">V následujících příkladech se dozvíte, jak volitelně pomocí nástroje pro generování [metadat třídy ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) vytvořit soubor třídy proxy.</span><span class="sxs-lookup"><span data-stu-id="443f4-141">The following examples show how to optionally use the [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy class file.</span></span> <span data-ttu-id="443f4-142">Tento nástroj generuje soubor třídy proxy a soubor *App.config* .</span><span class="sxs-lookup"><span data-stu-id="443f4-142">This tool generates the proxy class file and the *App.config* file.</span></span> <span data-ttu-id="443f4-143">Následující příklady ukazují, jak vygenerovat proxy v jazyce C# a Visual Basic v uvedeném pořadí:</span><span class="sxs-lookup"><span data-stu-id="443f4-143">The following examples show how to generate the proxy in C# and Visual Basic, respectively:</span></span>

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a><span data-ttu-id="443f4-144">Konfigurační soubor klienta</span><span class="sxs-lookup"><span data-stu-id="443f4-144">Client configuration file</span></span>

<span data-ttu-id="443f4-145">Po vytvoření klienta Visual Studio vytvoří konfigurační soubor **App.config** v projektu **GettingStartedClient** , který by měl být podobný následujícímu příkladu:</span><span class="sxs-lookup"><span data-stu-id="443f4-145">After you've created the client, Visual Studio creates the **App.config** configuration file in the **GettingStartedClient** project, which should be similar to the following example:</span></span>

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

<span data-ttu-id="443f4-146">V [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) části si všimněte [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="443f4-146">Under the [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notice the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="443f4-147">Element \*\* &lt; Endpoint &gt; \*\* definuje koncový bod, který klient používá pro přístup ke službě, následovně:</span><span class="sxs-lookup"><span data-stu-id="443f4-147">The **&lt;endpoint&gt;** element defines the endpoint that the client uses to access the service as follows:</span></span>

- <span data-ttu-id="443f4-148">Adresa: `http://localhost:8000/GettingStarted/CalculatorService` .</span><span class="sxs-lookup"><span data-stu-id="443f4-148">Address: `http://localhost:8000/GettingStarted/CalculatorService`.</span></span> <span data-ttu-id="443f4-149">Adresa koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="443f4-149">The address of the endpoint.</span></span>
- <span data-ttu-id="443f4-150">Kontrakt služby: `ServiceReference1.ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="443f4-150">Service contract: `ServiceReference1.ICalculator`.</span></span> <span data-ttu-id="443f4-151">Kontrakt služby zajišťuje komunikaci mezi klientem WCF a službou.</span><span class="sxs-lookup"><span data-stu-id="443f4-151">The service contract handles communication between the WCF client and the service.</span></span> <span data-ttu-id="443f4-152">Aplikace Visual Studio vygenerovala tento kontrakt při použití funkce **Přidat odkaz na službu** .</span><span class="sxs-lookup"><span data-stu-id="443f4-152">Visual Studio generated this contract when you used its **Add Service Reference** function.</span></span> <span data-ttu-id="443f4-153">Je v podstatě kopie smlouvy, kterou jste definovali v projektu GettingStartedLib.</span><span class="sxs-lookup"><span data-stu-id="443f4-153">It's essentially a copy of the contract that you defined in the GettingStartedLib project.</span></span>
- <span data-ttu-id="443f4-154">Vazba: <xref:System.ServiceModel.WSHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="443f4-154">Binding: <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="443f4-155">Vazba určí protokol HTTP jako přenos, prointeroperabilní zabezpečení a další podrobnosti o konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="443f4-155">The binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="443f4-156">Další kroky</span><span class="sxs-lookup"><span data-stu-id="443f4-156">Next steps</span></span>

<span data-ttu-id="443f4-157">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="443f4-157">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="443f4-158">Vytvořte a nakonfigurujte projekt konzolové aplikace pro klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="443f4-158">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="443f4-159">Přidejte odkaz na službu služby WCF, který vygeneruje proxy třídu a konfigurační soubory pro klientskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="443f4-159">Add a service reference to the WCF service to generate the proxy class and configuration files for the client application.</span></span>

<span data-ttu-id="443f4-160">Přejděte k dalšímu kurzu, kde se dozvíte, jak používat vygenerovaný klient.</span><span class="sxs-lookup"><span data-stu-id="443f4-160">Advance to the next tutorial to learn how to use the generated client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="443f4-161">Kurz: použití klienta WCF</span><span class="sxs-lookup"><span data-stu-id="443f4-161">Tutorial: Use a WCF client</span></span>](how-to-use-a-wcf-client.md)
