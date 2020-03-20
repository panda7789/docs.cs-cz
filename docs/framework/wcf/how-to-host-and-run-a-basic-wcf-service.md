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
ms.openlocfilehash: 30eb86987b83427b94c6fff22755cde3d73dd9f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184073"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="1c17d-102">Kurz: Hostování a spuštění základní služby Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="1c17d-102">Tutorial: Host and run a basic Windows Communication Foundation service</span></span>

<span data-ttu-id="1c17d-103">Tento kurz popisuje třetí z pěti úloh potřebných k vytvoření základní aplikace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1c17d-103">This tutorial describes the third of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="1c17d-104">Přehled výukových programů najdete v [tématu Výuka: Začínáme s aplikacemi Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="1c17d-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="1c17d-105">Dalším úkolem pro vytvoření aplikace WCF je hostování služby WCF v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1c17d-105">The next task for creating a WCF application is to host a WCF service in a console application.</span></span> <span data-ttu-id="1c17d-106">Služba WCF zpřístupňuje jeden nebo více *koncových bodů*, z nichž každý zpřístupňuje jednu nebo více operací služby.</span><span class="sxs-lookup"><span data-stu-id="1c17d-106">A WCF service exposes one or more *endpoints*, each of which exposes one or more service operations.</span></span> <span data-ttu-id="1c17d-107">Koncový bod služby určuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="1c17d-107">A service endpoint specifies the following information:</span></span>

- <span data-ttu-id="1c17d-108">Adresa, na které můžete najít službu.</span><span class="sxs-lookup"><span data-stu-id="1c17d-108">An address where you can find the service.</span></span>
- <span data-ttu-id="1c17d-109">Vazba, která obsahuje informace, které popisují, jak klient musí komunikovat se službou.</span><span class="sxs-lookup"><span data-stu-id="1c17d-109">A binding that contains the information that describes how a client must communicate with the service.</span></span>
- <span data-ttu-id="1c17d-110">Smlouva, která definuje funkce, které služba poskytuje svým klientům.</span><span class="sxs-lookup"><span data-stu-id="1c17d-110">A contract that defines the functionality that the service provides to its clients.</span></span>

<span data-ttu-id="1c17d-111">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="1c17d-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="1c17d-112">Vytvořte a nakonfigurujte projekt konzolové aplikace pro hostování služby WCF.</span><span class="sxs-lookup"><span data-stu-id="1c17d-112">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="1c17d-113">Přidejte kód pro hostování služby WCF.</span><span class="sxs-lookup"><span data-stu-id="1c17d-113">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="1c17d-114">Aktualizujte konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="1c17d-114">Update the configuration file.</span></span>
> - <span data-ttu-id="1c17d-115">Spusťte službu WCF a ověřte, zda je spuštěná.</span><span class="sxs-lookup"><span data-stu-id="1c17d-115">Start the WCF service and verify it's running.</span></span>

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a><span data-ttu-id="1c17d-116">Vytvoření a konfigurace projektu konzolové aplikace pro hostování služby</span><span class="sxs-lookup"><span data-stu-id="1c17d-116">Create and configure a console app project for hosting the service</span></span>

1. <span data-ttu-id="1c17d-117">Vytvoření projektu konzolové aplikace v Sadě Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="1c17d-117">Create a console app project in Visual Studio:</span></span>

    1. <span data-ttu-id="1c17d-118">V nabídce **Soubor** vyberte **Otevřít** > **projekt/řešení** a přejděte k řešení **GettingStarted,** které jste dříve vytvořili (*GettingStarted.sln*).</span><span class="sxs-lookup"><span data-stu-id="1c17d-118">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="1c17d-119">Vyberte **Open** (Otevřít).</span><span class="sxs-lookup"><span data-stu-id="1c17d-119">Select **Open**.</span></span>

    2. <span data-ttu-id="1c17d-120">V nabídce **Zobrazení** vyberte **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="1c17d-120">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="1c17d-121">V okně **Průzkumník řešení** vyberte řešení **GettingStarted** (horní uzel) a pak v místní nabídce vyberte **Přidat** > **nový projekt.**</span><span class="sxs-lookup"><span data-stu-id="1c17d-121">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span>

    4. <span data-ttu-id="1c17d-122">V okně **Přidat nový projekt** na levé straně vyberte kategorii Plocha **systému Windows** v části Visual **C#** nebo **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="1c17d-122">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span>

    5. <span data-ttu-id="1c17d-123">Vyberte šablonu **Konzolové aplikace (.NET Framework)** a zadejte *GettingStartedHost* pro **název**.</span><span class="sxs-lookup"><span data-stu-id="1c17d-123">Select the **Console App (.NET Framework)** template, and enter *GettingStartedHost* for the **Name**.</span></span> <span data-ttu-id="1c17d-124">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="1c17d-124">Select **OK**.</span></span>

2. <span data-ttu-id="1c17d-125">Přidejte odkaz v projektu **GettingStartedHost** do projektu **GettingStartedLib:**</span><span class="sxs-lookup"><span data-stu-id="1c17d-125">Add a reference in the **GettingStartedHost** project to the **GettingStartedLib** project:</span></span>

    1. <span data-ttu-id="1c17d-126">V okně **Průzkumník řešení** vyberte složku **Reference v** projektu **GettingStartedHost** a pak v místní nabídce vyberte **Přidat odkaz.**</span><span class="sxs-lookup"><span data-stu-id="1c17d-126">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="1c17d-127">V dialogovém okně **Přidat odkaz** vyberte v části **Projekty** na levé straně okna **možnost Řešení**.</span><span class="sxs-lookup"><span data-stu-id="1c17d-127">In the **Add Reference** dialog, under **Projects** on the left side of the window, select **Solution**.</span></span>

    3. <span data-ttu-id="1c17d-128">Vprostřední části okna vyberte **GettingStartedLib** a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="1c17d-128">Select **GettingStartedLib** in the center section of the window, and then select **OK**.</span></span>

       <span data-ttu-id="1c17d-129">Tato akce zpřístupní typy definované v projektu **GettingStartedLib** projektu **GettingStartedHost pro projekt GettingStartedHost.**</span><span class="sxs-lookup"><span data-stu-id="1c17d-129">This action makes the types defined in the **GettingStartedLib** project available to the **GettingStartedHost** project.</span></span>

3. <span data-ttu-id="1c17d-130">Přidejte odkaz v projektu **GettingStartedHost** do <xref:System.ServiceModel> sestavení:</span><span class="sxs-lookup"><span data-stu-id="1c17d-130">Add a reference in the **GettingStartedHost** project to the <xref:System.ServiceModel> assembly:</span></span>

    1. <span data-ttu-id="1c17d-131">V okně **Průzkumník řešení** vyberte složku **Reference v** projektu **GettingStartedHost** a pak v místní nabídce vyberte **Přidat odkaz.**</span><span class="sxs-lookup"><span data-stu-id="1c17d-131">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="1c17d-132">V okně **Přidat odkaz** vyberte v části **Sestavení** na levé straně okna **možnost Framework**.</span><span class="sxs-lookup"><span data-stu-id="1c17d-132">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>

    3. <span data-ttu-id="1c17d-133">Vyberte **Položku System.ServiceModel**a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="1c17d-133">Select **System.ServiceModel**, and then select **OK**.</span></span>

    4. <span data-ttu-id="1c17d-134">Uložte řešení výběrem **možnosti Uložit** > **vše**.</span><span class="sxs-lookup"><span data-stu-id="1c17d-134">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="add-code-to-host-the-service"></a><span data-ttu-id="1c17d-135">Přidání kódu pro hostování služby</span><span class="sxs-lookup"><span data-stu-id="1c17d-135">Add code to host the service</span></span>

<span data-ttu-id="1c17d-136">Chcete-li službu hostovat, přidejte kód, který provede následující kroky:</span><span class="sxs-lookup"><span data-stu-id="1c17d-136">To host the service, you add code to do the following steps:</span></span>

1. <span data-ttu-id="1c17d-137">Vytvořte identifikátor URI pro základní adresu.</span><span class="sxs-lookup"><span data-stu-id="1c17d-137">Create a URI for the base address.</span></span>
2. <span data-ttu-id="1c17d-138">Vytvořte instanci třídy pro hostování služby.</span><span class="sxs-lookup"><span data-stu-id="1c17d-138">Create a class instance for hosting the service.</span></span>
3. <span data-ttu-id="1c17d-139">Vytvořte koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="1c17d-139">Create a service endpoint.</span></span>
4. <span data-ttu-id="1c17d-140">Povolte výměnu metadat.</span><span class="sxs-lookup"><span data-stu-id="1c17d-140">Enable metadata exchange.</span></span>
5. <span data-ttu-id="1c17d-141">Otevřete hostitele služby a poslouchejte příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="1c17d-141">Open the service host to listen for incoming messages.</span></span>
  
<span data-ttu-id="1c17d-142">Proveďte následující změny kódu:</span><span class="sxs-lookup"><span data-stu-id="1c17d-142">Make the following changes to the code:</span></span>

1. <span data-ttu-id="1c17d-143">Otevřete soubor **Program.cs** nebo **Module1.vb** v projektu **GettingStartedHost** a nahraďte jeho kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="1c17d-143">Open the **Program.cs** or **Module1.vb** file in the **GettingStartedHost** project and replace its code with the following code:</span></span>

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

    <span data-ttu-id="1c17d-144">Informace o tom, jak tento kód funguje, naleznete [v tématu Service hosting program steps](#service-hosting-program-steps).</span><span class="sxs-lookup"><span data-stu-id="1c17d-144">For information about how this code works, see [Service hosting program steps](#service-hosting-program-steps).</span></span>

2. <span data-ttu-id="1c17d-145">Aktualizace vlastností projektu:</span><span class="sxs-lookup"><span data-stu-id="1c17d-145">Update the project properties:</span></span>

   1. <span data-ttu-id="1c17d-146">V okně **Průzkumník řešení** vyberte složku **GettingStartedHost** a pak v místní nabídce vyberte **Vlastnosti.**</span><span class="sxs-lookup"><span data-stu-id="1c17d-146">In the **Solution Explorer** window, select the **GettingStartedHost** folder, and then select **Properties** from the shortcut menu.</span></span>

   2. <span data-ttu-id="1c17d-147">Na stránce **Vlastností GettingStartedHost** vyberte kartu **Aplikace:**</span><span class="sxs-lookup"><span data-stu-id="1c17d-147">On the **GettingStartedHost** properties page, select the **Application** tab:</span></span>

      - <span data-ttu-id="1c17d-148">U projektů jazyka C# vyberte **gettingstartedhost.program** ze seznamu **spouštěcích objektů.**</span><span class="sxs-lookup"><span data-stu-id="1c17d-148">For C# projects, select **GettingStartedHost.Program** from the **Startup object** list.</span></span>

      - <span data-ttu-id="1c17d-149">U projektů jazyka Visual Basic vyberte **service.program** ze seznamu **spouštěcích objektů.**</span><span class="sxs-lookup"><span data-stu-id="1c17d-149">For Visual Basic projects, select **Service.Program** from the **Startup object** list.</span></span>

   3. <span data-ttu-id="1c17d-150">V nabídce **Soubor** vyberte **Uložit vše**.</span><span class="sxs-lookup"><span data-stu-id="1c17d-150">From the **File** menu, select **Save All**.</span></span>

## <a name="verify-the-service-is-working"></a><span data-ttu-id="1c17d-151">Ověřte, zda služba funguje</span><span class="sxs-lookup"><span data-stu-id="1c17d-151">Verify the service is working</span></span>

1. <span data-ttu-id="1c17d-152">Sestavte řešení a spusťte konzolovou aplikaci **GettingStartedHost** z aplikace Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1c17d-152">Build the solution, and then run the **GettingStartedHost** console application from inside Visual Studio.</span></span>

    <span data-ttu-id="1c17d-153">Služba musí být spuštěna s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="1c17d-153">The service must be run with administrator privileges.</span></span> <span data-ttu-id="1c17d-154">Vzhledem k tomu, že jste otevřeli Visual Studio s oprávněními správce, při spuštění **GettingStartedHost** v sadě Visual Studio je aplikace spuštěna také s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="1c17d-154">Because you opened Visual Studio with administrator privileges, when you run **GettingStartedHost** in Visual Studio, the application is run with administrator privileges as well.</span></span> <span data-ttu-id="1c17d-155">Jako alternativu můžete otevřít nový příkazový řádek jako správce (v místní nabídce vyberte **možnost Další** > **spuštění jako správce)** a spustit v něm soubor **GettingStartedHost.exe.**</span><span class="sxs-lookup"><span data-stu-id="1c17d-155">As an alternative, you can open a new command prompt as an administrator (select **More** > **Run as administrator** from the shortcut menu) and run **GettingStartedHost.exe** within it.</span></span>

2. <span data-ttu-id="1c17d-156">Otevřete webový prohlížeč a přejděte na `http://localhost:8000/GettingStarted/CalculatorService`stránku služby na adrese .</span><span class="sxs-lookup"><span data-stu-id="1c17d-156">Open a web browser and browse to the service's page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

   > [!NOTE]
   > <span data-ttu-id="1c17d-157">Služby, jako je tento, vyžadují řádné oprávnění k registraci adres HTTP v počítači pro naslouchání.</span><span class="sxs-lookup"><span data-stu-id="1c17d-157">Services such as this one require the proper permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="1c17d-158">Účty správce mají toto oprávnění, ale účty bez oprávnění správce musí být uděleno oprávnění pro obory názvů HTTP.</span><span class="sxs-lookup"><span data-stu-id="1c17d-158">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="1c17d-159">Další informace o konfiguraci rezervací oboru názvů naleznete v [tématu Konfigurace protokolů HTTP a HTTPS](feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="1c17d-159">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](feature-details/configuring-http-and-https.md).</span></span>

## <a name="service-hosting-program-steps"></a><span data-ttu-id="1c17d-160">Kroky programu hostování služeb</span><span class="sxs-lookup"><span data-stu-id="1c17d-160">Service hosting program steps</span></span>

<span data-ttu-id="1c17d-161">Kroky v kódu, který jste přidali k hostiteli služby jsou popsány takto:</span><span class="sxs-lookup"><span data-stu-id="1c17d-161">The steps in the code you added to host the service are described as follows:</span></span>

- <span data-ttu-id="1c17d-162">**Krok 1**: Vytvořte `Uri` instanci třídy pro uložení základní adresy služby.</span><span class="sxs-lookup"><span data-stu-id="1c17d-162">**Step 1**: Create an instance of the `Uri` class to hold the base address of the service.</span></span> <span data-ttu-id="1c17d-163">Adresa URL, která obsahuje základní adresu, má volitelný identifikátor URI, který identifikuje službu.</span><span class="sxs-lookup"><span data-stu-id="1c17d-163">A URL that contains a base address has an optional URI that identifies a service.</span></span> <span data-ttu-id="1c17d-164">Základní adresa je formátována `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`takto: .</span><span class="sxs-lookup"><span data-stu-id="1c17d-164">The base address is formatted as follows: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span></span> <span data-ttu-id="1c17d-165">Základní adresa pro službu kalkulačky používá přenos HTTP, localhost, port 8000 a segment URI GettingStarted.</span><span class="sxs-lookup"><span data-stu-id="1c17d-165">The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment, GettingStarted.</span></span>

- <span data-ttu-id="1c17d-166">**Krok 2**: Vytvořte <xref:System.ServiceModel.ServiceHost> instanci třídy, kterou používáte k hostování služby.</span><span class="sxs-lookup"><span data-stu-id="1c17d-166">**Step 2**: Create an instance of the <xref:System.ServiceModel.ServiceHost> class, which you use to host the service.</span></span> <span data-ttu-id="1c17d-167">Konstruktor má dva parametry: typ třídy, která implementuje servisní smlouvu a základní adresu služby.</span><span class="sxs-lookup"><span data-stu-id="1c17d-167">The constructor takes two parameters: the type of the class that implements the service contract and the base address of the service.</span></span>

- <span data-ttu-id="1c17d-168">**Krok 3**: <xref:System.ServiceModel.Description.ServiceEndpoint> Vytvoření instance.</span><span class="sxs-lookup"><span data-stu-id="1c17d-168">**Step 3**: Create a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="1c17d-169">Koncový bod služby se skládá z adresy, vazby a smlouvy o poskytování služeb.</span><span class="sxs-lookup"><span data-stu-id="1c17d-169">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="1c17d-170">Konstruktor <xref:System.ServiceModel.Description.ServiceEndpoint> se skládá z typu rozhraní servisní smlouvy, vazby a adresy.</span><span class="sxs-lookup"><span data-stu-id="1c17d-170">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor is composed of the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="1c17d-171">Servisní smlouva `ICalculator`je , kterou jste definovali a implementovali v typu služby.</span><span class="sxs-lookup"><span data-stu-id="1c17d-171">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="1c17d-172">Vazba pro tuto <xref:System.ServiceModel.WSHttpBinding>ukázku je , což je vestavěná vazba a připojuje se ke koncovým bodům, které odpovídají specifikacím WS-\*.</span><span class="sxs-lookup"><span data-stu-id="1c17d-172">The binding for this sample is <xref:System.ServiceModel.WSHttpBinding>, which is a built-in binding and connects to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="1c17d-173">Další informace o vazby WCF naleznete v tématu [Přehled vazby WCF](bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1c17d-173">For more information about WCF bindings, see [WCF bindings overview](bindings-overview.md).</span></span> <span data-ttu-id="1c17d-174">Připojíte adresu k základní adrese k identifikaci koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="1c17d-174">You append the address to the base address to identify the endpoint.</span></span> <span data-ttu-id="1c17d-175">Kód určuje adresu jako CalculatorService a plně kvalifikovanou adresu `http://localhost:8000/GettingStarted/CalculatorService`pro koncový bod jako .</span><span class="sxs-lookup"><span data-stu-id="1c17d-175">The code specifies the address as CalculatorService and the fully qualified address for the endpoint as `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="1c17d-176">Pro rozhraní .NET Framework verze 4 a novější je přidání koncového bodu služby volitelné.</span><span class="sxs-lookup"><span data-stu-id="1c17d-176">For .NET Framework Version 4 and later, adding a service endpoint is optional.</span></span> <span data-ttu-id="1c17d-177">Pro tyto verze, pokud nepřidáte kód nebo konfiguraci, WCF přidá jeden výchozí koncový bod pro každou kombinaci základní adresy a smlouvy implementované službou.</span><span class="sxs-lookup"><span data-stu-id="1c17d-177">For these versions, if you don't add your code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="1c17d-178">Další informace o výchozích koncových bodech naleznete [v tématu Určení adresy koncového bodu](specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="1c17d-178">For more information about default endpoints, see [Specifying an endpoint address](specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="1c17d-179">Další informace o výchozích koncových bodech, vazbách a chování naleznete v [tématu Zjednodušená konfigurace](simplified-configuration.md) a [Zjednodušená konfigurace pro služby WCF](samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="1c17d-179">For more information about default endpoints, bindings, and behaviors, see [Simplified configuration](simplified-configuration.md) and [Simplified configuration for WCF services](samples/simplified-configuration-for-wcf-services.md).</span></span>

- <span data-ttu-id="1c17d-180">**Krok 4**: Povolit výměnu metadat.</span><span class="sxs-lookup"><span data-stu-id="1c17d-180">**Step 4**: Enable metadata exchange.</span></span> <span data-ttu-id="1c17d-181">Klienti používají výměnu metadat ke generování proxy serverů pro volání operací služby.</span><span class="sxs-lookup"><span data-stu-id="1c17d-181">Clients use metadata exchange to generate proxies for calling the service operations.</span></span> <span data-ttu-id="1c17d-182">Chcete-li povolit výměnu <xref:System.ServiceModel.Description.ServiceMetadataBehavior> metadat, <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> vytvořte `true`instanci, nastavte její vlastnost na a přidejte `ServiceMetadataBehavior` objekt do <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekce <xref:System.ServiceModel.ServiceHost> instance.</span><span class="sxs-lookup"><span data-stu-id="1c17d-182">To enable metadata exchange, create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set its <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> property to `true`, and add the `ServiceMetadataBehavior` object to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

- <span data-ttu-id="1c17d-183">**Krok 5** <xref:System.ServiceModel.ServiceHost> : Otevřete pro poslech příchozích zpráv.</span><span class="sxs-lookup"><span data-stu-id="1c17d-183">**Step 5**: Open <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="1c17d-184">Aplikace čeká, až stisknete **klávesu Enter**.</span><span class="sxs-lookup"><span data-stu-id="1c17d-184">The application waits for you to press **Enter**.</span></span> <span data-ttu-id="1c17d-185">Poté, co aplikace <xref:System.ServiceModel.ServiceHost>instance , provede try/catch bloku.</span><span class="sxs-lookup"><span data-stu-id="1c17d-185">After the application instantiates <xref:System.ServiceModel.ServiceHost>, it executes a try/catch block.</span></span> <span data-ttu-id="1c17d-186">Další informace o bezpečném zachycení <xref:System.ServiceModel.ServiceHost>výjimek vyvolaných aplikacemi naleznete [v tématu Použití zavřít a přerušit uvolnění klientských prostředků WCF](samples/use-close-abort-release-wcf-client-resources.md).</span><span class="sxs-lookup"><span data-stu-id="1c17d-186">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Use Close and Abort to release WCF client resources](samples/use-close-abort-release-wcf-client-resources.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1c17d-187">Když přidáte knihovnu služeb WCF, Visual Studio ji hostuje za vás, pokud ji ladíte spuštěním hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="1c17d-187">When you add a WCF service library, Visual Studio hosts it for you if you debug it by starting a service host.</span></span> <span data-ttu-id="1c17d-188">Chcete-li se vyhnout konfliktům, můžete zabránit visual studio hostování knihovny služeb WCF.</span><span class="sxs-lookup"><span data-stu-id="1c17d-188">To avoid conflicts, you can prevent Visual Studio from hosting the WCF service library.</span></span>
>
> 1. <span data-ttu-id="1c17d-189">V průzkumníku **řešení** vyberte projekt **GettingStartedLib** a z místní nabídky zvolte **Vlastnosti.**</span><span class="sxs-lookup"><span data-stu-id="1c17d-189">Select the **GettingStartedLib** project in **Solution Explorer** and choose **Properties** from the shortcut menu.</span></span>
> 2. <span data-ttu-id="1c17d-190">Vyberte **možnosti WCF** a zrušte zaškrtnutí **políčka Spustit hostitele služby WCF při ladění jiného projektu ve stejném řešení**.</span><span class="sxs-lookup"><span data-stu-id="1c17d-190">Select **WCF Options** and uncheck **Start WCF Service Host when debugging another project in the same solution**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1c17d-191">Další kroky</span><span class="sxs-lookup"><span data-stu-id="1c17d-191">Next steps</span></span>

<span data-ttu-id="1c17d-192">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="1c17d-192">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="1c17d-193">Vytvořte a nakonfigurujte projekt konzolové aplikace pro hostování služby WCF.</span><span class="sxs-lookup"><span data-stu-id="1c17d-193">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="1c17d-194">Přidejte kód pro hostování služby WCF.</span><span class="sxs-lookup"><span data-stu-id="1c17d-194">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="1c17d-195">Aktualizujte konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="1c17d-195">Update the configuration file.</span></span>
> - <span data-ttu-id="1c17d-196">Spusťte službu WCF a ověřte, zda je spuštěná.</span><span class="sxs-lookup"><span data-stu-id="1c17d-196">Start the WCF service and verify it's running.</span></span>

<span data-ttu-id="1c17d-197">Přejdete k dalšímu kurzu, který se dozvíte, jak vytvořit klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="1c17d-197">Advance to the next tutorial to learn how to create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1c17d-198">Kurz: Vytvoření klienta WCF</span><span class="sxs-lookup"><span data-stu-id="1c17d-198">Tutorial: Create a WCF client</span></span>](how-to-create-a-wcf-client.md)
