---
title: 'Postupy: Kontrola nebo úprava parametrů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
ms.openlocfilehash: b4a673f97f06e8d489d9acc85d84e1ecea4656e4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795595"
---
# <a name="how-to-inspect-or-modify-parameters"></a>Postupy: Kontrola nebo úprava parametrů
Můžete zkontrolovat nebo upravit příchozí nebo odchozí zprávy pro jednu operaci na objektu klienta Windows Communication Foundation (WCF) nebo službě WCF implementací <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> rozhraní a jeho vložením do klienta nebo modulu runtime služby. K přidání inspektorů parametrů pro jednu operaci se obvykle používá chování operace. Další chování lze použít k zajištění snadného přístupu k modulu runtime v širším rozsahu. Další informace najdete v tématu [rozšíření klientů](extending-clients.md) a [rozšíření expedičních](extending-dispatchers.md)počítačů.  
  
### <a name="inspecting-or-modifying-parameters"></a>Kontrola nebo úprava parametrů  
  
1. Implementujte rozhraní <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>.  
  
2. <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> Implementujte<xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> , nebo (v<xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> závislosti na požadovaném oboru) přidejte svůj inspektor parametrů do vlastností nebo. <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>  
  
3. Vložte své chování před voláním <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> nebo metodou na <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Podrobnosti najdete v tématu [Konfigurace a rozšíření modulu runtime s chováním](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Příklad  
 Následující příklady kódu ukazují, v pořadí:  
  
- Implementace inspektoru parametru.  
  
- Implementace chování, která vloží inspektor parametru pomocí <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>a <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.  
  
- Konfigurační soubor, který načte a spustí chování koncového bodu v klientské aplikaci pro vložení inspektoru parametrů na klienta.  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a>Viz také:

- [Konfigurace a rozšíření modulu runtime pomocí chování](configuring-and-extending-the-runtime-with-behaviors.md)
