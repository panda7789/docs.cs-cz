---
title: 'Postupy: Konfigurace používání sdílení portů ve službě WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: 0a3aca2bac546c9142137afc025133bc1154ff90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a>Postupy: Konfigurace používání sdílení portů ve službě WCF
Nejjednodušší způsob, jak používat port net.tcp:// sdílení v aplikaci Windows Communication Foundation (WCF) je vystavit služby pomocí <xref:System.ServiceModel.NetTcpBinding>.  
  
 Poskytuje tuto vazbu <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> vlastnost, která určuje, zda je povoleno sdílení portů net.tcp:// pro službu konfigurován s touto vazbou.  
  
 Následující postup ukazuje, jak používat <xref:System.ServiceModel.NetTcpBinding> třída otevřete koncový bod v identifikátoru URI (Uniform Resource) net.tcp://localhost/MyService, nejprve v kódu a pak pomocí konfigurace – elementy.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a>Chcete-li povolit portu net.tcp:// sdílení na NetTcpBinding v kódu  
  
1.  Vytvoření služby implementace kontraktu názvem `IMyService` a pojmenujte ji `MyService`,.  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2.  Vytvoření instance <xref:System.ServiceModel.NetTcpBinding> a nastavit <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> vlastnost `true`.  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3.  Vytvoření <xref:System.ServiceModel.ServiceHost> a přidejte do ní pro koncový bod služby `MyService` používající port povoleno sdílení <xref:System.ServiceModel.NetTcpBinding> a že sleduje na koncový bod adresy URI "net.tcp://localhost/MyService".  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    >  Tento příklad používá výchozí port TCP 808, protože adresa koncového bodu URI neurčuje jiné číslo portu. Protože sdílení portů je explicitně na přenos vazba povolena, tato služba může sdílet port 808 s jinými službami v jiné procesy. Pokud nebyly povoleno sdílení portů a port 808 se již používá jiná aplikace, tato služba by throw <xref:System.ServiceModel.AddressAlreadyInUseException> kdy byl otevřen.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a>Chcete-li povolit sdílení na NetTcpBinding v konfiguraci portu net.tcp://  
  
1.  Následující příklad ukazuje, jak povolit sdílení portů a přidat koncový bod služby, pomocí konfigurace – elementy.  
  
```xml  
<system.serviceModel>  
  <bindings>  
    <netTcpBinding name="portSharingBinding"   
                   portSharingEnabled="true" />  
  </bindings>  
  <services>  
    <service name="MyService">  
        <endpoint address="net.tcp://localhost/MyService"  
                  binding="netTcpBinding"  
                  contract="IMyService"  
                  bindingConfiguration="portSharingBinding" />  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Viz také  
 [Sdílení portů Net.TCP](http://msdn.microsoft.com/library/f13692ee-a179-4439-ae72-50db9534eded)  
 [Postupy: Povolení služby sdílení portů Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
