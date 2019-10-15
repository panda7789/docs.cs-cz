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
# <a name="configuring-client-behaviors"></a><span data-ttu-id="a07f2-102">Konfigurace chování klientů</span><span class="sxs-lookup"><span data-stu-id="a07f2-102">Configuring Client Behaviors</span></span>
<span data-ttu-id="a07f2-103">Windows Communication Foundation (WCF) konfiguruje chování dvěma způsoby: buď odkazem na konfigurace chování, které jsou definovány v části `<behavior>` konfiguračního souboru klientské aplikace – nebo programově v volající aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a07f2-103">Windows Communication Foundation (WCF) configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="a07f2-104">V tomto tématu jsou popsány oba přístupy.</span><span class="sxs-lookup"><span data-stu-id="a07f2-104">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="a07f2-105">Při použití konfiguračního souboru je konfigurace chování pojmenovaná kolekce nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a07f2-105">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="a07f2-106">Název každé konfigurace chování musí být jedinečný.</span><span class="sxs-lookup"><span data-stu-id="a07f2-106">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="a07f2-107">Tento řetězec se používá v atributu `behaviorConfiguration` konfigurace koncového bodu pro propojení koncového bodu s chováním.</span><span class="sxs-lookup"><span data-stu-id="a07f2-107">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a07f2-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="a07f2-108">Example</span></span>  
 <span data-ttu-id="a07f2-109">Následující konfigurační kód definuje chování s názvem `myBehavior`.</span><span class="sxs-lookup"><span data-stu-id="a07f2-109">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="a07f2-110">Koncový bod klienta odkazuje na toto chování v atributu `behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="a07f2-110">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="a07f2-111">Programové použití chování</span><span class="sxs-lookup"><span data-stu-id="a07f2-111">Using Behaviors Programmatically</span></span>  
 <span data-ttu-id="a07f2-112">Chování můžete také nakonfigurovat nebo vložit programově tak, že před otevřením klienta vyhledáte @no__t příslušnou vlastnost-0 objektu klienta služby Windows Communication Foundation (WCF) nebo objektu factory kanálu klienta.</span><span class="sxs-lookup"><span data-stu-id="a07f2-112">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the Windows Communication Foundation (WCF) client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a07f2-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="a07f2-113">Example</span></span>  
 <span data-ttu-id="a07f2-114">Následující příklad kódu ukazuje, jak programově vložit chování přístupem k vlastnosti <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> u <xref:System.ServiceModel.Description.ServiceEndpoint> vráceného z vlastnosti <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> před vytvořením objektu kanálu.</span><span class="sxs-lookup"><span data-stu-id="a07f2-114">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="a07f2-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a07f2-115">See also</span></span>

- [<span data-ttu-id="a07f2-116">@no__t – 1behaviors ></span><span class="sxs-lookup"><span data-stu-id="a07f2-116">\<behaviors></span></span>](../configure-apps/file-schema/wcf/behaviors.md)
