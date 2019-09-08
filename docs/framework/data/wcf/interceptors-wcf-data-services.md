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
# <a name="interceptors-wcf-data-services"></a><span data-ttu-id="39919-102">Zachycení (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="39919-102">Interceptors (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="39919-103">umožňuje aplikaci zachytit zprávy požadavku, abyste mohli přidat vlastní logiku k operaci.</span><span class="sxs-lookup"><span data-stu-id="39919-103">enables an application to intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="39919-104">Pomocí této vlastní logiky můžete ověřovat data v příchozích zprávách.</span><span class="sxs-lookup"><span data-stu-id="39919-104">You can use this custom logic to validate data in incoming messages.</span></span> <span data-ttu-id="39919-105">Můžete ji také použít k dalšímu omezení rozsahu požadavku na dotaz, jako je například vložení vlastní zásady autorizace na jednotlivé požadavky.</span><span class="sxs-lookup"><span data-stu-id="39919-105">You can also use it to further restrict the scope of a query request, such as to insert a custom authorization policy on a per request basis.</span></span>  
  
 <span data-ttu-id="39919-106">Zachycení se provádí pomocí metod, které jsou v datové službě speciálně s atributy.</span><span class="sxs-lookup"><span data-stu-id="39919-106">Interception is performed by specially attributed methods in the data service.</span></span> <span data-ttu-id="39919-107">Tyto metody jsou volány [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] v příslušném bodě zpracování zprávy.</span><span class="sxs-lookup"><span data-stu-id="39919-107">These methods are called by [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] at the appropriate point in message processing.</span></span> <span data-ttu-id="39919-108">Zachycení jsou definovaná na základě sady pro každou entitu a metody pro zachycování nemůžou přijímat parametry ze žádosti, jako je například operace služby.</span><span class="sxs-lookup"><span data-stu-id="39919-108">Interceptors are defined on a per-entity set basis, and interceptor methods cannot accept parameters from the request like service operations can.</span></span> <span data-ttu-id="39919-109">Metody pro zachycování dotazů, které jsou volány při zpracování požadavku HTTP GET, musí vracet výraz lambda, který určuje, zda by měla být instance sady entit zachytávací vrácena pomocí výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="39919-109">Query interceptor methods, which are called when processing an HTTP GET request, must return a lambda expression that determines whether an instance of the interceptor's entity set should be returned by the query results.</span></span> <span data-ttu-id="39919-110">Tento výraz používá datová služba k dalšímu upřesnění požadované operace.</span><span class="sxs-lookup"><span data-stu-id="39919-110">This expression is used by the data service to further refine the requested operation.</span></span> <span data-ttu-id="39919-111">Následuje příklad definice zachycování dotazů.</span><span class="sxs-lookup"><span data-stu-id="39919-111">The following is an example definition of a query interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 <span data-ttu-id="39919-112">Další informace najdete v tématu [jak: Zachyťte zprávy](how-to-intercept-data-service-messages-wcf-data-services.md)datové služby.</span><span class="sxs-lookup"><span data-stu-id="39919-112">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="39919-113">Zachycení změn, které jsou volány při zpracování operací bez dotazů, musí vracet `void` (`Nothing` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="39919-113">Change interceptors, which are called when processing non-query operations, must return `void` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="39919-114">Metody Change zachytávací musí přijmout následující dva parametry:</span><span class="sxs-lookup"><span data-stu-id="39919-114">Change interceptor methods must accept the following two parameters:</span></span>  
  
1. <span data-ttu-id="39919-115">Parametr typu, který je kompatibilní s typem entity sady entit.</span><span class="sxs-lookup"><span data-stu-id="39919-115">A parameter of a type that is compatible with the entity type of the entity set.</span></span> <span data-ttu-id="39919-116">Když datová služba vyvolá zachytávací zachytávací, hodnota tohoto parametru bude odpovídat informacím v entitě, které odesílá požadavek.</span><span class="sxs-lookup"><span data-stu-id="39919-116">When the data service invokes the change interceptor, the value of this parameter will reflect the entity information that is sent by the request.</span></span>  
  
2. <span data-ttu-id="39919-117">Parametr typu <xref:System.Data.Services.UpdateOperations>.</span><span class="sxs-lookup"><span data-stu-id="39919-117">A parameter of type <xref:System.Data.Services.UpdateOperations>.</span></span> <span data-ttu-id="39919-118">Když datová služba vyvolá zachytávací modul pro změnu, hodnota tohoto parametru se projeví v operaci, kterou se požadavek pokouší provést.</span><span class="sxs-lookup"><span data-stu-id="39919-118">When the data service invokes the change interceptor, the value of this parameter will reflect the operation that the request is trying to perform.</span></span>  
  
 <span data-ttu-id="39919-119">Následuje příklad definice zachytávací.</span><span class="sxs-lookup"><span data-stu-id="39919-119">The following is an example definition of a change interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 <span data-ttu-id="39919-120">Další informace najdete v tématu [jak: Zachyťte zprávy](how-to-intercept-data-service-messages-wcf-data-services.md)datové služby.</span><span class="sxs-lookup"><span data-stu-id="39919-120">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="39919-121">Následující atributy jsou podporovány pro zachycení.</span><span class="sxs-lookup"><span data-stu-id="39919-121">The following attributes are supported for interception.</span></span>  
  
 <span data-ttu-id="39919-122">**[QueryInterceptor(** *EntitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="39919-122">**[QueryInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="39919-123">Metody s <xref:System.Data.Services.QueryInterceptorAttribute> použitým atributem jsou volány, když je přijat požadavek HTTP GET pro prostředek cílové sady entit.</span><span class="sxs-lookup"><span data-stu-id="39919-123">Methods with the <xref:System.Data.Services.QueryInterceptorAttribute> attribute applied are called when an HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="39919-124">Tyto metody musí vždycky vracet lambda výraz ve formě `Expression<Func<T,bool>>`.</span><span class="sxs-lookup"><span data-stu-id="39919-124">These methods must always return a lambda expression in the form of `Expression<Func<T,bool>>`.</span></span>  
  
 <span data-ttu-id="39919-125">**[ChangeInterceptor(** *EntitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="39919-125">**[ChangeInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="39919-126">Metody s <xref:System.Data.Services.ChangeInterceptorAttribute> použitým atributem jsou volány, když je přijat požadavek HTTP jiný než požadavek HTTP GET pro prostředek cílové sady entit.</span><span class="sxs-lookup"><span data-stu-id="39919-126">Methods with the <xref:System.Data.Services.ChangeInterceptorAttribute> attribute applied are called when an HTTP request other than HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="39919-127">Tyto metody musí vždycky vracet `void` (`Nothing` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="39919-127">These methods must always return `void` (`Nothing` in Visual Basic).</span></span>  
  
 <span data-ttu-id="39919-128">Další informace najdete v tématu [jak: Zachyťte zprávy](how-to-intercept-data-service-messages-wcf-data-services.md)datové služby.</span><span class="sxs-lookup"><span data-stu-id="39919-128">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39919-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="39919-129">See also</span></span>

- [<span data-ttu-id="39919-130">Operace služby</span><span class="sxs-lookup"><span data-stu-id="39919-130">Service Operations</span></span>](service-operations-wcf-data-services.md)
