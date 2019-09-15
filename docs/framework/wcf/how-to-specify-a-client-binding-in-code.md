---
title: 'Postupy: Určení klientské vazby v kódu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: 37769a84ca623e2f7f246d36180aa17537e90bfa
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990233"
---
# <a name="how-to-specify-a-client-binding-in-code"></a>Postupy: Určení klientské vazby v kódu
V tomto příkladu je vytvořen klient pro použití služby kalkulačky a vazba pro tohoto klienta je v kódu určena imperativně. Klient přistupuje `CalculatorService`k `ICalculator` rozhraní, které implementuje rozhraní a jak službu, tak i klient používající <xref:System.ServiceModel.BasicHttpBinding> třídu.  
  
 Tento postup předpokládá, že je spuštěná služba kalkulačky. Informace o tom, jak službu sestavovat, najdete v tématu [How to: Zadejte vazbu služby v konfiguraci](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md). K automatickému generování komponent klienta používá [Nástroj Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF). Nástroj vygeneruje kód klienta pro přístup ke službě.  
  
 Klient je sestaven ve dvou částech. Svcutil. exe vygeneruje `ClientCalculator` `ICalculator` rozhraní, které implementuje rozhraní. Tato klientská aplikace je pak vytvořena konstrukcí instance `ClientCalculator` a pak zadáním vazby a adresy služby v kódu.  
  
 Zdrojovou kopii tohoto příkladu najdete v ukázce [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) .  
  
### <a name="to-specify-a-custom-binding-in-code"></a>Určení vlastní vazby v kódu  
  
1. K vygenerování kódu z metadat služby použijte Svcutil. exe z příkazového řádku.  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. Vygenerovaný klient obsahuje `ICalculator` rozhraní, které definuje kontrakt služby, který musí implementace klienta splňovat.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. Vygenerovaný klient také obsahuje implementaci `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. Vytvořte instanci `ClientCalculator` , která <xref:System.ServiceModel.BasicHttpBinding> používá třídu v klientské aplikaci, a potom zavolejte operace služby na zadané adrese.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. Zkompilujte a spusťte klienta.  
  
## <a name="see-also"></a>Viz také:

- [Používání vazeb ke konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
