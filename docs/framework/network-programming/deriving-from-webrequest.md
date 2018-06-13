---
title: Odvozování z WebRequest
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
manager: markl
ms.openlocfilehash: 1a1dd850c6534443603fbefb2c1444c85f84a31b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396815"
---
# <a name="deriving-from-webrequest"></a>Odvozování z WebRequest
<xref:System.Net.WebRequest> Třída je abstraktní základní třída, která poskytuje základní metody a vlastnosti pro vytvoření obslužné rutiny specifické pro protokol požadavek, který nejlépe odpovídá modulární protokol model rozhraní .NET Framework. Aplikace, které používají **WebRequest** třídy můžete žádost o data pomocí libovolný podporovaný protokol bez nutnosti zadat protokol použít.  
  
 Musí být splněna dvě kritéria v pořadí pro třídu specifické pro protokol má být použit jako modulární protokol: musí implementovat třídu <xref:System.Net.IWebRequestCreate> rozhraní a je nutné se zaregistrovat <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> metoda. Třída musí přepsat všechny abstraktní metody a vlastnosti **WebRequest** zajistit modulární rozhraní.  
  
 **WebRequest** instance jsou určeny k použití jednorázové; Pokud chcete nastavit jinou žádost, vytvořte novou **WebRequest**. **WebRequest** podporuje <xref:System.Runtime.Serialization.ISerializable> rozhraní a umožňuje vývojářům k serializaci šablonu **WebRequest** a pak proveďte rekonstrukci šablony pro další požadavky.  
  
## <a name="iwebrequest-create-method"></a>IWebRequest Create – metoda  
 <xref:System.Net.IWebRequestCreate.Create%2A> Metoda zodpovídá za inicializaci nové instance třídy specifické pro protokol. Když nový **WebRequest** je vytvořen, <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metoda odpovídá požadovaný identifikátor URI s předponami URI zaregistrována **RegisterPrefix** metoda. **Vytvořit** metoda správné následník specifické pro protokol musí vrátit instanci následníka inicializovaného schopná provádět transakce standardní žádosti a odpovědi protokolu bez nutnosti žádné pole specifické pro protokol změnit.  
  
## <a name="connectiongroupname-property"></a>Vlastnost ConnectionGroupName  
 <xref:System.Net.WebRequest.ConnectionGroupName%2A> Vlastnost se používá k pojmenování skupinu připojení k prostředku, aby více požadavků můžete provést pomocí jediného připojení. K implementaci sdílení připojení, musíte použít metodu specifické pro protokol sdružování a přiřazení připojení. Například poskytnutého <xref:System.Net.ServicePointManager> třída implementuje sdílení pro připojení <xref:System.Net.HttpWebRequest> třídy. **ServicePointManager –** třída vytvoří <xref:System.Net.ServicePoint> poskytující připojení k určitému serveru pro každou skupinu připojení.  
  
## <a name="contentlength-property"></a>Vlastnost ContentLength  
 <xref:System.Net.WebRequest.ContentLength%2A> Vlastnost určuje počet bajtů dat, která bude odeslána na server při nahrávání dat.  
  
 Obvykle <xref:System.Net.WebRequest.Method%2A> musí být nastavena na znamenat, že nahrávaný trvá umístit při **ContentLength** je nastavena na hodnotu větší než nula.  
  
## <a name="contenttype-property"></a>Vlastnost ContentType  
 <xref:System.Net.WebRequest.ContentType%2A> Vlastnost poskytuje všechny speciální informace, že váš protokol vyžaduje, abyste k identifikaci typ obsahu, který odesíláte odeslat na server. Obvykle jde žádné data nahraná obsahu typ MIME.  
  
## <a name="credentials-property"></a>Vlastnost přihlašovací údaje  
 <xref:System.Net.WebRequest.Credentials%2A> Vlastnost obsahuje informace potřebné k ověření požadavku se serverem. Podrobnosti o procesu ověřování musí implementovat pro vaši protokol. <xref:System.Net.AuthenticationManager> Třída je odpovědná za ověřování požadavků a poskytování ověřovací token. Musí implementovat třídu, která poskytuje pověření používaná vaší protokolu <xref:System.Net.ICredentials> rozhraní.  
  
## <a name="headers-property"></a>Vlastnost hlavičky  
 <xref:System.Net.WebRequest.Headers%2A> Vlastnost obsahuje libovolné kolekci dvojic název/hodnota metadat přidružený k požadavku. Veškerá metadata, vyžaduje protokol, který může být vyjádřený jako můžou být součástí dvojici název/hodnota **hlavičky** vlastnost. Obvykle tyto informace musí být nastavená před volání <xref:System.Net.WebRequest.GetRequestStream%2A> nebo <xref:System.Net.WebRequest.GetResponse%2A> metody; po zadání požadavku metadata se považuje za jen pro čtení.  
  
 Není nutné použít **hlavičky** vlastnost na používání záhlaví metadat. Metadata specifická pro protokol mohou být zpřístupněny jako vlastnosti; například <xref:System.Net.HttpWebRequest.UserAgent%2A?displayProperty=nameWithType> zpřístupňuje vlastnost **User-Agent** hlavičky protokolu HTTP. Když vystavit Záhlaví metadat jako vlastnost byste neměli povolit stejné vlastnosti, která má nastavit pomocí **hlavičky** vlastnost.  
  
## <a name="method-property"></a>Vlastnost – metoda  
 <xref:System.Net.WebRequest.Method%2A> Vlastnost obsahuje příkaz nebo akce, která požadavek je žádostí serveru provádět. Výchozí hodnota pro **metoda** vlastnost musíte povolit standardní požadavků a odpovědí akce bez nutnosti jakékoli vlastnosti specifické pro protokol nastavení. Například <xref:System.Net.HttpWebResponse.Method%2A> výchozí hodnoty metody GET, které požádá o prostředek z webového serveru a vrátí odpověď.  
  
 Obvykle **ContentLength** vlastnost musí být nastaven na hodnotu větší než nula v případě **metoda** je nastavena na příkaz nebo akce, která určuje nahrávaný probíhá.  
  
## <a name="preauthenticate-property"></a>PreAuthenticate vlastnost  
 Sada aplikací <xref:System.Net.WebRequest.PreAuthenticate%2A> vlastnost označující, že ověřovací informace by měly být odeslány s původní žádost místo čekání na výzvu ověřování. **PreAuthenticate** vlastnost je pouze smysl, pokud protokol podporuje pověření pro ověření se počáteční požadavek odeslal.  
  
## <a name="proxy-property"></a>Vlastnost proxy  
 <xref:System.Net.WebRequest.Proxy%2A> Vlastnost obsahuje <xref:System.Net.IWebProxy> rozhraní, které slouží k přístupu k požadovanému zdroji. **Proxy** vlastnost má smysl pouze v případě, že váš protokol podporuje směrovány přes proxy server požadavky. Pokud je váš protokol je potřeba nastavit výchozí proxy server.  
  
 V některých prostředích, jako za podniková brána firewall, váš protokol bude pravděpodobně nutné použít proxy server. V takovém případě musí implementovat **IWebProxy** rozhraní pro vytvoření třídy proxy serveru, který bude fungovat pro váš protokol.  
  
## <a name="requesturi-property"></a>Vlastnost RequestUri  
 <xref:System.Net.WebRequest.RequestUri%2A> Vlastnost obsahuje identifikátor URI, který byl předán **WebRequest.Create** metoda. Je jen pro čtení a nelze **WebRequest** byla vytvořena. Pokud váš protokol podporuje přesměrování, odpověď vyplývají ze zdroje identifikovaného identifikátorem jiný identifikátor URI. Pokud potřebujete poskytovat přístup k identifikátoru URI, který odpověděl, je nutné zadat ve další vlastnosti obsahující tento identifikátor URI.  
  
## <a name="timeout-property"></a>Vlastnost časového limitu  
 <xref:System.Net.WebRequest.Timeout%2A> Vlastnost obsahuje dobu v milisekundách pro čekání, než vyprší časový limit žádost a vyvolá výjimku. **Časový limit** se vztahuje pouze na synchronní žádosti provedené <xref:System.Net.WebRequest.GetResponse%2A> metoda; asynchronní požadavky musí používat <xref:System.Net.WebRequest.Abort%2A> metoda zrušení čekající žádosti.  
  
 Nastavení **časový limit** vlastnost má smysl pouze v případě, že třída specifické pro protokol implementuje časový limit procesu.  
  
## <a name="abort-method"></a>Abort – metoda  
 <xref:System.Net.WebRequest.Abort%2A> Metoda zruší čekající asynchronní požadavek na server. Po požadavek byl zrušen, volání **GetResponse**, **BeginGetResponse**, **EndGetResponse**, **GetRequestStream**,  **BeginGetRequestStream**, nebo **EndGetRequestStream** vyvolá výjimku <xref:System.Net.WebException> s <xref:System.Net.WebException.Status%2A> vlastnost nastavena na hodnotu <xref:System.Net.WebExceptionStatus>.  
  
## <a name="begingetrequeststream-and-endgetrequeststream-methods"></a>BeginGetRequestStream a EndGetRequestStream metody  
 <xref:System.Net.WebRequest.BeginGetRequestStream%2A> Metoda spustí Asynchronní požadavek pro datový proud, který se používá k odesílání dat do serveru. <xref:System.Net.WebRequest.EndGetRequestStream%2A> Metoda dokončení asynchronní požadavek a vrátí požadovaný datový proud. Tyto metody implementovat **GetRequestStream** metodu pomocí standardní asynchronní vzor rozhraní .NET Framework.  
  
## <a name="begingetresponse-and-endgetresponse-methods"></a>BeginGetResponse a EndGetResponse metody  
 <xref:System.Net.WebRequest.BeginGetResponse%2A> Metoda spustí Asynchronní požadavek na server. <xref:System.Net.WebRequest.EndGetResponse%2A> Metoda dokončení asynchronní požadavek a vrátí požadovaný odpovědi. Tyto metody implementovat **GetResponse** metodu pomocí standardní asynchronní vzor rozhraní .NET Framework.  
  
## <a name="getrequeststream-method"></a>GetRequestStream – metoda  
 <xref:System.Net.WebRequest.GetRequestStream%2A> Metoda vrátí datový proud, který se používá k zápisu dat na požadovaný server. Datový proud vrátil by měl být jen pro zápis datový proud, který není Hledat; je určený jako jednosměrný datový proud dat, která je zapsán do serveru. Vrátí hodnotu false pro datový proud <xref:System.IO.Stream.CanRead%2A> a <xref:System.IO.Stream.CanSeek%2A> vlastnosti a hodnotu true pro <xref:System.IO.Stream.CanWrite%2A> vlastnost.  
  
 **GetRequestStream** metoda obvykle otevře připojení k serveru, a před vrácením datového proudu, odešle informace hlavičky, která určuje, že data odesílají na server. Protože **GetRequestStream** začne žádosti, nastavení žádné **záhlaví** vlastnosti nebo **ContentLength** vlastnost není povolená obvykle po volání metody **GetRequestStream**.  
  
## <a name="getresponse-method"></a>GetResponse – metoda  
 <xref:System.Net.WebRequest.GetResponse%2A> Metoda vrátí následníka specifické pro protokol <xref:System.Net.WebResponse> třídu, která představuje odpověď ze serveru. Pokud žádost již byla inicializována pomocí **GetRequestStream** metody **GetResponse** metoda vytvoří připojení k prostředku označeném identifikátorem **RequestUri**, odešle informace hlavičky označující typ požadavku prováděné a pak obdrží odpověď od prostředku.  
  
 Jednou **GetResponse** metoda je volána, všechny vlastnosti by mělo být jen pro čtení. **WebRequest** instance jsou určeny k použití jednorázové; Pokud chcete, aby jinou žádost, měli byste vytvořit nový **WebRequest**.  
  
 **GetResponse** metoda zodpovídá za vytvoření odpovídající **WebResponse** následné tak, aby obsahovala příchozí odpovědi.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.FileWebRequest>  
 [Programování připojitelných protokolů](../../../docs/framework/network-programming/programming-pluggable-protocols.md)  
 [Odvození z odpovědi WebResponse](../../../docs/framework/network-programming/deriving-from-webresponse.md)
