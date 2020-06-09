---
title: 'Postupy: Použití objektu pro vytváření kanálů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: 4bb2053fb50931756e79d5346a3f14d2acbe04f6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595307"
---
# <a name="how-to-use-the-channelfactory"></a>Postupy: Použití objektu pro vytváření kanálů
Obecná <xref:System.ServiceModel.ChannelFactory%601> Třída se používá v pokročilých scénářích, které vyžadují vytvoření továrny kanálu, který lze použít k vytvoření více než jednoho kanálu.  
  
### <a name="to-create-and-use-the-channelfactory-class"></a>Vytvoření a použití třídy ChannelFactory  
  
1. Sestavte a spusťte službu Windows Communication Foundation (WCF). Další informace najdete v tématu [navrhování a implementace služeb](../designing-and-implementing-services.md), [Konfigurace služeb](../configuring-services.md)a [hostování služeb](../hosting-services.md).  
  
2. K vygenerování kontraktu (rozhraní) pro klienta použijte [Nástroj pro metadata ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) .  
  
3. V kódu klienta použijte <xref:System.ServiceModel.ChannelFactory%601> třídu k vytvoření více naslouchací procesů koncového bodu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
