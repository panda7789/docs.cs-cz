---
title: Přehled modelu webového programování HTTP služby WCF
ms.date: 03/30/2017
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
ms.openlocfilehash: 8c13ad943bf4ef272c28266e12e175a0a21d5d40
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045235"
---
# <a name="wcf-web-http-programming-model-overview"></a>Přehled modelu webového programování HTTP služby WCF
Programovací model webového HTTP služby Windows Communication Foundation (WCF) poskytuje základní prvky potřebné k sestavení webových služeb HTTP pomocí WCF. WEBOVÉ HTTP služby WCF jsou navržené tak, aby měly k dispozici nejširší škálu možných klientů, včetně webových prohlížečů, a mají následující jedinečné požadavky:  
  
- **Identifikátory URI a zpracování identifikátorů URI** Identifikátory URI hrají centrální roli v rámci navrhování webových služeb HTTP. Programovací model webového HTTP WCF používá <xref:System.UriTemplate> třídy a <xref:System.UriTemplateTable> k poskytování schopností zpracování identifikátoru URI.  
  
- **Podpora operací GET a post** WEBOVÉ HTTP služby využívají příkaz GET pro načítání dat, kromě různých operací vyvolání pro úpravu dat a vzdálené vyvolání. Model programování webových služeb HTTP WCF používá <xref:System.ServiceModel.Web.WebGetAttribute> a <xref:System.ServiceModel.Web.WebInvokeAttribute> k přidružení operací služby k operacím Get a dalších http, jako jsou PUT, post a DELETE.  
  
- **Více formátů dat** Služby webového stylu zpracovávají kromě zpráv SOAP i mnoho druhů dat. Model programování webových služeb HTTP WCF používá <xref:System.ServiceModel.WebHttpBinding> a <xref:System.ServiceModel.Description.WebHttpBehavior> k podpoře mnoha různých datových formátů, včetně dokumentů XML, datových objektů JSON a datových proudů binárního obsahu, jako jsou obrázky, videosoubory nebo prostý text.  
  
 Model programování webových služeb HTTP WCF rozšiřuje dosah WCF na pokrytí scénářů webového stylu, které zahrnují webové HTTP služby, AJAX a JSON Services a syndikace (ATOM/RSS) kanálů. Další informace o službách AJAX a JSON najdete v tématu věnovaném [integraci AJAX a podpoře JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md). Další informace o syndikaci najdete v tématu [Přehled Syndikace WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md).  
  
 Neexistují žádná další omezení typů dat, která lze vrátit z webové služby HTTP. Z operace webové služby HTTP lze vrátit libovolný serializovatelný typ. Vzhledem k tomu, že je možné operace webové služby HTTP vyvolat webovým prohlížečem, existuje omezení toho, jaké typy dat lze zadat v adrese URL. Další informace o podporovaných typech ve výchozím nastavení najdete níže v části **parametry řetězce dotazu UriTemplate a adresy URL** . Výchozí chování lze změnit poskytnutím vlastní implementace T:System.ServiceModel.Dispatcher.QueryStringConverter, která určuje, jak převést parametry zadané v adrese URL na skutečný typ parametru. Další informace najdete v tématu.<xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
> [!CAUTION]
> Služby napsané pomocí programovacího modelu WEB HTTP WCF nepoužívají zprávy SOAP. Vzhledem k tomu, že protokol SOAP není použit, nelze použít funkce zabezpečení poskytované službou WCF. Můžete ale použít zabezpečení založené na přenosu, protože službu hostuje pomocí protokolu HTTPS. Další informace o zabezpečení WCF najdete v tématu [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md) .  
  
> [!WARNING]
> Instalace rozšíření WebDAV pro službu IIS může způsobit, že webové služby HTTP budou vracet chybu HTTP 405, protože se rozšíření WebDAV pokusí zpracovat všechny požadavky PUT. Pokud chcete tento problém obejít, můžete rozšíření WebDAV odinstalovat nebo zakázat rozšíření WebDAV pro váš web. Další informace najdete v tématu [IIS a WebDAV](https://learn.iis.net/page.aspx/357/webdav-for-iis-70/) .  
  
## <a name="uri-processing-with-uritemplate-and-uritemplatetable"></a>Zpracování identifikátorů URI pomocí UriTemplate a UriTemplateTable  
 Šablony identifikátorů URI poskytují efektivní syntaxi pro vyjádření velkých sad strukturně podobných identifikátorů URI. Například následující šablona vyjadřuje sadu všech identifikátorů URI se třemi segmenty, které začínají řetězcem "a" a končí "c" bez ohledu na hodnotu mezilehlého segmentu: a/{segment}/c  
  
 Tato šablona popisuje identifikátory URI jako následující:  
  
- a/x/c  
  
- a/y/c  
  
- a/z/c  
  
- a tak dále.  
  
 V této šabloně označuje notaci složené závorky ("{segment}") segment proměnné namísto hodnoty literálu.  
  
 .NET Framework poskytuje rozhraní API pro práci se šablonami identifikátorů URI s názvem <xref:System.UriTemplate>. `UriTemplates`umožňuje provést následující akce:  
  
- Můžete zavolat jednu z `Bind` metod se sadou parametrů k vytvoření *plně uzavřeného identifikátoru URI* , který odpovídá šabloně. To znamená, že všechny proměnné v šabloně identifikátoru URI se nahradí skutečnými hodnotami.  
  
- Můžete zavolat `Match`() s kandidátem identifikátor URI, který používá šablonu k rozdělení kandidátu identifikátoru URI na jeho části prvků a vrátí slovník, který obsahuje různé části identifikátoru URI označené podle proměnných v šabloně.  
  
- `Bind`() a `Match`() jsou Inverted, abyste mohli zavolat `Match`( `Bind`(x)) a vracet se stejným prostředím, které jste začali s.  
  
 Na serveru se často používá (zejména na serveru, kde je potřeba zrušit požadavek na operaci služby na základě identifikátoru URI), kterou chcete sledovat sadu <xref:System.UriTemplate> objektů v datové struktuře, která může nezávisle adresovat každý z obsažených šablony. <xref:System.UriTemplateTable>představuje sadu šablon identifikátorů URI a vybere nejlepší shodu dané sady šablon a kandidátního identifikátoru URI. Tato součást není přidružená k žádnému konkrétnímu síťovému zásobníku (zahrnutému do WCF), abyste ji mohli použít všude, kde je to potřeba.  
  
 Model <xref:System.UriTemplate> služby WCF využívá a <xref:System.UriTemplateTable> k přidružení operací služby se sadou identifikátorů URI popsaných <xref:System.UriTemplate>v. Operace služby je přidružena <xref:System.UriTemplate>k nástroji pomocí <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute>. Další informace o <xref:System.UriTemplate> a <xref:System.UriTemplateTable>najdete v tématu [UriTemplate a UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md) .  
  
## <a name="webget-and-webinvoke-attributes"></a>Atributy WebGet a WebInvoke  
 WEBOVÉ HTTP služby WCF využívají operace načítání (například HTTP GET) Kromě různých operací vyvolání (například HTTP POST, PUT a DELETE). Programovací model webového HTTP WCF umožňuje vývojářům služeb řídit jak šablonu identifikátoru URI, tak i operaci spojenou s jejich operacemi <xref:System.ServiceModel.Web.WebGetAttribute> služeb <xref:System.ServiceModel.Web.WebInvokeAttribute>pomocí a. <xref:System.ServiceModel.Web.WebGetAttribute> Aumožňujeřídit,jakjednotlivéoperacezískajívazbunaidentifikátoryURIametodyHTTPpřidruženék<xref:System.ServiceModel.Web.WebInvokeAttribute> těmto identifikátorům URI. Například přidání <xref:System.ServiceModel.Web.WebGetAttribute> a <xref:System.ServiceModel.Web.WebInvokeAttribute> v následujícím kódu.  
  
```  
[ServiceContract]  
interface ICustomer  
{  
  //"View It"  
  
  [WebGet]  
  Customer GetCustomer():  
  
  //"Do It"  
    [WebInvoke]  
  Customer UpdateCustomerName( string id,   
                               string newName );  
}  
```  
  
 Předchozí kód vám umožní provést následující požadavky HTTP.  
  
 `GET /GetCustomer`  
  
 `POST /UpdateCustomerName`  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>Výchozí hodnota je POST, ale můžete ji použít i pro jiné operace.  
  
```  
[ServiceContract]  
interface ICustomer  
{  
  //"View It" -> HTTP GET  
    [WebGet( UriTemplate="customers/{id}" )]  
  Customer GetCustomer( string id ):  
  
  //"Do It" -> HTTP PUT  
  [WebInvoke( UriTemplate="customers/{id}", Method="PUT" )]  
  Customer UpdateCustomer( string id, Customer newCustomer );  
}  
```  
  
 Chcete-li zobrazit úplnou ukázku služby WCF, která používá model programování webové služby HTTP WCF, přečtěte si téma [How to: Vytvoření základní webové služby HTTP WCF](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a>Parametry řetězce dotazu UriTemplate a adresy URL  
 Služby webového stylu je možné volat z webového prohlížeče zadáním adresy URL, která je přidružena k operaci služby. Tyto operace služby můžou přijímat parametry řetězce dotazu, které se musí zadat ve formě řetězce v rámci adresy URL. V následující tabulce jsou uvedeny typy, které mohou být předány v rámci adresy URL a používaného formátu.  
  
|type|Formát|  
|----------|------------|  
|<xref:System.Byte>|0 - 255|  
|<xref:System.SByte>|-128 - 127|  
|<xref:System.Int16>|-32768 - 32767|  
|<xref:System.Int32>|-2,147,483,648 - 2,147,483,647|  
|<xref:System.Int64>|-9,223,372,036,854,775,808 - 9,223,372,036,854,775,807|  
|<xref:System.UInt16>|0 - 65535|  
|<xref:System.UInt32>|0 - 4,294,967,295|  
|<xref:System.UInt64>|0 - 18,446,744,073,709,551,615|  
|<xref:System.Single>|-3.402823 E38-3.402823 E38 (není vyžadován zápis exponentu)|  
|<xref:System.Double>|-1.79769313486232 e308-1.79769313486232 e308 (není vyžadován zápis exponentu)|  
|<xref:System.Char>|Libovolný jeden znak|  
|<xref:System.Decimal>|Jakékoli desetinné číslo ve standardním zápisu (bez exponentu)|  
|<xref:System.Boolean>|True nebo false (nerozlišuje velká a malá písmena)|  
|<xref:System.String>|Libovolný řetězec (řetězec s hodnotou null není podporován a není provedeno žádné uvozovací znaky)|  
|<xref:System.DateTime>|MM/DD/RRRR<br /><br /> MM/DD/RRRR HH: MM: SS [AM&#124;ODP]<br /><br /> Den měsíce roku<br /><br /> Měsíc dne v roce HH: MM: SS [&#124;am ODP]|  
|<xref:System.TimeSpan>|DD.HH:MM:SS<br /><br /> Kde DD = dny, HH = hodiny, MM = minuty, SS = sekund|  
|<xref:System.Guid>|Identifikátor GUID, například:<br /><br /> 936DA01F-9ABD-4d9d-80C7-02AF85C822A8|  
|<xref:System.DateTimeOffset>|MM/DD/RRRR HH: MM: SS MM: SS<br /><br /> Kde DD = dny, HH = hodiny, MM = minuty, SS = sekund|  
|Výčty|Hodnota výčtu například definující výčet, jak je znázorněno v následujícím kódu.<br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> V řetězci dotazu lze zadat jakoukoli z individuálních hodnot výčtu (nebo jejich odpovídajících celočíselných hodnot).|  
|Typy, které mají `TypeConverterAttribute` , které mohou převést typ na a z řetězcové reprezentace.|Závisí na konvertoru typu.|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a>Formáty a programovací model webového HTTP WCF  
 Programovací model webového HTTP WCF má nové funkce pro práci s mnoha různými formáty dat. Ve vrstvě <xref:System.ServiceModel.WebHttpBinding> vazby může číst a zapisovat následující různé druhy dat:  
  
- XML  
  
- FORMÁT JSON  
  
- Neprůhledné binární proudy  
  
 To znamená, že model programování webového HTTP WCF může zpracovat jakýkoli typ dat, ale může se jednat o programování <xref:System.IO.Stream>.  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)]poskytuje podporu pro data JSON (AJAX) a také informační kanály syndikace (včetně ATOMů a RSS). Další informace o těchto funkcích najdete v tématu[Přehled syndikace](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md) [webového http](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)WCF a [integrace AJAX a podpora JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md).  
  
## <a name="wcf-web-http-programming-model-and-security"></a>Programovací model a zabezpečení webového HTTP WCF  
 Vzhledem k tomu, že model programování webových služeb HTTP WCF nepodporuje protokoly WS-*, jediným způsobem, jak zabezpečit službu WCF WEB HTTP, je vystavit službu přes protokol HTTPS pomocí protokolu SSL. Další informace o nastavení SSL se službou IIS 7,0 najdete v tématu [implementace protokolu SSL ve službě IIS](https://go.microsoft.com/fwlink/?LinkId=131613) .  
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a>Řešení potíží s programovacím modelem HTTP webu WCF  
 Při volání služby WCF Web HTTP pomocí a <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> k vytvoření kanálu <xref:System.ServiceModel.Description.WebHttpBehavior> použije <xref:System.ServiceModel.EndpointAddress> sada nastavenou v konfiguračním souboru <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>i v případě, že je předána jiná <xref:System.ServiceModel.EndpointAddress> metoda.  
  
## <a name="see-also"></a>Viz také:

- [Syndikace WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
- [Programovací objektový model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
