---
title: Výběr kodéru zprávy
ms.date: 03/30/2017
ms.assetid: 2204d82d-d962-4922-a79e-c9a231604f19
ms.openlocfilehash: 0c960505d6c8368396cddebe37c76c8d95550727
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409481"
---
# <a name="choosing-a-message-encoder"></a>Výběr kodéru zprávy
Toto téma popisuje kritéria pro výběr mezi kodérů zprávy, které jsou zahrnuté ve Windows Communication Foundation (WCF): binární soubor, text a zpráv přenosu optimalizace mechanismus (MTOM).  
  
 Ve službě WCF, můžete určit, jak přenášet data přes síť mezi koncovými body prostřednictvím *vazby*, který se skládá z posloupnosti *elementů vazby*. Kodér zprávy je reprezentován element vazby v zásobníku vazby kódování zprávy. Vazba obsahuje elementy vazby volitelné protokolu, jako je například element vazby zabezpečení nebo spolehlivé zasílání zpráv element vazby, vyžaduje zpráva kódování element vazby a element vazby přenosu vyžaduje.  
  
 Element vazby kódování zprávy nachází nad element vazby přenosu požadované a volitelné protokol elementů vazby. Na straně odchozí serializuje kodéru zprávy odchozí <xref:System.ServiceModel.Channels.Message> a předá ji do přenosu. Na straně příchozí kodéru zprávy obdrží serializovanou formu <xref:System.ServiceModel.Channels.Message> z přenosu a předá ji do protokolu vyšší vrstvy, pokud jsou k dispozici, nebo do aplikace, pokud tomu tak není.  
  
 Při připojování k existující klient nebo server, nemusí mít možnost o pomocí kódování konkrétní zprávu od zakódování zprávy tak, aby na straně očekává. Ale při psaní služby WCF, můžete zveřejnit služby prostřednictvím více koncových bodů, každý pomocí kódování s jinou zprávu. To umožňuje klientům zvolte nejvhodnější kódování pro mluvit k vaší službě přes koncový bod, který je pro ně nejvhodnější, také poskytuje flexibilitu zvolit si kódování, které je nejvhodnější pro ně vašim klientům. Použití více koncových bodů také umožňuje kombinovat výhody různých zpráv kodovaných s jinými prvky vazby.  
  
## <a name="system-provided-encoders"></a>Poskytnuté systémem kodérů  
 WCF obsahuje tři kodérů zprávy, které jsou znázorněny následující tři třídy:  
  
-   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>, kodér textu zprávy, podporuje prostý XML encoding i kódování SOAP. Standardní režim kódování XML kodér textu zprávy se nazývá "plain old XML" (POX), aby se odlišil od založený na textu kódování SOAP. Chcete-li povolit POX, nastavte <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement.MessageVersion%2A> vlastnost <xref:System.ServiceModel.Channels.MessageVersion.None%2A>. Kodér textu zprávy použijte pro spolupráci s koncovými body mimo WCF.  
  
-   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>, kodér binárních zpráv používá kompaktní binární formát a je optimalizována pro WCF pro komunikaci WCF a proto není interoperabilní. Toto je většina kodér výkonné všechny kodérů, které poskytuje WCF.  
  
-   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>, určuje element vazby na znak kódování a správu verzí zpráv pro zprávy pomocí kódování MTOM. MTOM je efektivní technologie pro přenos zpráv WCF binární data. Kodér MTOM se pokusí vytvořit rovnováhu mezi efektivitu a vzájemná funkční spolupráce. Kódování MTOM přenáší většina XML v textové formě, ale optimalizuje velkých bloků binárních dat jako ušetřený přenosem-je, bez převodu na text. Z hlediska efektivity mezi kodéry, které poskytuje WCF MTOM je mezi (nejpomalejší) textového a binárního souboru (nejrychlejší).  
  
## <a name="how-to-choose-a-message-encoder"></a>Výběr kodéru zprávy  
 Následující tabulka popisuje běžné faktory použitá pro výběr kodéru zprávy. Prioritizujte tyto faktory, které jsou důležité pro vaši aplikaci a klikněte na tlačítko kodérů zprávy, které pracují nejlépe faktorů. Ujistěte se, že vezměte v úvahu žádné další faktory, které nejsou uvedené v této tabulce a jakékoli vlastní zprávu kodéry, které může být nutné ve vaší aplikaci.  
  
|faktor|Popis|Kodéry, které podporují tento faktor|  
|------------|-----------------|---------------------------------------|  
|Podporované znakové sady|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> a <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> podporují pouze UTF8 a UTF16 Unicode (*formát big-endian* a *little endian*) kódování. Pokud jiné kódování, jako je například UTF7 nebo ASCII, musíte použít vlastní kodér. Vlastní kodér vzorku, naleznete v tématu [vlastní kodér zpráv](https://go.microsoft.com/fwlink/?LinkId=119857).|Text|  
|Kontrola|Kontrola je možnost k prozkoumání zpráv během přenosu. Kódování textu, s nebo bez použití protokolu SOAP, povolit zpráv ho zkontrolovat a analyzovat řada aplikací bez použití specializované nástroje. Všimněte si, že použití zabezpečení přenosu na úrovni zprávy nebo přenosu, ovlivňuje vaše schopnost kontrolovat zprávy. Důvěrnost zkoumají chrání zprávu a chrání integritu zprávu nebylo možné měnit.|Text|  
|Spolehlivost|Spolehlivost je odolnost proti chybám kodéru pro předávání chyb. Spolehlivost se dá zadat i zpráva, přenos nebo aplikační vrstvy. Všechny standardní kodérů WCF se předpokládá, že poskytuje další vrstvu spolehlivost. Kodér má málo moci provést zotavení po chybě přenosu.|Žádné|  
|Zjednodušení|Zjednodušení představuje snadné, pomocí kterého můžete vytvořit kodérů a dekodérů pro specifikaci kódování. Kódování textu výhodným pro zjednodušení a kódování textu POX má další výhodu v podobě není vyžadující podporu pro zpracování protokolu SOAP.|Text (POX)|  
|Velikost|Určuje množství režie na obsah, kódování. Velikost kódovaného zprávy přímo souvisí s maximální propustností operací služby. Binární kódování jsou obecně kompaktnějším než kódování textu. Když velikost zprávy v na úrovni premium, vezměte v úvahu také komprese obsah zprávy při kódování. Komprese však přidá náklady na zpracování pro příjemce i odesílatele zprávy.|binární|  
|Streamování|Streamování umožňuje aplikacím, aby začala zpracovat zprávu, před celá zpráva dorazila. Efektivně pomocí vysílání datového proudu vyžaduje, aby důležitá data zprávy k dispozici na na začátek zprávy tak, aby se přijímající aplikací není potřeba počkat na jeho doručení. Kromě toho aplikace, které používají přenos datovým proudem uspořádat data ve zprávě postupně tak, aby obsah nemá žádné závislosti. V mnoha případech se musí najít kompromis mezi streamování obsahu a s nejmenší možný přenos pro daný obsah.|Žádné|  
|3. stran podporováno|Oblasti podpory pro kódování zahrnují vývoje a diagnostiku. Vývojáři třetích stran v knihovnách a sady nástrojů pro zpracování zpráv zakódován do formátu POX provedli velkých investic.|Text (POX)|  
|Interoperabilita|Tento faktor odkazuje na možnost kodér WCF na vzájemnou spolupráci se službami jiných WCF.|Text<br /><br /> MTOM (částečná podpora)|  
  
Poznámka: Při používání binárního kodéru, pomocí nastavení IgnoreWhitespace při vytváření XMLReader nebude mít žádný efekt.  Například pokud provedete následující operace služby:  

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
  
Nastavení IgnoreWhitespace se ignoruje.  
  
## <a name="compression-and-the-binary-encoder"></a>Komprese při přenosu a binárního kodéru

Od verze WCF 4.5 binárního kodéru WCF přidává podporu pro kompresi. To vám umožní použít algoritmus metodou gzip nebo deflate pro odesílání komprimované zprávy z klienta WCF a také reagovat komprimované zprávy ze služby WCF v místním prostředí. Tato funkce umožňuje kompresi na přenosy HTTP i protokol TCP. Hostované IIS WCF služby vždy se dá nastavit pro odeslání komprimované odpovědi tím, že nakonfigurujete hostitele serveru služby IIS. Typ komprese, která má nakonfigurovanou <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A?displayProperty=nameWithType> vlastnost. Tato vlastnost nastavena na jednu z <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType> hodnot výčtu:

- <xref:System.ServiceModel.Channels.CompressionFormat.Deflate>
- <xref:System.ServiceModel.Channels.CompressionFormat.GZip>
- <xref:System.ServiceModel.Channels.CompressionFormat.None>
  
Protože tato vlastnost je dostupná jenom v případě ve třídě binaryMessageEncodingBindingElement, budete potřebovat k vytvoření vlastní vazby pro použití této funkce takto:

 ```xml
 <customBinding>
   <binding name="BinaryCompressionBinding">
     <binaryMessageEncoding compressionFormat ="GZip" />
     <httpTransport />
  </binding>
</customBinding>
 ```

Klient a služba musí shodnout odesílat a přijímat zprávy komprimované a proto musí být vlastnost Formát compressionFormat nakonfigurovaná na element binaryMessageEncoding na klienta a služby. Výjimka ProtocolException je vyvolána, pokud služba nebo klient není nakonfigurován pro kompresi, ale je druhé straně. Povolení komprese je třeba pečlivě zvážit. Komprese je ve většině případů užitečné, pokud je šířka pásma sítě kritickým bodem. V případě, kdy procesor problémové místo komprese se sníží propustnosti. Příslušné testy je třeba provést v prostředí s Simulovaná a zjistěte, pokud to je výhodné aplikace  
  
## <a name="see-also"></a>Viz také:

- [Vazby](../../../../docs/framework/wcf/feature-details/bindings.md)
