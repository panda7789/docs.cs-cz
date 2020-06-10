---
title: Zpracování chyb HTTP programování webové služby WCF
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: b1d41bebafa2795d390b120ad84475417389479b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598642"
---
# <a name="wcf-web-http-error-handling"></a><span data-ttu-id="84628-102">Zpracování chyb HTTP programování webové služby WCF</span><span class="sxs-lookup"><span data-stu-id="84628-102">WCF Web HTTP Error Handling</span></span>
<span data-ttu-id="84628-103">Zpracování chyb webového http Windows Communication Foundation (WCF) umožňuje vracet chyby ze služeb WCF Web HTTP, které určují stavový kód HTTP, a vracet podrobnosti o chybách pomocí stejného formátu jako operace (například XML nebo JSON).</span><span class="sxs-lookup"><span data-stu-id="84628-103">Windows Communication Foundation (WCF) Web HTTP error handling enables you to return errors from WCF Web HTTP services that specify an HTTP status code and return error details using the same format as the operation (for example, XML or JSON).</span></span>  
  
## <a name="wcf-web-http-error-handling"></a><span data-ttu-id="84628-104">Zpracování chyb HTTP programování webové služby WCF</span><span class="sxs-lookup"><span data-stu-id="84628-104">WCF Web HTTP Error Handling</span></span>  
 <span data-ttu-id="84628-105"><xref:System.ServiceModel.Web.WebFaultException>Třída definuje konstruktor, který umožňuje určit stavový kód HTTP.</span><span class="sxs-lookup"><span data-stu-id="84628-105">The <xref:System.ServiceModel.Web.WebFaultException> class defines a constructor that allows you to specify an HTTP status code.</span></span> <span data-ttu-id="84628-106">Tento stavový kód se pak vrátí klientovi.</span><span class="sxs-lookup"><span data-stu-id="84628-106">This status code is then returned to the client.</span></span> <span data-ttu-id="84628-107">Obecná verze <xref:System.ServiceModel.Web.WebFaultException> třídy <xref:System.ServiceModel.Web.WebFaultException%601> umožňuje vracet uživatelsky definovaný typ, který obsahuje informace o chybě, ke které došlo.</span><span class="sxs-lookup"><span data-stu-id="84628-107">A generic version of the <xref:System.ServiceModel.Web.WebFaultException> class, <xref:System.ServiceModel.Web.WebFaultException%601> enables you to return a user-defined type that contains information about the error that occurred.</span></span> <span data-ttu-id="84628-108">Tento vlastní objekt je serializován pomocí formátu zadaného operací a vráceného klientovi.</span><span class="sxs-lookup"><span data-stu-id="84628-108">This custom object is serialized using the format specified by the operation and returned to the client.</span></span> <span data-ttu-id="84628-109">Následující příklad ukazuje, jak vrátit stavový kód HTTP.</span><span class="sxs-lookup"><span data-stu-id="84628-109">The following example shows how to return an HTTP status code.</span></span>  
  
```csharp
public string Operation1()
{
    // Operation logic  
   // ...
   throw new WebFaultException(HttpStatusCode.Forbidden);
}  
```  
  
 <span data-ttu-id="84628-110">Následující příklad ukazuje, jak vrátit stavový kód HTTP a další informace v uživatelsky definovaném typu.</span><span class="sxs-lookup"><span data-stu-id="84628-110">The following example shows how to return an HTTP status code and extra information in a user-defined type.</span></span> <span data-ttu-id="84628-111">`MyErrorDetail`je uživatelsky definovaný typ, který obsahuje další informace o chybě, ke které došlo.</span><span class="sxs-lookup"><span data-stu-id="84628-111">`MyErrorDetail` is a user-defined type that contains extra information about the error that occurred.</span></span>  
  
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
  
 <span data-ttu-id="84628-112">Předchozí kód vrátí odpověď HTTP s kódem stavu zakázáno a textem, který obsahuje instanci `MyErrorDetails` objektu.</span><span class="sxs-lookup"><span data-stu-id="84628-112">The preceding code returns an HTTP response with the forbidden status code and a body that contains an instance of the `MyErrorDetails` object.</span></span> <span data-ttu-id="84628-113">Formát `MyErrorDetails` objektu určuje:</span><span class="sxs-lookup"><span data-stu-id="84628-113">The format of the `MyErrorDetails` object is determined by:</span></span>  
  
- <span data-ttu-id="84628-114">Hodnota `ResponseFormat` parametru <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> atributu nebo zadaná v rámci operace služby.</span><span class="sxs-lookup"><span data-stu-id="84628-114">The value of the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute specified on the service operation.</span></span>  
  
- <span data-ttu-id="84628-115">Hodnota <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> .</span><span class="sxs-lookup"><span data-stu-id="84628-115">The value of <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span></span>  
  
- <span data-ttu-id="84628-116">Hodnota <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> vlastnosti pomocí přístupu k <xref:System.ServiceModel.Web.OutgoingWebResponseContext> .</span><span class="sxs-lookup"><span data-stu-id="84628-116">The value of the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property by accessing the <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span></span>  
  
 <span data-ttu-id="84628-117">Další informace o tom, jak tyto hodnoty ovlivňují formátování operace, najdete v tématu [formátování webového HTTP WCF](wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="84628-117">For more information about how these values affect the formatting of the operation, see [WCF Web HTTP Formatting](wcf-web-http-formatting.md).</span></span>  
  
 <span data-ttu-id="84628-118"><xref:System.ServiceModel.Web.WebFaultException>je <xref:System.ServiceModel.FaultException> a lze jej proto použít jako programovací model pro výjimky chyb pro služby, které zveřejňují koncové body SOAP a také koncové body http webu.</span><span class="sxs-lookup"><span data-stu-id="84628-118"><xref:System.ServiceModel.Web.WebFaultException> is a <xref:System.ServiceModel.FaultException> and therefore can be used as the fault exception programming model for services that expose SOAP endpoints as well as web HTTP endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84628-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="84628-119">See also</span></span>

- [<span data-ttu-id="84628-120">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="84628-120">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- [<span data-ttu-id="84628-121">Formátování u programovacího modelu WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="84628-121">WCF Web HTTP Formatting</span></span>](wcf-web-http-formatting.md)
- [<span data-ttu-id="84628-122">Definice a určení chyb</span><span class="sxs-lookup"><span data-stu-id="84628-122">Defining and Specifying Faults</span></span>](../defining-and-specifying-faults.md)
- [<span data-ttu-id="84628-123">Zpracování výjimek a chyb</span><span class="sxs-lookup"><span data-stu-id="84628-123">Handling Exceptions and Faults</span></span>](../extending/handling-exceptions-and-faults.md)
- [<span data-ttu-id="84628-124">Chyby při odesílání a příjmu</span><span class="sxs-lookup"><span data-stu-id="84628-124">Sending and Receiving Faults</span></span>](../sending-and-receiving-faults.md)
