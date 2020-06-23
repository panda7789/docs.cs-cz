---
title: Konfigurace chování klientů
description: 'Přečtěte si o dvou způsobech, které WCF nakonfiguruje chování: v konfiguračním souboru aplikace nebo programově z volající aplikace.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: 4b83862221cf249455478c3ade159a3101062f3e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245437"
---
# <a name="configuring-client-behaviors"></a>Konfigurace chování klientů
Windows Communication Foundation (WCF) nakonfiguruje chování dvěma způsoby: buď odkazem na konfigurace chování, které jsou definovány v `<behavior>` části konfiguračního souboru klientské aplikace – nebo programově v volající aplikaci. V tomto tématu jsou popsány oba přístupy.  
  
 Při použití konfiguračního souboru je konfigurace chování pojmenovaná kolekce nastavení konfigurace. Název každé konfigurace chování musí být jedinečný. Tento řetězec se používá v `behaviorConfiguration` atributu konfigurace koncového bodu pro propojení koncového bodu s chováním.  
  
## <a name="example"></a>Příklad  
 Následující konfigurační kód definuje chování s názvem `myBehavior` . Koncový bod klienta odkazuje na toto chování v `behaviorConfiguration` atributu.  
  
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
 Chování můžete taky nakonfigurovat nebo vložit programově tak, že `Behaviors` před otevřením klienta vyhledáte příslušnou vlastnost objektu klienta Windows Communication Foundation (WCF) nebo objektu factory kanálu klienta.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak programově vložit chování přístupem k <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> vlastnosti <xref:System.ServiceModel.Description.ServiceEndpoint> vrácenou z <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> vlastnosti před vytvořením objektu kanálu.  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a>Viz také

- [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)
