---
title: Sběrače (služby WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
ms.openlocfilehash: f3ff08dd4cd20e7ce226750a386cfddb27731923
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="interceptors-wcf-data-services"></a>Sběrače (služby WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] umožňuje aplikaci intercept zpráv žádostí, aby můžete přidat vlastní logiky do operace. Tato vlastní logiky můžete použít pro ověření dat v příchozí zprávy. Můžete ji použít i další omezit obor dotazu požadavku, jako třeba vložit vlastní zásady autorizace na základě žádosti.  
  
 Zachycení provádí speciálně s atributy metody ve službě data. Tyto metody jsou volány [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] v odpovídajícím bodě v zpracování zprávy. Sběrače jsou definovány na základě sady za entity, a metody interceptoru nemůže přijímat parametry z požadavku jako operací služby můžete. Metody interceptoru dotazů, které se nazývají při zpracování požadavku HTTP GET, musí vrátit, že má být vrácen výrazu lambda, která určuje, zda instanci entity lze sběrač nastavit podle výsledků dotazu. Tento výraz se používá služba data pro další upřesnění požadovanou operaci. Toto je definici příklad interceptoru dotazu.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 Další informace najdete v tématu [postupy: zachycení datových služba zpráv](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
 Sběrače změny, které se nazývají při zpracování operace bez dotazů, musí vracet `void` (`Nothing` v jazyce Visual Basic). Změna metody interceptoru musí přijmout tyto dva parametry:  
  
1.  Parametr typu, který je kompatibilní s typem entity sady entit. Když služba dat vyvolá zachycování dotazů, hodnota tohoto parametru se projeví informace entity, který odeslal požadavek.  
  
2.  Parametr typu <xref:System.Data.Services.UpdateOperations>. Když služba dat vyvolá zachycování dotazů, hodnota tohoto parametru bude odrážet operaci, která se při pokusu o provedení je v požadavku.  
  
 Toto je definici příklad interceptoru změnu.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 Další informace najdete v tématu [postupy: zachycení datových služba zpráv](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
 Následující atributy jsou podporovány pro zachycení.  
  
 **[QueryInterceptor (** *EnitySetName* **)]**  
 Metody s <xref:System.Data.Services.QueryInterceptorAttribute> atribut použitý jsou volány při přijetí žádosti HTTP GET pro cílové entity nastavení prostředku. Tyto metody musí vracet vždycky výrazu lambda ve formě `Expression<Func<T,bool>>`.  
  
 **[ChangeInterceptor (** *EnitySetName* **)]**  
 Metody s <xref:System.Data.Services.ChangeInterceptorAttribute> atribut použitý jsou volány při přijetí požadavku HTTP než GET protokolu HTTP žádosti pro cílové entity nastavení prostředku. Tyto metody musí vracet vždycky `void` (`Nothing` v jazyce Visual Basic).  
  
 Další informace najdete v tématu [postupy: zachycení datových služba zpráv](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Operace služby](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)
