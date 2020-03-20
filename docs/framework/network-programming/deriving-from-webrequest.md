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
ms.openlocfilehash: 6bee864f8d24076d16f226c29d61801e856739d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048603"
---
# <a name="deriving-from-webrequest"></a>Odvození ze žádosti WebRequest
Třída <xref:System.Net.WebRequest> je abstraktní základní třída, která poskytuje základní metody a vlastnosti pro vytvoření obslužné rutiny požadavku specifické pro protokol, která odpovídá modelu protokolu připojitelného rozhraní .NET Framework. Aplikace, které používají třídu **WebRequest,** mohou požadovat data pomocí libovolného podporovaného protokolu bez nutnosti zadat použitý protokol.  
  
 Aby byla třída specifická pro protokol použita jako připojitelný protokol, musí být <xref:System.Net.IWebRequestCreate> splněna dvě kritéria: <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> Třída musí implementovat rozhraní a musí se zaregistrovat metodou. Třída musí přepsat všechny abstraktní metody a vlastnosti **WebRequest** poskytnout připojitelné rozhraní.  
  
 **Instance WebRequest** jsou určeny pro jednorázové použití. Pokud chcete podat další požadavek, vytvořte nový **WebRequest**. **WebRequest** podporuje <xref:System.Runtime.Serialization.ISerializable> rozhraní, které vývojářům umožňuje serializovat šablonu **WebRequest** a poté rekonstruovat šablonu pro další požadavky.  
  
## <a name="iwebrequest-create-method"></a>Metoda vytvoření iWebRequest  
 Metoda <xref:System.Net.IWebRequestCreate.Create%2A> je zodpovědná za inicializaci nové instance třídy specifické pro protokol. Při vytvoření nového požadavku <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> **WebRequest** odpovídá metoda požadovanému identifikátoru URI s předčíslími URI registrovanými metodou **RegisterPrefix.** Create **Create** Metoda správného potomka specifického pro protokol musí vrátit inicializovanou instanci následníka schopného provádět standardní transakci požadavku a odpovědi pro protokol bez nutnosti změny polí specifických pro protokol.  
  
## <a name="connectiongroupname-property"></a>Vlastnost ConnectionGroupName  
 Vlastnost <xref:System.Net.WebRequest.ConnectionGroupName%2A> se používá k pojmenování skupiny připojení k prostředku tak, aby více požadavků lze provést přes jedno připojení. Chcete-li implementovat sdílení připojení, musíte použít metodu sdružování a přiřazování připojení specifickou pro protokol. Například za předpokladu, že <xref:System.Net.ServicePointManager> třída <xref:System.Net.HttpWebRequest> implementuje sdílení připojení pro třídu. Třída **ServicePointManager** vytvoří <xref:System.Net.ServicePoint> připojení k určitému serveru pro každou skupinu připojení.  
  
## <a name="contentlength-property"></a>Vlastnost ContentLength  
 Vlastnost <xref:System.Net.WebRequest.ContentLength%2A> určuje počet bajtů dat, která budou odeslána na server při nahrávání dat.  
  
 Vlastnost <xref:System.Net.WebRequest.Method%2A> musí být obvykle nastavena tak, aby označovala, že nahrávání probíhá, když je vlastnost **ContentLength** nastavena na hodnotu větší než nula.  
  
## <a name="contenttype-property"></a>Vlastnost ContentType  
 Tato <xref:System.Net.WebRequest.ContentType%2A> vlastnost poskytuje všechny zvláštní informace, které protokol vyžaduje, abyste odeslali na server k identifikaci typu odesílaného obsahu. Obvykle se jedná o typ obsahu MIME všech nahraných dat.  
  
## <a name="credentials-property"></a>Vlastnost pověření  
 Vlastnost <xref:System.Net.WebRequest.Credentials%2A> obsahuje informace potřebné k ověření požadavku na serveru. Je nutné implementovat podrobnosti procesu ověřování pro váš protokol. Třída <xref:System.Net.AuthenticationManager> je zodpovědná za ověřování požadavků a poskytování ověřovacího tokenu. Třída, která poskytuje pověření používaná protokolem, musí implementovat <xref:System.Net.ICredentials> rozhraní.  
  
## <a name="headers-property"></a>Vlastnost záhlaví  
 Vlastnost <xref:System.Net.WebRequest.Headers%2A> obsahuje libovolnou kolekci párů názvů a hodnot metadat přidružených k požadavku. Všechna metadata potřebná protokolem, která mohou být vyjádřena jako dvojice název/hodnota, mohou být zahrnuta do **vlastnosti Headers.** Obvykle tyto informace musí být <xref:System.Net.WebRequest.GetRequestStream%2A> nastaveny před voláním nebo <xref:System.Net.WebRequest.GetResponse%2A> metody; po vytvoření žádosti jsou metadata považována za jen pro čtení.  
  
 Není nutné používat **Headers** vlastnost používat metadata záhlaví. Metadata specifická pro protokol mohou být vystavena jako vlastnosti; <xref:System.Net.HttpWebRequest.UserAgent%2A?displayProperty=nameWithType> například vlastnost zpřístupňuje hlavičku HTTP **user-agenta.** Když zveřejňujete metadata záhlaví jako vlastnost, neměli byste povolit stejnou vlastnost, která má být nastavena pomocí **headers** vlastnost.  
  
## <a name="method-property"></a>Vlastnost metody  
 Vlastnost <xref:System.Net.WebRequest.Method%2A> obsahuje příkaz nebo akci, o kterou požadavek žádá server. Výchozí hodnota vlastnosti **Method** musí povolit standardní akci požadavku a odpovědi bez nutnosti nastavení vlastností specifických pro protokol. Například <xref:System.Net.HttpWebResponse.Method%2A> metoda výchozí GET, který požaduje prostředek z webového serveru a vrátí odpověď.  
  
 Vlastnost **ContentLength** musí být obvykle nastavena na hodnotu větší než nula, pokud je vlastnost **Method** nastavena na příkaz ové nebo akce, která označuje, že dochází k nahrávání.  
  
## <a name="preauthenticate-property"></a>Vlastnost Předběžné ověření  
 Aplikace nastavit <xref:System.Net.WebRequest.PreAuthenticate%2A> vlastnost označující, že informace o ověřování by měly být odesílány s počáteční požadavek spíše než čekání na výzvu ověřování. Vlastnost **PreAuthenticate** je smysluplná pouze v případě, že protokol podporuje ověřovací pověření odeslaná s počátečním požadavkem.  
  
## <a name="proxy-property"></a>Vlastnost proxy serveru  
 Vlastnost <xref:System.Net.WebRequest.Proxy%2A> obsahuje <xref:System.Net.IWebProxy> rozhraní, které se používá pro přístup k požadovanému prostředku. Vlastnost **Proxy** má smysl pouze v případě, že protokol podporuje proxied požadavky. Je nutné nastavit výchozí proxy server, pokud je vyžadován protokolem.  
  
 V některých prostředích, například za podnikovou bránou firewall, může být protokol vyžadován k použití proxy serveru. V takovém případě je nutné implementovat rozhraní **IWebProxy** k vytvoření proxy třídy, která bude fungovat pro váš protokol.  
  
## <a name="requesturi-property"></a>Vlastnost RequestUri  
 Vlastnost <xref:System.Net.WebRequest.RequestUri%2A> obsahuje identifikátor URI, který byl předán metodě **WebRequest.Create.** Je jen pro čtení a nelze jej změnit, jakmile byl vytvořen **požadavek WebRequest.** Pokud váš protokol podporuje přesměrování, odpověď může pocházet z prostředku identifikovaného jiným identifikátorem URI. Pokud potřebujete poskytnout přístup k identifikátoru URI, který odpověděl, je nutné zadat další vlastnost obsahující tento identifikátor URI.  
  
## <a name="timeout-property"></a>Vlastnost časového opovenču  
 Vlastnost <xref:System.Net.WebRequest.Timeout%2A> obsahuje dobu v milisekundách, než časový čas požadavku a vyvolá výjimku. **Časový čas** se vztahuje pouze na synchronní <xref:System.Net.WebRequest.GetResponse%2A> požadavky provedené s metodou; asynchronní požadavky musí použít <xref:System.Net.WebRequest.Abort%2A> metodu ke zrušení čekající ho požadavku.  
  
 Nastavení **Timeout** vlastnost je smysluplné pouze v případě, že třída specifické pro protokol implementuje proces časového opomu.  
  
## <a name="abort-method"></a>Abort – metoda  
 Metoda <xref:System.Net.WebRequest.Abort%2A> zruší čekající asynchronní požadavek na server. Po zrušení požadavku bude volání **GetResponse**, **BeginGetResponse**, **EndGetResponse**, GetStream , **GetGetStream**, **BeginGetRequestStream**nebo **EndGetRequestStream** vyvolá a <xref:System.Net.WebException> s vlastností <xref:System.Net.WebException.Status%2A> nastavenou na <xref:System.Net.WebExceptionStatus>.  
  
## <a name="begingetrequeststream-and-endgetrequeststream-methods"></a>Metody BeginGetRequestStream a EndGetRequestStream  
 Metoda <xref:System.Net.WebRequest.BeginGetRequestStream%2A> spustí asynchronní požadavek pro datový proud, který se používá k odeslání dat na server. Metoda <xref:System.Net.WebRequest.EndGetRequestStream%2A> dokončí asynchronní požadavek a vrátí požadovaný datový proud. Tyto metody implementují metodu **GetRequestStream** pomocí standardního asynchronního vzoru rozhraní .NET Framework.  
  
## <a name="begingetresponse-and-endgetresponse-methods"></a>Metody BeginGetResponse a EndGetResponse  
 Metoda <xref:System.Net.WebRequest.BeginGetResponse%2A> spustí asynchronní požadavek na server. Metoda <xref:System.Net.WebRequest.EndGetResponse%2A> dokončí asynchronní požadavek a vrátí požadovanou odpověď. Tyto metody implementují metodu **GetResponse** pomocí standardního asynchronního vzoru rozhraní .NET Framework.  
  
## <a name="getrequeststream-method"></a>Metoda GetRequestStream  
 Metoda <xref:System.Net.WebRequest.GetRequestStream%2A> vrátí datový proud, který se používá k zápisu dat na požadovaný server. Datový proud vrácena by měl být datový proud pouze pro zápis, který nehledá; je určen jako jednosměrný datový proud, který je zapsán na server. Datový proud vrátí <xref:System.IO.Stream.CanRead%2A> false <xref:System.IO.Stream.CanSeek%2A> pro vlastnosti <xref:System.IO.Stream.CanWrite%2A> a true pro vlastnost.  
  
 Metoda **GetRequestStream** obvykle otevře připojení k serveru a před vrácením datového proudu odešle informace záhlaví, které označují, že data jsou odesílána na server. Vzhledem k tomu, **že GetRequestStream** začíná požadavek, nastavení všech vlastností **záhlaví** nebo **ContentLength** vlastnost je obvykle není povoleno po volání **GetRequestStream**.  
  
## <a name="getresponse-method"></a>Metoda getresponse  
 Metoda <xref:System.Net.WebRequest.GetResponse%2A> vrátí potomek <xref:System.Net.WebResponse> třídy specifický pro protokol, který představuje odpověď ze serveru. Pokud požadavek již byla zahájena **GetRequestStream** metoda, **GetResponse** metoda vytvoří připojení k prostředku identifikované **RequestUri**, odešle informace záhlaví označující typ požadavku, který je podán, a pak obdrží odpověď z prostředku.  
  
 Jakmile **getresponse** metoda je volána, všechny vlastnosti by měly být považovány za jen pro čtení. **Instance WebRequest** jsou určeny pro jednorázové použití. Pokud chcete podat další požadavek, měli byste vytvořit nový **WebRequest**.  
  
 **Metoda GetResponse** je zodpovědná za vytvoření příslušného potomka **WebResponse,** který bude obsahovat příchozí odpověď.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.WebRequest>
- <xref:System.Net.HttpWebRequest>
- <xref:System.Net.FileWebRequest>
- [Programování připojitelných protokolů](programming-pluggable-protocols.md)
- [Odvození z odpovědi WebResponse](deriving-from-webresponse.md)
