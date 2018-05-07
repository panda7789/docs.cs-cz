---
title: 'Postupy: Kontrola nebo úprava parametrů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
ms.openlocfilehash: ddf6ad667eb131ec6fa4f12ed112c57368c43d9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-inspect-or-modify-parameters"></a>Postupy: Kontrola nebo úprava parametrů
Můžete zkontrolovat nebo upravit příchozích nebo odchozích zpráv pro jednu operaci na objektu klienta Windows Communication Foundation (WCF) nebo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby implementací <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> rozhraní a jejich vložení do klienta nebo služby modul runtime. Obvykle se používá operaci chování k přidání inspektoři parametr pro jednu operaci; jiného chování slouží k poskytování snadného přístupu pro modul runtime na větší rozsah. Další informace najdete v tématu [rozšíření klienti](../../../../docs/framework/wcf/extending/extending-clients.md) a [rozšíření dispečerů](../../../../docs/framework/wcf/extending/extending-dispatchers.md).  
  
### <a name="inspecting-or-modifying-parameters"></a>Probíhá kontrola nebo úprava parametrů  
  
1.  Implementace <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> rozhraní.  
  
2.  Implementace <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (v závislosti na požadované oboru) přidat vaše parametr inspector buď <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> vlastnosti.  
  
3.  Vložit chování vaší před voláním <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metodu <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Podrobnosti najdete v tématu [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Příklad  
 Následující příklady kódu zobrazit v pořadí:  
  
-   Implementace parametr inspector.  
  
-   Implementace chování, která vloží inspector parametr pomocí <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>a <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.  
  
-   Konfigurační soubor, který načte a spustí chování koncového bodu v aplikaci klienta k vložení parametru inspector na straně klienta.  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace a rozšíření modulu runtime pomocí chování](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
