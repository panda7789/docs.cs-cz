---
title: Vlastní kodéry
ms.date: 03/30/2017
ms.assetid: fa0e1d7f-af36-4bf4-aac9-cd4eab95bc4f
ms.openlocfilehash: 586207af0bfbe106512dfb61ee7439d4f5ce64c6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797215"
---
# <a name="custom-encoders"></a>Vlastní kodéry
Toto téma popisuje, jak vytvořit vlastní kodéry.  
  
 V Windows Communication Foundation (WCF) použijete *vazbu* k určení způsobu přenosu dat mezi koncovými body v síti. Vazba je tvořena sekvencí *prvků vazby*. Vazba obsahuje volitelné prvky vazby protokolu, jako je například zabezpečení, požadovaný element vazby *kodéru zprávy* a požadovaný prvek vazby přenosu. Kodér zprávy je reprezentován prvkem vazby kódování zprávy. WCF obsahuje tři kodéry zpráv: Binární, mechanizmus pro optimalizaci přenosu zpráv (MTOM) a text.  
  
 Element vazby kódování zprávy serializaci odchozí <xref:System.ServiceModel.Channels.Message> a předává do přenosu, nebo přijímá serializovanou formu zprávy z přenosu a předává ji do vrstvy protokolu, pokud je k dispozici, nebo do aplikace, pokud není k dispozici.  
  
 Kodéry zpráv transformují <xref:System.ServiceModel.Channels.Message> instance do a z reprezentace v rámci vedení. I když jsou kodéry popsány tak, aby se nacházely nad přenosovou vrstvou v zásobníku kanálů, jsou umístěny uvnitř přenosové vrstvy. Přenos (například HTTP) formátuje zprávu podle požadavků standardu transportu. Kodéry (například text XML) právě zakódují zprávu.  
  
 Pokud se připojujete k již existujícímu klientovi nebo serveru, možná nebudete mít možnost používat konkrétní kódování zprávy. Služby WCF však lze zpřístupnit prostřednictvím více koncových bodů, z nichž každý má jiný kodér zpráv. Pokud jeden kodér nepokrývá celou cílovou skupinu pro vaši službu, zvažte zveřejnění služby přes více koncových bodů. Klientské aplikace potom můžou zvolit koncový bod, který je pro ně nejvhodnější. Použití více koncových bodů umožňuje kombinovat výhody různých kodérů zpráv s dalšími prvky vazby.  
  
## <a name="system-provided-encoders"></a>Kodéry poskytované systémem  
 WCF poskytuje několik vazeb poskytovaných systémem, které jsou navržené tak, aby pokrývaly nejběžnější scénáře použití aplikací. Každá z těchto vazeb kombinuje přenos, kodér zpráv a další možnosti (například zabezpečení). Toto téma popisuje, jak můžete roztáhnout `Text`kodéry `MTOM` , `Binary`, a zprávy, které jsou součástí WCF, nebo vytvořit vlastní kodér. Kodér textu zprávy podporuje jak kódování ve formátu XML, tak i kódování SOAP. Režim prostého kódování XML kodéru textové zprávy se nazývá kodér POX ("obyčejný starý soubor XML"), který ho odlišuje od textového kódování SOAP založeného na textu.  
  
 Další informace o kombinací prvků vazby poskytovaných pomocí vazeb poskytovaných systémem naleznete v odpovídající části [výběru přenosu](../feature-details/choosing-a-transport.md).  
  
## <a name="how-to-work-with-system-provided-encoders"></a>Jak pracovat s kodéry poskytnutými systémem  
 Do vazby se přidá kódování pomocí třídy odvozené z <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
 WCF poskytuje následující typy prvků vazby, které jsou odvozeny <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> ze třídy, která může poskytnout pro text, binární a kódování v mechanismu optimalizace přenosu zpráv (MTOM):  
  
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>: Nejvíce interoperabilní, ale nejméně efektivní kodér pro zprávy XML. Webová služba nebo klient webové služby může obecně pochopit text XML. Nicméně přenos velkých bloků binárních dat jako textu není efektivní.  
  
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>: Představuje prvek vazby, který určuje kódování znaků a verze zprávy používané pro binární zprávy XML. To je nejúčinnější z možností kódování, ale nejméně interoperabilní, protože jsou podporovány pouze koncovými body WCF.  
  
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>: Představuje prvek vazby, který určuje kódování znaků a správu verzí zpráv používané pro zprávu pomocí kódování MTOM (Message reoptimizationing mechanism). MTOM je efektivní technologie pro přenos binárních dat ve zprávách WCF. Kodér MTOM se pokusí vyvážit efektivitu a spolupráci. Kódování MTOM přenáší většinu XML v textové podobě, ale optimalizuje velké bloky binárních dat jejich přenosem tak, jak jsou, bez konverze na text.  
  
 Element Binding vytvoří binární, MTOM nebo text <xref:System.ServiceModel.Channels.MessageEncoderFactory>. Objekt pro vytváření vytvoří binární, MTOM nebo textovou <xref:System.ServiceModel.Channels.MessageEncoderFactory> instanci. Obvykle je k dispozici pouze jedna instance. Pokud se ale používají relace, může se každé relaci zadat jiný kodér. Binární kodér využívá tuto technologii ke koordinaci dynamických slovníků (viz infrastruktura XML).  
  
 Metody <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A> a<xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A> jsou jádrem kodéru. Metody poskytují pro čtení zprávy z datového proudu nebo z <xref:System.Byte> pole. Pole bajtů se používají, když přenos pracuje v režimu vyrovnávací paměti. Zprávy jsou vždy zapisovány do datových proudů. Pokud přenos musí zprávu ukládat do vyrovnávací paměti, poskytne datový proud, který ukládá do vyrovnávací paměti.  
  
 Zbytek členů pracuje s obsahem podpory, typy médií a <xref:System.ServiceModel.Channels.MessageEncoder.MessageVersion%2A>. Přenos volá tyto metody kodéru k otestování, zda je možné příchozí zprávu dekódovat, nebo zda je odchozí zpráva platná pro tento kodér.  
  
 Každé ze tří implementací kodéru přidá vlastnosti, které jsou relevantní pro konkrétní kódování, a je plně konfigurovatelné. Kodéry také zveřejňují kvóty čtecího zařízení, které mají zabezpečené výchozí hodnoty. Diskuzi o kvótách najdete v tématu Infrastruktura XML.  
  
## <a name="features-of-system-provided-encoders"></a>Funkce kodérů poskytovaných systémem  
 Kodéry poskytované systémem obsahují řadu funkcí.  
  
### <a name="pooling"></a>Sdružování  
 Každé z těchto implementací kodéru se pokusí co nejvíce vyřadit z fondu. Snížení počtu přidělení je klíčovým způsobem, jak vylepšit výkon spravovaného kódu. Pro dosažení tohoto sdružování implementují implementace `SynchronizedPool` třídu. C# Soubor obsahuje popis dalších optimalizace používaných touto třídou.  
  
 <xref:System.Xml.XmlDictionaryReader>a <xref:System.Xml.XmlDictionaryWriter> instance jsou sdružené a znovu inicializované, aby nedocházelo k přidělování nových zpráv pro každou zprávu. Pro čtenáře, `OnClose` zpětné volání Redeklarace čtenáře při `Close()` volání metody. Kodér také recykluje některé objekty stavu zprávy používané při sestavování zpráv. Velikosti těchto fondů lze konfigurovat pomocí `MaxReadPoolSize` vlastností a `MaxWritePoolSize` na každé ze tří tříd odvozených z <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
### <a name="binary-encoding"></a>Binární kódování  
 Když binární kódování používá relace, řetězec dynamického slovníku musí být sdělen příjemci zprávy. K tomu slouží předpona zprávy s dynamickými řetězci slovníku. Přijímač odliští řetězce, přidá je do relace a zpracuje zprávu. Správné předání řetězců slovníku vyžaduje, aby transport byl uložen do vyrovnávací paměti.  
  
 Řetězce jsou připojeny k zprávě pomocí interní `AddSessionInformationToMessage` metody. Přidá řetězce jako UTF-8 do přední části zprávy s předponou. Celá hlavička slovníku je pak předpona s délkou jejich dat. Reverzní operace provádí interní `ExtractSessionInformationFromMessage` metodu.  
  
 Kromě zpracování dynamických klíčů slovníku se zprávy relací s vyrovnávací pamětí přijímají jedinečným způsobem. Místo vytvoření čtecího modulu v dokumentu a jeho zpracování použije binární kodér interní `MessagePatterns` třídu k dekonstrukci binárního datového proudu. Výsledkem je, že většina zpráv má určitou sadu hlaviček, která se zobrazí v určitém pořadí při generování službou WCF. Systém vzorků rozdělí zprávy na základě toho, co očekává. Pokud je úspěšná, inicializuje <xref:System.ServiceModel.Channels.MessageHeaders> objekt bez analýzy XML. V takovém případě se vrátí zpět ke standardní metodě.  
  
### <a name="mtom-encoding"></a>Kódování MTOM  
 Třída má další vlastnost konfigurace s názvem <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement.MaxBufferSize%2A>. <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> Tím se umístí horní mez rozsahu dat, ke kterým může během procesu čtení zprávy docházet vyrovnávací paměť. Aby bylo možné překompilovat všechny části MIME do jediné zprávy, může být nutné ukládat do vyrovnávací paměti sadu informací XML (informační sada) nebo jiné části MIME.  
  
 Pro správnou práci s protokolem HTTP, interní třída kodéru zpráv MTOM poskytuje některá interní `GetContentType` rozhraní API pro (která jsou také `WriteMessage`interní) a, která je veřejná a může být přepsána. K zajištění toho, aby hodnoty hlaviček protokolu HTTP souhlasily s hodnotami v hlavičkách MIME, musí být k větší komunikace.  
  
 Kodér zprávy MTOM interně používá čtečky textu WCF a je podobný textu kodéru. Hlavním rozdílem je to, že optimalizuje velké bloky binárních souborů nebo "binárních velkých objektů" (blobů), protože je před vložením do bajtů zpráv nepřevádí na kódování Base-64. Místo toho se tyto objekty blob uchovávají a odkazují jako přílohy MIME.  
  
## <a name="writing-your-own-encoder"></a>Psaní vlastního kodéru  
 Chcete-li implementovat vlastní kodér zpráv, je nutné poskytnout vlastní implementace následujících abstraktních základních tříd:  
  
- <xref:System.ServiceModel.Channels.MessageEncoder>  
  
- <xref:System.ServiceModel.Channels.MessageEncoderFactory>  
  
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
  
 Převod z reprezentace zprávy v paměti na reprezentaci, která může být zapsána do datového proudu, je zapouzdřen v rámci <xref:System.ServiceModel.Channels.MessageEncoder> třídy, která slouží jako továrna pro čtečky XML a zapisovače XML, které podporují konkrétní typy kódování XML.  
  
- Klíčové metody této třídy, které je nutné přepsat, jsou:  
  
- <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A>který přebírá <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> objekt a zapisuje ho <xref:System.IO.Stream> do objektu.  
  
- <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A>který přebírá <xref:System.IO.Stream> objekt a maximální velikost hlavičky a <xref:System.ServiceModel.Channels.Message> vrací objekt.  
  
 Jedná se o kód, který zapisujete do těchto metod, který zpracovává převod mezi standardním transportním protokolem a vlastním kódováním.  
  
 Dále je nutné vytvořit kód třídy továrny, která vytvoří vlastní kodér. Přepište <xref:System.ServiceModel.Channels.MessageEncoder>a vraťte instanci svého vlastního. <xref:System.ServiceModel.Channels.MessageEncoderFactory.Encoder%2A>  
  
 Pak připojte vlastní <xref:System.ServiceModel.Channels.MessageEncoderFactory> ke zásobníku prvků vazby, který se používá ke konfiguraci služby nebo klienta, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> přepsáním metody, která vrátí instanci tohoto objektu pro vytváření.  
  
 Pro WCF jsou k dispozici dvě ukázky, které ilustrují tento proces s ukázkovým kódem: [Vlastní kodér zpráv: Vlastní kodér](../samples/custom-message-encoder-custom-text-encoder.md) textu a [vlastní kodér zpráv: Kompresní kodér](../samples/custom-message-encoder-compression-encoder.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MessageEncoderFactory>
- <xref:System.ServiceModel.Channels.MessageEncoder>
- [Strukturální přehled přenosu dat](../feature-details/data-transfer-architectural-overview.md)
- [Výběr kodéru zprávy](../feature-details/choosing-a-message-encoder.md)
- [Volba přenosu](../feature-details/choosing-a-transport.md)
