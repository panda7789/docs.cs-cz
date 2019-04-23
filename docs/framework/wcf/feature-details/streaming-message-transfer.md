---
title: Streamování přenosu zpráv
ms.date: 03/30/2017
ms.assetid: 72a47a51-e5e7-4b76-b24a-299d51e0ae5a
ms.openlocfilehash: e58b0ce698df310a5e18bcd24201fb2e27a9c1aa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136874"
---
# <a name="streaming-message-transfer"></a>Streamování přenosu zpráv
Přenosy Windows Communication Foundation (WCF) podporují dva režimy pro přenos zpráv:  
  
-   Přenosy ve vyrovnávací paměti uložení celá zpráva vyrovnávací paměť, až do dokončení přenosu. Ve vyrovnávací paměti zpráv musí být zcela doručována předtím, než příjemce může číst.  
  
-   Streamovaná přenosy zveřejnit zprávu jako datový proud. Příjemce se spustí předtím, než je zcela doručit zprávu zpracovat.  
  
-   Streamovaná přenosy lze vylepšit škálovatelnost služby eliminuje požadavek pro velké paměti vyrovnávací paměti. Zda je režim přenosu změna zlepšuje škálovatelnost závisí na velikosti přenášených zprávy. Velikost velkých zpráv upřednostnit pomocí proudu přenosy.  
  
 Ve výchozím nastavení používají ve vyrovnávací paměti přenosy HTTP, protokolu TCP/IP a přenosy pojmenovaného kanálu. Tento dokument popisuje, jak přepnout těchto přenosů z ve vyrovnávací paměti proudu přenosu režimu a důsledky tohoto postupu.  
  
## <a name="enabling-streamed-transfers"></a>Povolení streamovaná přenosy  
 Výběr mezi režimy ve vyrovnávací paměti a datovým proudem přenos se provádí na element vazby přenosu. Má element vazby <xref:System.ServiceModel.TransferMode> vlastnost, která může být nastaven na `Buffered`, `Streamed`, `StreamedRequest`, nebo `StreamedResponse`. Nastavení režimu převodu na `Streamed` umožňuje streamování komunikace v obou směrech. Nastavení režimu převodu na `StreamedRequest` nebo `StreamedResponse` umožňuje streamování komunikace v uvedeném směru.  
  
 <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.NetTcpBinding>, A <xref:System.ServiceModel.NetNamedPipeBinding> vystavení vazby <xref:System.ServiceModel.TransferMode> vlastnost. Pro další přenosy musíte vytvořit vlastní vazby pro nastavení režimu převodu.  
  
 Rozhodnout a použít ve vyrovnávací paměti nebo streamovaná přenosy je místní rozhodnutí koncového bodu. Pro přenosy HTTP je režim přenosu nešíří přes připojení, nebo na serverech a jiných dodavatelů. Nastavení režimu převodu se neprojeví v popisu rozhraní služby. Po vygenerování třídy klienta pro službu, musíte upravit konfigurační soubor služby určené pro použití s datovým proudem přenosy pro nastavení režimu. Pro protokoly TCP a přenosy pojmenovaný kanál se šíří je režim přenosu jako kontrolní výraz zásad.  
  
 Ukázky kódu najdete v tématu [jak: Povolení streamování](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md).  
  
## <a name="enabling-asynchronous-streaming"></a>Povolení asynchronního streamování  
 Pokud chcete povolit, asynchronního streamování, přidejte <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> chování koncového bodu do hostitele služby a nastavte jeho <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> vlastnost `true`.  
  
 Tato verze služby WCF také adde možnost true asynchronního streamování na straně odesílání. To zlepšuje škálovatelnost služby ve scénářích, kde je datový proud zpráv do více klientů, z nichž některé jsou pomalé v režimu čtení; pravděpodobně z důvodu zahlcení sítě nebo jsou není čtení vůbec. V těchto scénářích WCF už blokuje jednotlivá vlákna ve službě za klienta. Tím se zajistí, že služba je schopná zpracovat mnoho více klientů a zlepšuje škálovatelnost služby.  
  
## <a name="restrictions-on-streamed-transfers"></a>Omezení streamovaná převodů  
 Pomocí režimu proudu přenosu způsobí, že čas spuštění k vynucení další omezení.  
  
 Operace, ke kterým dochází mezi datovým proudem přenosu může mít kontrakt s maximálně jeden vstupní nebo výstupní parametr. Tento parametr odpovídá celý text zprávy a musí být <xref:System.ServiceModel.Channels.Message>, odvozený typ <xref:System.IO.Stream>, nebo <xref:System.Xml.Serialization.IXmlSerializable> implementace. S návratovou hodnotou operace je ekvivalentní s tím, že výstupní parametr.  
  
 Některé funkce WCF, jako je například spolehlivé zasílání zpráv, transakce a zabezpečení na úrovni zprávy protokolu SOAP, spoléhají na ukládání do vyrovnávací paměti zpráv pro přenosy. Pomocí těchto funkcí může snížit nebo odstranit přinese zlepšení výkonu díky využití datových proudů. K zabezpečení proudu přenosu, použijte pouze zabezpečení na úrovni přenosu nebo transportní vrstvy zabezpečení a zprávy jenom ověřování zabezpečení.  
  
 Záhlaví SOAP jsou vždy ukládány do vyrovnávací paměti, i v případě, že je režim přenosu je nastavena datovým proudem. Záhlaví zprávy nesmí překročit velikost `MaxBufferSize` kvóty přenosu. Další informace o tomto nastavení najdete v tématu [přenosové kvóty](../../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
## <a name="differences-between-buffered-and-streamed-transfers"></a>Rozdíly mezi přenosy ve vyrovnávací paměti a proudy  
 Změna režimu přenosu z uložených do vyrovnávací paměti datovým proudem, změní se také tvar nativní kanálu TCP a přenosy pojmenovaného kanálu. Ve vyrovnávací paměti při přenosech, obrazce nativní kanálu je <xref:System.ServiceModel.Channels.IDuplexSessionChannel>. Pro přenosy datovým proudem, nativní kanály jsou <xref:System.ServiceModel.Channels.IRequestChannel> a <xref:System.ServiceModel.Channels.IReplyChannel>. Změna režimu přenosu v existující aplikaci, která používá tyto přenosy přímo (to znamená, ne prostřednictvím smlouvy o poskytování služeb) vyžaduje změnu tvar očekávané kanálu pro vytváření kanálů a naslouchací procesy.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Povolení streamování](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
