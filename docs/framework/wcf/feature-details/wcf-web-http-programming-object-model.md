---
title: Programovací objektový model WCF Web HTTP
ms.date: 03/30/2017
ms.assetid: ed96b5fc-ca2c-4b0d-bdba-d06b77c3cb2a
ms.openlocfilehash: e15f616aa7ef9502176c5d508f8d8882e2a5bd47
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739362"
---
# <a name="wcf-web-http-programming-object-model"></a>Programovací objektový model WCF Web HTTP
HTTP programovacího modelu WCF WEB umožňuje vývojářům vystavit služby Windows Communication Foundation (WCF) Web prostřednictvím základních požadavků protokolu HTTP bez nutnosti SOAP. HTTP programovacího modelu WCF WEB je postavený na existující model rozšiřitelnosti WCF. Definuje následující třídy:  
  
 **Programovací Model:**  
  
-   <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>  
  
-   <xref:System.ServiceModel.Web.WebGetAttribute>  
  
-   <xref:System.ServiceModel.Web.WebInvokeAttribute>  
  
-   <xref:System.ServiceModel.Web.WebServiceHost>  
  
 **Kanály a dispečeru infrastruktury:**  
  
-   <xref:System.ServiceModel.WebHttpBinding>  
  
-   <xref:System.ServiceModel.Description.WebHttpBehavior>  
  
 **Třídy nástrojů a bodů rozšiřitelnosti:**  
  
-   <xref:System.UriTemplate>  
  
-   <xref:System.UriTemplateTable>  
  
-   <xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
-   <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>  
  
## <a name="aspnetcacheprofileattribute"></a>AspNetCacheProfileAttribute  
 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, Při použití na operaci služby, označuje, technologie ASP.NET profil výstupní mezipaměti v konfiguračním souboru, který by měly být používány do mezipaměti odpovědi z operace do výstupní mezipaměti ASP .NET. Tato vlastnost má pouze jeden parametr, název profilu mezipaměti, která určuje nastavení mezipaměti v konfiguračním souboru.  
  
## <a name="webgetattribute"></a>WebGetAttribute  
 <xref:System.ServiceModel.Web.WebGetAttribute> Atribut se používá k označení operace služby jako ten, který reaguje na požadavky HTTP GET. Je pasivní operace chování ( <xref:System.ServiceModel.Description.IOperationBehavior> metody nedělat nic), který přidá metadata do popis operace. Použití <xref:System.ServiceModel.Web.WebGetAttribute> nemá žádný vliv, pokud chování, která hledá tato metadata v popisu operace (konkrétně <xref:System.ServiceModel.Description.WebHttpBehavior>) se přidá do kolekce chování služby. <xref:System.ServiceModel.Web.WebGetAttribute> Atribut přebírá volitelné parametry uvedené v následující tabulce.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`BodyStyle`|Určuje, jestli se má zabalit požadavky a odpovědi odesílané do a z atributu se použije na operaci služby.|  
|`RequestFormat`|Určuje, jak jsou zprávy požadavku ve formátu.|  
|`ResponseFormat`|Určuje formátování zprávy odpovědi.|  
|`UriTemplate`|Určuje šablonu identifikátoru URI, který řídí, jaké požadavky HTTP mapována na atribut se použije na operaci služby.|  
  
## <a name="webhttpbinding"></a>WebHttpBinding  
 <xref:System.ServiceModel.WebHttpBinding> Třída zahrnuje podporu pro XML, JSON a používání Nezpracovaná binární data <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>. Skládá se z <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpTransportBindingElement> a <xref:System.ServiceModel.WebHttpSecurity> objektu. <xref:System.ServiceModel.WebHttpBinding> Používá ve spojení s <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
## <a name="webinvokeattribute"></a>WebInvokeAttribute  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> Atribut je podobný <xref:System.ServiceModel.Web.WebGetAttribute>, ale používá se k označení operace služby, jako ten, který reaguje na HTTP žádosti jiných než metoda GET. Je pasivní operace chování ( <xref:System.ServiceModel.Description.IOperationBehavior> metody nedělat nic), který přidá metadata do popis operace. Použití <xref:System.ServiceModel.Web.WebInvokeAttribute> nemá žádný vliv, pokud chování, která hledá tato metadata v popisu operace (konkrétně <xref:System.ServiceModel.Description.WebHttpBehavior>) se přidá do kolekce chování služby.  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> Atribut přebírá volitelné parametry uvedené v následující tabulce.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`BodyStyle`|Určuje, jestli se má zabalit požadavky a odpovědi odesílané do a z atributu se použije na operaci služby.|  
|`Method`|Určuje metodu HTTP, operace služby je namapována na.|  
|`RequestFormat`|Určuje, jak jsou zprávy požadavku ve formátu.|  
|`ResponseFormat`|Určuje formátování zprávy odpovědi.|  
|`UriTemplate`|Určuje šablonu identifikátoru URI, který řídí, jaké požadavky GET mapována na atribut se použije na operaci služby.|  
  
## <a name="uritemplate"></a>UriTemplate  
 <xref:System.UriTemplate> Třída umožňují definovat sadu strukturálně podobné identifikátorů URI. Šablony se skládají ze dvou částí, cestu a dotaz. Cesta se skládá z řady segmentů oddělených lomítkem (/). Každý segment může mít hodnotu literálu, hodnotu proměnné (napsané ve složených závorkách {[}], tak, aby odpovídaly obsah přesně jeden segment omezené) nebo zástupný znak (zapsán jako hvězdičku [\*], který odpovídá "zbývající část cesty"), která se musí nacházet v konce cesty. Výraz dotazu můžete zcela vynechat. Pokud jsou k dispozici, určuje Neseřazený řady párů název/hodnota. Elementy výrazu dotazu může být buď literál páry (? x = 2) nebo dvojice proměnné (? x = {*hodnotu*}). Nespárované hodnoty nejsou povoleny. <xref:System.UriTemplate> se používá interně pomocí protokolu HTTP programovacího modelu WCF WEB k mapování konkrétní identifikátory URI nebo skupiny identifikátorů URI k operacím služby.  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 <xref:System.UriTemplateTable> Třída reprezentuje asociativní sadu <xref:System.UriTemplate> objekty vázané na uživatele výběr objektu vývojáře. To umožňuje porovnání šablony v sadě Release candidate Uniform Resource Identifier (identifikátory URI) a načíst data související s odpovídající šablony. <xref:System.UriTemplateTable> se používá interně pomocí protokolu HTTP programovacího modelu WCF WEB k mapování konkrétní identifikátory URI nebo skupiny identifikátorů URI k operacím služby.  
  
## <a name="webservicehost"></a>WebServiceHost  
 <xref:System.ServiceModel.Web.WebServiceHost> rozšiřuje <xref:System.ServiceModel.ServiceHost> zjednodušit hostování-protokolu SOAP stylu webové služby. Pokud <xref:System.ServiceModel.Web.WebServiceHost> najde žádné koncové body v popisu služby se automaticky vytvoří výchozí koncový bod na základní adrese služby. Při vytváření výchozího koncového bodu HTTP, <xref:System.ServiceModel.Web.WebServiceHost> také zakáže stránky s nápovědou HTTP a funkci GET webové služby WSDL (Description Language), takže koncový bod metadat nebude v konfliktu s výchozí koncový bod HTTP. <xref:System.ServiceModel.Web.WebServiceHost> také zajistí, že všechny koncové body, které používají <xref:System.ServiceModel.WebHttpBinding> mají požadovaný <xref:System.ServiceModel.Description.WebHttpBehavior> připojen. Nakonec <xref:System.ServiceModel.Web.WebServiceHost> automaticky nakonfiguruje vazby koncového bodu pro práci s související zabezpečení nastavení Internetové informační služby (IIS) při použití v zabezpečené virtuální adresář.  
  
## <a name="webservicehostfactory"></a>WebServiceHostFactory  
 <xref:System.ServiceModel.Activation.WebServiceHostFactory> Třída se používá dynamicky se vytvářejí <xref:System.ServiceModel.Web.WebServiceHost> když služba hostována v rámci Internetové informační služby (IIS) nebo Windows Process Activation Service (WAS). Na rozdíl od služby v místním prostředí, kde vytvoří instanci hostitelské aplikace <xref:System.ServiceModel.Web.WebServiceHost>, služba hostovaná v IIS nebo byla tato třída slouží k vytvoření <xref:System.ServiceModel.Web.WebServiceHost> pro službu. <xref:System.ServiceModel.Activation.WebServiceHostFactory.CreateServiceHost%28System.Type%2CSystem.Uri%5B%5D%29> Metoda je volána při přijetí příchozího požadavku pro službu.  
  
## <a name="webhttpbehavior"></a>WebHttpBehavior  
 <xref:System.ServiceModel.Description.WebHttpBehavior> Třída poskytuje nezbytné formátovacích modulů, selektory provozu a atd., vyžadované pro podporu stylu webové služby v modelu služby vrstvě. Tato možnost je implementovaná jako chování koncového bodu (použít ve spojení s <xref:System.ServiceModel.WebHttpBinding>) a umožňuje formátovací moduly a operace selektory pro každý koncový bod, který povolí stejné implementaci service zpřístupňují koncové body SOAP a POX.  
  
### <a name="extending-webhttpbehavior"></a>Rozšíření WebHttpBehavior  
 <xref:System.ServiceModel.Description.WebHttpBehavior> je možné rozšířit pomocí čísla virtuální metody: <xref:System.ServiceModel.Description.WebHttpBehavior.GetOperationSelector%28System.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, a <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>. Vývojáři můžou odvodit třídu z <xref:System.ServiceModel.Description.WebHttpBehavior> a přepsat tyto metody můžete přizpůsobit výchozí chování.  
  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> Je příkladem rozšíření <xref:System.ServiceModel.Description.WebHttpBehavior>. <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> Umožňuje Windows Communication Foundation (WCF) koncových bodů pro příjem požadavků HTTP z klienta založené na prohlížeči technologie ASP.NET AJAX. [AJAX služba využívající HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) je příkladem pomocí tohoto bodu rozšiřitelnosti.  
  
> [!WARNING]
>  Při použití <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>, <xref:System.UriTemplate> nejsou podporovány v rámci <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> atributy.  
  
## <a name="webhttpdispatchoperationselector"></a>WebHttpDispatchOperationSelector  
 <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector> Třídy používá <xref:System.UriTemplate> a <xref:System.UriTemplateTable> třídy k odeslání volání operací služby.  
  
## <a name="compatibility"></a>Kompatibilita  
 Nepoužívá založený na protokolu SOAP zprávy HTTP programovacího modelu WCF WEB a proto nepodporuje WS-* protokoly. Ale můžete zpřístupnit stejný kontrakt ve dvou různých koncový bod: jeden pomocí protokolu SOAP a jiné ne pomocí protokolu SOAP. Zobrazit [jak: Zveřejnění kontraktu klientům SOAP a webovým klientům](../../../../docs/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) příklad.  
  
## <a name="security"></a>Zabezpečení  
 Protože HTTP programovacího modelu WCF WEB nepodporuje WS-* protokolů je jediný způsob, jak zabezpečit webová služba založená na protokolu HTTP programovacího modelu WCF WEB k vystavení služby pomocí protokolu SSL. Další informace o nastavení protokolu SSL s [!INCLUDE[iisver](../../../../includes/iisver-md.md)] naleznete v tématu [implementace protokolu SSL ve službě IIS](https://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>
- [Přehled programovacího modelu webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
