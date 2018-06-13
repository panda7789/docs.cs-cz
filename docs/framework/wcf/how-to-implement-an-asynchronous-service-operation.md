---
title: 'Postupy: Implementace operace asynchronní služby'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: b8e6ce386dc122ba059a18a448239cec7eaae222
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33500074"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a>Postupy: Implementace operace asynchronní služby
V aplikacích Windows Communication Foundation (WCF) mohou být operace služby implementovány synchronně nebo asynchronně bez diktování klientovi jejich volání. Například operace asynchronní služby můžete volání synchronně, a operací synchronní služby je možné volat asynchronně. Příklad, který ukazuje, jak asynchronní volání operace v aplikaci klienta, naleznete v části [postupy: asynchronní volání operací služby](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md). Další informace o synchronní a asynchronní operace najdete v tématu [navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md) a [synchronní a asynchronní operace](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md). Toto téma popisuje základní strukturu operace asynchronní služby, kód není úplný. Kompletní příklad, jak si služba a klient strany najdete v části [asynchronního](http://msdn.microsoft.com/library/833db946-f511-4f64-a26f-2759a11217c7).  
  
### <a name="implement-a-service-operation-asynchronously"></a>Asynchronně implementovat operaci služby  
  
1.  Ve vašem kontrakt služby deklarujte dvojici asynchronní metoda podle pokynů pro asynchronní návrh .NET. `Begin` Metoda přebírá parametr objekt zpětného volání a stavu objektu a vrátí <xref:System.IAsyncResult?displayProperty=nameWithType> a odpovídající `End` metody, která přijímá <xref:System.IAsyncResult?displayProperty=nameWithType> a vrátí návratovou hodnotu. Další informace o asynchronní volání najdete v tématu [asynchronní vzory návrhu programování](http://go.microsoft.com/fwlink/?LinkId=248221).  
  
2.  Označit `Begin` metoda pár asynchronní metody s <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> atribut a nastavte <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> vlastnost `true`. Například následující kód provede kroky 1 a 2.  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3.  Implementace `Begin/End` dvojice metody ve třídě služby podle pokynů pro asynchronní návrh. Například následující příklad kódu ukazuje implementaci, ve kterém je řetězec zapsána do konzoly v obou `Begin` a `End` části operace asynchronní služby a vrátí hodnotu, která `End` operace vrácen do klienta. Úplný příklad kódu najdete v části příklad.  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a>Příklad  
 Následující příklady kódu ukazují:  
  
1.  Rozhraní kontrakt služby s:  
  
    1.  Synchronního `SampleMethod` operaci.  
  
    2.  Asynchronní `BeginSampleMethod` operaci.  
  
    3.  Asynchronní `BeginServiceAsyncMethod` / `EndServiceAsyncMethod` pár operaci.  
  
2.  Službu pomocí implementace <xref:System.IAsyncResult?displayProperty=nameWithType> objektu.  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md)  
 [Synchronní a asynchronní operace](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
