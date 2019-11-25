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
# <a name="wcf-web-http-error-handling"></a>Zpracování chyb HTTP programování webové služby WCF
Zpracování chyb webového http Windows Communication Foundation (WCF) umožňuje vracet chyby ze služeb WCF Web HTTP, které určují stavový kód HTTP, a vracet podrobnosti o chybách pomocí stejného formátu jako operace (například XML nebo JSON).  
  
## <a name="wcf-web-http-error-handling"></a>Zpracování chyb HTTP programování webové služby WCF  
 Třída <xref:System.ServiceModel.Web.WebFaultException> definuje konstruktor, který umožňuje určit stavový kód HTTP. Tento stavový kód se pak vrátí klientovi. Obecná verze <xref:System.ServiceModel.Web.WebFaultException> třídy, <xref:System.ServiceModel.Web.WebFaultException%601> umožňuje vrátit uživatelem definovaný typ, který obsahuje informace o chybě, ke které došlo. Tento vlastní objekt je serializován pomocí formátu zadaného operací a vráceného klientovi. Následující příklad ukazuje, jak vrátit stavový kód HTTP.  
  
```csharp
public string Operation1()
{
    // Operation logic  
   // ...
   throw new WebFaultException(HttpStatusCode.Forbidden);
}  
```  
  
 Následující příklad ukazuje, jak vrátit stavový kód HTTP a další informace v uživatelsky definovaném typu. `MyErrorDetail` je uživatelsky definovaný typ, který obsahuje další informace o chybě, ke které došlo.  
  
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
  
 Předchozí kód vrátí odpověď HTTP s kódem stavu zakázáno a textem, který obsahuje instanci objektu `MyErrorDetails`. Formát objektu `MyErrorDetails` určuje:  
  
- Hodnota parametru `ResponseFormat` atributu <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> zadaného v rámci operace služby.  
  
- Hodnota <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.  
  
- Hodnota vlastnosti <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> přístupem k <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.  
  
 Další informace o tom, jak tyto hodnoty ovlivňují formátování operace, najdete v tématu [formátování webového HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).  
  
 <xref:System.ServiceModel.Web.WebFaultException> je <xref:System.ServiceModel.FaultException> a je možné ho použít jako programovací model pro výjimku chyb pro služby, které zveřejňují koncové body SOAP a také webové koncové body HTTP.  
  
## <a name="see-also"></a>Viz také:

- [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [Formátování webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)
- [Definice a určení chyb](../../../../docs/framework/wcf/defining-and-specifying-faults.md)
- [Zpracování výjimek a chyb](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)
- [Chyby při odesílání a příjmu](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
