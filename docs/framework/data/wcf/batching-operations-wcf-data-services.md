---
title: Dávkové operace (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
ms.openlocfilehash: 573a5fc43022e95bea81f299f461e91396f0d464
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974847"
---
# <a name="batching-operations-wcf-data-services"></a>Dávkové operace (WCF Data Services)
Protokol OData (Open Data Protocol) podporuje dávkové zpracování požadavků do služby založené na protokolu OData. Další informace najdete v tématu [OData: Batch Processing](https://go.microsoft.com/fwlink/?LinkId=186075). V [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]každá operace, která používá <xref:System.Data.Services.Client.DataServiceContext>, jako je například provedení dotazu nebo uložení změn, vede k odeslání samostatné žádosti do datové služby. Aby bylo možné zachovat logický rozsah pro sady operací, můžete explicitně definovat provozní dávky. Tím je zajištěno, že všechny operace v dávce budou odesílány do datové služby v rámci jedné žádosti HTTP, umožní serveru zpracovávat operace atomicky a snižuje počet přenosů dat do datové služby.  
  
## <a name="batching-query-operations"></a>Dávkování operací dotazů  
 Chcete-li v jedné dávce spustit více dotazů, je nutné vytvořit každý dotaz v dávce jako samostatnou instanci třídy <xref:System.Data.Services.Client.DataServiceRequest%601>. Při vytváření požadavku na dotaz tímto způsobem je samotný dotaz definován jako identifikátor URI a řídí se pravidly pro adresování prostředků. Další informace najdete v tématu [přístup k prostředkům datové služby](accessing-data-service-resources-wcf-data-services.md). Požadavky na dávkový dotaz jsou odesílány do datové služby, když je volána metoda <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A>, která obsahuje objekty žádosti o dotaz. Tato metoda vrátí objekt <xref:System.Data.Services.Client.DataServiceResponse>, což je kolekce objektů <xref:System.Data.Services.Client.QueryOperationResponse%601>, které reprezentují odpovědi na jednotlivé dotazy v dávce, z nichž každá obsahuje buď kolekci objektů vrácených dotazem nebo informace o chybě. Pokud dojde k selhání jakékoli operace s jedním dotazem v dávce, vrátí se informace o chybě v objektu <xref:System.Data.Services.Client.QueryOperationResponse%601> pro operaci, která selhala, a zbývající operace se ještě spustí. Další informace najdete v tématu [Postupy: spouštění dotazů v dávce](how-to-execute-queries-in-a-batch-wcf-data-services.md).  
  
 Dávkové dotazy lze také provádět asynchronně. Další informace najdete v tématu [asynchronní operace](asynchronous-operations-wcf-data-services.md).  
  
## <a name="batching-the-savechanges-operation"></a>Dávkování operace SaveChanges  
 Při volání metody <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> jsou všechny změny, které kontext sleduje, přeloženy do operací založených na REST, které jsou odeslány jako požadavky služby OData. Ve výchozím nastavení se tyto změny neodesílají v jediné zprávě požadavku. Chcete-li vyžadovat, aby všechny změny byly odeslány v jednom požadavku, je nutné zavolat metodu <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29> a zahrnout do výčtu <xref:System.Data.Services.Client.SaveChangesOptions> hodnotu <xref:System.Data.Services.Client.SaveChangesOptions.Batch>, kterou do metody zadáte.  
  
 Můžete také asynchronně ukládat dávkové změny. Další informace najdete v tématu [asynchronní operace](asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
