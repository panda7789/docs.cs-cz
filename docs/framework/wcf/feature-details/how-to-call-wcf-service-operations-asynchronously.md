---
title: 'Postupy: Asynchronní volání operací služby WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 90e00e4264ff808151c9e1c58fdaf290765620c8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43747668"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a>Postupy: Asynchronní volání operací služby WCF
Toto téma popisuje, jak má přístup klient služby operace asynchronně. Implementuje služby v tomto tématu `ICalculator` rozhraní. Klient může asynchronní volání operací na tomto rozhraní za použití založený na událostech asynchronní volání modelu. (Další informace o založený na událostech asynchronní volání modelu najdete v tématu [vícevláknové programování s asynchronní vzor založený na událostech](https://go.microsoft.com/fwlink/?LinkId=248184)). Příklad, který ukazuje, jak implementace operace asynchronní služby, najdete v části [postupy: implementace operace asynchronní služby](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md). Další informace o synchronní a asynchronní operace, najdete v části [synchronní a asynchronní operace](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
> [!NOTE]
>  Založený na událostech asynchronní volání modelu není podporováno při použití <xref:System.ServiceModel.ChannelFactory%601>. Informace o tom, že byla zahájena asynchronní volání pomocí <xref:System.ServiceModel.ChannelFactory%601>, naleznete v tématu [postupy: volání operace asynchronně pomocí objektu pro vytváření kanálů](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>Pro asynchronní volání operací služby WCF  
  
1.  Spustit [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj s oběma `/async` a `/tcv:Version35` možnosti příkazu společně, jak je znázorněno v následujícím příkazu.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     Tím se vygeneruje, kromě synchronní a standardní delegáta asynchronních operací, třída klienta WCF, která obsahuje:  
  
    -   Dva <`operationName` > `Async` operace pro použití s založený na událostech asynchronní volání přístup. Příklad:  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    -   Operace se dokončila událostí ve formátu <`operationName` > `Completed` pro použití s založený na událostech asynchronní volání přístup. Příklad:  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    -   <xref:System.EventArgs?displayProperty=nameWithType> typy pro každou operaci (ve formátu <`operationName`>`CompletedEventArgs`) pro použití s založený na událostech asynchronní volání přístup. Příklad:  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2.  Ve volání aplikace vytvořte metody zpětného volání se volá, když asynchronní operace nebude dokončena, jak je znázorněno v následujícím ukázkovém kódu.  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3.  Před voláním operace, používají nový obecný <xref:System.EventHandler%601?displayProperty=nameWithType> typu <`operationName` > `EventArgs` přidáte do metodu obslužné rutiny (vytvořený v předchozím kroku) <`operationName` > `Completed` událostí. Zavolejte <`operationName` > `Async` metody. Příklad:  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a>Příklad  
  
> [!NOTE]
>  Pokyny návrhu pro asynchronní model založený na událostech stát, že pokud se vrátí více než jednu hodnotu, se vrátí jednu hodnotu jako `Result` vlastnosti a ostatní jsou vrácena jako vlastnosti na <xref:System.EventArgs> objektu. Jeden výsledek tohoto je, že pokud klient naimportuje metadata pomocí možnosti založené na událostech asynchronního příkazu a operace vrátí více než jednu hodnotu, výchozí <xref:System.EventArgs> objekt vrátí jednu hodnotu jako `Result` vlastnost a zbývající jsou vlastnosti <xref:System.EventArgs> objektu. Pokud chcete přijímat zprávy objektu jako `Result` vlastnost a vrácené hodnoty jako vlastnosti objektu, použijte `/messageContract` možnost příkazu. Tím se vygeneruje podpis, který vrací zprávy s odpovědí jako `Result` vlastnost <xref:System.EventArgs> objektu. Všechny interní vrácené hodnoty jsou pak vlastnosti objektu zprávu odpovědi.  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Implementace operace asynchronní služby](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
