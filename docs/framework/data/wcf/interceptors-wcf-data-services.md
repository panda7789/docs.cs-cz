---
title: Sběrače (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
ms.openlocfilehash: 17926e144fae206d702c2bcb4f88dd2093442ed5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61876223"
---
# <a name="interceptors-wcf-data-services"></a>Sběrače (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] umožňuje aplikaci tak, že můžete přidat vlastní logiku na operaci zachycení zpráv požadavků. Můžete použít tuto vlastní logiku pro ověření dat v příchozí zprávy. Také vám pomůže ho dál omezit obor dotazu požadavku, například vložit vlastní zásady autorizace na základě žádosti.  
  
 Zachycení se provádí pomocí metody speciálně s atributy v datové služby. Tyto metody jsou volány [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] v odpovídajícím bodě při zpracování zpráv. Sběrače jsou definovány na základě sady jednotlivých entitách a metody pro zachycování nepřijímá parametry z požadavku jako servisní operace můžete. Metody zachycování dotazů, které jsou volány při zpracování požadavku HTTP GET, musí vracet výraz lambda, který určuje, zda instanci entity zachycování nastavit by měl vrátit výsledky dotazu. Tento výraz používá datové služby pro další upřesnění požadovanou operaci. Tady je příklad definice z zachycování dotazů.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 Další informace najdete v tématu [jak: Zachycování zpráv datové služby](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
 Změna zachycovacích dotazů, které se volají, pokud operace bez dotazů zpracování, musí vracet `void` (`Nothing` v jazyce Visual Basic). Metody pro zachycování změnu nutné přijmout následující dva parametry:  
  
1. Parametr typu, který je kompatibilní s typem entity ze sady entit. Když službu dat vyvolá změnu zachycování, hodnota tohoto parametru bude odrážet informací o entitách, který odeslal požadavek.  
  
2. Parametr typu <xref:System.Data.Services.UpdateOperations>. Když službu dat vyvolá změnu zachycování, hodnota tohoto parametru bude odrážet operace, která požadavek se pokouší provést.  
  
 Následuje příklad definice z zachycování změnit.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 Další informace najdete v tématu [jak: Zachycování zpráv datové služby](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
 Následující atributy jsou podporovány pro zachycení.  
  
 **[QueryInterceptor(** *EntitySetName* **)]**  
 Metody s <xref:System.Data.Services.QueryInterceptorAttribute> atribut jsou volány při přijetí požadavku HTTP GET pro cílové entity sadu prostředků. Tyto metody musí vracet vždycky, výraz lambda ve formě `Expression<Func<T,bool>>`.  
  
 **[ChangeInterceptor(** *EntitySetName* **)]**  
 Metody s <xref:System.Data.Services.ChangeInterceptorAttribute> atribut jsou volány při přijetí požadavku HTTP než požadavek HTTP GET pro cílové entity sadu prostředků. Tyto metody musí vracet vždycky `void` (`Nothing` v jazyce Visual Basic).  
  
 Další informace najdete v tématu [jak: Zachycování zpráv datové služby](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Operace služby](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)
