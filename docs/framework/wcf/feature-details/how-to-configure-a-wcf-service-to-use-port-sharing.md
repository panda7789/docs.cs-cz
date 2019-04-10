---
title: 'Postupy: Konfigurace používání sdílení portů ve službě WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: bc0c822659ee57ac8dd87a2adddcd32e934ea4fb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302388"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a>Postupy: Konfigurace používání sdílení portů ve službě WCF
Nejjednodušší způsob, jak používat sdílení v aplikaci Windows Communication Foundation (WCF) portu net.tcp:// je zveřejnit službu pomocí <xref:System.ServiceModel.NetTcpBinding>.  
  
 Poskytuje tuto vazbu <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> vlastnost, která určuje, zda je povoleno sdílení portu net.tcp:// služby konfigurován s touto vazbou.  
  
 Následující postup ukazuje, jak používat <xref:System.ServiceModel.NetTcpBinding> třídy v kódu a pak pomocí konfigurační prvky nejprve otevřete koncový bod na net.tcp://localhost/MyService identifikátor URI (Uniform Resource).  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a>Chcete povolit port net.tcp:// sdílení NetTcpBinding v kódu  
  
1. Vytvoření služby k implementaci kontraktu volá `IMyService` a volejte jej `MyService`,.  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2. Vytvoření instance <xref:System.ServiceModel.NetTcpBinding> třídy a nastavit <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> vlastnost `true`.  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3. Vytvoření <xref:System.ServiceModel.ServiceHost> a přidejte do ní pro koncový bod služby `MyService` , který používá port povoleno sdílení <xref:System.ServiceModel.NetTcpBinding> a že naslouchá na koncovém bodu řešit URI "net.tcp://localhost/MyService".  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    >  Tento příklad používá výchozí port TCP 808, protože adresa koncového bodu identifikátor URI neurčuje jiné číslo portu. Vzhledem k tomu, že port je explicitně povoleno sdílení u vazby přenosu, tato služba může sdílet port 808 s dalšími službami v jiných procesech. Pokud nebyly povoleno sdílení portu a portu 808 se již používá jiná aplikace, tato služba vede <xref:System.ServiceModel.AddressAlreadyInUseException> kdy byl otevřen.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a>Chcete povolit port net.tcp:// sdílení NetTcpBinding v konfiguraci  
  
1. Následující příklad ukazuje, jak povolit sdílení portů a přidat koncový bod služby pomocí konfigurační prvky.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Sdílení portů Net.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [Postupy: Povolení Služby sdílení portů Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
