---
title: 'Postupy: Zadání klientské vazby v kódu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: 9be571d7be020aef546fdd7ec7cb7519a48ea350
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184059"
---
# <a name="how-to-specify-a-client-binding-in-code"></a>Postupy: Zadání klientské vazby v kódu
V tomto příkladu je klient vytvořen pro použití služby kalkulačky a vazba pro tohoto klienta je zadána imperativně v kódu. Klient přistupuje k `CalculatorService` `ICalculator` aplikaci , která implementuje <xref:System.ServiceModel.BasicHttpBinding> rozhraní, a služba i klient používají třídu.  
  
 Tento postup předpokládá, že je spuštěna služba kalkulačky. Informace o vytváření služby naleznete v [tématu Postup: Zadání vazby služby v konfiguraci](how-to-specify-a-service-binding-in-configuration.md). Používá také [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) poskytuje automaticky generovat klientské součásti. Nástroj generuje kód klienta pro přístup ke službě.  
  
 Klient je postaven ve dvou částech. Svcutil.exe `ClientCalculator` generuje, který implementuje `ICalculator` rozhraní. Tato klientská aplikace je pak vytvořena `ClientCalculator` vytvořením instance a zadáním vazby a adresy pro službu v kódu.  
  
 Zdrojovou kopii tohoto příkladu naleznete v ukázce [BasicBinding.](./samples/basicbinding.md)  
  
### <a name="to-specify-a-custom-binding-in-code"></a>Určení vlastní vazby v kódu  
  
1. Pomocí příkazu Svcutil.exe z příkazového řádku vygenerujte kód z metadat služby.  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. Klient, který je generován `ICalculator` obsahuje rozhraní, které definuje servisní smlouvy, které implementace klienta musí splňovat.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. Vygenerovaný klient také `ClientCalculator`obsahuje implementaci .  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. Vytvořte `ClientCalculator` instanci, <xref:System.ServiceModel.BasicHttpBinding> která používá třídu v klientské aplikaci, a pak zavolejte operace služby na zadanou adresu.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. Zkompilujte a spusťte klienta.  
  
## <a name="see-also"></a>Viz také

- [Používání vazeb ke konfiguraci služeb a klientů](using-bindings-to-configure-services-and-clients.md)
