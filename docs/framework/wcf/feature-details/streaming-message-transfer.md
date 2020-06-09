---
title: Streamování přenosu zpráv
ms.date: 03/30/2017
ms.assetid: 72a47a51-e5e7-4b76-b24a-299d51e0ae5a
ms.openlocfilehash: 462144856750a1b8726b574fdc82746da2d72ff7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594787"
---
# <a name="streaming-message-transfer"></a>Streamování přenosu zpráv
Přenosy Windows Communication Foundation (WCF) podporují dva režimy přenosu zpráv:  
  
- Přenosy uložené do vyrovnávací paměti uchovávají celou zprávu ve vyrovnávací paměti, dokud se přenos nedokončí. Zpráva uložená do vyrovnávací paměti musí být zcela doručena předtím, než ji příjemce může přečíst.  
  
- Přenos streamů zveřejňuje zprávu jako datový proud. Příjemce spustí zpracování zprávy před úplným doručením.  
  
- Přenos přes datový proud může zlepšit škálovatelnost služby tím, že eliminuje požadavky na vyrovnávací paměti pro velké objemy paměti. Bez ohledu na to, jestli změna režimu přenosu zlepšuje škálovatelnost, závisí na velikosti přenášených zpráv. Větší velikost zpráv upřednostňuje použití přenosů přes datový proud.  
  
 Ve výchozím nastavení používají přenosy HTTP, TCP/IP a pojmenované kanály přenosy ve vyrovnávací paměti. Tento dokument popisuje, jak přepnout tyto přenosy z vyrovnávací paměti na režim přenosu streamování a důsledky jejich provedení.  
  
## <a name="enabling-streamed-transfers"></a>Povolení přenosů odeslaných datovým proudem  
 Výběr mezi mezipamětí a režimy přenosu s datovým proudem se provádí na elementu vazby přenosu. Element Binding má <xref:System.ServiceModel.TransferMode> vlastnost, která může být nastavena na `Buffered` , `Streamed` , `StreamedRequest` nebo `StreamedResponse` . Nastavení režimu přenosu pro `Streamed` povolení komunikace streamování v obou směrech. Nastavení režimu přenosu na `StreamedRequest` nebo `StreamedResponse` umožňuje komunikaci streamování pouze v uvedeném směru.  
  
 <xref:System.ServiceModel.BasicHttpBinding>Vazby, <xref:System.ServiceModel.NetTcpBinding> a <xref:System.ServiceModel.NetNamedPipeBinding> zpřístupňují <xref:System.ServiceModel.TransferMode> vlastnost. Pro jiné přenosy je nutné vytvořit vlastní vazbu pro nastavení režimu přenosu.  
  
 Rozhodnutí použít buď vyrovnávací paměť, nebo přenos streamování je místní rozhodnutí koncového bodu. V případě přenosů HTTP se režim přenosu nešíří v rámci připojení nebo na servery a další zprostředkovatele. Nastavení režimu přenosu se neprojeví v popisu rozhraní služby. Po vygenerování klientské třídy pro službu musíte upravit konfigurační soubor pro služby určené pro použití s přenosy pomocí streamování pro nastavení režimu. Pro přenosy TCP a pojmenovaného kanálu je Přenosový režim šířen jako kontrolní výraz zásady.  
  
 Ukázky kódu naleznete v tématu [How to: Enable Stream](how-to-enable-streaming.md).  
  
## <a name="enabling-asynchronous-streaming"></a>Povolení asynchronního streamování  
 Pokud chcete povolit asynchronní streamování, přidejte <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> do hostitele služby chování koncového bodu a nastavte jeho <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> vlastnost na `true` .  
  
 Tato verze WCF také ADDE schopnost skutečného asynchronního streamování na straně odeslání. To zlepšuje škálovatelnost služby ve scénářích, kdy je streamování zpráv do více klientů, jejichž čtení je pomalé; Pravděpodobnou příčinou zahlcení sítě nebo vůbec nečte. V těchto scénářích už WCF neblokuje jednotlivá vlákna ve službě pro každého klienta. Tím je zajištěno, že služba bude schopna zpracovat mnoho dalších klientů, což zlepšuje škálovatelnost služby.  
  
## <a name="restrictions-on-streamed-transfers"></a>Omezení přenosů v datových proudech  
 Použití režimu přenosu datového proudu způsobí, že doba běhu vynutí další omezení.  
  
 Operace, ke kterým dochází v přenosu datovým proudem, můžou mít kontrakt s maximálně jedním vstupním nebo výstupním parametrem. Tento parametr odpovídá celému těle zprávy a musí být <xref:System.ServiceModel.Channels.Message> odvozený typ <xref:System.IO.Stream> nebo <xref:System.Xml.Serialization.IXmlSerializable> implementace. Návratová hodnota pro operaci je ekvivalentní s parametrem Output.  
  
 Některé funkce služby WCF, jako jsou spolehlivé zasílání zpráv, transakce a zabezpečení na úrovni zpráv SOAP, se při přenosech spoléhají na ukládání zpráv do vyrovnávací paměti. Použití těchto funkcí může snížit nebo odstranit výhody výkonu získané pomocí streamování. Chcete-li zabezpečit přenos datovým proudem, použijte pouze zabezpečení na úrovni přenosu, nebo použijte zabezpečení zpráv na úrovni přenosu plus pouze ověřování.  
  
 Hlavičky SOAP jsou vždy uloženy do vyrovnávací paměti, i když je režim přenosu nastaven na streamování. Záhlaví zprávy nesmí přesáhnout velikost `MaxBufferSize` přenosového kvóty. Další informace o tomto nastavení najdete v tématu [přenosové kvóty](transport-quotas.md).  
  
## <a name="differences-between-buffered-and-streamed-transfers"></a>Rozdíly mezi mezipamětí a přenosem datovými proudy  
 Změna režimu přenosu z vyrovnávací paměti na streamované změní také tvar nativního kanálu pro přenos TCP a pojmenovaného kanálu. U přenosů ve vyrovnávací paměti je tvar nativního kanálu <xref:System.ServiceModel.Channels.IDuplexSessionChannel> . V případě přenosů v datových proudech jsou nativní kanály <xref:System.ServiceModel.Channels.IRequestChannel> a <xref:System.ServiceModel.Channels.IReplyChannel> . Změna režimu přenosu v existující aplikaci, která tyto přenosy používá přímo (tj. nikoli prostřednictvím kontraktu služby) vyžaduje změnu očekávaného tvaru kanálu pro objekty pro vytváření kanálů a naslouchací procesy.  
  
## <a name="see-also"></a>Viz také

- [Postupy: Povolení streamování](how-to-enable-streaming.md)
