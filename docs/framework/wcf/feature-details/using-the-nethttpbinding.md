---
title: Používání vazeb NetHttpBinding
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: 82222dbfa3f35ed00d0173f2bc927c32e9e98470
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184236"
---
# <a name="using-the-nethttpbinding"></a><span data-ttu-id="aa770-102">Používání vazeb NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="aa770-102">Using the NetHttpBinding</span></span>
<span data-ttu-id="aa770-103"><xref:System.ServiceModel.NetHttpBinding>je vazba určená pro využití služeb HTTP nebo WebSocket a ve výchozím nastavení používá binární kódování.</span><span class="sxs-lookup"><span data-stu-id="aa770-103"><xref:System.ServiceModel.NetHttpBinding> is a binding designed for consuming HTTP or WebSocket services and uses binary encoding by default.</span></span> <span data-ttu-id="aa770-104"><xref:System.ServiceModel.NetHttpBinding>zjistí, zda se používá se smlouvou požadavek odpověď nebo duplexní smlouvy a změnit jeho chování tak, aby odpovídalo – bude používat HTTP pro kontrakty požadavek odpověď a WebSockets pro duplexní smlouvy.</span><span class="sxs-lookup"><span data-stu-id="aa770-104"><xref:System.ServiceModel.NetHttpBinding> will detect whether it is used with a request-reply contract or duplex contract and change its behavior to match - it will use HTTP for request-reply contracts and WebSockets for duplex contracts.</span></span> <span data-ttu-id="aa770-105">Toto chování lze přepsat <xref:System.ServiceModel.Channels.WebSocketTransportUsage> pomocí nastavení:</span><span class="sxs-lookup"><span data-stu-id="aa770-105">This behavior can be overridden using the <xref:System.ServiceModel.Channels.WebSocketTransportUsage> setting:</span></span>  
  
1. <span data-ttu-id="aa770-106"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always>- To vynutí WebSockets, které mají být použity i pro smlouvy požadavek odpověď.</span><span class="sxs-lookup"><span data-stu-id="aa770-106"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always> - This forces WebSockets to be used even for request-reply contracts.</span></span>  
  
2. <span data-ttu-id="aa770-107"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never>- Tím zabráníte websockets z použití.</span><span class="sxs-lookup"><span data-stu-id="aa770-107"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never> - This prevents WebSockets from being used.</span></span> <span data-ttu-id="aa770-108">Pokus o použití duplexní smlouvy s tímto nastavením bude mít za následek výjimku.</span><span class="sxs-lookup"><span data-stu-id="aa770-108">Attempting to use a duplex contract with this setting will result in an exception.</span></span>  
  
3. <span data-ttu-id="aa770-109"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex>- Toto je výchozí hodnota a chová se, jak je popsáno výše.</span><span class="sxs-lookup"><span data-stu-id="aa770-109"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex> - This is the default value and behaves as described above.</span></span>  
  
 <span data-ttu-id="aa770-110"><xref:System.ServiceModel.NetHttpBinding>podporuje spolehlivé relace v režimu HTTP i websocket.</span><span class="sxs-lookup"><span data-stu-id="aa770-110"><xref:System.ServiceModel.NetHttpBinding> supports reliable sessions in both HTTP mode and WebSocket mode.</span></span> <span data-ttu-id="aa770-111">V režimu WebSocket relace jsou poskytovány přenosem.</span><span class="sxs-lookup"><span data-stu-id="aa770-111">In WebSocket mode sessions are provided by the transport.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="aa770-112">Při použití <xref:System.ServiceModel.NetHttpBinding> a vazby TransferMode je nastavena na TransferMode.Streamed, velké datové proudy může způsobit zablokování a volání bude časový režim.</span><span class="sxs-lookup"><span data-stu-id="aa770-112">When using the <xref:System.ServiceModel.NetHttpBinding> and the binding’s TransferMode is set to TransferMode.Streamed, large streams may cause a deadlock and the call will timeout.</span></span> <span data-ttu-id="aa770-113">Chcete-li tento problém vyřešit, odešlete menší zprávy nebo použijte TransferMode.Buffered.</span><span class="sxs-lookup"><span data-stu-id="aa770-113">To work around this issue send smaller messages or use TransferMode.Buffered.</span></span>  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a><span data-ttu-id="aa770-114">Konfigurace služby pro použití nethttpbinding</span><span class="sxs-lookup"><span data-stu-id="aa770-114">Configuring a Service to use NetHttpBinding</span></span>  
 <span data-ttu-id="aa770-115">Lze <xref:System.ServiceModel.NetHttpBinding> nakonfigurovat stejně jako všechny ostatní vazby.</span><span class="sxs-lookup"><span data-stu-id="aa770-115">The <xref:System.ServiceModel.NetHttpBinding> can be configured the same as any other binding.</span></span> <span data-ttu-id="aa770-116">Následující fragment konfigurace ukazuje, jak nakonfigurovat službu <xref:System.ServiceModel.NetHttpBinding>WCF s .</span><span class="sxs-lookup"><span data-stu-id="aa770-116">The following configuration snippet illustrates how to configure a WCF service with <xref:System.ServiceModel.NetHttpBinding>.</span></span>  
  
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
  
 <span data-ttu-id="aa770-117">Následující fragment kódu ukazuje, jak přidat <xref:System.ServiceModel.NetHttpBinding> v kódu.</span><span class="sxs-lookup"><span data-stu-id="aa770-117">The following code snippet shows how to add the <xref:System.ServiceModel.NetHttpBinding> in code.</span></span>  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);
        }  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa770-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa770-118">See also</span></span>

- [<span data-ttu-id="aa770-119">Konfigurace vazeb pro služby</span><span class="sxs-lookup"><span data-stu-id="aa770-119">Configuring Bindings for Services</span></span>](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="aa770-120">Vazby</span><span class="sxs-lookup"><span data-stu-id="aa770-120">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)
- [<span data-ttu-id="aa770-121">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="aa770-121">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
- [<span data-ttu-id="aa770-122">Duplexní služby</span><span class="sxs-lookup"><span data-stu-id="aa770-122">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
