---
title: 'Postupy: Zachytávání zpráv datových služeb (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: 24b9df1b-b54b-4795-a033-edf333675de6
ms.openlocfilehash: cecfdd74779e3ab1c908957afac3c9fccf79f383
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780033"
---
# <a name="how-to-intercept-data-service-messages-wcf-data-services"></a>Postupy: Zachytávání zpráv datových služeb (WCF Data Services)
Pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]můžete zachytit zprávy s požadavkem, abyste mohli přidat vlastní logiku k operaci. Chcete-li zachytit zprávu, použijte v datové službě speciálně používané metody s atributy. Další informace naleznete v tématu [zachycení](interceptors-wcf-data-services.md).  
  
 Příklad v tomto tématu používá ukázkovou datovou službu Northwind. Tato služba se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
### <a name="to-define-a-query-interceptor-for-the-orders-entity-set"></a>Definování zachycování dotazů pro sadu entit objednávky  
  
1. V projektu datové služby Northwind otevřete soubor Northwind. svc.  
  
2. Na kódové stránce `Northwind` třídy přidejte následující `using` příkaz (`Imports` v Visual Basic).  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3. Ve třídě Definujte metodu operace služby s názvem `OnQueryOrders` následujícím způsobem: `Northwind`  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### <a name="to-define-a-change-interceptor-for-the-products-entity-set"></a>Definování zachytávací pro sadu entit produktů  
  
1. V projektu datové služby Northwind otevřete soubor Northwind. svc.  
  
2. Ve třídě Definujte metodu operace služby s názvem `OnChangeProducts` následujícím způsobem: `Northwind`  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## <a name="example"></a>Příklad  
 Tento příklad definuje metodu pro zachycování dotazů pro `Orders` sadu entit, která vrací výraz lambda. Tento výraz obsahuje delegáta, který filtruje požadovaný `Orders` název na základě `Customers` souvisejícího názvu kontaktu. Název se pak určí na základě žádajícího uživatele. V tomto příkladu se předpokládá, že je datová služba hostovaná v ASP.NET webové aplikaci, která používá WCF a toto ověřování je povolené. <xref:System.Web.HttpContext> Třída se používá k načtení principu aktuální žádosti.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## <a name="example"></a>Příklad  
 Tento příklad definuje metodu pro zachycování pro `Products` sadu entit. Tato metoda ověřuje vstup služby pro <xref:System.Data.Services.UpdateOperations.Add> operaci nebo <xref:System.Data.Services.UpdateOperations.Change> a vyvolá výjimku, pokud se změní na zastavený produkt. Také blokuje odstraňování produktů jako nepodporovanou operaci.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Definovat operaci služby](how-to-define-a-service-operation-wcf-data-services.md)
- [Definování datových služeb WCF Data Services](defining-wcf-data-services.md)
