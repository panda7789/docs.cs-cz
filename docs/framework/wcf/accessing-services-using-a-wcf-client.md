---
title: Přístup ke službám pomocí klienta WCF
description: Naučte se vytvořit proxy server klienta WCF pro vaši službu WCF. Klientská aplikace používá ke komunikaci se službou klientský proxy server.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: 25446a89a0b5657d32d77e2d0d57f58f36bed71b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245541"
---
# <a name="accessing-services-using-a-wcf-client"></a><span data-ttu-id="67338-104">Přístup ke službám pomocí klienta WCF</span><span class="sxs-lookup"><span data-stu-id="67338-104">Accessing Services Using a WCF Client</span></span>

<span data-ttu-id="67338-105">Po vytvoření služby je dalším krokem vytvoření proxy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="67338-105">After you create a service, the next step is to create a WCF client proxy.</span></span> <span data-ttu-id="67338-106">Klientská aplikace používá ke komunikaci se službou klienta proxy serveru služby WCF.</span><span class="sxs-lookup"><span data-stu-id="67338-106">A client application uses the WCF client proxy to communicate with the service.</span></span> <span data-ttu-id="67338-107">Klientské aplikace obvykle importují metadata služby pro generování kódu klienta WCF, který lze použít k vyvolání služby.</span><span class="sxs-lookup"><span data-stu-id="67338-107">Client applications usually import a service's metadata to generate WCF client code that can be used to invoke the service.</span></span>

 <span data-ttu-id="67338-108">Základní kroky pro vytvoření klienta WCF zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="67338-108">The basic steps for creating a WCF client include the following:</span></span>

1. <span data-ttu-id="67338-109">Zkompilujte kód služby.</span><span class="sxs-lookup"><span data-stu-id="67338-109">Compile the service code.</span></span>

2. <span data-ttu-id="67338-110">Vygenerujte proxy server klienta služby WCF.</span><span class="sxs-lookup"><span data-stu-id="67338-110">Generate the WCF client proxy.</span></span>

3. <span data-ttu-id="67338-111">Vytvořte instanci proxy serveru služby WCF.</span><span class="sxs-lookup"><span data-stu-id="67338-111">Instantiate the WCF client proxy.</span></span>

<span data-ttu-id="67338-112">Proxy klienta WCF se dá vytvořit ručně pomocí nástroje Service model metadat Tool (SvcUtil.exe), kde najdete další informace v tématu [Nástroj pro nástroj pro metadata typu ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="67338-112">The WCF client proxy can be generated manually by using the Service Model Metadata Utility Tool (SvcUtil.exe) for more information see, [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="67338-113">Proxy klient služby WCF lze také vygenerovat v rámci sady Visual Studio pomocí funkce **Přidat odkaz na službu** .</span><span class="sxs-lookup"><span data-stu-id="67338-113">The WCF client proxy can also be generated within Visual Studio using the **Add Service Reference**  feature.</span></span> <span data-ttu-id="67338-114">Pro vygenerování proxy serveru služby WCF pomocí obou metod, které musí služba běžet.</span><span class="sxs-lookup"><span data-stu-id="67338-114">To generate the WCF client proxy using either method the service must be running.</span></span> <span data-ttu-id="67338-115">Pokud je služba v místním prostředí hostována, musíte spustit hostitele.</span><span class="sxs-lookup"><span data-stu-id="67338-115">If the service is self-hosted you must run the host.</span></span> <span data-ttu-id="67338-116">Pokud je služba hostovaná ve službě IIS/nemusíte dělat něco jiného.</span><span class="sxs-lookup"><span data-stu-id="67338-116">If the service is hosted in IIS/WAS you do not need to do anything else.</span></span>

## <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="67338-117">Nástroj pro metadata ServiceModel</span><span class="sxs-lookup"><span data-stu-id="67338-117">ServiceModel Metadata Utility Tool</span></span>
 <span data-ttu-id="67338-118">Nástroj pro vytváření [metadat (Svcutil.exe) třídy ServiceModel](servicemodel-metadata-utility-tool-svcutil-exe.md) je nástroj příkazového řádku pro generování kódu z metadat.</span><span class="sxs-lookup"><span data-stu-id="67338-118">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) is a command-line tool for generating code from metadata.</span></span> <span data-ttu-id="67338-119">Toto použití je příkladem základního příkazu Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="67338-119">The following use is an example of a basic Svcutil.exe command.</span></span>

```console
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
```

 <span data-ttu-id="67338-120">Alternativně můžete použít Svcutil.exe se soubory WSDL (Web Services Description Language) a XML Schema Definition Language (XSD) v systému souborů.</span><span class="sxs-lookup"><span data-stu-id="67338-120">Alternatively, you can use Svcutil.exe with Web Services Description Language (WSDL) and XML Schema definition language (XSD) files on the file system.</span></span>

```console
Svcutil.exe <list of WSDL and XSD files on file system>
```

 <span data-ttu-id="67338-121">Výsledkem je soubor kódu, který obsahuje kód klienta WCF, který může klientská aplikace použít k vyvolání služby.</span><span class="sxs-lookup"><span data-stu-id="67338-121">The result is a code file that contains WCF client code that the client application can use to invoke the service.</span></span>

 <span data-ttu-id="67338-122">Můžete také použít nástroj pro generování konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="67338-122">You can also use the tool to generate configuration files.</span></span>

```console
Svcutil.exe <file1 [,file2]>
```

 <span data-ttu-id="67338-123">Je-li zadán pouze jeden název souboru, jedná se o název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="67338-123">If only one file name is given, that is the name of the output file.</span></span> <span data-ttu-id="67338-124">Pokud jsou zadány dva názvy souborů, pak je prvním souborem vstupní konfigurační soubor, jehož obsah je sloučen s vygenerovanou konfigurací a napsaný do druhého souboru.</span><span class="sxs-lookup"><span data-stu-id="67338-124">If two file names are given, then the first file is an input configuration file whose contents are merged with the generated configuration and written out into the second file.</span></span> <span data-ttu-id="67338-125">Další informace o konfiguraci najdete v tématu [Konfigurace vazeb pro služby](configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="67338-125">For more information about configuration, see [Configuring Bindings for Services](configuring-bindings-for-wcf-services.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="67338-126">Nezabezpečené žádosti o metadata představují určitá rizika stejným způsobem jako jakákoli nezabezpečená síťová žádost: Pokud si nejste jisti, že koncový bod, se kterým komunikujete, je ten, kdo je vyjadřuje, informace, které načítajíte, mohou být metadata ze škodlivé služby.</span><span class="sxs-lookup"><span data-stu-id="67338-126">Unsecured metadata requests pose certain risks in the same way that any unsecured network request does: If you are not certain that the endpoint you are communicating with is who it says it is, the information you retrieve might be metadata from a malicious service.</span></span>

## <a name="add-service-reference-in-visual-studio"></a><span data-ttu-id="67338-127">Přidat odkaz na službu v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="67338-127">Add Service Reference in Visual Studio</span></span>

 <span data-ttu-id="67338-128">U spuštěné služby klikněte pravým tlačítkem myši na projekt, který bude obsahovat proxy klienta WCF a vyberte **Přidat**  >  **odkaz na službu**.</span><span class="sxs-lookup"><span data-stu-id="67338-128">With the service running, right click the project that will contain the WCF client proxy and select **Add** > **Service Reference**.</span></span> <span data-ttu-id="67338-129">V **dialogovém okně Přidat odkaz na službu**zadejte adresu URL služby, kterou chcete zavolat, a klikněte na tlačítko **Přejít** .</span><span class="sxs-lookup"><span data-stu-id="67338-129">In the **Add Service Reference Dialog**, type in the URL to the service you want to call and click the **Go** button.</span></span> <span data-ttu-id="67338-130">V dialogovém okně se zobrazí seznam služeb dostupných na adrese, kterou zadáte.</span><span class="sxs-lookup"><span data-stu-id="67338-130">The dialog will display a list of services available at the address you specify.</span></span> <span data-ttu-id="67338-131">Dvojím kliknutím na službu zobrazte dostupné kontrakty a operace, zadejte obor názvů pro vygenerovaný kód a klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="67338-131">Double click the service to see the contracts and operations available, specify a namespace for the generated code, and click the **OK** button.</span></span>

## <a name="example"></a><span data-ttu-id="67338-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="67338-132">Example</span></span>
 <span data-ttu-id="67338-133">Následující příklad kódu ukazuje kontrakt služby vytvořenou pro službu.</span><span class="sxs-lookup"><span data-stu-id="67338-133">The following code example shows a service contract created for a service.</span></span>

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

 <span data-ttu-id="67338-134">Nástroj pro dodávání metadat ServiceModel a **Přidat odkaz na službu** v aplikaci Visual Studio generuje následující třídu klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="67338-134">The ServiceModel Metadata utility tool and **Add Service Reference** in Visual Studio generates the following WCF client class.</span></span> <span data-ttu-id="67338-135">Třída dědí z obecné <xref:System.ServiceModel.ClientBase%601> třídy a implementuje `ICalculator` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="67338-135">The class inherits from the generic <xref:System.ServiceModel.ClientBase%601> class and implements the `ICalculator` interface.</span></span> <span data-ttu-id="67338-136">Nástroj také vygeneruje `ICalculator` rozhraní (zde není zobrazen).</span><span class="sxs-lookup"><span data-stu-id="67338-136">The tool also generates the `ICalculator` interface (not shown here).</span></span>

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

## <a name="using-the-wcf-client"></a><span data-ttu-id="67338-137">Použití klienta WCF</span><span class="sxs-lookup"><span data-stu-id="67338-137">Using the WCF Client</span></span>
 <span data-ttu-id="67338-138">Chcete-li použít klienta služby WCF, vytvořte instanci klienta WCF a pak zavolejte své metody, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="67338-138">To use the WCF client, create an instance of the WCF client, and then call its methods, as shown in the following code.</span></span>

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

## <a name="debugging-exceptions-thrown-by-a-client"></a><span data-ttu-id="67338-139">Ladění výjimek vyvolaných klientem</span><span class="sxs-lookup"><span data-stu-id="67338-139">Debugging Exceptions Thrown by a Client</span></span>

<span data-ttu-id="67338-140">Mnoho výjimek vyvolaných klientem WCF je způsobeno výjimkou ve službě.</span><span class="sxs-lookup"><span data-stu-id="67338-140">Many exceptions thrown by a WCF client are caused by an exception on the service.</span></span> <span data-ttu-id="67338-141">Mezi příklady patří:</span><span class="sxs-lookup"><span data-stu-id="67338-141">Some examples of this are:</span></span>

- <span data-ttu-id="67338-142"><xref:System.Net.Sockets.SocketException>: Vzdálený hostitel nuceně zavřel existující připojení.</span><span class="sxs-lookup"><span data-stu-id="67338-142"><xref:System.Net.Sockets.SocketException>: An existing connection was forcibly closed by the remote host.</span></span>

- <span data-ttu-id="67338-143"><xref:System.ServiceModel.CommunicationException>: Základní připojení bylo neočekávaně ukončeno.</span><span class="sxs-lookup"><span data-stu-id="67338-143"><xref:System.ServiceModel.CommunicationException>: The underlying connection was closed unexpectedly.</span></span>

- <span data-ttu-id="67338-144"><xref:System.ServiceModel.CommunicationObjectAbortedException>: Připojení soketu bylo přerušeno.</span><span class="sxs-lookup"><span data-stu-id="67338-144"><xref:System.ServiceModel.CommunicationObjectAbortedException>: The socket connection was aborted.</span></span> <span data-ttu-id="67338-145">To může být způsobeno chybou při zpracování vaší zprávy, překročením časového limitu příjmu vzdáleným hostitelem nebo problémem se síťovými prostředky.</span><span class="sxs-lookup"><span data-stu-id="67338-145">This could be caused by an error processing your message, a receive time-out being exceeded by the remote host, or an underlying network resource issue.</span></span>

<span data-ttu-id="67338-146">Pokud dojde k těmto typům výjimek, nejlepším způsobem, jak problém vyřešit, je zapnout trasování na straně služby a určit, k jaké výjimce došlo.</span><span class="sxs-lookup"><span data-stu-id="67338-146">When these types of exceptions occur, the best way to solve the problem is to turn on tracing on the service side and determine what exception occurred there.</span></span> <span data-ttu-id="67338-147">Další informace o trasování naleznete v tématu [trasování](./diagnostics/tracing/index.md) a [používání trasování pro řešení potíží s aplikací](./diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="67338-147">For more information about tracing, see [Tracing](./diagnostics/tracing/index.md) and [Using Tracing to Troubleshoot Your Application](./diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="67338-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="67338-148">See also</span></span>

- [<span data-ttu-id="67338-149">Postupy: Vytvoření klienta</span><span class="sxs-lookup"><span data-stu-id="67338-149">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [<span data-ttu-id="67338-150">Postupy: Přístup ke službám pomocí duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="67338-150">How to: Access Services with a Duplex Contract</span></span>](./feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="67338-151">Postupy: Asynchronní volání operací služby</span><span class="sxs-lookup"><span data-stu-id="67338-151">How to: Call Service Operations Asynchronously</span></span>](./feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [<span data-ttu-id="67338-152">Postupy: Přístup ke službám pomocí jednosměrných kontraktů a kontraktů požadavek-odpověď</span><span class="sxs-lookup"><span data-stu-id="67338-152">How to: Access Services with One-Way and Request-Reply Contracts</span></span>](./feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [<span data-ttu-id="67338-153">Postupy: Přístup ke službě WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="67338-153">How to: Access a WSE 3.0 Service</span></span>](./feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [<span data-ttu-id="67338-154">Principy generovaného klientského kódu</span><span class="sxs-lookup"><span data-stu-id="67338-154">Understanding Generated Client Code</span></span>](./feature-details/understanding-generated-client-code.md)
- [<span data-ttu-id="67338-155">Postupy: Vylepšení doby spouštění klientských aplikací WCF pomocí XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="67338-155">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>](./feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
- [<span data-ttu-id="67338-156">Nastavení chování klienta za běhu</span><span class="sxs-lookup"><span data-stu-id="67338-156">Specifying Client Run-Time Behavior</span></span>](specifying-client-run-time-behavior.md)
- [<span data-ttu-id="67338-157">Konfigurace chování klienta</span><span class="sxs-lookup"><span data-stu-id="67338-157">Configuring Client Behaviors</span></span>](configuring-client-behaviors.md)
