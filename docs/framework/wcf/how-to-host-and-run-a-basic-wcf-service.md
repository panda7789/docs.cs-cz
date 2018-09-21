---
title: 'Postupy: Hostování a spuštění základní služby Windows Communication Foundation Service'
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: b79c3246b7c12a3a99a5c68586387fc30573dcb6
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46562291"
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="b5d7b-102">Postupy: Hostování a spuštění základní služby Windows Communication Foundation Service</span><span class="sxs-lookup"><span data-stu-id="b5d7b-102">How to: Host and Run a Basic Windows Communication Foundation Service</span></span>

<span data-ttu-id="b5d7b-103">Toto je třetí webinář z šesti úkolů potřebný k vytvoření aplikace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b5d7b-103">This is the third of six tasks required to create a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="b5d7b-104">Přehled všech šesti úkoly, naleznete v tématu [kurz Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>

<span data-ttu-id="b5d7b-105">Toto téma popisuje, jak k hostování služby Windows Communication Foundation (WCF) v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-105">This topic describes how to host a Windows Communication Foundation (WCF) service in a console application.</span></span> <span data-ttu-id="b5d7b-106">Tento postup se skládá z následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="b5d7b-106">This procedure consists of the following steps:</span></span>

- <span data-ttu-id="b5d7b-107">Vytvořte projekt konzolové aplikace pro hostování služby.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-107">Create a console application project to host the service.</span></span>

- <span data-ttu-id="b5d7b-108">Vytvořte hostitelskou služby pro službu.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-108">Create a service host for the service.</span></span>

- <span data-ttu-id="b5d7b-109">Povolte výměny metadat.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-109">Enable metadata exchange.</span></span>

- <span data-ttu-id="b5d7b-110">Otevření hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-110">Open the service host.</span></span>

<span data-ttu-id="b5d7b-111">Úplný kód napsaný v této úloze je najdete v příkladu za postupem.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-111">A complete listing of the code written in this task is provided in the example following the procedure.</span></span>

## <a name="create-a-new-console-application-to-host-the-service"></a><span data-ttu-id="b5d7b-112">Vytvořte novou konzolovou aplikaci pro hostování služby</span><span class="sxs-lookup"><span data-stu-id="b5d7b-112">Create a new console application to host the service</span></span>

1. <span data-ttu-id="b5d7b-113">Vytvořte nový projekt konzolové aplikace v sadě Visual Studio tak, že kliknete pravým tlačítkem na řešení Začínáme a vyberete **přidat** > **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-113">Create a new Console Application project in Visual Studio by right-clicking on the Getting Started solution and selecting **Add** > **New Project**.</span></span> <span data-ttu-id="b5d7b-114">V **přidat nový projekt** dialogového okna na levé straně, vyberte **Windows Desktop** kategorie v části **Visual C#** nebo **jazyka Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-114">In the **Add New Project** dialog, on the left-hand side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> <span data-ttu-id="b5d7b-115">Vyberte **Konzolová aplikace (.NET Framework)** šablony a poté pojmenujte projekt **GettingStartedHost**.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-115">Select the **Console App (.NET Framework)** template, and then name the project **GettingStartedHost**.</span></span>

2. <span data-ttu-id="b5d7b-116">Přidáte odkaz na projekt GettingStartedLib GettingStartedHost projektu.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-116">Add a reference to the GettingStartedLib project to the GettingStartedHost project.</span></span> <span data-ttu-id="b5d7b-117">Klikněte pravým tlačítkem na **odkazy** ve složce projektu GettingStartedHost v **Průzkumníka řešení**a pak vyberte **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-117">Right-click on the **References** folder under the GettingStartedHost project in **Solution Explorer**, and then select **Add Reference**.</span></span> <span data-ttu-id="b5d7b-118">V **přidat odkaz** dialogového okna, vyberte **řešení** na levé straně dialogového okna, vyberte GettingStartedLib v System center části dialogového okna a pak zvolte **přidat**.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-118">In the **Add Reference** dialog, select **Solution** on the left-hand side of the dialog, select GettingStartedLib in the center section of the dialog, and then choose **Add**.</span></span> <span data-ttu-id="b5d7b-119">Díky tomu typy definované v GettingStartedLib GettingStartedHost projektu k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-119">This makes the types defined in GettingStartedLib available to the GettingStartedHost project.</span></span>

3. <span data-ttu-id="b5d7b-120">Přidáte odkaz na System.ServiceModel GettingStartedHost projektu.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-120">Add a reference to System.ServiceModel to the GettingStartedHost project.</span></span> <span data-ttu-id="b5d7b-121">Klikněte pravým tlačítkem myši **odkazy** ve složce projektu GettingStartedHost v **Průzkumníku řešení** a vyberte **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-121">Right-click the **References** folder under the GettingStartedHost project in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="b5d7b-122">V **přidat odkaz** dialogového okna, vyberte **Framework** na levé straně dialogového okna v části **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-122">In the **Add Reference** dialog, select **Framework** on the left-hand side of the dialog under **Assemblies**.</span></span> <span data-ttu-id="b5d7b-123">Vyhledejte a vyberte **System.ServiceModel**a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-123">Find and select **System.ServiceModel**, and then choose **OK**.</span></span> <span data-ttu-id="b5d7b-124">Uložte řešení tak, že vyberete **souboru** > **Uložit vše**.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-124">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="host-the-service"></a><span data-ttu-id="b5d7b-125">Hostitel služby</span><span class="sxs-lookup"><span data-stu-id="b5d7b-125">Host the service</span></span>

<span data-ttu-id="b5d7b-126">Otevřete soubor Program.cs nebo Module.vb a zadejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="b5d7b-126">Open the Program.cs or Module.vb file and enter the following code:</span></span>

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

<span data-ttu-id="b5d7b-127">**Krok 1** -vytvoří instanci třídy Uri k umístění základní adresu služby.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-127">**Step 1** - Creates an instance of the Uri class to hold the base address of the service.</span></span> <span data-ttu-id="b5d7b-128">Služby jsou označeny adresu URL, která obsahuje základní adresu a volitelné identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-128">Services are identified by a URL which contains a base address and an optional URI.</span></span> <span data-ttu-id="b5d7b-129">Základní adresa naformátován takto: [přenosu] :// [název počítače nebo domény] [: volitelné port č] / [volitelný segment identifikátoru URI] základní adresa pro službu kalkulačky používá přenos pomocí protokolu HTTP, místního hostitele, port 8000 a identifikátor URI segmentovat "GettingStarted"</span><span class="sxs-lookup"><span data-stu-id="b5d7b-129">The base address is formatted as follows:[transport]://[machine-name or domain][:optional port #]/[optional URI segment]The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment "GettingStarted"</span></span>

<span data-ttu-id="b5d7b-130">**Krok 2** – vytvoří instanci <xref:System.ServiceModel.ServiceHost> třídy pro hostování služby.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-130">**Step 2** – Creates an instance of the <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="b5d7b-131">Konstruktor přijímá dva parametry typu třídy, která implementuje kontrakt služby a základní adresu služby.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-131">The constructor takes two parameters, the type of the class that implements the service contract, and the base address of the service.</span></span>

<span data-ttu-id="b5d7b-132">**Krok 3** – vytvoří <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-132">**Step 3** – Creates a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="b5d7b-133">Koncový bod služby se skládá z adresy, vazby a smlouvy o poskytování služeb.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-133">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="b5d7b-134"><xref:System.ServiceModel.Description.ServiceEndpoint> Konstruktor proto přebírá typ rozhraní kontraktu služby, vazbu a adresu.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-134">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor therefore takes the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="b5d7b-135">Kontrakt služby je `ICalculator`, která definované a implementaci v typu služby.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-135">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="b5d7b-136">Vazba použitá v tomto příkladu je <xref:System.ServiceModel.WSHttpBinding> což je integrované vazbu, která se používá pro připojení ke koncovým bodům, které odpovídají WS-\* specifikace.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-136">The binding used in this sample is <xref:System.ServiceModel.WSHttpBinding> which is a built-in binding that is used for connecting to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="b5d7b-137">Další informace o vazbách WCF najdete v tématu [vazby WCF – přehled](../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b5d7b-137">For more information about WCF bindings, see [WCF Bindings Overview](../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="b5d7b-138">Adresa se připojí k základní adrese k identifikaci koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-138">The address is appended to the base address to identify the endpoint.</span></span> <span data-ttu-id="b5d7b-139">Adresa zadaná v tomto kódu je "CalculatorService", takže je plně kvalifikovanou adresu pro koncový bod `"http://localhost:8000/GettingStarted/CalculatorService"`.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-139">The address specified in this code is "CalculatorService" so the fully qualified address for the endpoint is `"http://localhost:8000/GettingStarted/CalculatorService"`.</span></span>

    > [!IMPORTANT]
    > Adding a service endpoint is optional when using .NET Framework 4 or later. In these versions, if no endpoints are added in code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service. For more information about default endpoints see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md). For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).

<span data-ttu-id="b5d7b-140">**Krok 4** – povolit výměny metadat.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-140">**Step 4** – Enable metadata exchange.</span></span> <span data-ttu-id="b5d7b-141">Klienti použijí ke generování proxy servery, které se použije k volání operací služby metadata exchange.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-141">Clients will use metadata exchange to generate proxies that will be used to call the service operations.</span></span> <span data-ttu-id="b5d7b-142">Umožňuje vytvořit výměny metadat <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, nastavte ho na <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> vlastnost `true`a přidat chování při <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  --> `System.ServiceModel.ServiceHost.Behaviors%2A` kolekce <xref:System.ServiceModel.ServiceHost> instance.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-142">To enable metadata exchange create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set it’s <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, and add the behavior to the <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A` collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

<span data-ttu-id="b5d7b-143">**Krok 5** – otevře <xref:System.ServiceModel.ServiceHost> k naslouchání pro příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-143">**Step 5** – Open the <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="b5d7b-144">Všimněte si, že kód čeká uživatelem zadejte.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-144">Notice the code waits for the user to hit enter.</span></span> <span data-ttu-id="b5d7b-145">Pokud to neprovedete, bude aplikace okamžitě ukončena a služby se vypne. Všimněte si také bloku try/catch použít.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-145">If you do not do this, the app will close immediately and the service will shut down.Also notice a  try/catch block used.</span></span> <span data-ttu-id="b5d7b-146">Po <xref:System.ServiceModel.ServiceHost> byla vytvořena instance, jiný kód je umístěn v bloku try/catch.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-146">After the <xref:System.ServiceModel.ServiceHost> has been instantiated, all other code is placed in a try/catch block.</span></span> <span data-ttu-id="b5d7b-147">Další informace o bezpečně zachycování výjimek vyvolaných <xref:System.ServiceModel.ServiceHost>, naleznete v tématu [vyhnout problémům s příkazem Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)</span><span class="sxs-lookup"><span data-stu-id="b5d7b-147">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Avoiding Problems with the Using Statement](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b5d7b-148">Úpravy souboru App.config v GettingStartedLib tak, aby odrážely změny provedené v kódu:</span><span class="sxs-lookup"><span data-stu-id="b5d7b-148">Edit App.config in GettingStartedLib to reflect the changes made in code:</span></span>
> 1. <span data-ttu-id="b5d7b-149">Změňte na řádek 14 `<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="b5d7b-149">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
> 2. <span data-ttu-id="b5d7b-150">Změňte řádek 17 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="b5d7b-150">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
> 3. <span data-ttu-id="b5d7b-151">Změňte řádek 22 na `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="b5d7b-151">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

## <a name="verify-the-service-is-working"></a><span data-ttu-id="b5d7b-152">Ověřte, že služba funguje</span><span class="sxs-lookup"><span data-stu-id="b5d7b-152">Verify the service is working</span></span>

1. <span data-ttu-id="b5d7b-153">Spustit konzolu GettingStartedHost z aplikace v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-153">Run the GettingStartedHost console application from inside Visual Studio.</span></span>

   <span data-ttu-id="b5d7b-154">Služba musí běžet s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-154">The service must be run with administrator privileges.</span></span> <span data-ttu-id="b5d7b-155">Vzhledem k tomu, že Visual Studio otevřené s oprávněními správce, GettingStartedHost také spouštět s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-155">Because Visual Studio was opened with administrator privileges, GettingStartedHost is also run with administrator privileges.</span></span> <span data-ttu-id="b5d7b-156">Můžete také otevřít nový příkazový řádek pomocí **spustit jako správce** a spusťte service.exe v něm.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-156">You can also open a new command prompt using **Run as administrator** and run service.exe within it.</span></span>

2. <span data-ttu-id="b5d7b-157">Otevřete webový prohlížeč a přejděte na stránku služby ladění na `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-157">Open a web browser and browse to the service's debug page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

## <a name="example"></a><span data-ttu-id="b5d7b-158">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5d7b-158">Example</span></span>

<span data-ttu-id="b5d7b-159">Následující příklad obsahuje kontrakt a implementaci služby z předchozích kroků tohoto kurzu a hostuje službu v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-159">The following example includes the service contract and implementation from previous steps in the tutorial and hosts the service in a console application.</span></span>

<span data-ttu-id="b5d7b-160">Chcete-li zkompilovat pomocí příkazového řádku kompilátoru, kompilace IService1.cs a Service1.cs do knihovny tříd, který odkazuje na `System.ServiceModel.dll`.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-160">To compile this with a command-line compiler, compile IService1.cs and Service1.cs into a class library that references `System.ServiceModel.dll`.</span></span> <span data-ttu-id="b5d7b-161">Soubor Program.cs zkompiluje kód jako konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-161">Compile Program.cs as a console application.</span></span>

```csharp
using System;
using System.ServiceModel;

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
using System;
using System.ServiceModel;

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
> <span data-ttu-id="b5d7b-162">Služby, jako je ten vyžadují oprávnění k registraci adresami protokolu HTTP na počítači pro naslouchání.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-162">Services such as this one require permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="b5d7b-163">Účty správců mají toto oprávnění, ale účty bez oprávnění správce musí být uděleno oprávnění pro obory názvů HTTP.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-163">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="b5d7b-164">Další informace o tom, jak konfigurace rezervace oboru názvů najdete v tématu [konfigurace HTTP a HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="b5d7b-164">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="b5d7b-165">Při spuštění v sadě Visual Studio, musí být spuštěn service.exe s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-165">When running under Visual Studio, the service.exe must be run with administrator privileges.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b5d7b-166">Další kroky</span><span class="sxs-lookup"><span data-stu-id="b5d7b-166">Next steps</span></span>

<span data-ttu-id="b5d7b-167">Nyní je služba spuštěna.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-167">Now the service is running.</span></span> <span data-ttu-id="b5d7b-168">V dalším krokem vytvoření klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="b5d7b-168">In the next task, you create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b5d7b-169">Postupy: vytvoření klienta WCF</span><span class="sxs-lookup"><span data-stu-id="b5d7b-169">How to: Create a WCF client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)

<span data-ttu-id="b5d7b-170">Informace o odstraňování potíží naleznete v tématu [řešení potíží s kurzu Začínáme](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="b5d7b-170">For troubleshooting information, see [Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b5d7b-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5d7b-171">See also</span></span>

- [<span data-ttu-id="b5d7b-172">Začínáme</span><span class="sxs-lookup"><span data-stu-id="b5d7b-172">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="b5d7b-173">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="b5d7b-173">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)