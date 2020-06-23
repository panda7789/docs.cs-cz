---
title: 'Postupy: Implementace operace asynchronní služby'
description: Přečtěte si o struktuře asynchronní operace služby v WFC. Operace služby se dá implementovat asynchronně nebo synchronně.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: 5f890bd5124e2353cecee37d163b7f2c65b87fde
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244618"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a>Postupy: Implementace operace asynchronní služby
V aplikacích Windows Communication Foundation (WCF) může být operace služby implementována asynchronně nebo synchronně bez diktování klienta, jak ho volat. Například asynchronní operace služby mohou být volány synchronně a synchronní operace služby mohou být volány asynchronně. Příklad, který ukazuje asynchronní volání operace v klientské aplikaci, naleznete v tématu [How to: Asynchronous volání Operations Service](./feature-details/how-to-call-wcf-service-operations-asynchronously.md). Další informace o synchronních a asynchronních operacích najdete v tématu [Navrhování kontraktů služeb](designing-service-contracts.md) a [synchronních a asynchronních operací](synchronous-and-asynchronous-operations.md). Toto téma popisuje základní strukturu operace asynchronní služby, kód není úplný. Úplný příklad na stranách služby a klienta najdete v tématu [asynchronní](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).  
  
### <a name="implement-a-service-operation-asynchronously"></a>Asynchronní implementace operace služby  
  
1. V kontraktu služby deklarujte dvojici asynchronních metod podle pokynů pro asynchronní návrh .NET. `Begin`Metoda přebírá parametr, objekt zpětného volání a objekt stavu a vrací a <xref:System.IAsyncResult?displayProperty=nameWithType> odpovídající `End` metodu, která přebírá <xref:System.IAsyncResult?displayProperty=nameWithType> a vrací vrácenou hodnotu. Další informace o asynchronních voláních naleznete v tématu [asynchronní programování vzory návrhu](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  
  
2. Označte `Begin` metodu dvojice asynchronních metod s <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> atributem a nastavte <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> vlastnost na hodnotu `true` . Například následující kód provádí kroky 1 a 2.  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3. Implementujte `Begin/End` dvojici metod ve třídě služby podle pokynů pro asynchronní návrh. Například následující příklad kódu ukazuje implementaci, ve které je řetězec zapsán do konzoly v `Begin` částech a v rámci `End` asynchronní operace služby a návratovou hodnotou `End` operace je vrácen klientovi. Úplný příklad kódu naleznete v části příklad.  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a>Příklad  
 Následující příklady kódu ukazují:  
  
1. Rozhraní kontraktu služby s:  
  
    1. Synchronní `SampleMethod` operace.  
  
    2. Asynchronní `BeginSampleMethod` operace.  
  
    3. Dvojice asynchronních `BeginServiceAsyncMethod` / `EndServiceAsyncMethod` operací.  
  
2. Implementace služby pomocí <xref:System.IAsyncResult?displayProperty=nameWithType> objektu.  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Navrhování kontraktů služby](designing-service-contracts.md)
- [Synchronní a asynchronní operace](synchronous-and-asynchronous-operations.md)
