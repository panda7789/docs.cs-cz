---
title: 'Postupy: Kontrola a změny zpráv ve službě'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
ms.openlocfilehash: ec1c60bc2b3e966c576de260dfe3b06a05ab84c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a>Postupy: Kontrola a změny zpráv ve službě
Můžete zkontrolovat nebo upravit příchozích nebo odchozích zpráv mezi klienta Windows Communication Foundation (WCF) implementací <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> a jejich vložení do služby modulu runtime. Další informace najdete v tématu [rozšíření dispečerů](../../../../docs/framework/wcf/extending/extending-dispatchers.md). Ekvivalentní funkce služby je <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.  
  
### <a name="to-inspect-or-modify-messages"></a>Chcete-li zkontrolovat nebo upravit zprávy  
  
1.  Implementace <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> rozhraní.  
  
2.  Implementace <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, nebo <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> rozhraní v závislosti na oboru, ve kterém chcete snadno vložit zprávu inspector vaší služby.  
  
3.  Vložit chování vaší před voláním <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metodu <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>. Podrobnosti najdete v tématu [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Příklad  
 Následující příklady kódu zobrazit v pořadí:  
  
-   Nástroj inspector implementaci služby.  
  
-   Chování služby, která vloží funkci Kontrola.  
  
-   Konfigurační soubor, který načte a spustí chování v aplikaci služby.  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>  
 [Konfigurace a rozšíření modulu runtime pomocí chování](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
