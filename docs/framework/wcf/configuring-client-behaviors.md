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
# <a name="configuring-client-behaviors"></a><span data-ttu-id="6ba16-103">Konfigurace chování klientů</span><span class="sxs-lookup"><span data-stu-id="6ba16-103">Configuring Client Behaviors</span></span>
<span data-ttu-id="6ba16-104">Windows Communication Foundation (WCF) nakonfiguruje chování dvěma způsoby: buď odkazem na konfigurace chování, které jsou definovány v `<behavior>` části konfiguračního souboru klientské aplikace – nebo programově v volající aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6ba16-104">Windows Communication Foundation (WCF) configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="6ba16-105">V tomto tématu jsou popsány oba přístupy.</span><span class="sxs-lookup"><span data-stu-id="6ba16-105">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="6ba16-106">Při použití konfiguračního souboru je konfigurace chování pojmenovaná kolekce nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="6ba16-106">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="6ba16-107">Název každé konfigurace chování musí být jedinečný.</span><span class="sxs-lookup"><span data-stu-id="6ba16-107">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="6ba16-108">Tento řetězec se používá v `behaviorConfiguration` atributu konfigurace koncového bodu pro propojení koncového bodu s chováním.</span><span class="sxs-lookup"><span data-stu-id="6ba16-108">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ba16-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ba16-109">Example</span></span>  
 <span data-ttu-id="6ba16-110">Následující konfigurační kód definuje chování s názvem `myBehavior` .</span><span class="sxs-lookup"><span data-stu-id="6ba16-110">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="6ba16-111">Koncový bod klienta odkazuje na toto chování v `behaviorConfiguration` atributu.</span><span class="sxs-lookup"><span data-stu-id="6ba16-111">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="6ba16-112">Programové použití chování</span><span class="sxs-lookup"><span data-stu-id="6ba16-112">Using Behaviors Programmatically</span></span>  
 <span data-ttu-id="6ba16-113">Chování můžete taky nakonfigurovat nebo vložit programově tak, že `Behaviors` před otevřením klienta vyhledáte příslušnou vlastnost objektu klienta Windows Communication Foundation (WCF) nebo objektu factory kanálu klienta.</span><span class="sxs-lookup"><span data-stu-id="6ba16-113">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the Windows Communication Foundation (WCF) client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ba16-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ba16-114">Example</span></span>  
 <span data-ttu-id="6ba16-115">Následující příklad kódu ukazuje, jak programově vložit chování přístupem k <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> vlastnosti <xref:System.ServiceModel.Description.ServiceEndpoint> vrácenou z <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> vlastnosti před vytvořením objektu kanálu.</span><span class="sxs-lookup"><span data-stu-id="6ba16-115">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="6ba16-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ba16-116">See also</span></span>

- [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)
