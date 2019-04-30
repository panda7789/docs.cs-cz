---
title: 'Postupy: Vytvoření služby vyžadující relace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 53b6c809103a2a32d544b8317164a5fa3aa81596
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787631"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a>Postupy: Vytvoření služby vyžadující relace
Relace vytvořit sdílený stav mezi dva nebo víc koncových bodů, které umožňuje užitečných funkcí, jako je například zpětná volání, zabezpečení s více segmenty směrování a přidružení mezi klienty a instance služby. Další informace o relacích v aplikacích Windows Communication Foundation (WCF) najdete v tématu [s využitím relací](../../../../docs/framework/wcf/using-sessions.md).  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a>Chcete-li určit, že kontrakt vyžadovat jeho vazby pro podporu relace  
  
1. Vytvoření kontraktu služby s alespoň jednu operaci. Příklad vytvoření kontraktu služby najdete v tématu [jak: Definování kontraktu služby](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).  
  
2. Upravit <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> kontrakt, který deklaruje tak, že nastavíte <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> vlastnost buď:  
  
    - <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> Pokud tento kontrakt musí být spuštěn v rámci relace.  
  
    - <xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> Pokud tuto smlouvu můžete spustit v relaci.  
  
    - <xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> Pokud tuto smlouvu nesmí běžet v rámci relace.  
  
3. Nakonfigurujte koncový bod služby můžete použít vazbu, která podporuje relace. Následující příklad konfigurace ukazuje použití <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, která podporuje WS`-`ReliableMessaging relace.  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]   
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak zadat vyžadování úroveň smlouvy relace a pomocí konfiguračního souboru splnění tohoto požadavku se <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> vazby.  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)] 
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]      
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]     
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
