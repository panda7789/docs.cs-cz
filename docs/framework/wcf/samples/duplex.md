---
title: Duplex
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Duplex Service Contract
ms.assetid: bc5de6b6-1a63-42a3-919a-67d21bae24e0
caps.latest.revision: "40"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0baf0a188ccb67f50a57ea0a56bb16dc40c53bbc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="duplex"></a><span data-ttu-id="69d4f-102">Duplex</span><span class="sxs-lookup"><span data-stu-id="69d4f-102">Duplex</span></span>
<span data-ttu-id="69d4f-103">Duplexní ukázka ukazuje, jak definovat a implementovat duplexního kontraktu.</span><span class="sxs-lookup"><span data-stu-id="69d4f-103">The Duplex sample demonstrates how to define and implement a duplex contract.</span></span> <span data-ttu-id="69d4f-104">Duplexní komunikace nastane, když klient vytvoří relaci se službou a poskytuje služby kanál, na kterém služba mohou zasílat zprávy zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="69d4f-104">Duplex communication occurs when a client establishes a session with a service and gives the service a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="69d4f-105">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="69d4f-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="69d4f-106">Duplexní kontrakt je definován jako dvojice rozhraní – primární rozhraní z klienta pro službu a rozhraní pro zpětné volání ze služby do klienta.</span><span class="sxs-lookup"><span data-stu-id="69d4f-106">A duplex contract is defined as a pair of interfaces—a primary interface from the client to the service and a callback interface from the service to the client.</span></span> <span data-ttu-id="69d4f-107">V této ukázce `ICalculatorDuplex` rozhraní, které umožňuje provádět matematické operace, výpočet výsledek přes relaci klienta.</span><span class="sxs-lookup"><span data-stu-id="69d4f-107">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating the result over a session.</span></span> <span data-ttu-id="69d4f-108">Služba vrátí výsledky na `ICalculatorDuplexCallback` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="69d4f-108">The service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="69d4f-109">Duplexní kontrakt vyžaduje relaci, protože kontextu musí být stanovena ke korelaci sadu zprávy odesílané mezi klientem a službu.</span><span class="sxs-lookup"><span data-stu-id="69d4f-109">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69d4f-110">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="69d4f-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="69d4f-111">V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="69d4f-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="69d4f-112">Duplexní kontrakt je definován následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="69d4f-112">The duplex contract is defined as follows:</span></span>  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required,  
                 CallbackContract=typeof(ICalculatorDuplexCallback))]  
public interface ICalculatorDuplex  
{  
    [OperationContract(IsOneWay = true)]  
    void Clear();  
    [OperationContract(IsOneWay = true)]  
    void AddTo(double n);  
    [OperationContract(IsOneWay = true)]  
    void SubtractFrom(double n);  
    [OperationContract(IsOneWay = true)]  
    void MultiplyBy(double n);  
    [OperationContract(IsOneWay = true)]  
    void DivideBy(double n);  
}  
  
public interface ICalculatorDuplexCallback  
{  
    [OperationContract(IsOneWay = true)]  
    void Result(double result);  
    [OperationContract(IsOneWay = true)]  
    void Equation(string eqn);  
}  
```  
  
 <span data-ttu-id="69d4f-113">`CalculatorService` Třída implementuje primární `ICalculatorDuplex` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="69d4f-113">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="69d4f-114">Služba používá <xref:System.ServiceModel.InstanceContextMode.PerSession> instance režimu zachování výsledek pro každou relaci.</span><span class="sxs-lookup"><span data-stu-id="69d4f-114">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="69d4f-115">Soukromá vlastnost s názvem `Callback` se používá pro přístup k kanál zpětného volání pro klienta.</span><span class="sxs-lookup"><span data-stu-id="69d4f-115">A private property named `Callback` is used to access the callback channel to the client.</span></span> <span data-ttu-id="69d4f-116">Služba používá zpětné volání pro odesílání zpráv zpět do klienta přes rozhraní zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="69d4f-116">The service uses the callback for sending messages back to the client through the callback interface.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
public class CalculatorService : ICalculatorDuplex  
{  
    double result = 0.0D;  
    string equation;  
  
    public CalculatorService()  
    {  
        equation = result.ToString();  
    }  
  
    public void Clear()  
    {  
        Callback.Equation(equation + " = " + result.ToString());  
        equation = result.ToString();  
    }  
  
    public void AddTo(double n)  
    {  
        result += n;  
        equation += " + " + n.ToString();  
        Callback.Result(result);  
    }  
    ...  
    ICalculatorDuplexCallback Callback  
    {  
        get  
        {  
            return OperationContext.Current.GetCallbackChannel<ICalculatorDuplexCallback>();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="69d4f-117">Klient musí poskytnout třídu, která implementuje rozhraní zpětné volání duplexního kontraktu pro příjem zpráv ze služby.</span><span class="sxs-lookup"><span data-stu-id="69d4f-117">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="69d4f-118">V ukázce `CallbackHandler` třída definovaná implementovat `ICalculatorDuplexCallback` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="69d4f-118">In the sample, a `CallbackHandler` class is defined to implement the `ICalculatorDuplexCallback` interface.</span></span>  
  
```  
public class CallbackHandler : ICalculatorDuplexCallback  
{  
   public void Result(double result)  
   {  
      Console.WriteLine("Result({0})", result);  
   }  
  
   public void Equation(string equation)  
   {  
      Console.WriteLine("Equation({0}", equation);  
   }  
}  
```  
  
 <span data-ttu-id="69d4f-119">Proxy server, který se vygeneruje pro vyžaduje duplexního kontraktu <xref:System.ServiceModel.InstanceContext> při vytváření, musíte zadat.</span><span class="sxs-lookup"><span data-stu-id="69d4f-119">The proxy that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> to be provided upon construction.</span></span> <span data-ttu-id="69d4f-120">To <xref:System.ServiceModel.InstanceContext> slouží jako lokality pro objekt, který implementuje rozhraní zpětného volání a zpracovává zprávy, které se odesílají zpět ze služby.</span><span class="sxs-lookup"><span data-stu-id="69d4f-120">This <xref:System.ServiceModel.InstanceContext> is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="69d4f-121"><xref:System.ServiceModel.InstanceContext> Je vytvořený pomocí instance `CallbackHandler` třídy.</span><span class="sxs-lookup"><span data-stu-id="69d4f-121">An <xref:System.ServiceModel.InstanceContext> is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="69d4f-122">Tento objekt zpracovává zprávy odeslané ze služby pro klienta v rozhraní zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="69d4f-122">This object handles messages sent from the service to the client on the callback interface.</span></span>  
  
```  
// Construct InstanceContext to handle messages on callback interface.  
InstanceContext instanceContext = new InstanceContext(new CallbackHandler());  
  
// Create a client.  
CalculatorDuplexClient client = new CalculatorDuplexClient(instanceContext);  
  
Console.WriteLine("Press <ENTER> to terminate client once the output is displayed.");  
Console.WriteLine();  
  
// Call the AddTo service operation.  
double value = 100.00D;  
client.AddTo(value);  
  
// Call the SubtractFrom service operation.  
value = 50.00D;  
client.SubtractFrom(value);  
  
// Call the MultiplyBy service operation.  
value = 17.65D;  
client.MultiplyBy(value);  
  
// Call the DivideBy service operation.  
value = 2.00D;  
client.DivideBy(value);  
  
// Complete equation.  
client.Clear();  
  
Console.ReadLine();  
  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```  
  
 <span data-ttu-id="69d4f-123">Má být poskytnuta vazba, která podporuje komunikaci relace a duplexní komunikace se změnila konfigurace.</span><span class="sxs-lookup"><span data-stu-id="69d4f-123">The configuration has been modified to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="69d4f-124">`wsDualHttpBinding` Podporuje komunikaci relace a umožňuje duplexní komunikace tím, že poskytuje duální připojení protokolu HTTP, jeden pro všechny směry.</span><span class="sxs-lookup"><span data-stu-id="69d4f-124">The `wsDualHttpBinding` supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span> <span data-ttu-id="69d4f-125">Ve službě je jediným rozdílem v konfiguraci vazby, který se používá.</span><span class="sxs-lookup"><span data-stu-id="69d4f-125">On the service, the only difference in configuration is the binding that is used.</span></span> <span data-ttu-id="69d4f-126">Na klientovi je nutné nakonfigurovat adresu, která server můžete použít pro připojení k klienta, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="69d4f-126">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>  
  
```xml  
<client>  
  <endpoint name=""  
            address="http://localhost/servicemodelsamples/service.svc"   
            binding="wsDualHttpBinding"   
            bindingConfiguration="DuplexBinding"   
            contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />  
</client>  
  
<bindings>  
  <!-- Configure a binding that support duplex communication. -->  
  <wsDualHttpBinding>  
    <binding name="DuplexBinding"   
             clientBaseAddress="http://localhost:8000/myClient/">  
    </binding>  
  </wsDualHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="69d4f-127">Při spuštění vzorového uvidíte zprávy, které se vrátí klientovi v rozhraní zpětné volání, která je odeslána ze služby.</span><span class="sxs-lookup"><span data-stu-id="69d4f-127">When you run the sample, you see the messages that are returned to the client on the callback interface that is sent from the service.</span></span> <span data-ttu-id="69d4f-128">Zobrazí se každý zprostředkující výsledek, za nímž následuje celý rovnice po dokončení všech operací.</span><span class="sxs-lookup"><span data-stu-id="69d4f-128">Each intermediate result is displayed, followed by the entire equation upon the completion of all operations.</span></span> <span data-ttu-id="69d4f-129">Stisknutím klávesy ENTER vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="69d4f-129">Press ENTER to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="69d4f-130">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="69d4f-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="69d4f-131">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="69d4f-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="69d4f-132">Sestavení C#, C++ nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="69d4f-132">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="69d4f-133">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="69d4f-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="69d4f-134">Při spuštění klienta v počítači konfiguraci, nezapomeňte nahradit "localhost" v obou `address` atribut [koncový bod](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu a `clientBaseAddress` atribut [ \< Vazba >](../../../../docs/framework/misc/binding.md) element [ \<– wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element s názvem příslušný počítač, jak je uvedené v následující:</span><span class="sxs-lookup"><span data-stu-id="69d4f-134">When running the client in a cross-machine configuration, be sure to replace "localhost" in both the `address` attribute of the [endpoint](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element and the `clientBaseAddress` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) element of the [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown in the following:</span></span>  
  
    ```xml  
    <client>  
    <endpoint name = ""  
    address="http://service_machine_name/servicemodelsamples/service.svc"  
    ... />  
    </client>  
    ...  
    <wsDualHttpBinding>  
    <binding name="DuplexBinding" clientBaseAddress="http://client_machine_name:8000/myClient/">  
    </binding>  
    </wsDualHttpBinding>  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="69d4f-135">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="69d4f-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="69d4f-136">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="69d4f-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="69d4f-137">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="69d4f-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="69d4f-138">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="69d4f-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Duplex`  
  
## <a name="see-also"></a><span data-ttu-id="69d4f-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="69d4f-139">See Also</span></span>
