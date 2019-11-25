---
title: Zpracování chyb HTTP programování webové služby WCF
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: 34912bccaefb645541f47d083c5c307b20ff77c5
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975958"
---
# <a name="wcf-web-http-error-handling"></a><span data-ttu-id="380d8-102">Zpracování chyb HTTP programování webové služby WCF</span><span class="sxs-lookup"><span data-stu-id="380d8-102">WCF Web HTTP Error Handling</span></span>
<span data-ttu-id="380d8-103">Zpracování chyb webového http Windows Communication Foundation (WCF) umožňuje vracet chyby ze služeb WCF Web HTTP, které určují stavový kód HTTP, a vracet podrobnosti o chybách pomocí stejného formátu jako operace (například XML nebo JSON).</span><span class="sxs-lookup"><span data-stu-id="380d8-103">Windows Communication Foundation (WCF) Web HTTP error handling enables you to return errors from WCF Web HTTP services that specify an HTTP status code and return error details using the same format as the operation (for example, XML or JSON).</span></span>  
  
## <a name="wcf-web-http-error-handling"></a><span data-ttu-id="380d8-104">Zpracování chyb HTTP programování webové služby WCF</span><span class="sxs-lookup"><span data-stu-id="380d8-104">WCF Web HTTP Error Handling</span></span>  
 <span data-ttu-id="380d8-105">Třída <xref:System.ServiceModel.Web.WebFaultException> definuje konstruktor, který umožňuje určit stavový kód HTTP.</span><span class="sxs-lookup"><span data-stu-id="380d8-105">The <xref:System.ServiceModel.Web.WebFaultException> class defines a constructor that allows you to specify an HTTP status code.</span></span> <span data-ttu-id="380d8-106">Tento stavový kód se pak vrátí klientovi.</span><span class="sxs-lookup"><span data-stu-id="380d8-106">This status code is then returned to the client.</span></span> <span data-ttu-id="380d8-107">Obecná verze <xref:System.ServiceModel.Web.WebFaultException> třídy, <xref:System.ServiceModel.Web.WebFaultException%601> umožňuje vrátit uživatelem definovaný typ, který obsahuje informace o chybě, ke které došlo.</span><span class="sxs-lookup"><span data-stu-id="380d8-107">A generic version of the <xref:System.ServiceModel.Web.WebFaultException> class, <xref:System.ServiceModel.Web.WebFaultException%601> enables you to return a user-defined type that contains information about the error that occurred.</span></span> <span data-ttu-id="380d8-108">Tento vlastní objekt je serializován pomocí formátu zadaného operací a vráceného klientovi.</span><span class="sxs-lookup"><span data-stu-id="380d8-108">This custom object is serialized using the format specified by the operation and returned to the client.</span></span> <span data-ttu-id="380d8-109">Následující příklad ukazuje, jak vrátit stavový kód HTTP.</span><span class="sxs-lookup"><span data-stu-id="380d8-109">The following example shows how to return an HTTP status code.</span></span>  
  
```csharp
public string Operation1()
{
    // Operation logic  
   // ...
   throw new WebFaultException(HttpStatusCode.Forbidden);
}  
```  
  
 <span data-ttu-id="380d8-110">Následující příklad ukazuje, jak vrátit stavový kód HTTP a další informace v uživatelsky definovaném typu.</span><span class="sxs-lookup"><span data-stu-id="380d8-110">The following example shows how to return an HTTP status code and extra information in a user-defined type.</span></span> <span data-ttu-id="380d8-111">`MyErrorDetail` je uživatelsky definovaný typ, který obsahuje další informace o chybě, ke které došlo.</span><span class="sxs-lookup"><span data-stu-id="380d8-111">`MyErrorDetail` is a user-defined type that contains extra information about the error that occurred.</span></span>  
  
```csharp
public string Operation2()
{
   // Operation logic  
   // ...
   MyErrorDetail detail = new MyErrorDetail()
   {  
      Message = "Error Message",  
      ErrorCode = 123,  
   }  
   throw new WebFaultException<MyErrorDetail>(detail, HttpStatusCode.Forbidden);  
}  
```  
  
 <span data-ttu-id="380d8-112">Předchozí kód vrátí odpověď HTTP s kódem stavu zakázáno a textem, který obsahuje instanci objektu `MyErrorDetails`.</span><span class="sxs-lookup"><span data-stu-id="380d8-112">The preceding code returns an HTTP response with the forbidden status code and a body that contains an instance of the `MyErrorDetails` object.</span></span> <span data-ttu-id="380d8-113">Formát objektu `MyErrorDetails` určuje:</span><span class="sxs-lookup"><span data-stu-id="380d8-113">The format of the `MyErrorDetails` object is determined by:</span></span>  
  
- <span data-ttu-id="380d8-114">Hodnota parametru `ResponseFormat` atributu <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> zadaného v rámci operace služby.</span><span class="sxs-lookup"><span data-stu-id="380d8-114">The value of the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute specified on the service operation.</span></span>  
  
- <span data-ttu-id="380d8-115">Hodnota <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span><span class="sxs-lookup"><span data-stu-id="380d8-115">The value of <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span></span>  
  
- <span data-ttu-id="380d8-116">Hodnota vlastnosti <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> přístupem k <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span><span class="sxs-lookup"><span data-stu-id="380d8-116">The value of the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property by accessing the <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span></span>  
  
 <span data-ttu-id="380d8-117">Další informace o tom, jak tyto hodnoty ovlivňují formátování operace, najdete v tématu [formátování webového HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="380d8-117">For more information about how these values affect the formatting of the operation, see [WCF Web HTTP Formatting](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>  
  
 <span data-ttu-id="380d8-118"><xref:System.ServiceModel.Web.WebFaultException> je <xref:System.ServiceModel.FaultException> a je možné ho použít jako programovací model pro výjimku chyb pro služby, které zveřejňují koncové body SOAP a také webové koncové body HTTP.</span><span class="sxs-lookup"><span data-stu-id="380d8-118"><xref:System.ServiceModel.Web.WebFaultException> is a <xref:System.ServiceModel.FaultException> and therefore can be used as the fault exception programming model for services that expose SOAP endpoints as well as web HTTP endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="380d8-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="380d8-119">See also</span></span>

- [<span data-ttu-id="380d8-120">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="380d8-120">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="380d8-121">Formátování webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="380d8-121">WCF Web HTTP Formatting</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)
- [<span data-ttu-id="380d8-122">Definice a určení chyb</span><span class="sxs-lookup"><span data-stu-id="380d8-122">Defining and Specifying Faults</span></span>](../../../../docs/framework/wcf/defining-and-specifying-faults.md)
- [<span data-ttu-id="380d8-123">Zpracování výjimek a chyb</span><span class="sxs-lookup"><span data-stu-id="380d8-123">Handling Exceptions and Faults</span></span>](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)
- [<span data-ttu-id="380d8-124">Chyby při odesílání a příjmu</span><span class="sxs-lookup"><span data-stu-id="380d8-124">Sending and Receiving Faults</span></span>](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
