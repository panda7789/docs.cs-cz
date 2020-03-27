---
title: Výběr kodéru zprávy
ms.date: 03/30/2017
ms.assetid: 2204d82d-d962-4922-a79e-c9a231604f19
ms.openlocfilehash: a306896af7a73d43956638981908c12d86126a9f
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345259"
---
# <a name="choosing-a-message-encoder"></a>Výběr kodéru zprávy
Toto téma popisuje kritéria pro výběr mezi kodéry zpráv, které jsou zahrnuty v Systému Windows Communication Foundation (WCF): binární, text a mechanismus optimalizace přenosu zpráv (MTOM).  
  
 V WCF určíte, jak přenášet data v síti mezi koncovými body pomocí *vazby*, která se skládá z posloupnosti *elementů vazby*. Kodér zpráv je reprezentován elementem vazby kódování zprávy v zásobníku vazby. Vazba obsahuje prvky vazby volitelného protokolu, jako je například element vazby vazby zabezpečení nebo element vazby spolehlivého zasílání zpráv, prvek vazby kódování požadované zprávy a povinný prvek vazby přenosu.  
  
 Prvek vazby kódování zprávy je uveden pod prvky vazby volitelného protokolu a nad požadovaným prvkem vazby přenosu. Na odchozí straně kodér zpráv serializuje odchozí <xref:System.ServiceModel.Channels.Message> a předá jej přenosu. Na příchozí straně kodér zprávy obdrží serializovanou formu <xref:System.ServiceModel.Channels.Message> a z přenosu a předá ji vyšší vrstvě protokolu, pokud je k dispozici, nebo do aplikace, pokud ne.  
  
 Při připojování k již existujícímu klientovi nebo serveru pravděpodobně nemáte na výběr ohledně použití určitého kódování zpráv, protože je třeba kódovat zprávy způsobem, který druhá strana očekává. Pokud však píšete službu WCF, můžete vystavit službu prostřednictvím více koncových bodů, z nichž každý používá jiné kódování zpráv. To umožňuje klientům zvolit nejlepší kódování pro mluvení se službou přes koncový bod, který je pro ně nejlepší, stejně jako poskytuje vašim klientům flexibilitu zvolit kódování, které je pro ně nejlepší. Použití více koncových bodů také umožňuje kombinovat výhody různých kódování zpráv s jinými prvky vazby.  
  
## <a name="system-provided-encoders"></a>Kodéry poskytované systémem  
 WCF obsahuje tři kodéry zpráv, které jsou reprezentovány následujícími třemi třídami:  
  
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>, kodér textových zpráv podporuje kódování prostého xml i kódování SOAP. Režim kódování prostého XML kodére textových zpráv se nazývá "prostý starý XML" (POX), aby se odlišil od textového kódování SOAP. Chcete-li povolit <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement.MessageVersion%2A> počitadla, nastavte vlastnost na <xref:System.ServiceModel.Channels.MessageVersion.None%2A>. Kodér textových zpráv slouží ke spolupráci s koncovými body mimo WCF.  
  
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>, binární zpráva kodér, používá kompaktní binární formát a je optimalizován pro WCF na WCF komunikace, a proto není interoperabilní. Toto je také nejvýkonnější kodér všech kodéry WCF poskytuje.  
  
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>, prvek vazby, určuje kódování znaků a správu verzí zpráv pro zprávy pomocí kódování MTOM. MTOM je efektivní technologie pro přenos binárních dat ve zprávách WCF. Kodér MTOM se pokouší vytvořit rovnováhu mezi efektivitou a interoperabilitou. Kódování MTOM přenáší většinu XML v textové podobě, ale optimalizuje velké bloky binárních dat jejich přenosem tak, jak jsou, bez převodu na text. Z hlediska efektivity, mezi kodéry WCF poskytuje, MTOM je mezi textem (nejpomalejší) a binární (nejrychlejší).  
  
## <a name="how-to-choose-a-message-encoder"></a>Jak si vybrat kodér zpráv  
 Následující tabulka popisuje běžné faktory používané k výběru kodéru zpráv. Upřednostněte faktory, které jsou důležité pro vaši aplikaci, a pak zvolte kodéry zpráv, které nejlépe fungují s těmito faktory. Nezapomeňte zvážit všechny další faktory, které nejsou uvedeny v této tabulce a všechny vlastní zprávy kodéry, které mohou být požadovány ve vaší aplikaci.  
  
|Faktor|Popis|Kodéry, které podporují tento faktor|  
|------------|-----------------|---------------------------------------|  
|Podporované znakové sady|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>a <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> podporují pouze kódování UTF8 a UTF16 Unicode *(big-endian* a *little-endian).* Pokud jsou požadována jiná kódování, například UTF7 nebo ASCII, musí být použit vlastní kodér. Ukázkový vlastní kodér najdete [v tématu Vlastní kodér zpráv](https://docs.microsoft.com/dotnet/framework/wcf/samples/custom-message-encoder-custom-text-encoder).|Text|  
|Kontrolní|Kontrola je schopnost zkoumat zprávy během přenosu. Kódování textu, s nebo bez použití SOAP, umožňují zprávy, které mají být kontrolovány a analyzovány mnoha aplikacemi bez použití specializovaných nástrojů. Všimněte si, že použití zabezpečení přenosu na úrovni zprávy nebo přenosu ovlivňuje vaši schopnost kontrolovat zprávy. Důvěrnost chrání zprávu před kontrolou a integrita chrání zprávu před změnou.|Text|  
|Spolehlivost|Spolehlivost je odolnost kodéru k chybám přenosu. Spolehlivost lze také poskytnout ve zprávě, přenosu nebo aplikační vrstvě. Všechny standardní kodéry WCF předpokládají, že jiná vrstva poskytuje spolehlivost. Kodér má malou schopnost zotavit se z chyby přenosu.|Žádný|  
|Jednoduchost|Jednoduchost představuje snadnost, s jakou můžete vytvářet kodéry a dekodéry pro specifikaci kódování. Kódování textu jsou obzvláště výhodné pro jednoduchost a kódování textu POX má další výhodu, že nevyžaduje podporu pro zpracování SOAP.|Text (POX)|  
|Velikost|Kódování určuje množství režie uložené na obsah. Velikost kódovaných zpráv přímo souvisí s maximální propustností operací služby. Binární kódování jsou obecně kompaktnější než kódování textu. Pokud je velikost zprávy na prémii, zvažte také kompresi obsahu zprávy během kódování. Komprese však zvyšuje náklady na zpracování pro odesílatele zprávy i příjemce.|binární|  
|Streamování|Streamování umožňuje aplikacím zahájit zpracování zprávy před příchodem celé zprávy. Efektivní použití streamování vyžaduje, aby důležitá data pro zprávu být k dispozici na začátku zprávy tak, aby přijímající aplikace není nutné čekat na doručení. Kromě toho aplikace, které používají datový proud ového přenosu musí uspořádat data ve zprávě postupně tak, aby obsah nemá dopředné závislosti. V mnoha případech je nutné ohrozit mezi streamování obsahu a mají nejmenší možnou velikost přenosu pro tento obsah.|Žádný|  
|Podpora nástrojů třetích stran|Oblasti podpory pro kódování zahrnují vývoj a diagnostiku. Vývojáři třetích stran provedli velké investice do knihoven a sad nástrojů pro zpracování zpráv kódovaných ve formátu POX.|Text (POX)|  
|Interoperabilita|Tento faktor odkazuje na schopnost kodéru WCF spolupracovat se službami, které nejsou wcf.|Text<br /><br /> MTOM (částečné)|  
  
Poznámka: Při použití binárního kodéru nebude mít použití nastavení IgnoreWhitespace při vytváření xmlreaderu žádný vliv.  Pokud například v rámci operace služby uděláte následující kroky:  

```csharp
public void OperationContract(XElement input)
{
    Console.WriteLine("{0}", input.Value);
    int counter = 0;
    var xreader = input.CreateReader();
    var reader = XmlReader.Create(xreader, new XmlReaderSettings() { IgnoreWhitespace = true });
    while (reader.Read())
    {
        counter++;
    }

    Console.WriteLine("Read {0} lines with reader", counter);
}
```  
  
Nastavení IgnoreWhitespace je ignorováno.  
  
## <a name="compression-and-the-binary-encoder"></a>Komprese a binární kodér

Počínaje WCF 4.5 wcf binární kodér přidává podporu pro kompresi. To umožňuje použít algoritmus gzip/deflate pro odesílání komprimovaných zpráv z klienta WCF a také reagovat komprimovanými zprávami ze služby WCF s vlastním hostitelem. Tato funkce umožňuje kompresi v přenosech HTTP i TCP. Službu WCF hostovojenskou službou IIS lze vždy povolit pro odesílání komprimovaných odpovědí konfigurací hostitelského serveru služby IIS. Typ komprese je konfigurován <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A?displayProperty=nameWithType> s vlastností. Tato vlastnost je nastavena <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType> na jednu z hodnot výčtu:

- <xref:System.ServiceModel.Channels.CompressionFormat.Deflate>
- <xref:System.ServiceModel.Channels.CompressionFormat.GZip>
- <xref:System.ServiceModel.Channels.CompressionFormat.None>
  
Vzhledem k tomu, že tato vlastnost je vystavena pouze na binaryMessageEncodingBindingElement, budete muset vytvořit vlastní vazbu, jako je následující, abyste použili tuto funkci:

 ```xml
 <customBinding>
   <binding name="BinaryCompressionBinding">
     <binaryMessageEncoding compressionFormat ="GZip" />
     <httpTransport />
  </binding>
</customBinding>
 ```

Klient i služba musí souhlasit s odesíláním a přijímáním komprimovaných zpráv, a proto musí být vlastnost compressionFormat nakonfigurována na elementu binaryMessageEncoding v klientovi i ve službě. Výjimka protocol je vyvolána, pokud služba nebo klient není nakonfigurován pro kompresi, ale druhá strana je. Povolení komprese by mělo být pečlivě zváženo. Komprese je většinou užitečná, pokud je šířka pásma sítě kritickým bodem. V případě, že procesor je kritickým bodem, komprese sníží propustnost. V simulovaném prostředí musí být provedeno vhodné testování, aby se zjistilo, zda je to přínosem pro aplikaci  
  
## <a name="see-also"></a>Viz také

- [Vazby](../../../../docs/framework/wcf/feature-details/bindings.md)
