---
title: 'Postupy: Konfigurace používání sdílení portů ve službě WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: cd8d76137ac195e452a7d66fb6ddbeda405a922f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185090"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a>Postupy: Konfigurace používání sdílení portů ve službě WCF
Nejjednodušší způsob, jak použít sdílení portů net.tcp:// v aplikaci WCF (Windows <xref:System.ServiceModel.NetTcpBinding>Communication Foundation), je vystavit službu pomocí rozhraní .  
  
 Tato vazba <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> poskytuje vlastnost, která řídí, zda net.tcp:// sdílení portů je povolena pro službu nakonfigurovanou s touto vazbou.  
  
 Následující postup ukazuje, jak <xref:System.ServiceModel.NetTcpBinding> pomocí třídy otevřít koncový bod na identifikátor ujednotného prostředku (URI) net.tcp://localhost/MyService, nejprve v kódu a potom pomocí konfiguračních prvků.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a>Povolení sdílení portu net.tcp:// na netTcpbinding v kódu  
  
1. Vytvořte službu pro `IMyService` implementaci smlouvy `MyService`s názvem a nazvejte ji .  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2. Vytvořte instanci <xref:System.ServiceModel.NetTcpBinding> třídy <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> a `true`nastavte vlastnost na .  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3. Vytvořte <xref:System.ServiceModel.ServiceHost> a přidejte koncový bod `MyService` služby, který <xref:System.ServiceModel.NetTcpBinding> používá povolenou funkci sdílení portů a který naslouchá na adrese koncového bodu URI "net.tcp://localhost/MyService".  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    > Tento příklad používá výchozí port TCP 808, protože identifikátor URI adresy koncového bodu neurčuje jiné číslo portu. Vzhledem k tomu, že sdílení portů je explicitně povoleno na vazbě přenosu, může tato služba sdílet port 808 s jinými službami v jiných procesech. Pokud sdílení portů nebyly povoleny a jiné aplikace již používají <xref:System.ServiceModel.AddressAlreadyInUseException> port 808, tato služba by vyvolat při otevření.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a>Povolení sdílení portu net.tcp:// na netTcpbinding v konfiguraci  
  
1. Následující příklad ukazuje, jak povolit sdílení portů a přidat koncový bod služby pomocí konfiguračních prvků.  
  
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

- [Sdílení portů Net.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [Postupy: Povolení služby sdílení portů Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
