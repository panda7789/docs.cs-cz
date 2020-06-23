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
# <a name="how-to-use-the-channelfactory"></a>Postupy: Použití objektu pro vytváření kanálů
Obecná <xref:System.ServiceModel.ChannelFactory%601> Třída se používá v pokročilých scénářích, které vyžadují vytvoření továrny kanálu, který lze použít k vytvoření více než jednoho kanálu.  
  
### <a name="to-create-and-use-the-channelfactory-class"></a>Vytvoření a použití třídy ChannelFactory  
  
1. Sestavte a spusťte službu Windows Communication Foundation (WCF). Další informace najdete v tématu [navrhování a implementace služeb](../designing-and-implementing-services.md), [Konfigurace služeb](../configuring-services.md)a [hostování služeb](../hosting-services.md).  
  
2. K vygenerování kontraktu (rozhraní) pro klienta použijte [Nástroj pro metadata ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) .  
  
3. V kódu klienta použijte <xref:System.ServiceModel.ChannelFactory%601> třídu k vytvoření více naslouchací procesů koncového bodu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
