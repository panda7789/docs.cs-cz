---
title: 'Postupy: Kontrola a změny zpráv ve službě'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
ms.openlocfilehash: 1356983361c483170d9d7365932b788f2421bf09
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795598"
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a>Postupy: Kontrola a změny zpráv ve službě
Příchozí nebo odchozí zprávy můžete kontrolovat nebo upravovat v rámci klienta Windows Communication Foundation (WCF) implementací <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> a vložením do modulu runtime služby. Další informace najdete v tématu [rozšíření expedičních](extending-dispatchers.md). Ekvivalentní funkce služby je <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.  
  
### <a name="to-inspect-or-modify-messages"></a>Kontrola nebo změna zpráv  
  
1. Implementujte rozhraní <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.  
  
2. Implementujte rozhraní <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> , nebo, v závislosti na rozsahu, ve kterém chcete snadno vložit kontrolu zpráv služby. <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>  
  
3. Před voláním <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metody na, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>vložte své chování. Podrobnosti najdete v tématu [Konfigurace a rozšíření modulu runtime s chováním](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Příklad  
 Následující příklady kódu ukazují, v pořadí:  
  
- Implementace v rámci kontroly služby.  
  
- Chování služby, které vkládá kontroler.  
  
- Konfigurační soubor, který načte a spustí chování aplikace služby.  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [Konfigurace a rozšíření modulu runtime pomocí chování](configuring-and-extending-the-runtime-with-behaviors.md)
