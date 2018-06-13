---
title: Konfigurace chování klientů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: 062e726b6f1d6831303e1cc0ae82a434daab860c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458104"
---
# <a name="configuring-client-behaviors"></a><span data-ttu-id="64c92-102">Konfigurace chování klientů</span><span class="sxs-lookup"><span data-stu-id="64c92-102">Configuring Client Behaviors</span></span>
<span data-ttu-id="64c92-103">Windows Communication Foundation (WCF) nakonfiguruje chování dvěma způsoby: buď odkazující na chování konfigurace – které jsou definovány v `<behavior>` části z konfiguračního souboru aplikace klienta – nebo prostřednictvím kódu programu volání aplikace.</span><span class="sxs-lookup"><span data-stu-id="64c92-103">Windows Communication Foundation (WCF) configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="64c92-104">Toto téma popisuje obou přístupů.</span><span class="sxs-lookup"><span data-stu-id="64c92-104">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="64c92-105">Při použití konfiguračního souboru, konfigurace chování je pojmenovaná kolekce nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="64c92-105">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="64c92-106">Název každé chování konfigurace musí být jedinečný.</span><span class="sxs-lookup"><span data-stu-id="64c92-106">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="64c92-107">Tento řetězec se používá v `behaviorConfiguration` atribut konfigurace koncového bodu na koncový bod propojit chování.</span><span class="sxs-lookup"><span data-stu-id="64c92-107">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64c92-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="64c92-108">Example</span></span>  
 <span data-ttu-id="64c92-109">Následující kód konfigurace definuje chování názvem `myBehavior`.</span><span class="sxs-lookup"><span data-stu-id="64c92-109">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="64c92-110">Koncový bod klienta odkazuje toto chování v `behaviorConfiguration` atribut.</span><span class="sxs-lookup"><span data-stu-id="64c92-110">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="64c92-111">Pomocí chování prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="64c92-111">Using Behaviors Programmatically</span></span>  
 <span data-ttu-id="64c92-112">Můžete také nakonfigurovat nebo vložit chování prostřednictvím kódu programu tím, že se příslušné `Behaviors` vlastnost v objektu klienta Windows Communication Foundation (WCF) nebo na objekt factory kanálu klienta před otevřením klienta.</span><span class="sxs-lookup"><span data-stu-id="64c92-112">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the Windows Communication Foundation (WCF) client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64c92-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="64c92-113">Example</span></span>  
 <span data-ttu-id="64c92-114">Následující příklad kódu ukazuje, jak programově vložit chování přímým přístupem <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> vlastnost na <xref:System.ServiceModel.Description.ServiceEndpoint> vrácená z <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> vlastnost před vytvoření objektu kanálu.</span><span class="sxs-lookup"><span data-stu-id="64c92-114">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="64c92-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="64c92-115">See Also</span></span>  
 [<span data-ttu-id="64c92-116">\<chování ></span><span class="sxs-lookup"><span data-stu-id="64c92-116">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
