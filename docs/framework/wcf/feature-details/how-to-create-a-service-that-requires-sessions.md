---
title: "Postupy: Vytvoření služby vyžadující relace"
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
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8f9cff53b598d4e477488bcb5b5e87be62e78bb9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-service-that-requires-sessions"></a>Postupy: Vytvoření služby vyžadující relace
Relace vytvořit sdílený stav mezi dva nebo víc koncových bodů, které umožňuje užitečných funkcí, jako je například zpětná volání, vícenásobného předávání zabezpečení a přidružení mezi klienty a instance služby. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]relace v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikace, najdete v části [pomocí relace](../../../../docs/framework/wcf/using-sessions.md).  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a>Chcete-li určit kontraktu vyžadují, aby se jeho vazby pro podporu relací  
  
1.  Vytvoření kontraktu služby s nejméně jednu operaci. Příklad vytvoření kontraktu služby, naleznete v části [postupy: definování kontraktu služby](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).  
  
2.  Změnit <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> , kontrakt deklaruje nastavením <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> vlastnost, která má buď:  
  
    -   <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>Pokud tento kontrakt musí být spuštěn v rámci relace.  
  
    -   <xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType>Pokud tuto smlouvu můžete spustit v rámci relace.  
  
    -   <xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType>Pokud tento kontrakt se nesmí spouštět v rámci relace.  
  
3.  Konfigurace vašeho koncového bodu služby použít vazbu, která podporuje relací. Následující příklad konfigurace ukazuje použití <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, který podporuje WS`-`ReliableMessaging relace.  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]   
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak zadat vyžadování kontrakt úrovni relace a pomocí konfiguračního souboru pro podporu tento požadavek se <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> vazby.  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)] 
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]      
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]     
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>  
 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
