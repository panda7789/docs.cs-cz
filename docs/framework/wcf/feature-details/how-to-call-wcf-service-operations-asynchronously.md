---
title: 'Postupy: Asynchronní volání operací služby WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 400ed8e5ee8b236e9d0f843f27b7c2112ec28861
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601254"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a>Postupy: Asynchronní volání operací služby WCF

Tento článek popisuje, jak může klient přistupovat k operaci služby asynchronně. Služba v tomto článku implementuje `ICalculator` rozhraní. Klient může volat operace v tomto rozhraní asynchronně pomocí asynchronního modelu volání založeného na událostech. (Další informace o asynchronním volání modelu založeném na událostech naleznete v tématu [vícevláknové programování s asynchronním vzorem založeným na událostech](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)). Příklad, který ukazuje, jak implementovat asynchronní operace ve službě, naleznete v tématu [How to: Implementing a Asynchronous Service](../how-to-implement-an-asynchronous-service-operation.md). Další informace o synchronních a asynchronních operacích naleznete v tématu [synchronní a asynchronní operace](../synchronous-and-asynchronous-operations.md).  
  
> [!NOTE]
> Asynchronní volající model řízený událostmi není podporován při použití <xref:System.ServiceModel.ChannelFactory%601> . Informace o tom, jak provádět asynchronní volání pomocí <xref:System.ServiceModel.ChannelFactory%601> , naleznete v tématu [How to: asynchronní volání operací pomocí objektu pro vytváření kanálů](how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>Asynchronní volání operací služby WCF  
  
1. Spusťte nástroj Nástroj pro dodané [metadata (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) pomocí `/async` `/tcv:Version35` možností a příkazu společně, jak je znázorněno v následujícím příkazu.  
  
    ```console
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     Vygeneruje se kromě synchronních a standardních asynchronních operací založených na delegátech Třída klienta WCF, která obsahuje:  
  
    - Dvě `operationName` > `Async` operace <pro použití s přístupem k asynchronnímu volání založenému na událostech. Například:  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    - Operace dokončila události <formuláře `operationName` > `Completed` pro použití s přístupem k asynchronnímu volání založenému na událostech. Například:  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    - <xref:System.EventArgs?displayProperty=nameWithType>typy pro každou operaci (<formuláře `operationName` > `CompletedEventArgs` ) pro použití s přístupem k asynchronnímu volání založenému na událostech. Například:  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. V volající aplikaci vytvořte metodu zpětného volání, která bude volána po dokončení asynchronní operace, jak je znázorněno v následujícím ukázkovém kódu.  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. Před voláním operace použijte nový obecný <xref:System.EventHandler%601?displayProperty=nameWithType> typ <`operationName` > `EventArgs` pro přidání metody obslužné rutiny (vytvořené v předchozím kroku) do `operationName` > `Completed` události <. Pak zavolejte metodu <`operationName` > `Async` . Například:  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a>Příklad  
  
> [!NOTE]
> Pokyny pro návrh pro stav asynchronního modelu založeného na událostech, pokud je vrácena více než jedna hodnota, jako vlastnost se vrátí jedna hodnota `Result` a ostatní jsou vráceny jako vlastnosti <xref:System.EventArgs> objektu. Jedním z těchto výsledků je, že pokud klient Importuje metadata pomocí parametrů asynchronního příkazu založeného na událostech a operace vrátí více než jednu hodnotu, výchozí <xref:System.EventArgs> objekt vrátí jednu hodnotu jako `Result` vlastnost a zbytek je vlastnosti <xref:System.EventArgs> objektu. Pokud chcete jako vlastnost přijmout objekt zprávy `Result` a vracet hodnoty jako vlastnosti tohoto objektu, použijte `/messageContract` možnost Command. Tím se vygeneruje podpis, který vrátí zprávu odpovědi jako `Result` vlastnost <xref:System.EventArgs> objektu. Všechny interní návratové hodnoty jsou potom vlastnostmi objektu zprávy odpovědi.  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a>Viz také

- [Postupy: Implementace operace asynchronní služby](../how-to-implement-an-asynchronous-service-operation.md)
