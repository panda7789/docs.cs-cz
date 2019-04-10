---
title: 'Postupy: Zachycování zpráv datové služby (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: 24b9df1b-b54b-4795-a033-edf333675de6
ms.openlocfilehash: a11334abc83db20bec06fd2459d7b8598f672f2f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317477"
---
# <a name="how-to-intercept-data-service-messages-wcf-data-services"></a>Postupy: Zachycování zpráv datové služby (WCF Data Services)
S [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], tak, že můžete přidat vlastní logiku na operaci je možné zachytit zprávy s požadavkem. Aby se zachytily zprávu, použijte metody speciálně s atributy v datové služby. Další informace najdete v tématu [sběrače](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind. Tato služba se vytvoří při dokončení [rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-define-a-query-interceptor-for-the-orders-entity-set"></a>Chcete-li definovat zachycování dotazů pro sadu entit objednávky  
  
1. V projektu služby Northwind data otevřete soubor Northwind.svc.  
  
2. Na stránce kódu `Northwind` třídy, přidejte následující `using` – příkaz (`Imports` v jazyce Visual Basic).  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3. V `Northwind` tříd, definice služby operace metodu s názvem `OnQueryOrders` následujícím způsobem:  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### <a name="to-define-a-change-interceptor-for-the-products-entity-set"></a>Chcete-li definovat zachycování změnu pro sadu entit produkty  
  
1. V projektu služby Northwind data otevřete soubor Northwind.svc.  
  
2. V `Northwind` tříd, definice služby operace metodu s názvem `OnChangeProducts` následujícím způsobem:  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## <a name="example"></a>Příklad  
 Tento příklad definuje metodu pro zachycování dotazů `Orders` sadu entit, který vrací výraz lambda. Tento výraz obsahuje delegáta, který filtruje požadovanou `Orders` podle související `Customers` , které mají konkrétní jméno kontaktu. Název pak závisí na žádajícího uživatele. Tento příklad předpokládá, že datové služby je hostovaná ve webové aplikaci ASP.NET, která používá WCF a že ověřování je povoleno. <xref:System.Web.HttpContext> Třída se používá k načtení Princip aktuálního požadavku.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## <a name="example"></a>Příklad  
 Tento příklad definuje metoda pro zachycování dotazů pro `Products` sady entit. Tato metoda ověřuje vstup do služby pro <xref:System.Data.Services.UpdateOperations.Add> nebo <xref:System.Data.Services.UpdateOperations.Change> operace a vyvolá výjimku, pokud je se provede změna ukončená produktu. Blokuje taky odstranění produkty jako nepodporovaná operace.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Definování operace služby](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md)
- [Definování datových služeb WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
