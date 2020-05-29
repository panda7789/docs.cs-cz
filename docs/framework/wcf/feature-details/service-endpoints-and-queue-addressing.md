---
title: Koncové body služby a adresování front
ms.date: 03/30/2017
ms.assetid: 7d2d59d7-f08b-44ed-bd31-913908b83d97
ms.openlocfilehash: 8b323993a698dac219e0f2be43e9b508a19065dd
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202414"
---
# <a name="service-endpoints-and-queue-addressing"></a>Koncové body služby a adresování front
Toto téma popisuje, jak klienti adresují služby, které čtou z front a jak se mapují koncové body služby na fronty. Jako připomenutí znázorňuje následující ilustrace nasazení aplikace ve frontě Windows Communication Foundation (WCF).  
  
 ![Diagram aplikace ve frontě](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Distribuované – fronta – obrázek")  
  
 Aby mohl klient odeslat zprávu do služby, klient adresuje zprávu do cílové fronty. Aby služba četla zprávy z fronty, nastaví její adresu naslouchání na cílovou frontu. Adresování ve službě WCF je založené na identifikátoru URI (Uniform Resource Identifier), zatímco názvy front služby Řízení front zpráv (MSMQ) nejsou založené na identifikátoru URI. Proto je důležité pochopit, jak se ve službě MSMQ vytvořily fronty vytvořené pomocí WCF.  
  
## <a name="msmq-addressing"></a>Adresování MSMQ  
 Služba MSMQ používá k identifikaci fronty cesty a názvy formátu. Cesty určují název hostitele a `QueueName` . Volitelně může existovat `Private$` mezi názvem hostitele a a `QueueName` označením soukromé fronty, která není publikována v adresářové službě Active Directory.  
  
 Názvy cest jsou namapovány na "FormatNames" k určení dalších aspektů adresy, včetně směrování a přenosového protokolu pro správce fronty. Správce fronty podporuje dva protokoly přenosů: nativní protokol MSMQ a protokol SRMP (SOAP Reliable Messaging Protocol).  
  
 Další informace o cestách a názvech formátu MSMQ najdete v tématu [o službě Řízení front zpráv](https://docs.microsoft.com/previous-versions/windows/desktop/legacy/ms706032(v=vs.85)).  
  
## <a name="netmsmqbinding-and-service-addressing"></a>NetMsmqBinding a adresování služeb  
 Při adresování zprávy službě se vybere schéma v identifikátoru URI na základě přenosu používaného pro komunikaci. Každý přenos v rámci WCF má jedinečné schéma. Schéma musí odrážet povahu přenosu používaného pro komunikaci. Například NET. TCP, NET. pipe, HTTP atd.  
  
 Přenos ve frontě MSMQ ve službě WCF zpřístupňuje schéma NET. MSMQ. Všechny zprávy, které jsou adresovány pomocí schématu NET. MSMQ, se odesílají pomocí `NetMsmqBinding` přenosového kanálu MSMQ ve frontě.  
  
 Adresování fronty ve službě WCF je založené na následujícím vzoru:  
  
 NET. MSMQ:// \<*host-name*> /[Private/]\<*queue-name*>  
  
 kde:  
  
- \<*host-name*>je název počítače, který je hostitelem cílové fronty.  
  
- [Private] je volitelné. Používá se při adresování cílové fronty, která je privátní frontou. Pokud chcete adresovat veřejnou frontu, nesmíte zadat Private. Všimněte si, že na rozdíl od cest služby MSMQ není ve formuláři identifikátoru URI WCF žádná "$".  
  
- \<*queue-name*>je název fronty. Název fronty může také odkazovat na dílčí frontu. Proto \<*queue-name*>  =  \<*name-of-queue*> [;* Název podřízené fronty*].  
  
 Priklad1: aby se PurchaseOrders privátní fronta hostovaná v počítači abc atadatum.com, identifikátor URI by byl NET. MSMQ://abc.adatum.com/private/PurchaseOrders.  
  
 Example2: Pokud chcete adresovat AccountsPayable veřejné fronty hostované na počítači atadatum.com, identifikátor URI by byl NET. MSMQ://def.adatum.com/AccountsPayable..  
  
 Adresa fronty se používá jako identifikátor URI poslechu naslouchacího procesu ke čtení zpráv z. Jinými slovy, adresa fronty je ekvivalentní portu TCP soketu.  
  
 Koncový bod, který čte z fronty, musí specifikovat adresu fronty za použití stejného schématu zadaného dříve při otevírání třídy ServiceHost. Příklady najdete v tématu o [vytváření vazeb v síti MSMQ](../../../../docs/framework/wcf/samples/net-msmq-binding.md).  
  
### <a name="multiple-contracts-in-a-queue"></a>Několik kontraktů ve frontě  
 Zprávy ve frontě můžou implementovat různé kontrakty. V takovém případě je nutné, aby jedna z následujících podmínek byla úspěšně čtena a zpracována všechny zprávy:  
  
- Zadejte koncový bod pro službu, která implementuje všechny smlouvy. Toto je doporučený postup.  
  
- Zadejte více koncových bodů s různými kontrakty, ale zajistěte, aby všechny koncové body používaly stejný `NetMsmqBinding` objekt. Logika odeslání ve ServiceModel používá čerpadlo zpráv, které čte zprávy z transportního kanálu pro odesílání, což nakonec demultiplexuje zprávy na základě kontraktu na různé koncové body. Vytvoří se čerpadlo zpráv pro dvojici identifikátorů URI a vazeb pro poslech. Adresa fronty se používá pro naslouchací proces zařazený do fronty jako identifikátor URI poslechu. Když všechny koncové body používají stejný objekt vazby, zajistí se použití jediného pumpy zpráv ke čtení zprávy a demultiplexování do relevantních koncových bodů na základě kontraktu.  
  
### <a name="srmp-messaging"></a>Zprávy SRMP  
 Jak je popsáno výše, můžete použít protokol SRMP pro přenosy front-Queue. To se běžně používá, když přenos HTTP přenáší zprávy mezi frontou přenosů a cílovou frontou.  
  
 Chcete-li použít přenosový protokol SRMP, adresujte zprávy pomocí schématu identifikátoru URI NET. MSMQ, jak bylo zmíněno dříve, a určete volbu protokolu SRMP nebo zabezpečení SRMP ve `QueueTransferProtocol` vlastnosti `NetMsmqBinding` .  
  
 Zadání `QueueTransferProtocol` vlastnosti je funkce pouze pro odesílání. Označuje klienta, který druh přenosového protokolu fronty se má použít.  
  
### <a name="using-active-directory"></a>Pomocí Active Directory  
 Služba MSMQ je dodávána s podporou integrace služby Active Directory. Když je služba MSMQ nainstalována s integrací služby Active Directory, musí být počítač součástí domény systému Windows. Služba Active Directory se používá k publikování front pro zjišťování; takové fronty se nazývají *veřejné fronty*. Při adresování fronty je možné tuto frontu přeložit pomocí služby Active Directory. To se podobá tomu, jak se používá služba DNS (Domain Name System) k překladu IP adresy síťového názvu. `UseActiveDirectory`Vlastnost v `NetMsmqBinding` je logická hodnota, která označuje, jestli kanál zařazený do fronty musí používat službu Active Directory k překladu identifikátoru URI fronty. Ve výchozím nastavení je nastaveno na `false` . Pokud `UseActiveDirectory` je vlastnost nastavena na `true` , kanál ve frontě používá službu Active Directory k převodu NET. MSMQ://URI na název formátu.  
  
 `UseActiveDirectory`Vlastnost má smysl jenom pro klienta, který posílá zprávu, protože se používá k překladu adresy fronty při posílání zpráv.  
  
### <a name="mapping-netmsmq-uri-to-message-queuing-format-names"></a>Mapování identifikátoru URI NET. MSMQ na názvy formátů služby Řízení front zpráv  
 Kanál kanálu zpracovává mapování názvu identifikátoru URI NET. MSMQ, který je zadaný pro kanál, na názvy formátu MSMQ. Následující tabulka shrnuje pravidla používaná k mapování mezi nimi.  
  
|Adresa fronty na základě identifikátoru URI WCF|Použít vlastnost služby Active Directory|Vlastnost protokolu přenosu fronty|Výsledné názvy formátu MSMQ|  
|----------------------------------|-----------------------------------|--------------------------------------|---------------------------------|  
|`Net.msmq://<machine-name>/private/abc`|False (výchozí)|Nativní (výchozí)|`DIRECT=OS:machine-name\private$\abc`|  
|`Net.msmq://<machine-name>/private/abc`|False|SRMP|`DIRECT=http://machine/msmq/private$/abc`|  
|`Net.msmq://<machine-name>/private/abc`|True|Nativní|`PUBLIC=some-guid`(identifikátor GUID fronty)|  
  
### <a name="reading-messages-from-the-dead-letter-queue-or-the-poison-message-queue"></a>Načítají se zprávy z fronty nedoručených zpráv nebo z fronty pro nepoškozené zprávy.  
 Chcete-li číst zprávy z fronty nezpracovatelných zpráv, která je podfrontou cílové fronty, otevřete `ServiceHost` adresu dílčí fronty.  
  
 Příklad: služba, která čte z fronty nezpracovatelných zpráv PurchaseOrders soukromé fronty z místního počítače, bude adresovat NET. MSMQ://localhost/private/PurchaseOrders; jed.  
  
 Chcete-li číst zprávy z fronty nedoručených zpráv transakčního systému, musí být identifikátor URI ve tvaru: NET. MSMQ://localhost/System $;D eadXact.  
  
 Chcete-li číst zprávy z fronty nedoručených zpráv netransakčního systému, identifikátor URI musí být ve tvaru: NET. MSMQ://localhost/System $;D eadLetter.  
  
 Pokud používáte vlastní frontu nedoručených zpráv, musí být fronta nedoručených zpráv v místním počítači. V takovém případě je identifikátor URI pro frontu nedoručených zpráv omezený na formát:  
  
 NET. MSMQ://localhost/[Private/] \<*custom-dead-letter-queue-name*> .  
  
 Služba WCF ověřuje, že všechny zprávy, které obdrží, byly adresovány do konkrétní fronty, na které naslouchá. Pokud cílová fronta zprávy nesouhlasí s frontou, ve které se nachází, služba zprávu nezpracovává. Jedná se o problém, který musí splňovat služby, které naslouchá frontě nedoručených zpráv, protože jakékoli zprávy ve frontě nedoručených zpráv byly určeny k doručování jinde. Aby bylo možné číst zprávy z fronty nedoručených zpráv nebo z fronty nefunkčních, `ServiceBehavior` <xref:System.ServiceModel.AddressFilterMode.Any> musí být použit parametr s parametrem. Příklad najdete v tématu [fronty nedoručených zpráv](../../../../docs/framework/wcf/samples/dead-letter-queues.md).  
  
## <a name="msmqintegrationbinding-and-service-addressing"></a>MsmqIntegrationBinding a adresování služeb  
 `MsmqIntegrationBinding`Slouží ke komunikaci s tradičními aplikacemi služby MSMQ. Pro usnadnění spolupráce s existující aplikací služby MSMQ podporuje WCF pouze adresování názvů formátu. Proto zprávy odeslané pomocí této vazby musí odpovídat schématu identifikátoru URI:  
  
 MSMQ. FormatName:\<*MSMQ-format-name*>>  
  
 Služba MSMQ-Format-Name má formu určenou službou MSMQ v části [o službě Řízení front zpráv](https://docs.microsoft.com/previous-versions/windows/desktop/legacy/ms706032(v=vs.85)).  
  
 Všimněte si, že při přijímání zpráv z fronty pomocí nástroje můžete použít pouze přímé názvy formátů a názvy veřejných a privátních formátů (vyžaduje integraci služby Active Directory) `MsmqIntegrationBinding` . Doporučuje se ale používat přímé názvy formátů. Například v systému Windows Vista může použití jiného názvu formátu způsobit chybu, protože systém se pokusí otevřít dílčí frontu, která se dá otevřít jenom s přímými názvy formátu.  
  
 Při adresování SRMP pomocí `MsmqIntegrationBinding` není potřeba přidat/MSMQ/do přímého názvu formátu, aby se usnadnila Internetová informační služba (IIS) s odesíláním. Příklad: při adresování fronty ABC pomocí protokolu SRMP namísto nástroje `DIRECT=http://adatum.com/msmq/private$/abc` byste měli použít `DIRECT=http://adatum.com/private$/abc` .  
  
 Počítejte s tím, že nemůžete použít NET. MSMQ://Addressing with `MsmqIntegrationBinding` . Vzhledem `MsmqIntegrationBinding` k tomu, že nástroj podporuje adresování názvů ve formátu MSMQ, můžete použít službu WCF, která pomocí této vazby používá funkce vícesměrového a distribučního seznamu ve službě MSMQ. Jedna výjimka je specifikována `CustomDeadLetterQueue` při použití `MsmqIntegrationBinding` . Musí mít formát NET. MSMQ://, podobně jako jeho zadání pomocí `NetMsmqBinding` .  
  
## <a name="see-also"></a>Viz také

- [Webhosting frontové aplikace](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
