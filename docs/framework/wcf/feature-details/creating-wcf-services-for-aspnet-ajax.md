---
title: Vytváření služeb WCF pro ASP.NET AJAX
ms.date: 03/30/2017
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
ms.openlocfilehash: 4d3953046a796686a465cd8096b8f2ba930aa9fd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463257"
---
# <a name="creating-wcf-services-for-aspnet-ajax"></a>Vytváření služeb WCF pro ASP.NET AJAX
Microsoft ASP.NET AJAX umožňuje rychle vytvářet webové stránky, které zahrnují bohaté uživatelské prostředí s rychlou odezvou a zkušenosti prvky uživatelského rozhraní. ASP.NET AJAX obsahuje klientského skriptu knihovny, které zahrnují prohlížečů ECMAScript (JavaScript) a technologie dynamického HTML (DHTML) a se integruje s ASP.NET 2.0 na serveru vývojovou platformu. Pomocí prvku ASP.NET AJAX, můžete zlepšit uživatelské prostředí a efektivitu vaší webové aplikace.  
  
 ASP.NET AJAX se skládá z knihoven klienta skriptů a součásti serveru, které jsou integrované a poskytnou robustní vývojářská platforma. Přístup ke službě ze stránky ASP.NET: Jakmile se na ovládací prvek správce skriptů ASP.NET na stránku se přidá adresa URL služby, operací služby mohou být vyvolány pomocí kódu jazyka JavaScript, která vypadá stejně jako regulární volání funkce jazyka JavaScript. Zobrazit [informace ASP.NET AJAX](https://go.microsoft.com/fwlink/?LinkId=186475) o využívání webové služby v rámci rozhraní AJAX framework.  
  
 Většina služeb Windows Communication Foundation (WCF) může být vystavený jako služba kompatibilní s technologií ASP.NET AJAX tak, že přidáte odpovídající koncového bodu ASP.NET AJAX.  
  
 Pokud používáte Visual Studio, můžete použít předem připravené šablony pro služby WCF s podporou jazyka AJAX, k dispozici v **přidat novou položku** dialogové okno při práci s weby ASP.NET nebo webových aplikací.  
  
 Pokud nepoužíváte šablony sady Visual Studio, existují dva způsoby vytvoření koncového bodu ASP.NET AJAX:  
  
-   Vytvoření koncového bodu pomocí aktivace dynamické hostitele bez použití jakékoli konfigurace. Jedná se o nejzákladnější postup, pokud nejste obeznámeni s konfigurací systému WCF. Další informace najdete v tématu [postupy: Přidání ASP.NET AJAX konfigurace koncového bodu bez použití](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
-   Přidáte koncový bod s povoleným AJAX pro služby WCF pomocí konfigurace. Další informace najdete v tématu [postupy: použití konfigurace k přidání koncového bodu ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
 Modelu programování webových služeb podle [WCF Web HTTP programovací Model Overview](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md) může být použit s služeb technologie ASP.NET AJAX. Konkrétně:  
  
-   Můžete použít <xref:System.ServiceModel.Web.WebGetAttribute> a <xref:System.ServiceModel.Web.WebInvokeAttribute> atributy na výběr mezi příkazy HTTP GET a POST protokolu HTTP. Pokud jsou správně použity, to může výrazně zlepšit výkon vaší aplikace. Další informace najdete v tématu [postupy: volba mezi HTTP POST a HTTP GET požadavky u koncových bodů ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md).  
  
-   Můžete použít <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> a <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> vlastnosti způsobit, že vaše služba vrátit data XML místo výchozího objektu zápis JSON (JavaScript). To s použitím rozhraní ASP.NET AJAX framework způsobí, že klient jazyka JavaScript pro příjem objekt modelu DOM jazyka XML.  
  
    > [!WARNING]
    >  Operaci musíte nastavit typ obsahu na text/xml, aby to fungovalo. V opačném případě javascriptový klient obdrží řetězec obsahující XML namísto objektu modelu DOM jazyka XML.  
  
     Následuje příklad operace, která vrací XML data s odpovídajícím způsobem nastavit typ obsahu:  
  
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
  
-   Bez dalších vlastností <xref:System.ServiceModel.Web.WebGetAttribute> a <xref:System.ServiceModel.Web.WebInvokeAttribute> atributy lze změnit, pokud se vyžaduje kompatibilitu s ASP.NET AJAX. Další aspekty modelu webového programování je možné tak dlouho, dokud nejsou konvence volání jazyka AJAX technologie ASP.NET došlo k porušení.  
  
 Pokročilejší scénáře vyžadují interpretovat některé další podrobnosti o podporu AJAX ve službě WCF:  
  
-   Vysvětlení, jak jsou data přenášena mezi klientem stránky AJAX a služby WCF pomocí JavaScriptu a podrobnosti o mapování typů rozhraní .NET Framework pro typy jazyka JavaScript, najdete v tématu [Podpora JSON a jiné přenosu dat formáty](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md).  
  
-   Abyste mohli využívat funkce technologie ASP.NET, například ověřování na základě adresy URL a přístup k informacím o relaci ASP.NET, můžete povolit režim kompatibility ASP.NET prostřednictvím konfigurace.  
  
 Koncových bodů WCF AJAX mohou být využívány i bez rozhraní ASP.NET AJAX framework. Tím jsou nutné znalosti architektury podporu AJAX podpory ve službě WCF. Informace o této architektuře, najdete v části [WCF Web HTTP programovací objektový Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md). Ukázku kódu demonstrace tento přístup, najdete v článku [služba AJAX s JSON a XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="see-also"></a>Viz také  
 [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Postupy: Přidání koncového bodu ASP.NET AJAX bez použití konfigurace](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)  
 [Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)  
 [Postupy: Volba mezi žádostmi HTTP POST a HTTP GET u koncových bodů ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)
