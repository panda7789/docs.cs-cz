---
title: 'Postupy: Volba mezi žádostmi HTTP POST a HTTP GET u koncových bodů ASP.NET AJAX'
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: 33763a77d1ab1c82af9b9e1fb9c42d72392f8798
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047227"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a>Postupy: Volba mezi žádostmi HTTP POST a HTTP GET u koncových bodů ASP.NET AJAX

Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zpřístupňuje koncový bod s podporou technologie ASP.NET AJAX, který může být volána z jazyka JavaScript na webové stránce klienta. Základní postupy pro vytváření těchto služeb je podrobněji popsána [jak: Použití konfigurace k přidání koncového bodu ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) a [jak: Přidání koncového bodu ASP.NET AJAX bez použití konfiguračního](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
 ASP.NET AJAX podporuje operace, které používají operace HTTP POST a HTTP GET, pomocí HTTP POST, je výchozí hodnota. Při vytváření operace, která nemá žádné vedlejší účinky a vrací data, která se mění jen zřídka nebo vůbec, použijte GET protokolu HTTP. Výsledky operací GET můžete uložit do mezipaměti, což znamená, že několik volání do stejné operace mohou způsobit pouze jeden požadavek na vaši službu. Ukládání do mezipaměti se provádí WCF, ale může probíhat na libovolné úrovni (do prohlížeče uživatele, na proxy server a další úrovně.) Ukládání do mezipaměti je výhodné, pokud chcete zvýšit výkon služby, ale nemusí být akceptovatelné Pokud, data se často mění, nebo pokud operace provede určitou akci.  
  
 Například pokud navrhujete služby ke správě uživatele hudební knihovnu, operace, která vyhledá interpreta podle výhody alba název pomocí GET, ale operaci, která přidá alba do vlastní kolekce uživatele musíte použít příspěvku.  
  
 Pokud chcete řídit dobu životnosti mezipaměti, použijte <xref:System.ServiceModel.Web.OutgoingWebResponseContext> typu. Při návrhu služby, která vrací předpověď počasí aktualizován po hodinách, můžete využít získat ale omezit dobu uložení do mezipaměti na jednu hodinu nebo méně zabránit v přístupu k zastaralých dat uživatelům této služby.  
  
 Při použití služby ze stránky technologie ASP.NET AJAX využívající ovládací prvek správce skriptů, už nezáleží, jestli používá operace GET nebo POST - mechanismus skript správce zajišťuje, že typ správnou žádost vydává.  
  
 Operace GET protokolu HTTP používají vstupní parametry. podporované operace POST, včetně komplexních datových typů kontraktu. Ve většině případů doporučujeme ale příliš mnoha parametry ani parametry, které jsou příliš složité v operace GET, protože snižuje efektivita ukládání do mezipaměti.  
  
 Toto téma ukazuje, jak vybrat mezi GET a POST přidáním <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> atributy do příslušné operace v kontraktu služby. Další kroky (k implementaci, konfiguraci a hostitelem služby), které jsou požadovány pro spuštění služby jsou podobné těm, které používá služba všechny technologie ASP.NET AJAX ve službě WCF.  
  
 Operace označené <xref:System.ServiceModel.Web.WebGetAttribute> vždy používá požadavek GET. Operace označené <xref:System.ServiceModel.Web.WebInvokeAttribute>, nebo není označená pomocí některé z těchto atributů, používá požadavek POST. <xref:System.ServiceModel.Web.WebInvokeAttribute> Umožňuje používat další příkazy HTTP, jiné než GET a POST (například PUT a DELETE) prostřednictvím <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> vlastnost. Tyto příkazy však nepodporuje technologie ASP.NET AJAX. Pokud máte v úmyslu používat službu ze stránky ASP.NET s využitím ovládací prvek správce skriptů, nepoužívejte <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> vlastnost.  
  
 Funkční příklad přepínání GET, najdete v článku [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) vzorku.  
  
 Příklad, který používá metodu POST, najdete v článku [AJAX služba využívající HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) vzorku.  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a>Vytvoření služby WCF, který reaguje na HTTP GET nebo POST protokolu HTTP žádosti
  
1. Definování základní kontraktu služby WCF s rozhraním označené <xref:System.ServiceModel.ServiceContractAttribute> atribut. Označit každou operaci s <xref:System.ServiceModel.OperationContractAttribute>. Přidat <xref:System.ServiceModel.Web.WebGetAttribute> atribut stanoví, že operace by měla reagovat na požadavky HTTP GET. Můžete také přidat <xref:System.ServiceModel.Web.WebInvokeAttribute> atribut s ohledem na HTTP POST, nebo není zadán atribut výchozí nastavení je HTTP POST.
  
    ```csharp
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
  
2. Implementace `IMusicService` kontrakt služby s `MusicService`.
  
    ```csharp
    public class MusicService : IMusicService  
    {  
        public void AddAlbum(string user, string album)  
        {  
            //Add implementation here.  
        }  
  
         //Other operations omitted…  
    }  
    ```  
  
3. Vytvořte nový soubor s názvem služby s příponou .svc v aplikaci. Tento soubor upravit tak, že přidáte odpovídající [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) direktiv informace pro službu. Určit, že <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> se použije [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) směrnice pro automatickou konfiguraci koncového bodu ASP.NET AJAX.  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a>Volání služby  
  
1. Operace GET vaší služby bez žádný kód klienta, můžete otestovat pomocí prohlížeče. Například, pokud vaše služba je nakonfigurována na `http://example.com/service.svc` adresu zadáním `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` do prohlížeče adresa vyvolá službu a způsobí, že odpověď na stažení nebo zobrazení.
  
2. Služby můžete použít s operacemi GET stejným způsobem jako jiné služby technologie ASP.NET AJAX – tak, že zadáte službu ovládací prvek adresy URL do kolekce skriptů správce skriptů AJAX technologie ASP.NET. Příklad najdete v tématu [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md).
  
## <a name="see-also"></a>Viz také:

- [Vytváření služeb WCF pro ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Postupy: Migrace s povoleným AJAX webových služeb ASP.NET na WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
