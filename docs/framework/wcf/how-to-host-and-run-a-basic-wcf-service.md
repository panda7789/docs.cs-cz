---
title: 'Postupy: Hostování a spuštění základní služby Windows Communication Foundation Service'
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a13e5a0044c51700acce6b123688868443f635ae
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="10f5e-102">Postupy: Hostování a spuštění základní služby Windows Communication Foundation Service</span><span class="sxs-lookup"><span data-stu-id="10f5e-102">How to: Host and Run a Basic Windows Communication Foundation Service</span></span>
<span data-ttu-id="10f5e-103">Toto je třetí šesti úlohy, které jsou nutné k vytváření [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="10f5e-103">This is the third of six tasks required to create a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="10f5e-104">Přehled všech šest úloh najdete v tématu [kurzu Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="10f5e-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="10f5e-105">Toto téma popisuje, jak hostovat [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] službu v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="10f5e-105">This topic describes how to host a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service in a console application.</span></span> <span data-ttu-id="10f5e-106">Tento postup se skládá z následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="10f5e-106">This procedure consists of the following steps:</span></span>  
  
-   <span data-ttu-id="10f5e-107">Vytvoření projektu konzolové aplikace k hostování služby.</span><span class="sxs-lookup"><span data-stu-id="10f5e-107">Create a console application project to host the service.</span></span>  
  
-   <span data-ttu-id="10f5e-108">Vytvořte hostitele služby pro službu.</span><span class="sxs-lookup"><span data-stu-id="10f5e-108">Create a service host for the service.</span></span>  
  
-   <span data-ttu-id="10f5e-109">Povolte metadata exchange.</span><span class="sxs-lookup"><span data-stu-id="10f5e-109">Enable metadata exchange.</span></span>  
  
-   <span data-ttu-id="10f5e-110">Otevření hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="10f5e-110">Open the service host.</span></span>  
  
 <span data-ttu-id="10f5e-111">Úplný kód napsaný v této úloze najdete v příkladu za postupem.</span><span class="sxs-lookup"><span data-stu-id="10f5e-111">A complete listing of the code written in this task is provided in the example following the procedure.</span></span>  
  
## <a name="to-create-a-new-console-application-to-host-the-service"></a><span data-ttu-id="10f5e-112">Chcete-li vytvořit novou konzolovou aplikaci k hostování služby</span><span class="sxs-lookup"><span data-stu-id="10f5e-112">To create a new console application to host the service</span></span>  
  
1.  <span data-ttu-id="10f5e-113">Vytvořte nový projekt konzolové aplikace kliknutím pravým tlačítkem na řešení Začínáme vyberete, **přidat**, **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="10f5e-113">Create a new Console Application project by right-clicking on the Getting Started solution, selecting, **Add**, **New Project**.</span></span> <span data-ttu-id="10f5e-114">V **přidat nový projekt** dialog v dialogovém okně vyberte na levé straně **Windows** pod **C#** nebo **VB**.</span><span class="sxs-lookup"><span data-stu-id="10f5e-114">In the **Add New Project** dialog on the left hand side of the dialog select **Windows** under **C#** or **VB**.</span></span> <span data-ttu-id="10f5e-115">V části center dialogového okna Vybrat **konzolové aplikace**.</span><span class="sxs-lookup"><span data-stu-id="10f5e-115">In the center section of the dialog select **Console Application**.</span></span> <span data-ttu-id="10f5e-116">Název projektu GettingStartedHost.</span><span class="sxs-lookup"><span data-stu-id="10f5e-116">Name the project GettingStartedHost.</span></span>  
  
2.  <span data-ttu-id="10f5e-117">Nastavte cílový framework projektu GettingStartedHost na rozhraní .NET Framework 4.5 kliknutím pravým tlačítkem na **GettingStartedHost** v Průzkumníku řešení a výběrem **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="10f5e-117">Set the target framework of the GettingStartedHost project to .NET Framework 4.5 by right clicking on **GettingStartedHost** in the Solution Explorer and selecting **Properties**.</span></span> <span data-ttu-id="10f5e-118">Rozevírací pole s popiskem **cílové rozhraní** vyberte **rozhraní .NET Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="10f5e-118">In the dropdown box labeled **Target Framework** select **.NET Framework 4.5**.</span></span> <span data-ttu-id="10f5e-119">Nastavení cílové rozhraní projektu jazyka Visual Basic je mírně liší v dialogovém okně Vlastnosti projektu GettingStartedHost, klikněte na tlačítko **zkompilovat** na levé straně obrazovky a pak klikněte **Advanced kompilace Možnosti** tlačítko v levém dolním rohu dialogu.</span><span class="sxs-lookup"><span data-stu-id="10f5e-119">Setting the target framework for a VB project is a little different, in the GettingStartedHost project properties dialog, click the **Compile** tab on the left-hand side of the screen, and then click the **Advanced Compile Options** button at the lower left-hand corner of the dialog.</span></span> <span data-ttu-id="10f5e-120">Potom vyberte **rozhraní .NET Framework 4.5** rozevírací pole s popiskem **cílové rozhraní**.</span><span class="sxs-lookup"><span data-stu-id="10f5e-120">Then select **.NET Framework 4.5** in the dropdown box labeled **Target Framework**.</span></span>  
  
     <span data-ttu-id="10f5e-121">Nastavení způsobí, že cílový framework [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] Pokud chcete znovu načíst řešení, stiskněte **OK** po zobrazení výzvy.</span><span class="sxs-lookup"><span data-stu-id="10f5e-121">Setting the target framework will cause [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] to reload the solution, press **OK** when prompted.</span></span>  
  
3.  <span data-ttu-id="10f5e-122">Přidat odkaz na projekt GettingStartedLib do projektu GettingStartedHost kliknutím pravým tlačítkem na **odkazy** ve složce projektu GettingStartedHost v Průzkumníku řešení a vyberte **přidání odkazu** .</span><span class="sxs-lookup"><span data-stu-id="10f5e-122">Add a reference to the GettingStartedLib project to the GettingStartedHost project by right clicking on the **References** folder under the GettingStartedHost project in the solution explorer and select **Add Reference**.</span></span> <span data-ttu-id="10f5e-123">V **přidat odkaz na** dialogovém okně, vyberte **řešení** na levé straně dialogové okno a vyberte GettingStartedLib v části center dialogové okno a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="10f5e-123">In the **Add Reference** dialog, select **Solution** on the left-hand side of the dialog and select GettingStartedLib in the center section of the dialog and click **Add**.</span></span> <span data-ttu-id="10f5e-124">Díky tomu typy definované v GettingStartedLib GettingStartedHost projektu k dispozici.</span><span class="sxs-lookup"><span data-stu-id="10f5e-124">This makes the types defined in GettingStartedLib available to the GettingStartedHost project.</span></span>  
  
4.  <span data-ttu-id="10f5e-125">Přidat odkaz na System.ServiceModel do projektu GettingStartedHost kliknutím pravým tlačítkem myši **odkaz** ve složce projektu GettingStartedHost v Průzkumníku řešení a vyberte **přidat** Odkaz.</span><span class="sxs-lookup"><span data-stu-id="10f5e-125">Add a reference to System.ServiceModel to the GettingStartedHost project by right-clicking the **Reference** folder under the GettingStartedHost project in Solution Explorer and select **Add** Reference.</span></span> <span data-ttu-id="10f5e-126">V **přidat odkaz na** dialogovém okně vyberte **Framework** na levé straně dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="10f5e-126">In the **Add Reference** dialog select **Framework** on the left-hand side of the dialog.</span></span> <span data-ttu-id="10f5e-127">Zadejte do textového pole hledání sestavení v `System.ServiceModel`.</span><span class="sxs-lookup"><span data-stu-id="10f5e-127">In the Search Assemblies textbox, type in `System.ServiceModel`.</span></span> <span data-ttu-id="10f5e-128">V části center dialogového okna Vybrat **System.ServiceModel**, klikněte na tlačítko **přidat** tlačítko a klikněte na tlačítko **Zavřít** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="10f5e-128">In the center section of the dialog select **System.ServiceModel**, click the **Add** button, and click the **Close** button.</span></span> <span data-ttu-id="10f5e-129">Řešení uložte kliknutím na tlačítko Uložit vše v hlavní nabídce.</span><span class="sxs-lookup"><span data-stu-id="10f5e-129">Save the solution by clicking the Save All button below the main menu.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="10f5e-130">K hostování služby</span><span class="sxs-lookup"><span data-stu-id="10f5e-130">To host the service</span></span>  
  
-   <span data-ttu-id="10f5e-131">Otevřete soubor Program.cs nebo Module.vb a zadejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="10f5e-131">Open the Program.cs or Module.vb file and enter the following code:</span></span>  
  
    ```csharp
    // program.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.ServiceModel;  
    using GettingStartedLib;  
    using System.ServiceModel.Description;   
  
    namespace GettingStartedHost  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                // Step 1 Create a URI to serve as the base address.  
                Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");  
  
                // Step 2 Create a ServiceHost instance  
                ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
  
                try  
                {  
                    // Step 3 Add a service endpoint.  
                    selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");  
  
                    // Step 4 Enable metadata exchange.  
                    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
                    smb.HttpGetEnabled = true;  
                    selfHost.Description.Behaviors.Add(smb);  
  
                    // Step 5 Start the service.  
                    selfHost.Open();  
                    Console.WriteLine("The service is ready.");  
                    Console.WriteLine("Press <ENTER> to terminate service.");  
                    Console.WriteLine();  
                    Console.ReadLine();  
  
                    // Close the ServiceHostBase to shutdown the service.  
                    selfHost.Close();  
                }  
                catch (CommunicationException ce)  
                {  
                    Console.WriteLine("An exception occurred: {0}", ce.Message);  
                    selfHost.Abort();  
                }  
            }  
        }  
    }  
    ```  
  
    ```vb
    'Module1.vb  
    Imports System  
    Imports System.ServiceModel  
    Imports System.ServiceModel.Description  
    Imports GettingStartedLibVB.GettingStartedLib  
  
    Module Service  
  
        Class Program  
            Shared Sub Main()  
                ' Step 1 Create a URI to serve as the base address  
                Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")  
  
                ' Step 2 Create a ServiceHost instance  
                Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)  
                Try  
  
                    ' Step 3 Add a service endpoint  
                    ' Add a service endpoint  
                    selfHost.AddServiceEndpoint( _  
                        GetType(ICalculator), _  
                        New WSHttpBinding(), _  
                        "CalculatorService")  
  
                    ' Step 4 Enable metadata exchange.  
                    Dim smb As New ServiceMetadataBehavior()  
                    smb.HttpGetEnabled = True  
                    selfHost.Description.Behaviors.Add(smb)  
  
                    ' Step 5 Start the service  
                    selfHost.Open()  
                    Console.WriteLine("The service is ready.")  
                    Console.WriteLine("Press <ENTER> to terminate service.")  
                    Console.WriteLine()  
                    Console.ReadLine()  
  
                    ' Close the ServiceHostBase to shutdown the service.  
                    selfHost.Close()  
                Catch ce As CommunicationException  
                    Console.WriteLine("An exception occurred: {0}", ce.Message)  
                    selfHost.Abort()  
                End Try  
            End Sub  
        End Class  
  
    End Module  
    ```  
  
    1.  <span data-ttu-id="10f5e-132">Krok 1 – vytvoří instanci třídy identifikátor Uri pro uložení základní adresa služby.</span><span class="sxs-lookup"><span data-stu-id="10f5e-132">Step 1 - Creates an instance of the Uri class to hold the base address of the service.</span></span> <span data-ttu-id="10f5e-133">Služby jsou označeny adresy URL, která obsahuje základní adresu a volitelné identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="10f5e-133">Services are identified by a URL which contains a base address and an optional URI.</span></span> <span data-ttu-id="10f5e-134">Základní adresa je naformátován takto: [přenosu] :// [název počítače nebo domény] [: volitelný port #] nebo [volitelné segment identifikátoru URI] přenos HTTP používá základní adresu pro službu kalkulačky, localhost, port 8000 a identifikátor URI segmentovat "GettingStarted"</span><span class="sxs-lookup"><span data-stu-id="10f5e-134">The base address is formatted as follows:[transport]://[machine-name or domain][:optional port #]/[optional URI segment]The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment "GettingStarted"</span></span>  
  
    2.  <span data-ttu-id="10f5e-135">Krok 2 – vytvoří instanci <xref:System.ServiceModel.ServiceHost> třída k hostování služby.</span><span class="sxs-lookup"><span data-stu-id="10f5e-135">Step 2 – Creates an instance of the <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="10f5e-136">Konstruktor přebírá dva parametry, typu třídy, která implementuje kontrakt služby a základní adresa služby.</span><span class="sxs-lookup"><span data-stu-id="10f5e-136">The constructor takes two parameters, the type of the class that implements the service contract, and the base address of the service.</span></span>  
  
    3.  <span data-ttu-id="10f5e-137">Krok 3 – vytvoří <!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint` instance.</span><span class="sxs-lookup"><span data-stu-id="10f5e-137">Step 3 – Creates a <!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint` instance.</span></span> <span data-ttu-id="10f5e-138">Koncový bod služby se skládá z adresy, vazby a kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="10f5e-138">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="10f5e-139"><!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint` Konstruktor proto trvá typ rozhraní kontraktu služby, vazbu a adresu.</span><span class="sxs-lookup"><span data-stu-id="10f5e-139">The <!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint`  constructor therefore takes the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="10f5e-140">Kontrakt služby je `ICalculator`, která definované a implementovat typ služby.</span><span class="sxs-lookup"><span data-stu-id="10f5e-140">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="10f5e-141">Vazba použitá v této ukázce je <xref:System.ServiceModel.WSHttpBinding> tedy předdefinované vazbu, která se používá pro připojení ke koncovým bodům, které odpovídají WS-\* specifikace.</span><span class="sxs-lookup"><span data-stu-id="10f5e-141">The binding used in this sample is <xref:System.ServiceModel.WSHttpBinding> which is a built-in binding that is used for connecting to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="10f5e-142">Další informace o vazby WCF najdete v tématu [vazby WCF – přehled](../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="10f5e-142">For more information about WCF bindings, see [WCF Bindings Overview](../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="10f5e-143">Adresa se připojuje k základní adresu k identifikaci koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="10f5e-143">The address is appended to the base address to identify the endpoint.</span></span> <span data-ttu-id="10f5e-144">Zadaná adresa v tento kód je "CalculatorService" plně kvalifikovanou adresu pro koncový bod je `"http://localhost:8000/GettingStarted/CalculatorService"` přidání koncového bodu služby je volitelný při použití rozhraní .NET Framework 4.0 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="10f5e-144">The address specified in this code is "CalculatorService" so the fully qualified address for the endpoint is `"http://localhost:8000/GettingStarted/CalculatorService"` Adding a service endpoint is optional when using .NET Framework 4.0 or later.</span></span> <span data-ttu-id="10f5e-145">V těchto verzích Pokud žádné koncové body se přidají kódu nebo konfigurace, WCF přidá jeden výchozí koncový bod pro každou kombinaci základní adresa a kontrakt implementované službu.</span><span class="sxs-lookup"><span data-stu-id="10f5e-145">In these versions, if no endpoints are added in code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="10f5e-146">Další informace o výchozím nastavení najdete v části koncové body [zadání adresy koncového bodu](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="10f5e-146">For more information about default endpoints see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="10f5e-147"> výchozí koncové body, vazby a chování, viz [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="10f5e-147"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="10f5e-148">Přidání koncového bodu služby je volitelný při použití rozhraní .NET Framework 4 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="10f5e-148">Adding a service endpoint is optional when using .NET Framework 4 or later.</span></span> <span data-ttu-id="10f5e-149">V těchto verzích Pokud žádné koncové body se přidají kódu nebo konfigurace, WCF přidá jeden výchozí koncový bod pro každou kombinaci základní adresa a kontrakt implementované službu.</span><span class="sxs-lookup"><span data-stu-id="10f5e-149">In these versions, if no endpoints are added in code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="10f5e-150">Další informace o výchozím nastavení najdete v části koncové body [zadání adresy koncového bodu](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="10f5e-150">For more information about default endpoints see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="10f5e-151"> výchozí koncové body, vazby a chování, viz [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="10f5e-151"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
    4.  <span data-ttu-id="10f5e-152">Krok 4 – povolení metadata exchange.</span><span class="sxs-lookup"><span data-stu-id="10f5e-152">Step 4 – Enable metadata exchange.</span></span> <span data-ttu-id="10f5e-153">Metadata exchange budou klienti používat ke generování proxy servery, které se použije k volání operací služby.</span><span class="sxs-lookup"><span data-stu-id="10f5e-153">Clients will use metadata exchange to generate proxies that will be used to call the service operations.</span></span> <span data-ttu-id="10f5e-154">Povolit vytvořit metadata exchange <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, nastavte ji na <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> vlastnost `true`a přidejte požadované chování, <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  --> `System.ServiceModel.ServiceHost.Behaviors%2A` kolekce <xref:System.ServiceModel.ServiceHost> instance.</span><span class="sxs-lookup"><span data-stu-id="10f5e-154">To enable metadata exchange create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set it’s <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, and add the behavior to the <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A` collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>  
  
    5.  <span data-ttu-id="10f5e-155">Krok 5 – otevřete <xref:System.ServiceModel.ServiceHost> přijímat příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="10f5e-155">Step 5 – Open the <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="10f5e-156">Zadejte oznámení, které kód čeká uživatelem.</span><span class="sxs-lookup"><span data-stu-id="10f5e-156">Notice the code waits for the user to hit enter.</span></span> <span data-ttu-id="10f5e-157">Pokud není to uděláte, aplikace bude okamžitě ukončena a služba bude vypnuta. Také oznámení používá blok try/catch.</span><span class="sxs-lookup"><span data-stu-id="10f5e-157">If you do not do this, the app will close immediately and the service will shut down.Also notice a  try/catch block used.</span></span> <span data-ttu-id="10f5e-158">Po <xref:System.ServiceModel.ServiceHost> byla vytvořena instance, jiný kód je umístěn v bloku try/catch.</span><span class="sxs-lookup"><span data-stu-id="10f5e-158">After the <xref:System.ServiceModel.ServiceHost> has been instantiated, all other code is placed in a try/catch block.</span></span> <span data-ttu-id="10f5e-159">Další informace o bezpečně zachytávání výjimek vyvolaných <xref:System.ServiceModel.ServiceHost>, najdete v části [vyhnout problémům s příkazem Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)</span><span class="sxs-lookup"><span data-stu-id="10f5e-159">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Avoiding Problems with the Using Statement](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)</span></span>  
  
### <a name="to-verify-the-service-is-working"></a><span data-ttu-id="10f5e-160">Chcete-li ověřit, že služba funguje</span><span class="sxs-lookup"><span data-stu-id="10f5e-160">To verify the service is working</span></span>  
  
1.  <span data-ttu-id="10f5e-161">Spusťte konzolovou aplikaci GettingStartedHost z uvnitř [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="10f5e-161">Run the GettingStartedHost console application from inside [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span> <span data-ttu-id="10f5e-162">Při spuštění [!INCLUDE[wv](../../../includes/wv-md.md)] a novějších operačních systémech, služba musí být spuštěn s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="10f5e-162">When running on [!INCLUDE[wv](../../../includes/wv-md.md)] and later operating systems, the service must be run with administrator privileges.</span></span> <span data-ttu-id="10f5e-163">Protože Visual Studio byla spuštěna s oprávněními správce, GettingStartedHost je také spouštět s oprávněním správce.</span><span class="sxs-lookup"><span data-stu-id="10f5e-163">Because Visual Studio was run with Administrator privileges, GettingStartedHost is also run with Administrator privileges.</span></span> <span data-ttu-id="10f5e-164">Můžete také otevřete nový příkazový řádek s oprávněními správce a spusťte service.exe v něm.</span><span class="sxs-lookup"><span data-stu-id="10f5e-164">You can also start a new command prompt running it with Administrator privileges and run service.exe within it.</span></span>  
  
2.  <span data-ttu-id="10f5e-165">Otevřete Internet Explorer a přejděte k ladění služby stránky v `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="10f5e-165">Open Internet Explorer and browse to the service's debug page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10f5e-166">Příklad</span><span class="sxs-lookup"><span data-stu-id="10f5e-166">Example</span></span>  
 <span data-ttu-id="10f5e-167">Následující příklad obsahuje kontrakt služby a implementaci z předchozích kroků tohoto kurzu a hostuje službu v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="10f5e-167">The following example includes the service contract and implementation from previous steps in the tutorial and hosts the service in a console application.</span></span>  
  
 <span data-ttu-id="10f5e-168">To zkompilovat pomocí příkazového řádku kompilátoru, kompilována IService1.cs a Service1.cs knihovny tříd odkazující na `System.ServiceModel.dll`.</span><span class="sxs-lookup"><span data-stu-id="10f5e-168">To compile this with a command-line compiler, compile IService1.cs and Service1.cs into a class library referencing `System.ServiceModel.dll`.</span></span> <span data-ttu-id="10f5e-169">A kompilaci souboru Program.cs do konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="10f5e-169">And compile Program.cs to a console application.</span></span>  
  
```csharp
// IService1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
namespace GettingStartedLib  
{  
        [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
        public interface ICalculator  
        {  
            [OperationContract]  
            double Add(double n1, double n2);  
            [OperationContract]  
            double Subtract(double n1, double n2);  
            [OperationContract]  
            double Multiply(double n1, double n2);  
            [OperationContract]  
            double Divide(double n1, double n2);  
        }  
}  
```  
  
```csharp
// Service1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
namespace GettingStartedLib  
{  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            double result = n1 + n2;  
            Console.WriteLine("Received Add({0},{1})", n1, n2);  
            // Code added to write output to the console window.  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Subtract(double n1, double n2)  
        {  
            double result = n1 - n2;  
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Multiply(double n1, double n2)  
        {  
            double result = n1 * n2;  
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Divide(double n1, double n2)  
        {  
            double result = n1 / n2;  
            Console.WriteLine("Received Divide({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
    }  
}  
```  
  
```csharp
//Program.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel;  
using GettingStartedLib;  
using System.ServiceModel.Description;   
  
namespace GettingStartedHost  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Step 1 of the address configuration procedure: Create a URI to serve as the base address.  
            Uri baseAddress = new Uri("http://localhost:8000/ServiceModelSamples/Service");  
  
            // Step 2 of the hosting procedure: Create ServiceHost  
            ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
  
            try  
            {  
                // Step 3 of the hosting procedure: Add a service endpoint.  
                selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");  
  
                // Step 4 of the hosting procedure: Enable metadata exchange.  
                ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
                smb.HttpGetEnabled = true;  
                selfHost.Description.Behaviors.Add(smb);  
  
                // Step 5 of the hosting procedure: Start (and then stop) the service.  
                selfHost.Open();  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                selfHost.Close();  
            }  
            catch (CommunicationException ce)  
            {  
                Console.WriteLine("An exception occurred: {0}", ce.Message);  
                selfHost.Abort();  
            }  
        }  
    }  
}  
```  
  
```vb
'IService1.vb  
Imports System  
Imports System.ServiceModel  
  
Namespace GettingStartedLib  
  
    <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _  
    Public Interface ICalculator  
  
        <OperationContract()> _  
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double  
    End Interface  
End Namespace  
```  
  
```vb
'Service1.vb  
Imports System  
Imports System.ServiceModel  
  
Namespace GettingStartedLib  
  
    Public Class CalculatorService  
        Implements ICalculator  
  
        Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add  
            Dim result As Double = n1 + n2  
            ' Code added to write output to the console window.  
            Console.WriteLine("Received Add({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
        End Function  
  
        Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract  
            Dim result As Double = n1 - n2  
            Console.WriteLine("Received Subtract({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
  
        Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply  
            Dim result As Double = n1 * n2  
            Console.WriteLine("Received Multiply({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
  
        Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide  
            Dim result As Double = n1 / n2  
            Console.WriteLine("Received Divide({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
    End Class  
End Namespace  
```  
  
```vb
'Module1.vb  
Imports System  
Imports System.ServiceModel  
Imports System.ServiceModel.Description  
Imports GettingStartedLibVB.GettingStartedLib  
  
Module Service  
  
    Class Program  
        Shared Sub Main()  
            ' Step 1 of the address configuration procedure: Create a URI to serve as the base address.  
            Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")  
  
            ' Step 2 of the hosting procedure: Create ServiceHost  
            Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)  
            Try  
  
                ' Step 3 of the hosting procedure: Add a service endpoint.  
                ' Add a service endpoint  
                selfHost.AddServiceEndpoint( _  
                    GetType(ICalculator), _  
                    New WSHttpBinding(), _  
                    "CalculatorService")  
  
                ' Step 4 of the hosting procedure: Enable metadata exchange.  
                ' Enable metadata exchange  
                Dim smb As New ServiceMetadataBehavior()  
                smb.HttpGetEnabled = True  
                selfHost.Description.Behaviors.Add(smb)  
  
                ' Step 5 of the hosting procedure: Start (and then stop) the service.  
                selfHost.Open()  
                Console.WriteLine("The service is ready.")  
                Console.WriteLine("Press <ENTER> to terminate service.")  
                Console.WriteLine()  
                Console.ReadLine()  
  
                ' Close the ServiceHostBase to shutdown the service.  
                selfHost.Close()  
            Catch ce As CommunicationException  
                Console.WriteLine("An exception occurred: {0}", ce.Message)  
                selfHost.Abort()  
            End Try  
        End Sub  
    End Class  
  
End Module  
```  
  
> [!NOTE]
>  <span data-ttu-id="10f5e-170">Služby, jako je tento vyžadují oprávnění k registraci adresy protokolu HTTP na počítači pro naslouchání.</span><span class="sxs-lookup"><span data-stu-id="10f5e-170">Services such as this one require permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="10f5e-171">Toto oprávnění mají účty správců, ale není správcem účty je potřeba udělit oprávnění pro obory názvů HTTP.</span><span class="sxs-lookup"><span data-stu-id="10f5e-171">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="10f5e-172"> Postup konfigurace oboru názvů rezervace najdete v tématu [konfigurace HTTP a HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="10f5e-172"> how to configure namespace reservations, see [Configuring HTTP and HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="10f5e-173">Při spuštění v sadě Visual Studio, musí být service.exe spuštěn s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="10f5e-173">When running under Visual Studio, the service.exe must be run with administrator privileges.</span></span>  
  
 <span data-ttu-id="10f5e-174">Nyní je služba spuštěná.</span><span class="sxs-lookup"><span data-stu-id="10f5e-174">Now the service is running.</span></span> <span data-ttu-id="10f5e-175">Pokračujte [postupy: vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="10f5e-175">Proceed to [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="10f5e-176">Informace o odstraňování potíží, najdete v části [řešení potíží s kurzu Začínáme](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="10f5e-176">For troubleshooting information, see [Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10f5e-177">Viz také</span><span class="sxs-lookup"><span data-stu-id="10f5e-177">See Also</span></span>  
 [<span data-ttu-id="10f5e-178">Začínáme</span><span class="sxs-lookup"><span data-stu-id="10f5e-178">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="10f5e-179">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="10f5e-179">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
