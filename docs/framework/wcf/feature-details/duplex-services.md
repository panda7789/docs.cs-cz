---
title: Duplexní služby
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: 3f8e13c6983b6c3a88bc1d9f559f7fac3d6342d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110081"
---
# <a name="duplex-services"></a><span data-ttu-id="cb330-102">Duplexní služby</span><span class="sxs-lookup"><span data-stu-id="cb330-102">Duplex Services</span></span>
<span data-ttu-id="cb330-103">Duplexní kontrakt služeb je vzoru výměny zpráv, ve kterém oba koncové body můžete odesílat zprávy do jiné nezávisle na sobě.</span><span class="sxs-lookup"><span data-stu-id="cb330-103">A duplex service contract is a message exchange pattern in which both endpoints can send messages to the other independently.</span></span> <span data-ttu-id="cb330-104">Duplexní služby proto může odesílat zprávy zpět do koncový bod klienta, poskytování podobně jako události.</span><span class="sxs-lookup"><span data-stu-id="cb330-104">A duplex service, therefore, can send messages back to the client endpoint, providing event-like behavior.</span></span> <span data-ttu-id="cb330-105">Duplexní komunikaci nastane, pokud se klient připojí ke službě a poskytuje službu s kanálem, na kterém služba odesílat zprávy o zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="cb330-105">Duplex communication occurs when a client connects to a service and provides the service with a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="cb330-106">Všimněte si, že události podobně duplexní služby funguje jenom v rámci relace.</span><span class="sxs-lookup"><span data-stu-id="cb330-106">Note that the event-like behavior of duplex services only works within a session.</span></span>  
  
 <span data-ttu-id="cb330-107">K vytvoření duplexního kontraktu vytvořit dvojici rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cb330-107">To create a duplex contract you create a pair of interfaces.</span></span> <span data-ttu-id="cb330-108">První je rozhraní kontraktu služby, který popisuje operace, které může klient vyvolat.</span><span class="sxs-lookup"><span data-stu-id="cb330-108">The first is the service contract interface that describes the operations that a client can invoke.</span></span> <span data-ttu-id="cb330-109">Musíte zadat Tento kontrakt služby *kontrakt zpětného volání* v <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="cb330-109">That service contract must specify a *callback contract* in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="cb330-110">Smlouva zpětného volání je rozhraní, které definuje operace, které můžete volat službu na koncový bod klienta.</span><span class="sxs-lookup"><span data-stu-id="cb330-110">The callback contract is the interface that defines the operations that the service can call on the client endpoint.</span></span> <span data-ttu-id="cb330-111">Duplexní kontrakt nevyžaduje relace, i když duplexní vazeb poskytovaných systémem Ujistěte se, jejich použití.</span><span class="sxs-lookup"><span data-stu-id="cb330-111">A duplex contract does not require a session, although the system-provided duplex bindings make use of them.</span></span>  
  
 <span data-ttu-id="cb330-112">Následuje příklad duplexního kontraktu.</span><span class="sxs-lookup"><span data-stu-id="cb330-112">The following is an example of a duplex contract.</span></span>  
  
 [!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
 [!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]  
  
 <span data-ttu-id="cb330-113">`CalculatorService` Třída implementuje primární `ICalculatorDuplex` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cb330-113">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="cb330-114">Služba používá <xref:System.ServiceModel.InstanceContextMode.PerSession> režimu instance udržovat výsledek pro každou relaci.</span><span class="sxs-lookup"><span data-stu-id="cb330-114">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="cb330-115">Soukromá vlastnost s názvem `Callback` přistupuje k zpětného volání kanálu ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="cb330-115">A private property named `Callback` accesses the callback channel to the client.</span></span> <span data-ttu-id="cb330-116">Služba používá zpětné volání pro odesílání zpráv zpět do klienta prostřednictvím rozhraní zpětného volání, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="cb330-116">The service uses the callback for sending messages back to the client through the callback interface, as shown in the following sample code.</span></span>  
  
 [!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
 [!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]  
  
 <span data-ttu-id="cb330-117">Klient musí poskytnout třídu, která implementuje rozhraní zpětného volání duplexní kontrakt pro příjem zpráv ze služby.</span><span class="sxs-lookup"><span data-stu-id="cb330-117">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="cb330-118">Následující ukázkový kód ukazuje `CallbackHandler` třídu, která implementuje `ICalculatorDuplexCallback` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cb330-118">The following sample code shows a `CallbackHandler` class that implements the `ICalculatorDuplexCallback` interface.</span></span>  
  
 [!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
 [!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]  
  
 <span data-ttu-id="cb330-119">Klient WCF, který je vygenerován pro duplexní kontrakt vyžaduje <xref:System.ServiceModel.InstanceContext> poskytované při konstrukci třídy.</span><span class="sxs-lookup"><span data-stu-id="cb330-119">The WCF client that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> class to be provided upon construction.</span></span> <span data-ttu-id="cb330-120">To <xref:System.ServiceModel.InstanceContext> třída se používá jako web pro objekt, který implementuje rozhraní zpětného volání a zpracovává zprávy odeslané ze služby.</span><span class="sxs-lookup"><span data-stu-id="cb330-120">This <xref:System.ServiceModel.InstanceContext> class is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="cb330-121"><xref:System.ServiceModel.InstanceContext> Třídy je vytvořený pomocí instance `CallbackHandler` třídy.</span><span class="sxs-lookup"><span data-stu-id="cb330-121">An <xref:System.ServiceModel.InstanceContext> class is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="cb330-122">Tento objekt zpracovává zprávy odeslané do klienta v rozhraní zpětného volání ze služby.</span><span class="sxs-lookup"><span data-stu-id="cb330-122">This object handles messages sent from the service to the client on the callback interface.</span></span>  
  
 [!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
 [!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]  
  
 <span data-ttu-id="cb330-123">Konfigurace pro službu, musíte nastavit má být poskytnuta vazba, která podporuje komunikace relace a duplexní komunikaci.</span><span class="sxs-lookup"><span data-stu-id="cb330-123">The configuration for the service must be set up to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="cb330-124">`wsDualHttpBinding` Element podporuje komunikaci relace a umožňuje duplexní komunikaci poskytnutím duální připojení pomocí protokolu HTTP, jeden pro každý směr.</span><span class="sxs-lookup"><span data-stu-id="cb330-124">The `wsDualHttpBinding` element supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span>  
  
 <span data-ttu-id="cb330-125">Na straně klienta je nutné nakonfigurovat adresu serveru můžete použít pro připojení ke klientovi, jak je znázorněno v následující ukázková konfigurace.</span><span class="sxs-lookup"><span data-stu-id="cb330-125">On the client, you must configure an address that the server can use to connect to the client, as shown in the following sample configuration.</span></span>  

> [!NOTE]
>  <span data-ttu-id="cb330-126">Throw bez duplexní klienty, kteří neumožňuje ověřovat, obvykle pomocí zabezpečené konverzace <xref:System.ServiceModel.Security.MessageSecurityException>.</span><span class="sxs-lookup"><span data-stu-id="cb330-126">Non-duplex clients that fail to authenticate using a secure conversation typically throw a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="cb330-127">Ale pokud se ověření nezdaří duplexní klienta, který využívá zabezpečené konverzace, klient přijme <xref:System.TimeoutException> místo.</span><span class="sxs-lookup"><span data-stu-id="cb330-127">However, if a duplex client that uses a secure conversation fails to authenticate, the client receives a <xref:System.TimeoutException> instead.</span></span>  
  
 <span data-ttu-id="cb330-128">Pokud vytvoříte klienta a služby pomocí `WSHttpBinding` elementu a nezahrnují koncový bod klienta zpětné volání, zobrazí se následující chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="cb330-128">If you create a client/service using the `WSHttpBinding` element and you do not include the client callback endpoint, you will receive the following error.</span></span>  
  
```  
HTTP could not register URL  
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.  
```  
  
 <span data-ttu-id="cb330-129">Následující ukázkový kód ukazuje, jak zadat klienta adresy koncového bodu prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="cb330-129">The following sample code shows how to specify the client endpoint address programmatically.</span></span>
  
```csharp  
WSDualHttpBinding binding = new WSDualHttpBinding();  
EndpointAddress endptadr = new EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server");  
binding.ClientBaseAddress = new Uri("http://localhost:8000/DuplexTestUsingCode/Client/");  
```  
```vb
Dim binding As New WSDualHttpBinding()
Dim endptadr As New EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server")
binding.ClientBaseAddress = New Uri("http://localhost:8000/DuplexTestUsingCode/Client/")  
```

 <span data-ttu-id="cb330-130">Následující ukázkový kód ukazuje, jak zadat klienta adresy koncového bodu v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="cb330-130">The following sample code shows how to specify the client endpoint address in configuration.</span></span>  
  
```xml  
<client>  
    <endpoint name ="ServerEndpoint"   
          address="http://localhost:12000/DuplexTestUsingConfig/Server"  
          bindingConfiguration="WSDualHttpBinding_IDuplexTest"   
            binding="wsDualHttpBinding"  
           contract="IDuplexTest" />  
</client>  
<bindings>  
    <wsDualHttpBinding>  
        <binding name="WSDualHttpBinding_IDuplexTest"    
          clientBaseAddress="http://localhost:8000/myClient/" >  
            <security mode="None"/>  
         </binding>  
    </wsDualHttpBinding>  
</bindings>  
```  
  
> [!WARNING]
>  <span data-ttu-id="cb330-131">Když služba nebo klient ukončí její kanál duplexní modelu nerozpozná automaticky.</span><span class="sxs-lookup"><span data-stu-id="cb330-131">The duplex model does not automatically detect when a service or client closes its channel.</span></span> <span data-ttu-id="cb330-132">Takže pokud klient neočekávaně ukončí, ve výchozím nastavení službu nedostanou nebo pokud klient neočekávaně skončí, nebudete nijak upozorněni služby.</span><span class="sxs-lookup"><span data-stu-id="cb330-132">So if a client unexpectedly terminates, by default the service will not be notified, or if a client unexpectedly terminates, the service will not be notified.</span></span> <span data-ttu-id="cb330-133">Služby a klienti můžou implementovat vlastní protokol na sebe navzájem upozornit, pokud se tedy rozhodne.</span><span class="sxs-lookup"><span data-stu-id="cb330-133">Clients and services can implement their own protocol to notify each other if they so choose.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb330-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb330-134">See also</span></span>

- [<span data-ttu-id="cb330-135">Duplex</span><span class="sxs-lookup"><span data-stu-id="cb330-135">Duplex</span></span>](../../../../docs/framework/wcf/samples/duplex.md)
- [<span data-ttu-id="cb330-136">Nastavení běhového chování klienta</span><span class="sxs-lookup"><span data-stu-id="cb330-136">Specifying Client Run-Time Behavior</span></span>](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="cb330-137">Postupy: Vytvoření postupu kanálu a jeho použití k vytvoření a správě kanálů</span><span class="sxs-lookup"><span data-stu-id="cb330-137">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
