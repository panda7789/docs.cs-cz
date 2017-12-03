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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c63a91683817311b8d644eb4285101e32eaea7f1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-client-behaviors"></a><span data-ttu-id="b0e3f-102">Konfigurace chování klientů</span><span class="sxs-lookup"><span data-stu-id="b0e3f-102">Configuring Client Behaviors</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="b0e3f-103">Nakonfiguruje chování dvěma způsoby: buď odkazující na chování konfigurace – které jsou definovány v `<behavior>` oddílu konfiguračního souboru aplikace klienta – nebo prostřednictvím kódu programu v volající aplikace.</span><span class="sxs-lookup"><span data-stu-id="b0e3f-103"> configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="b0e3f-104">Toto téma popisuje obou přístupů.</span><span class="sxs-lookup"><span data-stu-id="b0e3f-104">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="b0e3f-105">Při použití konfiguračního souboru, konfigurace chování je pojmenovaná kolekce nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b0e3f-105">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="b0e3f-106">Název každé chování konfigurace musí být jedinečný.</span><span class="sxs-lookup"><span data-stu-id="b0e3f-106">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="b0e3f-107">Tento řetězec se používá v `behaviorConfiguration` atribut konfigurace koncového bodu na koncový bod propojit chování.</span><span class="sxs-lookup"><span data-stu-id="b0e3f-107">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0e3f-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0e3f-108">Example</span></span>  
 <span data-ttu-id="b0e3f-109">Následující kód konfigurace definuje chování názvem `myBehavior`.</span><span class="sxs-lookup"><span data-stu-id="b0e3f-109">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="b0e3f-110">Koncový bod klienta odkazuje toto chování v `behaviorConfiguration` atribut.</span><span class="sxs-lookup"><span data-stu-id="b0e3f-110">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="b0e3f-111">Pomocí chování prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="b0e3f-111">Using Behaviors Programmatically</span></span>  
 <span data-ttu-id="b0e3f-112">Můžete také nakonfigurovat nebo vložit chování prostřednictvím kódu programu tím, že se příslušné `Behaviors` vlastnost [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] objekt klienta nebo v objektu factory kanálu klienta před otevřením klienta.</span><span class="sxs-lookup"><span data-stu-id="b0e3f-112">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0e3f-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0e3f-113">Example</span></span>  
 <span data-ttu-id="b0e3f-114">Následující příklad kódu ukazuje, jak programově vložit chování přímým přístupem <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> vlastnost na <xref:System.ServiceModel.Description.ServiceEndpoint> vrácená z <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> vlastnost před vytvoření objektu kanálu.</span><span class="sxs-lookup"><span data-stu-id="b0e3f-114">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="b0e3f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0e3f-115">See Also</span></span>  
 [<span data-ttu-id="b0e3f-116">\<chování ></span><span class="sxs-lookup"><span data-stu-id="b0e3f-116">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
