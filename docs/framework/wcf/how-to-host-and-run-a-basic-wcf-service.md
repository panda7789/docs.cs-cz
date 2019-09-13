---
title: 'Kurz: Hostování a spuštění služby Windows Communication Foundation Basic'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 984c5e73a8efc4e9c2d487485267868ffa2f60f3
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928715"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="baeae-102">Kurz: Hostování a spuštění služby Windows Communication Foundation Basic</span><span class="sxs-lookup"><span data-stu-id="baeae-102">Tutorial: Host and run a basic Windows Communication Foundation service</span></span>

<span data-ttu-id="baeae-103">Tento kurz popisuje třetí z pěti úloh potřebných k vytvoření aplikace Basic Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="baeae-103">This tutorial describes the third of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="baeae-104">Přehled kurzů najdete v tématu [kurz: Začněte s Windows Communication Foundation aplikacemi](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="baeae-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="baeae-105">Další úlohou pro vytvoření aplikace WCF je hostování služby WCF v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="baeae-105">The next task for creating a WCF application is to host a WCF service in a console application.</span></span> <span data-ttu-id="baeae-106">Služba WCF zveřejňuje jeden nebo více *koncových bodů*, z nichž každý zveřejňuje jednu nebo více operací služby.</span><span class="sxs-lookup"><span data-stu-id="baeae-106">A WCF service exposes one or more *endpoints*, each of which exposes one or more service operations.</span></span> <span data-ttu-id="baeae-107">Koncový bod služby určuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="baeae-107">A service endpoint specifies the following information:</span></span>

- <span data-ttu-id="baeae-108">Adresa, kde můžete najít službu.</span><span class="sxs-lookup"><span data-stu-id="baeae-108">An address where you can find the service.</span></span>
- <span data-ttu-id="baeae-109">Vazba obsahující informace, které popisují, jak klient musí komunikovat se službou.</span><span class="sxs-lookup"><span data-stu-id="baeae-109">A binding that contains the information that describes how a client must communicate with the service.</span></span> 
- <span data-ttu-id="baeae-110">Kontrakt definující funkce, které služba poskytuje svým klientům.</span><span class="sxs-lookup"><span data-stu-id="baeae-110">A contract that defines the functionality that the service provides to its clients.</span></span>

<span data-ttu-id="baeae-111">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="baeae-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="baeae-112">Vytvořte a nakonfigurujte projekt konzolové aplikace pro hostování služby WCF.</span><span class="sxs-lookup"><span data-stu-id="baeae-112">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="baeae-113">Přidejte kód pro hostování služby WCF.</span><span class="sxs-lookup"><span data-stu-id="baeae-113">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="baeae-114">Aktualizujte konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="baeae-114">Update the configuration file.</span></span>
> - <span data-ttu-id="baeae-115">Spusťte službu WCF a ověřte, zda je spuštěná.</span><span class="sxs-lookup"><span data-stu-id="baeae-115">Start the WCF service and verify it's running.</span></span>

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a><span data-ttu-id="baeae-116">Vytvoření a konfigurace projektu konzolové aplikace pro hostování služby</span><span class="sxs-lookup"><span data-stu-id="baeae-116">Create and configure a console app project for hosting the service</span></span>

1. <span data-ttu-id="baeae-117">Vytvoření projektu konzolové aplikace v aplikaci Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="baeae-117">Create a console app project in Visual Studio:</span></span> 
 
    1. <span data-ttu-id="baeae-118">V nabídce **soubor** vyberte **otevřít** > **projekt/řešení** a přejděte k **soubor GettingStarted** řešení, které jste dříve vytvořili (*soubor GettingStarted. sln*).</span><span class="sxs-lookup"><span data-stu-id="baeae-118">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="baeae-119">Vyberte **Open** (Otevřít).</span><span class="sxs-lookup"><span data-stu-id="baeae-119">Select **Open**.</span></span>

    2. <span data-ttu-id="baeae-120">V nabídce **zobrazení** vyberte **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="baeae-120">From the **View** menu, select **Solution Explorer**.</span></span>
    
    3. <span data-ttu-id="baeae-121">V okně **Průzkumník řešení** vyberte řešení **soubor GettingStarted** (nejvyšší uzel) a pak v místní nabídce vyberte **Přidat** > **Nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="baeae-121">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span> 

    4. <span data-ttu-id="baeae-122">V okně **Přidat nový projekt** na levé straně vyberte kategorii **Desktop systému Windows** pod položkou  **C# Visual** nebo **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="baeae-122">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> 

    5. <span data-ttu-id="baeae-123">Vyberte šablonu **Konzolová aplikace (.NET Framework)** a jako **název**zadejte *GettingStartedHost* .</span><span class="sxs-lookup"><span data-stu-id="baeae-123">Select the **Console App (.NET Framework)** template, and enter *GettingStartedHost* for the **Name**.</span></span> <span data-ttu-id="baeae-124">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="baeae-124">Select **OK**.</span></span>

2. <span data-ttu-id="baeae-125">Přidejte odkaz do projektu **GettingStartedHost** do projektu **GettingStartedLib** :</span><span class="sxs-lookup"><span data-stu-id="baeae-125">Add a reference in the **GettingStartedHost** project to the **GettingStartedLib** project:</span></span> 

    1. <span data-ttu-id="baeae-126">V okně **Průzkumník řešení** vyberte složku **odkazy** v projektu **GettingStartedHost** a pak vyberte **Přidat odkaz** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="baeae-126">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span> 

    2. <span data-ttu-id="baeae-127">V dialogovém okně **Přidat odkaz** vyberte v části **projekty** na levé straně okna možnost **řešení**.</span><span class="sxs-lookup"><span data-stu-id="baeae-127">In the **Add Reference** dialog, under **Projects** on the left side of the window, select **Solution**.</span></span> 
 
    3. <span data-ttu-id="baeae-128">V okně střední části okna vyberte **GettingStartedLib** a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="baeae-128">Select **GettingStartedLib** in the center section of the window, and then select **OK**.</span></span> 

       <span data-ttu-id="baeae-129">Tato akce zpřístupňuje typy definované v projektu **GettingStartedLib** k projektu **GettingStartedHost** .</span><span class="sxs-lookup"><span data-stu-id="baeae-129">This action makes the types defined in the **GettingStartedLib** project available to the **GettingStartedHost** project.</span></span>

3. <span data-ttu-id="baeae-130">Přidejte odkaz do projektu **GettingStartedHost** do <xref:System.ServiceModel> sestavení:</span><span class="sxs-lookup"><span data-stu-id="baeae-130">Add a reference in the **GettingStartedHost** project to the <xref:System.ServiceModel> assembly:</span></span> 

    1. <span data-ttu-id="baeae-131">V okně **Průzkumník řešení** vyberte složku **odkazy** v projektu **GettingStartedHost** a pak vyberte **Přidat odkaz** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="baeae-131">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>
    
    2. <span data-ttu-id="baeae-132">V okně **Přidat odkaz** v části **sestavení** na levé straně okna vyberte možnost **Architektura**.</span><span class="sxs-lookup"><span data-stu-id="baeae-132">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span> 

    3. <span data-ttu-id="baeae-133">Vyberte **System. ServiceModel**a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="baeae-133">Select **System.ServiceModel**, and then select **OK**.</span></span> 
    
    4. <span data-ttu-id="baeae-134">Uložte řešení tak, že vyberete **soubor** > **Uložit vše**.</span><span class="sxs-lookup"><span data-stu-id="baeae-134">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="add-code-to-host-the-service"></a><span data-ttu-id="baeae-135">Přidat kód pro hostování služby</span><span class="sxs-lookup"><span data-stu-id="baeae-135">Add code to host the service</span></span>

<span data-ttu-id="baeae-136">Chcete-li hostovat službu, přidejte kód, který provede následující kroky:</span><span class="sxs-lookup"><span data-stu-id="baeae-136">To host the service, you add code to do the following steps:</span></span> 

1. <span data-ttu-id="baeae-137">Vytvořte identifikátor URI pro základní adresu.</span><span class="sxs-lookup"><span data-stu-id="baeae-137">Create a URI for the base address.</span></span>
2. <span data-ttu-id="baeae-138">Vytvořte instanci třídy pro hostování služby.</span><span class="sxs-lookup"><span data-stu-id="baeae-138">Create a class instance for hosting the service.</span></span>
3. <span data-ttu-id="baeae-139">Vytvořte koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="baeae-139">Create a service endpoint.</span></span>
4. <span data-ttu-id="baeae-140">Povolte výměnu metadat.</span><span class="sxs-lookup"><span data-stu-id="baeae-140">Enable metadata exchange.</span></span>
5. <span data-ttu-id="baeae-141">Otevřete hostitele služby pro příjem příchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="baeae-141">Open the service host to listen for incoming messages.</span></span>
  
<span data-ttu-id="baeae-142">Proveďte následující změny kódu:</span><span class="sxs-lookup"><span data-stu-id="baeae-142">Make the following changes to the code:</span></span>

1. <span data-ttu-id="baeae-143">Otevřete soubor **program.cs** nebo **Module1. vb** v projektu **GettingStartedHost** a nahraďte jeho kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="baeae-143">Open the **Program.cs** or **Module1.vb** file in the **GettingStartedHost** project and replace its code with the following code:</span></span>

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
    
    <span data-ttu-id="baeae-144">Informace o tom, jak tento kód funguje, najdete v tématu věnovaném [postupům hostujícím programům](#service-hosting-program-steps).</span><span class="sxs-lookup"><span data-stu-id="baeae-144">For information about how this code works, see [Service hosting program steps](#service-hosting-program-steps).</span></span>

2. <span data-ttu-id="baeae-145">Aktualizujte vlastnosti projektu:</span><span class="sxs-lookup"><span data-stu-id="baeae-145">Update the project properties:</span></span>

   1. <span data-ttu-id="baeae-146">V okně **Průzkumník řešení** vyberte složku **GettingStartedHost** a potom v místní nabídce vyberte možnost **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="baeae-146">In the **Solution Explorer** window, select the **GettingStartedHost** folder, and then select **Properties** from the shortcut menu.</span></span>

   2. <span data-ttu-id="baeae-147">Na stránce vlastnosti **GettingStartedHost** vyberte kartu **aplikace** :</span><span class="sxs-lookup"><span data-stu-id="baeae-147">On the **GettingStartedHost** properties page, select the **Application** tab:</span></span>

      - <span data-ttu-id="baeae-148">V C# části projekty vyberte **GettingStartedHost. program** ze seznamu **spouštěcích objektů** .</span><span class="sxs-lookup"><span data-stu-id="baeae-148">For C# projects, select **GettingStartedHost.Program** from the **Startup object** list.</span></span>

      - <span data-ttu-id="baeae-149">U Visual Basic projektů vyberte ze seznamu **spouštěcí objekt** položku **Service. program** .</span><span class="sxs-lookup"><span data-stu-id="baeae-149">For Visual Basic projects, select **Service.Program** from the **Startup object** list.</span></span>

   3. <span data-ttu-id="baeae-150">V nabídce **soubor** vyberte **Uložit vše**.</span><span class="sxs-lookup"><span data-stu-id="baeae-150">From the **File** menu, select **Save All**.</span></span>

## <a name="verify-the-service-is-working"></a><span data-ttu-id="baeae-151">Ověření funkčnosti služby</span><span class="sxs-lookup"><span data-stu-id="baeae-151">Verify the service is working</span></span>

1. <span data-ttu-id="baeae-152">Sestavte řešení a potom spusťte konzolovou aplikaci **GettingStartedHost** ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="baeae-152">Build the solution, and then run the **GettingStartedHost** console application from inside Visual Studio.</span></span> 

    <span data-ttu-id="baeae-153">Služba musí být spuštěná s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="baeae-153">The service must be run with administrator privileges.</span></span> <span data-ttu-id="baeae-154">Vzhledem k tomu, že jste otevřeli aplikaci Visual Studio s oprávněními správce, při spuštění **GettingStartedHost** v aplikaci Visual Studio se aplikace spouští také s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="baeae-154">Because you opened Visual Studio with administrator privileges, when you run **GettingStartedHost** in Visual Studio, the application is run with administrator privileges as well.</span></span> <span data-ttu-id="baeae-155">Jako alternativu můžete otevřít nový příkazový řádek jako správce (v místní nabídce vyberte **Další** > **Spustit jako správce** ) a v něm spustit **GettingStartedHost. exe** .</span><span class="sxs-lookup"><span data-stu-id="baeae-155">As an alternative, you can open a new command prompt as an administrator (select **More** > **Run as administrator** from the shortcut menu) and run **GettingStartedHost.exe** within it.</span></span>

2. <span data-ttu-id="baeae-156">Otevřete webový prohlížeč a přejděte na stránku služby na adrese `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="baeae-156">Open a web browser and browse to the service's page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>
   
   > [!NOTE]
   > <span data-ttu-id="baeae-157">Služby, jako je tato jedna, vyžadují správné oprávnění k registraci adres HTTP na počítači pro naslouchání.</span><span class="sxs-lookup"><span data-stu-id="baeae-157">Services such as this one require the proper permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="baeae-158">Účty správců mají toto oprávnění, ale účty bez oprávnění správce musí mít udělené oprávnění pro obory názvů HTTP.</span><span class="sxs-lookup"><span data-stu-id="baeae-158">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="baeae-159">Další informace o tom, jak nakonfigurovat rezervace oboru názvů, najdete v tématu [Konfigurace HTTP a HTTPS](feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="baeae-159">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](feature-details/configuring-http-and-https.md).</span></span> 

## <a name="service-hosting-program-steps"></a><span data-ttu-id="baeae-160">Kroky hostujícího programu služby</span><span class="sxs-lookup"><span data-stu-id="baeae-160">Service hosting program steps</span></span>

<span data-ttu-id="baeae-161">Kroky v kódu, který jste přidali k hostování služby, jsou popsány takto:</span><span class="sxs-lookup"><span data-stu-id="baeae-161">The steps in the code you added to host the service are described as follows:</span></span>

- <span data-ttu-id="baeae-162">**Krok 1**: Vytvořte instanci `Uri` třídy, která bude uchovávat základní adresu služby.</span><span class="sxs-lookup"><span data-stu-id="baeae-162">**Step 1**: Create an instance of the `Uri` class to hold the base address of the service.</span></span> <span data-ttu-id="baeae-163">Adresa URL, která obsahuje základní adresu, má volitelný identifikátor URI, který identifikuje službu.</span><span class="sxs-lookup"><span data-stu-id="baeae-163">A URL that contains a base address has an optional URI that identifies a service.</span></span> <span data-ttu-id="baeae-164">Základní adresa je formátována takto: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span><span class="sxs-lookup"><span data-stu-id="baeae-164">The base address is formatted as follows: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span></span> <span data-ttu-id="baeae-165">Základní adresa služby kalkulačky používá přenos HTTP, localhost, port 8000 a segment identifikátoru URI soubor GettingStarted.</span><span class="sxs-lookup"><span data-stu-id="baeae-165">The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment, GettingStarted.</span></span>

- <span data-ttu-id="baeae-166">**Krok 2**: Vytvořte instanci <xref:System.ServiceModel.ServiceHost> třídy, kterou použijete k hostování služby.</span><span class="sxs-lookup"><span data-stu-id="baeae-166">**Step 2**: Create an instance of the <xref:System.ServiceModel.ServiceHost> class, which you use to host the service.</span></span> <span data-ttu-id="baeae-167">Konstruktor přijímá dva parametry: typ třídy, která implementuje kontrakt služby a základní adresu služby.</span><span class="sxs-lookup"><span data-stu-id="baeae-167">The constructor takes two parameters: the type of the class that implements the service contract and the base address of the service.</span></span>

- <span data-ttu-id="baeae-168">**Krok 3**: <xref:System.ServiceModel.Description.ServiceEndpoint> Vytvořte instanci.</span><span class="sxs-lookup"><span data-stu-id="baeae-168">**Step 3**: Create a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="baeae-169">Koncový bod služby se skládá z adresy, vazby a kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="baeae-169">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="baeae-170"><xref:System.ServiceModel.Description.ServiceEndpoint> Konstruktor se skládá z typu rozhraní kontraktu služby, vazby a adresy.</span><span class="sxs-lookup"><span data-stu-id="baeae-170">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor is composed of the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="baeae-171">Kontrakt služby je `ICalculator`, který jste definovali a implementovali v typu služby.</span><span class="sxs-lookup"><span data-stu-id="baeae-171">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="baeae-172">Vazba pro tuto ukázku je <xref:System.ServiceModel.WSHttpBinding>, což je integrovaná vazba a připojuje se k koncovým bodům, které odpovídají specifikacím WS-\*.</span><span class="sxs-lookup"><span data-stu-id="baeae-172">The binding for this sample is <xref:System.ServiceModel.WSHttpBinding>, which is a built-in binding and connects to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="baeae-173">Další informace o vazbách WCF najdete v tématu [Přehled vazeb WCF](bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="baeae-173">For more information about WCF bindings, see [WCF bindings overview](bindings-overview.md).</span></span> <span data-ttu-id="baeae-174">K identifikaci koncového bodu připojíte adresu k základní adrese.</span><span class="sxs-lookup"><span data-stu-id="baeae-174">You append the address to the base address to identify the endpoint.</span></span> <span data-ttu-id="baeae-175">Kód určuje adresu jako CalculatorService a plně kvalifikovanou adresu koncového bodu jako `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="baeae-175">The code specifies the address as CalculatorService and the fully qualified address for the endpoint as `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="baeae-176">Pro .NET Framework verze 4 a novější je přidání koncového bodu služby volitelné.</span><span class="sxs-lookup"><span data-stu-id="baeae-176">For .NET Framework Version 4 and later, adding a service endpoint is optional.</span></span> <span data-ttu-id="baeae-177">Pro tyto verze, pokud nepřidáte kód nebo konfiguraci, WCF přidá jeden výchozí koncový bod pro každou kombinaci základní adresy a smlouvy implementované službou.</span><span class="sxs-lookup"><span data-stu-id="baeae-177">For these versions, if you don't add your code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="baeae-178">Další informace o výchozích koncových bodech najdete v tématu [určení adresy koncového bodu](specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="baeae-178">For more information about default endpoints, see [Specifying an endpoint address](specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="baeae-179">Další informace o výchozích koncových bodech, vazbách a chování najdete v tématu [zjednodušená konfigurace](simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="baeae-179">For more information about default endpoints, bindings, and behaviors, see [Simplified configuration](simplified-configuration.md) and [Simplified configuration for WCF services](samples/simplified-configuration-for-wcf-services.md).</span></span>

- <span data-ttu-id="baeae-180">**Krok 4**: Povolte výměnu metadat.</span><span class="sxs-lookup"><span data-stu-id="baeae-180">**Step 4**: Enable metadata exchange.</span></span> <span data-ttu-id="baeae-181">Klienti používají výměnu metadat k vygenerování proxy serverů pro volání operací služby.</span><span class="sxs-lookup"><span data-stu-id="baeae-181">Clients use metadata exchange to generate proxies for calling the service operations.</span></span> <span data-ttu-id="baeae-182">Chcete-li povolit výměnu metadat, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> vytvořte instanci, nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> její vlastnost `true` `ServiceMetadataBehavior` na a <xref:System.ServiceModel.ServiceHost> přidejte objekt do <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekce instance.</span><span class="sxs-lookup"><span data-stu-id="baeae-182">To enable metadata exchange, create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set its <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> property to `true`, and add the `ServiceMetadataBehavior` object to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

- <span data-ttu-id="baeae-183">**Krok 5**: Otevřete <xref:System.ServiceModel.ServiceHost> pro příjem příchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="baeae-183">**Step 5**: Open <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="baeae-184">Aplikace čeká na stisknutí klávesy **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="baeae-184">The application waits for you to press **Enter**.</span></span> <span data-ttu-id="baeae-185">Po vytvoření instance <xref:System.ServiceModel.ServiceHost>aplikace se spustí blok try/catch.</span><span class="sxs-lookup"><span data-stu-id="baeae-185">After the application instantiates <xref:System.ServiceModel.ServiceHost>, it executes a try/catch block.</span></span> <span data-ttu-id="baeae-186">Další informace o bezpečném zachycení výjimek vyvolaných <xref:System.ServiceModel.ServiceHost>naleznete v tématu [použití funkcí zavřít a přerušit k vydání prostředků klienta WCF](samples/use-close-abort-release-wcf-client-resources.md).</span><span class="sxs-lookup"><span data-stu-id="baeae-186">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Use Close and Abort to release WCF client resources](samples/use-close-abort-release-wcf-client-resources.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="baeae-187">Když přidáte knihovnu služby WCF, Visual Studio ji hostuje za vás, pokud ji ladíte spuštěním hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="baeae-187">When you add a WCF service library, Visual Studio hosts it for you if you debug it by starting a service host.</span></span> <span data-ttu-id="baeae-188">Aby nedocházelo ke konfliktům, můžete aplikaci Visual Studio zabránit v hostování knihovny služby WCF.</span><span class="sxs-lookup"><span data-stu-id="baeae-188">To avoid conflicts, you can prevent Visual Studio from hosting the WCF service library.</span></span> 
>
> 1. <span data-ttu-id="baeae-189">V **Průzkumník řešení** vyberte projekt **GettingStartedLib** a v místní nabídce vyberte **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="baeae-189">Select the **GettingStartedLib** project in **Solution Explorer** and choose **Properties** from the shortcut menu.</span></span>
> 2. <span data-ttu-id="baeae-190">Vyberte **možnost WCF možnosti** a zrušte zaškrtnutí políčka **spustit hostitele služby WCF při ladění jiného projektu ve stejném řešení**.</span><span class="sxs-lookup"><span data-stu-id="baeae-190">Select **WCF Options** and uncheck **Start WCF Service Host when debugging another project in the same solution**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="baeae-191">Další postup</span><span class="sxs-lookup"><span data-stu-id="baeae-191">Next steps</span></span>

<span data-ttu-id="baeae-192">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="baeae-192">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="baeae-193">Vytvořte a nakonfigurujte projekt konzolové aplikace pro hostování služby WCF.</span><span class="sxs-lookup"><span data-stu-id="baeae-193">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="baeae-194">Přidejte kód pro hostování služby WCF.</span><span class="sxs-lookup"><span data-stu-id="baeae-194">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="baeae-195">Aktualizujte konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="baeae-195">Update the configuration file.</span></span>
> - <span data-ttu-id="baeae-196">Spusťte službu WCF a ověřte, zda je spuštěná.</span><span class="sxs-lookup"><span data-stu-id="baeae-196">Start the WCF service and verify it's running.</span></span>

<span data-ttu-id="baeae-197">Přejděte k dalšímu kurzu, kde se dozvíte, jak vytvořit klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="baeae-197">Advance to the next tutorial to learn how to create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="baeae-198">Kurz: Vytvoření klienta WCF</span><span class="sxs-lookup"><span data-stu-id="baeae-198">Tutorial: Create a WCF client</span></span>](how-to-create-a-wcf-client.md)
