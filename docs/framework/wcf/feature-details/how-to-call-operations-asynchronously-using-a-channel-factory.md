---
title: 'Postupy: Asynchronní volání operací pomocí ChannelFactory'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
ms.openlocfilehash: 17b6dd979f7554cd433cc1abcf2a4da8dd9b83cb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779337"
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a>Postupy: Asynchronní volání operací pomocí ChannelFactory
Toto téma popisuje, jak má přístup klient operace služby asynchronně při použití <xref:System.ServiceModel.ChannelFactory%601>– klientské aplikace. (Při použití <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> objektu, abyste mohli vyvolat službu, můžete použít založený na událostech asynchronní volání model. Další informace najdete v tématu [jak: Asynchronní volání operací služby](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md). Další informace o založený na událostech asynchronní volání modelu najdete v tématu [události asynchronní vzor založený (EAP)](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).)  
  
 Implementuje služby v tomto tématu `ICalculator` rozhraní. Klient může asynchronní volání operací na tomto rozhraní, což znamená, že operace jako `Add` jsou rozděleny do dvou metod `BeginAdd` a `EndAdd`, o které zahájí volání a druhý z nich načítá výsledek Po dokončení operace. Příklad ukazuje, jak implementace operace asynchronní služby najdete v tématu [jak: Implementace operace asynchronní služby](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md). Podrobnosti o synchronní a asynchronní operace, najdete v článku [synchronní a asynchronní operace](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>Pro asynchronní volání operací služby WCF  
  
1. Spustit [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj s `/async` možnosti, jak je znázorněno v následujícím příkazu.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     Tím se vygeneruje asynchronního klientského verzi kontrakt služby pro tuto operaci.  
  
2. Vytvořte zpětné volání funkce se volá, když asynchronní operace nebude dokončena, jak je znázorněno v následujícím ukázkovém kódu.  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3. Pro přístup k asynchronní operaci služby, vytvoření klienta a volání `Begin[Operation]` (například `BeginAdd`) a zadejte funkci zpětného volání, jak je znázorněno v následujícím ukázkovém kódu.  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     Jakmile funkce zpětného volání spustí, klient volá `End<operation>` (například `EndAdd`) načíst výsledky.  
  
## <a name="example"></a>Příklad  
 Služba, která se použije klientský kód, který se používá v předchozím postupu implementuje `ICalculator` rozhraní, jak je znázorněno v následujícím kódu. Na straně služeb `Add` a `Subtract` operace kontraktu se vyvolala synchronně podle Windows Communication Foundation (WCF) běhu, i když v předchozích krocích klienta jsou vyvolány asynchronně na straně klienta. `Multiply` a `Divide` operace slouží k vyvolání služby asynchronně na straně služeb, i když klient vyvolá je synchronně. Tento příklad nastaví <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> vlastnost `true`. Nastavení této vlastnosti v kombinaci s implementací [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] asynchronního vzoru, říká běhu k vyvolání operace asynchronně.  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
