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
# <a name="using-the-nethttpbinding"></a>Používání vazeb NetHttpBinding
<xref:System.ServiceModel.NetHttpBinding>je vazba určená pro využití služeb HTTP nebo WebSocket a ve výchozím nastavení používá binární kódování. <xref:System.ServiceModel.NetHttpBinding>zjistí, zda se používá se smlouvou požadavek odpověď nebo duplexní smlouvy a změnit jeho chování tak, aby odpovídalo – bude používat HTTP pro kontrakty požadavek odpověď a WebSockets pro duplexní smlouvy. Toto chování lze přepsat <xref:System.ServiceModel.Channels.WebSocketTransportUsage> pomocí nastavení:  
  
1. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always>- To vynutí WebSockets, které mají být použity i pro smlouvy požadavek odpověď.  
  
2. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never>- Tím zabráníte websockets z použití. Pokus o použití duplexní smlouvy s tímto nastavením bude mít za následek výjimku.  
  
3. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex>- Toto je výchozí hodnota a chová se, jak je popsáno výše.  
  
 <xref:System.ServiceModel.NetHttpBinding>podporuje spolehlivé relace v režimu HTTP i websocket. V režimu WebSocket relace jsou poskytovány přenosem.  
  
> [!WARNING]
> Při použití <xref:System.ServiceModel.NetHttpBinding> a vazby TransferMode je nastavena na TransferMode.Streamed, velké datové proudy může způsobit zablokování a volání bude časový režim. Chcete-li tento problém vyřešit, odešlete menší zprávy nebo použijte TransferMode.Buffered.  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a>Konfigurace služby pro použití nethttpbinding  
 Lze <xref:System.ServiceModel.NetHttpBinding> nakonfigurovat stejně jako všechny ostatní vazby. Následující fragment konfigurace ukazuje, jak nakonfigurovat službu <xref:System.ServiceModel.NetHttpBinding>WCF s .  
  
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
  
 Následující fragment kódu ukazuje, jak přidat <xref:System.ServiceModel.NetHttpBinding> v kódu.  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);
        }  
```  
  
## <a name="see-also"></a>Viz také

- [Konfigurace vazeb pro služby](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [Vazby](../../../../docs/framework/wcf/feature-details/bindings.md)
- [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)
- [Duplexní služby](../../../../docs/framework/wcf/feature-details/duplex-services.md)
