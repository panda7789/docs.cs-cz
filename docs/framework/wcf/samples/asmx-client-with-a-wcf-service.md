---
title: "Klient ASMX se službou WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 11ccb40fb4c29678ce0552da2dd8eb29c1ae561e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="asmx-client-with-a-wcf-service"></a><span data-ttu-id="71503-102">Klient ASMX se službou WCF</span><span class="sxs-lookup"><span data-stu-id="71503-102">ASMX Client with a WCF Service</span></span>
<span data-ttu-id="71503-103">Tento příklad ukazuje, jak vytvořit službu pomocí [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a poté přístup ke službě z jinou hodnotu než[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientovi, například klient ASMX.</span><span class="sxs-lookup"><span data-stu-id="71503-103">This sample demonstrates how to create a service using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and then access the service from a non-[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, such as an ASMX client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71503-104">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="71503-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="71503-105">Tato ukázka se skládá z konzoly programu klienta (.exe) a služby knihovny (DLL) hostované Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="71503-105">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="71503-106">Služba se implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="71503-106">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="71503-107">Kontrakt je definována `ICalculator` rozhraní, která zpřístupňuje matematické operace (`Add`, `Subtract`, `Multiply`, a `Divide`).</span><span class="sxs-lookup"><span data-stu-id="71503-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="71503-108">Klient ASMX zadává synchronní požadavků a odpovědí služby s výsledkem matematické operace.</span><span class="sxs-lookup"><span data-stu-id="71503-108">The ASMX client makes synchronous requests to a math operation and the service replies with the result.</span></span>  
  
 <span data-ttu-id="71503-109">Implementuje služby `ICalculator` smlouvy definovaným v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="71503-109">The service implements an `ICalculator` contract as defined in the following code.</span></span>  
  
```  
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
  
 <span data-ttu-id="71503-110"><xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Xml.Serialization.XmlSerializer> mapování typů CLR na reprezentaci XML.</span><span class="sxs-lookup"><span data-stu-id="71503-110">The <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Xml.Serialization.XmlSerializer> map CLR types to an XML representation.</span></span> <span data-ttu-id="71503-111"><xref:System.Runtime.Serialization.DataContractSerializer> Jinak než XmlSerializer interpretuje některé reprezentace XML.</span><span class="sxs-lookup"><span data-stu-id="71503-111">The <xref:System.Runtime.Serialization.DataContractSerializer> interprets some XML representations differently than XmlSerializer.</span></span> <span data-ttu-id="71503-112">Jinou hodnotu než[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generátory proxy serveru, jako je například Wsdl.exe, generovat více použitelné rozhraní při používání třídy XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="71503-112">Non-[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] proxy generators, such as Wsdl.exe, generate a more usable interface when the XmlSerializer is being used.</span></span> <span data-ttu-id="71503-113"><xref:System.ServiceModel.XmlSerializerFormatAttribute> Se použije na `ICalculator` rozhraní, aby třídy XmlSerializer je používána pro mapování typů CLR do formátu XML.</span><span class="sxs-lookup"><span data-stu-id="71503-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> is applied to the `ICalculator` interface, to ensure that the XmlSerializer is used for mapping CLR types to XML.</span></span> <span data-ttu-id="71503-114">Implementace služby vypočítá a vrátí odpovídající výsledek.</span><span class="sxs-lookup"><span data-stu-id="71503-114">The service implementation calculates and returns the appropriate result.</span></span>  
  
 <span data-ttu-id="71503-115">Službu zpřístupní jeden koncový bod pro komunikaci se službou, definovat pomocí konfiguračního souboru (Web.config).</span><span class="sxs-lookup"><span data-stu-id="71503-115">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="71503-116">Koncový bod se skládá z adresy, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="71503-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="71503-117">Službu zpřístupní koncový bod na základní adrese od hostitele Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="71503-117">The service exposes the endpoint at the base address provided by the Internet Information Services (IIS) host.</span></span> <span data-ttu-id="71503-118">`binding` Je atribut nastaven na basicHttpBinding, která poskytuje HTTP komunikaci pomocí protokolu SOAP 1.1, který je kompatibilní s WS-I BasicProfile 1.1, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="71503-118">The `binding` attribute is set to basicHttpBinding that provides HTTP communications using SOAP 1.1, which is compliant with WS-I BasicProfile 1.1 as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="71503-119">Klient ASMX komunikuje s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby pomocí zadaných proxy server, který je generován nástroj webové služby popis Language (WSDL) (Wsdl.exe).</span><span class="sxs-lookup"><span data-stu-id="71503-119">The ASMX client communicates with the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service using a typed proxy that is generated by the Web Services Description Language (WSDL) utility (Wsdl.exe).</span></span> <span data-ttu-id="71503-120">Typové proxy je obsažený v souboru generatedClient.cs.</span><span class="sxs-lookup"><span data-stu-id="71503-120">The typed proxy is contained in the file generatedClient.cs.</span></span> <span data-ttu-id="71503-121">Nástroj WSDL načte metadata pro zadanou službu a generuje typové proxy server pro použití klientem komunikovat.</span><span class="sxs-lookup"><span data-stu-id="71503-121">The WSDL utility retrieves metadata for the specified service and generates a typed proxy for use by a client to communicate.</span></span> <span data-ttu-id="71503-122">Ve výchozím nastavení rozhraní nevystavuje veškerá metadata.</span><span class="sxs-lookup"><span data-stu-id="71503-122">By default, the framework does not expose any metadata.</span></span> <span data-ttu-id="71503-123">Ke zveřejnění metadata vyžadovaných ke generování proxy server, je nutné přidat [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) a nastavit jeho `httpGetEnabled` atribut `True` jak je znázorněno v následující konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="71503-123">To expose the metadata required to generate the proxy, you must add a [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) and set its `httpGetEnabled` attribute to `True` as shown in the following configuration.</span></span>  
  
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
  
 <span data-ttu-id="71503-124">Spusťte následující příkaz z příkazového řádku v adresáři klienta ke generování typem proxy.</span><span class="sxs-lookup"><span data-stu-id="71503-124">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl  
```  
  
 <span data-ttu-id="71503-125">Pomocí vygenerovaný typové proxy server, klient může získat koncový bod uvedená služba nakonfigurováním příslušnou adresu.</span><span class="sxs-lookup"><span data-stu-id="71503-125">By using the generated typed proxy, the client can access a given service endpoint by configuring the appropriate address.</span></span> <span data-ttu-id="71503-126">Klient použije k určení koncového bodu pro komunikaci se konfigurační soubor (App.config).</span><span class="sxs-lookup"><span data-stu-id="71503-126">The client uses a configuration file (App.config) to specify the endpoint to communicate with.</span></span>  
  
```xml  
<appSettings>  
  <add key="CalculatorServiceAddress"   
       value="http://localhost/ServiceModelSamples/service.svc"/>  
</appSettings>  
```  
  
 <span data-ttu-id="71503-127">Implementace klienta vytvoří instanci typu proxy server při zahájení komunikace se službou.</span><span class="sxs-lookup"><span data-stu-id="71503-127">The client implementation constructs an instance of the typed proxy to begin communicating with the service.</span></span>  
  
```  
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
  
 <span data-ttu-id="71503-128">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="71503-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="71503-129">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="71503-129">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="71503-130">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="71503-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="71503-131">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="71503-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="71503-132">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="71503-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="71503-133">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="71503-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="71503-134">předávání a vrácení komplexní dat najdete v tématu typy: [datové vazby v klientovi Windows Forms](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [datové vazby v klientovi Windows Presentation Foundation](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md), a [datové vazby v technologie ASP.NET Klienta](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)</span><span class="sxs-lookup"><span data-stu-id="71503-134"> passing and returning complex data types see: [Data Binding in a Windows Forms Client](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [Data Binding in a Windows Presentation Foundation Client](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md), and [Data Binding in an ASP.NET Client](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="71503-135">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="71503-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="71503-136">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="71503-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="71503-137">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="71503-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="71503-138">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="71503-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`  
  
## <a name="see-also"></a><span data-ttu-id="71503-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="71503-139">See Also</span></span>
