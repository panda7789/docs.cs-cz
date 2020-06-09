---
title: Výběr kodéru zprávy
ms.date: 03/30/2017
ms.assetid: 2204d82d-d962-4922-a79e-c9a231604f19
ms.openlocfilehash: dbc5981013fe5e023f1d6d9eaf64b2e1fa18e2df
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587336"
---
# <a name="choose-a-message-encoder"></a>Výběr kodéru zprávy

Tento článek popisuje kritéria pro výběr mezi kodéry zpráv, které jsou součástí Windows Communication Foundation (WCF): binární, text a mechanismus optimalizace přenosu zpráv (MTOM).  
  
 V rámci služby WCF určíte, jak přenést data mezi koncovými body pomocí *vazby*, která je tvořena sekvencí *prvků vazby*. Kodér zprávy je reprezentován prvkem vazby kódování zprávy v zásobníku vazby. Vazba obsahuje volitelné prvky vazby protokolu, jako je například prvek vazby zabezpečení nebo prvek spolehlivého zasílání zpráv, požadovaný element vazby kódování a požadovaný element vazby přenosu.  
  
 Element vazby kódování zprávy se nachází pod volitelnými prvky vazby protokolu a nad požadovaným prvkem vazby přenosu. Na straně odchozího přenosu kodér zprávy serializaci odchozí <xref:System.ServiceModel.Channels.Message> a předává do přenosu. Na straně příchozího přenosu kodér zprávy přijímá serializovanou formu <xref:System.ServiceModel.Channels.Message> z přenosů a předává je do vrstvy s vyšším protokolem, pokud je k dispozici, nebo do aplikace, pokud ne.  
  
 Pokud se připojujete k již existujícímu klientovi nebo serveru, možná nebudete mít možnost používat konkrétní kódování zpráv, protože je potřeba zakódovat zprávy způsobem, který očekává druhá strana. Pokud však píšete službu WCF, můžete službu zveřejnit prostřednictvím více koncových bodů, z nichž každá používá jiné kódování zpráv. To umožňuje klientům zvolit nejlepší kódování pro komunikaci s vaší službou prostřednictvím koncového bodu, který je pro ně nejvhodnější, a poskytnout tak vašim klientům flexibilitu pro výběr kódování, které je pro ně nejvhodnější. Použití více koncových bodů také umožňuje kombinovat výhody různých kódování zpráv s jinými prvky vazby.  
  
## <a name="system-provided-encoders"></a>Kodéry poskytované systémem  
 Služba WCF zahrnuje tři kodéry zpráv, které jsou reprezentovány následujícími třemi třídami:  
  
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>, kodér textové zprávy, podporuje kódování v obyčejném jazyce XML i kódování protokolu SOAP. Režim prostého kódování XML kodéru textové zprávy se nazývá "" obyčejný Star XML "(POX), který rozlišuje od textu založeného na kódování SOAP. Chcete-li povolit POX, nastavte <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement.MessageVersion%2A> vlastnost na hodnotu <xref:System.ServiceModel.Channels.MessageVersion.None%2A> . Pomocí kodéru textové zprávy můžete spolupracovat s koncovými body, které nejsou typu WCF.  
  
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>, binární kodér zpráv, používá kompaktní binární formát a je optimalizován pro WCF na komunikaci WCF, a proto není interoperabilní. Toto je také nejvíce výkonné kodér všech kodérů, které WCF nabízí.  
  
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>, element Binding, určuje kódování znaků a správu verzí zpráv pro zprávy pomocí kódování MTOM. MTOM je efektivní technologie pro přenos binárních dat ve zprávách WCF. Kodér MTOM se pokusí vytvořit rovnováhu mezi efektivitou a interoperabilitou. Kódování MTOM přenáší většinu XML v textové podobě, ale optimalizuje velké bloky binárních dat jejich přenosem tak, jak jsou, bez konverze na text. V souvislosti s efektivitou, mezi kodéry WCF poskytuje, je MTOM mezi textem (nejpomalejší) a binární (nejrychlejší).  
  
## <a name="how-to-choose-a-message-encoder"></a>Výběr kodéru zprávy  
 V následující tabulce jsou popsány běžné faktory, které slouží k výběru kodéru zpráv. Určete prioritu faktorů, které jsou pro vaši aplikaci důležité, a pak zvolte kodéry zpráv, které fungují nejlépe s těmito faktory. Nezapomeňte zvážit jakékoli další faktory, které nejsou uvedené v této tabulce, a žádné vlastní kodéry zpráv, které mohou být ve vaší aplikaci nutné.  
  
|Jednotek|Popis|Kodéry, které podporují tento faktor|  
|------------|-----------------|---------------------------------------|  
|Podporované znakové sady|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>a <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> podporují jenom kódování UTF8 a UTF16 Unicode (*big-endian* a *Little endian*). Pokud je vyžadováno jiné kódování, například UTF7 nebo ASCII, je nutné použít vlastní kodér. Ukázku vlastního kodéru najdete v tématu [vlastní kodér zpráv](https://docs.microsoft.com/dotnet/framework/wcf/samples/custom-message-encoder-custom-text-encoder).|Text|  
|Určených|Kontrola je schopnost kontrolovat zprávy během přenosu. Kódování textu, buď s použitím protokolu SOAP nebo bez něj, umožňuje kontrolovat a analyzovat zprávy mnoha aplikacemi bez použití specializovaných nástrojů. Použití zabezpečení přenosu na úrovni zprávy nebo přenosu má vliv na vaši možnost kontrolovat zprávy. Utajení chrání zprávu před tím, než je prověřena a integrita chrání zprávu před úpravou.|Text|  
|Spolehlivost|Spolehlivost je odolnost kodéru proti chybám přenosu. Spolehlivost lze také poskytnout na úrovni zpráv, přenosů nebo aplikací. Všechny standardní kodéry WCF předpokládají, že spolehlivost zajišťuje jiná vrstva. Kodér má malou schopnost obnovení z chyby přenosu.|Žádné|  
|Administrativ|Jednoduchost představuje náběh, ve kterém můžete vytvořit kodéry a dekodéry pro specifikaci kódování. Kódování textu je obzvláště výhodné pro jednoduchost a kódování textu POX má další výhodu nevyžadování podpory pro zpracování protokolu SOAP.|Text (POX)|  
|Velikost|Kódování určuje množství režie uložené na obsahu. Velikost kódovaných zpráv je přímo v souvislosti s maximální propustností operací služby. Binární kódování jsou všeobecně kompaktnější než kódování textu. Pokud je velikost zprávy na úrovni Premium, zvažte také komprimaci obsahu zprávy během kódování. Komprese však přidává náklady na zpracování pro odesílatele zprávy i příjemce.|Binární|  
|Streamování|Streamování umožňuje aplikacím zahájit zpracování zprávy před doručením celé zprávy. Efektivní používání streamování vyžaduje, aby na začátku zprávy byla k dispozici důležitá data pro zprávu, aby přijímající aplikace nemusela čekat na doručení. Aplikace používající přenos přes datový proud musí navíc organizovat data ve zprávě přírůstkově, takže obsah nemá dopředné závislosti. V mnoha případech je nutné narušit obsah streamování a mít nejmenší možnou velikost přenosu tohoto obsahu.|Žádné|  
|Podpora nástrojů třetích stran|Oblasti podpory pro kódování zahrnují vývoj a diagnostiku. Vývojáři třetích stran udělali velké investice do knihoven a sad nástrojů pro zpracování zpráv kódovaných ve formátu POX.|Text (POX)|  
|Interoperabilita|Tento faktor odkazuje na schopnost kodéru WCF spolupracovat s jinými službami než WCF.|Text<br /><br /> MTOM (částečný)|  
  
Poznámka: při použití binárního kodéru nebude použití nastavení IgnoreWhitespace při vytváření objektu XMLReader nijak ovlivněno.  Například pokud v rámci operace služby provedete následující:  

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
  
## <a name="compression-and-the-binary-encoder"></a>Komprese a binární kodér

Počínaje WCF 4,5 binární kodér WCF přidá podporu pro kompresi. To umožňuje použít algoritmus gzip/deflate pro posílání komprimovaných zpráv z klienta služby WCF a také reagovat pomocí komprimovaných zpráv z místního rozhraní WCF. Tato funkce umožňuje kompresi v přenosech HTTP i TCP. Služba WCF hostovaná službou IIS může být vždy povolena pro odesílání komprimovaných odpovědí konfigurací hostitelského serveru služby IIS. Typ komprese je nakonfigurován s <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A?displayProperty=nameWithType> vlastností. Tato vlastnost je nastavena na jednu z <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType> hodnot výčtu:

- <xref:System.ServiceModel.Channels.CompressionFormat.Deflate>
- <xref:System.ServiceModel.Channels.CompressionFormat.GZip>
- <xref:System.ServiceModel.Channels.CompressionFormat.None>
  
Vzhledem k tomu, že se tato vlastnost zveřejňuje jenom na binaryMessageEncodingBindingElement, bude potřeba vytvořit vlastní vazbu, jako je třeba následující, abyste mohli tuto funkci použít:

 ```xml
 <customBinding>
   <binding name="BinaryCompressionBinding">
     <binaryMessageEncoding compressionFormat ="GZip" />
     <httpTransport />
  </binding>
</customBinding>
 ```

Klient i služba musí souhlasit s odesíláním a přijímáním komprimovaných zpráv, a proto musí být vlastnost compressionFormat nakonfigurována na elementu binaryMessageEncoding na straně klienta i služby. ProtocolException je vyvolána, pokud buď není nakonfigurována služba nebo klient pro komprimaci, ale druhá strana je. Povolení komprese by mělo být pečlivě zváženo. Komprese je hlavně užitečná v případě, že šířka pásma sítě je kritická. V případě, že je procesor kritickým bodem, komprese sníží propustnost. Aby bylo možné zjistit, zda se jedná o výhody aplikace, je nutné provést příslušné testování v simulovaném prostředí.  
  
## <a name="see-also"></a>Viz také

- [Vazby](bindings.md)
