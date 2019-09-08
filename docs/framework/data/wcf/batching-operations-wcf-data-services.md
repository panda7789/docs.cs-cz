---
title: Dávkové operace (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
ms.openlocfilehash: 2a642bdfd6a8891c54c01a07609760bede2f5d5d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780497"
---
# <a name="batching-operations-wcf-data-services"></a>Dávkové operace (WCF Data Services)
Podporuje dávkové zpracování požadavků [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]službě na základě. [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Další informace najdete v tématu [OData: Dávkové zpracování](https://go.microsoft.com/fwlink/?LinkId=186075). Každá operace, která <xref:System.Data.Services.Client.DataServiceContext>používá, jako je například provedení dotazu nebo uložení změn, vede k odeslání samostatné žádosti do datové služby. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Aby bylo možné zachovat logický rozsah pro sady operací, můžete explicitně definovat provozní dávky. Tím je zajištěno, že všechny operace v dávce budou odesílány do datové služby v rámci jedné žádosti HTTP, umožní serveru zpracovávat operace atomicky a snižuje počet přenosů dat do datové služby.  
  
## <a name="batching-query-operations"></a>Dávkování operací dotazů  
 Chcete-li v jedné dávce spustit více dotazů, je nutné vytvořit každý dotaz v dávce jako samostatnou instanci <xref:System.Data.Services.Client.DataServiceRequest%601> třídy. Při vytváření požadavku na dotaz tímto způsobem je samotný dotaz definován jako identifikátor URI a řídí se pravidly pro adresování prostředků. Další informace najdete v tématu [přístup k prostředkům datové služby](accessing-data-service-resources-wcf-data-services.md). Požadavky na dávkový dotaz jsou odesílány do datové služby při <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> volání metody, která obsahuje objekty žádosti o dotaz. Tato metoda vrátí <xref:System.Data.Services.Client.DataServiceResponse> objekt, což je <xref:System.Data.Services.Client.QueryOperationResponse%601> kolekce objektů, které reprezentují odpovědi na jednotlivé dotazy v dávce, z nichž každá obsahuje buď kolekci objektů vrácených dotazem nebo informace o chybě. V případě selhání jakékoli operace s jedním dotazem v dávce se v <xref:System.Data.Services.Client.QueryOperationResponse%601> objektu vrátí informace o chybě pro operaci, která selhala, a zbývající operace jsou stále provedeny. Další informace najdete v tématu [jak: Spouštění dotazů v dávce](how-to-execute-queries-in-a-batch-wcf-data-services.md).  
  
 Dávkové dotazy lze také provádět asynchronně. Další informace najdete v tématu [asynchronní operace](asynchronous-operations-wcf-data-services.md).  
  
## <a name="batching-the-savechanges-operation"></a>Dávkování operace SaveChanges  
 Při volání <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metody jsou všechny změny, které kontext sleduje, přeloženy do operací založených na REST, které jsou odeslány jako požadavky [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] do služby. Ve výchozím nastavení se tyto změny neodesílají v jediné zprávě požadavku. Chcete-li vyžadovat, aby všechny změny byly odeslány v jednom požadavku, je nutné <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29> zavolat metodu a zahrnout <xref:System.Data.Services.Client.SaveChangesOptions.Batch> hodnotu do <xref:System.Data.Services.Client.SaveChangesOptions> výčtu, který zadáte do metody.  
  
 Můžete také asynchronně ukládat dávkové změny. Další informace najdete v tématu [asynchronní operace](asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
