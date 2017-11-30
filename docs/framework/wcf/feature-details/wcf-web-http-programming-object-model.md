---
title: "Programovací objektový model WCF Web HTTP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed96b5fc-ca2c-4b0d-bdba-d06b77c3cb2a
caps.latest.revision: "40"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 81a905205666f50f65192c015ea018b05482e0ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="wcf-web-http-programming-object-model"></a>Programovací objektový model WCF Web HTTP
WCF WEB HTTP programovací Model umožňuje vývojářům vystavit [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] webové služby prostřednictvím základních požadavků HTTP bez nutnosti protokolu SOAP. WCF WEB HTTP programovací Model je postavená na existující [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model rozšiřitelnosti. Definuje následující třídy:  
  
 **Model programování:**  
  
-   <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>  
  
-   <xref:System.ServiceModel.Web.WebGetAttribute>  
  
-   <xref:System.ServiceModel.Web.WebInvokeAttribute>  
  
-   <xref:System.ServiceModel.Web.WebServiceHost>  
  
 **Kanály a dispečera infrastruktury:**  
  
-   <xref:System.ServiceModel.WebHttpBinding>  
  
-   <xref:System.ServiceModel.Description.WebHttpBehavior>  
  
 **Třídy nástrojů a bodů rozšiřitelnosti:**  
  
-   <xref:System.UriTemplate>  
  
-   <xref:System.UriTemplateTable>  
  
-   <xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
-   <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>  
  
## <a name="aspnetcacheprofileattribute"></a>AspNetCacheProfileAttribute  
 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, Při použití operace služby, označuje ASP.NET profil výstupní mezipaměti v konfiguračním souboru, který má být používána do mezipaměti odpovědi z operace ve výstupní mezipaměti ASP .NET. Tato vlastnost přijímá pouze jeden parametr, název profilu mezipaměti, která určuje nastavení ukládání do mezipaměti v konfiguračním souboru.  
  
## <a name="webgetattribute"></a>WebGetAttribute  
 <xref:System.ServiceModel.Web.WebGetAttribute> Atribut slouží k označení operace služby jako ten, který reaguje na požadavky HTTP GET. Je pasivní operaci chování ( <xref:System.ServiceModel.Description.IOperationBehavior> metody nedělat nic), přidá metadata k popisu operaci. Použití <xref:System.ServiceModel.Web.WebGetAttribute> nemá žádný vliv, pokud chování, která vypadá pro tato metadata v popisu operace (konkrétně <xref:System.ServiceModel.Description.WebHttpBehavior>) je přidán do kolekce chování služby. <xref:System.ServiceModel.Web.WebGetAttribute> Atribut přebírá volitelné parametry uvedené v následující tabulce.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`BodyStyle`|Určuje, zda zabalit požadavky a odpovědi odesílané do a z atributu se použije na operaci služby.|  
|`RequestFormat`|Určuje způsob formátování zprávy žádosti.|  
|`ResponseFormat`|Určuje způsob formátování zprávy odpovědi.|  
|`UriTemplate`|Určuje identifikátor URI šablonu, která určuje, jaké požadavky HTTP get namapované na atribut se použije na operaci služby.|  
  
## <a name="webhttpbinding"></a>WebHttpBinding  
 <xref:System.ServiceModel.WebHttpBinding> Třída zahrnuje podporu pro XML, JSON a Nezpracovaná binární data pomocí <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>. Skládá se z <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpTransportBindingElement> a <xref:System.ServiceModel.WebHttpSecurity> objektu. <xref:System.ServiceModel.WebHttpBinding> Je určen k použití ve spojení s <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
## <a name="webinvokeattribute"></a>WebInvokeAttribute  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> Atribut je podobná <xref:System.ServiceModel.Web.WebGetAttribute>, ale je použita k označení operace služby, jako ten, který reaguje na HTTP než GET požadavky. Je pasivní operaci chování ( <xref:System.ServiceModel.Description.IOperationBehavior> metody nedělat nic), přidá metadata k popisu operaci. Použití <xref:System.ServiceModel.Web.WebInvokeAttribute> nemá žádný vliv, pokud chování, která vypadá pro tato metadata v popisu operace (konkrétně <xref:System.ServiceModel.Description.WebHttpBehavior>) je přidán do kolekce chování služby.  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> Atribut přebírá volitelné parametry uvedené v následující tabulce.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`BodyStyle`|Určuje, zda zabalit požadavky a odpovědi odesílané do a z atributu se použije na operaci služby.|  
|`Method`|Určuje metodu HTTP, operace služby je namapovaná na.|  
|`RequestFormat`|Určuje způsob formátování zprávy žádosti.|  
|`ResponseFormat`|Určuje způsob formátování zprávy odpovědi.|  
|`UriTemplate`|Určuje identifikátor URI šablonu, která určuje, jaké požadavky GET namapovat do atribut se použije na operaci služby.|  
  
## <a name="uritemplate"></a>UriTemplate  
 <xref:System.UriTemplate> Třída umožňuje definovat sadu strukturálně podobné identifikátory URI. Šablony se skládají ze dvou částí, cesta a dotaz. Cesta se skládá z řady segmentů oddělená lomítko (/). Každý segment může mít hodnotu literálu, hodnota proměnné (zapsané do složených závorek {[}], omezené tak, aby odpovídaly obsah přesně jeden segment) nebo zástupný znak (zapisují jako hvězdičku [\*], který odpovídá "zbývající část cesty"), která se musí nacházet v konec cesty. Zcela lze vynechat výrazu dotazu. Pokud je k dispozici, určuje neuspořádaný řadu dvojice název/hodnota. Elementy výrazu dotazu může být buď literálu páry (? x = 2) nebo proměnné páry (? x = {*hodnotu*}). Nepárové hodnoty nejsou povoleny. <xref:System.UriTemplate>se používá interně pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] webové HTTP programovací Model pro mapování konkrétní identifikátory URI nebo skupiny identifikátorů URI k operacím služby.  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 <xref:System.UriTemplateTable> Třída reprezentuje asociativní sadu <xref:System.UriTemplate> objekty vázána na objekt vývojář je výběr. Umožňuje vám odpovídající identifikátory Uniform Resource (Identifier) candidate šablony v sadě a načíst data související s odpovídající šablony. <xref:System.UriTemplateTable>se používá interně pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] webové HTTP programovací Model pro mapování konkrétní identifikátory URI nebo skupiny identifikátorů URI k operacím služby.  
  
## <a name="webservicehost"></a>Hostitel WebServiceHost  
 <xref:System.ServiceModel.Web.WebServiceHost>rozšiřuje <xref:System.ServiceModel.ServiceHost> usnadnění hostování služby Web-style-protokolu SOAP. Pokud <xref:System.ServiceModel.Web.WebServiceHost> vyhledá žádné koncové body v popisu služby automaticky vytvoří výchozí koncový bod na základní adresa služby. Při vytváření výchozího koncového bodu protokolu HTTP, <xref:System.ServiceModel.Web.WebServiceHost> také zakáže stránku nápovědy HTTP a funkci GET webové služby popis Language (WSDL), takže koncový bod metadat nebudou v konfliktu s výchozí koncový bod HTTP. <xref:System.ServiceModel.Web.WebServiceHost>také zajistí, že všechny koncové body, které používají <xref:System.ServiceModel.WebHttpBinding> mít požadované <xref:System.ServiceModel.Description.WebHttpBehavior> připojen. Nakonec <xref:System.ServiceModel.Web.WebServiceHost> automaticky nakonfiguruje vazba pro koncový bod pro práci s přidružené nastavení zabezpečení Internetové informační služby (IIS) při použití v zabezpečené virtuální adresář.  
  
## <a name="webservicehostfactory"></a>WebServiceHostFactory  
 <xref:System.ServiceModel.Activation.WebServiceHostFactory> Třída se používá k vytvoření dynamicky <xref:System.ServiceModel.Web.WebServiceHost> když je služby hostované v rámci Internetové informační služby (IIS) nebo služby Aktivace procesů systému Windows (WAS). Na rozdíl od služba s vlastním hostováním kde hostitelskou aplikaci vytvoří <xref:System.ServiceModel.Web.WebServiceHost>, služby hostované v rámci služby IIS nebo byla tato třída slouží k vytvoření <xref:System.ServiceModel.Web.WebServiceHost> pro službu. <xref:System.ServiceModel.Activation.WebServiceHostFactory.CreateServiceHost%28System.Type%2CSystem.Uri%5B%5D%29> Metoda je volána, když je obdržena příchozí žádost o službu.  
  
## <a name="webhttpbehavior"></a>WebHttpBehavior  
 <xref:System.ServiceModel.Description.WebHttpBehavior> – Třída poskytuje nezbytné formátovací moduly, operace selektory a tak dále, podpora stylu webové služby ve vrstvě modelu služby vyžaduje. Tato možnost je implementovaná jako chování koncového bodu (používá ve spojení s <xref:System.ServiceModel.WebHttpBinding>) a umožňuje formátování a operace selektory pro každý koncový bod, který povolí stejné implementaci služby vystavit koncové body SOAP a POX nutné zadat.  
  
### <a name="extending-webhttpbehavior"></a>Rozšíření WebHttpBehavior  
 <xref:System.ServiceModel.Description.WebHttpBehavior>je rozšiřitelný pomocí virtuální metody: <xref:System.ServiceModel.Description.WebHttpBehavior.GetOperationSelector%28System.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, a <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>. Vývojáři mohou odvození třídy z <xref:System.ServiceModel.Description.WebHttpBehavior> a přepsat tyto metody přizpůsobit výchozí chování.  
  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> Je příkladem rozšíření <xref:System.ServiceModel.Description.WebHttpBehavior>. <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>umožňuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] koncových bodů pro příjem požadavků HTTP od klienta založené na prohlížeči prvku ASP.NET AJAX. [AJAX služby pomocí HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) je příkladem pomocí tohoto bodu rozšíření.  
  
> [!WARNING]
>  Při použití <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>, <xref:System.UriTemplate> nejsou podporovány v rámci <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> atributy.  
  
## <a name="webhttpdispatchoperationselector"></a>WebHttpDispatchOperationSelector  
 <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector> Třídy používá <xref:System.UriTemplate> a <xref:System.UriTemplateTable> třídy odesláním volání operací služby.  
  
## <a name="compatibility"></a>Kompatibilita  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Model programování webových HTTP nepoužívá založený na protokolu SOAP zprávy a proto nepodporuje WS-* protokoly. Ale můžete zpřístupnit stejné smlouvy ve dvou různých koncový bod: jeden pomocí protokolu SOAP a jiné ne pomocí protokolu SOAP. V tématu [postupy: vystavení kontraktu protokolu SOAP a webovými klienty](../../../../docs/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) příklad.  
  
## <a name="security"></a>Zabezpečení  
 Protože [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Model programování webových HTTP nepodporuje WS-* protokoly jediným způsobem, jak zabezpečit webová služba založená na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Model programování webových HTTP je vystavit služby pomocí protokolu SSL. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]nastavení protokolu SSL s [!INCLUDE[iisver](../../../../includes/iisver-md.md)] najdete v části [implementaci protokolu SSL ve službě IIS](http://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>  
 [Přehled modelu programování WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
