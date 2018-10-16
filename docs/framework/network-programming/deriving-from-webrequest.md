---
title: Odvození ze žádosti WebRequest
ms.date: 03/30/2017
helpviewer_keywords:
- WebRequest class, pluggable protocols
- protocol-specific request handler
- sending data, pluggable protocols
- pluggable protocols, class criteria
- Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
ms.assetid: 9810c177-973e-43d7-823c-14960bd625ea
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 9f4f1756d42e8931a5265017088021b5f4022044
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2018
ms.locfileid: "49337620"
---
# <a name="deriving-from-webrequest"></a>Odvození ze žádosti WebRequest
<xref:System.Net.WebRequest> Třída je abstraktní základní třídu, která poskytuje základní metody a vlastnosti pro vytvoření konkrétní žádost o obslužnou rutinu, která vyhovuje připojitelných protokolů model rozhraní .NET Framework. Aplikace, které používají **WebRequest** třídy můžete žádost o data pomocí libovolného protokolu pro podporované bez nutnosti určit protokol použitý.  
  
 Dvě kritéria musí být splněny, aby konkrétní třída má být použit jako připojitelná protokol: třída musí implementovat <xref:System.Net.IWebRequestCreate> rozhraní a zaregistrujte se <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metoda. Třída musí přepsat všechny abstraktní metody a vlastnosti **WebRequest** poskytnout modulární rozhraní.  
  
 **WebRequest** instancí jsou určeny k použití jednorázového; Pokud chcete provést další požadavek, vytvořte nový **WebRequest**. **WebRequest** podporuje <xref:System.Runtime.Serialization.ISerializable> rozhraní a umožňuje vývojářům k serializaci šablonu **WebRequest** a pak proveďte rekonstrukci šablony pro další požadavky.  
  
## <a name="iwebrequest-create-method"></a>Vytvoření IWebRequest – metoda  
 <xref:System.Net.IWebRequestCreate.Create%2A> Metoda zodpovídá za inicializaci nové instance třídy specifické pro protokol. Při nové **WebRequest** se vytvoří <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metoda odpovídá požadovanému identifikátoru URI pomocí předpony identifikátoru URI, který je zaregistrován s **RegisterPrefix** metoda. **Vytvořit** metoda správné následník protokolu specifické musí vracet inicializované instance následníka schopný provádět transakce standardní žádost/odpověď protokolu bez nutnosti žádné Upravit pole specifické pro protokol.  
  
## <a name="connectiongroupname-property"></a>Vlastnost ConnectionGroupName  
 <xref:System.Net.WebRequest.ConnectionGroupName%2A> Vlastnost se používá k pojmenování skupiny připojení k prostředku, tak, aby žádosti více můžete provést přes samostatné připojení. K implementaci sdílení připojení, musíte použít konkrétní metodu sdružování a přiřazování připojení. Například zadaná <xref:System.Net.ServicePointManager> třída implementuje sdílení pro připojení <xref:System.Net.HttpWebRequest> třídy. **Třída ServicePointManager** vytvoří třídu <xref:System.Net.ServicePoint> , který poskytuje připojení pro konkrétní server pro každou skupinu připojení.  
  
## <a name="contentlength-property"></a>Vlastnost ContentLength  
 <xref:System.Net.WebRequest.ContentLength%2A> Vlastnost určuje počet bajtů dat, které se odešlou na server při nahrávání data.  
  
 Obvykle <xref:System.Net.WebRequest.Method%2A> musí být nastavena vlastnost k označení, že nahrání trvá případech **ContentLength** je nastavena na hodnotu větší než nula.  
  
## <a name="contenttype-property"></a>Vlastnost ContentType  
 <xref:System.Net.WebRequest.ContentType%2A> Vlastnost poskytuje všechny speciální informace, že váš protokol vyžaduje, abyste odesílání na server, který identifikuje typ obsahu, který odesíláte. Obvykle je to typ obsahu MIME všech dat odeslaných.  
  
## <a name="credentials-property"></a>Vlastnosti přihlašovacích údajů  
 <xref:System.Net.WebRequest.Credentials%2A> Vlastnost obsahuje informace potřebné k ověření požadavku se serverem. Podrobnosti o procesu ověřování je nutné implementovat pro váš protokol. <xref:System.Net.AuthenticationManager> Třídy je odpovědná za ověřování požadavků a poskytování ověřovací token. Musí implementovat třídu, která poskytuje přihlašovací údaje, které používá váš protokol <xref:System.Net.ICredentials> rozhraní.  
  
## <a name="headers-property"></a>Vlastnost záhlaví  
 <xref:System.Net.WebRequest.Headers%2A> Vlastnost obsahuje libovolnou kolekci dvojic název/hodnota metadat přidružený k požadavku. Veškerá metadata, vyžaduje protokol, který může být vyjádřena jako dvojice název/hodnota může být součástí **záhlaví** vlastnost. Obvykle tyto informace musí být nastavena před voláním <xref:System.Net.WebRequest.GetRequestStream%2A> nebo <xref:System.Net.WebRequest.GetResponse%2A> metody; po zadání požadavku metadata se považuje za jen pro čtení.  
  
 Není nutné použít **záhlaví** vlastnost použít hlavičku metadat. Metadata specifická pro protokol může být vystavena jako vlastnosti; například <xref:System.Net.HttpWebRequest.UserAgent%2A?displayProperty=nameWithType> zpřístupňuje vlastnost **User-Agent** hlavičky protokolu HTTP. Pokud zveřejňujete hlavičku metadat jako vlastnost, by nemělo umožňovat stejnou vlastnost používat **záhlaví** vlastnost.  
  
## <a name="method-property"></a>Vlastnost – metoda  
 <xref:System.Net.WebRequest.Method%2A> Vlastnost obsahuje operaci nebo akci, která požadavku žádá serveru provádět. Výchozí nastavení pro **metoda** vlastnost musí povolit standardní žádost/odpověď akce bez nutnosti jakékoli vlastnosti specifické nastavení. Například <xref:System.Net.HttpWebResponse.Method%2A> výchozí hodnoty metody GET, která požádá o prostředek z webového serveru a vrátí odpověď.  
  
 Obvykle **ContentLength** vlastnost musí být nastavena na hodnotu větší než nula v případě **metoda** je nastavena na operaci nebo akci, která označuje, že nahrání probíhat.  
  
## <a name="preauthenticate-property"></a>PreAuthenticate vlastnost  
 Sada aplikací <xref:System.Net.WebRequest.PreAuthenticate%2A> vlastnost umožňující označit, že informace o ověřování mají být odeslány v prvotní žádosti Nečekejte na výzvu ověřování. **PreAuthenticate** vlastnost má smysl pouze v případě protokol podporuje ověřování pověření odeslána s počáteční požadavek.  
  
## <a name="proxy-property"></a>Vlastnost proxy  
 <xref:System.Net.WebRequest.Proxy%2A> Obsahuje vlastnost <xref:System.Net.IWebProxy> rozhraní, které se používá pro přístup k požadovanému prostředku. **Proxy** vlastnost má smysl pouze v případě, že váš protokol podporuje požadavky směrovány přes proxy server. Pokud váš protokol je vyžadováno jedno je potřeba nastavit výchozí proxy server.  
  
 V některých prostředích, jako za firemní branou firewall, váš protokol může být potřeba používat proxy server. V takovém případě je nutné implementovat **IWebProxy** rozhraní pro vytvoření třídy proxy, který bude fungovat pro váš protokol.  
  
## <a name="requesturi-property"></a>Vlastnost RequestUri  
 <xref:System.Net.WebRequest.RequestUri%2A> Vlastnost obsahuje identifikátor URI, který byl předán **WebRequest.Create** metody. To je jen pro čtení a nedá se změnit jednou **WebRequest** se vytvořil. Pokud váš protokol podporuje přesměrování, odpověď mohou pocházet ze zdroje identifikovaného identifikátorem jiný identifikátor URI. Pokud je potřeba poskytnout přístup k identifikátoru URI, který odpověděl, je nutné zadat je další vlastnost obsahující tento identifikátor URI.  
  
## <a name="timeout-property"></a>Vlastnost časového limitu  
 <xref:System.Net.WebRequest.Timeout%2A> Vlastnost obsahuje dobu v milisekundách, čekat, než vyprší časový limit žádosti a vyvolá výjimku. **Časový limit** se vztahuje pouze na synchronní požadavky provedené přes <xref:System.Net.WebRequest.GetResponse%2A> metoda; asynchronní požadavky musí používat <xref:System.Net.WebRequest.Abort%2A> metodě pro zrušení čekající žádosti o.  
  
 Nastavení **vypršení časového limitu** vlastnost má smysl pouze v případě, že konkrétní třída implementuje proces vypršení časového limitu.  
  
## <a name="abort-method"></a>Abort – metoda  
 <xref:System.Net.WebRequest.Abort%2A> Metoda zruší čekající asynchronní požadavek na server. Poté, co žádost byla zrušena, volání **GetResponse**, **BeginGetResponse**, **EndGetResponse**, **GetRequestStream**,  **BeginGetRequestStream**, nebo **EndGetRequestStream** vyvolá výjimku <xref:System.Net.WebException> s <xref:System.Net.WebException.Status%2A> nastavenou na <xref:System.Net.WebExceptionStatus>.  
  
## <a name="begingetrequeststream-and-endgetrequeststream-methods"></a>BeginGetRequestStream a EndGetRequestStream metody  
 <xref:System.Net.WebRequest.BeginGetRequestStream%2A> Metoda začíná asynchronního požadavku pro datový proud, který se používá k odesílání dat do serveru. <xref:System.Net.WebRequest.EndGetRequestStream%2A> Metoda dokončení asynchronního požadavku a vrací požadovaný datový proud. Tyto metody implementovat **GetRequestStream** standardním způsobem rozhraní .NET Framework asynchronní metoda.  
  
## <a name="begingetresponse-and-endgetresponse-methods"></a>BeginGetResponse a EndGetResponse metody  
 <xref:System.Net.WebRequest.BeginGetResponse%2A> Metoda začíná Asynchronní požadavek na server. <xref:System.Net.WebRequest.EndGetResponse%2A> Metoda dokončí Asynchronní požadavek a vrátí požadovaná odpověď. Tyto metody implementovat **GetResponse** standardním způsobem rozhraní .NET Framework asynchronní metoda.  
  
## <a name="getrequeststream-method"></a>GetRequestStream – metoda  
 <xref:System.Net.WebRequest.GetRequestStream%2A> Metoda vrací datový proud, který se používá k zápisu dat na požadovaný server. Stream vrácený by měla být jen pro zápis datového proudu, který neupravuje; je určena jako jednosměrná datový proud dat, která jsou zapsána do serveru. Vrátí hodnotu false pro datový proud <xref:System.IO.Stream.CanRead%2A> a <xref:System.IO.Stream.CanSeek%2A> vlastnosti a hodnotu true <xref:System.IO.Stream.CanWrite%2A> vlastnost.  
  
 **GetRequestStream** metoda obvykle otevře připojení k serveru a před vrácením datového proudu, odešle informace v hlavičce určující těchto dat je odesíláno do serveru. Protože **GetRequestStream** zahájí požadavek žádné nastavení **záhlaví** vlastnosti nebo **ContentLength** vlastnost se obvykle nepovoluje po volání **GetRequestStream**.  
  
## <a name="getresponse-method"></a>GetResponse – metoda  
 <xref:System.Net.WebRequest.GetResponse%2A> Metoda vrátí konkrétní potomkem <xref:System.Net.WebResponse> třídu, která představuje odpověď ze serveru. Pokud již byl zahájen požadavek podle **GetRequestStream** metody **GetResponse** metoda vytvoří připojení k prostředku označeném identifikátorem **RequestUri**, odešle informace v hlavičce určující typ požadavku odeslaná a pak obdrží odpověď od zdroje.  
  
 Jakmile **GetResponse** metoda je volána, všechny vlastnosti by měl být jen pro čtení. **WebRequest** instancí jsou určeny k použití jednorázového; Pokud budete chtít provést další požadavek, měli byste vytvořit nový **WebRequest**.  
  
 **GetResponse** metoda zodpovídá za vytvoření odpovídající **WebResponse** potomků tak, aby obsahovala příchozí odpovědi.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.FileWebRequest>  
 [Programování připojitelných protokolů](../../../docs/framework/network-programming/programming-pluggable-protocols.md)  
 [Odvození z odpovědi WebResponse](../../../docs/framework/network-programming/deriving-from-webresponse.md)
