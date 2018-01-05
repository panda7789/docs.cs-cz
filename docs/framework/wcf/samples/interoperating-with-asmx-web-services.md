---
title: "Spolupráce s webovými službami ASMX"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7c11f0a-9e68-4f03-a6b1-39cf478d1a89
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ce0f548f345e3711edfd547b2e6879fafdbd0ad4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="interoperating-with-asmx-web-services"></a><span data-ttu-id="0c7db-102">Spolupráce s webovými službami ASMX</span><span class="sxs-lookup"><span data-stu-id="0c7db-102">Interoperating with ASMX Web Services</span></span>
<span data-ttu-id="0c7db-103">Tento příklad ukazuje, jak integrovat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klientská aplikace s existující ASMX webovou službu.</span><span class="sxs-lookup"><span data-stu-id="0c7db-103">This sample demonstrates how to integrate a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client application with an existing ASMX Web service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c7db-104">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="0c7db-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0c7db-105">Tato ukázka se skládá z konzoly programu klienta (.exe) a služby knihovny (DLL) hostované Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="0c7db-105">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="0c7db-106">Služba je webové služby ASMX, který implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="0c7db-106">The service is an ASMX Web Service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="0c7db-107">Službu zpřístupní matematické operace (`Add`, `Subtract`, `Multiply`, a `Divide`).</span><span class="sxs-lookup"><span data-stu-id="0c7db-107">The service exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="0c7db-108">Klient podá synchronní požadavky a odpovědi služby s výsledkem matematické operace.</span><span class="sxs-lookup"><span data-stu-id="0c7db-108">The client makes synchronous requests to a math operation and the service replies with the result.</span></span> <span data-ttu-id="0c7db-109">Činnost klienta je viditelný v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="0c7db-109">Client activity is visible in the console window.</span></span>  
  
 <span data-ttu-id="0c7db-110">Implementace ASMX webové služby, které jsou uvedené v následující vzorový kód vypočítá a vrátí odpovídající výsledek.</span><span class="sxs-lookup"><span data-stu-id="0c7db-110">The ASMX Web service implementation shown in the following sample code calculates and returns the appropriate result.</span></span>  
  
```  
[WebService(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class CalculatorService : System.Web.Services.WebService  
    {  
        [WebMethod]  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
        [WebMethod]  
        public double Subtract(double n1, double n2)  
        {  
            return n1 - n2;  
        }  
        [WebMethod]  
        public double Multiply(double n1, double n2)  
        {  
            return n1 * n2;  
        }  
        [WebMethod]  
        public double Divide(double n1, double n2)  
        {  
            return n1 / n2;  
        }  
    }  
```  
  
 <span data-ttu-id="0c7db-111">Podle konfigurace, služba je přístupná na http://localhost/servicemodelsamples/service.asmx klientem na stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="0c7db-111">As configured, the service can be accessed at http://localhost/servicemodelsamples/service.asmx by a client on the same machine.</span></span> <span data-ttu-id="0c7db-112">Pro klienty na vzdálených počítačích pro přístup ke službě je nutné zadat platný kvalifikovaný název domény místo localhost.</span><span class="sxs-lookup"><span data-stu-id="0c7db-112">For clients on remote machines to access the service, a qualified domain name must be specified instead of localhost.</span></span>  
  
 <span data-ttu-id="0c7db-113">Komunikace probíhá prostřednictvím klienta vygenerované [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="0c7db-113">Communication is done through a client generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="0c7db-114">Klient je obsažený v souboru generatedClient.cs.</span><span class="sxs-lookup"><span data-stu-id="0c7db-114">The client is contained in the file generatedClient.cs.</span></span> <span data-ttu-id="0c7db-115">Služba ASMX musí být k dispozici pro generování kódu proxy, protože se používá k načtení aktualizované metadata.</span><span class="sxs-lookup"><span data-stu-id="0c7db-115">The ASMX service must be available to generate the proxy code, because it is used to retrieve the updated metadata.</span></span> <span data-ttu-id="0c7db-116">Spusťte následující příkaz z příkazového řádku v adresáři klienta ke generování typem proxy.</span><span class="sxs-lookup"><span data-stu-id="0c7db-116">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedClient.cs  
```  
  
 <span data-ttu-id="0c7db-117">Pomocí generovaného klienta, můžete přejít koncového bodu služby pomocí konfigurace příslušnou adresu a vazby.</span><span class="sxs-lookup"><span data-stu-id="0c7db-117">By using the generated client, you can access a service endpoint by configuring the appropriate address and binding.</span></span> <span data-ttu-id="0c7db-118">Jako službu Klient použije konfigurační soubor (App.config) k určení koncového bodu pro komunikaci s.</span><span class="sxs-lookup"><span data-stu-id="0c7db-118">Like the service, the client uses a configuration file (App.config) to specify the endpoint to communicate with.</span></span> <span data-ttu-id="0c7db-119">Konfigurace klienta koncový bod se skládá z absolutní adresu pro koncový bod služby, vazby a kontrakt, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="0c7db-119">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract, as shown in the following sample configuration.</span></span>  
  
```xml  
<client>  
   <endpoint   
      address="http://localhost/ServiceModelSamples/service.asmx"   
      binding="basicHttpBinding"   
      contract="Microsoft.ServiceModel.Samples.CalculatorServiceSoap" />  
</client>  
```  
  
 <span data-ttu-id="0c7db-120">Implementace klienta vytvoří instanci objektu generovaného klienta.</span><span class="sxs-lookup"><span data-stu-id="0c7db-120">The client implementation constructs an instance of the generated client.</span></span> <span data-ttu-id="0c7db-121">Generovaného klienta můžete potom použít ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="0c7db-121">The generated client can then be used to communicate with the service.</span></span>  
  
```  
// Create a client.  
CalculatorServiceSoapClient client = new CalculatorServiceSoapClient();  
  
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
  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```  
  
 <span data-ttu-id="0c7db-122">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="0c7db-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="0c7db-123">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="0c7db-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0c7db-124">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="0c7db-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0c7db-125">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0c7db-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="0c7db-126">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0c7db-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="0c7db-127">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0c7db-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0c7db-128">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="0c7db-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0c7db-129">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="0c7db-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0c7db-130">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="0c7db-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0c7db-131">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="0c7db-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\Interop\ASMX`  
  
## <a name="see-also"></a><span data-ttu-id="0c7db-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c7db-132">See Also</span></span>
