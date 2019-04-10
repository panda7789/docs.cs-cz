---
title: 'Postupy: Používání ChannelFactory'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: 7d542a3dcae514e75194b49c23a8dec5dd7e8c3b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298848"
---
# <a name="how-to-use-the-channelfactory"></a><span data-ttu-id="c36a2-102">Postupy: Používání ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="c36a2-102">How to: Use the ChannelFactory</span></span>
<span data-ttu-id="c36a2-103">Obecné <xref:System.ServiceModel.ChannelFactory%601> třída se používá v pokročilých scénářích, které vyžadují vytvoření objektu pro vytváření kanálů, které je možné vytvořit více než jeden kanál.</span><span class="sxs-lookup"><span data-stu-id="c36a2-103">The generic <xref:System.ServiceModel.ChannelFactory%601> class is used in advanced scenarios that require the creation of a channel factory that can be used to create more than one channel.</span></span>  
  
### <a name="to-create-and-use-the-channelfactory-class"></a><span data-ttu-id="c36a2-104">Vytvoření a použití třídy ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="c36a2-104">To create and use the ChannelFactory class</span></span>  
  
1. <span data-ttu-id="c36a2-105">Sestavte a spusťte službu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c36a2-105">Build and run an Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="c36a2-106">Další informace najdete v tématu [návrh a implementace služeb](../../../../docs/framework/wcf/designing-and-implementing-services.md), [konfigurace služby](../../../../docs/framework/wcf/configuring-services.md), a [hostování služeb](../../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="c36a2-106">For more information, see [Designing and Implementing Services](../../../../docs/framework/wcf/designing-and-implementing-services.md), [Configuring Services](../../../../docs/framework/wcf/configuring-services.md), and [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
2. <span data-ttu-id="c36a2-107">Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování kontraktu (interface) pro klienta.</span><span class="sxs-lookup"><span data-stu-id="c36a2-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the contract (interface) for the client.</span></span>  
  
3. <span data-ttu-id="c36a2-108">V kódu klienta, použijte <xref:System.ServiceModel.ChannelFactory%601> třída pro vytvoření naslouchacích procesů více koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="c36a2-108">In the client code, use the <xref:System.ServiceModel.ChannelFactory%601> class to create multiple endpoint listeners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c36a2-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="c36a2-109">Example</span></span>  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
