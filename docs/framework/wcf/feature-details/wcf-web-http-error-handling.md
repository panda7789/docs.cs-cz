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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c5f397d50a5a97801241afd8e64abf2e56b05dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
 [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Formátování webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)  
 [Definice a určení chyb](../../../../docs/framework/wcf/defining-and-specifying-faults.md)  
 [Zpracování výjimek a chyb](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)  
 [Chyby při odesílání a příjmu](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
