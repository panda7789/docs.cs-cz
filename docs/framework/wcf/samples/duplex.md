---
title: Duplex
ms.date: 03/30/2017
helpviewer_keywords:
- Duplex Service Contract
ms.assetid: bc5de6b6-1a63-42a3-919a-67d21bae24e0
ms.openlocfilehash: b00f5dd31ba572a2c8fb5301cc7ae9ddda77f0e5
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045041"
---
# <a name="duplex"></a><span data-ttu-id="d9562-102">Duplex</span><span class="sxs-lookup"><span data-stu-id="d9562-102">Duplex</span></span>

<span data-ttu-id="d9562-103">Duplexní Ukázka ukazuje, jak definovat a implementovat duplexní kontrakt.</span><span class="sxs-lookup"><span data-stu-id="d9562-103">The Duplex sample demonstrates how to define and implement a duplex contract.</span></span> <span data-ttu-id="d9562-104">Duplexní komunikace probíhá, když klient vytvoří relaci se službou a poskytne službě kanál, na kterém může služba odesílat zprávy zpátky klientovi.</span><span class="sxs-lookup"><span data-stu-id="d9562-104">Duplex communication occurs when a client establishes a session with a service and gives the service a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="d9562-105">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="d9562-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="d9562-106">Duplexní kontrakt je definován jako dvojice rozhraní – primární rozhraní od klienta ke službě a rozhraní zpětného volání od služby ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="d9562-106">A duplex contract is defined as a pair of interfaces—a primary interface from the client to the service and a callback interface from the service to the client.</span></span> <span data-ttu-id="d9562-107">V této ukázce `ICalculatorDuplex` rozhraní umožňuje klientovi provádět matematické operace a vypočítat výsledek v relaci.</span><span class="sxs-lookup"><span data-stu-id="d9562-107">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating the result over a session.</span></span> <span data-ttu-id="d9562-108">Služba vrátí výsledky na `ICalculatorDuplexCallback` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d9562-108">The service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="d9562-109">Duplexní smlouva vyžaduje relaci, protože je nutné vytvořit kontext, který bude korelovat sadu zpráv odesílaných mezi klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="d9562-109">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span>

> [!NOTE]
> <span data-ttu-id="d9562-110">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="d9562-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="d9562-111">V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="d9562-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="d9562-112">Duplexní smlouva je definována takto:</span><span class="sxs-lookup"><span data-stu-id="d9562-112">The duplex contract is defined as follows:</span></span>

```csharp
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

<span data-ttu-id="d9562-113">Třída implementuje primární `ICalculatorDuplex`rozhraní. `CalculatorService`</span><span class="sxs-lookup"><span data-stu-id="d9562-113">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="d9562-114">Služba používá <xref:System.ServiceModel.InstanceContextMode.PerSession> režim instance k uchování výsledku pro každou relaci.</span><span class="sxs-lookup"><span data-stu-id="d9562-114">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="d9562-115">Soukromá vlastnost s názvem `Callback` se používá pro přístup k kanálu zpětného volání ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="d9562-115">A private property named `Callback` is used to access the callback channel to the client.</span></span> <span data-ttu-id="d9562-116">Služba používá zpětné volání pro posílání zpráv zpátky do klienta prostřednictvím rozhraní zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="d9562-116">The service uses the callback for sending messages back to the client through the callback interface.</span></span>

```csharp
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
        Callback.Equation($"{equation} = {result}");
        equation = result.ToString();
    }

    public void AddTo(double n)
    {
        result += n;
        equation += $" + {n}";
        Callback.Result(result);
    }

    //...

    ICalculatorDuplexCallback Callback
    {
        get
        {
            return OperationContext.Current.GetCallbackChannel<ICalculatorDuplexCallback>();
        }
    }
}
```

<span data-ttu-id="d9562-117">Klient musí poskytnout třídu, která implementuje rozhraní zpětného volání pro oboustrannou smlouvu pro příjem zpráv ze služby.</span><span class="sxs-lookup"><span data-stu-id="d9562-117">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="d9562-118">V ukázce `CallbackHandler` je třída definována pro `ICalculatorDuplexCallback` implementaci rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d9562-118">In the sample, a `CallbackHandler` class is defined to implement the `ICalculatorDuplexCallback` interface.</span></span>

```csharp
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

<span data-ttu-id="d9562-119">Proxy, který je generován pro duplexní kontrakt, vyžaduje <xref:System.ServiceModel.InstanceContext> , aby byl po konstrukci poskytnut.</span><span class="sxs-lookup"><span data-stu-id="d9562-119">The proxy that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> to be provided upon construction.</span></span> <span data-ttu-id="d9562-120"><xref:System.ServiceModel.InstanceContext> Slouží jako web pro objekt, který implementuje rozhraní zpětného volání a zpracovává zprávy odesílané zpět ze služby.</span><span class="sxs-lookup"><span data-stu-id="d9562-120">This <xref:System.ServiceModel.InstanceContext> is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="d9562-121">Objekt <xref:System.ServiceModel.InstanceContext> je vytvořen s instancí `CallbackHandler` třídy.</span><span class="sxs-lookup"><span data-stu-id="d9562-121">An <xref:System.ServiceModel.InstanceContext> is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="d9562-122">Tento objekt zpracovává zprávy odesílané ze služby klientovi na rozhraní zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="d9562-122">This object handles messages sent from the service to the client on the callback interface.</span></span>

```csharp
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

<span data-ttu-id="d9562-123">Konfigurace byla změněna tak, aby poskytovala vazbu, která podporuje komunikaci relace i duplexní komunikaci.</span><span class="sxs-lookup"><span data-stu-id="d9562-123">The configuration has been modified to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="d9562-124">`wsDualHttpBinding` Podporuje komunikaci relací a umožňuje duplexní komunikaci tím, že poskytuje duální připojení HTTP, jedno pro každý směr.</span><span class="sxs-lookup"><span data-stu-id="d9562-124">The `wsDualHttpBinding` supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span> <span data-ttu-id="d9562-125">V rámci služby je jediným rozdílem v konfiguraci použití vazby.</span><span class="sxs-lookup"><span data-stu-id="d9562-125">On the service, the only difference in configuration is the binding that is used.</span></span> <span data-ttu-id="d9562-126">Na straně klienta je nutné nakonfigurovat adresu, kterou může server používat pro připojení ke klientovi, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="d9562-126">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>

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

<span data-ttu-id="d9562-127">Při spuštění ukázky se zobrazí zprávy vracené klientovi na rozhraní zpětného volání, které je odesláno ze služby.</span><span class="sxs-lookup"><span data-stu-id="d9562-127">When you run the sample, you see the messages that are returned to the client on the callback interface that is sent from the service.</span></span> <span data-ttu-id="d9562-128">Po dokončení všech operací se zobrazí každý mezilehlé výsledek následovaný celým vzorcem.</span><span class="sxs-lookup"><span data-stu-id="d9562-128">Each intermediate result is displayed, followed by the entire equation upon the completion of all operations.</span></span> <span data-ttu-id="d9562-129">Pro vypnutí klienta stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="d9562-129">Press ENTER to shut down the client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d9562-130">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="d9562-130">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="d9562-131">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d9562-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="d9562-132">Pokud chcete vytvořit C#edici, C++nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d9562-132">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="d9562-133">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d9562-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="d9562-134">Pokud spouštíte klienta v konfiguraci mezi počítači, nezapomeňte nahradit "localhost" v `address` atributu [ \<koncového bodu > \<> elementu klienta](../../configure-apps/file-schema/wcf/endpoint-of-client.md) a atributu `clientBaseAddress` [ vazba\<>](../../../../docs/framework/misc/binding.md) [ elementu\<prvku > elementu WSDualHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) s názvem příslušného počítače, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d9562-134">When running the client in a cross-machine configuration, be sure to replace "localhost" in both the `address` attribute of the [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element and the `clientBaseAddress` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) element of the [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown in the following:</span></span>

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
> <span data-ttu-id="d9562-135">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="d9562-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d9562-136">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="d9562-136">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="d9562-137">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="d9562-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d9562-138">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d9562-138">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Duplex`
