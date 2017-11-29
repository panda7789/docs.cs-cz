---
title: "Sběrače (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7aad516b819723c97a40a016a46ddcbe0fcdf4d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="interceptors-wcf-data-services"></a><span data-ttu-id="41c3e-102">Sběrače (služby WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="41c3e-102">Interceptors (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="41c3e-103">umožňuje aplikaci intercept zpráv žádostí, aby můžete přidat vlastní logiky do operace.</span><span class="sxs-lookup"><span data-stu-id="41c3e-103"> enables an application to intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="41c3e-104">Tato vlastní logiky můžete použít pro ověření dat v příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="41c3e-104">You can use this custom logic to validate data in incoming messages.</span></span> <span data-ttu-id="41c3e-105">Můžete ji použít i další omezit obor dotazu požadavku, jako třeba vložit vlastní zásady autorizace na základě žádosti.</span><span class="sxs-lookup"><span data-stu-id="41c3e-105">You can also use it to further restrict the scope of a query request, such as to insert a custom authorization policy on a per request basis.</span></span>  
  
 <span data-ttu-id="41c3e-106">Zachycení provádí speciálně s atributy metody ve službě data.</span><span class="sxs-lookup"><span data-stu-id="41c3e-106">Interception is performed by specially attributed methods in the data service.</span></span> <span data-ttu-id="41c3e-107">Tyto metody jsou volány [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] v odpovídajícím bodě v zpracování zprávy.</span><span class="sxs-lookup"><span data-stu-id="41c3e-107">These methods are called by [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] at the appropriate point in message processing.</span></span> <span data-ttu-id="41c3e-108">Sběrače jsou definovány na základě sady za entity, a metody interceptoru nemůže přijímat parametry z požadavku jako operací služby můžete.</span><span class="sxs-lookup"><span data-stu-id="41c3e-108">Interceptors are defined on a per-entity set basis, and interceptor methods cannot accept parameters from the request like service operations can.</span></span> <span data-ttu-id="41c3e-109">Metody interceptoru dotazů, které se nazývají při zpracování požadavku HTTP GET, musí vrátit, že má být vrácen výrazu lambda, která určuje, zda instanci entity lze sběrač nastavit podle výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="41c3e-109">Query interceptor methods, which are called when processing an HTTP GET request, must return a lambda expression that determines whether an instance of the interceptor's entity set should be returned by the query results.</span></span> <span data-ttu-id="41c3e-110">Tento výraz se používá služba data pro další upřesnění požadovanou operaci.</span><span class="sxs-lookup"><span data-stu-id="41c3e-110">This expression is used by the data service to further refine the requested operation.</span></span> <span data-ttu-id="41c3e-111">Toto je definici příklad interceptoru dotazu.</span><span class="sxs-lookup"><span data-stu-id="41c3e-111">The following is an example definition of a query interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 <span data-ttu-id="41c3e-112">Další informace najdete v tématu [postupy: zachycení datových služba zpráv](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="41c3e-112">For more information, see [How to: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="41c3e-113">Sběrače změny, které se nazývají při zpracování operace bez dotazů, musí vracet `void` (`Nothing` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="41c3e-113">Change interceptors, which are called when processing non-query operations, must return `void` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="41c3e-114">Změna metody interceptoru musí přijmout tyto dva parametry:</span><span class="sxs-lookup"><span data-stu-id="41c3e-114">Change interceptor methods must accept the following two parameters:</span></span>  
  
1.  <span data-ttu-id="41c3e-115">Parametr typu, který je kompatibilní s typem entity sady entit.</span><span class="sxs-lookup"><span data-stu-id="41c3e-115">A parameter of a type that is compatible with the entity type of the entity set.</span></span> <span data-ttu-id="41c3e-116">Když služba dat vyvolá zachycování dotazů, hodnota tohoto parametru se projeví informace entity, který odeslal požadavek.</span><span class="sxs-lookup"><span data-stu-id="41c3e-116">When the data service invokes the change interceptor, the value of this parameter will reflect the entity information that is sent by the request.</span></span>  
  
2.  <span data-ttu-id="41c3e-117">Parametr typu <xref:System.Data.Services.UpdateOperations>.</span><span class="sxs-lookup"><span data-stu-id="41c3e-117">A parameter of type <xref:System.Data.Services.UpdateOperations>.</span></span> <span data-ttu-id="41c3e-118">Když služba dat vyvolá zachycování dotazů, hodnota tohoto parametru bude odrážet operaci, která se při pokusu o provedení je v požadavku.</span><span class="sxs-lookup"><span data-stu-id="41c3e-118">When the data service invokes the change interceptor, the value of this parameter will reflect the operation that the request is trying to perform.</span></span>  
  
 <span data-ttu-id="41c3e-119">Toto je definici příklad interceptoru změnu.</span><span class="sxs-lookup"><span data-stu-id="41c3e-119">The following is an example definition of a change interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 <span data-ttu-id="41c3e-120">Další informace najdete v tématu [postupy: zachycení datových služba zpráv](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="41c3e-120">For more information, see [How to: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="41c3e-121">Následující atributy jsou podporovány pro zachycení.</span><span class="sxs-lookup"><span data-stu-id="41c3e-121">The following attributes are supported for interception.</span></span>  
  
 <span data-ttu-id="41c3e-122">**[QueryInterceptor (** *EnitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="41c3e-122">**[QueryInterceptor(** *EnitySetName* **)]**</span></span>  
 <span data-ttu-id="41c3e-123">Metody s <xref:System.Data.Services.QueryInterceptorAttribute> atribut použitý jsou volány při přijetí žádosti HTTP GET pro cílové entity nastavení prostředku.</span><span class="sxs-lookup"><span data-stu-id="41c3e-123">Methods with the <xref:System.Data.Services.QueryInterceptorAttribute> attribute applied are called when an HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="41c3e-124">Tyto metody musí vracet vždycky výrazu lambda ve formě `Expression<Func<T,bool>>`.</span><span class="sxs-lookup"><span data-stu-id="41c3e-124">These methods must always return a lambda expression in the form of `Expression<Func<T,bool>>`.</span></span>  
  
 <span data-ttu-id="41c3e-125">**[ChangeInterceptor (** *EnitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="41c3e-125">**[ChangeInterceptor(** *EnitySetName* **)]**</span></span>  
 <span data-ttu-id="41c3e-126">Metody s <xref:System.Data.Services.ChangeInterceptorAttribute> atribut použitý jsou volány při přijetí požadavku HTTP než GET protokolu HTTP žádosti pro cílové entity nastavení prostředku.</span><span class="sxs-lookup"><span data-stu-id="41c3e-126">Methods with the <xref:System.Data.Services.ChangeInterceptorAttribute> attribute applied are called when an HTTP request other than HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="41c3e-127">Tyto metody musí vracet vždycky `void` (`Nothing` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="41c3e-127">These methods must always return `void` (`Nothing` in Visual Basic).</span></span>  
  
 <span data-ttu-id="41c3e-128">Další informace najdete v tématu [postupy: zachycení datových služba zpráv](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="41c3e-128">For more information, see [How to: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41c3e-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="41c3e-129">See Also</span></span>  
 [<span data-ttu-id="41c3e-130">Operace služby</span><span class="sxs-lookup"><span data-stu-id="41c3e-130">Service Operations</span></span>](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)
