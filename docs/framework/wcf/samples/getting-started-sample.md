---
title: "Ukázka Začínáme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- basic samples [WCF], getting started
ms.assetid: 967a3d94-0261-49ff-b85a-20bb07f1af20
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2f97ad418f3d5ed197e8c35edf9e897eb393ef18
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-sample"></a><span data-ttu-id="3d203-102">Ukázka Začínáme</span><span class="sxs-lookup"><span data-stu-id="3d203-102">Getting Started Sample</span></span>
<span data-ttu-id="3d203-103">Ukázka Začínáme ukazuje, jak implementovat typické služby a typické klienta pomocí [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3d203-103">The Getting Started sample demonstrates how to implement a typical service and a typical client using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="3d203-104">Tato ukázka je základem pro všechny ostatní vzorky základní technologie.</span><span class="sxs-lookup"><span data-stu-id="3d203-104">This sample is the basis for all other basic technology samples.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d203-105">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="3d203-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3d203-106">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="3d203-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3d203-107">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="3d203-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3d203-108">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="3d203-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3d203-109">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="3d203-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\GettingStarted\GettingStarted`  
  
 <span data-ttu-id="3d203-110">Služba popisuje operace, které provádí v kontraktu služby, který zveřejňuje veřejně jako metadata.</span><span class="sxs-lookup"><span data-stu-id="3d203-110">The service describes the operations it performs in a service contract that it exposes publicly as metadata.</span></span> <span data-ttu-id="3d203-111">Služba také obsahuje kód k provedení operace.</span><span class="sxs-lookup"><span data-stu-id="3d203-111">The service also contains the code to implement the operations.</span></span>  
  
 <span data-ttu-id="3d203-112">Klient obsahuje definici kontraktu služby a třídu proxy pro přístup k službě.</span><span class="sxs-lookup"><span data-stu-id="3d203-112">The client contains a definition of the service contract and a proxy class for accessing the service.</span></span> <span data-ttu-id="3d203-113">Generování kódu proxy z metadat služby pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3d203-113">The proxy code is generated from the service metadata using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
 <span data-ttu-id="3d203-114">Na [!INCLUDE[wv](../../../../includes/wv-md.md)], služba je hostovaná v aktivační služby systému Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="3d203-114">On [!INCLUDE[wv](../../../../includes/wv-md.md)], the service is hosted in the Windows Activation Service (WAS).</span></span> <span data-ttu-id="3d203-115">Na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], se hostuje na Internetové informační služby (IIS) a ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3d203-115">On [!INCLUDE[wxp](../../../../includes/wxp-md.md)] and [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], it is hosted by Internet Information Services (IIS) and ASP.NET.</span></span> <span data-ttu-id="3d203-116">Hostování služby ve službě IIS nebo WAS umožňuje službě automaticky aktivovat při prvním přístupu.</span><span class="sxs-lookup"><span data-stu-id="3d203-116">Hosting a service in IIS or WAS allows the service to be activated automatically when it is accessed for the first time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d203-117">Pokud chcete začít pracovat s vzorku, který hostuje službu v konzolové aplikaci, místo služby IIS najdete v tématu [hostování na vlastním](../../../../docs/framework/wcf/samples/self-host.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="3d203-117">If you would prefer to get started with a sample that hosts the service in a console application instead of IIS, see the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span>  
  
 <span data-ttu-id="3d203-118">Služba a klient zadejte podrobnosti přístupu v souboru nastavení konfigurace, které poskytují flexibilitu v době nasazení.</span><span class="sxs-lookup"><span data-stu-id="3d203-118">The service and client specify access details in configuration file settings, which provide flexibility at the time of deployment.</span></span> <span data-ttu-id="3d203-119">To zahrnuje definici koncového bodu, které určuje adresy, vazby a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="3d203-119">This includes an endpoint definition that specifies an address, binding, and contract.</span></span> <span data-ttu-id="3d203-120">Vazba určuje přenos a zabezpečení podrobnosti jak služba je přístupná.</span><span class="sxs-lookup"><span data-stu-id="3d203-120">The binding specifies transport and security details for how the service is to be accessed.</span></span>  
  
 <span data-ttu-id="3d203-121">Nakonfiguruje službu běhového chování publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="3d203-121">The service configures a run-time behavior to publish its metadata.</span></span>  
  
 <span data-ttu-id="3d203-122">Služba se implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="3d203-122">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="3d203-123">Kontrakt je definována `ICalculator` rozhraní, která zpřístupňuje matematické operace (přidat, odečíst, násobit a dělit).</span><span class="sxs-lookup"><span data-stu-id="3d203-123">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="3d203-124">Klient podá požadavky a odpovědi služby s výsledkem dané matematické operace.</span><span class="sxs-lookup"><span data-stu-id="3d203-124">The client makes requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="3d203-125">Implementuje služby `ICalculator` kontrakt, který je definován v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="3d203-125">The service implements an `ICalculator` contract that is defined in the following code.</span></span>  
  
```vb  
' Define a service contract.  
    <ServiceContract(Namespace:="http://Microsoft.Samples.GettingStarted")>  
     Public Interface ICalculator  
        <OperationContract()>  
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()>  
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()>  
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()>  
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double  
    End Interface  
```  
  
```csharp  
// Define a service contract.  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
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
  
 <span data-ttu-id="3d203-126">Implementace služby vypočítá a vrátí odpovídající výsledek, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="3d203-126">The service implementation calculates and returns the appropriate result, as shown in the following example code.</span></span>  
  
```vb  
' Service class which implements the service contract.  
Public Class CalculatorService  
Implements ICalculator  
Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add  
Return n1 + n2  
End Function  
  
Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract  
Return n1 - n2  
End Function  
  
Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply  
Return n1 * n2  
End Function  
  
Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide  
Return n1 / n2  
End Function  
End Class  
```  
  
```csharp  
// Service class that implements the service contract.  
public class CalculatorService : ICalculator  
{  
    public double Add(double n1, double n2)  
    {  
        return n1 + n2;  
    }  
    public double Subtract(double n1, double n2)  
    {  
        return n1 - n2;  
    }  
    public double Multiply(double n1, double n2)  
    {  
        return n1 * n2;  
    }  
    public double Divide(double n1, double n2)  
    {  
        return n1 / n2;  
    }  
}  
```  
  
 <span data-ttu-id="3d203-127">Službu zpřístupní koncový bod pro komunikaci se službou, definovat pomocí konfiguračního souboru aplikace (Web.config), jak je znázorněno v následující ukázková konfigurace.</span><span class="sxs-lookup"><span data-stu-id="3d203-127">The service exposes an endpoint for communicating with the service, defined using a configuration file (Web.config), as shown in the following sample configuration.</span></span>  
  
```xaml  
<services>  
    <service   
        name="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- ICalculator is exposed at the base address provided by  
         host: http://localhost/servicemodelsamples/service.svc.  -->  
       <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
       ...  
    </service>  
</services>  
```  
  
 <span data-ttu-id="3d203-128">Službu zpřístupní koncový bod na základní adrese od hostitele služby IIS nebo WAS.</span><span class="sxs-lookup"><span data-stu-id="3d203-128">The service exposes the endpoint at the base address provided by the IIS or WAS host.</span></span> <span data-ttu-id="3d203-129">Vazba je nakonfigurována s standardní <xref:System.ServiceModel.WSHttpBinding>, který poskytuje komunikaci pomocí protokolu HTTP a standardní protokoly webové služby pro adresování a zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3d203-129">The binding is configured with a standard <xref:System.ServiceModel.WSHttpBinding>, which provides HTTP communication and standard Web service protocols for addressing and security.</span></span> <span data-ttu-id="3d203-130">Smlouva je `ICalculator` implementované službu.</span><span class="sxs-lookup"><span data-stu-id="3d203-130">The contract is the `ICalculator` implemented by the service.</span></span>  
  
 <span data-ttu-id="3d203-131">Podle konfigurace, služba je přístupná na http://localhost/servicemodelsamples/service.svc klientem na stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="3d203-131">As configured, the service can be accessed at http://localhost/servicemodelsamples/service.svc by a client on the same computer.</span></span> <span data-ttu-id="3d203-132">Pro klienty na computersto vzdálený přístup službu musí zadat název plně kvalifikované domény místo localhost.</span><span class="sxs-lookup"><span data-stu-id="3d203-132">For clients on remote computersto access the service, a fully-qualified domain name must be specified instead of localhost.</span></span>  
  
 <span data-ttu-id="3d203-133">Rozhraní framework nevystavuje metadata ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="3d203-133">The framework does not expose metadata by default.</span></span> <span data-ttu-id="3d203-134">Jako takový službu Zapne <xref:System.ServiceModel.Description.ServiceMetadataBehavior> a zpřístupní koncový bod metadat exchange (MEX) v http://localhost/servicemodelsamples/service.svc/mex.</span><span class="sxs-lookup"><span data-stu-id="3d203-134">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> and exposes a metadata exchange (MEX) endpoint at http://localhost/servicemodelsamples/service.svc/mex.</span></span> <span data-ttu-id="3d203-135">Následující konfigurace ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="3d203-135">The following configuration demonstrates this.</span></span>  
  
```xaml  
<system.serviceModel>  
  <services>  
    <service   
        name="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
      ...  
      <!-- the mex endpoint is explosed at  
       http://localhost/servicemodelsamples/service.svc/mex -->  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange" />  
    </service>  
  </services>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults  
   attribute to true-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
        <serviceMetadata httpGetEnabled="True"/>  
        <serviceDebug includeExceptionDetailInFaults="False" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="3d203-136">Klient komunikuje pomocí danou zakázku typu pomocí třídy klienta, který je generovaný [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3d203-136">The client communicates using a given contract type by using a client class that is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="3d203-137">Tato generovaného klienta je obsažený v souboru generatedClient.cs nebo generatedClient.vb.</span><span class="sxs-lookup"><span data-stu-id="3d203-137">This generated client is contained in the file generatedClient.cs or generatedClient.vb.</span></span> <span data-ttu-id="3d203-138">Tento nástroj načte metadata pro danou službu a vygeneruje klienta pro použití klientskou aplikací pro komunikaci pomocí typu danou zakázku.</span><span class="sxs-lookup"><span data-stu-id="3d203-138">This utility retrieves metadata for a given service and generates a client for use by the client application to communicate using a given contract type.</span></span> <span data-ttu-id="3d203-139">Hostovaná služba musí být k dispozici pro generování kódu klienta, protože služba se používá k načtení aktualizované metadata.</span><span class="sxs-lookup"><span data-stu-id="3d203-139">The hosted service must be available to generate the client code, because the service is used to retrieve the updated metadata.</span></span>  
  
 <span data-ttu-id="3d203-140">Spusťte následující příkaz z příkazového řádku sady SDK v adresáři klienta ke generování typové proxy server:</span><span class="sxs-lookup"><span data-stu-id="3d203-140">Run the following command from the SDK command prompt in the client directory to generate the typed proxy:</span></span>  
  
```  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
```  
  
 <span data-ttu-id="3d203-141">Ke generování klienta v jazyce Visual Basic typu následující z příkazového řádku SDK:</span><span class="sxs-lookup"><span data-stu-id="3d203-141">To generate client in Visual Basic type the following from the SDK command prompt:</span></span>  
  
 `Svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb`  
  
 <span data-ttu-id="3d203-142">Pomocí generovaného klienta, klient může získat koncový bod uvedená služba nakonfigurováním příslušnou adresu a vazby.</span><span class="sxs-lookup"><span data-stu-id="3d203-142">By using the generated client, the client can access a given service endpoint by configuring the appropriate address and binding.</span></span> <span data-ttu-id="3d203-143">Jako službu Klient použije konfigurační soubor (App.config) k určení koncový bod, pomocí kterého chce komunikovat.</span><span class="sxs-lookup"><span data-stu-id="3d203-143">Like the service, the client uses a configuration file (App.config) to specify the endpoint with which it wants to communicate.</span></span> <span data-ttu-id="3d203-144">Konfigurace klienta koncový bod se skládá z absolutní adresu pro koncový bod služby, vazby a kontrakt, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3d203-144">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract, as shown in the following example.</span></span>  
  
```xaml  
<client>  
     <endpoint  
         address="http://localhost/servicemodelsamples/service.svc"   
         binding="wsHttpBinding"   
         contract=" Microsoft.ServiceModel.Samples.ICalculator" />  
</client>  
```  
  
 <span data-ttu-id="3d203-145">Implementace klienta vytvoří klienta a používá rozhraní typové zahájíte komunikaci se službou, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="3d203-145">The client implementation instantiates the client and uses the typed interface to begin communicating with the service, as shown in the following example code.</span></span>  
  
```vb  
' Create a client  
Dim client As New CalculatorClient()  
  
' Call the Add service operation.  
            Dim value1 = 100.0R  
            Dim value2 = 15.99R  
            Dim result = client.Add(value1, value2)  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)  
  
' Call the Subtract service operation.  
value1 = 145.00R  
value2 = 76.54R  
result = client.Subtract(value1, value2)  
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)  
  
' Call the Multiply service operation.  
value1 = 9.00R  
value2 = 81.25R  
result = client.Multiply(value1, value2)  
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)  
  
' Call the Divide service operation.  
value1 = 22.00R  
value2 = 7.00R  
result = client.Divide(value1, value2)  
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)  
  
'Closing the client gracefully closes the connection and cleans up resources  
```  
  
```csharp  
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
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
  
//Closing the client releases all communication resources.  
client.Close();  
```  
  
 <span data-ttu-id="3d203-146">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="3d203-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3d203-147">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="3d203-147">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="3d203-148">Ukázka Začínáme ukazuje standardní způsob, jak vytvořit klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="3d203-148">The Getting Started sample shows the standard way to create a service and client.</span></span> <span data-ttu-id="3d203-149">Druhá [základní](../../../../docs/framework/wcf/samples/basic-sample.md) pracovat s tímto příkladem k předvedení funkcí určitý produkt.</span><span class="sxs-lookup"><span data-stu-id="3d203-149">The other [Basic](../../../../docs/framework/wcf/samples/basic-sample.md) build on this sample to demonstrate specific product features.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3d203-150">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="3d203-150">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3d203-151">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d203-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="3d203-152">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d203-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="3d203-153">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d203-153">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d203-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d203-154">See Also</span></span>  
 [<span data-ttu-id="3d203-155">Postupy: Hostování služby WCF ve spravované aplikaci</span><span class="sxs-lookup"><span data-stu-id="3d203-155">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [<span data-ttu-id="3d203-156">Postupy: Hostování služby WCF v IIS</span><span class="sxs-lookup"><span data-stu-id="3d203-156">How to: Host a WCF Service in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
