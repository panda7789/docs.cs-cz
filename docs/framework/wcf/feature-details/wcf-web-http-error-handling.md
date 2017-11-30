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
# <a name="wcf-web-http-error-handling"></a>Zpracování chyb HTTP programování webové služby WCF
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Zpracování chyb webových služeb HTTP umožňuje vracet chyby z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP webové služby, které zadejte stav HTTP kód a vrátí podrobnosti o chybě používá stejný formát jako operace (například XML nebo JSON).  
  
## <a name="wcf-web-http-error-handling"></a>Zpracování chyb HTTP programování webové služby WCF  
 <xref:System.ServiceModel.Web.WebFaultException> Třída definuje konstruktor, který vám umožní určit stavový kód HTTP. Tento kód stavu je pak vrácen do klienta. Obecná verze <xref:System.ServiceModel.Web.WebFaultException> třídy, <xref:System.ServiceModel.Web.WebFaultException%601> umožní vám vrátit uživatelem definovaný typ, který obsahuje informace o této chybě, která došlo k chybě. Tato vlastní objekt serializován formátu určeného operaci a vrátí klientovi. Následující příklad ukazuje, jak vrátit stavový kód HTTP.  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 Následující příklad ukazuje, jak se vrátit stavový kód HTTP a doplňující informace v uživatelsky definovaný typ. `MyErrorDetail`je typ definovaný uživatelem, který obsahuje další informace o této chybě, která došlo k chybě.  
  
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
  
 Předchozí kód vrátí odpověď HTTP s zakázané stavový kód a text, který obsahuje instance `MyErrorDetails` objektu. Formát `MyErrorDetails` objektu je určen podle:  
  
-   Hodnota `ResponseFormat` parametr <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> atribut na operaci služby.  
  
-   Hodnota <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.  
  
-   Hodnota <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> vlastnost přímým přístupem <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]jak tyto hodnoty ovlivňují formátování operaci, najdete v části [WCF Web HTTP formátování](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).  
  
 <xref:System.ServiceModel.Web.WebFaultException>je <xref:System.ServiceModel.FaultException> a proto může sloužit jako programovací model selhání výjimky pro služby, které zveřejňují koncových bodů protokolu SOAP a také web koncových bodů protokolu HTTP.  
  
## <a name="see-also"></a>Viz také  
 [Model programování webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Formátování WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)  
 [Definice a určení chyb](../../../../docs/framework/wcf/defining-and-specifying-faults.md)  
 [Zpracování výjimek a chyb](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)  
 [Chyby odesílání a přijímání](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
