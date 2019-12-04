---
title: Klient ASMX se službou WCF
ms.date: 03/30/2017
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
ms.openlocfilehash: a560650dba250d1ee4f0b959ead70a2915c9997f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716140"
---
# <a name="asmx-client-with-a-wcf-service"></a><span data-ttu-id="d839a-102">Klient ASMX se službou WCF</span><span class="sxs-lookup"><span data-stu-id="d839a-102">ASMX Client with a WCF Service</span></span>

<span data-ttu-id="d839a-103">Tento příklad ukazuje, jak vytvořit službu pomocí Windows Communication Foundation (WCF) a pak přistupovat ke službě z klienta jiného typu než WCF, jako je například klient ASMX.</span><span class="sxs-lookup"><span data-stu-id="d839a-103">This sample demonstrates how to create a service using Windows Communication Foundation (WCF) and then access the service from a non-WCF client, such as an ASMX client.</span></span>

> [!NOTE]
> <span data-ttu-id="d839a-104">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="d839a-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="d839a-105">Tato ukázka se skládá z programu klientské konzoly (. exe) a knihovny služeb (. dll) hostované službou Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="d839a-105">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="d839a-106">Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď.</span><span class="sxs-lookup"><span data-stu-id="d839a-106">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="d839a-107">Kontrakt je definován rozhraním `ICalculator`, které zpřístupňuje matematické operace (`Add`, `Subtract`, `Multiply`a `Divide`).</span><span class="sxs-lookup"><span data-stu-id="d839a-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="d839a-108">Klient ASMX provede synchronní požadavky na matematickou operaci a službu s výsledkem.</span><span class="sxs-lookup"><span data-stu-id="d839a-108">The ASMX client makes synchronous requests to a math operation and the service replies with the result.</span></span>

<span data-ttu-id="d839a-109">Služba implementuje kontrakt `ICalculator`, jak je definován v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="d839a-109">The service implements an `ICalculator` contract as defined in the following code.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"), XmlSerializerFormat]
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
```

<span data-ttu-id="d839a-110"><xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Xml.Serialization.XmlSerializer> mapují typy CLR do reprezentace XML.</span><span class="sxs-lookup"><span data-stu-id="d839a-110">The <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Xml.Serialization.XmlSerializer> map CLR types to an XML representation.</span></span> <span data-ttu-id="d839a-111"><xref:System.Runtime.Serialization.DataContractSerializer> interpretuje některé reprezentace XML jinak než XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="d839a-111">The <xref:System.Runtime.Serialization.DataContractSerializer> interprets some XML representations differently than XmlSerializer.</span></span> <span data-ttu-id="d839a-112">Generátory proxy jiných než WCF, jako je WSDL. exe, vygenerují při použití objektu XmlSerializer užitečnější rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d839a-112">Non-WCF proxy generators, such as Wsdl.exe, generate a more usable interface when the XmlSerializer is being used.</span></span> <span data-ttu-id="d839a-113"><xref:System.ServiceModel.XmlSerializerFormatAttribute> se aplikuje na rozhraní `ICalculator`, aby se zajistilo, že se XmlSerializer používá pro mapování typů CLR do XML.</span><span class="sxs-lookup"><span data-stu-id="d839a-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> is applied to the `ICalculator` interface, to ensure that the XmlSerializer is used for mapping CLR types to XML.</span></span> <span data-ttu-id="d839a-114">Implementace služby vypočítá a vrátí příslušný výsledek.</span><span class="sxs-lookup"><span data-stu-id="d839a-114">The service implementation calculates and returns the appropriate result.</span></span>

<span data-ttu-id="d839a-115">Služba zpřístupňuje jeden koncový bod pro komunikaci se službou, definovaná pomocí konfiguračního souboru (Web. config).</span><span class="sxs-lookup"><span data-stu-id="d839a-115">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="d839a-116">Koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="d839a-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="d839a-117">Služba zpřístupňuje koncový bod na základní adrese poskytnuté hostitelem služby Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="d839a-117">The service exposes the endpoint at the base address provided by the Internet Information Services (IIS) host.</span></span> <span data-ttu-id="d839a-118">Atribut `binding` je nastaven na basicHttpBinding, který poskytuje komunikaci HTTP pomocí protokolu SOAP 1,1, který je kompatibilní s WS-I BasicProfile 1,1, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="d839a-118">The `binding` attribute is set to basicHttpBinding that provides HTTP communications using SOAP 1.1, which is compliant with WS-I BasicProfile 1.1 as shown in the following sample configuration.</span></span>

```xml
<services>
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc.  -->
    <endpoint address=""
              binding="basicHttpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </service>
</services>
```

<span data-ttu-id="d839a-119">Klient ASMX komunikuje se službou WCF pomocí typovaného proxy, který je generovaný nástrojem WSDL (Web Services Description Language) (WSDL. exe).</span><span class="sxs-lookup"><span data-stu-id="d839a-119">The ASMX client communicates with the WCF service using a typed proxy that is generated by the Web Services Description Language (WSDL) utility (Wsdl.exe).</span></span> <span data-ttu-id="d839a-120">Zadaný proxy server je obsažený v souboru generatedClient.cs.</span><span class="sxs-lookup"><span data-stu-id="d839a-120">The typed proxy is contained in the file generatedClient.cs.</span></span> <span data-ttu-id="d839a-121">Nástroj WSDL načte metadata pro zadanou službu a vygeneruje typový proxy pro použití klientem ke komunikaci.</span><span class="sxs-lookup"><span data-stu-id="d839a-121">The WSDL utility retrieves metadata for the specified service and generates a typed proxy for use by a client to communicate.</span></span> <span data-ttu-id="d839a-122">Ve výchozím nastavení rozhraní nevystavuje žádná metadata.</span><span class="sxs-lookup"><span data-stu-id="d839a-122">By default, the framework does not expose any metadata.</span></span> <span data-ttu-id="d839a-123">Chcete-li zveřejnit metadata požadovaná pro vygenerování proxy serveru, je nutné přidat [\<> oddílu serviceMetadata](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) a nastavit jeho atribut `httpGetEnabled` na `True`, jak je znázorněno v následující konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="d839a-123">To expose the metadata required to generate the proxy, you must add a [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) and set its `httpGetEnabled` attribute to `True` as shown in the following configuration.</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <!-- Setting httpGetEnabled to True on the serviceMetadata
           behavior exposes the service's wsdl at <base address>?wsdl :
           http://localhost/servicemodelsamples/service.svc?wsdl -->
      <serviceMetadata httpGetEnabled="True"/>
      <serviceDebug includeExceptionDetailInFaults="False" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="d839a-124">Spusťte následující příkaz z příkazového řádku v adresáři klienta pro vygenerování typovaného proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="d839a-124">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>

```console
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl
```

<span data-ttu-id="d839a-125">Pomocí generovaného typovaného proxy serveru může klient získat přístup k danému koncovému bodu služby nakonfigurováním příslušné adresy.</span><span class="sxs-lookup"><span data-stu-id="d839a-125">By using the generated typed proxy, the client can access a given service endpoint by configuring the appropriate address.</span></span> <span data-ttu-id="d839a-126">Klient používá konfigurační soubor (App. config) k určení koncového bodu ke komunikaci.</span><span class="sxs-lookup"><span data-stu-id="d839a-126">The client uses a configuration file (App.config) to specify the endpoint to communicate with.</span></span>

```xml
<appSettings>
  <add key="CalculatorServiceAddress"
       value="http://localhost/ServiceModelSamples/service.svc"/>
</appSettings>
```

<span data-ttu-id="d839a-127">Implementace klienta vytvoří instanci typového proxy serveru pro zahájení komunikace se službou.</span><span class="sxs-lookup"><span data-stu-id="d839a-127">The client implementation constructs an instance of the typed proxy to begin communicating with the service.</span></span>

```csharp
// Create a client to the CalculatorService.
using (CalculatorService client = new CalculatorService())
{
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

    // Call the Subtract service operation.
    value1 = 145.00D;
    value2 = 76.54D;
    result = client.Subtract(value1, value2);
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

    // Call the Multiply service operation.
    value1 = 9.00D;
    value2 = 81.25D;
    result = client.Multiply(value1, value2);
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

    // Call the Divide service operation.
    value1 = 22.00D;
    value2 = 7.00D;
    result = client.Divide(value1, value2);
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);

}

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

<span data-ttu-id="d839a-128">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="d839a-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="d839a-129">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="d839a-129">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d839a-130">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="d839a-130">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="d839a-131">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d839a-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="d839a-132">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d839a-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="d839a-133">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d839a-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!NOTE]
> <span data-ttu-id="d839a-134">Další informace o předávání a vracení složitých datových typů naleznete v tématu: [datové vazby v klientovi model Windows Forms](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [datové vazby v klientovi Windows Presentation Foundation](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md)a [datové vazby v klientovi ASP.NET](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md) .</span><span class="sxs-lookup"><span data-stu-id="d839a-134">For more information about passing and returning complex data types see: [Data Binding in a Windows Forms Client](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [Data Binding in a Windows Presentation Foundation Client](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md), and [Data Binding in an ASP.NET Client](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d839a-135">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="d839a-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d839a-136">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="d839a-136">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="d839a-137">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="d839a-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d839a-138">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d839a-138">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`
