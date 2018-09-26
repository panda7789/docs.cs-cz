---
title: Koncové body služby a adresování front
ms.date: 03/30/2017
ms.assetid: 7d2d59d7-f08b-44ed-bd31-913908b83d97
ms.openlocfilehash: 71ebf29e51118a7f555f3e79598e49ffd65e0c63
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47156582"
---
# <a name="service-endpoints-and-queue-addressing"></a>Koncové body služby a adresování front
Toto téma popisuje, jak klienti adres služby, které načítají z fronty a mapování koncových bodů služby do fronty. Následující obrázek znázorňuje Připomínáme, classic, že nasazení aplikace Windows Communication Foundation (WCF) zařazených do fronty.  
  
 ![Ve frontě diagramu aplikace](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "distribuované obrázek fronty")  
  
 Pro klienta k odeslání zprávy do služby Klient adresy zprávy do cílové fronty. Služba čtení zpráv z fronty nastaví adresu naslouchání do cílové fronty. Adresování ve službě WCF je Uniform Resource Identifier URI názvy front služby Řízení front zpráv (MSMQ) nejsou založené na identifikátor URI. Proto je důležité pochopit, jak řešit fronty vytvořené ve službě MSMQ pomocí technologie WCF.  
  
## <a name="msmq-addressing"></a>Adresování MSMQ  
 K identifikaci fronty používaný službou MSMQ cesty a názvy ve formátu. Cesty zadejte název hostitele a `QueueName`. Volitelně může být `Private$` mezi název hostitele a `QueueName` označuje soukromou frontu, která není publikována ve službě Active Directory directory.  
  
 Názvy cest se mapují na "FormatNames" k určení dalších aspektů na adrese, včetně směrování a fronty přenosu protokolu správce. Správce fronty podporuje dva protokoly přenosu: nativní protokol služby MSMQ a protokol spolehlivého zasílání zpráv na SOAP (SRMP).  
  
 Další informace o názvech cestu a formátu MSMQ najdete v tématu [o služby Řízení front zpráv](https://go.microsoft.com/fwlink/?LinkId=94837).  
  
## <a name="netmsmqbinding-and-service-addressing"></a>NetMsmqBinding a adresování služeb  
 Při přiřazování zpráv do služby, je vybrán schéma v identifikátoru URI podle přenosu používá pro komunikaci. Každý přenos ve službě WCF má jedinečné schéma. Schéma musí odpovídat povaze přenosu používá pro komunikaci. Například net.tcp net.pipe, HTTP a tak dále.  
  
 Služby MSMQ zařadí do fronty ve WCF zpřístupňuje přenosu schéma net.msmq. Všechny zákazníky a vyřešené používá schéma net.msmq zprávy pomocí `NetMsmqBinding` přes kanál zařazených do fronty přenosu služby MSMQ.  
  
 Adresování fronty ve WCF je založena na vzoru následující:  
  
 NET.MSMQ: / / \< *název hostitele*> / [privátní /] \< *název fronty*>  
  
 kde:  
  
-   \<*název hostitele*> je název počítače, který je hostitelem cílové fronty.  
  
-   [privátní] je volitelné. Používá se při adresování cílové fronty, která je soukromé fronty. K vyřešení veřejné fronty, nesmíte zadat privátní. Všimněte si, že na rozdíl od služby MSMQ cesty, neexistuje žádný "$" ve formě identifikátoru URI WCF.  
  
-   \<*Název fronty*> je název fronty. Název fronty najdete také dílčí. Proto \< *název fronty*> = \< *název fronty*> [; *Název dílčí queue*].  
  
 Test1: K adresování soukromé fronty PurchaseOrders hostované na počítač abc atadatum.com, identifikátor URI by net.msmq://abc.adatum.com/private/PurchaseOrders.  
  
 Priklad2: K vyřešení veřejné fronty AccountsPayable hostované na počítači def atadatum.com identifikátoru URI by net.msmq://def.adatum.com/AccountsPayable.  
  
 Adresa fronty se používá jako identifikátor URI naslouchání naslouchací proces ke čtení zpráv z. Jinými slovy adresa fronty je ekvivalentní k naslouchání TCP portu soketu.  
  
 Koncový bod, který čte z fronty, musíte zadat adresu fronty pomocí stejné schéma, které jste zadali dříve při otevření hostitele ServiceHost. Příklady najdete v tématu [vazby Net MSMQ](../../../../docs/framework/wcf/samples/net-msmq-binding.md) a [zprávy služby Řízení front integrace vazby ukázky](https://msdn.microsoft.com/library/997d11cb-f2c5-4ba0-9209-92843d4d0e1a).  
  
### <a name="multiple-contracts-in-a-queue"></a>Více kontraktů ve frontě  
 Různé smlouvy můžete implementovat zprávy ve frontě. V takovém případě je důležité, že je PRAVDA, pokud chcete úspěšně číst a zpracovávat všechny zprávy jednu z následujících:  
  
-   Zadejte koncový bod pro službu, která implementuje všechny kontrakty. Toto je doporučený postup.  
  
-   Zadejte několik koncových bodů s různé kontrakty, ale ujistěte se, že všechny koncové body používat stejné `NetMsmqBinding` objektu. Dispatching logika ServiceModel používá pumpu zpráv, který čte zprávy z přenosový kanál pro odesílání, který nakonec zrušit spojuje zprávy na základě smlouvy do různých koncových bodů. Pro dvojice identifikátoru URI/vytváření vazby vlastností listenurimode nastavenou na se vytvoří pumpu zpráv. Adresa fronty se používá jako identifikátor URI naslouchání naslouchací proces ve frontě. Všechny koncové body pomocí stejného objektu vazby zajistí, že jeden zprávy odeslané používá číst zprávy a rušit multiplexovaný do příslušných koncových bodů s podle smlouvy.  
  
### <a name="srmp-messaging"></a>SRMP zasílání zpráv  
 Jak bylo uvedeno výše můžete použít protokol SRMP k frontě přenosů. To se běžně používá, když přenos pomocí protokolu HTTP odesílá zprávy mezi fronty přenosu a cílové fronty.  
  
 Pro použití protokolu přenosu SRMP, adresa zpráv pomocí net.msmq schéma identifikátoru URI, jak již bylo zmíněno dříve a zadejte volbu SRMP nebo zabezpečené SRMP v `QueueTransferProtocol` vlastnost `NetMsmqBinding`.  
  
 Zadání `QueueTransferProtocol` vlastnost je jen pro odesílání funkce. Tento údaj klientem, který typ fronty přenosu protokol se má použít.  
  
### <a name="using-active-directory"></a>Pomocí služby Active Directory  
 Služby MSMQ obsahuje podporu pro integraci služby Active Directory. Když je služba MSMQ nainstalovaná s integrací služby Active Directory, musí být počítač součástí domény Windows. Služby Active Directory se používá k publikování fronty pro zjišťování; Tyto fronty se nazývají *veřejné fronty*. Při řešení do fronty, fronta možné vyřešit pomocí služby Active Directory. To se podobá použití systému DNS (Domain Name) překládání IP adresy z názvu sítě. `UseActiveDirectory` Vlastnost `NetMsmqBinding` je logická hodnota, která označuje, zda kanálu ve frontě musí používat Active Directory k vyřešení fronty identifikátoru URI. Ve výchozím nastavení nastavena na `false`. Pokud `UseActiveDirectory` je nastavena na `true`, pak kanálu ve frontě net.msmq:// URI převést na formát názvu pomocí služby Active Directory.  
  
 `UseActiveDirectory` Vlastnost má smysl pouze pro klienta, který odesílá zprávy, protože se používá pro překlad adres fronty, při odesílání zpráv.  
  
### <a name="mapping-netmsmq-uri-to-message-queuing-format-names"></a>Mapovací identifikátor URI net.msmq ke zprávě fronty názvy ve formátu souboru  
 Kanálu ve frontě zpracovává mapování názvu identifikátoru URI net.msmq poskytuje kanál názvy ve formátu MSMQ. Následující tabulka shrnuje pravidla použít k mapování mezi nimi.  
  
|Adresa WCF URI na základě fronty|Použijte vlastnost služby Active Directory|Vlastnost fronty přenosu protokolu|Výsledný formát názvů MSMQ|  
|----------------------------------|-----------------------------------|--------------------------------------|---------------------------------|  
|Net.msmq://\<machine-name>/private/abc|False (výchozí)|Nativní (výchozí)|DIRECT=OS:machine-name\private$\abc|  
|Net.msmq://\<machine-name>/private/abc|False|SRMP|DIRECT = os http://machine/msmq/private$/ abc|  
|Net.msmq://\<machine-name>/private/abc|Hodnota TRUE|Nativní|VEŘEJNÉ = některé guid (identifikátor GUID fronty)|  
  
### <a name="reading-messages-from-the-dead-letter-queue-or-the-poison-message-queue"></a>Čtení zpráv z fronty nedoručených zpráv nebo Poison zpráv fronty  
 Chcete-li načíst zprávy z fronty poison zpráv, která je dílčí cílové fronty, otevřete `ServiceHost` adresou dílčí fronty.  
  
 Příklad: Služba, která čte z fronty zpráv poison PurchaseOrders soukromou frontu z místního počítače chcete řešit net.msmq://localhost/private/PurchaseOrders;poison.  
  
 Ke čtení zpráv z fronty nedoručených zpráv transakcí systému, identifikátor URI musí být ve tvaru: net.msmq://localhost/system$; DeadXact.  
  
 Ke čtení zpráv z fronty nedoručených zpráv netransakční systému, identifikátor URI musí být ve tvaru: net.msmq://localhost/system$; nedoručených zpráv.  
  
 Pokud používáte vlastní frontu nedoručených zpráv, mějte na paměti, že fronta nedoručených zpráv musí být umístěn v místním počítači. Identifikátor URI fronty nedoručených zpráv v důsledku toho je omezen na formuláři:  
  
 NET.MSMQ: //localhost/ [privátní /] \< *vlastní dead písmeno fronty name*>.  
  
 Služby WCF ověřuje, že byly všechny zprávy, které obdrží řešit do konkrétní fronty, který naslouchá. Pokud cílové fronty zprávy do fronty, které se nachází v neodpovídá, službu nezpracovává zprávy. Jedná se o problém, který služby naslouchání do fronty nedoručených zpráv musí řešit, protože všechny zprávy ve frontě nedoručených měl být doručena jinde. Ke čtení zpráv z fronty nedoručených zpráv, nebo z nezpracovatelných fronty `ServiceBehavior` s <xref:System.ServiceModel.AddressFilterMode.Any> parametr je nutné použít. Příklad najdete v tématu [fronty nedoručených zpráv](../../../../docs/framework/wcf/samples/dead-letter-queues.md).  
  
## <a name="msmqintegrationbinding-and-service-addressing"></a>MsmqIntegrationBinding a adresování služeb  
 `MsmqIntegrationBinding` Se používá ke komunikaci s tradiční aplikacím služby MSMQ. K usnadnění vzájemná spolupráce s existující aplikaci služby MSMQ, WCF podporuje adresování pouze název formátu. Díky tomu se zprávy odesílané pomocí této vazby musí odpovídat schéma identifikátoru URI:  
  
 MSMQ.formatname:\<*název formátu MSMQ*>>  
  
 Název formátu MSMQ je ve formátu určeném služby MSMQ v [o služby Řízení front zpráv](https://go.microsoft.com/fwlink/?LinkId=94837).  
  
 Všimněte si, že můžete použít pouze názvů v přímém formátu a názvy veřejných a privátních formátu (vyžaduje integrace služby Active Directory) při příjmu zprávy z fronty pomocí `MsmqIntegrationBinding`. Doporučujeme však, že používáte názvů v přímém formátu. Třeba na [!INCLUDE[wv](../../../../includes/wv-md.md)], pomocí žádným jiným názvem formátu způsobí chybu, protože systém se pokusí otevřít dílčí fronty, která se dá otevřít jenom pomocí přímého názvu formátu.  
  
 Při adresování pomocí SRMP `MsmqIntegrationBinding`, neexistuje žádný požadavek na přidání /msmq/ v přímém formátu název, který pomůže Internetové informační služby (IIS) s odesíláním. Příklad: při adresování protokolu abc pomocí SRMP místo přímé fronty =http://adatum.com/msmq/private$/ abc, měli byste použít přímo =http://adatum.com/private$/ abc.  
  
 Všimněte si, že nemůžete použít net.msmq:// adresování s `MsmqIntegrationBinding`. Protože `MsmqIntegrationBinding` podporuje volného tvaru MSMQ formát názvu adresování, můžete použít službu WCF používající tuto vazbu použít vícesměrové vysílání a distribuční seznam funkcí ve službě MSMQ. Jedinou výjimkou je určení `CustomDeadLetterQueue` při použití `MsmqIntegrationBinding`. Musí být formulář net.msmq://, podobně jako na to, jak je určen pomocí `NetMsmqBinding`.  
  
## <a name="see-also"></a>Viz také  
 [Webhosting frontové aplikace](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
