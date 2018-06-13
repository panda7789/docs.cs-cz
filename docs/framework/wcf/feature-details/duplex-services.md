---
title: Duplexní služby
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: da92b8f2d1223f582677a93a8ff6fd697512d297
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
ms.locfileid: "34037360"
---
# <a name="duplex-services"></a><span data-ttu-id="4dc4c-102">Duplexní služby</span><span class="sxs-lookup"><span data-stu-id="4dc4c-102">Duplex Services</span></span>
<span data-ttu-id="4dc4c-103">Kontrakt duplexní služby je vzorce výměny zpráv, ve kterém oba koncové body mohou zasílat zprávy do dalších nezávisle.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-103">A duplex service contract is a message exchange pattern in which both endpoints can send messages to the other independently.</span></span> <span data-ttu-id="4dc4c-104">Duplexní služby, proto mohou zasílat zprávy zpět do koncového bodu klienta, poskytuje podobné události chování.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-104">A duplex service, therefore, can send messages back to the client endpoint, providing event-like behavior.</span></span> <span data-ttu-id="4dc4c-105">Duplexní komunikace nastane, když se klient připojuje ke službě a poskytuje službu s kanálem, na kterém služba mohou zasílat zprávy zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-105">Duplex communication occurs when a client connects to a service and provides the service with a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="4dc4c-106">Všimněte si, že událost jako chování duplexní služby funguje pouze v rámci relace.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-106">Note that the event-like behavior of duplex services only works within a session.</span></span>  
  
 <span data-ttu-id="4dc4c-107">K vytvoření duplexního kontraktu vytvořit pár rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-107">To create a duplex contract you create a pair of interfaces.</span></span> <span data-ttu-id="4dc4c-108">První je rozhraní kontraktu služby, které popisuje operace, které můžete vyvolat klienta.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-108">The first is the service contract interface that describes the operations that a client can invoke.</span></span> <span data-ttu-id="4dc4c-109">Musíte zadat Tento kontrakt služby *kontrakt zpětného volání* v <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-109">That service contract must specify a *callback contract* in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="4dc4c-110">Kontrakt zpětného volání je rozhraní, které definuje operace, které služba můžete volat na koncovém bodu klienta.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-110">The callback contract is the interface that defines the operations that the service can call on the client endpoint.</span></span> <span data-ttu-id="4dc4c-111">Duplexního kontraktu nevyžaduje relace, i když zkontrolujte duplexní vazby poskytované systémem použijte z nich.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-111">A duplex contract does not require a session, although the system-provided duplex bindings make use of them.</span></span>  
  
 <span data-ttu-id="4dc4c-112">Následuje příklad duplexního kontraktu.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-112">The following is an example of a duplex contract.</span></span>  
  
 [!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
 [!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]  
  
 <span data-ttu-id="4dc4c-113">`CalculatorService` Třída implementuje primární `ICalculatorDuplex` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-113">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="4dc4c-114">Služba používá <xref:System.ServiceModel.InstanceContextMode.PerSession> instance režimu zachování výsledek pro každou relaci.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-114">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="4dc4c-115">Soukromá vlastnost s názvem `Callback` přistupuje k kanál zpětného volání pro klienta.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-115">A private property named `Callback` accesses the callback channel to the client.</span></span> <span data-ttu-id="4dc4c-116">Služba používá zpětné volání pro odesílání zpráv zpět do klienta přes rozhraní zpětné volání, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-116">The service uses the callback for sending messages back to the client through the callback interface, as shown in the following sample code.</span></span>  
  
 [!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
 [!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]  
  
 <span data-ttu-id="4dc4c-117">Klient musí poskytnout třídu, která implementuje rozhraní zpětné volání duplexního kontraktu pro příjem zpráv ze služby.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-117">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="4dc4c-118">Následující ukázkový kód ukazuje `CallbackHandler` třídu, která implementuje `ICalculatorDuplexCallback` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-118">The following sample code shows a `CallbackHandler` class that implements the `ICalculatorDuplexCallback` interface.</span></span>  
  
 [!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
 [!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]  
  
 <span data-ttu-id="4dc4c-119">Klienta WCF, který se vygeneruje pro vyžaduje duplexního kontraktu <xref:System.ServiceModel.InstanceContext> třídy je třeba zadat při vytváření.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-119">The WCF client that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> class to be provided upon construction.</span></span> <span data-ttu-id="4dc4c-120">To <xref:System.ServiceModel.InstanceContext> třída se používá jako lokality pro objekt, který implementuje rozhraní zpětného volání a zpracovává zprávy, které se odesílají zpět ze služby.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-120">This <xref:System.ServiceModel.InstanceContext> class is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="4dc4c-121"><xref:System.ServiceModel.InstanceContext> Třída je vytvořený pomocí instance `CallbackHandler` třídy.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-121">An <xref:System.ServiceModel.InstanceContext> class is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="4dc4c-122">Tento objekt zpracovává zprávy odeslané ze služby pro klienta v rozhraní zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-122">This object handles messages sent from the service to the client on the callback interface.</span></span>  
  
 [!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
 [!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]  
  
 <span data-ttu-id="4dc4c-123">Konfigurace služby musí ho nastavit má být poskytnuta vazba, která podporuje komunikaci relace a duplexní komunikace.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-123">The configuration for the service must be set up to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="4dc4c-124">`wsDualHttpBinding` Element podporuje komunikaci relace a umožňuje duplexní komunikace tím, že poskytuje duální připojení protokolu HTTP, jeden pro všechny směry.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-124">The `wsDualHttpBinding` element supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span>  
  
 <span data-ttu-id="4dc4c-125">Na klientovi je nutné nakonfigurovat adresu, která server můžete použít pro připojení ke klientovi, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-125">On the client, you must configure an address that the server can use to connect to the client, as shown in the following sample configuration.</span></span>  
  
  
  
> [!NOTE]
>  <span data-ttu-id="4dc4c-126">Duplexní bez klienty, kteří nepodaří ověřit pomocí zabezpečenou konverzaci obvykle throw <xref:System.ServiceModel.Security.MessageSecurityException>.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-126">Non-duplex clients that fail to authenticate using a secure conversation typically throw a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="4dc4c-127">Ale pokud se ověření nezdaří duplexní klienta, který používá zabezpečené konverzaci, klient přijme <xref:System.TimeoutException> místo.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-127">However, if a duplex client that uses a secure conversation fails to authenticate, the client receives a <xref:System.TimeoutException> instead.</span></span>  
  
 <span data-ttu-id="4dc4c-128">Pokud vytvoříte klienta nebo službu pomocí `WSHttpBinding` elementu a nezahrnovat koncový bod zpětného volání klienta, zobrazí se následující chyba.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-128">If you create a client/service using the `WSHttpBinding` element and you do not include the client callback endpoint, you will receive the following error.</span></span>  
  
```  
HTTP could not register URL  
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.  
```  
  
 <span data-ttu-id="4dc4c-129">Následující vzorový kód ukazuje, jak zadat klienta adresa koncového bodu prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-129">The following sample code shows how to specify the client endpoint address programmatically.</span></span>
  
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

 <span data-ttu-id="4dc4c-130">Následující vzorový kód ukazuje, jak zadat klienta adresa koncového bodu v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-130">The following sample code shows how to specify the client endpoint address in configuration.</span></span>  
  
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
>  <span data-ttu-id="4dc4c-131">Duplexní modelu automaticky nerozpozná služba nebo klienta zavře jeho kanálu.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-131">The duplex model does not automatically detect when a service or client closes its channel.</span></span> <span data-ttu-id="4dc4c-132">Takže pokud klient neočekávaně ukončí, ve výchozím nastavení služba nebudete nijak upozorněni, nebo pokud neočekávaně ukončí klient služby nebudete nijak upozorněni.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-132">So if a client unexpectedly terminates, by default the service will not be notified, or if a client unexpectedly terminates, the service will not be notified.</span></span> <span data-ttu-id="4dc4c-133">Služby a klienti můžete implementovat vlastní protokol navzájem upozorní, pokud si vyberou.</span><span class="sxs-lookup"><span data-stu-id="4dc4c-133">Clients and services can implement their own protocol to notify each other if they so choose.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dc4c-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="4dc4c-134">See Also</span></span>  
 [<span data-ttu-id="4dc4c-135">Duplex</span><span class="sxs-lookup"><span data-stu-id="4dc4c-135">Duplex</span></span>](../../../../docs/framework/wcf/samples/duplex.md)  
 [<span data-ttu-id="4dc4c-136">Nastavení chování klienta za běhu</span><span class="sxs-lookup"><span data-stu-id="4dc4c-136">Specifying Client Run-Time Behavior</span></span>](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)  
 [<span data-ttu-id="4dc4c-137">Postupy: Vytvoření objektu pro vytváření kanálů a jeho použití k vytvoření a správě kanálů</span><span class="sxs-lookup"><span data-stu-id="4dc4c-137">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
