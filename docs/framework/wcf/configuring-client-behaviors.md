---
title: Konfigurace chování klientů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: bf65844cda195847989d1eb8ef752fe87c9de22c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532191"
---
# <a name="configuring-client-behaviors"></a>Konfigurace chování klientů
Windows Communication Foundation (WCF) nakonfiguruje chování dvěma způsoby: buď odkazující na chování konfigurace – které jsou definovány v `<behavior>` oddílu konfiguračního souboru aplikace klienta – nebo prostřednictvím kódu programu ve volání aplikace. Toto téma popisuje oba přístupy.  
  
 Při použití konfiguračního souboru, konfiguraci chování je pojmenovaná kolekce nastavení konfigurace. Název každé konfigurace chování musí být jedinečný. Tento řetězec se používá v `behaviorConfiguration` atributů konfigurace koncového bodu propojení chování koncového bodu.  
  
## <a name="example"></a>Příklad  
 Následující kód konfigurace definuje chování volá `myBehavior`. Koncový bod klienta odkazuje na toto chování v `behaviorConfiguration` atribut.  
  
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
  
## <a name="using-behaviors-programmatically"></a>Pomocí chování prostřednictvím kódu programu  
 Můžete také nakonfigurovat nebo vložit chování prostřednictvím kódu programu vyhledáním odpovídající `Behaviors` vlastnost v objektu klienta Windows Communication Foundation (WCF) nebo na objekt factory kanálu klienta před otevřením klienta.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak prostřednictvím kódu programu vložit chování díky přístupu do <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> vlastnost <xref:System.ServiceModel.Description.ServiceEndpoint> vrácená <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> vlastnost před vytvořením objektu kanálu.  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a>Viz také:
- [\<behaviors>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
