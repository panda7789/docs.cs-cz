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
# <a name="wcf-web-http-error-handling"></a>Zpracování chyb HTTP programování webové služby WCF
Zpracování chyb webových služeb HTTP Windows Communication Foundation (WCF) umožňuje vrátit chyby z webových služeb HTTP WCF služby, které zadejte stavový kód HTTP a vrátí podrobnosti o chybě pomocí stejný formát jako operace (například XML nebo JSON).  
  
## <a name="wcf-web-http-error-handling"></a>Zpracování chyb HTTP programování webové služby WCF  
 <xref:System.ServiceModel.Web.WebFaultException> Třída definuje konstruktor, který vám umožní určit stavový kód HTTP. Tento kód stavu je pak vrácen do klienta. Obecné verzi <xref:System.ServiceModel.Web.WebFaultException> třídy, <xref:System.ServiceModel.Web.WebFaultException%601> umožňuje vrátit uživatelem definovaný typ, který obsahuje informace o této chybě, ke které došlo. Tato vlastní objekt serializován ve formátu určeném operaci a vrácen do klienta. Následující příklad ukazuje, jak vrátit stavový kód HTTP.  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 Následující příklad ukazuje, jak vrátit stavový kód HTTP a další informace služby v uživatelem definovaného typu. `MyErrorDetail` je uživatelem definovaný typ, který obsahuje další informace o chybě, ke které došlo.  
  
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
  
 Předchozí kód vrátí odpověď HTTP s zakázané stavový kód a text, který obsahuje instanci `MyErrorDetails` objektu. Formát `MyErrorDetails` objektu se určuje podle:  
  
-   Hodnota `ResponseFormat` parametr <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> atribut zadaný u operace služby.  
  
-   Hodnota <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.  
  
-   Hodnota <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> vlastnost díky přístupu <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.  
  
 Další informace o tom, jak tyto hodnoty ovlivňují formátování operaci najdete v tématu [WCF Web HTTP formátování](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).  
  
 <xref:System.ServiceModel.Web.WebFaultException> je <xref:System.ServiceModel.FaultException> a lze proto použít jako selhání výjimka programovací model pro služby, které zpřístupňují koncové body SOAP, stejně jako webových koncových bodů HTTP.  
  
## <a name="see-also"></a>Viz také:
- [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [Formátování webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)
- [Definice a určení chyb](../../../../docs/framework/wcf/defining-and-specifying-faults.md)
- [Zpracování výjimek a chyb](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)
- [Chyby při odesílání a příjmu](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
