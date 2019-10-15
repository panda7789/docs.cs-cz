---
title: Konfigurace chování klientů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: ca466af71f62ef72e021753b132afdc847f75d76
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320694"
---
# <a name="configuring-client-behaviors"></a>Konfigurace chování klientů
Windows Communication Foundation (WCF) konfiguruje chování dvěma způsoby: buď odkazem na konfigurace chování, které jsou definovány v části `<behavior>` konfiguračního souboru klientské aplikace – nebo programově v volající aplikaci. V tomto tématu jsou popsány oba přístupy.  
  
 Při použití konfiguračního souboru je konfigurace chování pojmenovaná kolekce nastavení konfigurace. Název každé konfigurace chování musí být jedinečný. Tento řetězec se používá v atributu `behaviorConfiguration` konfigurace koncového bodu pro propojení koncového bodu s chováním.  
  
## <a name="example"></a>Příklad  
 Následující konfigurační kód definuje chování s názvem `myBehavior`. Koncový bod klienta odkazuje na toto chování v atributu `behaviorConfiguration`.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="myBehavior">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <bindings>  
            <basicHttpBinding>  
                <binding name="myBinding" maxReceivedMessageSize="10000" />  
            </basicHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="myAddress" binding="basicHttpBinding" bindingConfiguration="myBinding" behaviorConfiguration="myBehavior" contract="myContract" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-behaviors-programmatically"></a>Programové použití chování  
 Chování můžete také nakonfigurovat nebo vložit programově tak, že před otevřením klienta vyhledáte @no__t příslušnou vlastnost-0 objektu klienta služby Windows Communication Foundation (WCF) nebo objektu factory kanálu klienta.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak programově vložit chování přístupem k vlastnosti <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> u <xref:System.ServiceModel.Description.ServiceEndpoint> vráceného z vlastnosti <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> před vytvořením objektu kanálu.  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a>Viz také:

- [@no__t – 1behaviors >](../configure-apps/file-schema/wcf/behaviors.md)
