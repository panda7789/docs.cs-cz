---
title: Zachycení (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
ms.openlocfilehash: c9799037ae0ea8b29b5e989859aff29c310593d4
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568972"
---
# <a name="interceptors-wcf-data-services"></a>Zachycení (WCF Data Services)
WCF Data Services umožňuje aplikaci zachytit zprávy požadavků, abyste mohli přidat vlastní logiku k operaci. Pomocí této vlastní logiky můžete ověřovat data v příchozích zprávách. Můžete ji také použít k dalšímu omezení rozsahu požadavku na dotaz, jako je například vložení vlastní zásady autorizace na jednotlivé požadavky.  
  
 Zachycení se provádí pomocí metod, které jsou v datové službě speciálně s atributy. Tyto metody jsou volány WCF Data Services v příslušném bodě zpracování zprávy. Zachycení jsou definovaná na základě sady pro každou entitu a metody pro zachycování nemůžou přijímat parametry ze žádosti, jako je například operace služby. Metody pro zachycování dotazů, které jsou volány při zpracování požadavku HTTP GET, musí vracet výraz lambda, který určuje, zda by měla být instance sady entit zachytávací vrácena pomocí výsledků dotazu. Tento výraz používá datová služba k dalšímu upřesnění požadované operace. Následuje příklad definice zachycování dotazů.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 Další informace najdete v tématu [Postup: zachycení zpráv datových služeb](how-to-intercept-data-service-messages-wcf-data-services.md).  
  
 Zachycení změn, které jsou volány při zpracování operací bez dotazů, musí vracet `void` (`Nothing` v Visual Basic). Metody Change zachytávací musí přijmout následující dva parametry:  
  
1. Parametr typu, který je kompatibilní s typem entity sady entit. Když datová služba vyvolá zachytávací zachytávací, hodnota tohoto parametru bude odpovídat informacím v entitě, které odesílá požadavek.  
  
2. Parametr typu <xref:System.Data.Services.UpdateOperations>. Když datová služba vyvolá zachytávací modul pro změnu, hodnota tohoto parametru se projeví v operaci, kterou se požadavek pokouší provést.  
  
 Následuje příklad definice zachytávací.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 Další informace najdete v tématu [Postup: zachycení zpráv datových služeb](how-to-intercept-data-service-messages-wcf-data-services.md).  
  
 Následující atributy jsou podporovány pro zachycení.  
  
 **[QueryInterceptor (** *EntitySetName* **)]**  
 Metody s aplikovaným atributem <xref:System.Data.Services.QueryInterceptorAttribute> se nazývají při přijetí požadavku HTTP GET pro prostředek cílové sady entit. Tyto metody musí vždycky vracet lambda výraz ve formě `Expression<Func<T,bool>>`.  
  
 **[ChangeInterceptor (** *EntitySetName* **)]**  
 Metody s aplikovaným atributem <xref:System.Data.Services.ChangeInterceptorAttribute> jsou volány, když je přijat požadavek HTTP jiný než požadavek HTTP GET pro prostředek cílové sady entit. Tyto metody musí vždycky vracet `void` (`Nothing` v Visual Basic).  
  
 Další informace najdete v tématu [Postup: zachycení zpráv datových služeb](how-to-intercept-data-service-messages-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Operace služby](service-operations-wcf-data-services.md)
