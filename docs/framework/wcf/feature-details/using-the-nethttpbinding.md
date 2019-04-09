---
title: Používání vazeb NetHttpBinding
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: 5090cfdfeb068acda1e1092e408f3cd747c574c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121014"
---
# <a name="using-the-nethttpbinding"></a><span data-ttu-id="ea02b-102">Používání vazeb NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="ea02b-102">Using the NetHttpBinding</span></span>
<xref:System.ServiceModel.NetHttpBinding> <span data-ttu-id="ea02b-103">Vazba určená pro použití protokolu HTTP nebo objektu websocket na straně služby a používá binární kódování ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="ea02b-103">is a binding designed for consuming HTTP or WebSocket services and uses binary encoding by default.</span></span> <xref:System.ServiceModel.NetHttpBinding> <span data-ttu-id="ea02b-104">zjistí, jestli se používá s kontraktů požadavek odpověď nebo duplexní kontrakt a změnit její chování tak, aby odpovídaly – použije HTTP pro kontraktů požadavek odpověď a protokoly Websocket pro duplexní kontrakty.</span><span class="sxs-lookup"><span data-stu-id="ea02b-104">will detect whether it is used with a request-reply contract or duplex contract and change its behavior to match - it will use HTTP for request-reply contracts and WebSockets for duplex contracts.</span></span> <span data-ttu-id="ea02b-105">Toto chování lze přepsat pomocí <xref:System.ServiceModel.Channels.WebSocketTransportUsage> nastavení:</span><span class="sxs-lookup"><span data-stu-id="ea02b-105">This behavior can be overridden using the <xref:System.ServiceModel.Channels.WebSocketTransportUsage> setting:</span></span>  
  
1. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always> <span data-ttu-id="ea02b-106">– To přinutí WebSockets se použije i pro kontraktů požadavek odpověď.</span><span class="sxs-lookup"><span data-stu-id="ea02b-106">- This forces WebSockets to be used even for request-reply contracts.</span></span>  
  
2. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never> <span data-ttu-id="ea02b-107">– To brání použití objekty Websocket.</span><span class="sxs-lookup"><span data-stu-id="ea02b-107">- This prevents WebSockets from being used.</span></span> <span data-ttu-id="ea02b-108">Pokus o použití duplexního kontraktu s tímto nastavením bude mít za následek výjimku.</span><span class="sxs-lookup"><span data-stu-id="ea02b-108">Attempting to use a duplex contract with this setting will result in an exception.</span></span>  
  
3. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex> <span data-ttu-id="ea02b-109">– Toto je výchozí hodnota a chová, jak je popsáno výše.</span><span class="sxs-lookup"><span data-stu-id="ea02b-109">- This is the default value and behaves as described above.</span></span>  
  
 <xref:System.ServiceModel.NetHttpBinding> <span data-ttu-id="ea02b-110">podporuje spolehlivé relace v režimu HTTP a WebSocket režimu.</span><span class="sxs-lookup"><span data-stu-id="ea02b-110">supports reliable sessions in both HTTP mode and WebSocket mode.</span></span> <span data-ttu-id="ea02b-111">V objektu websocket na straně relace režimu jsou poskytovány přenos.</span><span class="sxs-lookup"><span data-stu-id="ea02b-111">In WebSocket mode sessions are provided by the transport.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="ea02b-112">Při použití <xref:System.ServiceModel.NetHttpBinding> a režim přenosu vazby je nastavena na TransferMode.Streamed, velké datové proudy může způsobit zablokování a vypršení časového limitu bude volání.</span><span class="sxs-lookup"><span data-stu-id="ea02b-112">When using the <xref:System.ServiceModel.NetHttpBinding> and the binding’s TransferMode is set to TransferMode.Streamed, large streams may cause a deadlock and the call will timeout.</span></span> <span data-ttu-id="ea02b-113">Chcete vyřešit tento problém odesílat menší zprávy nebo použít třídy TransferMode.Buffered.</span><span class="sxs-lookup"><span data-stu-id="ea02b-113">To work around this issue send smaller messages or use TransferMode.Buffered.</span></span>  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a><span data-ttu-id="ea02b-114">Konfigurace služby k použití NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="ea02b-114">Configuring a Service to use NetHttpBinding</span></span>  
 <span data-ttu-id="ea02b-115"><xref:System.ServiceModel.NetHttpBinding> Může být nakonfigurované stejně jako jakákoli jiná vazba.</span><span class="sxs-lookup"><span data-stu-id="ea02b-115">The <xref:System.ServiceModel.NetHttpBinding> can be configured the same as any other binding.</span></span> <span data-ttu-id="ea02b-116">Následující konfigurace fragment kódu ukazuje, jak se konfigurace služby WCF s <xref:System.ServiceModel.NetHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="ea02b-116">The following configuration snippet illustrates how to configure a WCF service with <xref:System.ServiceModel.NetHttpBinding>.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="WcfService1.Service1">  
        <endpoint address=""  
                  binding="netHttpBinding"  
                  contract="WcfService1.IService1"/>  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
    <bindings>  
      <netHttpBinding>  
        <binding name="My_NetHttpBindingConfig">  
          <webSocketSettings transportUsage="WhenDuplex"/>  
        </binding>  
      </netHttpBinding>  
    </bindings>  
    ...
  </system.serviceModel>  
```  
  
 <span data-ttu-id="ea02b-117">Následující fragment kódu ukazuje, jak přidat <xref:System.ServiceModel.NetHttpBinding> v kódu.</span><span class="sxs-lookup"><span data-stu-id="ea02b-117">The following code snippet shows how to add the <xref:System.ServiceModel.NetHttpBinding> in code.</span></span>  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);   
        }  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea02b-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea02b-118">See also</span></span>

- [<span data-ttu-id="ea02b-119">Konfigurace vazeb pro služby</span><span class="sxs-lookup"><span data-stu-id="ea02b-119">Configuring Bindings for Services</span></span>](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="ea02b-120">Vazby</span><span class="sxs-lookup"><span data-stu-id="ea02b-120">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)
- [<span data-ttu-id="ea02b-121">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="ea02b-121">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
- [<span data-ttu-id="ea02b-122">Duplexní služby</span><span class="sxs-lookup"><span data-stu-id="ea02b-122">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
