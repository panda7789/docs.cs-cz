---
title: Dávkování operací (služby WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
ms.openlocfilehash: 5284d1a3c2ea95e26eddd9c5617f09f299bda4f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357858"
---
# <a name="batching-operations-wcf-data-services"></a>Dávkování operací (služby WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Podporuje dávkové zpracování žádostí o [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]– na základě služby. Další informace najdete v tématu [OData: dávkové zpracování](http://go.microsoft.com/fwlink/?LinkId=186075). V [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], každou operaci, která používá <xref:System.Data.Services.Client.DataServiceContext>, jako jsou například provádění dotazu nebo uložení změn, výsledkem samostatné žádosti odesílány ke službě data. Aby byla zachována logické obor pro sady operací, můžete definovat explicitně provozní dávky. To zajistí, že všechny operace v dávce se odesílají do služby data v jednom požadavku HTTP, umožňuje, aby server ke zpracování operace atomicky a snižuje počet zpátečních cest k službě data.  
  
## <a name="batching-query-operations"></a>Dávkování operace dotazů  
 K provedení více dotazů v jedné dávce, musíte vytvořit každý dotaz v dávce jako samostatnou instanci <xref:System.Data.Services.Client.DataServiceRequest%601> třídy. Když vytvoříte žádost o dotazu tímto způsobem, samotný dotaz je definován jako identifikátor URI a postupuje pravidla pro přiřazování prostředků. Další informace najdete v tématu [přístup k prostředkům služby Data](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md). Dávkové dotaz požadavky se odesílají do data služby, kdy <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> metoda je volána, který obsahuje objekty dotazu požadavku. Tato metoda vrátí hodnotu <xref:System.Data.Services.Client.DataServiceResponse> objekt, který je kolekce z <xref:System.Data.Services.Client.QueryOperationResponse%601> objekty, které představují odpovědi na jednotlivé dotazy v dávce, z nichž každý obsahuje buď na kolekci objektů vrácené informace o dotazu nebo chyba. Pokud všechny jeden dotaz operace v dávce selže, informace o chybě je vrácený v <xref:System.Data.Services.Client.QueryOperationResponse%601> stále provádět objekt pro operaci, která se nezdařila a zbývajících operací. Další informace najdete v tématu [postup: provedení dotazy v dávce](../../../../docs/framework/data/wcf/how-to-execute-queries-in-a-batch-wcf-data-services.md).  
  
 Dávkové dotazy mohou být spouštěny také asynchronně. Další informace najdete v tématu [asynchronních operací](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="batching-the-savechanges-operation"></a>Dávkování SaveChanges operaci  
 Při volání <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> metoda, všechny změny, které sleduje jsou převedeny na bázi REST operace, které se odesílají jako kontext žádosti [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby. Ve výchozím nastavení nejsou v jedné žádosti zprávě zasláno tyto změny. Pokud chcete vyžadovat, aby odeslat všechny změny v jedné žádosti, musí volat <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29> metoda a obsahují hodnotu <xref:System.Data.Services.Client.SaveChangesOptions.Batch> v <xref:System.Data.Services.Client.SaveChangesOptions> výčet, který zadáte do metody.  
  
 Dávkové změny můžete uložit také asynchronně. Další informace najdete v tématu [asynchronních operací](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
