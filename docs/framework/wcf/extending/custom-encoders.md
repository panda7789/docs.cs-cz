---
title: Vlastní kodéry
ms.date: 03/30/2017
ms.assetid: fa0e1d7f-af36-4bf4-aac9-cd4eab95bc4f
ms.openlocfilehash: cd8b9172278ce5bcca2965872d697b03698bd850
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50034342"
---
# <a name="custom-encoders"></a>Vlastní kodéry
Toto téma popisuje, jak vytvořit vlastní kodéry.  
  
 Ve Windows Communication Foundation (WCF), je použít *vazby* určete, jak přenášet data přes síť mezi koncovými body. Vazba se skládá z posloupnosti *elementů vazby*. Vazba obsahuje volitelné protokol vazby prvky jako je zabezpečení, požadované *kodéru zpráv* element vazby a element vazby přenosu vyžaduje. Kodér zprávy je reprezentován element vazby kódování zprávy. Tři kodérů zprávy jsou součástí WCF: binární soubor, zpráv přenosu optimalizace mechanismus (MTOM) a Text.  
  
 Element vazby kódování serializuje odchozí zprávu <xref:System.ServiceModel.Channels.Message> a předá ji do přenosu, nebo přijímá serializovanou formu zpráva z přenosu a předá ji do vrstvy protokolu, pokud jsou k dispozici, nebo k aplikaci, pokud není k dispozici.  
  
 Transformují kodéry zpráva <xref:System.ServiceModel.Channels.Message> instance do a z síťové vyjádření. I když kodérů jsou popsány jako nesídlí nad přenosové vrstvy v zásobníku kanál, jsou umístěné v přenosové vrstvě. Přenosy (třeba HTTP) formátu zpráv podle požadavků standardu přenosu. Kodérů (například Xml na Text) jenom kódování zprávy.  
  
 Při připojování k dříve existující klient nebo server, nemusí mít možnost použití určité zprávy kódování. Ale WCF služby můžou být přístupné přes několik koncových bodů, každý s kodéru různé zprávy. Při jedné kodér nepokrývá celý cílový pro vaši službu, vezměte v úvahu vystavení služby přes několik koncových bodů. Klientské aplikace pak můžou zvolit koncový bod, který je pro ně nejvhodnější. Pomocí více koncových bodů můžete zkombinovat s jinými prvky vazby výhody jiná zpráva kodérů.  
  
## <a name="system-provided-encoders"></a>Poskytnuté systémem kodérů  
 WCF poskytuje několik vazeb poskytovaných systémem, které jsou navrženy pro nejčastější scénáře aplikací. Každá z těchto vazeb kombinovat přenosu, kodéru zpráv a dalších možností (například zabezpečení). Toto téma popisuje, jak rozšířit `Text`, `Binary`, a `MTOM` kodéry, které jsou součástí WCF, nebo vytvořte vlastní vlastní kodér zpráv. Kodér textu zprávy podporuje prostý XML encoding i kódování SOAP. Standardní režim kódování XML kodér textu zprávy se nazývá kodér POX ("Plain Old XML") pro jeho odlišení od založený na textu protokolu SOAP kódování.  
  
 Další informace o kombinacích prvky vazeb poskytovaných vazeb poskytovaných systémem, naleznete v části odpovídající v [volba přenosu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
## <a name="how-to-work-with-system-provided-encoders"></a>Jak pracovat s poskytnutými systémem kodérů  
 Kódování se přidá do vazby pomocí třídy odvozené od <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
 Poskytuje následující typy odvozené z elementů vazby WCF <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> třídu, která můžete zadat text, binárního souboru a kódování zpráv přenosu optimalizace mechanismus (MTOM):  
  
-   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>: Nejvíce interoperabilní, ale nejméně efektivní kodéru zpráv XML. Webová služba nebo klient webové služby obecně by rozuměla textové XML. Ale přenosu velkých bloků binárních dat jako text není efektivní.  
  
-   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>: Představuje element vazby, který určuje kódování znaků a verzování zprávy použité pro binární soubor založené zprávy XML. Toto je nejefektivnější možnosti kódování, ale nejméně interoperabilní, protože je podporován pouze pomocí koncových bodů WCF.  
  
-   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>: Představuje element vazby, který určuje kódování znaků a správu verzí zpráv používá zprávy pomocí kódování zpráv přenosu optimalizace mechanismus (MTOM). MTOM je efektivní technologie pro přenos zpráv WCF binární data. Kodér MTOM se pokusí rovnováhu mezi efektivitu a vzájemná funkční spolupráce. Kódování MTOM přenáší většina XML v textové formě, ale optimalizuje velkých bloků binárních dat jako ušetřený přenosem-je, bez převodu na text.  
  
 Element vazby vytvoří binární soubor, MTOM nebo text <xref:System.ServiceModel.Channels.MessageEncoderFactory>. Vytvoří objekt pro vytváření binární soubor, MTOM nebo text <xref:System.ServiceModel.Channels.MessageEncoderFactory> instance. Obvykle je zaznamenána pouze jedna instance. Ale pokud jsou použity relace, můžeme poskytovat různé kodér každé relaci. Binárního kodéru využívá to ke koordinaci dynamické slovníky (viz XML, infrastrukturu).  
  
 <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A> a <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A> metody jsou základní u kodérů. Poskytují metody pro čtení z datového proudu nebo zpráva <xref:System.Byte> pole. Bajtová pole se používají při přenosu pracuje v režimu vyrovnávací paměti. Vždy se zprávy zapisují do datových proudů. Pokud přenos musí uložit do vyrovnávací paměti se zpráva, poskytuje datový proud, který nemá vyrovnávací paměti.  
  
 Zbývající členy fungují s typy médií obsahu, podpora, a <xref:System.ServiceModel.Channels.MessageEncoder.MessageVersion%2A>. Přenos volá tyto metody kodér k ověření, zda příchozí zpráva může dekódovat jím nebo k určení, zda je platný pro tento kodér odchozí zprávy.  
  
 Všechny tři implementace kodér přidá vlastnosti, které jsou relevantní pro konkrétní kódování a je plně konfigurovatelné. U kodérů také zveřejnit čtečky kvóty, které mají výchozí hodnoty zabezpečení. Diskuzi o kvóty najdete v článku XML, infrastrukturu.  
  
## <a name="features-of-system-provided-encoders"></a>Funkce poskytované systémem kodérů  
 Existuje mnoho z funkcí poskytovaných službou kodérů poskytované systémem.  
  
### <a name="pooling"></a>Sdružování  
 Každá implementace kodér pokusí fondu co největší míře. Omezení přidělení je klíče způsob, jak zlepšit výkon spravovaného kódu. K provedení této sdružování, implementace použít `SynchronizedPool` třídy. C# Soubor obsahuje popis Další optimalizace použitou touto třídou.  
  
 `XmlDictionaryReader` a `XmlDictionaryWriter` instance jsou ve fondu a znovu inicializovat, aby se zabránilo přidělení nové značky pro každou zprávu. Pro čtenáře `OnClose` čtečky uvolňuje zpětného volání při `Close()` je volána. Kodér recykluje také některé objekty stavu zprávy používá při vytváření zpráv. Velikosti tyto fondy se dají konfigurovat pomocí `MaxReadPoolSize` a `MaxWritePoolSize` vlastnosti na každé tři třídy odvozené z <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
### <a name="binary-encoding"></a>Binární kódování  
 Když binární kódování používá relace, řetězec dynamický slovník musí sdělí příjemce zprávy. To se provádí přidáním prefixu zprávu s řetězci dynamický slovník. Příjemce odstraní vypnout řetězce, se přidají do relace a zprávu zpracuje. Správně předávání řetězce slovníku vyžaduje, že přenos do vyrovnávací paměti.  
  
 Řetězce jsou připojeny k zpráva o interní `AddSessionInformationToMessage` metody. Řetězce jako UTF-8 přidá do popředí předponu jejich délku zprávy. Hlavička slovníku celý je pak předponu délky jeho data. Zpětný provoz se provádí pomocí vnitřního `ExtractSessionInformationFromMessage` metody.  
  
 Kromě zpracování dynamický slovník klíčů, jsou ve vyrovnávací paměti s relacemi zprávy přijímány jednoznačným způsobem. Místo vytváření čtečky přes dokument a její zpracování, používá vnitřní binárního kodéru `MessagePatterns` třídy dekonstruovat binárního datového proudu. Cílem je, že většina zprávy mají určitou sadu záhlaví, které se zobrazí v určitém pořadí při generování službou WCF. Zpráva této doby změny nepublikujete založené na co se očekává, že se rozdělí vzor systému. Pokud je úspěšná, inicializuje <xref:System.ServiceModel.Channels.MessageHeaders> objekt bez při parsování kódu XML. Pokud ne, vrátí se zpět na standardní metodu.  
  
### <a name="mtom-encoding"></a>Kódování MTOM  
 <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`> Třída nemá další konfigurační vlastnost s názvem <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`.MaxBufferSize2A%>. To umístí horní mez na tom, kolik dat je povoleno ji uložit do vyrovnávací paměti při čtení zprávy. XML informace o sadě (informační sadu) nebo jiné části MIME možná muset být sestavit všechny části MIME do jedné zprávy do vyrovnávací paměti.  
  
 Pro fungování s protokolem HTTP, poskytuje vnitřní třídu zpráv kodér MTOM některá interní rozhraní API pro `GetContentType` (což je také vnitřní) a `WriteMessage`, což je veřejná a mohou být přepsána nastaveními. Pokud chcete zajistit, aby hodnoty v hlavičkách protokolu HTTP svůj souhlas s hodnotami v hlavičky MIME se musí vyskytovat další komunikaci.  
  
 Kodér MTOM zpráv interně používá čtečky textu pro WCF a je podobný kodér textu. Hlavní rozdíl je, že optimalizuje velké skupiny binární soubor, nebo "Binární rozsáhlé objekty" objektů (BLOB), není jejich převedením do kódování Base-64 před je vložen do bajtů zpráv. Místo toho tyto objekty BLOB jsou udržovány extrahované a odkazované jako přílohy MIME.  
  
## <a name="writing-your-own-encoder"></a>Zápis vlastní kodér  
 Pokud chcete implementovat vlastní vlastní kodér zpráv, je nutné zadat vlastní implementace následujících základních tříd abstraktu:  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder>  
  
-   <xref:System.ServiceModel.Channels.MessageEncoderFactory>  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
  
 Převod z reprezentace v paměti zprávy na reprezentaci, jež lze zapsat do datového proudu je zapouzdřen v rámci <xref:System.ServiceModel.Channels.MessageEncoder> třídu, která slouží jako objekt pro vytváření pro XML čtečky a zapisovače XML, které podporují konkrétní typy kódování XML.  
  
-   Jsou klíčové metody této třídy, které je nutné přepsat:  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A> které přebírá <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> objektu a zapíše jej do <xref:System.IO.Stream> objektu.  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A> které přebírá <xref:System.IO.Stream> a záhlaví maximální velikost a vrací <xref:System.ServiceModel.Channels.Message> objektu.  
  
 Je kód, který píšete v těchto metodách, který zpracovává převod mezi standardní přenosový protokol a vlastní kódování.  
  
 Dál musíte kód třídu objektů factory, který vytváří vlastní kodér. Přepsat <xref:System.ServiceModel.Channels.MessageEncoderFactory.Encoder%2A> vrátit instanci vaší vlastní <xref:System.ServiceModel.Channels.MessageEncoder>.  
  
 Připojte své vlastní <xref:System.ServiceModel.Channels.MessageEncoderFactory> na zásobník element vazby, který se používá ke konfiguraci služby ani klienta tak, že přepíšete <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> metoda vrátí instanci tento objekt pro vytváření.  
  
 Existují dvě ukázky součástí WCF, které ilustrují tento proces se vzorovým kódem: [vlastní kodér zpráv: vlastní kodér textu](../../../../docs/framework/wcf/samples/custom-message-encoder-custom-text-encoder.md) a [vlastní kodér zpráv: kompresní kodér](../../../../docs/framework/wcf/samples/custom-message-encoder-compression-encoder.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.MessageEncoderFactory>  
 <xref:System.ServiceModel.Channels.MessageEncoder>  
 [Strukturální přehled přenosu dat](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 [Výběr kodéru zprávy](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [Volba přenosu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
