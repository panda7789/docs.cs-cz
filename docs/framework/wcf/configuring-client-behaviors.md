---
title: "Konfigurace chování klientů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6f16f32128c7223fa600802ae593d36286847dc8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="configuring-client-behaviors"></a>Konfigurace chování klientů
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]Nakonfiguruje chování dvěma způsoby: buď odkazující na chování konfigurace – které jsou definovány v `<behavior>` oddílu konfiguračního souboru aplikace klienta – nebo prostřednictvím kódu programu v volající aplikace. Toto téma popisuje obou přístupů.  
  
 Při použití konfiguračního souboru, konfigurace chování je pojmenovaná kolekce nastavení konfigurace. Název každé chování konfigurace musí být jedinečný. Tento řetězec se používá v `behaviorConfiguration` atribut konfigurace koncového bodu na koncový bod propojit chování.  
  
## <a name="example"></a>Příklad  
 Následující kód konfigurace definuje chování názvem `myBehavior`. Koncový bod klienta odkazuje toto chování v `behaviorConfiguration` atribut.  
  
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
 Můžete také nakonfigurovat nebo vložit chování prostřednictvím kódu programu tím, že se příslušné `Behaviors` vlastnost [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] objekt klienta nebo v objektu factory kanálu klienta před otevřením klienta.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak programově vložit chování přímým přístupem <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> vlastnost na <xref:System.ServiceModel.Description.ServiceEndpoint> vrácená z <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> vlastnost před vytvoření objektu kanálu.  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a>Viz také  
 [\<chování >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
