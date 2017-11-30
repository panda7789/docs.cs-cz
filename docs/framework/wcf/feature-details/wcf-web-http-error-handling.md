---
title: "Zpracování chyb HTTP programování webové služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3366ab851c6e6b66a5df94bdb24baad4ae0c8d14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="wcf-web-http-error-handling"></a><span data-ttu-id="95207-102">Zpracování chyb HTTP programování webové služby WCF</span><span class="sxs-lookup"><span data-stu-id="95207-102">WCF Web HTTP Error Handling</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="95207-103">Zpracování chyb webových služeb HTTP umožňuje vracet chyby z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP webové služby, které zadejte stav HTTP kód a vrátí podrobnosti o chybě používá stejný formát jako operace (například XML nebo JSON).</span><span class="sxs-lookup"><span data-stu-id="95207-103"> Web HTTP error handling enables you to return errors from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web HTTP services that specify an HTTP status code and return error details using the same format as the operation (for example, XML or JSON).</span></span>  
  
## <a name="wcf-web-http-error-handling"></a><span data-ttu-id="95207-104">Zpracování chyb HTTP programování webové služby WCF</span><span class="sxs-lookup"><span data-stu-id="95207-104">WCF Web HTTP Error Handling</span></span>  
 <span data-ttu-id="95207-105"><xref:System.ServiceModel.Web.WebFaultException> Třída definuje konstruktor, který vám umožní určit stavový kód HTTP.</span><span class="sxs-lookup"><span data-stu-id="95207-105">The <xref:System.ServiceModel.Web.WebFaultException> class defines a constructor that allows you to specify an HTTP status code.</span></span> <span data-ttu-id="95207-106">Tento kód stavu je pak vrácen do klienta.</span><span class="sxs-lookup"><span data-stu-id="95207-106">This status code is then returned to the client.</span></span> <span data-ttu-id="95207-107">Obecná verze <xref:System.ServiceModel.Web.WebFaultException> třídy, <xref:System.ServiceModel.Web.WebFaultException%601> umožní vám vrátit uživatelem definovaný typ, který obsahuje informace o této chybě, která došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="95207-107">A generic version of the <xref:System.ServiceModel.Web.WebFaultException> class, <xref:System.ServiceModel.Web.WebFaultException%601> enables you to return a user-defined type that contains information about the error that occurred.</span></span> <span data-ttu-id="95207-108">Tato vlastní objekt serializován formátu určeného operaci a vrátí klientovi.</span><span class="sxs-lookup"><span data-stu-id="95207-108">This custom object is serialized using the format specified by the operation and returned to the client.</span></span> <span data-ttu-id="95207-109">Následující příklad ukazuje, jak vrátit stavový kód HTTP.</span><span class="sxs-lookup"><span data-stu-id="95207-109">The following example shows how to return an HTTP status code.</span></span>  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 <span data-ttu-id="95207-110">Následující příklad ukazuje, jak se vrátit stavový kód HTTP a doplňující informace v uživatelsky definovaný typ.</span><span class="sxs-lookup"><span data-stu-id="95207-110">The following example shows how to return an HTTP status code and extra information in a user-defined type.</span></span> <span data-ttu-id="95207-111">`MyErrorDetail`je typ definovaný uživatelem, který obsahuje další informace o této chybě, která došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="95207-111">`MyErrorDetail` is a user-defined type that contains extra information about the error that occurred.</span></span>  
  
```  
Public string Operation2()  
   // Operation logic  
   // ...   MyErrorDetail detail = new MyErrorDetail  
   {  
      Message = "Error Message",  
      ErrorCode = 123,  
   }  
   throw new WebFaultException<MyErrorDetail>(detail, HttpStatusCode.Forbidden);  
}  
```  
  
 <span data-ttu-id="95207-112">Předchozí kód vrátí odpověď HTTP s zakázané stavový kód a text, který obsahuje instance `MyErrorDetails` objektu.</span><span class="sxs-lookup"><span data-stu-id="95207-112">The preceding code returns an HTTP response with the forbidden status code and a body that contains an instance of the `MyErrorDetails` object.</span></span> <span data-ttu-id="95207-113">Formát `MyErrorDetails` objektu je určen podle:</span><span class="sxs-lookup"><span data-stu-id="95207-113">The format of the `MyErrorDetails` object is determined by:</span></span>  
  
-   <span data-ttu-id="95207-114">Hodnota `ResponseFormat` parametr <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> atribut na operaci služby.</span><span class="sxs-lookup"><span data-stu-id="95207-114">The value of the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute specified on the service operation.</span></span>  
  
-   <span data-ttu-id="95207-115">Hodnota <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span><span class="sxs-lookup"><span data-stu-id="95207-115">The value of <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span></span>  
  
-   <span data-ttu-id="95207-116">Hodnota <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> vlastnost přímým přístupem <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span><span class="sxs-lookup"><span data-stu-id="95207-116">The value of the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property by accessing the <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="95207-117">jak tyto hodnoty ovlivňují formátování operaci, najdete v části [WCF Web HTTP formátování](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="95207-117"> how these values affect the formatting of the operation, see [WCF Web HTTP Formatting](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>  
  
 <span data-ttu-id="95207-118"><xref:System.ServiceModel.Web.WebFaultException>je <xref:System.ServiceModel.FaultException> a proto může sloužit jako programovací model selhání výjimky pro služby, které zveřejňují koncových bodů protokolu SOAP a také web koncových bodů protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="95207-118"><xref:System.ServiceModel.Web.WebFaultException> is a <xref:System.ServiceModel.FaultException> and therefore can be used as the fault exception programming model for services that expose SOAP endpoints as well as web HTTP endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95207-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="95207-119">See Also</span></span>  
 [<span data-ttu-id="95207-120">Model programování webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="95207-120">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="95207-121">Formátování WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="95207-121">WCF Web HTTP Formatting</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)  
 [<span data-ttu-id="95207-122">Definice a určení chyb</span><span class="sxs-lookup"><span data-stu-id="95207-122">Defining and Specifying Faults</span></span>](../../../../docs/framework/wcf/defining-and-specifying-faults.md)  
 [<span data-ttu-id="95207-123">Zpracování výjimek a chyb</span><span class="sxs-lookup"><span data-stu-id="95207-123">Handling Exceptions and Faults</span></span>](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)  
 [<span data-ttu-id="95207-124">Chyby odesílání a přijímání</span><span class="sxs-lookup"><span data-stu-id="95207-124">Sending and Receiving Faults</span></span>](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
