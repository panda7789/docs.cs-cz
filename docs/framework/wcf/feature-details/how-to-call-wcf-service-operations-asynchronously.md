---
title: 'Postupy: Asynchronní volání operací služby WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 2d075bfebf7b5cbd2b2ce031a1c3855a925405a2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964031"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a>Postupy: Asynchronní volání operací služby WCF
Toto téma popisuje, jak může klient přistupovat k operaci služby asynchronně. Služba v tomto tématu implementuje `ICalculator` rozhraní. Klient může volat operace v tomto rozhraní asynchronně pomocí asynchronního modelu volání založeného na událostech. (Další informace o asynchronním volání modelu založeném na událostech naleznete v tématu [vícevláknové programování s asynchronním vzorem založeným](https://go.microsoft.com/fwlink/?LinkId=248184)na událostech). Příklad, který ukazuje, jak provést asynchronní implementaci operace ve službě, naleznete v tématu [How to: Implementujte asynchronní operaci](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)služby. Další informace o synchronních a asynchronních operacích naleznete v tématu [synchronní a asynchronní operace](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
> [!NOTE]
> Asynchronní volající model řízený událostmi není podporován při použití <xref:System.ServiceModel.ChannelFactory%601>. Informace o tom <xref:System.ServiceModel.ChannelFactory%601>, jak provádět asynchronní volání pomocí, [naleznete v tématu How to: Asynchronní volání operací pomocí objektu pro vytváření](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md)kanálů.  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>Asynchronní volání operací služby WCF  
  
1. Spusťte nástroj Nástroj pro dodané [metadata (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pomocí `/async` možností a `/tcv:Version35` příkazu společně, jak je znázorněno v následujícím příkazu.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     Vygeneruje se kromě synchronních a standardních asynchronních operací založených na delegátech Třída klienta WCF, která obsahuje:  
  
    - Dvě operace`operationName` <>propoužitís přístupemkasynchronnímuvolánízaloženémunaudálostech.`Async` Příklad:  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    - Operace dokončila události <`operationName` > `Completed` formuláře pro použití s přístupem k asynchronnímu volání založenému na událostech. Příklad:  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    - <xref:System.EventArgs?displayProperty=nameWithType>typy pro každou operaci (<`operationName`>`CompletedEventArgs`formuláře) pro použití s přístupem k asynchronnímu volání založenému na událostech. Příklad:  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. V volající aplikaci vytvořte metodu zpětného volání, která bude volána po dokončení asynchronní operace, jak je znázorněno v následujícím ukázkovém kódu.  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. Před <xref:System.EventHandler%601?displayProperty=nameWithType> voláním operace použijte nový obecný typ <`operationName` > `EventArgs` pro přidání metody obslužné rutiny (vytvořené v předchozím kroku) do události <`operationName`. > `Completed` Pak zavolejte metodu <`operationName`. > `Async` Příklad:  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a>Příklad  
  
> [!NOTE]
> Pokyny pro návrh pro stav asynchronního modelu založeného na událostech, pokud je vrácena více než jedna hodnota, jako `Result` vlastnost se vrátí jedna hodnota a ostatní jsou vráceny jako vlastnosti <xref:System.EventArgs> objektu. Jedním z těchto výsledků je, že pokud klient Importuje metadata pomocí parametrů asynchronního příkazu založeného na událostech a operace vrátí více než jednu hodnotu, výchozí <xref:System.EventArgs> objekt vrátí jednu hodnotu `Result` jako vlastnost a zbytek je <xref:System.EventArgs> vlastnosti objektu Pokud chcete jako `Result` vlastnost přijmout objekt zprávy a vracet hodnoty jako vlastnosti tohoto objektu, `/messageContract` použijte možnost Command. Tím se vygeneruje podpis, který vrátí zprávu odpovědi jako `Result` vlastnost <xref:System.EventArgs> objektu. Všechny interní návratové hodnoty jsou potom vlastnostmi objektu zprávy odpovědi.  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Implementace asynchronní operace služby](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
