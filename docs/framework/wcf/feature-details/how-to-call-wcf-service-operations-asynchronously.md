---
title: "Postupy: Asynchronní volání operací služby WCF"
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
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 549510d4d2b2ae0ee031b1c5426e7e28ab902bcd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a>Postupy: Asynchronní volání operací služby WCF
Toto téma popisuje, jak mít klient přístup operace služby asynchronně. Implementuje službu v tomto tématu `ICalculator` rozhraní. Klienta můžete asynchronní volání operací na tomto rozhraní pomocí událostmi řízené asynchronní volání modelu. (Další informace o na základě událostí asynchronní volání modelu najdete v tématu [vícevláknové programování s asynchronním vzorem na základě událostí](http://go.microsoft.com/fwlink/?LinkId=248184)). Příklad, který ukazuje, jak implementovat asynchronní operace služby, naleznete v části [postupy: implementace operace asynchronní služby](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md). Další informace o synchronní a asynchronní operace najdete v tématu [synchronní a asynchronní operace](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
> [!NOTE]
>  Událostmi řízené asynchronní volání modelu není podporováno při použití <xref:System.ServiceModel.ChannelFactory%601>. Informace o asynchronní volání pomocí <xref:System.ServiceModel.ChannelFactory%601>, najdete v části [postupy: volání operace asynchronně pomocí postupu kanálu](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>Chcete-li asynchronní volání operací služby WCF  
  
1.  Spustit [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj s oběma `/async` a `/tcv:Version35` společně příkaz Možnosti, jak je znázorněno v následujícím příkazu.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     Tím se vygeneruje, kromě synchronní a standard na základě delegáta asynchronních operací, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] třída klienta, který obsahuje:  
  
    -   Dva <`operationName` > `Async` operací pro použití s na základě událostí asynchronní volání přístup. Příklad:  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    -   Operace byla dokončena události ve formátu <`operationName` > `Completed` pro použití s na základě událostí asynchronní volání přístup. Příklad:  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    -   <xref:System.EventArgs?displayProperty=nameWithType>typy pro každou operaci (ve formátu <`operationName`>`CompletedEventArgs`) pro použití s na základě událostí asynchronní volání přístup. Příklad:  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2.  Ve volání aplikace vytvořte metody zpětného volání, která se má volat při asynchronní operace se dokončila, jak je znázorněno v následujícím ukázkovém kódu.  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3.  Před voláním operace, použijte nové obecného <xref:System.EventHandler%601?displayProperty=nameWithType> typu <`operationName` > `EventArgs` přidat metodu obslužné rutiny (vytvořený v předchozím kroku) do <`operationName` > `Completed` událostí. Potom zavolejte <`operationName` > `Async` metoda. Příklad:  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a>Příklad  
  
> [!NOTE]
>  Podle pokynů návrhu pro asynchronní model na základě událostí stavu, že pokud je vrácen více než jednu hodnotu, se vrátí jednu hodnotu jako `Result` vlastnost a jiné jsou vrácena jako vlastnosti na <xref:System.EventArgs> objektu. Jeden výsledek tohoto objektu je, že pokud klient naimportuje metadata pomocí možností na základě událostí asynchronní příkaz a operaci vrátí více než jednu hodnotu, výchozí <xref:System.EventArgs> objekt vrátí jednu hodnotu jako `Result` vlastnost a zbývající jsou vlastnosti <xref:System.EventArgs> objektu. Pokud chcete dostávat zprávy objektu jako `Result` vlastnost a mít vrácené hodnoty jako vlastnosti tohoto objektu, použijte `/messageContract` příkaz možnost. Tím se vygeneruje podpisu, který vrátí zprávu odpovědi jako `Result` vlastnost <xref:System.EventArgs> objektu. Všechny interní návratové hodnoty jsou pak vlastnosti objektu zprávu odpovědi.  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: implementace operace asynchronní služby](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
