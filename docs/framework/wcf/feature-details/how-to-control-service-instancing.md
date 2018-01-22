---
title: "Postupy: vytváření instancí služby Řízení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c77cae35abacb780aec86750c37c6ecd91ff370
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-control-service-instancing"></a>Postupy: vytváření instancí služby Řízení
Nastavení režimu instance služby umožňuje určit, kdy <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (a jeho objekt přidružená služba definovaný uživatelem) je vytvořen. Najdete v článku <xref:System.ServiceModel.InstanceContextMode> výčet režimů možné. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]najdete v části chování, [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md). Pracovní příklady najdete v tématu [chování](../../../../docs/framework/wcf/samples/behaviors.md).  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a>K řízení životního cyklu instance služby pomocí kódu  
  
1.  Použít <xref:System.ServiceModel.ServiceBehaviorAttribute> k třídě služby.  
  
2.  Nastavte <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost na jednu z následujících hodnot: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, nebo <xref:System.ServiceModel.InstanceContextMode.Single>.  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu nastaví <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut <xref:System.ServiceModel.InstanceContextMode.PerCall>.  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>  
 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>  
 <xref:System.ServiceModel.InstanceContextMode>  
 [Služby: Ukázky chování](http://msdn.microsoft.com/library/4e3c6513-a7ff-4b35-8dcf-b5506c6f39a7)
