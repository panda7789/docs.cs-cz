---
title: 'Postupy: Volba mezi žádostmi HTTP POST a HTTP GET u koncových bodů ASP.NET AJAX'
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: 0f7a221d1fd14b4a978683f008858e35cbd2df19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184759"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a>Postupy: Volba mezi žádostmi HTTP POST a HTTP GET u koncových bodů ASP.NET AJAX

Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zveřejňuje koncový bod s podporou ASP.NET AJAX, který lze volat z Jazyka JavaScript na klientském webu. Základní postupy pro vytváření těchto služeb je popsána v [Postup: Použití konfigurace přidat ASP.NET koncový bod AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) a [jak: Přidat ASP.NET koncový bod AJAX bez použití konfigurace](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
 ASP.NET AJAX podporuje operace, které používají http post a HTTP GET slovesa, s HTTP POST je výchozí. Při vytváření operace, která nemá žádné vedlejší účinky a vrátí data, která zřídka nebo nikdy nezmění, použijte HTTP GET místo. Výsledky operací GET lze uložit do mezipaměti, což znamená, že více volání stejné operace může mít za následek pouze jeden požadavek na vaši službu. Ukládání do mezipaměti není provedeno WCF, ale může probíhat na libovolné úrovni (v prohlížeči uživatele, na proxy serveru a na jiných úrovních.) Ukládání do mezipaměti je výhodné, pokud chcete zvýšit výkon služby, ale nemusí být přijatelné, pokud se data často mění nebo pokud operace provede nějakou akci.  
  
 Například pokud navrhujete službu pro správu hudební knihovny uživatele, operace, která vyhledá umělce na základě názvu alba výhody z použití GET, ale operace, která přidá album do osobní kolekce uživatele musí používat POST.  
  
 Chcete-li řídit životnost mezipaměti, použijte <xref:System.ServiceModel.Web.OutgoingWebResponseContext> typ. Například při navrhování služby, která vrací předpovědi počasí aktualizovány každou hodinu, byste použít GET, ale omezit dobu trvání mezipaměti na hodinu nebo méně, aby se zabránilo uživatelům služby v přístupu k zastaralým datům.  
  
 Při použití služeb ze stránky ASP.NET AJAX, které používají ovládací prvek Správce skriptů, je jedno, zda operace používá GET nebo POST - mechanismus správce skriptů zajišťuje, že je vydán správný typ požadavku.  
  
 Operace HTTP GET používají všechny vstupní parametry podporované operacemi POST, včetně typů složitých datových kontraktů. Ve většině případů se však doporučuje vyhnout se příliš mnoha parametrům nebo parametrům, které jsou v operacích GET příliš složité, protože snižují efektivitu ukládání do mezipaměti.  
  
 Toto téma ukazuje, jak vybrat mezi <xref:System.ServiceModel.Web.WebGetAttribute> GET <xref:System.ServiceModel.Web.WebInvokeAttribute> a POST přidáním atributů nebo do příslušných operací v servisní smlouvě. Další kroky (k implementaci, konfiguraci a hostování služby), které jsou nutné k získání služby běží jsou podobné těm, které používají všechny ASP.NET služby AJAX v WCF.  
  
 Operace označená <xref:System.ServiceModel.Web.WebGetAttribute> vždy používá požadavek GET. Operace označená <xref:System.ServiceModel.Web.WebInvokeAttribute>nebo neoznačená žádným ze dvou atributů používá požadavek POST. Umožňuje <xref:System.ServiceModel.Web.WebInvokeAttribute> použití jiných http slovesa, jiné než GET a POST (například PUT a DELETE) prostřednictvím vlastnosti. <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> Tato slovesa však nejsou podporovány ASP.NET AJAX. Pokud máte v úmyslu použít službu z ASP.NET stránek pomocí <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> ovládacího prvku Správce skriptů, nepoužívejte vlastnost.  
  
 Pracovní příklad přechodu na GET, naleznete základní [AJAX service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázka.  
  
 Ukázka, která používá POST, naleznete [v ajax služby pomocí http post](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) ukázku.  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a>Vytvoření služby WCF, která reaguje na požadavky HTTP GET nebo HTTP POST
  
1. Definujte základní servisní smlouvu WCF <xref:System.ServiceModel.ServiceContractAttribute> s rozhraním označeným atributem. Každou operaci označte pomocí <xref:System.ServiceModel.OperationContractAttribute>. Přidejte <xref:System.ServiceModel.Web.WebGetAttribute> atribut a stanovte, že operace by měla odpovídat na požadavky HTTP GET. Můžete také přidat <xref:System.ServiceModel.Web.WebInvokeAttribute> atribut explicitně určit HTTP POST, nebo ne zadat atribut, který výchozí http post.
  
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
  
2. Dokončujte `IMusicService` `MusicService`servisní smlouvu s .
  
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
  
3. Vytvořte nový soubor s názvem služby s příponou SVC v aplikaci. Upravte tento soubor [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) přidáním příslušných informací směrnice ServiceHost pro službu. Určete, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> že má být použit v [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) směrnice automaticky konfigurovat koncový bod ASP.NET AJAX.  
  
    ```
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a>Chcete-li volat službu  
  
1. Pomocí prohlížeče můžete otestovat operace GET vaší služby bez kódu klienta. Pokud je například vaše služba `http://example.com/service.svc` nakonfigurována `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` na adrese, potom zadáním do adresního řádku prohlížeče vyvolá službu a způsobí, že odpověď bude stažena nebo zobrazena.
  
2. Služby s operacemi GET můžete používat stejným způsobem jako všechny ostatní služby ASP.NET AJAX – zadáním adresy URL služby do kolekce Skripty ASP.NET ovládacího prvku AJAX Script Manager. Příklad naleznete v části [Základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md).
  
## <a name="see-also"></a>Viz také

- [Vytváření služeb WCF pro ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Postupy: Migrace webových služeb ASP.NET s podporou AJAXu na službu WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
