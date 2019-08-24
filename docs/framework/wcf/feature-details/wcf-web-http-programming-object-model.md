---
title: Programovací objektový model WCF Web HTTP
ms.date: 03/30/2017
ms.assetid: ed96b5fc-ca2c-4b0d-bdba-d06b77c3cb2a
ms.openlocfilehash: 43ec16927c703ca373eaa4299093503b2fab2266
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988565"
---
# <a name="wcf-web-http-programming-object-model"></a>Programovací objektový model WCF Web HTTP
Programovací model webového HTTP WCF umožňuje vývojářům vystavit webové služby Windows Communication Foundation (WCF) prostřednictvím základních požadavků HTTP bez vyžadování protokolu SOAP. Model programování webové služby HTTP WCF je postaven nad existujícím modelem rozšiřitelnosti WCF. Definuje následující třídy:  
  
 **Programovací model:**  
  
- <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>  
  
- <xref:System.ServiceModel.Web.WebGetAttribute>  
  
- <xref:System.ServiceModel.Web.WebInvokeAttribute>  
  
- <xref:System.ServiceModel.Web.WebServiceHost>  
  
 **Kanály a Dispečerská infrastruktura:**  
  
- <xref:System.ServiceModel.WebHttpBinding>  
  
- <xref:System.ServiceModel.Description.WebHttpBehavior>  
  
 **Třídy nástrojů a body rozšiřitelnosti:**  
  
- <xref:System.UriTemplate>  
  
- <xref:System.UriTemplateTable>  
  
- <xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
- <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>  
  
## <a name="aspnetcacheprofileattribute"></a>AspNetCacheProfileAttribute  
 V <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>případě použití na operaci služby označuje profil výstupní mezipaměti ASP.NET v konfiguračním souboru, který by měl být použit pro ukládání odpovědí z operace do výstupní mezipaměti ASP .NET. Tato vlastnost přijímá pouze jeden parametr, název profilu mezipaměti, který určuje nastavení mezipaměti v konfiguračním souboru.  
  
## <a name="webgetattribute"></a>WebGetAttribute  
 <xref:System.ServiceModel.Web.WebGetAttribute> Atribut slouží k označení operace služby jako jednoho, který reaguje na požadavky HTTP GET. Jedná se o chování pasivní operace ( <xref:System.ServiceModel.Description.IOperationBehavior> metody nedělají nic), které přidávají metadata k popisu operace. Použití funkce <xref:System.ServiceModel.Description.WebHttpBehavior>nemá žádný vliv, pokud se do kolekce chování služby přidá chování, které vyhledá tato metadata v popisu operace (konkrétně). <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebGetAttribute> Atribut přebírá volitelné parametry, které jsou uvedeny v následující tabulce.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`BodyStyle`|Určuje, jestli se mají zabalit žádosti a odpovědi odeslané a přijaté z operace služby, na kterou se atribut aplikuje.|  
|`RequestFormat`|Určuje způsob formátování zpráv požadavků.|  
|`ResponseFormat`|Určuje, jak mají být zprávy odpovědí formátovány.|  
|`UriTemplate`|Určuje šablonu identifikátoru URI, která určuje, které požadavky HTTP se mapují na operaci služby, na kterou je atribut použit.|  
  
## <a name="webhttpbinding"></a>WebHttpBinding  
 Třída zahrnuje podporu pro XML, JSON a Nezpracovaná binární data <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>pomocí. <xref:System.ServiceModel.WebHttpBinding> Skládá se z <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> <xref:System.ServiceModel.Channels.HttpTransportBindingElement> <xref:System.ServiceModel.WebHttpSecurity> objektu a objektu. Je určen k použití ve spojení <xref:System.ServiceModel.Description.WebHttpBehavior>s. <xref:System.ServiceModel.WebHttpBinding>  
  
## <a name="webinvokeattribute"></a>WebInvokeAttribute  
 Atribut je podobný <xref:System.ServiceModel.Web.WebGetAttribute>, ale používá se k označení operace služby jako takové, která reaguje na požadavky HTTP jiné než Get. <xref:System.ServiceModel.Web.WebInvokeAttribute> Jedná se o chování pasivní operace ( <xref:System.ServiceModel.Description.IOperationBehavior> metody nedělají nic), které přidávají metadata k popisu operace. Použití funkce <xref:System.ServiceModel.Description.WebHttpBehavior>nemá žádný vliv, pokud se do kolekce chování služby přidá chování, které vyhledá tato metadata v popisu operace (konkrétně). <xref:System.ServiceModel.Web.WebInvokeAttribute>  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> Atribut přebírá volitelné parametry, které jsou uvedeny v následující tabulce.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`BodyStyle`|Určuje, jestli se mají zabalit žádosti a odpovědi odeslané a přijaté z operace služby, na kterou se atribut aplikuje.|  
|`Method`|Určuje metodu HTTP, na kterou je operace služby namapovaná.|  
|`RequestFormat`|Určuje způsob formátování zpráv požadavků.|  
|`ResponseFormat`|Určuje, jak mají být zprávy odpovědí formátovány.|  
|`UriTemplate`|Určuje šablonu identifikátoru URI, která určuje, které požadavky GET se mapují na operaci služby, na kterou je atribut použit.|  
  
## <a name="uritemplate"></a>UriTemplate  
 <xref:System.UriTemplate> Třída umožňuje definovat sadu strukturovaných podobných identifikátorů URI. Šablony se skládají ze dvou částí, cesty a dotazu. Cesta se skládá z řady segmentů oddělených lomítkem (/). Každý segment může mít literálovou hodnotu, hodnotu proměnné (napsanou v rámci složených závorek [{}], která je omezená tak, aby odpovídala obsahu přesně jednoho segmentu), nebo zástupný znak (napsaný jako hvězdička [\*], který odpovídá "zbytek cesty"), který se musí objevit v konec cesty Výraz dotazu může být zcela vynechán. Je-li k dispozici, určuje neuspořádanou řadu párů název/hodnota. Prvky výrazu dotazu mohou být buď páry literálů (? x = 2), nebo páry proměnných (? x = {*Value*}). Nespárované hodnoty nejsou povolené. <xref:System.UriTemplate>používá se interně WEBOVÝm modelem HTTP pro WCF k mapování konkrétních identifikátorů URI nebo skupin identifikátorů URI na operace služby.  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 Třída představuje asociativní <xref:System.UriTemplate> sadu objektů svázaných s objektem výběru vývojáře. <xref:System.UriTemplateTable> Umožňuje párovat kandidáty identifikátorů URI (Uniform Resource Identifier) proti šablonám v sadě a načíst data přidružená k odpovídajícím šablonám. <xref:System.UriTemplateTable>používá se interně WEBOVÝm modelem HTTP pro WCF k mapování konkrétních identifikátorů URI nebo skupin identifikátorů URI na operace služby.  
  
## <a name="webservicehost"></a>WebServiceHost  
 <xref:System.ServiceModel.Web.WebServiceHost>rozšiřuje rozhraní <xref:System.ServiceModel.ServiceHost> , aby bylo snazší hostovat službu, která není webovým stylem SOAP. Pokud <xref:System.ServiceModel.Web.WebServiceHost> nenalezne v popisu služby žádné koncové body, automaticky vytvoří výchozí koncový bod na základní adrese služby. Při vytváření výchozího koncového bodu http <xref:System.ServiceModel.Web.WebServiceHost> také zakáže stránku Nápověda http a funkci WSDL (Web Services Description Language), takže koncový bod metadat nekoliduje s výchozím koncovým bodem http. <xref:System.ServiceModel.Web.WebServiceHost>také zajistí, že všechny koncové body <xref:System.ServiceModel.WebHttpBinding> , které používají <xref:System.ServiceModel.Description.WebHttpBehavior> , mají požadované připojené. <xref:System.ServiceModel.Web.WebServiceHost> Nakonec automaticky nakonfiguruje vazbu koncového bodu tak, aby fungovala s přidruženými nastaveními zabezpečení Internetová informační služba (IIS) při použití v zabezpečeném virtuálním adresáři.  
  
## <a name="webservicehostfactory"></a>WebServiceHostFactory  
 Třída se používá k dynamickému vytváření a <xref:System.ServiceModel.Web.WebServiceHost> při hostování služby v rámci služby Internetová informační služba (IIS) nebo aktivační služby procesů systému Windows (WAS). <xref:System.ServiceModel.Activation.WebServiceHostFactory> Na rozdíl od samoobslužné služby <xref:System.ServiceModel.Web.WebServiceHost>, ve které hostující aplikace vytváří instance, služby hostované v rámci služby IIS nebo tuto třídu použil k <xref:System.ServiceModel.Web.WebServiceHost> vytvoření pro službu. Metoda <xref:System.ServiceModel.Activation.WebServiceHostFactory.CreateServiceHost%28System.Type%2CSystem.Uri%5B%5D%29> je volána, když je přijata příchozí žádost o službu.  
  
## <a name="webhttpbehavior"></a>WebHttpBehavior  
 <xref:System.ServiceModel.Description.WebHttpBehavior> Třída poskytuje potřebné formátovací moduly, selektory operací atd., které jsou vyžadovány pro podporu služeb webového stylu v rámci vrstvy modelu služby. To je implementováno jako chování koncového bodu (používá se ve <xref:System.ServiceModel.WebHttpBinding>spojení s) a umožňuje pro každý koncový bod zadat formátovací moduly a selektory operací, což umožňuje, aby stejná implementace služby zveřejnila koncové body SOAP i POX.  
  
### <a name="extending-webhttpbehavior"></a>Rozšíření WebHttpBehavior  
 <xref:System.ServiceModel.Description.WebHttpBehavior>je rozšiřitelná pomocí <xref:System.ServiceModel.Description.WebHttpBehavior.GetOperationSelector%28System.ServiceModel.Description.ServiceEndpoint%29>několika virtuálních metod:, <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>a <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>. Vývojáři mohou odvodit třídu z <xref:System.ServiceModel.Description.WebHttpBehavior> a přepsat tyto metody pro přizpůsobení výchozího chování.  
  
 Je příkladem rozšíření <xref:System.ServiceModel.Description.WebHttpBehavior>. <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>povoluje koncovým bodům Windows Communication Foundation (WCF) přijímat požadavky HTTP z klienta AJAX v prohlížeči ASP.NET. [Služba AJAX využívající HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) je příkladem použití tohoto bodu rozšiřitelnosti.  
  
> [!WARNING]
> <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>Při použití <xref:System.UriTemplate> nejsou podporovány v rámci <xref:System.ServiceModel.Web.WebGetAttribute> atributů nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> .  
  
## <a name="webhttpdispatchoperationselector"></a>WebHttpDispatchOperationSelector  
 Třída používá <xref:System.UriTemplate> třídy a<xref:System.UriTemplateTable> k odesílání volání operací služby. <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>  
  
## <a name="compatibility"></a>Kompatibilita  
 Model programování webových služeb HTTP WCF nepoužívá zprávy založené na protokolu SOAP, a proto nepodporuje protokoly WS-*. Stejný kontrakt ale můžete zveřejnit pomocí dvou různých koncových bodů: jednoho pomocí protokolu SOAP a jiného bez použití protokolu SOAP. Viz [jak: Příklad Zveřejnění kontraktu pro SOAP a webové](../../../../docs/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) klienty.  
  
## <a name="security"></a>Zabezpečení  
 Vzhledem k tomu, že model programování webového HTTP WCF nepodporuje protokoly WS-*, jediným způsobem, jak zabezpečit webovou službu založenou na programovacím modelu webového HTTP WCF, je vystavení vaší služby pomocí protokolu SSL. Další informace o nastavení SSL se službou IIS 7,0 najdete v tématu [implementace protokolu SSL ve službě IIS](https://go.microsoft.com/fwlink/?LinkId=131613) .  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>
- [Přehled programovacího modelu webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
