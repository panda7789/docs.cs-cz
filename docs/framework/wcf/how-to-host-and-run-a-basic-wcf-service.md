---
title: 'Postupy: Hostování a spuštění základní služby Windows Communication Foundation Service'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: e2bf16bd07c7ac9d918a4ae95d7f4aa185d436ec
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2018
ms.locfileid: "44227178"
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="bf08b-102">Postupy: Hostování a spuštění základní služby Windows Communication Foundation Service</span><span class="sxs-lookup"><span data-stu-id="bf08b-102">How to: Host and Run a Basic Windows Communication Foundation Service</span></span>
<span data-ttu-id="bf08b-103">Toto je třetí webinář z šesti úkolů potřebný k vytvoření aplikace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="bf08b-103">This is the third of six tasks required to create a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="bf08b-104">Přehled všech šesti úkoly, naleznete v tématu [kurz Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="bf08b-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="bf08b-105">Toto téma popisuje, jak k hostování služby Windows Communication Foundation (WCF) v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bf08b-105">This topic describes how to host a Windows Communication Foundation (WCF) service in a console application.</span></span> <span data-ttu-id="bf08b-106">Tento postup se skládá z následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="bf08b-106">This procedure consists of the following steps:</span></span>  
  
-   <span data-ttu-id="bf08b-107">Vytvořte projekt konzolové aplikace pro hostování služby.</span><span class="sxs-lookup"><span data-stu-id="bf08b-107">Create a console application project to host the service.</span></span>  
  
-   <span data-ttu-id="bf08b-108">Vytvořte hostitelskou služby pro službu.</span><span class="sxs-lookup"><span data-stu-id="bf08b-108">Create a service host for the service.</span></span>  
  
-   <span data-ttu-id="bf08b-109">Povolte výměny metadat.</span><span class="sxs-lookup"><span data-stu-id="bf08b-109">Enable metadata exchange.</span></span>  
  
-   <span data-ttu-id="bf08b-110">Otevření hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="bf08b-110">Open the service host.</span></span>  
  
 <span data-ttu-id="bf08b-111">Úplný kód napsaný v této úloze je najdete v příkladu za postupem.</span><span class="sxs-lookup"><span data-stu-id="bf08b-111">A complete listing of the code written in this task is provided in the example following the procedure.</span></span>  
  
## <a name="to-create-a-new-console-application-to-host-the-service"></a><span data-ttu-id="bf08b-112">Vytvořte novou konzolovou aplikaci pro hostování služby</span><span class="sxs-lookup"><span data-stu-id="bf08b-112">To create a new console application to host the service</span></span>  
  
1.  <span data-ttu-id="bf08b-113">Vytvořte nový projekt konzolové aplikace kliknutím pravým tlačítkem na řešení Začínáme vyberete, **přidat**, **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="bf08b-113">Create a new Console Application project by right-clicking on the Getting Started solution, selecting, **Add**, **New Project**.</span></span> <span data-ttu-id="bf08b-114">V **přidat nový projekt** dialogového okna na levé straně dialogového okna vyberte **Windows** pod **jazyka C#** nebo **VB**.</span><span class="sxs-lookup"><span data-stu-id="bf08b-114">In the **Add New Project** dialog on the left hand side of the dialog select **Windows** under **C#** or **VB**.</span></span> <span data-ttu-id="bf08b-115">V části System center dialogového okna vyberte **konzolovou aplikaci**.</span><span class="sxs-lookup"><span data-stu-id="bf08b-115">In the center section of the dialog select **Console Application**.</span></span> <span data-ttu-id="bf08b-116">Pojmenujte projekt GettingStartedHost.</span><span class="sxs-lookup"><span data-stu-id="bf08b-116">Name the project GettingStartedHost.</span></span>  
  
2.  <span data-ttu-id="bf08b-117">Nastavte cílovou architekturu projektu GettingStartedHost na rozhraní .NET Framework 4.5 kliknutím pravým tlačítkem na **GettingStartedHost** v Průzkumníku řešení a vyberete **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="bf08b-117">Set the target framework of the GettingStartedHost project to .NET Framework 4.5 by right clicking on **GettingStartedHost** in the Solution Explorer and selecting **Properties**.</span></span> <span data-ttu-id="bf08b-118">V rozevíracím seznamu s názvem **Cílová architektura** vyberte **rozhraní .NET Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="bf08b-118">In the dropdown box labeled **Target Framework** select **.NET Framework 4.5**.</span></span> <span data-ttu-id="bf08b-119">Nastavení cílové rozhraní projektu VB je trochu jiné, v dialogovém okně Vlastnosti projektu GettingStartedHost, klikněte na tlačítko **kompilaci** kartu na levé straně obrazovky a pak klikněte na tlačítko **rozšířené kompilace Možnosti** tlačítko v levém dolním rohu dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="bf08b-119">Setting the target framework for a VB project is a little different, in the GettingStartedHost project properties dialog, click the **Compile** tab on the left-hand side of the screen, and then click the **Advanced Compile Options** button at the lower left-hand corner of the dialog.</span></span> <span data-ttu-id="bf08b-120">Potom vyberte **rozhraní .NET Framework 4.5** v rozevíracím seznamu s názvem **Cílová architektura**.</span><span class="sxs-lookup"><span data-stu-id="bf08b-120">Then select **.NET Framework 4.5** in the dropdown box labeled **Target Framework**.</span></span>  
  
     <span data-ttu-id="bf08b-121">Nastavení způsobí, že Cílová architektura [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] načtěte řešení znovu, stiskněte klávesu **OK** po zobrazení výzvy.</span><span class="sxs-lookup"><span data-stu-id="bf08b-121">Setting the target framework will cause [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] to reload the solution, press **OK** when prompted.</span></span>  
  
3.  <span data-ttu-id="bf08b-122">Přidat odkaz na projekt GettingStartedLib GettingStartedHost projektu kliknutím pravým tlačítkem na **odkazy** ve složce GettingStartedHost projekt v Průzkumníku řešení a vyberte **přidat odkaz** .</span><span class="sxs-lookup"><span data-stu-id="bf08b-122">Add a reference to the GettingStartedLib project to the GettingStartedHost project by right clicking on the **References** folder under the GettingStartedHost project in the solution explorer and select **Add Reference**.</span></span> <span data-ttu-id="bf08b-123">V **přidat odkaz** dialogového okna, vyberte **řešení** na levé straně dialogového okna a vyberte GettingStartedLib v System center části dialogového okna a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="bf08b-123">In the **Add Reference** dialog, select **Solution** on the left-hand side of the dialog and select GettingStartedLib in the center section of the dialog and click **Add**.</span></span> <span data-ttu-id="bf08b-124">Díky tomu typy definované v GettingStartedLib GettingStartedHost projektu k dispozici.</span><span class="sxs-lookup"><span data-stu-id="bf08b-124">This makes the types defined in GettingStartedLib available to the GettingStartedHost project.</span></span>  
  
4.  <span data-ttu-id="bf08b-125">Přidat odkaz na System.ServiceModel GettingStartedHost projektu kliknutím pravým tlačítkem myši **odkaz** ve složce GettingStartedHost projekt v Průzkumníku řešení a vyberte **přidat** Referenční dokumentace.</span><span class="sxs-lookup"><span data-stu-id="bf08b-125">Add a reference to System.ServiceModel to the GettingStartedHost project by right-clicking the **Reference** folder under the GettingStartedHost project in Solution Explorer and select **Add** Reference.</span></span> <span data-ttu-id="bf08b-126">V **přidat odkaz** dialogové okno Vybrat **Framework** na levé straně dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="bf08b-126">In the **Add Reference** dialog select **Framework** on the left-hand side of the dialog.</span></span> <span data-ttu-id="bf08b-127">Do textového pole hledání sestavení, zadejte v `System.ServiceModel`.</span><span class="sxs-lookup"><span data-stu-id="bf08b-127">In the Search Assemblies textbox, type in `System.ServiceModel`.</span></span> <span data-ttu-id="bf08b-128">V části System center dialogového okna vyberte **System.ServiceModel**, klikněte na tlačítko **přidat** tlačítko a klikněte na tlačítko **Zavřít** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="bf08b-128">In the center section of the dialog select **System.ServiceModel**, click the **Add** button, and click the **Close** button.</span></span> <span data-ttu-id="bf08b-129">Uložte řešení kliknutím na tlačítko Uložit vše pod hlavní nabídky.</span><span class="sxs-lookup"><span data-stu-id="bf08b-129">Save the solution by clicking the Save All button below the main menu.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="bf08b-130">K hostování služby</span><span class="sxs-lookup"><span data-stu-id="bf08b-130">To host the service</span></span>  
  
-   <span data-ttu-id="bf08b-131">Otevřete soubor Program.cs nebo Module.vb a zadejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="bf08b-131">Open the Program.cs or Module.vb file and enter the following code:</span></span>  
  
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
  
    1.  <span data-ttu-id="bf08b-132">Krok 1: vytvoří instanci třídy Uri k umístění základní adresu služby.</span><span class="sxs-lookup"><span data-stu-id="bf08b-132">Step 1 - Creates an instance of the Uri class to hold the base address of the service.</span></span> <span data-ttu-id="bf08b-133">Služby jsou označeny adresu URL, která obsahuje základní adresu a volitelné identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="bf08b-133">Services are identified by a URL which contains a base address and an optional URI.</span></span> <span data-ttu-id="bf08b-134">Základní adresa naformátován takto: [přenosu] :// [název počítače nebo domény] [: volitelné port č] / [volitelný segment identifikátoru URI] základní adresa pro službu kalkulačky používá přenos pomocí protokolu HTTP, místního hostitele, port 8000 a identifikátor URI segmentovat "GettingStarted"</span><span class="sxs-lookup"><span data-stu-id="bf08b-134">The base address is formatted as follows:[transport]://[machine-name or domain][:optional port #]/[optional URI segment]The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment "GettingStarted"</span></span>  
  
    2.  <span data-ttu-id="bf08b-135">Krok 2 – vytvoří instanci <xref:System.ServiceModel.ServiceHost> třídy pro hostování služby.</span><span class="sxs-lookup"><span data-stu-id="bf08b-135">Step 2 – Creates an instance of the <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="bf08b-136">Konstruktor přijímá dva parametry typu třídy, která implementuje kontrakt služby a základní adresu služby.</span><span class="sxs-lookup"><span data-stu-id="bf08b-136">The constructor takes two parameters, the type of the class that implements the service contract, and the base address of the service.</span></span>  
  
    3.  <span data-ttu-id="bf08b-137">Krok 3 – vytvoří <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span><span class="sxs-lookup"><span data-stu-id="bf08b-137">Step 3 – Creates a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="bf08b-138">Koncový bod služby se skládá z adresy, vazby a smlouvy o poskytování služeb.</span><span class="sxs-lookup"><span data-stu-id="bf08b-138">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="bf08b-139"><xref:System.ServiceModel.Description.ServiceEndpoint> Konstruktor proto přebírá typ rozhraní kontraktu služby, vazbu a adresu.</span><span class="sxs-lookup"><span data-stu-id="bf08b-139">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor therefore takes the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="bf08b-140">Kontrakt služby je `ICalculator`, která definované a implementaci v typu služby.</span><span class="sxs-lookup"><span data-stu-id="bf08b-140">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="bf08b-141">Vazba použitá v tomto příkladu je <xref:System.ServiceModel.WSHttpBinding> což je integrované vazbu, která se používá pro připojení ke koncovým bodům, které odpovídají WS-\* specifikace.</span><span class="sxs-lookup"><span data-stu-id="bf08b-141">The binding used in this sample is <xref:System.ServiceModel.WSHttpBinding> which is a built-in binding that is used for connecting to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="bf08b-142">Další informace o vazbách WCF najdete v tématu [vazby WCF – přehled](../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bf08b-142">For more information about WCF bindings, see [WCF Bindings Overview](../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="bf08b-143">Adresa se připojí k základní adrese k identifikaci koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="bf08b-143">The address is appended to the base address to identify the endpoint.</span></span> <span data-ttu-id="bf08b-144">Adresa zadaná v tomto kódu je "CalculatorService", takže je plně kvalifikovanou adresu pro koncový bod `"http://localhost:8000/GettingStarted/CalculatorService"`.</span><span class="sxs-lookup"><span data-stu-id="bf08b-144">The address specified in this code is "CalculatorService" so the fully qualified address for the endpoint is `"http://localhost:8000/GettingStarted/CalculatorService"`.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="bf08b-145">Přidání koncového bodu služby je volitelné, pokud používáte rozhraní .NET Framework 4 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="bf08b-145">Adding a service endpoint is optional when using .NET Framework 4 or later.</span></span> <span data-ttu-id="bf08b-146">V těchto verzích Pokud žádné koncové body jsou přidány do kódu nebo konfigurace WCF přidá jeden výchozí koncový bod pro každou kombinaci základní adresu a kontraktů implementovaných službou.</span><span class="sxs-lookup"><span data-stu-id="bf08b-146">In these versions, if no endpoints are added in code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="bf08b-147">Další informace o výchozí koncové body naleznete v tématu [zadání adresy koncového bodu](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="bf08b-147">For more information about default endpoints see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="bf08b-148">Další informace o výchozí koncové body, vazby a chování najdete v tématu [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="bf08b-148">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
    4.  <span data-ttu-id="bf08b-149">Krok 4 – povolení metadata exchange.</span><span class="sxs-lookup"><span data-stu-id="bf08b-149">Step 4 – Enable metadata exchange.</span></span> <span data-ttu-id="bf08b-150">Klienti použijí ke generování proxy servery, které se použije k volání operací služby metadata exchange.</span><span class="sxs-lookup"><span data-stu-id="bf08b-150">Clients will use metadata exchange to generate proxies that will be used to call the service operations.</span></span> <span data-ttu-id="bf08b-151">Umožňuje vytvořit výměny metadat <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, nastavte ho na <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> vlastnost `true`a přidat chování při <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  --> `System.ServiceModel.ServiceHost.Behaviors%2A` kolekce <xref:System.ServiceModel.ServiceHost> instance.</span><span class="sxs-lookup"><span data-stu-id="bf08b-151">To enable metadata exchange create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set it’s <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, and add the behavior to the <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A` collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>  
  
    5.  <span data-ttu-id="bf08b-152">Krok 5 – otevřít <xref:System.ServiceModel.ServiceHost> k naslouchání pro příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="bf08b-152">Step 5 – Open the <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="bf08b-153">Všimněte si, že kód čeká uživatelem zadejte.</span><span class="sxs-lookup"><span data-stu-id="bf08b-153">Notice the code waits for the user to hit enter.</span></span> <span data-ttu-id="bf08b-154">Pokud to neprovedete, bude aplikace okamžitě ukončena a služby se vypne. Všimněte si také bloku try/catch použít.</span><span class="sxs-lookup"><span data-stu-id="bf08b-154">If you do not do this, the app will close immediately and the service will shut down.Also notice a  try/catch block used.</span></span> <span data-ttu-id="bf08b-155">Po <xref:System.ServiceModel.ServiceHost> byla vytvořena instance, jiný kód je umístěn v bloku try/catch.</span><span class="sxs-lookup"><span data-stu-id="bf08b-155">After the <xref:System.ServiceModel.ServiceHost> has been instantiated, all other code is placed in a try/catch block.</span></span> <span data-ttu-id="bf08b-156">Další informace o bezpečně zachycování výjimek vyvolaných <xref:System.ServiceModel.ServiceHost>, naleznete v tématu [vyhnout problémům s příkazem Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)</span><span class="sxs-lookup"><span data-stu-id="bf08b-156">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Avoiding Problems with the Using Statement](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bf08b-157">Úpravy souboru App.config v GettingStartedLib tak, aby odrážely změny provedené v kódu:</span><span class="sxs-lookup"><span data-stu-id="bf08b-157">Edit App.config in GettingStartedLib to reflect the changes made in code:</span></span> 
> 1. <span data-ttu-id="bf08b-158">Změňte na řádek 14 `<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="bf08b-158">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
> 2. <span data-ttu-id="bf08b-159">Změňte řádek 17 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="bf08b-159">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
> 3. <span data-ttu-id="bf08b-160">Změňte řádek 22 na `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="bf08b-160">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>
        
### <a name="to-verify-the-service-is-working"></a><span data-ttu-id="bf08b-161">Chcete-li ověřit, že služba funguje</span><span class="sxs-lookup"><span data-stu-id="bf08b-161">To verify the service is working</span></span>  
  
1.  <span data-ttu-id="bf08b-162">Spuštění aplikace konzoly GettingStartedHost z uvnitř [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf08b-162">Run the GettingStartedHost console application from inside [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span> <span data-ttu-id="bf08b-163">Když se používá [!INCLUDE[wv](../../../includes/wv-md.md)] a novějších operačních systémů, musí se spustit službu s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="bf08b-163">When running on [!INCLUDE[wv](../../../includes/wv-md.md)] and later operating systems, the service must be run with administrator privileges.</span></span> <span data-ttu-id="bf08b-164">Protože spuštění sady Visual Studio s oprávněními správce GettingStartedHost také spouštět s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="bf08b-164">Because Visual Studio was run with Administrator privileges, GettingStartedHost is also run with Administrator privileges.</span></span> <span data-ttu-id="bf08b-165">Můžete také spustit nový příkazový řádek s oprávněními správce a spusťte service.exe v něm.</span><span class="sxs-lookup"><span data-stu-id="bf08b-165">You can also start a new command prompt running it with Administrator privileges and run service.exe within it.</span></span>  
  
2.  <span data-ttu-id="bf08b-166">Otevřete Internet Explorer a přejděte do služby ladění stránce v `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="bf08b-166">Open Internet Explorer and browse to the service's debug page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf08b-167">Příklad</span><span class="sxs-lookup"><span data-stu-id="bf08b-167">Example</span></span>  
 <span data-ttu-id="bf08b-168">Následující příklad obsahuje kontrakt a implementaci služby z předchozích kroků tohoto kurzu a hostuje službu v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bf08b-168">The following example includes the service contract and implementation from previous steps in the tutorial and hosts the service in a console application.</span></span>  
  
 <span data-ttu-id="bf08b-169">Chcete-li zkompilovat pomocí kompilátoru příkazového řádku, zkompilovat do knihovny třídy odkazující na IService1.cs a Service1.cs `System.ServiceModel.dll`.</span><span class="sxs-lookup"><span data-stu-id="bf08b-169">To compile this with a command-line compiler, compile IService1.cs and Service1.cs into a class library referencing `System.ServiceModel.dll`.</span></span> <span data-ttu-id="bf08b-170">A zkompilujte soubor Program.cs do konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="bf08b-170">And compile Program.cs to a console application.</span></span>  
  
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
>  <span data-ttu-id="bf08b-171">Služby, jako je ten vyžadují oprávnění k registraci adresami protokolu HTTP na počítači pro naslouchání.</span><span class="sxs-lookup"><span data-stu-id="bf08b-171">Services such as this one require permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="bf08b-172">Účty správců mají toto oprávnění, ale účty bez oprávnění správce musí být uděleno oprávnění pro obory názvů HTTP.</span><span class="sxs-lookup"><span data-stu-id="bf08b-172">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="bf08b-173">Další informace o tom, jak konfigurace rezervace oboru názvů najdete v tématu [konfigurace HTTP a HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="bf08b-173">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="bf08b-174">Při spuštění v sadě Visual Studio, musí být spuštěn service.exe s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="bf08b-174">When running under Visual Studio, the service.exe must be run with administrator privileges.</span></span>  
  
 <span data-ttu-id="bf08b-175">Nyní je služba spuštěna.</span><span class="sxs-lookup"><span data-stu-id="bf08b-175">Now the service is running.</span></span> <span data-ttu-id="bf08b-176">Přejít k [postupy: vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="bf08b-176">Proceed to [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="bf08b-177">Informace o odstraňování potíží naleznete v tématu [řešení potíží s kurzu Začínáme](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="bf08b-177">For troubleshooting information, see [Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf08b-178">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf08b-178">See Also</span></span>  
 [<span data-ttu-id="bf08b-179">Začínáme</span><span class="sxs-lookup"><span data-stu-id="bf08b-179">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="bf08b-180">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="bf08b-180">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
