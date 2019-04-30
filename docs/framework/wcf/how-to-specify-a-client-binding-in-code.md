---
title: 'Postupy: Určení klientské vazby v kódu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: c95e30c65c6096140fca0c1241e76fbc7af4df3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929126"
---
# <a name="how-to-specify-a-client-binding-in-code"></a>Postupy: Určení klientské vazby v kódu
V tomto příkladu se vytvoří klienta pro použití kalkulačky služby a vazby pro tohoto klienta je imperativně zadat v kódu. Klient přistupuje k `CalculatorService`, která implementuje `ICalculator` rozhraní a službě i klientovi použít <xref:System.ServiceModel.BasicHttpBinding> třídy.  
  
 Tento postup předpokládá, že je spuštěna služba kalkulačky. Informace o vytváření služby najdete v tématu [jak: Zadání vazby služby v konfiguraci](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md). Využívá také [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) poskytuje klientské součásti budou automaticky generovány. Nástroj vygeneruje kód klienta pro přístupu ke službě.  
  
 Klient je vytvořená ve dvou částech. Generuje svcutil.exe `ClientCalculator` , který implementuje `ICalculator` rozhraní. Tato klientská aplikace pak konstruován tak, že vytváří instanci `ClientCalculator` a potom zadáte vazbu a adresu pro službu v kódu.  
  
 Pro zdrojovou kopii tohoto příkladu, najdete v článku [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) vzorku.  
  
### <a name="to-specify-a-custom-binding-in-code"></a>Chcete-li určit vlastní vazby v kódu  
  
1. Pomocí Svcutil.exe lze generovat kód z metadat služby z příkazového řádku.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. Klient, který je generován obsahuje `ICalculator` rozhraní, které definuje kontrakt služby, který musí splňovat implementace klienta.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. Také obsahuje implementaci generovaného klienta `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. Vytvoření instance `ClientCalculator` , která používá <xref:System.ServiceModel.BasicHttpBinding> třídy v klientské aplikaci a potom volání operací služby na zadané adrese.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. Kompilace a spuštění klienta.  
  
## <a name="see-also"></a>Viz také:

- [Používání vazeb ke konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
