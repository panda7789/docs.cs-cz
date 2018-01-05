---
title: "Vytváření služeb WCF pro ASP.NET AJAX"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c2e3ba1d360c55f10cde9447b3961d84ffe1cdb2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="creating-wcf-services-for-aspnet-ajax"></a>Vytváření služeb WCF pro ASP.NET AJAX
Microsoft ASP.NET AJAX umožňuje rychle vytvářet webové stránky, které zahrnují bohaté uživatelské prostředí s reakce a známé prvky uživatelského rozhraní. Poskytuje klientský skript knihovny, které jsou různé prohlížeče ECMAScript (JavaScript) a dynamické HTML (DHTML) technologie ASP.NET AJAX a se integruje s platformou ASP.NET 2.0 na serveru vývoj. Pomocí prvku ASP.NET AJAX, můžete zlepšit činnost koncového uživatele a efektivitu webových aplikací.  
  
 Knihovny klientských skriptů a součásti serveru, které jsou integrované zajistit robustní vývoj rozhraní se skládá prvku ASP.NET AJAX. Pro přístup k službě ze stránky ASP.NET: po adresu URL služby se přidá do ovládacího prvku správce skriptu ASP.NET na stránce, může být volána operací služby pomocí kódu jazyka JavaScript, který může vypadat přesně regulární volání funkce jazyka JavaScript. V tématu [další prvku ASP.NET AJAX](http://go.microsoft.com/fwlink/?LinkId=186475) o použití webových služeb v rámci rozhraní AJAX.  
  
 Většina [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služeb mohou být vystaveny jako kompatibilní s technologií ASP.NET AJAX služby přidáním příslušné koncového bodu ASP.NET AJAX.  
  
 Pokud používáte Visual Studio, můžete použít pro služby WCF s podporou AJAXU, k dispozici v předem připravených šablon **přidat novou položku** dialogové okno při práci s weby technologie ASP.NET a webových aplikací.  
  
 Pokud nepoužíváte šablony sady Visual Studio, existují dva způsoby vytvoření koncového bodu ASP.NET AJAX:  
  
-   Vytvořte koncový bod pomocí dynamický aktivace bez použití žádnou konfiguraci. Toto je nejzákladnější přístup, pokud jste obeznámeni s WCF konfigurační systém. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Postupy: Přidání koncového bodu ASP.NET AJAX bez použití konfigurace](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
-   Přidání koncového bodu podporou AJAXU na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby pomocí konfigurace. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Postupy: použití konfigurace k přidání koncového bodu ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
 Popsané v modelu webového programování [programování přehled modelu WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md) lze pomocí prvku ASP.NET AJAX služby. Konkrétně:  
  
-   Můžete použít <xref:System.ServiceModel.Web.WebGetAttribute> a <xref:System.ServiceModel.Web.WebInvokeAttribute> atributů k výběru mezi příkazy HTTP GET a POST protokolu HTTP. Pokud se používá správně, může to výrazně zlepšit výkon vaší aplikace. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Postupy: výběr mezi HTTP POST a HTTP GET požadavky pro koncové body ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md).  
  
-   Můžete použít <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> a <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> vlastnosti způsobí služby vrátit data XML místo výchozího JavaScript Object Notation (JSON). Díky tomuto pomocí rozhraní ASP.NET AJAX způsobí, že klient JavaScript pro příjem objektu XML DOM.  
  
    > [!WARNING]
    >  Tuto operaci, musíte nastavit typ obsahu na text/xml pro tento postup. JavaScript klienta, jinak se zobrazí řetězec, který obsahuje XML místo objekt XML DOM.  
  
     Následuje příklad operace, která vrací XML data s typem obsahu správně nastavené:  
  
    ```  
    [OperationContract, WebGet(ResponseFormat=WebMessageFormat.Xml)]  
    public XElement GetData()  
    {  
    XElement x;  
    //Get some data here...  
  
    WebOperationContext.Current.OutgoingResponse.ContentType = "text/xml";      
    return x;  
    }  
    ```  
  
-   Žádné jiné vlastnosti na <xref:System.ServiceModel.Web.WebGetAttribute> a <xref:System.ServiceModel.Web.WebInvokeAttribute> atributy lze změnit, pokud se vyžaduje kompatibilitu s ASP.NET AJAX. Další aspekty Model programování webových lze tak dlouho, dokud nejsou došlo k porušení pravidel pro volání prvku ASP.NET AJAX.  
  
 Pokročilejší scénáře vyžadují některé další podrobnosti o podpoře AJAX v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rozumí:  
  
-   Abyste pochopili, jak je dat přenesených mezi klientem AJAX stránky a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby pomocí jazyka JavaScript a informace o mapování typů rozhraní .NET Framework do typů jazyka JavaScript, najdete v části [podpora formátu JSON a ostatní přenosu dat formátů](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md) .  
  
-   Abyste mohli využívat funkce technologie ASP.NET, například ověřování na základě adresy URL a přístup k informacím o relace ASP.NET, můžete povolit režim kompatibility ASP.NET prostřednictvím konfigurace.  
  
 Koncové body AJAX v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mohou být využívány i bez rozhraní ASP.NET AJAX. Díky tomu vyžaduje znalosti o architekturu podpory AJAX v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Informace o této architektuře, najdete v části [WCF Web HTTP programovací objektový Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md). Ukázku kódu demonstraci tuto metodu, najdete [služba AJAX s protokoly JSON a XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="see-also"></a>Viz také  
 [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Postupy: Přidání koncového bodu ASP.NET AJAX bez použití konfigurace](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)  
 [Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)  
 [Postupy: Volba mezi žádostmi HTTP POST a HTTP GET u koncových bodů ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)
