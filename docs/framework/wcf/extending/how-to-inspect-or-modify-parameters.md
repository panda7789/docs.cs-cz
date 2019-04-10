---
title: 'Postupy: Kontrola nebo úprava parametrů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
ms.openlocfilehash: 1238c81e2607da6fc5e742aacd1b1dcc69996a8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209941"
---
# <a name="how-to-inspect-or-modify-parameters"></a>Postupy: Kontrola nebo úprava parametrů
Můžete zkontrolovat nebo upravit příchozí nebo odchozí zprávy pro jediná operace na objektu klienta Windows Communication Foundation (WCF) nebo službu WCF implementací <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> rozhraní a jejich vložení do klienta nebo služby modulu runtime. Obvykle na operaci chování slouží k přidání kontroly parametrů pro jednu operaci. jiné chování slouží k poskytování snadného přístupu k modulu runtime na větší rozsah. Další informace najdete v tématu [rozšíření klienty](../../../../docs/framework/wcf/extending/extending-clients.md) a [rozšíření dispečerů](../../../../docs/framework/wcf/extending/extending-dispatchers.md).  
  
### <a name="inspecting-or-modifying-parameters"></a>Kontrola nebo úprava parametrů  
  
1.  Implementujte rozhraní <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>.  
  
2.  Implementace <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (v závislosti na požadovaný rozsah) a přidejte ho do vašeho parametru inspector <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> vlastnosti.  
  
3.  Vložit vaše chování před voláním <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metodu <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Podrobnosti najdete v tématu [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Příklad  
 Následující příklady kódu zobrazit v pořadí:  
  
-   Na parametr inspektoru implementace.  
  
-   Implementace chování, která vloží inspektor parametr pomocí <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>a <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.  
  
-   Konfigurační soubor, který načte a spustí chování koncového bodu v klientské aplikaci k vložení parametru inspektoru na straně klienta.  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a>Viz také:

- [Konfigurace a rozšíření modulu runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
