---
title: 'Postupy: Používání ChannelFactory'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: 7d542a3dcae514e75194b49c23a8dec5dd7e8c3b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773724"
---
# <a name="how-to-use-the-channelfactory"></a>Postupy: Používání ChannelFactory
Obecné <xref:System.ServiceModel.ChannelFactory%601> třída se používá v pokročilých scénářích, které vyžadují vytvoření objektu pro vytváření kanálů, které je možné vytvořit více než jeden kanál.  
  
### <a name="to-create-and-use-the-channelfactory-class"></a>Vytvoření a použití třídy ChannelFactory  
  
1. Sestavte a spusťte službu Windows Communication Foundation (WCF). Další informace najdete v tématu [návrh a implementace služeb](../../../../docs/framework/wcf/designing-and-implementing-services.md), [konfigurace služby](../../../../docs/framework/wcf/configuring-services.md), a [hostování služeb](../../../../docs/framework/wcf/hosting-services.md).  
  
2. Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování kontraktu (interface) pro klienta.  
  
3. V kódu klienta, použijte <xref:System.ServiceModel.ChannelFactory%601> třída pro vytvoření naslouchacích procesů více koncových bodů.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
