---
title: 'Postupy: Řízení vytváření instancí služby'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
ms.openlocfilehash: 8a73dd90d268c61e0df974861753119e205a870f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599071"
---
# <a name="how-to-control-service-instancing"></a>Postupy: Řízení vytváření instancí služby
Nastavení režimu instance služby vám umožní určit, kdy <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> se vytvoří (a přidružený objekt služby definované uživatelem). Podívejte se na <xref:System.ServiceModel.InstanceContextMode> výčet možných režimů. Další informace o chování najdete v tématu [Konfigurace a rozšíření modulu runtime s chováním](../extending/configuring-and-extending-the-runtime-with-behaviors.md). Pracovní příklady najdete v tématu [chování](../samples/behaviors.md).  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a>Řízení životnosti instance služby pomocí kódu  
  
1. Použijte <xref:System.ServiceModel.ServiceBehaviorAttribute> pro třídu služby.  
  
2. Nastavte <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost na jednu z následujících hodnot: <xref:System.ServiceModel.InstanceContextMode.PerCall> , <xref:System.ServiceModel.InstanceContextMode.PerSession> , nebo <xref:System.ServiceModel.InstanceContextMode.Single> .  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu nastaví <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost <xref:System.ServiceModel.ServiceBehaviorAttribute> atributu na <xref:System.ServiceModel.InstanceContextMode.PerCall> .  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>
- <xref:System.ServiceModel.InstanceContextMode>
- [Služba: ukázky chování](../samples/behaviors.md)
