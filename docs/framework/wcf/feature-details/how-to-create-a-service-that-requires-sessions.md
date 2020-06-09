---
title: 'Postupy: Vytvoření služby vyžadující relace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 29c2a87daaf763a50aa657c9badc002ff2fa27e1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593331"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a>Postupy: Vytvoření služby vyžadující relace
Relace vytvoří sdílený stav mezi dvěma nebo více koncovými body, které umožňují užitečné funkce, jako jsou zpětná volání, zabezpečení více segmentů a přidružení mezi klienty a instancemi služby. Další informace o relacích v aplikacích Windows Communication Foundation (WCF) najdete v tématu [použití relací](../using-sessions.md).  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a>Určení, že kontrakt vyžaduje svoji vazbu na podporu relací  
  
1. Vytvořte kontrakt služby s nejméně jednou operací. Příklad vytvoření kontraktu služby naleznete v tématu [How to: define a Service kontrakt](../how-to-define-a-wcf-service-contract.md).  
  
2. Upravte <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> , který deklaruje kontrakt, nastavením <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> vlastnosti na hodnotu:  
  
    - <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>Pokud se tento kontrakt musí spustit v rámci relace.  
  
    - <xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType>Pokud se tato smlouva dá spustit v rámci relace.  
  
    - <xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType>Pokud tato smlouva nesmí běžet v rámci relace.  
  
3. Nakonfigurujte koncový bod služby tak, aby používal vazbu, která podporuje relace. Následující příklad konfigurace ukazuje použití <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> , který podporuje relaci WS- `-` ReliableMessaging.  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak zadat požadavek relace na úrovni smlouvy a použít konfigurační soubor pro podporu tohoto požadavku s <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> vazbou.  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
