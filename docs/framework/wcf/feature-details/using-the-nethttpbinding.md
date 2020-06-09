---
title: Používání vazeb NetHttpBinding
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: ac6fc658731d032051f2dfd4058397f9b9a55828
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585633"
---
# <a name="using-the-nethttpbinding"></a><span data-ttu-id="76955-102">Používání vazeb NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="76955-102">Using the NetHttpBinding</span></span>
<span data-ttu-id="76955-103"><xref:System.ServiceModel.NetHttpBinding>je vazba určená pro využívání služeb HTTP nebo WebSocket a ve výchozím nastavení používá binární kódování.</span><span class="sxs-lookup"><span data-stu-id="76955-103"><xref:System.ServiceModel.NetHttpBinding> is a binding designed for consuming HTTP or WebSocket services and uses binary encoding by default.</span></span> <span data-ttu-id="76955-104"><xref:System.ServiceModel.NetHttpBinding>zjistí, jestli se používá se smlouvou požadavek-odpověď nebo oboustrannou smlouvou a že se má změnit chování, aby odpovídalo. bude používat protokol HTTP pro kontrakty požadavek-odpověď a objekty WebSocket pro duplexní kontrakty.</span><span class="sxs-lookup"><span data-stu-id="76955-104"><xref:System.ServiceModel.NetHttpBinding> will detect whether it is used with a request-reply contract or duplex contract and change its behavior to match - it will use HTTP for request-reply contracts and WebSockets for duplex contracts.</span></span> <span data-ttu-id="76955-105">Toto chování lze přepsat pomocí <xref:System.ServiceModel.Channels.WebSocketTransportUsage> nastavení:</span><span class="sxs-lookup"><span data-stu-id="76955-105">This behavior can be overridden using the <xref:System.ServiceModel.Channels.WebSocketTransportUsage> setting:</span></span>  
  
1. <span data-ttu-id="76955-106"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always>– To vynutí, aby se WebSockets používaly i pro kontrakty požadavek-odpověď.</span><span class="sxs-lookup"><span data-stu-id="76955-106"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always> - This forces WebSockets to be used even for request-reply contracts.</span></span>  
  
2. <span data-ttu-id="76955-107"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never>– To zabraňuje použití WebSockets.</span><span class="sxs-lookup"><span data-stu-id="76955-107"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never> - This prevents WebSockets from being used.</span></span> <span data-ttu-id="76955-108">Pokus o použití duplexního kontraktu s tímto nastavením bude mít za následek výjimku.</span><span class="sxs-lookup"><span data-stu-id="76955-108">Attempting to use a duplex contract with this setting will result in an exception.</span></span>  
  
3. <span data-ttu-id="76955-109"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex>– Toto je výchozí hodnota a chová se, jak je popsáno výše.</span><span class="sxs-lookup"><span data-stu-id="76955-109"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex> - This is the default value and behaves as described above.</span></span>  
  
 <span data-ttu-id="76955-110"><xref:System.ServiceModel.NetHttpBinding>podporuje spolehlivé relace v režimu HTTP i v režimu WebSocket.</span><span class="sxs-lookup"><span data-stu-id="76955-110"><xref:System.ServiceModel.NetHttpBinding> supports reliable sessions in both HTTP mode and WebSocket mode.</span></span> <span data-ttu-id="76955-111">V relacích režimu WebSocket je přenos zajištěný přenosem.</span><span class="sxs-lookup"><span data-stu-id="76955-111">In WebSocket mode sessions are provided by the transport.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="76955-112">Při použití ovládacího <xref:System.ServiceModel.NetHttpBinding> prvku a třídy TransferMode vazby je nastavena na třídy TransferMode. streamovaná, velké datové proudy mohou způsobit zablokování a volání bude mít časový limit.</span><span class="sxs-lookup"><span data-stu-id="76955-112">When using the <xref:System.ServiceModel.NetHttpBinding> and the binding’s TransferMode is set to TransferMode.Streamed, large streams may cause a deadlock and the call will timeout.</span></span> <span data-ttu-id="76955-113">Pokud chcete tento problém obejít, pošlete menší zprávy nebo použijte třídy TransferMode. Buffered.</span><span class="sxs-lookup"><span data-stu-id="76955-113">To work around this issue send smaller messages or use TransferMode.Buffered.</span></span>  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a><span data-ttu-id="76955-114">Konfigurace služby pro použití NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="76955-114">Configuring a Service to use NetHttpBinding</span></span>  
 <span data-ttu-id="76955-115"><xref:System.ServiceModel.NetHttpBinding>Lze nakonfigurovat stejné jako jakékoli jiné vazby.</span><span class="sxs-lookup"><span data-stu-id="76955-115">The <xref:System.ServiceModel.NetHttpBinding> can be configured the same as any other binding.</span></span> <span data-ttu-id="76955-116">Následující fragment kódu ukazuje, jak nakonfigurovat službu WCF pomocí <xref:System.ServiceModel.NetHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="76955-116">The following configuration snippet illustrates how to configure a WCF service with <xref:System.ServiceModel.NetHttpBinding>.</span></span>  
  
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
  
 <span data-ttu-id="76955-117">Následující fragment kódu ukazuje, jak přidat do <xref:System.ServiceModel.NetHttpBinding> kódu.</span><span class="sxs-lookup"><span data-stu-id="76955-117">The following code snippet shows how to add the <xref:System.ServiceModel.NetHttpBinding> in code.</span></span>  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);
        }  
```  
  
## <a name="see-also"></a><span data-ttu-id="76955-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="76955-118">See also</span></span>

- [<span data-ttu-id="76955-119">Konfigurace vazeb pro služby</span><span class="sxs-lookup"><span data-stu-id="76955-119">Configuring Bindings for Services</span></span>](../configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="76955-120">Vazby</span><span class="sxs-lookup"><span data-stu-id="76955-120">Bindings</span></span>](bindings.md)
- [<span data-ttu-id="76955-121">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="76955-121">System-Provided Bindings</span></span>](../system-provided-bindings.md)
- [<span data-ttu-id="76955-122">Duplexní služby</span><span class="sxs-lookup"><span data-stu-id="76955-122">Duplex Services</span></span>](duplex-services.md)
