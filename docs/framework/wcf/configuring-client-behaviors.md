---
title: Konfigurace chování klientů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: 83fdc77bd17115f9952f2ca6c494ed0eb873cd9c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608772"
---
# <a name="configuring-client-behaviors"></a><span data-ttu-id="2931c-102">Konfigurace chování klientů</span><span class="sxs-lookup"><span data-stu-id="2931c-102">Configuring Client Behaviors</span></span>
<span data-ttu-id="2931c-103">Windows Communication Foundation (WCF) nakonfiguruje chování dvěma způsoby: buď odkazující na chování konfigurace – které jsou definovány v `<behavior>` oddílu konfiguračního souboru aplikace klienta – nebo prostřednictvím kódu programu ve volání aplikace.</span><span class="sxs-lookup"><span data-stu-id="2931c-103">Windows Communication Foundation (WCF) configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="2931c-104">Toto téma popisuje oba přístupy.</span><span class="sxs-lookup"><span data-stu-id="2931c-104">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="2931c-105">Při použití konfiguračního souboru, konfiguraci chování je pojmenovaná kolekce nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="2931c-105">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="2931c-106">Název každé konfigurace chování musí být jedinečný.</span><span class="sxs-lookup"><span data-stu-id="2931c-106">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="2931c-107">Tento řetězec se používá v `behaviorConfiguration` atributů konfigurace koncového bodu propojení chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="2931c-107">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2931c-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="2931c-108">Example</span></span>  
 <span data-ttu-id="2931c-109">Následující kód konfigurace definuje chování volá `myBehavior`.</span><span class="sxs-lookup"><span data-stu-id="2931c-109">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="2931c-110">Koncový bod klienta odkazuje na toto chování v `behaviorConfiguration` atribut.</span><span class="sxs-lookup"><span data-stu-id="2931c-110">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="2931c-111">Pomocí chování prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="2931c-111">Using Behaviors Programmatically</span></span>  
 <span data-ttu-id="2931c-112">Můžete také nakonfigurovat nebo vložit chování prostřednictvím kódu programu vyhledáním odpovídající `Behaviors` vlastnost v objektu klienta Windows Communication Foundation (WCF) nebo na objekt factory kanálu klienta před otevřením klienta.</span><span class="sxs-lookup"><span data-stu-id="2931c-112">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the Windows Communication Foundation (WCF) client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2931c-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="2931c-113">Example</span></span>  
 <span data-ttu-id="2931c-114">Následující příklad kódu ukazuje, jak prostřednictvím kódu programu vložit chování díky přístupu do <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> vlastnost <xref:System.ServiceModel.Description.ServiceEndpoint> vrácená <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> vlastnost před vytvořením objektu kanálu.</span><span class="sxs-lookup"><span data-stu-id="2931c-114">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="2931c-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2931c-115">See also</span></span>

- [<span data-ttu-id="2931c-116">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="2931c-116">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
