---
title: Zpracování chyb HTTP programování webové služby WCF
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: 491c39d97c48e2f92ff258ac42b9576d407b898e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648421"
---
# <a name="wcf-web-http-error-handling"></a><span data-ttu-id="47353-102">Zpracování chyb HTTP programování webové služby WCF</span><span class="sxs-lookup"><span data-stu-id="47353-102">WCF Web HTTP Error Handling</span></span>
<span data-ttu-id="47353-103">Zpracování chyb webových služeb HTTP Windows Communication Foundation (WCF) umožňuje vrátit chyby z webových služeb HTTP WCF služby, které zadejte stavový kód HTTP a vrátí podrobnosti o chybě pomocí stejný formát jako operace (například XML nebo JSON).</span><span class="sxs-lookup"><span data-stu-id="47353-103">Windows Communication Foundation (WCF) Web HTTP error handling enables you to return errors from WCF Web HTTP services that specify an HTTP status code and return error details using the same format as the operation (for example, XML or JSON).</span></span>  
  
## <a name="wcf-web-http-error-handling"></a><span data-ttu-id="47353-104">Zpracování chyb HTTP programování webové služby WCF</span><span class="sxs-lookup"><span data-stu-id="47353-104">WCF Web HTTP Error Handling</span></span>  
 <span data-ttu-id="47353-105"><xref:System.ServiceModel.Web.WebFaultException> Třída definuje konstruktor, který vám umožní určit stavový kód HTTP.</span><span class="sxs-lookup"><span data-stu-id="47353-105">The <xref:System.ServiceModel.Web.WebFaultException> class defines a constructor that allows you to specify an HTTP status code.</span></span> <span data-ttu-id="47353-106">Tento kód stavu je pak vrácen do klienta.</span><span class="sxs-lookup"><span data-stu-id="47353-106">This status code is then returned to the client.</span></span> <span data-ttu-id="47353-107">Obecné verzi <xref:System.ServiceModel.Web.WebFaultException> třídy, <xref:System.ServiceModel.Web.WebFaultException%601> umožňuje vrátit uživatelem definovaný typ, který obsahuje informace o této chybě, ke které došlo.</span><span class="sxs-lookup"><span data-stu-id="47353-107">A generic version of the <xref:System.ServiceModel.Web.WebFaultException> class, <xref:System.ServiceModel.Web.WebFaultException%601> enables you to return a user-defined type that contains information about the error that occurred.</span></span> <span data-ttu-id="47353-108">Tato vlastní objekt serializován ve formátu určeném operaci a vrácen do klienta.</span><span class="sxs-lookup"><span data-stu-id="47353-108">This custom object is serialized using the format specified by the operation and returned to the client.</span></span> <span data-ttu-id="47353-109">Následující příklad ukazuje, jak vrátit stavový kód HTTP.</span><span class="sxs-lookup"><span data-stu-id="47353-109">The following example shows how to return an HTTP status code.</span></span>  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 <span data-ttu-id="47353-110">Následující příklad ukazuje, jak vrátit stavový kód HTTP a další informace služby v uživatelem definovaného typu.</span><span class="sxs-lookup"><span data-stu-id="47353-110">The following example shows how to return an HTTP status code and extra information in a user-defined type.</span></span> <span data-ttu-id="47353-111">`MyErrorDetail` je uživatelem definovaný typ, který obsahuje další informace o chybě, ke které došlo.</span><span class="sxs-lookup"><span data-stu-id="47353-111">`MyErrorDetail` is a user-defined type that contains extra information about the error that occurred.</span></span>  
  
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
  
 <span data-ttu-id="47353-112">Předchozí kód vrátí odpověď HTTP s zakázané stavový kód a text, který obsahuje instanci `MyErrorDetails` objektu.</span><span class="sxs-lookup"><span data-stu-id="47353-112">The preceding code returns an HTTP response with the forbidden status code and a body that contains an instance of the `MyErrorDetails` object.</span></span> <span data-ttu-id="47353-113">Formát `MyErrorDetails` objektu se určuje podle:</span><span class="sxs-lookup"><span data-stu-id="47353-113">The format of the `MyErrorDetails` object is determined by:</span></span>  
  
- <span data-ttu-id="47353-114">Hodnota `ResponseFormat` parametr <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> atribut zadaný u operace služby.</span><span class="sxs-lookup"><span data-stu-id="47353-114">The value of the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute specified on the service operation.</span></span>  
  
- <span data-ttu-id="47353-115">Hodnota <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span><span class="sxs-lookup"><span data-stu-id="47353-115">The value of <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span></span>  
  
- <span data-ttu-id="47353-116">Hodnota <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> vlastnost díky přístupu <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span><span class="sxs-lookup"><span data-stu-id="47353-116">The value of the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property by accessing the <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span></span>  
  
 <span data-ttu-id="47353-117">Další informace o tom, jak tyto hodnoty ovlivňují formátování operaci najdete v tématu [WCF Web HTTP formátování](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="47353-117">For more information about how these values affect the formatting of the operation, see [WCF Web HTTP Formatting](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>  
  
 <span data-ttu-id="47353-118"><xref:System.ServiceModel.Web.WebFaultException> je <xref:System.ServiceModel.FaultException> a lze proto použít jako selhání výjimka programovací model pro služby, které zpřístupňují koncové body SOAP, stejně jako webových koncových bodů HTTP.</span><span class="sxs-lookup"><span data-stu-id="47353-118"><xref:System.ServiceModel.Web.WebFaultException> is a <xref:System.ServiceModel.FaultException> and therefore can be used as the fault exception programming model for services that expose SOAP endpoints as well as web HTTP endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47353-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47353-119">See also</span></span>

- [<span data-ttu-id="47353-120">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="47353-120">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="47353-121">Formátování webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="47353-121">WCF Web HTTP Formatting</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)
- [<span data-ttu-id="47353-122">Definice a určení chyb</span><span class="sxs-lookup"><span data-stu-id="47353-122">Defining and Specifying Faults</span></span>](../../../../docs/framework/wcf/defining-and-specifying-faults.md)
- [<span data-ttu-id="47353-123">Zpracování výjimek a chyb</span><span class="sxs-lookup"><span data-stu-id="47353-123">Handling Exceptions and Faults</span></span>](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)
- [<span data-ttu-id="47353-124">Chyby při odesílání a příjmu</span><span class="sxs-lookup"><span data-stu-id="47353-124">Sending and Receiving Faults</span></span>](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
