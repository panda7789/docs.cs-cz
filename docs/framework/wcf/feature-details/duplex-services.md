---
title: Duplexní služby
description: Naučte se, jak vytvořit duplexní kontrakt služby ve službě WCF, který umožňuje oběma koncovým bodům posílat zprávy mezi sebou prostřednictvím kanálu vytvořeného klientem.
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: a43bb63a0ccf1a34b79dce755c19f7ed4cb6c16c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247348"
---
# <a name="duplex-services"></a><span data-ttu-id="df020-103">Duplexní služby</span><span class="sxs-lookup"><span data-stu-id="df020-103">Duplex Services</span></span>

<span data-ttu-id="df020-104">Duplexní kontrakt služby je vzor výměny zpráv, ve kterém oba koncové body mohou odesílat zprávy jiným způsobem nezávisle.</span><span class="sxs-lookup"><span data-stu-id="df020-104">A duplex service contract is a message exchange pattern in which both endpoints can send messages to the other independently.</span></span> <span data-ttu-id="df020-105">Duplexní služba, proto může odesílat zprávy zpátky do koncového bodu klienta a poskytovat tak chování podobné událostem.</span><span class="sxs-lookup"><span data-stu-id="df020-105">A duplex service, therefore, can send messages back to the client endpoint, providing event-like behavior.</span></span> <span data-ttu-id="df020-106">Duplexní komunikace probíhá při připojení klienta ke službě a poskytování služby s kanálem, ve kterém služba může odesílat zprávy zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="df020-106">Duplex communication occurs when a client connects to a service and provides the service with a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="df020-107">Všimněte si, že chování funkcí duplexní služby funguje pouze v rámci relace.</span><span class="sxs-lookup"><span data-stu-id="df020-107">Note that the event-like behavior of duplex services only works within a session.</span></span>

<span data-ttu-id="df020-108">Pro vytvoření duplexního kontraktu vytvoříte dvojici rozhraní.</span><span class="sxs-lookup"><span data-stu-id="df020-108">To create a duplex contract you create a pair of interfaces.</span></span> <span data-ttu-id="df020-109">První je rozhraní kontraktu služby, které popisuje operace, které může klient vyvolat.</span><span class="sxs-lookup"><span data-stu-id="df020-109">The first is the service contract interface that describes the operations that a client can invoke.</span></span> <span data-ttu-id="df020-110">Tento kontrakt služby musí ve vlastnosti zadat *kontrakt zpětného volání* <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="df020-110">That service contract must specify a *callback contract* in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="df020-111">Kontrakt zpětného volání je rozhraní, které definuje operace, které může služba volat na koncový bod klienta.</span><span class="sxs-lookup"><span data-stu-id="df020-111">The callback contract is the interface that defines the operations that the service can call on the client endpoint.</span></span> <span data-ttu-id="df020-112">Duplexní kontrakt nevyžaduje relaci, i když se systémem zajištěné duplexní vazby využívají.</span><span class="sxs-lookup"><span data-stu-id="df020-112">A duplex contract does not require a session, although the system-provided duplex bindings make use of them.</span></span>

<span data-ttu-id="df020-113">Následuje příklad duplexního kontraktu.</span><span class="sxs-lookup"><span data-stu-id="df020-113">The following is an example of a duplex contract.</span></span>

[!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
[!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]

<span data-ttu-id="df020-114">`CalculatorService`Třída implementuje primární `ICalculatorDuplex` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="df020-114">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="df020-115">Služba používá <xref:System.ServiceModel.InstanceContextMode.PerSession> režim instance k uchování výsledku pro každou relaci.</span><span class="sxs-lookup"><span data-stu-id="df020-115">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="df020-116">Soukromá vlastnost s názvem `Callback` přistupuje k kanálu zpětného volání klientovi.</span><span class="sxs-lookup"><span data-stu-id="df020-116">A private property named `Callback` accesses the callback channel to the client.</span></span> <span data-ttu-id="df020-117">Služba používá zpětné volání pro posílání zpráv zpátky do klienta prostřednictvím rozhraní zpětného volání, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="df020-117">The service uses the callback for sending messages back to the client through the callback interface, as shown in the following sample code.</span></span>

[!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
[!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]

<span data-ttu-id="df020-118">Klient musí poskytnout třídu, která implementuje rozhraní zpětného volání pro oboustrannou smlouvu pro příjem zpráv ze služby.</span><span class="sxs-lookup"><span data-stu-id="df020-118">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="df020-119">Následující vzorový kód ukazuje `CallbackHandler` třídu, která implementuje `ICalculatorDuplexCallback` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="df020-119">The following sample code shows a `CallbackHandler` class that implements the `ICalculatorDuplexCallback` interface.</span></span>

[!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
[!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]

<span data-ttu-id="df020-120">Klient služby WCF, který je generován pro duplexní smlouvu, vyžaduje, <xref:System.ServiceModel.InstanceContext> aby byla při konstrukci poskytnuta třída.</span><span class="sxs-lookup"><span data-stu-id="df020-120">The WCF client that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> class to be provided upon construction.</span></span> <span data-ttu-id="df020-121">Tato <xref:System.ServiceModel.InstanceContext> Třída se používá jako web pro objekt, který implementuje rozhraní zpětného volání a zpracovává zprávy odesílané zpět ze služby.</span><span class="sxs-lookup"><span data-stu-id="df020-121">This <xref:System.ServiceModel.InstanceContext> class is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="df020-122"><xref:System.ServiceModel.InstanceContext>Třída je vytvořena s instancí `CallbackHandler` třídy.</span><span class="sxs-lookup"><span data-stu-id="df020-122">An <xref:System.ServiceModel.InstanceContext> class is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="df020-123">Tento objekt zpracovává zprávy odesílané ze služby klientovi na rozhraní zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="df020-123">This object handles messages sent from the service to the client on the callback interface.</span></span>

[!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
[!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]

<span data-ttu-id="df020-124">Aby bylo možné vytvořit vazbu, která podporuje komunikaci relace i duplexní komunikaci, musí být nastavena konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="df020-124">The configuration for the service must be set up to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="df020-125">`wsDualHttpBinding`Element podporuje komunikaci relací a umožňuje duplexní komunikaci tím, že poskytuje duální připojení HTTP, jedno pro každý směr.</span><span class="sxs-lookup"><span data-stu-id="df020-125">The `wsDualHttpBinding` element supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span>

<span data-ttu-id="df020-126">Na straně klienta je nutné nakonfigurovat adresu, kterou může server použít pro připojení ke klientovi, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="df020-126">On the client, you must configure an address that the server can use to connect to the client, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="df020-127">Neduplexní klienti, kteří se nedaří ověřit pomocí zabezpečené konverzace, obvykle vyvolají <xref:System.ServiceModel.Security.MessageSecurityException> .</span><span class="sxs-lookup"><span data-stu-id="df020-127">Non-duplex clients that fail to authenticate using a secure conversation typically throw a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="df020-128">Pokud však dojde k ověření duplexního klienta, který používá zabezpečenou konverzaci, klient obdrží <xref:System.TimeoutException> místo toho.</span><span class="sxs-lookup"><span data-stu-id="df020-128">However, if a duplex client that uses a secure conversation fails to authenticate, the client receives a <xref:System.TimeoutException> instead.</span></span>

<span data-ttu-id="df020-129">Pokud vytvoříte klienta nebo službu pomocí `WSHttpBinding` elementu a nezahrnete koncový bod zpětného volání klienta, zobrazí se následující chyba.</span><span class="sxs-lookup"><span data-stu-id="df020-129">If you create a client/service using the `WSHttpBinding` element and you do not include the client callback endpoint, you will receive the following error.</span></span>

```console
HTTP could not register URL
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.
```

<span data-ttu-id="df020-130">Následující vzorový kód ukazuje, jak zadat adresu koncového bodu klienta programově.</span><span class="sxs-lookup"><span data-stu-id="df020-130">The following sample code shows how to specify the client endpoint address programmatically.</span></span>

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

<span data-ttu-id="df020-131">Následující vzorový kód ukazuje, jak zadat adresu koncového bodu klienta v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="df020-131">The following sample code shows how to specify the client endpoint address in configuration.</span></span>

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
> <span data-ttu-id="df020-132">Duplexní model se automaticky nerozpozná, když služba nebo klient ukončí svůj kanál.</span><span class="sxs-lookup"><span data-stu-id="df020-132">The duplex model doesn't automatically detect when a service or client closes its channel.</span></span> <span data-ttu-id="df020-133">Takže pokud se klient neočekávaně ukončí, služba se ve výchozím nastavení nebude informovat nebo pokud se služba neočekávaně ukončí, klient nebude upozorněn.</span><span class="sxs-lookup"><span data-stu-id="df020-133">So if a client unexpectedly terminates, by default the service will not be notified, or if a service unexpectedly terminates, the client will not be notified.</span></span> <span data-ttu-id="df020-134">Pokud používáte službu, která je odpojena, <xref:System.ServiceModel.CommunicationException> vyvolá se výjimka.</span><span class="sxs-lookup"><span data-stu-id="df020-134">If you use a service that is disconnected, the <xref:System.ServiceModel.CommunicationException> exception is raised.</span></span> <span data-ttu-id="df020-135">Klienti a služby můžou implementovat svůj vlastní protokol, aby si je vzájemně oznámili.</span><span class="sxs-lookup"><span data-stu-id="df020-135">Clients and services can implement their own protocol to notify each other if they so choose.</span></span> <span data-ttu-id="df020-136">Další informace o zpracování chyb naleznete v tématu [zpracování chyb WCF](../wcf-error-handling.md).</span><span class="sxs-lookup"><span data-stu-id="df020-136">For more information on error handling, see [WCF Error Handling](../wcf-error-handling.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="df020-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="df020-137">See also</span></span>

- [<span data-ttu-id="df020-138">Duplex</span><span class="sxs-lookup"><span data-stu-id="df020-138">Duplex</span></span>](../samples/duplex.md)
- [<span data-ttu-id="df020-139">Nastavení chování klienta za běhu</span><span class="sxs-lookup"><span data-stu-id="df020-139">Specifying Client Run-Time Behavior</span></span>](../specifying-client-run-time-behavior.md)
- [<span data-ttu-id="df020-140">Postupy: Vytvoření objektu pro vytváření kanálů a jeho použití k vytvoření a správě kanálů</span><span class="sxs-lookup"><span data-stu-id="df020-140">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>](how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
