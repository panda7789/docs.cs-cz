---
title: 'Postupy: Vytvoření služby vyžadující relace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 495de5a926cfc0c5aab88337f5f33b991c49e71a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184991"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a>Postupy: Vytvoření služby vyžadující relace
Relace vytvořit sdílený stav mezi dvěma nebo více koncových bodů, které umožňuje užitečné funkce, jako jsou zpětná volání, multi-hop zabezpečení a přidružení mezi klienty a instance služby. Další informace o relacích v aplikacích WCF (Windows Communication Foundation) naleznete v [tématu Using Sessions](../../../../docs/framework/wcf/using-sessions.md).  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a>Určení, že smlouva vyžaduje její vazbu pro podporu relací  
  
1. Vytvořte servisní smlouvu s alespoň jednou operací. Příklad vytvoření servisní smlouvy naleznete v tématu [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).  
  
2. <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> Upravte, který deklaruje smlouvu nastavením <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> vlastnosti buď:  
  
    - <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>pokud tato smlouva musí být spuštěna v rámci relace.  
  
    - <xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType>pokud lze tuto smlouvu spustit v rámci relace.  
  
    - <xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType>pokud tato smlouva nesmí být spuštěna v rámci relace.  
  
3. Nakonfigurujte koncový bod služby tak, aby používal vazbu, která podporuje relace. Následující příklad konfigurace ukazuje použití <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, který podporuje`-`ws reliablemessaging relace.  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="example"></a>Příklad  
 Následující ukázkový kód ukazuje, jak zadat požadavek relace na úrovni smlouvy <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> a použít konfigurační soubor pro podporu tohoto požadavku s vazbou.  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
