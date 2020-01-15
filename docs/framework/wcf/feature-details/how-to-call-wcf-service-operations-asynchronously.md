---
title: 'Postupy: Asynchronní volání operací služby WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 5eae08ab6b8dee5ebece66a1c41c87ebab3387bc
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963283"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a>Postupy: Asynchronní volání operací služby WCF

Tento článek popisuje, jak může klient přistupovat k operaci služby asynchronně. Služba v tomto článku implementuje rozhraní `ICalculator`. Klient může volat operace v tomto rozhraní asynchronně pomocí asynchronního modelu volání založeného na událostech. (Další informace o asynchronním volání modelu založeném na událostech naleznete v tématu [vícevláknové programování s asynchronním vzorem založeným na událostech](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)). Příklad, který ukazuje, jak implementovat asynchronní operace ve službě, naleznete v tématu [How to: Implementing a Asynchronous Service](../how-to-implement-an-asynchronous-service-operation.md). Další informace o synchronních a asynchronních operacích naleznete v tématu [synchronní a asynchronní operace](../synchronous-and-asynchronous-operations.md).  
  
> [!NOTE]
> Asynchronní model volání založený na událostech není podporován při použití <xref:System.ServiceModel.ChannelFactory%601>. Informace o tom, jak provádět asynchronní volání pomocí <xref:System.ServiceModel.ChannelFactory%601>, naleznete v tématu [How to: asynchronní volání operací pomocí objektu pro vytváření kanálů](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>Asynchronní volání operací služby WCF  
  
1. Spusťte nástroj Nástroj pro [metadata ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pomocí obou `/async` a možností příkazu `/tcv:Version35` společně, jak je znázorněno v následujícím příkazu.  
  
    ```console
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     Vygeneruje se kromě synchronních a standardních asynchronních operací založených na delegátech Třída klienta WCF, která obsahuje:  
  
    - Dvě <`operationName`>`Async` operace pro použití s přístupem k asynchronnímu volání založenému na událostech. Příklad:  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    - Operace dokončených operací ve formuláři <`operationName`>`Completed` pro použití s přístupem k asynchronnímu volání založenému na událostech. Příklad:  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    - <xref:System.EventArgs?displayProperty=nameWithType> typy pro každou operaci (< formuláře`operationName`>`CompletedEventArgs`) pro použití s přístupem k asynchronnímu volání založenému na událostech. Příklad:  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. V volající aplikaci vytvořte metodu zpětného volání, která bude volána po dokončení asynchronní operace, jak je znázorněno v následujícím ukázkovém kódu.  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. Před voláním operace použijte nový obecný <xref:System.EventHandler%601?displayProperty=nameWithType> typu <`operationName`>`EventArgs` k přidání metody obslužné rutiny (vytvořené v předchozím kroku) do události <`operationName`>`Completed`. Potom zavolejte metodu <`operationName`>`Async`. Příklad:  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a>Příklad  
  
> [!NOTE]
> Pokyny pro návrh stavu asynchronního modelu založeného na událostech, pokud je vrácena více než jedna hodnota, je vrácena jedna hodnota jako vlastnost `Result` a ostatní jsou vráceny jako vlastnosti objektu <xref:System.EventArgs>. Jedním z těchto výsledků je, že pokud klient Importuje metadata pomocí parametrů asynchronního příkazu založeného na událostech a operace vrátí více než jednu hodnotu, výchozí objekt <xref:System.EventArgs> vrátí jednu hodnotu jako vlastnost `Result` a zbytek je vlastnosti objektu <xref:System.EventArgs>. Pokud chcete objekt zprávy přijmout jako vlastnost `Result` a vracet hodnoty jako vlastnosti tohoto objektu, použijte možnost příkazu `/messageContract`. Tím se vygeneruje podpis, který vrátí zprávu odpovědi jako vlastnost `Result` objektu <xref:System.EventArgs>. Všechny interní návratové hodnoty jsou potom vlastnostmi objektu zprávy odpovědi.  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Implementace operace asynchronní služby](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
