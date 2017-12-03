---
title: "Výběr kodéru zprávy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2204d82d-d962-4922-a79e-c9a231604f19
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 743e8cdf1a10efb7b99d6c6dcfcff611df6fbf4e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="choosing-a-message-encoder"></a>Výběr kodéru zprávy
Toto téma popisuje kritéria pro výběr mezi kodéry zprávy, které jsou součástí [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]: binární, text a zpráva přenosu optimalizace mechanismus (MTOM).  
  
 V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], můžete určit, jak k přenosu dat v síti mezi koncovými body prostřednictvím *vazby*, který se skládá z posloupnost *elementů vazby*. Kodér zpráv je reprezentována prvku vazby v zásobníku vazby kódování zprávy. Vazba obsahuje prvky vazby volitelné protokolu, například element vazby a zabezpečení nebo spolehlivého zasílání zpráv prvku vazby, zprávu vyžaduje kódování prvku vazby a element vazby požadované přenosu.  
  
 Element vazby kódování zprávy je umístěna nad prvku vyžaduje přenos vazby a prvky vazeb volitelné protokolu. Na straně pro odchozí kodéru zprávy serializuje odchozích <xref:System.ServiceModel.Channels.Message> a předává je pro přenos. Na straně pro příchozí kodéru zprávy přijme serializovaný formu <xref:System.ServiceModel.Channels.Message> z přenosu a předává jej do protokolu vyšší vrstvy, pokud existuje, nebo aplikaci, pokud není.  
  
 Při připojení k existující klient nebo server, nemusí mít volba o pomocí kódování konkrétní zprávu vzhledem k tomu, že budete muset kódování zpráv způsobem, který je očekáván druhé straně. Ale pokud píšete [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] službu, můžete vystavit služby prostřednictvím několik koncových bodů, každý pomocí jiná zpráva kódování. To umožňuje klientům vybrat nejvhodnější kódování pro rozhovoru k službě přes koncový bod, který je nejvhodnější pro ně, jakož i poskytnutí vašim klientům flexibilitu zvolit si, že kódování, které je nejvhodnější pro ně. Pomocí několik koncových bodů také můžete kombinovat s jinými prvky vazby výhod jiná zpráva kódování.  
  
## <a name="system-provided-encoders"></a>Kodéry poskytované systémem  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zahrnuje tři kodéry zprávy, které jsou reprezentované pomocí následujících tří tříd:  
  
-   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>, kodér textu zprávy, podporuje prostý kódování XML i kódování SOAP. Nešifrovaná režim kódování XML kodér textu zprávy se nazývá "prostý formát XML" (POX) ho odlišuje od založený na textu protokolu SOAP kódování. Chcete-li povolit POX, nastavte <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement.MessageVersion%2A> vlastnost <xref:System.ServiceModel.Channels.MessageVersion.None%2A>. Použít kodér textu zprávy pro spolupráci s jinou hodnotu než[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncové body.  
  
-   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>, kodéru zprávy v binární používá kompaktní binární formát a je optimalizovaný pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] k [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] komunikaci a proto není umožňuje vzájemnou spolupráci. Toto je také nejvíce původce kodér všechny kodéry [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje.  
  
-   <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement -->`System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`> prvku vazby Určuje kódování znaků, a správa verzí zpráva pro zprávy pomocí kódování MTOM. MTOM je technologie efektivní přenosu zpráv binární data v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zprávy. Kodér MTOM se pokusí vytvořit rovnováhu mezi efektivitu a vzájemná funkční spolupráce. Kódování MTOM přenáší většina XML v textové podobě, ale optimalizuje velkých bloků binárních dat tím, že je jako přenosu-je, bez převodu na text. Z hlediska efektivitu mezi kodéry [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje, MTOM je mezi text (nejpomalejší) a binární (nejrychlejší).  
  
## <a name="how-to-choose-a-message-encoder"></a>Jak vybrat kodéru zprávy  
 Následující tabulka popisuje běžných faktorů použitá pro výběr kodéru zprávy. Určení priority faktorů, které jsou důležité pro vaši aplikaci a potom vyberte kodéry zpráva které pracují nejlépe s tyto faktory. Je nutné zvážit všechny dalších faktorů, které nejsou uvedené v této tabulce a jakékoli vlastní zprávu kodéry, které mohou být vyžadovány ve vaší aplikaci.  
  
|Koeficient|Popis|Kódovací moduly, které podporují tento faktor|  
|------------|-----------------|---------------------------------------|  
|Podporované znakové sady|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>a <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`> podporují pouze UTF8 a UTF16 Unicode (*big endian* a *little endian*) kódování. Je-li další kódování je vyžadovat, například UTF7 nebo ASCII, je nutné použít vlastní kodér. Vlastní kodér ukázkové, najdete v části [vlastní kodér zpráv](http://go.microsoft.com/fwlink/?LinkId=119857).|Text|  
|Kontroly|Kontroly je schopnost zkontrolujte zprávy během přenosu. Kódování textu, ať už s nebo bez použití protokolu SOAP, povolí zpráv, které mají být zkontrolovány a analyzovat mnoho aplikací bez použití specializované nástroje. Všimněte si, že ovlivňuje použití přenosu zabezpečení na úrovni zprávy nebo přenosu, budete moci prohlédnout zprávy. Důvěrnost chrání zprávu z se zkontrolován a integrity chrání zprávu nebylo možné měnit.|Text|  
|Spolehlivost|Spolehlivost je odolnost kodér přenosu chyb. Spolehlivost se dá zadat i na zprávu, přenos nebo aplikační vrstvu. Všechny standardní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kodéry předpokládá, že poskytuje další úroveň spolehlivosti. Kodér má moc moci provést zotavení po chybě přenosu.|Žádné|  
|Jednoduchost|Jednoduchost představuje snadnou, pomocí kterého můžete vytvořit kodérů a dekodérů pro specifikace kódování. Kódování textu je zvláště výhodné pro jednoduchost a kódování textu POX má Další výhodou není vyžadující podporu pro zpracování protokolu SOAP.|Text (POX)|  
|Velikost|Kódování určuje objem režie vynucená pro obsah. Velikost kódovaného zprávy přímo souvisí s maximální propustnost operací služby. Binární kódování je obecně kompaktnější než kódování textu. Pokud je velikost zprávy na prémiový, zvažte také komprese obsah zprávy během kódování. Komprese však přidá zpracování náklady pro odesílatele zprávy a příjemce.|binární|  
|streamování|Streamování umožňuje aplikacím začala zpracovat zprávu, než dorazila celé zprávy. Efektivně pomocí vysílání datového proudu vyžaduje, aby důležitá data zprávy k dispozici na začátku zprávy tak, aby přijímající aplikace není potřeba počkat na jeho doručení. Kromě toho aplikace, které používají přenos přenášené datovými proudy musí uspořádání dat ve zprávě postupně tak, aby obsah nemá dopředného závislosti. V mnoha případech musí ohrožení mezi streamování obsahu a nutnosti nejmenší možný přenos pro tento obsah.|Žádné|  
|3. stran nástroj podpory|Patří sem podporu pro kódování vývoj a diagnostiku. Vývojáři třetích stran provedli velké investice v sadách pro zpracování zprávy ve formátu POX a knihovny.|Text (POX)|  
|Interoperabilita|Tento faktor odkazuje na schopnost [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kodéru pro spolupráci s jinou hodnotu než[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.|Text<br /><br /> MTOM (částečné)|  
  
Poznámka: Pokud používáte binární kodéru, pomocí nastavení IgnoreWhitespace při vytváření XMLReader nebude mít žádný vliv.  Například, pokud proveďte následující operace služby:  

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
  
IgnoreWhitespace nastavení se ignoruje.  
  
## <a name="compression-and-the-binary-encoder"></a>Komprese a binární kodér

Od verze WCF 4.5 binární kodér WCF přidává podporu pro kompresi. To vám umožní použít algoritmus gzip nebo deflate pro odesílání zpráv komprimované z klienta WCF a také odpovědět s komprimované zpráv ze služby WCF s vlastním hostováním. Tato funkce umožňuje kompresi na přenosy HTTP a TCP. Hostované IIS WCF služby se dá vždy povolit pro odeslání komprimované odpovědi nakonfigurováním hostitelský server služby IIS. Typ komprese nastavena <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A?displayProperty=nameWithType> vlastnost. Tato vlastnost nastavena na jednu z <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType> hodnoty výčtu:

* `CompressionFormat.Deflate`
* `CompressionFormat.GZip`
* `CompressionFormat.None`
  
Vzhledem k tomu, že tato vlastnost je k dispozici pouze ve třídě binaryMessageEncodingBindingElement, bude muset vytvořit vlastní vazby takto k použití této funkce:

 ```xml
 <customBinding>
   <binding name="BinaryCompressionBinding">
     <binaryMessageEncoding compressionFormat ="GZip" />
     <httpTransport />
  </binding>
</customBinding>
 ```

Klient a služba musí souhlasit s odesílat a přijímat zprávy komprimované a proto musí být vlastnost compressionFormat nakonfigurované na elementu binaryMessageEncoding na klienta a služby. Protocolexception – je vyvolána, pokud se služba nebo klienta není nakonfigurován pro kompresi, ale je druhé straně. Povolení komprese je třeba pečlivě zvážit. Komprese je ve většině případů užitečné, pokud je kritický bod šířka pásma sítě. V případě, kdy procesor problémové místo se sníží komprese propustnost. Odpovídající testování je třeba provést v simulovaném prostředí a zjistěte, pokud to výhody aplikace  
  
## <a name="see-also"></a>Viz také

[Vazby](../../../../docs/framework/wcf/feature-details/bindings.md)
