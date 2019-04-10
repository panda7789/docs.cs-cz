---
title: 'Postupy: Řízení vytváření instancí služby'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
ms.openlocfilehash: e8efbc5a3dec5f60dbefc8f6dc377d97b29b7653
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330178"
---
# <a name="how-to-control-service-instancing"></a>Postupy: Řízení vytváření instancí služby
Nastavení režimu instance služby umožňuje určit, kdy <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (a její přidružená služba uživatelského objektu) se vytvoří. Zobrazit <xref:System.ServiceModel.InstanceContextMode> výčet možných režimů. Další informace o chování najdete v tématu [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md). Příklady práce, naleznete v tématu [chování](../../../../docs/framework/wcf/samples/behaviors.md).  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a>K řízení životního cyklu instance služby pomocí kódu  
  
1. Použít <xref:System.ServiceModel.ServiceBehaviorAttribute> na třídu služby.  
  
2. Nastavte <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost na jednu z následujících hodnot: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, nebo <xref:System.ServiceModel.InstanceContextMode.Single>.  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu nastaví <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut <xref:System.ServiceModel.InstanceContextMode.PerCall>.  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>
- <xref:System.ServiceModel.InstanceContextMode>
- [Služba: Chování ukázky](../samples/behaviors.md)
