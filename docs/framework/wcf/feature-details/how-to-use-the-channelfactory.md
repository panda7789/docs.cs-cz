---
title: 'Postupy: Použití objektu pro vytváření kanálů'
description: Naučte se vytvořit továrnu kanálu pro vytvoření více než jednoho kanálu pro přístup ke službám pomocí klienta WCF.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: 7c87026ca4cf7c739f4615da9bc7f0272a382392
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246659"
---
# <a name="how-to-use-the-channelfactory"></a><span data-ttu-id="05bbc-103">Postupy: Použití objektu pro vytváření kanálů</span><span class="sxs-lookup"><span data-stu-id="05bbc-103">How to: Use the ChannelFactory</span></span>
<span data-ttu-id="05bbc-104">Obecná <xref:System.ServiceModel.ChannelFactory%601> Třída se používá v pokročilých scénářích, které vyžadují vytvoření továrny kanálu, který lze použít k vytvoření více než jednoho kanálu.</span><span class="sxs-lookup"><span data-stu-id="05bbc-104">The generic <xref:System.ServiceModel.ChannelFactory%601> class is used in advanced scenarios that require the creation of a channel factory that can be used to create more than one channel.</span></span>  
  
### <a name="to-create-and-use-the-channelfactory-class"></a><span data-ttu-id="05bbc-105">Vytvoření a použití třídy ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="05bbc-105">To create and use the ChannelFactory class</span></span>  
  
1. <span data-ttu-id="05bbc-106">Sestavte a spusťte službu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="05bbc-106">Build and run an Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="05bbc-107">Další informace najdete v tématu [navrhování a implementace služeb](../designing-and-implementing-services.md), [Konfigurace služeb](../configuring-services.md)a [hostování služeb](../hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="05bbc-107">For more information, see [Designing and Implementing Services](../designing-and-implementing-services.md), [Configuring Services](../configuring-services.md), and [Hosting Services](../hosting-services.md).</span></span>  
  
2. <span data-ttu-id="05bbc-108">K vygenerování kontraktu (rozhraní) pro klienta použijte [Nástroj pro metadata ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="05bbc-108">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the contract (interface) for the client.</span></span>  
  
3. <span data-ttu-id="05bbc-109">V kódu klienta použijte <xref:System.ServiceModel.ChannelFactory%601> třídu k vytvoření více naslouchací procesů koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="05bbc-109">In the client code, use the <xref:System.ServiceModel.ChannelFactory%601> class to create multiple endpoint listeners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05bbc-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="05bbc-110">Example</span></span>  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
