---
title: "Postupy: Zadání klientské vazby v kódu"
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
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6c44bc03642eb83a28497b320a77b2f9f8c6fb7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-a-client-binding-in-code"></a>Postupy: Zadání klientské vazby v kódu
V tomto příkladu se vytvoří klienta pomocí kalkulačky služby a vazby pro tohoto klienta je imperativní zadaný v kódu. Klient přistupuje k `CalculatorService`, který implementuje `ICalculator` rozhraní a jak službu a klienta použít <xref:System.ServiceModel.BasicHttpBinding> třídy.  
  
 Tento postup předpokládá, že je spuštěna služba kalkulačky. Informace o vytváření služby najdete v tématu [postupy: zadání vazby služby v konfiguraci](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md). Používá také [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] poskytuje k automatickému generování součásti klienta. Nástroj generuje kód klienta pro přístup k službě.  
  
 Klient je součástí dvě části. Generuje svcutil.exe `ClientCalculator` , která implementuje `ICalculator` rozhraní. Tuto aplikaci klienta je pak vytvořený vytvořením instanci `ClientCalculator` a potom zadáte vazby a adresu pro služby v kódu.  
  
 Zdroj kopírování tohoto příkladu, najdete v článku [základní vazby](../../../docs/framework/wcf/samples/basicbinding.md) ukázka.  
  
### <a name="to-specify-a-custom-binding-in-code"></a>Chcete-li určit vlastní vazby v kódu  
  
1.  Generování kódu z metadat služby pomocí Svcutil.exe z příkazového řádku.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  Obsahuje klienta, který se generuje `ICalculator` rozhraní, které definuje kontrakt služby, které musí splňovat implementace klienta.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3.  Generovaného klienta obsahuje také provádění `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4.  Vytvoření instance `ClientCalculator` používající <xref:System.ServiceModel.BasicHttpBinding> třídy v aplikaci klienta a pak volání operací služby na zadané adrese.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5.  Zkompilování a spuštění klienta.  
  
## <a name="see-also"></a>Viz také  
 [Používání vazeb ke konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
