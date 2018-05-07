---
title: 'Postupy: zachycení datových služba zpráv (služby WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: 24b9df1b-b54b-4795-a033-edf333675de6
ms.openlocfilehash: 9d79a9ca27470512105b3a04d681906aa365d7e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-intercept-data-service-messages-wcf-data-services"></a>Postupy: zachycení datových služba zpráv (služby WCF Data Services)
S [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], tak, aby můžete přidat vlastní logiky do operace je možné zachytit zprávy žádosti. K zachycení zprávy, použijete speciálně s atributy metody ve službě data. Další informace najdete v tématu [sběrače](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).  
  
 Příklad v tomto tématu používá službu Northwind ukázková data. Tato služba se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-define-a-query-interceptor-for-the-orders-entity-set"></a>Chcete-li definovat interceptoru dotazu pro sadu entit objednávky  
  
1.  V projektu služby Northwind data otevřete soubor Northwind.svc.  
  
2.  V kódové stránky pro `Northwind` třídy, přidejte následující `using` – příkaz (`Imports` v jazyce Visual Basic).  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3.  V `Northwind` třídy, definování metody operace služby s názvem `OnQueryOrders` následujícím způsobem:  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### <a name="to-define-a-change-interceptor-for-the-products-entity-set"></a>Chcete-li definovat Změna interceptoru pro sadu entit produkty  
  
1.  V projektu služby Northwind data otevřete soubor Northwind.svc.  
  
2.  V `Northwind` třídy, definování metody operace služby s názvem `OnChangeProducts` následujícím způsobem:  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## <a name="example"></a>Příklad  
 Tento příklad definuje metodu interceptoru dotaz `Orders` sady entit, který vrací výraz lambda. Tento výraz obsahuje delegáta, který filtruje požadované `Orders` podle související `Customers` mají konkrétní jméno kontaktní osoby. Název je zase určen na základě žádajícího uživatele. Tento příklad předpokládá, že je služba data hostovaným v rámci ASP.NET – webové aplikace, která používá WCF a je povolen, ověření. <xref:System.Web.HttpContext> Třída se používá k načtení Princip aktuální žádosti.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## <a name="example"></a>Příklad  
 Tento příklad definuje metodu interceptoru změn `Products` sady entit. Tato metoda ověří vstup se službou pro <xref:System.Data.Services.UpdateOperations.Add> nebo <xref:System.Data.Services.UpdateOperations.Change> operace a vyvolá výjimku, je-li ke změně je odeslána na deaktivovaný produkt. Blokuje taky odstranění produkty jako nepodporovanou operaci.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Definování operace služby](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md)  
 [Definování datových služeb WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
