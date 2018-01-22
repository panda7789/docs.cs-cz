---
title: "Postupy: volání operací asynchronně pomocí postupu kanálu"
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
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 216c0d529a15004ea9f7d6f087aeee4bf4f10e56
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a>Postupy: volání operací asynchronně pomocí postupu kanálu
Toto téma popisuje, jak mít klient přístup operace služby asynchronně při použití <xref:System.ServiceModel.ChannelFactory%601>– na základě klientské aplikace. (Při použití <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> objekt k vyvolání služby můžete použít událostmi řízené asynchronní volání modelu. Další informace najdete v tématu [postupy: asynchronní volání operací služby](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md). Další informace o na základě událostí asynchronní volání modelu najdete v tématu [vícevláknové programování s asynchronním vzorem na základě událostí](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md).)  
  
 Implementuje službu v tomto tématu `ICalculator` rozhraní. Klient může asynchronní volání operací na tomto rozhraní, což znamená, že operace jako `Add` jsou rozdělit na dvě metody, `BeginAdd` a `EndAdd`, dřívějším, které zahájí volání a druhé z nich načte výsledek Po dokončení operace. Příklad způsobu implementace operace asynchronní ve službě, naleznete v části [postupy: implementace operace asynchronní služby](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md). Podrobnosti o synchronní a asynchronní operace najdete v tématu [synchronní a asynchronní operace](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>Chcete-li asynchronní volání operací služby WCF  
  
1.  Spustit [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj s `/async` možnost, jak je znázorněno v následujícím příkazu.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     Tím se vygeneruje na klienta asynchronní verzi kontrakt služby pro danou operaci.  
  
2.  Vytvoření funkce zpětného volání, která se má volat při asynchronní operace se dokončila, jak je znázorněno v následujícím ukázkovém kódu.  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3.  Pro přístup k operaci služby asynchronně, vytvoření klienta a volání `Begin[Operation]` (například `BeginAdd`) a zadejte funkci zpětného volání, jak je znázorněno v následujícím ukázkovém kódu.  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     Když funkce zpětného volání provede, klient volá `End<operation>` (například `EndAdd`) načíst výsledky.  
  
## <a name="example"></a>Příklad  
 Implementuje službu, která se používá s kód klienta, který se používá v předchozím postupu `ICalculator` rozhraní, jak je znázorněno v následujícím kódu. Na straně služby `Add` a `Subtract` operace kontraktu jsou vyvolány synchronně pomocí [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] běh, i když předchozí kroky klienta se asynchronně vyvolá na straně klienta. `Multiply` a `Divide` operací se používají k vyvolání službu asynchronně na straně služby, i když klient vyvolá je synchronně. Tento příklad nastaví <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> vlastnost `true`. Nastavení této vlastnosti v kombinaci s implementací [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] asynchronní vzor informuje běhu k vyvolání operace asynchronně.  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
  
## <a name="see-also"></a>Viz také  
 [Kontrakt služby: Ukázka asynchronního](http://msdn.microsoft.com/library/833db946-f511-4f64-a26f-2759a11217c7)
