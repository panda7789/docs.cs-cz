---
title: 'Postupy: Zadání klientské vazby v kódu'
description: Naučte se, jak určit vazbu pro klienta WCF imperativně v kódu. V tomto příkladu přistupuje klient ke službě.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: e5e1dff98121985a598579d83043de838e21e5f1
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244501"
---
# <a name="how-to-specify-a-client-binding-in-code"></a>Postupy: Zadání klientské vazby v kódu
V tomto příkladu je vytvořen klient pro použití služby kalkulačky a vazba pro tohoto klienta je v kódu určena imperativně. Klient přistupuje k `CalculatorService` rozhraní, které implementuje `ICalculator` rozhraní a jak službu, tak i klient používající <xref:System.ServiceModel.BasicHttpBinding> třídu.  
  
 Tento postup předpokládá, že je spuštěná služba kalkulačky. Informace o sestavování služby najdete v tématu [How to: určení vazby služby v konfiguraci](how-to-specify-a-service-binding-in-configuration.md). K automatickému generování komponent klienta používá také nástroj pro dodávání [metadat (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF). Nástroj vygeneruje kód klienta pro přístup ke službě.  
  
 Klient je sestaven ve dvou částech. Svcutil.exe generuje `ClientCalculator` rozhraní, které implementuje `ICalculator` rozhraní. Tato klientská aplikace je pak vytvořena konstrukcí instance `ClientCalculator` a pak zadáním vazby a adresy služby v kódu.  
  
 Zdrojovou kopii tohoto příkladu najdete v ukázce [BasicBinding](./samples/basicbinding.md) .  
  
### <a name="to-specify-a-custom-binding-in-code"></a>Určení vlastní vazby v kódu  
  
1. K vygenerování kódu z metadat služby použijte Svcutil.exe z příkazového řádku.  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. Vygenerovaný klient obsahuje `ICalculator` rozhraní, které definuje kontrakt služby, který musí implementace klienta splňovat.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. Vygenerovaný klient také obsahuje implementaci `ClientCalculator` .  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. Vytvořte instanci `ClientCalculator` , která používá <xref:System.ServiceModel.BasicHttpBinding> třídu v klientské aplikaci, a potom zavolejte operace služby na zadané adrese.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. Zkompilujte a spusťte klienta.  
  
## <a name="see-also"></a>Viz také

- [Používání vazeb ke konfiguraci služeb a klientů](using-bindings-to-configure-services-and-clients.md)
