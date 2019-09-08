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
ms.openlocfilehash: 7decfdd738e71a01afa8cb32604953142b46e588
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790436"
---
# <a name="interceptors-wcf-data-services"></a>Zachycení (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umožňuje aplikaci zachytit zprávy požadavku, abyste mohli přidat vlastní logiku k operaci. Pomocí této vlastní logiky můžete ověřovat data v příchozích zprávách. Můžete ji také použít k dalšímu omezení rozsahu požadavku na dotaz, jako je například vložení vlastní zásady autorizace na jednotlivé požadavky.  
  
 Zachycení se provádí pomocí metod, které jsou v datové službě speciálně s atributy. Tyto metody jsou volány [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] v příslušném bodě zpracování zprávy. Zachycení jsou definovaná na základě sady pro každou entitu a metody pro zachycování nemůžou přijímat parametry ze žádosti, jako je například operace služby. Metody pro zachycování dotazů, které jsou volány při zpracování požadavku HTTP GET, musí vracet výraz lambda, který určuje, zda by měla být instance sady entit zachytávací vrácena pomocí výsledků dotazu. Tento výraz používá datová služba k dalšímu upřesnění požadované operace. Následuje příklad definice zachycování dotazů.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 Další informace najdete v tématu [jak: Zachyťte zprávy](how-to-intercept-data-service-messages-wcf-data-services.md)datové služby.  
  
 Zachycení změn, které jsou volány při zpracování operací bez dotazů, musí vracet `void` (`Nothing` v Visual Basic). Metody Change zachytávací musí přijmout následující dva parametry:  
  
1. Parametr typu, který je kompatibilní s typem entity sady entit. Když datová služba vyvolá zachytávací zachytávací, hodnota tohoto parametru bude odpovídat informacím v entitě, které odesílá požadavek.  
  
2. Parametr typu <xref:System.Data.Services.UpdateOperations>. Když datová služba vyvolá zachytávací modul pro změnu, hodnota tohoto parametru se projeví v operaci, kterou se požadavek pokouší provést.  
  
 Následuje příklad definice zachytávací.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 Další informace najdete v tématu [jak: Zachyťte zprávy](how-to-intercept-data-service-messages-wcf-data-services.md)datové služby.  
  
 Následující atributy jsou podporovány pro zachycení.  
  
 **[QueryInterceptor(** *EntitySetName* **)]**  
 Metody s <xref:System.Data.Services.QueryInterceptorAttribute> použitým atributem jsou volány, když je přijat požadavek HTTP GET pro prostředek cílové sady entit. Tyto metody musí vždycky vracet lambda výraz ve formě `Expression<Func<T,bool>>`.  
  
 **[ChangeInterceptor(** *EntitySetName* **)]**  
 Metody s <xref:System.Data.Services.ChangeInterceptorAttribute> použitým atributem jsou volány, když je přijat požadavek HTTP jiný než požadavek HTTP GET pro prostředek cílové sady entit. Tyto metody musí vždycky vracet `void` (`Nothing` v Visual Basic).  
  
 Další informace najdete v tématu [jak: Zachyťte zprávy](how-to-intercept-data-service-messages-wcf-data-services.md)datové služby.  
  
## <a name="see-also"></a>Viz také:

- [Operace služby](service-operations-wcf-data-services.md)
