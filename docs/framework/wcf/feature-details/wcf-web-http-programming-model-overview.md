---
title: Přehled modelu webového programování HTTP služby WCF
ms.date: 03/30/2017
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
ms.openlocfilehash: a6f267232085a46d481199eac83e464f5f774273
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199580"
---
# <a name="wcf-web-http-programming-model-overview"></a>Přehled modelu webového programování HTTP služby WCF
Model programování webových služeb HTTP Windows Communication Foundation (WCF) poskytuje základní prvky, které jsou potřebné k sestavení služeb webových služeb HTTP s použitím technologie WCF. WEBOVÝCH služeb HTTP WCF services jsou navržené tak přístup k nejširší škálu možných klientů, včetně webových prohlížečů a mají následující jedinečné požadavky:  
  
-   **Identifikátory URI a identifikátor URI zpracování** identifikátory URI přehrát hlavní roli v návrhu webové služby HTTP. WCF WEB HTTP používá model programování <xref:System.UriTemplate> a <xref:System.UriTemplateTable> třídy, které poskytují možnosti zpracování identifikátoru URI.  
  
-   **Podpora pro operace GET a POST** webových služeb HTTP služby použijte příkaz GET pro načtení dat, kromě různých volat příkazy pro úpravu dat a vzdálené volání. WCF WEB HTTP používá model programování <xref:System.ServiceModel.Web.WebGetAttribute> a <xref:System.ServiceModel.Web.WebInvokeAttribute> přidružit servisní operace GET a další příkazy HTTP, jako jsou PUT, POST a DELETE.  
  
-   **Několika datových formátů** zpracovávat různé druhy dat kromě zprávy protokolu SOAP stylu webové služby. WCF WEB HTTP používá model programování <xref:System.ServiceModel.WebHttpBinding> a <xref:System.ServiceModel.Description.WebHttpBehavior> pro podporu mnoha různých datových formátů, včetně dokumentů XML, JSON datového objektu a proudy binární obsah, jako jsou obrázky, soubory videa nebo prostý text.  
  
 Model programování webových služeb HTTP WCF rozšiřuje dosah WCF Web – vizuální styl scénáře, které obsahují webové služby HTTP, služby AJAX a JSON a informační kanály syndikace (ATOM nebo RSS). Další informace o službách AJAX a JSON najdete v tématu [integrace jazyka AJAX a podpora formátu JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md). Další informace o syndikace najdete v tématu [syndikace WCF – přehled](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md).  
  
 Neexistují žádná další omezení na typy dat, může být vrácen z webových služeb HTTP služby. Žádné serializovatelný typ. může být vrácen z operace HTTP webové služby. Vzhledem k tomu může být operace služby webových služeb HTTP vyvolejte z webového prohlížeče, které existuje omezení na jaká data typy můžou být specifikované v adrese URL. Další informace o typech podporovaných ve výchozím nastavení najdete v článku **UriTemplate parametrů řetězce dotazu a adresy URL** níže v části. Výchozí chování lze změnit tím, že poskytuje vlastní T:System.ServiceModel.Dispatcher.QueryStringConverter implementace, která určuje, jak převést parametry zadané v adrese URL na typ skutečného parametru. Další informace najdete v tématu <xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
> [!CAUTION]
>  Služby, které jsou napsané pomocí programovacího modelu WCF WEB HTTP nepoužívejte zprávy protokolu SOAP. Vzhledem k tomu, že není použit protokol SOAP, nelze použít funkcích zabezpečení poskytovaných WCF. Můžete ale použít zabezpečení na základě přenosu hostováním vaši službu pomocí protokolu HTTPS. Další informace o zabezpečení WCF najdete v tématu [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
> [!WARNING]
>  Instalace rozšíření WebDAV pro službu IIS může způsobit webové služby HTTP vrátit chybu HTTP 405 jako WebDAV rozšíření, pokusí se zpracovat všechny požadavky PUT. Chcete-li vyřešit tento problém můžete odinstalovat rozšíření WebDAV nebo zakázat rozšíření WebDAV pro váš web. Další informace najdete v tématu [služby IIS a protokolu WebDav](https://learn.iis.net/page.aspx/357/webdav-for-iis-70/)  
  
## <a name="uri-processing-with-uritemplate-and-uritemplatetable"></a>Identifikátor URI zpracování ve službě UriTemplate a UriTemplateTable  
 Identifikátor URI šablony poskytují efektivní syntaxe pro vyjádření velkých sad strukturálně podobné identifikátorů URI. Například následující šablonu vyjadřuje sadu URI všechny tři segmentu, které začínají řetězcem "a" a na konci "c" bez ohledu na hodnotu zprostředkující segmentu: / {segmentovat} /c  
  
 Tato šablona popisuje identifikátory URI vypadat asi takto:  
  
-   a/x/c  
  
-   / y/c  
  
-   a/z/c  
  
-   a tak dále.  
  
 V této šabloně zápis složenou závorku ("{segment}") označuje segment proměnné místo literálovou hodnotou.  
  
 Rozhraní .NET framework poskytuje rozhraní API pro práci se šablonami identifikátoru URI volá <xref:System.UriTemplate>. `UriTemplates` umožní provést následující kroky:  
  
-   Můžete volat jednu z `Bind` metody sadu parametrů za účelem vytvoření *plně ukončena, identifikátor URI* , který odpovídá šabloně. To znamená, že jsou všechny proměnné v rámci šablona identifikátoru URI nahradit skutečnými hodnotami.  
  
-   Můžete volat `Match`() se kandidát identifikátor URI, který používá k rozdělení kandidát URI do jeho složky části a vrátí slovník, který obsahuje různé části identifikátoru URI podle proměnné v šabloně označené jako šablonu.  
  
-   `Bind`() a `Match`() jsou inverses, takže můžete volat `Match`( `Bind`(x)) a vraťte se stejné prostředí, můžete začít.  
  
 Nejsou k dispozici v mnoha případech (zejména na serveru, pokud odesílání žádosti pro operaci služby podle identifikátoru URI je nezbytné), že chcete sledovat, sadu <xref:System.UriTemplate> objekty do datové struktury, která může nezávisle na sobě vztahují na všechny uzavřeného šablony. <xref:System.UriTemplateTable> představuje sadu šablon pro identifikátor URI a vybere nejlepší shodu určitou sadu šablon a Release candidate identifikátoru URI. Proto můžete použít, kdykoli je to nutné, to není přidružený žádné konkrétní sadu síťových protokolů (je součástí WCF).  
  
 Model služby WCF využívá <xref:System.UriTemplate> a <xref:System.UriTemplateTable> přidružení operací služby se sadou URI popsal <xref:System.UriTemplate>. Operace služby je přidružena <xref:System.UriTemplate>, buď pomocí <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute>. Další informace o <xref:System.UriTemplate> a <xref:System.UriTemplateTable>, naleznete v tématu [UriTemplate a UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
  
## <a name="webget-and-webinvoke-attributes"></a>WebGet a WebInvoke atributy  
 Ujistěte se, webových služeb HTTP WCF services použijte načítání příkazů (třeba HTTP GET), kromě různých vyvolání operací (třeba HTTP POST, PUT a DELETE). Model programování webových služeb HTTP WCF umožňuje vývojářům služby ovládacího prvku na i šablona identifikátoru URI a operace spojené s jejich operace služby s <xref:System.ServiceModel.Web.WebGetAttribute> a <xref:System.ServiceModel.Web.WebInvokeAttribute>. <xref:System.ServiceModel.Web.WebGetAttribute> a <xref:System.ServiceModel.Web.WebInvokeAttribute> povolit jak určovat, jak jednotlivé operace váže na identifikátory URI a metody HTTP spojený s těmito identifikátory URI. Například přidáním <xref:System.ServiceModel.Web.WebGetAttribute> a <xref:System.ServiceModel.Web.WebInvokeAttribute> v následujícím kódu.  
  
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
  
 Předchozí kód umožňuje zajistit následující požadavky HTTP.  
  
 `GET /GetCustomer`  
  
 `POST /UpdateCustomerName`  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> Výchozí hodnota je příspěvek, ale můžete použít pro ostatní operace příliš.  
  
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
  
 Úplnou ukázku služby WCF, který používá model programování webových služeb HTTP WCF najdete v tématu [jak: Vytvoření základní webové HTTP služby WCF](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a>Parametry řetězce dotazu UriTemplate a adresy URL  
 Styl webové služby lze volat z webového prohlížeče zadáním adresy URL, který je přidružený k operaci služby. Tyto operace služby může trvat parametrů řetězce dotazu, které musí být zadán ve formátu řetězce v rámci adresy URL. V následující tabulce jsou uvedeny typy, které mohou být předány v rámci adresy URL a formát používaný.  
  
|Type|Formát|  
|----------|------------|  
|<xref:System.Byte>|0 - 255|  
|<xref:System.SByte>|-128 - 127|  
|<xref:System.Int16>|-32768 - 32767|  
|<xref:System.Int32>|-2,147,483,648 - 2,147,483,647|  
|<xref:System.Int64>|-9,223,372,036,854,775,808 - 9,223,372,036,854,775,807|  
|<xref:System.UInt16>|0 - 65535|  
|<xref:System.UInt32>|0 - 4,294,967,295|  
|<xref:System.UInt64>|0 - 18,446,744,073,709,551,615|  
|<xref:System.Single>|-3.402823e38 - 3.402823e38 (exponentu zápisu se nevyžaduje)|  
|<xref:System.Double>|-1.79769313486232E308 až - 1.79769313486232E308 až (exponentu zápisu se nevyžaduje)|  
|<xref:System.Char>|Libovolný znak|  
|<xref:System.Decimal>|Žádné desetinné ve standardním zápisu (žádné exponent)|  
|<xref:System.Boolean>|PRAVDA nebo NEPRAVDA (malá a velká malá a velká písmena)|  
|<xref:System.String>|Jakýkoli řetězec (null řetězec není podporován a žádné uvození probíhá)|  
|<xref:System.DateTime>|MM/DD/RRRR<br /><br /> MM/DD/RRRR HH: MM: [AM&AMP;#124;PM]<br /><br /> Měsíc den roku<br /><br /> Den měsíce roku hh: mm: [AM&#124;PM]|  
|<xref:System.TimeSpan>|DD.HH:MM:SS<br /><br /> Kde DD HH = dny, = hodiny, MM minuty, SS = = sekund|  
|<xref:System.Guid>|Identifikátor GUID, například:<br /><br /> 936DA01F-9ABD-4d9d-80C7-02AF85C822A8|  
|<xref:System.DateTimeOffset>|MM/DD/RRRR HH: MM: MM: SS<br /><br /> Kde DD HH = dny, = hodiny, MM minuty, SS = = sekund|  
|Výčty|Hodnota výčtu například, která definuje výčet, jak je znázorněno v následujícím kódu.<br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> Některé z hodnot výčtu jednotlivých (nebo jejich odpovídající hodnoty celé číslo) je možné zadat řetězec dotazu.|  
|Typy, které mají `TypeConverterAttribute` typ, který můžete převést do a z řetězcové reprezentace.|Závisí na konvertor typu.|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a>Formáty a Model programování webových služeb HTTP WCF  
 Model programování webových služeb HTTP WCF obsahuje nové funkce pro práci s mnoha různých datových formátů. Ve vrstvě vazby <xref:System.ServiceModel.WebHttpBinding> může číst a zapisovat následující různé druhy dat:  
  
-   XML  
  
-   FORMÁT JSON  
  
-   Neprůhledný binární proudy  
  
 To znamená, že model programování webových služeb HTTP WCF dokáže zpracovat jakýkoli typ dat, ale můžete programovat s <xref:System.IO.Stream>.  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] poskytuje podporu pro data JSON (AJAX) a také informační kanály syndikace (včetně ATOM a RSS). Další informace o těchto funkcích najdete v tématu [WCF Web HTTP formátování](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)[syndikace WCF – přehled](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md) a [integrace jazyka AJAX a podpora formátu JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md).  
  
## <a name="wcf-web-http-programming-model-and-security"></a>Zabezpečení a modelu programování webových služeb HTTP WCF  
 Protože model programování webových služeb HTTP WCF nepodporuje WS-* protokoly, je jediný způsob, jak zabezpečit službu WCF WEB HTTP pro vystavení služby přes protokol HTTPS pomocí protokolu SSL. Další informace o nastavení protokolu SSL s [!INCLUDE[iisver](../../../../includes/iisver-md.md)], naleznete v tématu [implementace protokolu SSL ve službě IIS](https://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a>Řešení potíží s WCF WEB HTTP programovací Model  
 Při volání webových služeb HTTP WCF services pomocí <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> k vytvoření kanálu, <xref:System.ServiceModel.Description.WebHttpBehavior> používá <xref:System.ServiceModel.EndpointAddress> nastavit i když soubor konfigurace jiný <xref:System.ServiceModel.EndpointAddress> je předána <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>.  
  
## <a name="see-also"></a>Viz také:

- [Syndikace WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
- [Programovací objektový model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
