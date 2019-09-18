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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048603"
---
# <a name="deriving-from-webrequest"></a>Odvození ze žádosti WebRequest
<xref:System.Net.WebRequest> Třída je abstraktní základní třída, která poskytuje základní metody a vlastnosti pro vytvoření obslužné rutiny žádosti specifické pro protokol, která odpovídá modelu .NET Framework připojitelné k protokolu. Aplikace, které používají třídu **WebRequest** , mohou vyžádat data pomocí libovolného podporovaného protokolu, aniž by museli zadat použitý protokol.  
  
 Aby bylo možné třídu specifickou pro protokol použít jako připojitelný protokol, musí být splněné dvě kritéria: Třída musí implementovat <xref:System.Net.IWebRequestCreate> rozhraní a musí <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> se zaregistrovat spolu s metodou. Třída musí přepsat všechny abstraktní metody a vlastnosti **WebRequest** za účelem poskytnutí připojitelné rozhraní.  
  
 Instance **WebRequest** jsou určené pro jednorázové použití; Pokud chcete vytvořit další žádost, vytvořte novou **WebRequest**. **WebRequest** podporuje <xref:System.Runtime.Serialization.ISerializable> rozhraní, které vývojářům umožní serializovat šablonu **WebRequest** a pak šablonu znovu sestavit pro další požadavky.  
  
## <a name="iwebrequest-create-method"></a>IWebRequest – metoda Create  
 <xref:System.Net.IWebRequestCreate.Create%2A> Metoda je zodpovědná za inicializaci nové instance třídy specifické pro protokol. Když je vytvořena nová **WebRequest** , <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metoda odpovídá požadovanému identifikátoru URI s předponami URI registrovanými metodou **RegisterPrefix** . Metoda **Create** správného následníka konkrétního protokolu musí vracet inicializované instance následníka schopné provést standardní transakci žádosti nebo odpovědi pro protokol bez nutnosti měnit pole specifická pro protokol. .  
  
## <a name="connectiongroupname-property"></a>ConnectionGroupName Property  
 Tato <xref:System.Net.WebRequest.ConnectionGroupName%2A> vlastnost slouží k pojmenování skupin připojení k prostředku, aby bylo možné vytvořit více požadavků v rámci jednoho připojení. Chcete-li implementovat sdílení připojení, je nutné použít metodu sdružování a přiřazování připojení, která je specifická pro protokol. Například poskytnutá <xref:System.Net.ServicePointManager> třída implementuje sdílení připojení <xref:System.Net.HttpWebRequest> pro třídu. Třída **Třída ServicePointManager** vytvoří <xref:System.Net.ServicePoint> , která poskytuje připojení ke konkrétnímu serveru pro každou skupinu připojení.  
  
## <a name="contentlength-property"></a>Vlastnost ContentLength  
 <xref:System.Net.WebRequest.ContentLength%2A> Vlastnost určuje počet bajtů dat, která budou odeslána na server při nahrávání dat.  
  
 Vlastnost musí být obvykle nastavena tak, aby označovala, že nahrávání probíhá, když je vlastnost ContentLength nastavena na hodnotu větší než nula. <xref:System.Net.WebRequest.Method%2A>  
  
## <a name="contenttype-property"></a>ContentType – vlastnost  
 <xref:System.Net.WebRequest.ContentType%2A> Vlastnost poskytuje všechny zvláštní informace, které protokol vyžaduje k odeslání na server, aby bylo možné identifikovat typ obsahu, který odesíláte. Obvykle se jedná o typ obsahu MIME všech nahraných dat.  
  
## <a name="credentials-property"></a>Vlastnost přihlašovací údaje  
 <xref:System.Net.WebRequest.Credentials%2A> Vlastnost obsahuje informace potřebné k ověření žádosti se serverem. Je nutné implementovat podrobnosti procesu ověřování pro váš protokol. <xref:System.Net.AuthenticationManager> Třída zodpovídá za ověřování požadavků a poskytování ověřovacího tokenu. Třída, která poskytuje pověření používaná protokolem, musí implementovat <xref:System.Net.ICredentials> rozhraní.  
  
## <a name="headers-property"></a>Vlastnost Headers  
 <xref:System.Net.WebRequest.Headers%2A> Vlastnost obsahuje libovolnou kolekci párů název/hodnota metadat přidružených k žádosti. Všechna metadata potřebná v protokolu, která lze vyjádřit jako dvojici název/hodnota, lze zahrnout do vlastnosti **Headers** . Tyto informace jsou obvykle nutné nastavit před voláním <xref:System.Net.WebRequest.GetRequestStream%2A> metody <xref:System.Net.WebRequest.GetResponse%2A> nebo; po provedení žádosti jsou metadata považována za jen pro čtení.  
  
 Pro použití metadat hlaviček není nutné použít vlastnost **Headers** . Metadata specifická pro protokol se dají zveřejnit jako vlastnosti. <xref:System.Net.HttpWebRequest.UserAgent%2A?displayProperty=nameWithType> vlastnost například zveřejňuje hlavičku HTTP **uživatelského agenta** . Když zveřejňujete metadata hlaviček jako vlastnost, neměli byste mít možnost nastavit tuto vlastnost pomocí vlastnosti **Headers** .  
  
## <a name="method-property"></a>Vlastnost metody  
 <xref:System.Net.WebRequest.Method%2A> Vlastnost obsahuje operaci nebo akci, kterou požadavek vyžaduje k provedení serveru. Výchozí hodnota pro vlastnost **Method** musí umožňovat standardní akci žádosti nebo odpovědi, aniž by bylo nutné nastavit vlastnosti specifické pro protokol. <xref:System.Net.HttpWebResponse.Method%2A> Metoda například nastaví jako výchozí hodnotu získat, která vyžaduje prostředek z webového serveru a vrátí odpověď.  
  
 Vlastnost **ContentLength** musí být obvykle nastavena na hodnotu větší než nula, pokud je vlastnost **Method** nastavena na operaci nebo akci, která označuje, že probíhá nahrávání.  
  
## <a name="preauthenticate-property"></a>Vlastnost předběžně ověřit  
 Aplikace nastaví <xref:System.Net.WebRequest.PreAuthenticate%2A> vlastnost tak, aby označovala, že ověřovací údaje by měly být odesílány s počátečním požadavkem a nikoli čekáním na ověřovací výzvu. Vlastnost předběžného **ověření** má smysl pouze v případě, že protokol podporuje ověřovací přihlašovací údaje odeslané s počátečním požadavkem.  
  
## <a name="proxy-property"></a>Vlastnost proxy  
 <xref:System.Net.WebRequest.Proxy%2A> Vlastnost<xref:System.Net.IWebProxy> obsahuje rozhraní, které se používá pro přístup k požadovanému prostředku. Vlastnost **proxy** má smysl jenom v případě, že váš protokol podporuje proxy požadavky. Výchozí proxy server musíte nastavit, pokud ho váš protokol vyžaduje.  
  
 V některých prostředích, jako je třeba za podnikovou bránou firewall, může být protokol nutný k použití proxy serveru. V takovém případě je nutné implementovat rozhraní **IWebProxy** a vytvořit třídu proxy, která bude pro váš protokol fungovat.  
  
## <a name="requesturi-property"></a>Vlastnost RequestUri  
 Vlastnost obsahuje identifikátor URI, který byl předán metodě **WebRequest. Create.** <xref:System.Net.WebRequest.RequestUri%2A> Je jen pro čtení a po vytvoření **WebRequest** nelze změnit. Pokud protokol podporuje přesměrování, může odpověď pocházet z prostředku identifikovaného jiným identifikátorem URI. Pokud potřebujete poskytnout přístup k identifikátoru URI, který odpověděl, musíte zadat další vlastnost obsahující tento identifikátor URI.  
  
## <a name="timeout-property"></a>Timeout – vlastnost  
 <xref:System.Net.WebRequest.Timeout%2A> Vlastnost obsahuje dobu v milisekundách, po kterou se má čekat před vypršením časového limitu požadavku a vyvolá výjimku. **Timeout** se vztahuje pouze na synchronní požadavky vytvořené <xref:System.Net.WebRequest.GetResponse%2A> metodou. asynchronní <xref:System.Net.WebRequest.Abort%2A> požadavky musí použít metodu pro zrušení žádosti, která čeká na vyřízení.  
  
 Nastavení vlastnosti **timeout** má smysl pouze v případě, že třída specifická pro protokol implementuje proces časového limitu.  
  
## <a name="abort-method"></a>Abort – metoda  
 <xref:System.Net.WebRequest.Abort%2A> Metoda zruší probíhající asynchronní požadavek na server. Po zrušení žádosti volání **GetResponse**, **BeginGetResponse nelze**, **EndGetResponse**, **GetRequestStream**, **funkci BeginGetRequestStream**nebo **EndGetRequestStream** vyvolá výjimku <xref:System.Net.WebException> s vlastnost <xref:System.Net.WebException.Status%2A> je nastavena na <xref:System.Net.WebExceptionStatus>hodnotu.  
  
## <a name="begingetrequeststream-and-endgetrequeststream-methods"></a>Metody funkci BeginGetRequestStream a EndGetRequestStream  
 <xref:System.Net.WebRequest.BeginGetRequestStream%2A> Metoda spustí asynchronní požadavek pro datový proud, který slouží k nahrání dat na server. <xref:System.Net.WebRequest.EndGetRequestStream%2A> Metoda dokončí asynchronní požadavek a vrátí požadovaný datový proud. Tyto metody implementují metodu **GetRequestStream** pomocí asynchronního vzoru Standard .NET Framework.  
  
## <a name="begingetresponse-and-endgetresponse-methods"></a>Metody BeginGetResponse nelze a EndGetResponse  
 <xref:System.Net.WebRequest.BeginGetResponse%2A> Metoda spustí asynchronní požadavek na server. <xref:System.Net.WebRequest.EndGetResponse%2A> Metoda dokončí asynchronní požadavek a vrátí požadovanou odpověď. Tyto metody implementují metodu **GetResponse** pomocí asynchronního vzoru Standard .NET Framework.  
  
## <a name="getrequeststream-method"></a>Metoda GetRequestStream  
 <xref:System.Net.WebRequest.GetRequestStream%2A> Metoda vrátí datový proud, který se používá k zápisu dat na požadovaný server. Vrácený datový proud by měl být datový proud jen pro zápis, který nehledá; je určený jako jednosměrný datový proud dat, který se zapisuje na server. Datový proud vrátí hodnotu false pro <xref:System.IO.Stream.CanRead%2A> <xref:System.IO.Stream.CanWrite%2A> vlastnosti <xref:System.IO.Stream.CanSeek%2A> a a hodnotu true pro vlastnost.  
  
 Metoda **GetRequestStream** obvykle otevírá připojení k serveru a před vrácením datového proudu pošle informaci hlavičky, která indikuje, že se data odesílají na server. Vzhledem k tomu, že **GetRequestStream** zahájí požadavek, nastavení vlastností **záhlaví** nebo vlastnosti **ContentLength** obvykle není po volání **GetRequestStream**povoleno.  
  
## <a name="getresponse-method"></a>Metoda GetResponse  
 Metoda vrátí následníka <xref:System.Net.WebResponse> třídy, která představuje odpověď ze serveru. <xref:System.Net.WebRequest.GetResponse%2A> Pokud žádost již nebyla iniciována metodou **GetRequestStream** , metoda **GetResponse** vytvoří připojení k prostředku identifikovanému **RequestUri**, pošle informace hlavičky určující typ žádosti, která je určena. a poté obdrží odpověď z prostředku.  
  
 Po volání metody **GetResponse** by měly být všechny vlastnosti považovány za jen pro čtení. Instance **WebRequest** jsou určené pro jednorázové použití; Pokud chcete vytvořit další žádost, měli byste vytvořit novou **WebRequest**.  
  
 Metoda **GetResponse** zodpovídá za vytvoření vhodného následníka **WebResponse** , který bude obsahovat příchozí odpověď.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.WebRequest>
- <xref:System.Net.HttpWebRequest>
- <xref:System.Net.FileWebRequest>
- [Programování připojitelných protokolů](programming-pluggable-protocols.md)
- [Odvození z odpovědi WebResponse](deriving-from-webresponse.md)
