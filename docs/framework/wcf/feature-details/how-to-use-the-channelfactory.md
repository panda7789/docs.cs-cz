---
title: 'Postupy: použití třídy ChannelFactory'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a076fb5b95c6750e6352235490b4e2e9ab883bbe
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-use-the-channelfactory"></a>Postupy: použití třídy ChannelFactory
Obecná <xref:System.ServiceModel.ChannelFactory%601> třída se používá v pokročilých scénářích, které vyžadují vytvoření kanálu, který slouží k vytvoření více než jeden kanál.  
  
### <a name="to-create-and-use-the-channelfactory-class"></a>Vytváření a používání ChannelFactory – třída  
  
1.  Sestavení a spuštění [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby. Další informace najdete v tématu [návrh a implementace služeb](../../../../docs/framework/wcf/designing-and-implementing-services.md), [konfigurace služby](../../../../docs/framework/wcf/configuring-services.md), a [hostování služeb](../../../../docs/framework/wcf/hosting-services.md).  
  
2.  Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování kontrakt (rozhraní) pro klienta.  
  
3.  V kódu klienta pomocí <xref:System.ServiceModel.ChannelFactory%601> třídy za účelem vytvoření více naslouchací procesy koncový bod.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
