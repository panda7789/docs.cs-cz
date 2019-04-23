---
title: 'Kurz: Hostování a spuštění základní služby Windows Communication Foundation'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: ad9536b1f27ba3945bf76d0474de4825033a1e8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197903"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="4b767-102">Kurz: Hostování a spuštění základní služby Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="4b767-102">Tutorial: Host and run a basic Windows Communication Foundation service</span></span>

<span data-ttu-id="4b767-103">Tento kurz popisuje třetí pět úloh potřebných k vytvoření základní aplikace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4b767-103">This tutorial describes the third of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="4b767-104">Přehled v kurzech, naleznete v tématu [kurzu: Začínáme s aplikacemi Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="4b767-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="4b767-105">Dalším úkolem pro vytvoření aplikace WCF je hostování služby WCF v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4b767-105">The next task for creating a WCF application is to host a WCF service in a console application.</span></span> <span data-ttu-id="4b767-106">Služby WCF zpřístupňuje jeden nebo více *koncové body*, každý z nich vystavuje jednu nebo víc operací služeb.</span><span class="sxs-lookup"><span data-stu-id="4b767-106">A WCF service exposes one or more *endpoints*, each of which exposes one or more service operations.</span></span> <span data-ttu-id="4b767-107">Koncový bod služby určuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="4b767-107">A service endpoint specifies the following information:</span></span> 
- <span data-ttu-id="4b767-108">Adresa, kde najdete službu.</span><span class="sxs-lookup"><span data-stu-id="4b767-108">An address where you can find the service.</span></span>
- <span data-ttu-id="4b767-109">Vazbu, která obsahuje informace, které popisuje, jak klient musí komunikovat se službou.</span><span class="sxs-lookup"><span data-stu-id="4b767-109">A binding that contains the information that describes how a client must communicate with the service.</span></span> 
- <span data-ttu-id="4b767-110">Kontrakt, který definuje funkci, která poskytuje služby svým klientům.</span><span class="sxs-lookup"><span data-stu-id="4b767-110">A contract that defines the functionality that the service provides to its clients.</span></span>

<span data-ttu-id="4b767-111">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="4b767-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="4b767-112">Vytvořte a nakonfigurujte projekt konzolové aplikace pro hostování služby WCF.</span><span class="sxs-lookup"><span data-stu-id="4b767-112">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="4b767-113">Přidejte kód pro hostování služby WCF.</span><span class="sxs-lookup"><span data-stu-id="4b767-113">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="4b767-114">Aktualizujte konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="4b767-114">Update the configuration file.</span></span>
> - <span data-ttu-id="4b767-115">Spusťte službu WCF a ověří, že je spuštěná.</span><span class="sxs-lookup"><span data-stu-id="4b767-115">Start the WCF service and verify it's running.</span></span>

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a><span data-ttu-id="4b767-116">Vytvořte a nakonfigurujte projekt konzolové aplikace pro hostování služby</span><span class="sxs-lookup"><span data-stu-id="4b767-116">Create and configure a console app project for hosting the service</span></span>

1. <span data-ttu-id="4b767-117">Vytvořte projekt konzolové aplikace v sadě Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="4b767-117">Create a console app project in Visual Studio:</span></span> 
 
    1. <span data-ttu-id="4b767-118">Z **souboru** nabídce vyberte možnost **otevřít** > **projekt či řešení** a přejděte do **GettingStarted** řešení můžete vytvořené (*GettingStarted.sln*).</span><span class="sxs-lookup"><span data-stu-id="4b767-118">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="4b767-119">Vyberte **Open** (Otevřít).</span><span class="sxs-lookup"><span data-stu-id="4b767-119">Select **Open**.</span></span>

    2. <span data-ttu-id="4b767-120">Z **zobrazení** nabídce vyberte možnost **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="4b767-120">From the **View** menu, select **Solution Explorer**.</span></span>
    
    3. <span data-ttu-id="4b767-121">V **Průzkumníka řešení** okna, vyberte **GettingStarted** řešení (nejvyšší uzel) a pak vyberte **přidat** > **nový projekt** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="4b767-121">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span> 

    4. <span data-ttu-id="4b767-122">V **přidat nový projekt** na levé straně vyberte okno **Windows Desktop** kategorie v části **Visual C#**  nebo **jazyka Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="4b767-122">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> 

    5. <span data-ttu-id="4b767-123">Vyberte **Konzolová aplikace (.NET Framework)** šablony a zadejte *GettingStartedHost* pro **název**.</span><span class="sxs-lookup"><span data-stu-id="4b767-123">Select the **Console App (.NET Framework)** template, and enter *GettingStartedHost* for the **Name**.</span></span> <span data-ttu-id="4b767-124">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="4b767-124">Select **OK**.</span></span>

2. <span data-ttu-id="4b767-125">Přidat odkaz **GettingStartedHost** projektu **GettingStartedLib** projektu:</span><span class="sxs-lookup"><span data-stu-id="4b767-125">Add a reference in the **GettingStartedHost** project to the **GettingStartedLib** project:</span></span> 

    1. <span data-ttu-id="4b767-126">V **Průzkumníka řešení** okna, vyberte **odkazy** ve složce **GettingStartedHost** projektu a pak vyberte **přidat odkaz** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="4b767-126">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span> 

    2. <span data-ttu-id="4b767-127">V **přidat odkaz** dialogového okna, v části **projekty** v levé části okna vyberte **řešení**.</span><span class="sxs-lookup"><span data-stu-id="4b767-127">In the **Add Reference** dialog, under **Projects** on the left side of the window, select **Solution**.</span></span> 
 
    3. <span data-ttu-id="4b767-128">Vyberte **GettingStartedLib** v System center části okna a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="4b767-128">Select **GettingStartedLib** in the center section of the window, and then select **OK**.</span></span> 

       <span data-ttu-id="4b767-129">Tato akce vytvoří typy definované v **GettingStartedLib** projektu, které jsou k dispozici na **GettingStartedHost** projektu.</span><span class="sxs-lookup"><span data-stu-id="4b767-129">This action makes the types defined in the **GettingStartedLib** project available to the **GettingStartedHost** project.</span></span>

3. <span data-ttu-id="4b767-130">Přidat odkaz **GettingStartedHost** projektu <xref:System.ServiceModel> sestavení:</span><span class="sxs-lookup"><span data-stu-id="4b767-130">Add a reference in the **GettingStartedHost** project to the <xref:System.ServiceModel> assembly:</span></span> 

    1. <span data-ttu-id="4b767-131">V **Průzkumníka řešení** okna, vyberte **odkazy** ve složce **GettingStartedHost** projektu a pak vyberte **přidat odkaz** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="4b767-131">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>
    
    2. <span data-ttu-id="4b767-132">V **přidat odkaz** okně v části **sestavení** v levé části okna vyberte **Framework**.</span><span class="sxs-lookup"><span data-stu-id="4b767-132">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span> 

    3. <span data-ttu-id="4b767-133">Vyberte **System.ServiceModel**a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="4b767-133">Select **System.ServiceModel**, and then select **OK**.</span></span> 
    
    4. <span data-ttu-id="4b767-134">Uložte řešení tak, že vyberete **souboru** > **Uložit vše**.</span><span class="sxs-lookup"><span data-stu-id="4b767-134">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="add-code-to-host-the-service"></a><span data-ttu-id="4b767-135">Přidejte kód pro hostování služby</span><span class="sxs-lookup"><span data-stu-id="4b767-135">Add code to host the service</span></span>

<span data-ttu-id="4b767-136">K hostování služby, přidejte kód proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="4b767-136">To host the service, you add code to do the following steps:</span></span> 
   1. <span data-ttu-id="4b767-137">Vytvořte identifikátor URI pro základní adresu.</span><span class="sxs-lookup"><span data-stu-id="4b767-137">Create a URI for the base address.</span></span>
   2. <span data-ttu-id="4b767-138">Vytvoření instance třídy, pro který je hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="4b767-138">Create a class instance for hosting the service.</span></span>
   3. <span data-ttu-id="4b767-139">Vytvoření koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="4b767-139">Create a service endpoint.</span></span>
   4. <span data-ttu-id="4b767-140">Povolte výměny metadat.</span><span class="sxs-lookup"><span data-stu-id="4b767-140">Enable metadata exchange.</span></span>
   5. <span data-ttu-id="4b767-141">Otevření hostitele služby k naslouchání pro příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="4b767-141">Open the service host to listen for incoming messages.</span></span>
  
<span data-ttu-id="4b767-142">Proveďte následující změny kódu:</span><span class="sxs-lookup"><span data-stu-id="4b767-142">Make the following changes to the code:</span></span>

1. <span data-ttu-id="4b767-143">Otevřít **Program.cs** nebo **Module1.vb** soubor **GettingStartedHost** projektu a nahraďte jeho kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="4b767-143">Open the **Program.cs** or **Module1.vb** file in the **GettingStartedHost** project and replace its code with the following code:</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Description;
    using GettingStartedLib;

    namespace GettingStartedHost
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Step 1: Create a URI to serve as the base address.
                Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");

                // Step 2: Create a ServiceHost instance.
                ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

                try
                {
                    // Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                    // Step 4: Enable metadata exchange.
                    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                    smb.HttpGetEnabled = true;
                    selfHost.Description.Behaviors.Add(smb)    ;

                    // Step 5: Start the service.
                    selfHost.Open();
                    Console.WriteLine("The service is ready.");

                    // Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.");
                    Console.WriteLine();
                    Console.ReadLine();
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
    Imports System.ServiceModel
    Imports System.ServiceModel.Description
    Imports GettingStartedLib.GettingStartedLib

    Module Service

        Class Program
            Shared Sub Main()
                ' Step 1: Create a URI to serve as the base address.
                Dim baseAddress As New Uri("http://localhost:8000/GettingStarted/")

                ' Step 2: Create a ServiceHost instance.
                Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
               Try

                    ' Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint( _
                        GetType(ICalculator), _
                        New WSHttpBinding(), _
                        "CalculatorService")

                    ' Step 4: Enable metadata exchange.
                    Dim smb As New ServiceMetadataBehavior()
                    smb.HttpGetEnabled = True
                    selfHost.Description.Behaviors.Add(smb)

                    ' Step 5: Start the service.
                    selfHost.Open()
                    Console.WriteLine("The service is ready.")

                    ' Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.")
                    Console.WriteLine()
                    Console.ReadLine()
                    selfHost.Close()

                Catch ce As CommunicationException
                    Console.WriteLine("An exception occurred: {0}", ce.Message)
                    selfHost.Abort()
                End Try
            End Sub
        End Class

    End Module
    ```
    
    <span data-ttu-id="4b767-144">Informace o tom, jak tento kód funguje, najdete v tématu [služby hostování program kroky](#service-hosting-program-steps).</span><span class="sxs-lookup"><span data-stu-id="4b767-144">For information about how this code works, see [Service hosting program steps](#service-hosting-program-steps).</span></span>

2. <span data-ttu-id="4b767-145">Aktualizace vlastností projektu:</span><span class="sxs-lookup"><span data-stu-id="4b767-145">Update the project properties:</span></span>

   1. <span data-ttu-id="4b767-146">V **Průzkumníka řešení** okna, vyberte **GettingStartedHost** složku a pak vyberte **vlastnosti** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="4b767-146">In the **Solution Explorer** window, select the **GettingStartedHost** folder, and then select **Properties** from the shortcut menu.</span></span>

   2. <span data-ttu-id="4b767-147">Na **GettingStartedHost** stránku vlastností, vyberte **aplikace** kartu:</span><span class="sxs-lookup"><span data-stu-id="4b767-147">On the **GettingStartedHost** properties page, select the **Application** tab:</span></span>

      - <span data-ttu-id="4b767-148">Pro C# projektů, vyberte **GettingStartedHost.Program** z **spouštěcí objekt** seznamu.</span><span class="sxs-lookup"><span data-stu-id="4b767-148">For C# projects, select **GettingStartedHost.Program** from the **Startup object** list.</span></span>

      - <span data-ttu-id="4b767-149">Pro projekty jazyka Visual Basic, vyberte **Service.Program** z **spouštěcí objekt** seznamu.</span><span class="sxs-lookup"><span data-stu-id="4b767-149">For Visual Basic projects, select **Service.Program** from the **Startup object** list.</span></span>

   3. <span data-ttu-id="4b767-150">Z **souboru** nabídce vyberte možnost **Uložit vše**.</span><span class="sxs-lookup"><span data-stu-id="4b767-150">From the **File** menu, select **Save All**.</span></span>

## <a name="verify-the-service-is-working"></a><span data-ttu-id="4b767-151">Ověřte, že služba funguje</span><span class="sxs-lookup"><span data-stu-id="4b767-151">Verify the service is working</span></span>

1. <span data-ttu-id="4b767-152">Sestavte řešení a pak spusťte **GettingStartedHost** konzoly z aplikace v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4b767-152">Build the solution, and then run the **GettingStartedHost** console application from inside Visual Studio.</span></span> 

    <span data-ttu-id="4b767-153">Služba musí běžet s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="4b767-153">The service must be run with administrator privileges.</span></span> <span data-ttu-id="4b767-154">Protože jste spustili sady Visual Studio s oprávněními správce, když spustíte **GettingStartedHost** v sadě Visual Studio, při spuštění aplikace se také oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="4b767-154">Because you opened Visual Studio with administrator privileges, when you run **GettingStartedHost** in Visual Studio, the application is run with administrator privileges as well.</span></span> <span data-ttu-id="4b767-155">Alternativně můžete otevřít nový příkazový řádek jako správce (vyberte **Další** > **spustit jako správce** z místní nabídky) a spusťte **GettingStartedHost.exe**  v něm.</span><span class="sxs-lookup"><span data-stu-id="4b767-155">As an alternative, you can open a new command prompt as an administrator (select **More** > **Run as administrator** from the shortcut menu) and run **GettingStartedHost.exe** within it.</span></span>

2. <span data-ttu-id="4b767-156">Otevřete webový prohlížeč a přejděte na stránku služby na `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="4b767-156">Open a web browser and browse to the service's page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>
   
   > [!NOTE]
   > <span data-ttu-id="4b767-157">Služby, jako je ten vyžadují správné oprávnění k registraci adresami protokolu HTTP na počítači pro naslouchání.</span><span class="sxs-lookup"><span data-stu-id="4b767-157">Services such as this one require the proper permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="4b767-158">Účty správců mají toto oprávnění, ale účty bez oprávnění správce musí být uděleno oprávnění pro obory názvů HTTP.</span><span class="sxs-lookup"><span data-stu-id="4b767-158">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="4b767-159">Další informace o tom, jak konfigurace rezervace oboru názvů najdete v tématu [konfigurace HTTP a HTTPS](feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="4b767-159">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](feature-details/configuring-http-and-https.md).</span></span> 

## <a name="service-hosting-program-steps"></a><span data-ttu-id="4b767-160">Služby hostování program kroky</span><span class="sxs-lookup"><span data-stu-id="4b767-160">Service hosting program steps</span></span>

<span data-ttu-id="4b767-161">Kroky v kódu, který jste přidali do hostitele služby jsou popsány v následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="4b767-161">The steps in the code you added to host the service are described as follows:</span></span>

- <span data-ttu-id="4b767-162">**Krok 1**: Vytvoření instance `Uri` třídy pro uložení základní adresu služby.</span><span class="sxs-lookup"><span data-stu-id="4b767-162">**Step 1**: Create an instance of the `Uri` class to hold the base address of the service.</span></span> <span data-ttu-id="4b767-163">Adresa URL, která obsahuje základní adresa má volitelný identifikátor URI, který identifikuje službu.</span><span class="sxs-lookup"><span data-stu-id="4b767-163">A URL that contains a base address has an optional URI that identifies a service.</span></span> <span data-ttu-id="4b767-164">Základní adresa naformátován takto: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span><span class="sxs-lookup"><span data-stu-id="4b767-164">The base address is formatted as follows: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span></span> <span data-ttu-id="4b767-165">Základní adresa pro službu kalkulačky používá přenos pomocí protokolu HTTP, místního hostitele, port 8000 a segment identifikátoru URI GettingStarted.</span><span class="sxs-lookup"><span data-stu-id="4b767-165">The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment, GettingStarted.</span></span>

- <span data-ttu-id="4b767-166">**Krok 2**: Vytvoření instance <xref:System.ServiceModel.ServiceHost> třídy, který použijete k hostování služby.</span><span class="sxs-lookup"><span data-stu-id="4b767-166">**Step 2**: Create an instance of the <xref:System.ServiceModel.ServiceHost> class, which you use to host the service.</span></span> <span data-ttu-id="4b767-167">Konstruktor používá dva parametry: typ třídy, která implementuje kontrakt služby a základní adresu služby.</span><span class="sxs-lookup"><span data-stu-id="4b767-167">The constructor takes two parameters: the type of the class that implements the service contract and the base address of the service.</span></span>

- <span data-ttu-id="4b767-168">**Krok 3**: Vytvoření <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span><span class="sxs-lookup"><span data-stu-id="4b767-168">**Step 3**: Create a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="4b767-169">Koncový bod služby se skládá z adresy, vazby a smlouvy o poskytování služeb.</span><span class="sxs-lookup"><span data-stu-id="4b767-169">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="4b767-170"><xref:System.ServiceModel.Description.ServiceEndpoint> Konstruktoru se skládá z typu rozhraní kontraktu služby, vazbu a adresu.</span><span class="sxs-lookup"><span data-stu-id="4b767-170">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor is composed of the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="4b767-171">Kontrakt služby je `ICalculator`, která definované a implementaci v typu služby.</span><span class="sxs-lookup"><span data-stu-id="4b767-171">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="4b767-172">Vazba pro tuto ukázku je <xref:System.ServiceModel.WSHttpBinding>, které jsou integrované vazby a připojení ke koncovým bodům, které odpovídají WS-\* specifikace.</span><span class="sxs-lookup"><span data-stu-id="4b767-172">The binding for this sample is <xref:System.ServiceModel.WSHttpBinding>, which is a built-in binding and connects to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="4b767-173">Další informace o vazbách WCF najdete v tématu [vazby WCF – přehled](bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4b767-173">For more information about WCF bindings, see [WCF bindings overview](bindings-overview.md).</span></span> <span data-ttu-id="4b767-174">Adresa se připojí k základní adresu, abyste identifikovali koncový bod.</span><span class="sxs-lookup"><span data-stu-id="4b767-174">You append the address to the base address to identify the endpoint.</span></span> <span data-ttu-id="4b767-175">Kód určuje adresu jako CalculatorService a plně kvalifikovanou adresu pro koncový bod jako `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="4b767-175">The code specifies the address as CalculatorService and the fully qualified address for the endpoint as `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="4b767-176">Pro rozhraní .NET Framework verze 4 a novější přidává se koncový bod služby je volitelný.</span><span class="sxs-lookup"><span data-stu-id="4b767-176">For .NET Framework Version 4 and later, adding a service endpoint is optional.</span></span> <span data-ttu-id="4b767-177">Pro tyto verze pokud nepřidáte kódu nebo konfigurace WCF přidá jeden výchozí koncový bod pro každou kombinaci základní adresu a kontraktů implementovaných službou.</span><span class="sxs-lookup"><span data-stu-id="4b767-177">For these versions, if you don't add your code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="4b767-178">Další informace o výchozí koncové body, naleznete v tématu [zadání adresy koncového bodu](specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="4b767-178">For more information about default endpoints, see [Specifying an endpoint address](specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="4b767-179">Další informace o výchozí koncové body, vazby a chování najdete v tématu [zjednodušené konfigurace](simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="4b767-179">For more information about default endpoints, bindings, and behaviors, see [Simplified configuration](simplified-configuration.md) and [Simplified configuration for WCF services](samples/simplified-configuration-for-wcf-services.md).</span></span>

- <span data-ttu-id="4b767-180">**Krok 4**: Povolte výměny metadat.</span><span class="sxs-lookup"><span data-stu-id="4b767-180">**Step 4**: Enable metadata exchange.</span></span> <span data-ttu-id="4b767-181">Klienti používají ke generování proxy serverů k volání operací služby výměny metadat.</span><span class="sxs-lookup"><span data-stu-id="4b767-181">Clients use metadata exchange to generate proxies for calling the service operations.</span></span> <span data-ttu-id="4b767-182">Povolit výměny metadat, vytvořte <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, nastavte jeho <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> vlastnost `true`a přidejte `ServiceMetadataBehavior` objektu <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekce <xref:System.ServiceModel.ServiceHost> instance.</span><span class="sxs-lookup"><span data-stu-id="4b767-182">To enable metadata exchange, create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set its <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> property to `true`, and add the `ServiceMetadataBehavior` object to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

- <span data-ttu-id="4b767-183">**Krok 5**: Otevřít <xref:System.ServiceModel.ServiceHost> k naslouchání pro příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="4b767-183">**Step 5**: Open <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="4b767-184">Aplikace čeká, až stisknete **Enter**.</span><span class="sxs-lookup"><span data-stu-id="4b767-184">The application waits for you to press **Enter**.</span></span> <span data-ttu-id="4b767-185">Jakmile aplikace vytvoří instanci <xref:System.ServiceModel.ServiceHost>, provede blok try/catch.</span><span class="sxs-lookup"><span data-stu-id="4b767-185">After the application instantiates <xref:System.ServiceModel.ServiceHost>, it executes a try/catch block.</span></span> <span data-ttu-id="4b767-186">Další informace o bezpečně zachycování výjimek vyvolaných <xref:System.ServiceModel.ServiceHost>, naleznete v tématu [použití zavřít a Abort k uvolnění prostředků klienta WCF](samples/use-close-abort-release-wcf-client-resources.md).</span><span class="sxs-lookup"><span data-stu-id="4b767-186">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Use Close and Abort to release WCF client resources](samples/use-close-abort-release-wcf-client-resources.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4b767-187">Když přidáte knihovny služby WCF, Visual Studio hostuje za vás při ladění pomocí spuštění hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="4b767-187">When you add a WCF service library, Visual Studio hosts it for you if you debug it by starting a service host.</span></span> <span data-ttu-id="4b767-188">Aby nedocházelo ke konfliktům, můžete zabránit sady Visual Studio hostování knihovny služby WCF.</span><span class="sxs-lookup"><span data-stu-id="4b767-188">To avoid conflicts, you can prevent Visual Studio from hosting the WCF service library.</span></span> 
> 1. <span data-ttu-id="4b767-189">Vyberte **GettingStartedLib** projekt **Průzkumníka řešení** a zvolte **vlastnosti** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="4b767-189">Select the **GettingStartedLib** project in **Solution Explorer** and choose **Properties** from the shortcut menu.</span></span>
> 2. <span data-ttu-id="4b767-190">Vyberte **možnosti WCF** a zrušte zaškrtnutí políčka **spuštění hostitele služby WCF při ladění jiného projektu ve stejném řešení**.</span><span class="sxs-lookup"><span data-stu-id="4b767-190">Select **WCF Options** and uncheck **Start WCF Service Host when debugging another project in the same solution**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4b767-191">Další kroky</span><span class="sxs-lookup"><span data-stu-id="4b767-191">Next steps</span></span>

<span data-ttu-id="4b767-192">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="4b767-192">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="4b767-193">Vytvořte a nakonfigurujte projekt konzolové aplikace pro hostování služby WCF.</span><span class="sxs-lookup"><span data-stu-id="4b767-193">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="4b767-194">Přidejte kód pro hostování služby WCF.</span><span class="sxs-lookup"><span data-stu-id="4b767-194">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="4b767-195">Aktualizujte konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="4b767-195">Update the configuration file.</span></span>
> - <span data-ttu-id="4b767-196">Spusťte službu WCF a ověří, že je spuštěná.</span><span class="sxs-lookup"><span data-stu-id="4b767-196">Start the WCF service and verify it's running.</span></span>

<span data-ttu-id="4b767-197">Přejděte k dalšímu kurzu se naučíte, jak vytvořit klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="4b767-197">Advance to the next tutorial to learn how to create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4b767-198">Kurz: Vytvořte klienta WCF</span><span class="sxs-lookup"><span data-stu-id="4b767-198">Tutorial: Create a WCF client</span></span>](how-to-create-a-wcf-client.md)
