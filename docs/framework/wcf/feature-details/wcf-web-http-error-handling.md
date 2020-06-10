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
# <a name="wcf-web-http-error-handling"></a>Zpracování chyb HTTP programování webové služby WCF
Zpracování chyb webového http Windows Communication Foundation (WCF) umožňuje vracet chyby ze služeb WCF Web HTTP, které určují stavový kód HTTP, a vracet podrobnosti o chybách pomocí stejného formátu jako operace (například XML nebo JSON).  
  
## <a name="wcf-web-http-error-handling"></a>Zpracování chyb HTTP programování webové služby WCF  
 <xref:System.ServiceModel.Web.WebFaultException>Třída definuje konstruktor, který umožňuje určit stavový kód HTTP. Tento stavový kód se pak vrátí klientovi. Obecná verze <xref:System.ServiceModel.Web.WebFaultException> třídy <xref:System.ServiceModel.Web.WebFaultException%601> umožňuje vracet uživatelsky definovaný typ, který obsahuje informace o chybě, ke které došlo. Tento vlastní objekt je serializován pomocí formátu zadaného operací a vráceného klientovi. Následující příklad ukazuje, jak vrátit stavový kód HTTP.  
  
```csharp
public string Operation1()
{
    // Operation logic  
   // ...
   throw new WebFaultException(HttpStatusCode.Forbidden);
}  
```  
  
 Následující příklad ukazuje, jak vrátit stavový kód HTTP a další informace v uživatelsky definovaném typu. `MyErrorDetail`je uživatelsky definovaný typ, který obsahuje další informace o chybě, ke které došlo.  
  
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
  
 Předchozí kód vrátí odpověď HTTP s kódem stavu zakázáno a textem, který obsahuje instanci `MyErrorDetails` objektu. Formát `MyErrorDetails` objektu určuje:  
  
- Hodnota `ResponseFormat` parametru <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> atributu nebo zadaná v rámci operace služby.  
  
- Hodnota <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> .  
  
- Hodnota <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> vlastnosti pomocí přístupu k <xref:System.ServiceModel.Web.OutgoingWebResponseContext> .  
  
 Další informace o tom, jak tyto hodnoty ovlivňují formátování operace, najdete v tématu [formátování webového HTTP WCF](wcf-web-http-formatting.md).  
  
 <xref:System.ServiceModel.Web.WebFaultException>je <xref:System.ServiceModel.FaultException> a lze jej proto použít jako programovací model pro výjimky chyb pro služby, které zveřejňují koncové body SOAP a také koncové body http webu.  
  
## <a name="see-also"></a>Viz také

- [Programovací model webových služeb HTTP WCF](wcf-web-http-programming-model.md)
- [Formátování u programovacího modelu WCF Web HTTP](wcf-web-http-formatting.md)
- [Definice a určení chyb](../defining-and-specifying-faults.md)
- [Zpracování výjimek a chyb](../extending/handling-exceptions-and-faults.md)
- [Chyby při odesílání a příjmu](../sending-and-receiving-faults.md)
