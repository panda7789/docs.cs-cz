---
title: 'Postupy: Asynchronní volání operací pomocí ChannelFactory'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
ms.openlocfilehash: 3080514d06119a2f1b621cff16056ac7577c30b3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966806"
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a>Postupy: Asynchronní volání operací pomocí ChannelFactory
Toto téma popisuje, jak může klient přistupovat k operaci služby asynchronně při použití <xref:System.ServiceModel.ChannelFactory%601>klientské aplikace založené na systému. (Při použití <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> objektu k vyvolání služby můžete použít asynchronní model volání řízený událostmi. Další informace najdete v tématu [jak: Asynchronní volání operací služby](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md). Další informace o asynchronním volání modelu založeném na událostech naleznete v tématu [asynchronní vzor založený na událostech (EAP)](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  
  
 Služba v tomto tématu implementuje `ICalculator` rozhraní. Klient může volat operace v tomto rozhraní asynchronně, což znamená, že operace, jako například `Add` , jsou rozděleny do dvou `BeginAdd` metod `EndAdd`, a v případě, že se volání Inicializuje a druhý z nich načítá výsledek Po dokončení operace. Příklad znázorňující asynchronní implementaci operace ve službě najdete v tématu [How to: Implementujte asynchronní operaci](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)služby. Podrobnosti o synchronních a asynchronních operacích naleznete v tématu [synchronní a asynchronní operace](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>Asynchronní volání operací služby WCF  
  
1. Spusťte nástroj [obslužné rutiny metadat ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) s `/async` možností, jak je znázorněno v následujícím příkazu.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     Tím se vygeneruje asynchronní verze klienta kontraktu služby pro danou operaci.  
  
2. Vytvořte funkci zpětného volání, která bude volána po dokončení asynchronní operace, jak je znázorněno v následujícím ukázkovém kódu.  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3. Pro asynchronní přístup k operaci služby vytvořte klienta a zavolejte `Begin[Operation]` ( `BeginAdd`například) a zadejte funkci zpětného volání, jak je znázorněno v následujícím ukázkovém kódu.  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     Když se spustí funkce zpětného volání, klient `End<operation>` zavolá ( `EndAdd`například), aby načetl výsledek.  
  
## <a name="example"></a>Příklad  
 Služba, která se používá s klientským kódem použitým v předchozím postupu, implementuje `ICalculator` rozhraní, jak je znázorněno v následujícím kódu. Na straně `Add` služby vyvolají operace a `Subtract` kontraktu synchronně synchronní dobu běhu služby Windows Communication Foundation (WCF), a to i v případě, že předchozí kroky klienta jsou na klientovi vyvolány asynchronně. Operace `Multiply` a`Divide` se používají k asynchronnímu vyvolání služby na straně služby, a to i v případě, že je klient vyvolá synchronně. Tento příklad nastaví <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> vlastnost na `true`hodnotu. Toto nastavení vlastnosti v kombinaci s implementací asynchronního vzoru .NET Framework instruuje dobu běhu k asynchronnímu vyvolání operace.  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
