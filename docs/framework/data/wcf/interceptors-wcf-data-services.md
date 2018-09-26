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
ms.openlocfilehash: c2086d451af72157785796052af123cd210ee036
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47202721"
---
# <a name="interceptors-wcf-data-services"></a><span data-ttu-id="8e287-102">Sběrače (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="8e287-102">Interceptors (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] <span data-ttu-id="8e287-103">umožňuje aplikaci tak, že můžete přidat vlastní logiku na operaci zachycení zpráv požadavků.</span><span class="sxs-lookup"><span data-stu-id="8e287-103"> enables an application to intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="8e287-104">Můžete použít tuto vlastní logiku pro ověření dat v příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="8e287-104">You can use this custom logic to validate data in incoming messages.</span></span> <span data-ttu-id="8e287-105">Také vám pomůže ho dál omezit obor dotazu požadavku, například vložit vlastní zásady autorizace na základě žádosti.</span><span class="sxs-lookup"><span data-stu-id="8e287-105">You can also use it to further restrict the scope of a query request, such as to insert a custom authorization policy on a per request basis.</span></span>  
  
 <span data-ttu-id="8e287-106">Zachycení se provádí pomocí metody speciálně s atributy v datové služby.</span><span class="sxs-lookup"><span data-stu-id="8e287-106">Interception is performed by specially attributed methods in the data service.</span></span> <span data-ttu-id="8e287-107">Tyto metody jsou volány [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] v odpovídajícím bodě při zpracování zpráv.</span><span class="sxs-lookup"><span data-stu-id="8e287-107">These methods are called by [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] at the appropriate point in message processing.</span></span> <span data-ttu-id="8e287-108">Sběrače jsou definovány na základě sady jednotlivých entitách a metody pro zachycování nepřijímá parametry z požadavku jako servisní operace můžete.</span><span class="sxs-lookup"><span data-stu-id="8e287-108">Interceptors are defined on a per-entity set basis, and interceptor methods cannot accept parameters from the request like service operations can.</span></span> <span data-ttu-id="8e287-109">Metody zachycování dotazů, které jsou volány při zpracování požadavku HTTP GET, musí vracet výraz lambda, který určuje, zda instanci entity zachycování nastavit by měl vrátit výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="8e287-109">Query interceptor methods, which are called when processing an HTTP GET request, must return a lambda expression that determines whether an instance of the interceptor's entity set should be returned by the query results.</span></span> <span data-ttu-id="8e287-110">Tento výraz používá datové služby pro další upřesnění požadovanou operaci.</span><span class="sxs-lookup"><span data-stu-id="8e287-110">This expression is used by the data service to further refine the requested operation.</span></span> <span data-ttu-id="8e287-111">Tady je příklad definice z zachycování dotazů.</span><span class="sxs-lookup"><span data-stu-id="8e287-111">The following is an example definition of a query interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 <span data-ttu-id="8e287-112">Další informace najdete v tématu [jak na: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="8e287-112">For more information, see [How to: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="8e287-113">Změna zachycovacích dotazů, které se volají, pokud operace bez dotazů zpracování, musí vracet `void` (`Nothing` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="8e287-113">Change interceptors, which are called when processing non-query operations, must return `void` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="8e287-114">Metody pro zachycování změnu nutné přijmout následující dva parametry:</span><span class="sxs-lookup"><span data-stu-id="8e287-114">Change interceptor methods must accept the following two parameters:</span></span>  
  
1.  <span data-ttu-id="8e287-115">Parametr typu, který je kompatibilní s typem entity ze sady entit.</span><span class="sxs-lookup"><span data-stu-id="8e287-115">A parameter of a type that is compatible with the entity type of the entity set.</span></span> <span data-ttu-id="8e287-116">Když službu dat vyvolá změnu zachycování, hodnota tohoto parametru bude odrážet informací o entitách, který odeslal požadavek.</span><span class="sxs-lookup"><span data-stu-id="8e287-116">When the data service invokes the change interceptor, the value of this parameter will reflect the entity information that is sent by the request.</span></span>  
  
2.  <span data-ttu-id="8e287-117">Parametr typu <xref:System.Data.Services.UpdateOperations>.</span><span class="sxs-lookup"><span data-stu-id="8e287-117">A parameter of type <xref:System.Data.Services.UpdateOperations>.</span></span> <span data-ttu-id="8e287-118">Když službu dat vyvolá změnu zachycování, hodnota tohoto parametru bude odrážet operace, která požadavek se pokouší provést.</span><span class="sxs-lookup"><span data-stu-id="8e287-118">When the data service invokes the change interceptor, the value of this parameter will reflect the operation that the request is trying to perform.</span></span>  
  
 <span data-ttu-id="8e287-119">Následuje příklad definice z zachycování změnit.</span><span class="sxs-lookup"><span data-stu-id="8e287-119">The following is an example definition of a change interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 <span data-ttu-id="8e287-120">Další informace najdete v tématu [jak na: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="8e287-120">For more information, see [How to: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="8e287-121">Následující atributy jsou podporovány pro zachycení.</span><span class="sxs-lookup"><span data-stu-id="8e287-121">The following attributes are supported for interception.</span></span>  
  
 <span data-ttu-id="8e287-122">**[QueryInterceptor (** *EntitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="8e287-122">**[QueryInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="8e287-123">Metody s <xref:System.Data.Services.QueryInterceptorAttribute> atribut jsou volány při přijetí požadavku HTTP GET pro cílové entity sadu prostředků.</span><span class="sxs-lookup"><span data-stu-id="8e287-123">Methods with the <xref:System.Data.Services.QueryInterceptorAttribute> attribute applied are called when an HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="8e287-124">Tyto metody musí vracet vždycky, výraz lambda ve formě `Expression<Func<T,bool>>`.</span><span class="sxs-lookup"><span data-stu-id="8e287-124">These methods must always return a lambda expression in the form of `Expression<Func<T,bool>>`.</span></span>  
  
 <span data-ttu-id="8e287-125">**[ChangeInterceptor (** *EntitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="8e287-125">**[ChangeInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="8e287-126">Metody s <xref:System.Data.Services.ChangeInterceptorAttribute> atribut jsou volány při přijetí požadavku HTTP než požadavek HTTP GET pro cílové entity sadu prostředků.</span><span class="sxs-lookup"><span data-stu-id="8e287-126">Methods with the <xref:System.Data.Services.ChangeInterceptorAttribute> attribute applied are called when an HTTP request other than HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="8e287-127">Tyto metody musí vracet vždycky `void` (`Nothing` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="8e287-127">These methods must always return `void` (`Nothing` in Visual Basic).</span></span>  
  
 <span data-ttu-id="8e287-128">Další informace najdete v tématu [jak na: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="8e287-128">For more information, see [How to: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e287-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e287-129">See Also</span></span>  
 [<span data-ttu-id="8e287-130">Operace služby</span><span class="sxs-lookup"><span data-stu-id="8e287-130">Service Operations</span></span>](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)
