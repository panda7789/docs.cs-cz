---
title: Dávkování operací (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
ms.openlocfilehash: a9f74f025af6dfc5737ea9f4971f68c5ad913e8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793441"
---
# <a name="batching-operations-wcf-data-services"></a>Dávkování operací (WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Podporuje dávkové zpracování žádostí o [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]– na základě služby. Další informace najdete v tématu [OData: Dávkové zpracování](https://go.microsoft.com/fwlink/?LinkId=186075). V [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], každé operace, která se používá <xref:System.Data.Services.Client.DataServiceContext>, jako například provádění dotazu nebo uložení změn, výsledky v samostatné žádosti odesílané datové službě. Aby zůstalo zachované logické obor pro sadu operací, můžete explicitně definovat provozní dávky. Tím se zajistí, že všechny operace v dávce se odesílají do datové služby v jednom požadavku HTTP, umožňuje, aby server ke zpracování operace atomicky a snižuje počet zpátečních cest k datové službě.  
  
## <a name="batching-query-operations"></a>Dávkové zpracování operace dotazů  
 Chcete-li spustit více dotazů v jedné dávce, musíte vytvořit každý dotaz v dávce jako samostatnou instanci <xref:System.Data.Services.Client.DataServiceRequest%601> třídy. Když vytvoříte žádost o dotaz tímto způsobem, samotný dotaz je definován jako identifikátor URI a dodržuje pravidla pro adresování prostředků. Další informace najdete v tématu [přístup k prostředkům datové služby](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md). Dávkové dotazu žádosti se odesílají do data provozu, jestliže <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> metoda je volána, který obsahuje objekty dotazu požadavku. Tato metoda vrátí hodnotu <xref:System.Data.Services.Client.DataServiceResponse> objekt, což je kolekce z <xref:System.Data.Services.Client.QueryOperationResponse%601> objekty, které představují odpovědi na jednotlivé dotazy v dávce, z nichž každý obsahuje kolekci objektů vrácených podle dotazu nebo chyba informace. Při jakékoli operaci jednoho dotazu v dávce selže, informace o chybě se vrací v <xref:System.Data.Services.Client.QueryOperationResponse%601> stále provádět objektu pro operace, která selhala a zbývajících operací. Další informace najdete v tématu [jak: Provádění dotazů v dávce](../../../../docs/framework/data/wcf/how-to-execute-queries-in-a-batch-wcf-data-services.md).  
  
 Dávkové dotazy mohou být provedeny také asynchronně. Další informace najdete v tématu [asynchronních operací](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="batching-the-savechanges-operation"></a>Dávkování SaveChanges operace  
 Při volání <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda, všechny změny, které sleduje jsou přeloženy do operace REST, které se odesílají jako kontext žádosti [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby. Ve výchozím nastavení tyto změny se neodesílají do jednoho požadavku zprávy. Vyžadovat odeslání všechny změny v jedné žádosti, musí volat <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29> metoda a obsahují hodnotu <xref:System.Data.Services.Client.SaveChangesOptions.Batch> v <xref:System.Data.Services.Client.SaveChangesOptions> výčet, který zadáte do metody.  
  
 Dávkové změny můžete uložit také asynchronně. Další informace najdete v tématu [asynchronních operací](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
