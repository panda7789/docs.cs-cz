---
title: 'Postupy: Zadání klientské vazby v kódu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: ec5db7a305a63ac7ae9c2e2a7bb1c9c7691b8daa
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320890"
---
# <a name="how-to-specify-a-client-binding-in-code"></a>Postupy: Zadání klientské vazby v kódu
V tomto příkladu je vytvořen klient pro použití služby kalkulačky a vazba pro tohoto klienta je v kódu určena imperativně. Klient přistupuje k `CalculatorService`, který implementuje rozhraní `ICalculator` a jak službu, tak i klient používající třídu <xref:System.ServiceModel.BasicHttpBinding>.  
  
 Tento postup předpokládá, že je spuštěná služba kalkulačky. Informace o sestavování služby najdete v tématu [How to: určení vazby služby v konfiguraci](how-to-specify-a-service-binding-in-configuration.md). K automatickému generování komponent klienta používá [Nástroj Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF). Nástroj vygeneruje kód klienta pro přístup ke službě.  
  
 Klient je sestaven ve dvou částech. Svcutil. exe vygeneruje `ClientCalculator`, který implementuje rozhraní `ICalculator`. Tato klientská aplikace je pak vytvořena konstrukcí instance `ClientCalculator` a zadáním vazby a adresy pro službu v kódu.  
  
 Zdrojovou kopii tohoto příkladu najdete v ukázce [BasicBinding](./samples/basicbinding.md) .  
  
### <a name="to-specify-a-custom-binding-in-code"></a>Určení vlastní vazby v kódu  
  
1. K vygenerování kódu z metadat služby použijte Svcutil. exe z příkazového řádku.  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. Vygenerovaný klient obsahuje rozhraní `ICalculator` definující kontrakt služby, který musí implementace klienta splňovat.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. Vygenerovaný klient obsahuje také implementaci `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. Vytvořte instanci `ClientCalculator`, která používá třídu <xref:System.ServiceModel.BasicHttpBinding> v klientské aplikaci, a pak na zadané adrese volejte operace služby.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. Zkompilujte a spusťte klienta.  
  
## <a name="see-also"></a>Viz také:

- [Používání vazeb ke konfiguraci služeb a klientů](using-bindings-to-configure-services-and-clients.md)
