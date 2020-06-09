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
# <a name="using-the-nethttpbinding"></a>Používání vazeb NetHttpBinding
<xref:System.ServiceModel.NetHttpBinding>je vazba určená pro využívání služeb HTTP nebo WebSocket a ve výchozím nastavení používá binární kódování. <xref:System.ServiceModel.NetHttpBinding>zjistí, jestli se používá se smlouvou požadavek-odpověď nebo oboustrannou smlouvou a že se má změnit chování, aby odpovídalo. bude používat protokol HTTP pro kontrakty požadavek-odpověď a objekty WebSocket pro duplexní kontrakty. Toto chování lze přepsat pomocí <xref:System.ServiceModel.Channels.WebSocketTransportUsage> nastavení:  
  
1. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always>– To vynutí, aby se WebSockets používaly i pro kontrakty požadavek-odpověď.  
  
2. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never>– To zabraňuje použití WebSockets. Pokus o použití duplexního kontraktu s tímto nastavením bude mít za následek výjimku.  
  
3. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex>– Toto je výchozí hodnota a chová se, jak je popsáno výše.  
  
 <xref:System.ServiceModel.NetHttpBinding>podporuje spolehlivé relace v režimu HTTP i v režimu WebSocket. V relacích režimu WebSocket je přenos zajištěný přenosem.  
  
> [!WARNING]
> Při použití ovládacího <xref:System.ServiceModel.NetHttpBinding> prvku a třídy TransferMode vazby je nastavena na třídy TransferMode. streamovaná, velké datové proudy mohou způsobit zablokování a volání bude mít časový limit. Pokud chcete tento problém obejít, pošlete menší zprávy nebo použijte třídy TransferMode. Buffered.  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a>Konfigurace služby pro použití NetHttpBinding  
 <xref:System.ServiceModel.NetHttpBinding>Lze nakonfigurovat stejné jako jakékoli jiné vazby. Následující fragment kódu ukazuje, jak nakonfigurovat službu WCF pomocí <xref:System.ServiceModel.NetHttpBinding> .  
  
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
  
 Následující fragment kódu ukazuje, jak přidat do <xref:System.ServiceModel.NetHttpBinding> kódu.  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);
        }  
```  
  
## <a name="see-also"></a>Viz také

- [Konfigurace vazeb pro služby](../configuring-bindings-for-wcf-services.md)
- [Vazby](bindings.md)
- [Vazby poskytované systémem](../system-provided-bindings.md)
- [Duplexní služby](duplex-services.md)
