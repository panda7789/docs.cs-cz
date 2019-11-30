---
title: 'Postupy: zachycení zpráv datových služeb (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: 24b9df1b-b54b-4795-a033-edf333675de6
ms.openlocfilehash: 4f2d6cf34c820c60181d5287298898af5eb8d038
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569034"
---
# <a name="how-to-intercept-data-service-messages-wcf-data-services"></a>Postupy: zachycení zpráv datových služeb (WCF Data Services)
Pomocí WCF Data Services můžete zachytit zprávy s požadavkem, abyste mohli přidat vlastní logiku k operaci. Chcete-li zachytit zprávu, použijte v datové službě speciálně používané metody s atributy. Další informace naleznete v tématu [zachycení](interceptors-wcf-data-services.md).  
  
 Příklad v tomto tématu používá ukázkovou datovou službu Northwind. Tato služba se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
### <a name="to-define-a-query-interceptor-for-the-orders-entity-set"></a>Definování zachycování dotazů pro sadu entit objednávky  
  
1. V projektu datové služby Northwind otevřete soubor Northwind. svc.  
  
2. Na kódové stránce pro třídu `Northwind` přidejte následující příkaz `using` (`Imports` v Visual Basic).  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3. Ve třídě `Northwind` Definujte metodu operace služby s názvem `OnQueryOrders` následujícím způsobem:  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### <a name="to-define-a-change-interceptor-for-the-products-entity-set"></a>Definování zachytávací pro sadu entit produktů  
  
1. V projektu datové služby Northwind otevřete soubor Northwind. svc.  
  
2. Ve třídě `Northwind` Definujte metodu operace služby s názvem `OnChangeProducts` následujícím způsobem:  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## <a name="example"></a>Příklad  
 Tento příklad definuje metodu zachycování dotazů pro sadu entit `Orders`, která vrací výraz lambda. Tento výraz obsahuje delegáta, který filtruje požadované `Orders` na základě souvisejících `Customers`, které mají konkrétní název kontaktu. Název se pak určí na základě žádajícího uživatele. V tomto příkladu se předpokládá, že je datová služba hostovaná v ASP.NET webové aplikaci, která používá WCF a toto ověřování je povolené. Třída <xref:System.Web.HttpContext> slouží k načtení principu aktuální žádosti.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## <a name="example"></a>Příklad  
 Tento příklad definuje metodu pro zachycování `Products` entit pro sadu entit. Tato metoda ověřuje vstup služby pro operaci <xref:System.Data.Services.UpdateOperations.Add> nebo <xref:System.Data.Services.UpdateOperations.Change> a vyvolá výjimku, pokud se změní na zastavený produkt. Také blokuje odstraňování produktů jako nepodporovanou operaci.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Definování operace služby](how-to-define-a-service-operation-wcf-data-services.md)
- [Definování datových služeb WCF Data Services](defining-wcf-data-services.md)
