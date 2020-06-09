---
title: 'Postupy: Volba mezi žádostmi HTTP POST a HTTP GET u koncových bodů ASP.NET AJAX'
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: 15d7ad43ce9120e97aba9119aff6a6c1a19f301f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596913"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a>Postupy: Volba mezi žádostmi HTTP POST a HTTP GET u koncových bodů ASP.NET AJAX

Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zveřejňuje koncový bod s povoleným ASP.NET AJAX, který se dá volat z JavaScriptu na klientském webu. Základní postupy pro sestavování takových služeb jsou popsány v tématu [Postupy: použití konfigurace k přidání koncového bodu ASP.NET AJAX](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) a [Postup: Přidání koncového bodu ASP.NET AJAX bez použití konfigurace](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
 ASP.NET AJAX podporuje operace, které používají příkazy HTTP POST a HTTP GET, přičemž HTTP POST je výchozí. Při vytváření operace, která nemá žádné vedlejší účinky, a vrátí data, která se zřídka nebo nikdy nemění, použijte místo toho HTTP GET. Výsledky operací GET lze ukládat do mezipaměti, což znamená, že více volání stejné operace může mít za následek pouze jeden požadavek na vaši službu. Služba WCF neprovádí ukládání do mezipaměti, ale může probíhat na libovolné úrovni (v prohlížeči uživatele, na proxy server a na jiných úrovních.) Ukládání do mezipaměti je výhodné, pokud chcete zvýšit výkon služby, ale nemusí být přijatelné, pokud se data často mění nebo pokud operace provádí určitou akci.  
  
 Například pokud navrhujete službu pro správu hudební knihovny uživatele, operace, která vyhledá interpreta v závislosti na názvu alba, je výhodná pro použití GET, ale operace, která přidá album do osobní kolekce uživatele, musí používat POST.  
  
 Chcete-li řídit dobu života mezipaměti, použijte <xref:System.ServiceModel.Web.OutgoingWebResponseContext> typ. Například při navrhování služby, která vrátí každou hodinu aktualizovanou předpověď počasí, byste měli použít možnost získat, ale omezit dobu trvání mezipaměti na hodinu nebo méně, aby uživatelé služby nemohli přistupovat k zastaralým datům.  
  
 Při používání služeb ze stránky ASP.NET AJAX, která používá ovládací prvek Správce skriptů, neprovede žádný rozdíl bez ohledu na to, zda operace používá funkci GET nebo POST – mechanismus správce skriptu zajišťuje, aby byl vydán správný typ žádosti.  
  
 Operace HTTP GET používají všechny vstupní parametry, které podporuje operace POST, včetně složitých typů kontraktů dat. Ve většině případů se ale doporučuje vyhnout se příliš mnoha parametrům nebo parametrům, které jsou příliš složité v operacích GET, protože se snižuje efektivita ukládání do mezipaměti.  
  
 Toto téma ukazuje, jak vybrat mezi GET a POST přidáním <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> atributů nebo do relevantních operací v kontraktu služby. Ostatní kroky (k implementaci, konfiguraci a hostování služby), které jsou potřeba k tomu, aby služba běžela, jsou podobné těm, které používá služba ASP.NET AJAX ve službě WCF.  
  
 Operace označená pomocí <xref:System.ServiceModel.Web.WebGetAttribute> vždy používá požadavek GET. Operace označená pomocí <xref:System.ServiceModel.Web.WebInvokeAttribute> , nebo není označená žádným z těchto dvou atributů, používá požadavek POST. <xref:System.ServiceModel.Web.WebInvokeAttribute>Umožňuje použít jiné příkazy HTTP, než Get a post (například PUT a Delete) prostřednictvím <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> Vlastnosti. Nicméně ASP.NET AJAX nepodporuje tyto příkazy. Pokud máte v úmyslu používat službu ze stránek ASP.NET pomocí ovládacího prvku Správce skriptů, nepoužívejte <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> vlastnost.  
  
 Pracovní příklad přepínání na získání najdete v ukázce [základní služby AJAX](../samples/basic-ajax-service.md) .  
  
 Ukázku, která používá POST, najdete v ukázce [služby AJAX pomocí protokolu HTTP POST](../samples/ajax-service-using-http-post.md) .  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a>Vytvoření služby WCF, která reaguje na požadavky HTTP GET nebo HTTP POST
  
1. Definujte základní kontrakt služby WCF s rozhraním označeným <xref:System.ServiceModel.ServiceContractAttribute> atributem. Označte každou operaci pomocí <xref:System.ServiceModel.OperationContractAttribute> . Přidejte <xref:System.ServiceModel.Web.WebGetAttribute> atribut, který stanoví, že operace by měla reagovat na požadavky HTTP GET. Můžete také přidat <xref:System.ServiceModel.Web.WebInvokeAttribute> atribut pro explicitní určení http post nebo Neurčovat atribut, který má výchozí hodnotu http post.
  
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
  
2. Implementujte `IMusicService` kontrakt služby s `MusicService` .
  
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
  
3. V aplikaci vytvořte nový soubor s názvem služba s příponou. svc. Upravte tento soubor přidáním příslušné informace o direktivě [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) pro službu. Určete, že se má <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> použít v direktivě [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) k automatické konfiguraci koncového bodu ASP.NET AJAX.  
  
    ```
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a>Volání služby  
  
1. Pomocí prohlížeče můžete testovat operace GET vaší služby bez jakéhokoli klientského kódu. Například pokud je vaše služba nakonfigurovaná na `http://example.com/service.svc` adrese, pak se zadáním `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` do panelu Adresa prohlížeče vyvolá služba a dojde ke stažení nebo zobrazení odpovědi.
  
2. Služby s operacemi GET můžete používat stejným způsobem jako jakékoli jiné ASP.NET služby AJAX – zadáním adresy URL služby do kolekce Scripts v ovládacím prvku Správce skriptů ASP.NET AJAX. Příklad naleznete v tématu [základní služba AJAX](../samples/basic-ajax-service.md).
  
## <a name="see-also"></a>Viz také

- [Vytváření služeb WCF pro ASP.NET AJAX](creating-wcf-services-for-aspnet-ajax.md)
- [Postupy: Migrace webových služeb ASP.NET s podporou AJAXu na službu WCF](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
