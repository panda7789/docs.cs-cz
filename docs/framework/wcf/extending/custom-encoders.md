---
title: Vlastní kodéry
ms.date: 03/30/2017
ms.assetid: fa0e1d7f-af36-4bf4-aac9-cd4eab95bc4f
ms.openlocfilehash: ae3904af83452dd76723abb78a7a06fdb0f798cc
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809274"
---
# <a name="custom-encoders"></a>Vlastní kodéry
Toto téma popisuje, jak vytvořit vlastní kodéry.  
  
 Ve Windows Communication Foundation (WCF), můžete použít *vazby* určení způsobu přenosu dat v síti mezi koncovými body. Vazba je tvořen posloupnost *elementů vazby*. Vazba obsahuje prvky vazby volitelné protokol například zabezpečení, požadovanou *kodér zpráv* prvku vazby a element vazby požadované přenosu. Kodér zpráv je reprezentována zprávu kódování prvku vazby. Tři kodéry zprávy jsou součástí WCF: binární, zpráva přenosu optimalizace mechanismus (MTOM) a Text.  
  
 Kódování prvku vazby serializuje odchozí zprávy <xref:System.ServiceModel.Channels.Message> a předává je pro přenos, nebo přijme serializovaný formu zprávu z přenosu a předá ji do vrstvy protokolu, pokud existuje, nebo k aplikaci, pokud nejsou přítomny.  
  
 Zpráva kodéry transformace <xref:System.ServiceModel.Channels.Message> instance do a z síťové vyjádření. I když kodéry jsou popsány jako najednou vyšší přenosové vrstvy v zásobníku kanál, jsou umístěny v přenosové vrstvě. Přenosy (například protokol HTTP) formátu zprávy v souladu s požadavky standardu přenosu. Kódovací moduly (například textu Xml) právě kódování zprávy.  
  
 Při připojování k dříve existující klient nebo server, nemusí mít volba o pomocí konkrétní zprávu kódování. Ale služby WCF mohou být přístupné přes několik koncových bodů, každý s kodéru různé zprávy. Při jednom kodér nepokrývá celou cílovou skupinu pro vaši službu, vezměte v úvahu vystavení služby přes několik koncových bodů. Klientské aplikace můžete pak vybrat koncový bod, který je nejvhodnější pro ně. Pomocí několik koncových bodů můžete kombinovat s jinými prvky vazby výhod kodéry jiná zpráva.  
  
## <a name="system-provided-encoders"></a>Kodéry poskytované systémem  
 WCF poskytuje několik vazeb poskytovaných systémem, které jsou navrženy tak, aby pokrývalo nejběžnějších scénářů aplikace. Každý z těchto vazeb kombinovat přenos, kodér zpráv a další možnosti (například zabezpečení). Toto téma popisuje, jak rozšířit `Text`, `Binary`, a `MTOM` kodéry, které jsou součástí WCF, nebo vytvořit vlastní kodér zpráv. Kodér textu zprávy podporuje prostý kódování XML jak kódování SOAP. Kodér POX ("prostý formát XML") ho odlišuje od založený na textu protokolu SOAP kódování se nazývá prostý režim kódování XML kodér textu zprávy.  
  
 Další informace o kombinace prvky vazeb poskytovaných vazby poskytované systémem, najdete v části odpovídající v [volba přenosu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
## <a name="how-to-work-with-system-provided-encoders"></a>Jak pracovat s kodéry poskytované systémem  
 Kódování se přidá do vazbu pomocí třídy odvozené od <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
 Poskytuje následující typy odvozené z elementů vazby WCF <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> třídu, která může poskytnout pro text, binary a kódování zpráv přenosu optimalizace mechanismus (MTOM):  
  
-   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>: Interoperabilních nejvíce, ale alespoň efektivní kodéru zpráv XML. Webová služba nebo klient webové služby lze obecně pochopit textovou XML. Ale přenos velkých bloků binárních dat jako text není efektivní.  
  
-   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>: Představuje vazby elementu, který určuje kódování znaků a správa verzí používá pro zprávy XML, binární zprávy. Toto je nejúčinnější možnosti kódování, ale alespoň interoperabilní, protože je podporován pouze pomocí koncových bodů WCF.  
  
-   <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`>: představuje element vazby, který určuje kódování znaků a správa verzí zpráv použít pro zprávu pomocí kódování zpráv přenosu optimalizace mechanismus (MTOM). MTOM je technologie efektivní přenosu zpráv binární data v zpráv WCF. Kodér MTOM pokusí rovnováha mezi efektivitu a vzájemná funkční spolupráce. Kódování MTOM přenáší většina XML v textové podobě, ale optimalizuje velkých bloků binárních dat tím, že je jako přenosu-je, bez převodu na text.  
  
 Element vazby vytvoří binární, MTOM nebo text <xref:System.ServiceModel.Channels.MessageEncoderFactory>. Vytvoří objekt factory binární, MTOM nebo text <xref:System.ServiceModel.Channels.MessageEncoderFactory> instance. Obvykle je pouze jedna instance. Ale pokud relací se používají, může poskytovat různé kodér každé relaci. Binární kodér využívá tohoto ke koordinaci dynamické slovník (viz XML infrastruktury).  
  
 <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A> a <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A> metody jsou jádrem kodérů. Poskytují metody pro čtení zprávy z datového proudu nebo <xref:System.Byte> pole. Bajtová pole se používají při přenosu pracuje v režimu vyrovnávací paměti. Zprávy jsou vždy zapisovány do datových proudů. Pokud přenos musí vyrovnávací paměť zprávy, poskytuje datový proud, který nemá ukládání do vyrovnávací paměti.  
  
 Zbývající členy, pracovat s typy médií obsahu, podpora, a <xref:System.ServiceModel.Channels.MessageEncoder.MessageVersion%2A>. Přenos volá tyto metody kodér otestovat, zda lze příchozí zpráva dekódovat tímto nebo určit, zda je platná pro tento kodér odchozí zprávy.  
  
 Všechny tři implementace kodér přidá vlastnosti, které jsou relevantní pro konkrétní kódování a je plně konfigurovatelné. Kodéry také vystavit čtečky kvóty, které mají výchozí nastavení zabezpečení. V tématu XML infrastruktura diskuzi o kvóty.  
  
## <a name="features-of-system-provided-encoders"></a>Funkce poskytované systémem kodéry  
 Existuje několik funkcí poskytovaných kodéry poskytované systémem.  
  
### <a name="pooling"></a>Sdružování  
 Každý z implementace kodér pokusí fond co nejvíc. Omezení přidělení je klíče způsob, jak zlepšit výkon spravovaného kódu. K provedení této sdružování, implementace použít `SynchronizedPool` třídy. Soubor C# obsahuje popis Další optimalizace použitou touto třídou.  
  
 `XmlDictionaryReader` a `XmlDictionaryWriter` instance jsou ve fondu a znovu inicializován, aby se zabránilo přidělování nové pro každou zprávu. Pro čtečky `OnClose` zpětného volání získá čtečky při `Close()` je volána. Kodér recyklování také některé objekty stavu zpráv použitý při sestavování zprávy. Velikosti tyto fondy se dají konfigurovat pomocí `MaxReadPoolSize` a `MaxWritePoolSize` vlastnosti na všech tří třídy odvozené od <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
### <a name="binary-encoding"></a>Binární kódování  
 Když binární kódování relace používá dynamický slovník řetězec musí sdělit k příjemce zprávy. To se provádí pomocí prefixu zprávu s řetězci dynamický slovník. Příjemce odstraní vypnout řetězce, je přidá do relace a zprávu zpracuje. Správně předávání řetězce slovník vyžaduje, aby přenosu do vyrovnávací paměti.  
  
 Řetězce se připojují ke zprávě pomocí interní `AddSessionInformationToMessage` metoda. Přidá řetězce jako UTF-8 před předponu jejich délku zprávy. Hlavička celý slovníku je pak předponu délka jeho data. Operaci zpětné provádí interní `ExtractSessionInformationFromMessage` metoda.  
  
 Kromě zpracování dynamický slovník klíče, jsou přijaty ve vyrovnávací paměti relacemi zprávy jednoznačným způsobem. Místo vytváření čtečku přes dokument a její zpracování, binární kodér používá interní `MessagePatterns` třídy deconstruct binárního datového proudu. Cílem je, že většina zprávy mají sadu hlaviček, které se zobrazí v určitém pořadí při vygenerování službou WCF. Vzor systému dělí zprávu od sebe založenou na se očekává. Pokud je úspěšné, inicializuje <xref:System.ServiceModel.Channels.MessageHeaders> objektu bez analýza kódu XML. Pokud ne, spadne zpět na standardní metoda.  
  
### <a name="mtom-encoding"></a>Kódování MTOM  
 <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`> Třída má další konfiguraci vlastnost s názvem <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`. MaxBufferSize % 2A >. Horní mez to umístí na kolik dat je povoleno vyrovnávací paměti při čtení zprávy. XML informace sady (informační sadu), nebo dalšími částmi MIME chtít do vyrovnávací paměti sestavit všechny části standardu MIME do jedné zprávy.  
  
 Fungovat správně s protokolem HTTP, interní třída kodér zpráv MTOM poskytuje některé interní rozhraní API pro `GetContentType` (což je také vnitřní) a `WriteMessage`, který je veřejný a je možné přepsat. Další komunikace, musí dojít k zajištění, že hodnoty v hlavičkách protokolu HTTP souhlas s hodnotami v hlavičkách MIME.  
  
 Kodér zpráv MTOM interně používá čtečky textu na WCF a je podobná kodér textu. Hlavní rozdíl je, že optimalizuje velké skupiny binární, nebo "Binární rozsáhlé objekty" (BLOB), není převede na kódování Base-64 před jeho vkládání do bajtů zpráv. Místo toho tyto objekty BLOB jsou uchovány extrahované a odkazované jako přílohy MIME.  
  
## <a name="writing-your-own-encoder"></a>Zápis vlastní kodér  
 Chcete-li implementovat vlastní vlastní kodér zpráv, je nutné zadat vlastní implementace následující abstraktní základní třídy:  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder>  
  
-   <xref:System.ServiceModel.Channels.MessageEncoderFactory>  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
  
 Převod z reprezentací v paměti zprávu k reprezentaci, s možností zápisu do datového proudu je zapouzdřený <xref:System.ServiceModel.Channels.MessageEncoder> třídy, která slouží jako objekt pro vytváření pro čtečky XML a zapisovače XML, které podporují konkrétní typy XML kódování.  
  
-   Klíče metody této třídy, které je nutné přepsat jsou následující:  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A> které trvá <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> objektu a zapíše ho do <xref:System.IO.Stream> objektu.  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A> které trvá <xref:System.IO.Stream> objekt a velikost maximální záhlaví a vrátí <xref:System.ServiceModel.Channels.Message> objektu.  
  
 Je kód napsaný v těchto metod, který zpracovává převod mezi standardní přenosový protokol a vlastní kódování.  
  
 Dále je třeba kód třídu objektů factory, který vytváří vlastní kodér. Přepsání <xref:System.ServiceModel.Channels.MessageEncoderFactory.Encoder%2A> vrátit instanci vaše vlastní <xref:System.ServiceModel.Channels.MessageEncoder>.  
  
 Připojte se vaše vlastní <xref:System.ServiceModel.Channels.MessageEncoderFactory> slouží ke konfiguraci služby nebo klienta přepsáním zásobníku element vazby <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> metoda vrátit instanci tohoto objektu pro vytváření.  
  
 Jsou k dispozici dva vzorky zadat s použitím technologie WCF, které ilustrují tento proces se ukázkový kód: [vlastní kodér zpráv: vlastní kodér textu](../../../../docs/framework/wcf/samples/custom-message-encoder-custom-text-encoder.md) a [vlastní kodér zpráv: kompresní kodér](../../../../docs/framework/wcf/samples/custom-message-encoder-compression-encoder.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.MessageEncoderFactory>  
 <xref:System.ServiceModel.Channels.MessageEncoder>  
 [Strukturální přehled přenosu dat](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 [Výběr kodéru zprávy](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [Volba přenosu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
