---
title: "Postupy: výběr mezi HTTP POST a HTTP GET požadavky pro koncové body ASP.NET AJAX"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 340f06c760ec4af6427343578790a8dad2d5dd62
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a>Postupy: výběr mezi HTTP POST a HTTP GET požadavky pro koncové body ASP.NET AJAX
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Umožňuje vytvořit službu, která zveřejňuje koncový bod podporou technologie ASP.NET AJAX, který lze volat z jazyka JavaScript na webovém serveru klienta. Ale základní postupy pro vytváření těchto služeb je popsané v [postupy: použití konfigurace k přidání koncového bodu ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) a [postupy: Přidání aplikace ASP.NET AJAX konfigurace koncového bodu bez pomocí](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
 Technologie ASP.NET AJAX podporuje operace, které používají akce HTTP POST a HTTP GET s HTTP POST se výchozí hodnota. Při vytváření operace, která nemá žádné vedlejší účinky a vrátí data, která změní občas nebo vůbec, použijte GET protokolu HTTP. Výsledky operace GET do mezipaměti, což znamená, že několik volání do stejné operace může způsobit pouze jeden požadavek pro vaši službu. Ukládání do mezipaměti není provádí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] , ale může probíhat na kterékoli úrovni (prohlížeč, na serveru proxy a jiných úrovních.) Ukládání do mezipaměti je výhodné, pokud chcete zvýšit výkon služby, ale nemusí být přijatelné, pokud často mění data, nebo pokud operace provede určitou akci.  
  
 Například pokud navrhujete služby ke správě uživatele Knihovna Hudba, operace, která vyhledává umělcem podle výhody title album pomocí GET, ale operace, která přidá album do vlastní kolekce uživatele musíte použít POST.  
  
 Chcete-li řídit Životnost mezipaměti, použijte <xref:System.ServiceModel.Web.OutgoingWebResponseContext> typu. Při navrhování služby, která vrací předpovědi počasí aktualizovat každou hodinu, byste použili získat ale maximální doba uložení do mezipaměti na jednu hodinu nebo méně uživatelé služby zabránit v přístupu k zastaralá data.  
  
 Při použití služeb ze stránky ASP.NET AJAX, které používají řízení správce skriptu, ať už používá operace GET nebo POST - mechanismus skript správce zajistí, že je typ správný požadavku vydané umožňuje žádný rozdíl.  
  
 Operace HTTP GET používají žádné vstupní parametry nepodporuje operace POST, včetně komplexními datovými typy kontrakt. Ve většině případů doporučujeme však vyhnout příliš mnoho parametrů nebo parametry, které jsou v operacích GET příliš složité, protože snižuje efektivitu ukládání do mezipaměti.  
  
 Toto téma ukazuje, jak můžete vybrat, jestli GET a POST pomocí přidání <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> atributy s příslušnými operacemi kontrakt služby. Další kroky (k implementaci, konfigurace a hostitelem služby), které je potřeba získat služba spuštěná jsou podobné těm, které používá služba žádné prvku ASP.NET AJAX v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Operace označené jako <xref:System.ServiceModel.Web.WebGetAttribute> vždy používá požadavek GET. Operace označené jako <xref:System.ServiceModel.Web.WebInvokeAttribute>, nebo není označena s žádným z těchto atributů, používá požadavek POST. <xref:System.ServiceModel.Web.WebInvokeAttribute> Umožňuje použít další příkazy HTTP, jiné než GET a POST (například PUT a DELETE) prostřednictvím <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> vlastnost. Tyto příkazy však nepodporuje prvku ASP.NET AJAX. Pokud máte v úmyslu používat službu ze stránky ASP.NET pomocí ovládacího prvku správce skriptu, nepoužívejte <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> vlastnost.  
  
 Příklad pracovní přepínání GET, naleznete [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázka.  
  
 Příklad, který používá metodu POST, najdete v článku [AJAX služby pomocí HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) ukázka.  
  
### <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a>Vytvoření služby WCF, odpoví na HTTP GET nebo POST protokolu HTTP požadavky  
  
1.  Zadejte základní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontrakt služby s rozhraním označené jako <xref:System.ServiceModel.ServiceContractAttribute> atribut. Označit každou operaci s <xref:System.ServiceModel.OperationContractAttribute>. Přidat <xref:System.ServiceModel.Web.WebGetAttribute> atribut ke stanovení, zda operace by měla odpovídat na požadavky HTTP GET. Můžete také přidat <xref:System.ServiceModel.Web.WebInvokeAttribute> atribut k explicitnímu zadání HTTP POST, nebo není uveden atribut, který se standardně HTTP POST.  
  
    ```  
    [ServiceContract]  
    public interface IMusicService  
    {  
        //This operation uses a GET method.  
        [OperationContract]  
        [WebGet]  
        string LookUpArtist(string album);  
  
        //This operation will use a POST method.  
        [OperationContract]  
        [WebInvoke]  
        void AddAlbum(string user, string album);  
  
        //This operation will use POST method by default  
        //since nothing else is explicitly specified.  
        [OperationContract]  
        string[] GetAlbums(string user);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2.  Implementace `IMusicService` kontrakt služby s `MusicService`.  
  
    ```  
    public class MusicService : IMusicService  
    {  
        public void AddAlbum(string user, string album)  
        {  
            //Add implementation here.  
        }  
  
         //Other operations omitted…  
    }  
    ```  
  
3.  Vytvořte nový soubor s názvem služby s příponou .svc v aplikaci. Tento soubor upravit přidáním odpovídající [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) direktivy informace pro službu. Určit, že <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> má být použita v [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) směrnice pro automatickou konfiguraci koncového bodu ASP.NET AJAX.  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
### <a name="to-call-the-service"></a>Pro volání služby  
  
1.  Operace GET vaší služby bez žádný kód klienta, můžete otestovat pomocí prohlížeče. Například pokud vaše služba je nakonfigurována na adrese "http://example.com/service.svc", do panelu Adresa prohlížeče zadáním příkazu "http://example.com/service.svc/LookUpArtist?album=SomeAlbum" vyvolá službu a způsobí, že odpověď na být stáhnout nebo zobrazit.  
  
2.  Služby můžete použít s operacemi GET stejným způsobem jako jiné služby prvku ASP.NET AJAX – zadáním službu Řízení adresu URL do kolekce skripty správce skript AJAX technologie ASP.NET. Příklad, naleznete v části [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md).  
  
## <a name="see-also"></a>Viz také  
 [Vytváření služeb WCF pro ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [Postupy: migrace technologie AJAX webových služeb ASP.NET na WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
