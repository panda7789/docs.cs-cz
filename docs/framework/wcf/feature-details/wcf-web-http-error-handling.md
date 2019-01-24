---
title: Zpracování chyb HTTP programování webové služby WCF
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: c331d70a69740a9830cafb5cafdfcf1de14b541b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499242"
---
# <a name="wcf-web-http-error-handling"></a><span data-ttu-id="c1ce1-102">Zpracování chyb HTTP programování webové služby WCF</span><span class="sxs-lookup"><span data-stu-id="c1ce1-102">WCF Web HTTP Error Handling</span></span>
<span data-ttu-id="c1ce1-103">Zpracování chyb webových služeb HTTP Windows Communication Foundation (WCF) umožňuje vrátit chyby z webových služeb HTTP WCF služby, které zadejte stavový kód HTTP a vrátí podrobnosti o chybě pomocí stejný formát jako operace (například XML nebo JSON).</span><span class="sxs-lookup"><span data-stu-id="c1ce1-103">Windows Communication Foundation (WCF) Web HTTP error handling enables you to return errors from WCF Web HTTP services that specify an HTTP status code and return error details using the same format as the operation (for example, XML or JSON).</span></span>  
  
## <a name="wcf-web-http-error-handling"></a><span data-ttu-id="c1ce1-104">Zpracování chyb HTTP programování webové služby WCF</span><span class="sxs-lookup"><span data-stu-id="c1ce1-104">WCF Web HTTP Error Handling</span></span>  
 <span data-ttu-id="c1ce1-105"><xref:System.ServiceModel.Web.WebFaultException> Třída definuje konstruktor, který vám umožní určit stavový kód HTTP.</span><span class="sxs-lookup"><span data-stu-id="c1ce1-105">The <xref:System.ServiceModel.Web.WebFaultException> class defines a constructor that allows you to specify an HTTP status code.</span></span> <span data-ttu-id="c1ce1-106">Tento kód stavu je pak vrácen do klienta.</span><span class="sxs-lookup"><span data-stu-id="c1ce1-106">This status code is then returned to the client.</span></span> <span data-ttu-id="c1ce1-107">Obecné verzi <xref:System.ServiceModel.Web.WebFaultException> třídy, <xref:System.ServiceModel.Web.WebFaultException%601> umožňuje vrátit uživatelem definovaný typ, který obsahuje informace o této chybě, ke které došlo.</span><span class="sxs-lookup"><span data-stu-id="c1ce1-107">A generic version of the <xref:System.ServiceModel.Web.WebFaultException> class, <xref:System.ServiceModel.Web.WebFaultException%601> enables you to return a user-defined type that contains information about the error that occurred.</span></span> <span data-ttu-id="c1ce1-108">Tato vlastní objekt serializován ve formátu určeném operaci a vrácen do klienta.</span><span class="sxs-lookup"><span data-stu-id="c1ce1-108">This custom object is serialized using the format specified by the operation and returned to the client.</span></span> <span data-ttu-id="c1ce1-109">Následující příklad ukazuje, jak vrátit stavový kód HTTP.</span><span class="sxs-lookup"><span data-stu-id="c1ce1-109">The following example shows how to return an HTTP status code.</span></span>  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 <span data-ttu-id="c1ce1-110">Následující příklad ukazuje, jak vrátit stavový kód HTTP a další informace služby v uživatelem definovaného typu.</span><span class="sxs-lookup"><span data-stu-id="c1ce1-110">The following example shows how to return an HTTP status code and extra information in a user-defined type.</span></span> <span data-ttu-id="c1ce1-111">`MyErrorDetail` je uživatelem definovaný typ, který obsahuje další informace o chybě, ke které došlo.</span><span class="sxs-lookup"><span data-stu-id="c1ce1-111">`MyErrorDetail` is a user-defined type that contains extra information about the error that occurred.</span></span>  
  
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
  
 <span data-ttu-id="c1ce1-112">Předchozí kód vrátí odpověď HTTP s zakázané stavový kód a text, který obsahuje instanci `MyErrorDetails` objektu.</span><span class="sxs-lookup"><span data-stu-id="c1ce1-112">The preceding code returns an HTTP response with the forbidden status code and a body that contains an instance of the `MyErrorDetails` object.</span></span> <span data-ttu-id="c1ce1-113">Formát `MyErrorDetails` objektu se určuje podle:</span><span class="sxs-lookup"><span data-stu-id="c1ce1-113">The format of the `MyErrorDetails` object is determined by:</span></span>  
  
-   <span data-ttu-id="c1ce1-114">Hodnota `ResponseFormat` parametr <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> atribut zadaný u operace služby.</span><span class="sxs-lookup"><span data-stu-id="c1ce1-114">The value of the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute specified on the service operation.</span></span>  
  
-   <span data-ttu-id="c1ce1-115">Hodnota <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span><span class="sxs-lookup"><span data-stu-id="c1ce1-115">The value of <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span></span>  
  
-   <span data-ttu-id="c1ce1-116">Hodnota <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> vlastnost díky přístupu <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span><span class="sxs-lookup"><span data-stu-id="c1ce1-116">The value of the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property by accessing the <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span></span>  
  
 <span data-ttu-id="c1ce1-117">Další informace o tom, jak tyto hodnoty ovlivňují formátování operaci najdete v tématu [WCF Web HTTP formátování](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="c1ce1-117">For more information about how these values affect the formatting of the operation, see [WCF Web HTTP Formatting](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>  
  
 <span data-ttu-id="c1ce1-118"><xref:System.ServiceModel.Web.WebFaultException> je <xref:System.ServiceModel.FaultException> a lze proto použít jako selhání výjimka programovací model pro služby, které zpřístupňují koncové body SOAP, stejně jako webových koncových bodů HTTP.</span><span class="sxs-lookup"><span data-stu-id="c1ce1-118"><xref:System.ServiceModel.Web.WebFaultException> is a <xref:System.ServiceModel.FaultException> and therefore can be used as the fault exception programming model for services that expose SOAP endpoints as well as web HTTP endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1ce1-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1ce1-119">See also</span></span>
- [<span data-ttu-id="c1ce1-120">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="c1ce1-120">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="c1ce1-121">Formátování webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="c1ce1-121">WCF Web HTTP Formatting</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)
- [<span data-ttu-id="c1ce1-122">Definice a určení chyb</span><span class="sxs-lookup"><span data-stu-id="c1ce1-122">Defining and Specifying Faults</span></span>](../../../../docs/framework/wcf/defining-and-specifying-faults.md)
- [<span data-ttu-id="c1ce1-123">Zpracování výjimek a chyb</span><span class="sxs-lookup"><span data-stu-id="c1ce1-123">Handling Exceptions and Faults</span></span>](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)
- [<span data-ttu-id="c1ce1-124">Chyby při odesílání a příjmu</span><span class="sxs-lookup"><span data-stu-id="c1ce1-124">Sending and Receiving Faults</span></span>](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
