---
title: 'Postupy: Kontrola a změny zpráv ve službě'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
ms.openlocfilehash: ec1c60bc2b3e966c576de260dfe3b06a05ab84c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488072"
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a><span data-ttu-id="5ef12-102">Postupy: Kontrola a změny zpráv ve službě</span><span class="sxs-lookup"><span data-stu-id="5ef12-102">How to: Inspect and Modify Messages on the Service</span></span>
<span data-ttu-id="5ef12-103">Můžete zkontrolovat nebo upravit příchozích nebo odchozích zpráv mezi klienta Windows Communication Foundation (WCF) implementací <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> a jejich vložení do služby modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="5ef12-103">You can inspect or modify the incoming or outgoing messages across a Windows Communication Foundation (WCF) client by implementing a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> and inserting it into the service runtime.</span></span> <span data-ttu-id="5ef12-104">Další informace najdete v tématu [rozšíření dispečerů](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span><span class="sxs-lookup"><span data-stu-id="5ef12-104">For more information, see [Extending Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span></span> <span data-ttu-id="5ef12-105">Ekvivalentní funkce služby je <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5ef12-105">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="5ef12-106">Chcete-li zkontrolovat nebo upravit zprávy</span><span class="sxs-lookup"><span data-stu-id="5ef12-106">To inspect or modify messages</span></span>  
  
1.  <span data-ttu-id="5ef12-107">Implementace <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5ef12-107">Implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2.  <span data-ttu-id="5ef12-108">Implementace <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, nebo <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> rozhraní v závislosti na oboru, ve kterém chcete snadno vložit zprávu inspector vaší služby.</span><span class="sxs-lookup"><span data-stu-id="5ef12-108">Implement a <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> interface depending upon the scope at which you want to easily insert your service message inspector.</span></span>  
  
3.  <span data-ttu-id="5ef12-109">Vložit chování vaší před voláním <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metodu <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5ef12-109">Insert your behavior prior to calling the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5ef12-110">Podrobnosti najdete v tématu [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="5ef12-110">For details, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ef12-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="5ef12-111">Example</span></span>  
 <span data-ttu-id="5ef12-112">Následující příklady kódu zobrazit v pořadí:</span><span class="sxs-lookup"><span data-stu-id="5ef12-112">The following code examples show, in order:</span></span>  
  
-   <span data-ttu-id="5ef12-113">Nástroj inspector implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="5ef12-113">A service inspector implementation.</span></span>  
  
-   <span data-ttu-id="5ef12-114">Chování služby, která vloží funkci Kontrola.</span><span class="sxs-lookup"><span data-stu-id="5ef12-114">A service behavior that inserts the inspector.</span></span>  
  
-   <span data-ttu-id="5ef12-115">Konfigurační soubor, který načte a spustí chování v aplikaci služby.</span><span class="sxs-lookup"><span data-stu-id="5ef12-115">A configuration file that loads and runs the behavior in a service application.</span></span>  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a><span data-ttu-id="5ef12-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ef12-116">See Also</span></span>  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>  
 [<span data-ttu-id="5ef12-117">Konfigurace a rozšíření modulu runtime pomocí chování</span><span class="sxs-lookup"><span data-stu-id="5ef12-117">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
