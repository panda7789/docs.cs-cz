---
title: Přehled modelu webového programování HTTP služby WCF
ms.date: 03/30/2017
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
ms.openlocfilehash: fb6ef0fdcefbc6ceec75ce30db3abf5896d85c61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184188"
---
# <a name="wcf-web-http-programming-model-overview"></a>Přehled modelu webového programování HTTP služby WCF
Programovací model WCF (Windows Communication Foundation) WEB HTTP poskytuje základní prvky potřebné k vytvoření webových služeb HTTP s WCF. Služby WCF WEB HTTP jsou navrženy tak, aby k nim přistupovaly co nejširší spektrum možných klientů, včetně webových prohlížečů, a mají následující jedinečné požadavky:  
  
- **Uri a zpracování identifikátorů URI** Identifikátory URI hrají ústřední roli při navrhování služeb WEB HTTP. Programovací model WCF WEB <xref:System.UriTemplate> <xref:System.UriTemplateTable> HTTP používá třídy a k poskytování možností zpracování identifikátoru URI.  
  
- **Podpora operací GET a POST** Služby WEB HTTP využívají příkaz GET pro načítání dat, kromě různých invoke sloves pro úpravu dat a vzdálené vyvolání. WCF WEB HTTP programovací <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> model používá a přidružit operace služby get a další http slovesa jako PUT, POST a DELETE.  
  
- **Více formátů dat** Služby webového stylu zpracovávají kromě zpráv SOAP mnoho druhů dat. Programovací model WCF WEB <xref:System.ServiceModel.WebHttpBinding> <xref:System.ServiceModel.Description.WebHttpBehavior> HTTP používá a podporuje mnoho různých formátů dat, včetně dokumentů XML, datového objektu JSON a datových proudů binárního obsahu, jako jsou obrázky, soubory videa nebo prostý text.  
  
 WCF WEB HTTP programovací model rozšiřuje dosah WCF na webové styl scénáře, které zahrnují webové služby HTTP, AJAX a JSON služby a syndication (ATOM/RSS) kanály. Další informace o službách AJAX a JSON naleznete v [tématu Integrace AJAX a Podpora JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md). Další informace o syndikaci naleznete v tématu [Přehled syndikace WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md).  
  
 Neexistují žádná další omezení pro typy dat, které mohou být vráceny ze služby WEB HTTP. Z operace služby WEB HTTP lze vrátit libovolný serializovatelný typ. Vzhledem k tomu, že operace služby WEB HTTP mohou být vyvolány webovým prohlížečem, existuje omezení, jaké datové typy lze zadat v adrese URL. Další informace o typech, které jsou ve výchozím nastavení podporovány, naleznete v části **Parametry a adresy URL dotazu urišablony** níže. Výchozí chování lze změnit poskytnutím vlastní implementace T:System.ServiceModel.Dispatcher.QueryStringConverter, která určuje, jak převést parametry zadané v adrese URL na skutečný typ parametru. Další informace najdete v tématu <xref:System.ServiceModel.Dispatcher.QueryStringConverter>.  
  
> [!CAUTION]
> Služby napsané pomocí programovacího modelu WCF WEB HTTP nepoužívají zprávy SOAP. Vzhledem k tomu, že soap se nepoužívá, nelze použít funkce zabezpečení poskytované WCF. Můžete však použít zabezpečení založené na přenosu hostováním služby pomocí protokolu HTTPS. Další informace o zabezpečení WCF naleznete v [tématu Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
> [!WARNING]
> Instalace rozšíření WebDAV pro službu IIS může způsobit, že webové služby HTTP vrátí chybu HTTP 405, protože rozšíření WebDAV se pokusí zpracovat všechny požadavky PUT. Chcete-li tento problém vyřešit, můžete odinstalovat rozšíření WebDAV nebo zakázat rozšíření WebDAV pro váš web. Další informace naleznete v tématech [IIS a WebDav](https://learn.iis.net/page.aspx/357/webdav-for-iis-70/)  
  
## <a name="uri-processing-with-uritemplate-and-uritemplatetable"></a>Zpracování identifikátoru URI pomocí šablony UriTemplate a tabulky šablony uri  
 Šablony identifikátorů URI poskytují efektivní syntaxi pro vyjádření velkých sad strukturálně podobných identifikátorů URI. Například následující šablona vyjadřuje sadu všech třísegmentových identifikátorů URI, které začínají písmenem "a" a končí písmenem "c" bez ohledu na hodnotu mezilehlého segmentu: a/{segment}/c  
  
 Tato šablona popisuje identifikátory URI takto:  
  
- a/x/c  
  
- a/y/c  
  
- a/z/c  
  
- a tak dále.  
  
 V této šabloně označuje zápis složených závorek ({segment}") místo literálové hodnoty segment proměnné.  
  
 Rozhraní .NET Framework poskytuje rozhraní API <xref:System.UriTemplate>pro práci se šablonami URI nazývanými . `UriTemplates`umožňují provést následující akce:  
  
- Můžete volat jednu `Bind` z metod se sadou parametrů k vytvoření *plně uzavřený identifikátor URI,* který odpovídá šabloně. To znamená, že všechny proměnné v šabloně URI jsou nahrazeny skutečnými hodnotami.  
  
- Můžete volat `Match`() s kandidátem URI, který používá šablonu k rozdělení kandidáta URI do jeho součástí a vrátí slovník, který obsahuje různé části URI označené podle proměnných v šabloně.  
  
- `Bind`() `Match`a () jsou inverzní, `Match` `Bind`takže můžete volat ( ( x ) ) a vrátit se se stejným prostředím, se kterým jste začali.  
  
 Existuje mnohokrát (zejména na serveru, kde je nutné odeslat požadavek na operaci služby na základě <xref:System.UriTemplate> identifikátoru URI), které chcete sledovat sadu objektů v datové struktuře, která může nezávisle řešit každou z obsažených šablon. <xref:System.UriTemplateTable>představuje sadu šablon URI a vybere nejlepší shodu danou sadu šablon a identifikátor URI kandidáta. To není spojen s žádným konkrétním síťového zásobníku (WCF v ceně), takže jej můžete použít všude tam, kde je to nutné.  
  
 Model služby WCF <xref:System.UriTemplate> využívá <xref:System.UriTemplateTable> a přidružuje operace služby <xref:System.UriTemplate>k sadě identifikátorů URI popsaných . Operace služby je <xref:System.UriTemplate>přidružena k <xref:System.ServiceModel.Web.WebGetAttribute> , <xref:System.ServiceModel.Web.WebInvokeAttribute>pomocí nebo . Další informace <xref:System.UriTemplate> o <xref:System.UriTemplateTable>a najdete v [tématu UriTemplate a UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
  
## <a name="webget-and-webinvoke-attributes"></a>Atributy WebGet a WebInvoke  
 WCF WEB HTTP služby využívají načtení slovesa (například HTTP GET) kromě různých invoke sloves (například HTTP POST, PUT a DELETE). Programovací model WCF WEB HTTP umožňuje vývojářům služeb řídit šablonu URI <xref:System.ServiceModel.Web.WebGetAttribute> i <xref:System.ServiceModel.Web.WebInvokeAttribute>sloveso přidružené k jejich operacím služby s a . <xref:System.ServiceModel.Web.WebGetAttribute> A <xref:System.ServiceModel.Web.WebInvokeAttribute> umožňují řídit, jak se jednotlivé operace propojí s identifikátory URI a metodami HTTP přidruženými k těmto identifikátorům URI. Například přidání <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> a v následujícím kódu.  
  
```csharp
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
  
 Předchozí kód umožňuje provádět následující požadavky HTTP.  
  
 `GET /GetCustomer`  
  
 `POST /UpdateCustomerName`  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>výchozí post, ale můžete jej použít i pro jiná slovesa.  
  
```csharp
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
  
 Chcete-li zobrazit úplnou ukázku služby WCF, která používá programovací model WCF WEB HTTP, [přečtěte si postup: Vytvoření základní webové služby HTTP WCF](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a>Parametry a adresy URL řetězce dotazu UriTemplate  
 Služby webového stylu lze volat z webového prohlížeče zadáním adresy URL, která je přidružena k operaci služby. Tyto operace služby mohou mít parametry řetězce dotazu, které musí být zadány v řetězcovém formuláři v rámci adresy URL. V následující tabulce jsou uvedeny typy, které mohou být předány v rámci adresy URL a použitý formát.  
  
|Typ|Formát|  
|----------|------------|  
|<xref:System.Byte>|0 - 255|  
|<xref:System.SByte>|-128 - 127|  
|<xref:System.Int16>|-32768 - 32767|  
|<xref:System.Int32>|-2,147,483,648 - 2,147,483,647|  
|<xref:System.Int64>|-9,223,372,036,854,775,808 - 9,223,372,036,854,775,807|  
|<xref:System.UInt16>|0 - 65535|  
|<xref:System.UInt32>|0 - 4,294,967,295|  
|<xref:System.UInt64>|0 - 18,446,744,073,709,551,615|  
|<xref:System.Single>|-3.402823e38 - 3.402823e38 (zápis exponentu není vyžadován)|  
|<xref:System.Double>|-1.79769313486232e308 - 1.79769313486232e308 (zápis exponentu není vyžadován)|  
|<xref:System.Char>|Libovolný jednotlivý znak|  
|<xref:System.Decimal>|Jakékoliv desetinné místo ve standardním zápisu (bez exponentu)|  
|<xref:System.Boolean>|Pravda nebo nepravda (malá a velká písmena)|  
|<xref:System.String>|Libovolný řetězec (nulový řetězec není podporován a není provedeno žádné úniky)|  
|<xref:System.DateTime>|MM/DD/RRRR<br /><br /> MM/DD/YYYY HH:MM:SS [AM&#124;PM]<br /><br /> Měsíc den rok<br /><br /> Měsíc den rok HH: MM: SS [AM&#124;PM]|  
|<xref:System.TimeSpan>|Dd. HH:MM:SS<br /><br /> Kde DD = Dny, HH = Hodiny, MM = minuty, SS = Sekundy|  
|<xref:System.Guid>|Identifikátor GUID, například:<br /><br /> 936DA01F-9ABD-4d9d-80C7-02AF85C822A8|  
|<xref:System.DateTimeOffset>|MM/DD/YYYY HH:MM:SS MM:SS<br /><br /> Kde DD = Dny, HH = Hodiny, MM = minuty, SS = Sekundy|  
|Výčty|Hodnota výčtu, která definuje výčet, jak je znázorněno v následujícím kódu.<br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> V řetězci dotazu může být zadána libovolná z jednotlivých hodnot výčtu (nebo jejich odpovídajících celých hodnot).|  
|Typy, `TypeConverterAttribute` které mají, které lze převést typ do a z řetězcové reprezentace.|Závisí na převaděč typu.|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a>Formáty a programovací model WCF WEB HTTP  
 Programovací model WCF WEB HTTP má nové funkce pro práci s mnoha různými formáty dat. Ve vrstvě vazby <xref:System.ServiceModel.WebHttpBinding> může číst a zapisovat následující druhy dat:  
  
- XML  
  
- JSON  
  
- Neprůhledné binární datové proudy  
  
 To znamená, že programovací model WCF WEB HTTP může zpracovávat libovolný typ dat, ale může být programování proti <xref:System.IO.Stream>.  
  
 Rozhraní .NET Framework 3.5 poskytuje podporu pro data JSON (AJAX) a také pro zdroje Syndication (včetně ATOM a RSS). Další informace o těchto funkcích naleznete v [tématu WCF Web HTTP Formátování](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)[WCF Syndication Overview](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md) a AJAX Integrace a Podpora [JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md).  
  
## <a name="wcf-web-http-programming-model-and-security"></a>WCF WEB HTTP programovací model a zabezpečení  

Vzhledem k tomu, že programovací model WCF WEB HTTP nepodporuje protokoly WS-*, jediným způsobem, jak zabezpečit službu WCF WEB HTTP, je vystavit službu prostřednictvím protokolu HTTPS pomocí protokolu SSL. Další informace o nastavení ssl se sis 7.0 naleznete [v tématu Jak implementovat ssl ve iis](https://support.microsoft.com/help/299875/how-to-implement-ssl-in-iis).
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a>Poradce při potížích s programovacím modelem WCF WEB HTTP  
 Při volání wcf web <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> http služby pomocí <xref:System.ServiceModel.Description.WebHttpBehavior> vytvořit <xref:System.ServiceModel.EndpointAddress> kanál, používá sadu v <xref:System.ServiceModel.EndpointAddress> konfiguračním souboru i v případě, že jiný je předán <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>.  
  
## <a name="see-also"></a>Viz také

- [Syndikace WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
- [Programovací objektový model WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
