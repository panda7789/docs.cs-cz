---
title: Přístup ke službám pomocí klienta WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: 6bf683cdd0a03a5d1dbc452c28e7b33911464f09
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297249"
---
# <a name="accessing-services-using-a-wcf-client"></a><span data-ttu-id="08aeb-102">Přístup ke službám pomocí klienta WCF</span><span class="sxs-lookup"><span data-stu-id="08aeb-102">Accessing Services Using a WCF Client</span></span>

<span data-ttu-id="08aeb-103">Po vytvoření služby, dalším krokem je vytvoření proxy serveru klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="08aeb-103">After you create a service, the next step is to create a WCF client proxy.</span></span> <span data-ttu-id="08aeb-104">Klientská aplikace bude používat ke komunikaci se službou proxy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="08aeb-104">A client application uses the WCF client proxy to communicate with the service.</span></span> <span data-ttu-id="08aeb-105">Klientské aplikace obvykle importovat metadata služby pro generování kódu klienta WCF, který můžete použít k vyvolání služby.</span><span class="sxs-lookup"><span data-stu-id="08aeb-105">Client applications usually import a service's metadata to generate WCF client code that can be used to invoke the service.</span></span>

 <span data-ttu-id="08aeb-106">Základní kroky pro vytvoření klienta WCF patří:</span><span class="sxs-lookup"><span data-stu-id="08aeb-106">The basic steps for creating a WCF client include the following:</span></span>

1. <span data-ttu-id="08aeb-107">Kompilace kódu služby.</span><span class="sxs-lookup"><span data-stu-id="08aeb-107">Compile the service code.</span></span>

2. <span data-ttu-id="08aeb-108">Generování proxy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="08aeb-108">Generate the WCF client proxy.</span></span>

3. <span data-ttu-id="08aeb-109">Vytvořit instanci proxy serveru klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="08aeb-109">Instantiate the WCF client proxy.</span></span>

<span data-ttu-id="08aeb-110">Klient proxy WCF je vygenerovat ručně pomocí nástroje modelu služby Metadata Utility (SvcUtil.exe) pro další informace najdete [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="08aeb-110">The WCF client proxy can be generated manually by using the Service Model Metadata Utility Tool (SvcUtil.exe) for more information see, [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="08aeb-111">Klient proxy WCF můžou být taky vygenerovaná v rámci sady Visual Studio pomocí **přidat odkaz na službu** funkce.</span><span class="sxs-lookup"><span data-stu-id="08aeb-111">The WCF client proxy can also be generated within Visual Studio using the **Add Service Reference**  feature.</span></span> <span data-ttu-id="08aeb-112">Generování proxy klienta WCF pomocí některé z metod služby musí být spuštěna.</span><span class="sxs-lookup"><span data-stu-id="08aeb-112">To generate the WCF client proxy using either method the service must be running.</span></span> <span data-ttu-id="08aeb-113">Pokud je služba v místním prostředí je nutné spustit hostiteli.</span><span class="sxs-lookup"><span data-stu-id="08aeb-113">If the service is self-hosted you must run the host.</span></span> <span data-ttu-id="08aeb-114">Pokud služba je hostována ve službě IIS nebo WAS, nemusíte dělat nic dalšího.</span><span class="sxs-lookup"><span data-stu-id="08aeb-114">If the service is hosted in IIS/WAS you do not need to do anything else.</span></span>

## <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="08aeb-115">Nástroj ServiceModel Metadata Utility</span><span class="sxs-lookup"><span data-stu-id="08aeb-115">ServiceModel Metadata Utility Tool</span></span>
 <span data-ttu-id="08aeb-116">[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) je nástroj příkazového řádku pro generování kódu z metadat.</span><span class="sxs-lookup"><span data-stu-id="08aeb-116">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) is a command-line tool for generating code from metadata.</span></span> <span data-ttu-id="08aeb-117">Následující je příklad základní příkaz Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="08aeb-117">The following use is an example of a basic Svcutil.exe command.</span></span>

```
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
```

 <span data-ttu-id="08aeb-118">Alternativně můžete použít Svcutil.exe webové služby WSDL (Description Language) a schéma XML definice jazyk (XSD) soubory v systému souborů.</span><span class="sxs-lookup"><span data-stu-id="08aeb-118">Alternatively, you can use Svcutil.exe with Web Services Description Language (WSDL) and XML Schema definition language (XSD) files on the file system.</span></span>

```
Svcutil.exe <list of WSDL and XSD files on file system>
```

 <span data-ttu-id="08aeb-119">Výsledkem je soubor kódu, který obsahuje kód klienta WCF, který klientská aplikace můžete použít k vyvolání služby.</span><span class="sxs-lookup"><span data-stu-id="08aeb-119">The result is a code file that contains WCF client code that the client application can use to invoke the service.</span></span>

 <span data-ttu-id="08aeb-120">Nástroj můžete použít také ke generování konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="08aeb-120">You can also use the tool to generate configuration files.</span></span>

```
Svcutil.exe <file1 [,file2]>
```

 <span data-ttu-id="08aeb-121">Pokud pouze jeden název souboru je uveden, to je název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="08aeb-121">If only one file name is given, that is the name of the output file.</span></span> <span data-ttu-id="08aeb-122">Dva názvy souborů směru, je-li první soubor je soubor vstupní konfigurace, jejichž obsah jsou sloučeny s vygenerovanou konfiguraci a zapsat do druhého souboru.</span><span class="sxs-lookup"><span data-stu-id="08aeb-122">If two file names are given, then the first file is an input configuration file whose contents are merged with the generated configuration and written out into the second file.</span></span> <span data-ttu-id="08aeb-123">Další informace o konfiguraci najdete v tématu [Konfigurace vazeb pro služby](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="08aeb-123">For more information about configuration, see [Configuring Bindings for Services](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="08aeb-124">Požadavky na nezabezpečenou metadata představovat určitá rizika stejným způsobem, který nemá žádné žádosti o nezabezpečené síti: Pokud si nejste jisti, že je koncový bod, které komunikují s který říká, že se že jedná, může být informace, které můžete načíst metadata ze škodlivých služby.</span><span class="sxs-lookup"><span data-stu-id="08aeb-124">Unsecured metadata requests pose certain risks in the same way that any unsecured network request does: If you are not certain that the endpoint you are communicating with is who it says it is, the information you retrieve might be metadata from a malicious service.</span></span>

## <a name="add-service-reference-in-visual-studio"></a><span data-ttu-id="08aeb-125">Přidání odkazu na službu v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="08aeb-125">Add Service Reference in Visual Studio</span></span>

 <span data-ttu-id="08aeb-126">Služba spuštěná, klikněte pravým tlačítkem na projekt, který bude obsahovat proxy klienta WCF a zvolte **přidat** > **odkaz na službu**.</span><span class="sxs-lookup"><span data-stu-id="08aeb-126">With the service running, right click the project that will contain the WCF client proxy and select **Add** > **Service Reference**.</span></span> <span data-ttu-id="08aeb-127">V **dialogové okno Přidat odkaz na službu**, zadejte adresu URL služby, které chcete volat a klikněte na tlačítko **Přejít** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="08aeb-127">In the **Add Service Reference Dialog**, type in the URL to the service you want to call and click the **Go** button.</span></span> <span data-ttu-id="08aeb-128">Dialogové okno se zobrazí seznam služeb, které jsou k dispozici na adrese, kterou zadáte.</span><span class="sxs-lookup"><span data-stu-id="08aeb-128">The dialog will display a list of services available at the address you specify.</span></span> <span data-ttu-id="08aeb-129">Dvakrát klikněte na službu naleznete v tématu smluv a operace, které jsou k dispozici, zadejte obor názvů pro generovaný kód a klikněte na tlačítko **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="08aeb-129">Double click the service to see the contracts and operations available, specify a namespace for the generated code, and click the **OK** button.</span></span>

## <a name="example"></a><span data-ttu-id="08aeb-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="08aeb-130">Example</span></span>
 <span data-ttu-id="08aeb-131">Následující příklad kódu ukazuje kontraktu služby vytvořené pro službu.</span><span class="sxs-lookup"><span data-stu-id="08aeb-131">The following code example shows a service contract created for a service.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    // Other methods are not shown here.
}
```

```vb
' Define a service contract.
<ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
Public Interface ICalculator
    <OperationContract()>  _
    Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
    ' Other methods are not shown here.
End Interface
```

 <span data-ttu-id="08aeb-132">Nástroj ServiceModel Metadata a **přidat odkaz na službu** v sadě Visual Studio generuje následující třídy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="08aeb-132">The ServiceModel Metadata utility tool and **Add Service Reference** in Visual Studio generates the following WCF client class.</span></span> <span data-ttu-id="08aeb-133">Třída dědí z obecného <xref:System.ServiceModel.ClientBase%601> třídy a implementuje `ICalculator` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="08aeb-133">The class inherits from the generic <xref:System.ServiceModel.ClientBase%601> class and implements the `ICalculator` interface.</span></span> <span data-ttu-id="08aeb-134">Nástroj také vytvoří `ICalculator` rozhraní (není tady zobrazené).</span><span class="sxs-lookup"><span data-stu-id="08aeb-134">The tool also generates the `ICalculator` interface (not shown here).</span></span>

```csharp
public partial class CalculatorClient : System.ServiceModel.ClientBase<ICalculator>, ICalculator
{
    public CalculatorClient()
    {}

    public CalculatorClient(string endpointConfigurationName) :
            base(endpointConfigurationName)
    {}

    public CalculatorClient(string endpointConfigurationName, string remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(string endpointConfigurationName,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(System.ServiceModel.Channels.Binding binding,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(binding, remoteAddress)
    {}

    public double Add(double n1, double n2)
    {
        return base.Channel.Add(n1, n2);
    }
}
```

```vb
Partial Public Class CalculatorClient
    Inherits System.ServiceModel.ClientBase(Of ICalculator)
    Implements ICalculator

    Public Sub New()
        MyBase.New
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String)
        MyBase.New(endpointConfigurationName)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String, ByVal remoteAddress As String)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal binding As System.ServiceModel.Channels.Binding,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(binding, remoteAddress)
    End Sub

    Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        Implements ICalculator.Add
        Return MyBase.Channel.Add(n1, n2)
    End Function
End Class
```

## <a name="using-the-wcf-client"></a><span data-ttu-id="08aeb-135">Pomocí klienta WCF</span><span class="sxs-lookup"><span data-stu-id="08aeb-135">Using the WCF Client</span></span>
 <span data-ttu-id="08aeb-136">Použití klienta WCF, vytvořte instanci klienta WCF a potom volání obsažených metod, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="08aeb-136">To use the WCF client, create an instance of the WCF client, and then call its methods, as shown in the following code.</span></span>

```csharp
// Create a client object with the given client endpoint configuration.
CalculatorClient calcClient = new CalculatorClient("CalculatorEndpoint"));
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = calcClient.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```

```vb
' Create a client object with the given client endpoint configuration.
Dim calcClient As CalculatorClient = _
New CalculatorClient("CalculatorEndpoint")

' Call the Add service operation.
Dim value1 As Double = 100.00D
Dim value2 As Double = 15.99D
Dim result As Double = calcClient.Add(value1, value2)
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)
```

## <a name="debugging-exceptions-thrown-by-a-client"></a><span data-ttu-id="08aeb-137">Ladění výjimky vyvolané klientem</span><span class="sxs-lookup"><span data-stu-id="08aeb-137">Debugging Exceptions Thrown by a Client</span></span>

<span data-ttu-id="08aeb-138">Velký počet výjimek vyvolaných klienta WCF jsou způsobeny výjimku ve službě.</span><span class="sxs-lookup"><span data-stu-id="08aeb-138">Many exceptions thrown by a WCF client are caused by an exception on the service.</span></span> <span data-ttu-id="08aeb-139">Některé příklady jsou:</span><span class="sxs-lookup"><span data-stu-id="08aeb-139">Some examples of this are:</span></span>

-   <span data-ttu-id="08aeb-140"><xref:System.Net.Sockets.SocketException>: Stávající připojení vynuceně zavřel vzdálený hostitel.</span><span class="sxs-lookup"><span data-stu-id="08aeb-140"><xref:System.Net.Sockets.SocketException>: An existing connection was forcibly closed by the remote host.</span></span>

-   <span data-ttu-id="08aeb-141"><xref:System.ServiceModel.CommunicationException>: Základní připojení bylo neočekávaně ukončeno.</span><span class="sxs-lookup"><span data-stu-id="08aeb-141"><xref:System.ServiceModel.CommunicationException>: The underlying connection was closed unexpectedly.</span></span>

-   <span data-ttu-id="08aeb-142"><xref:System.ServiceModel.CommunicationObjectAbortedException>: Připojení soketu bylo přerušeno.</span><span class="sxs-lookup"><span data-stu-id="08aeb-142"><xref:System.ServiceModel.CommunicationObjectAbortedException>: The socket connection was aborted.</span></span> <span data-ttu-id="08aeb-143">Může to být způsobeno chybou při zpracování zprávy, vypršení časového limitu příjmu, překročení vzdáleným hostitelem nebo problém prostředků základní sítě.</span><span class="sxs-lookup"><span data-stu-id="08aeb-143">This could be caused by an error processing your message, a receive time-out being exceeded by the remote host, or an underlying network resource issue.</span></span>

<span data-ttu-id="08aeb-144">Pokud dojde k tyto typy výjimek, je nejlepší způsob, jak problém vyřešit zapnout trasování na straně služby a zjistit, jaké výjimky došlo k chybě došlo.</span><span class="sxs-lookup"><span data-stu-id="08aeb-144">When these types of exceptions occur, the best way to solve the problem is to turn on tracing on the service side and determine what exception occurred there.</span></span> <span data-ttu-id="08aeb-145">Další informace o trasování najdete v tématu [trasování](../../../docs/framework/wcf/diagnostics/tracing/index.md) a [pomocí trasování řešení potíží s aplikace](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="08aeb-145">For more information about tracing, see [Tracing](../../../docs/framework/wcf/diagnostics/tracing/index.md) and [Using Tracing to Troubleshoot Your Application](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="08aeb-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="08aeb-146">See also</span></span>

- [<span data-ttu-id="08aeb-147">Postupy: Vytvoření klienta</span><span class="sxs-lookup"><span data-stu-id="08aeb-147">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="08aeb-148">Postupy: Přístup ke službám pomocí duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="08aeb-148">How to: Access Services with a Duplex Contract</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="08aeb-149">Postupy: Asynchronní volání operací služby</span><span class="sxs-lookup"><span data-stu-id="08aeb-149">How to: Call Service Operations Asynchronously</span></span>](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [<span data-ttu-id="08aeb-150">Postupy: Přístup ke službám pomocí jednosměrných kontraktů a kontraktů požadavek odpověď</span><span class="sxs-lookup"><span data-stu-id="08aeb-150">How to: Access Services with One-Way and Request-Reply Contracts</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [<span data-ttu-id="08aeb-151">Postupy: Přístup k WSE 3.0 Service</span><span class="sxs-lookup"><span data-stu-id="08aeb-151">How to: Access a WSE 3.0 Service</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [<span data-ttu-id="08aeb-152">Principy generovaného klientského kódu</span><span class="sxs-lookup"><span data-stu-id="08aeb-152">Understanding Generated Client Code</span></span>](../../../docs/framework/wcf/feature-details/understanding-generated-client-code.md)
- [<span data-ttu-id="08aeb-153">Postupy: Vylepšení spuštění čas z klientských aplikací WCF pomocí třídy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="08aeb-153">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
- [<span data-ttu-id="08aeb-154">Nastavení chování klienta za běhu</span><span class="sxs-lookup"><span data-stu-id="08aeb-154">Specifying Client Run-Time Behavior</span></span>](../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="08aeb-155">Konfigurace chování klienta</span><span class="sxs-lookup"><span data-stu-id="08aeb-155">Configuring Client Behaviors</span></span>](../../../docs/framework/wcf/configuring-client-behaviors.md)
