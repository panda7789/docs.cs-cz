---
title: "Koncové body služby a adresování front"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d2d59d7-f08b-44ed-bd31-913908b83d97
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ebfd4b977083206dc0210441fff2c0c08079e34a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="service-endpoints-and-queue-addressing"></a>Koncové body služby a adresování front
Toto téma popisuje, jak klienti adres služby, které čtení z fronty a mapování koncových bodů služby do fronty. Připomínáme, následující obrázek znázorňuje classic [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zařazených do fronty nasazení aplikace.  
  
 ![Diagram aplikace ve frontě](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "distribuované obrázek fronty")  
  
 Pro klienta k odeslání zprávy do služby řeší klienta zprávy do cílové fronty. Pro službu ke čtení zpráv z fronty nastaví její adresu naslouchání do cílové fronty. Adresování v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je založen na Uniform Resource Identifier URI, pokud nejsou názvy fronty služby Řízení front zpráv (MSMQ) na základě identifikátoru URI. Proto je důležité pochopit, jak vyřešit vytvořených pomocí služby MSMQ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="msmq-addressing"></a>Adresování MSMQ  
 MSMQ používá k identifikaci fronty cesty a názvy ve formátu. Cesty, zadejte název hostitele a `QueueName`. Volitelně může být `Private$` mezi název hostitele a `QueueName` udávajících soukromou frontu, která není publikována ve službě Active Directory directory.  
  
 Názvy cest jsou namapované na "FormatNames" k určení dalších aspektů na adresu, včetně směrování a fronty přenosu protokolu správce. Správce front podporuje dva protokoly přenosu: nativní protokol služby MSMQ a protokol spolehlivého zasílání zpráv na protokolu SOAP (SRMP).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Cesta a formát názvy služby MSMQ, najdete v části [o služby Řízení front zpráv](http://go.microsoft.com/fwlink/?LinkId=94837).  
  
## <a name="netmsmqbinding-and-service-addressing"></a>– NetMsmqBinding a adresování služeb  
 Při přiřazování zpráv do služby, je zvolen schéma v identifikátoru URI v závislosti na přenos používá pro komunikaci. Každý přenosu v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] má jedinečné schéma. Schéma musí odrážet povaha přenos používá pro komunikaci. Například net.tcp net.pipe, HTTP a tak dále.  
  
 Služby MSMQ zařazených do fronty přenosu v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zpřístupní net.msmq schéma. Všechny řešit pomocí schéma net.msmq zprávy pomocí `NetMsmqBinding` kanálem zařazených do fronty přenosu služby MSMQ.  
  
 Adresování fronty v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podle vzoru následující:  
  
 NET.MSMQ: / / \< *název hostitele*> / [privátní /] \< *název fronty*>  
  
 kde:  
  
-   \<*název hostitele*> je název počítače, který je hostitelem cílové fronty.  
  
-   [privátní] je volitelné. Používá se při adresování cílové fronty, který je soukromou frontu. Chcete-li vyřešit veřejné fronty, nesmíte zadat privátní. Všimněte si, že na rozdíl od služby MSMQ cesty, neexistuje žádný "$" v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] URI formuláře.  
  
-   \<*Název fronty*> je název fronty. Název fronty najdete také dílčí fronta. Proto \< *název fronty*> = \< *název fronty*> [; *Název dílčí queue*].  
  
 Test1: Chcete-li vyřešit soukromou frontu PurchaseOrders hostované na počítač abc atadatum.com, identifikátor URI by net.msmq://abc.adatum.com/private/PurchaseOrders.  
  
 Priklad2: Chcete-li vyřešit veřejné fronty AccountsPayable hostované na počítači def atadatum.com, identifikátor URI by net.msmq://def.adatum.com/AccountsPayable.  
  
 Adresa fronty se používá jako identifikátor URI naslouchání naslouchací proces ke čtení zpráv z. Jinými slovy adresa fronty je ekvivalentní naslouchání portu TCP soketu.  
  
 Koncový bod, který čte z fronty, musíte zadat adresu fronty pomocí stejné schéma při otevření hostitele ServiceHost zadali dřív. Příklady najdete v tématu [vazby Net MSMQ](../../../../docs/framework/wcf/samples/net-msmq-binding.md) a [zpráv služby Řízení front integrace vazby ukázky](http://msdn.microsoft.com/en-us/997d11cb-f2c5-4ba0-9209-92843d4d0e1a).  
  
### <a name="multiple-contracts-in-a-queue"></a>Víc kontraktů ve frontě  
 Zprávy ve frontě můžete implementovat různé smlouvy. V takovém případě je nezbytné, že je hodnota true, má-li úspěšně číst a zpracovávat všechny zprávy jednu z následujících:  
  
-   Zadejte koncový bod služby, který implementuje všechny smlouvy. Toto je doporučený postup.  
  
-   Zadejte několik koncových bodů s jinou kontrakty, ale zkontrolujte, zda všechny koncové body používají stejné `NetMsmqBinding` objektu. Expediční logiku ServiceModel používá zprávy odeslané, který čte zprávy z kanál přenosu pro odesílání, který nakonec multiplexových zprávy na základě smlouvy k různým koncovým bodům. Zprávy odeslané se vytvoří pro identifikátor URI nebo vazba pár naslouchání. Fronty adresu používá jako identifikátor URI naslouchání naslouchací proces ve frontě. Všechny koncové body pomocí stejného objektu vazby zajistí, že jeden zprávy odeslané se používá k tuto zprávu přečíst a zrušte multiplexovaný do příslušných koncových bodů s založené na smlouvě.  
  
### <a name="srmp-messaging"></a>SRMP zasílání zpráv  
 Jak bylo popsáno dříve můžete protokol SRMP pro přenosy fronty fronty. To se často používá při přenosového protokolu HTTP přenáší zprávy mezi fronty přenosu a cílové fronty.  
  
 Chcete-li používat protokol SRMP přenos, adresa zpráv pomocí schématu identifikátoru URI net.msmq, jak je uvedeno nahoře a zadejte výběr SRMP nebo zabezpečené SRMP v `QueueTransferProtocol` vlastnost `NetMsmqBinding`.  
  
 Určení `QueueTransferProtocol` vlastnost je funkce jen pro odesílání. Tento údaj klientem, který druh fronty přenosu protokol bude použit.  
  
### <a name="using-active-directory"></a>Pomocí služby Active Directory  
 MSMQ teď obsahuje podporu pro integraci služby Active Directory. Když služba MSMQ je nainstalována pomocí integrace služby Active Directory, musí být počítač součástí domény systému Windows. Služby Active Directory se používá k publikování fronty pro zjišťování; Tyto fronty se nazývají *veřejných front*. Při zadávání adresy fronty, dají se fronty vyřešit pomocí služby Active Directory. Toto je podobná použití systému DNS (Domain Name) pro překlad adres IP názvu sítě. `UseActiveDirectory` Vlastnost `NetMsmqBinding` je logická hodnota, která označuje, zda kanálu ve frontě musí používat služby Active Directory k vyřešení fronty identifikátor URI. Ve výchozím nastavení je nastavena na `false`. Pokud `UseActiveDirectory` je nastavena na `true`, pak ve frontě channel převést na název formátu net.msmq:// URI pomocí služby Active Directory.  
  
 `UseActiveDirectory` Vlastnost má smysl pouze pro klienta, který je odesílání zprávy, protože se používá pro překlad adres fronty při odesílání zpráv.  
  
### <a name="mapping-netmsmq-uri-to-message-queuing-format-names"></a>Mapování zpráv služby Řízení front názvy ve formátu URI net.msmq  
 Ve frontě kanál zpracovává mapování zadané net.msmq jméno identifikátor URI kanálu pro názvy ve formátu služby MSMQ. Následující tabulka shrnuje pravidla slouží k mapování mezi nimi.  
  
|Adresa WCF URI na základě fronty|Použijte vlastnost služby Active Directory|Vlastnost fronty přenosu protokolu|Výsledný názvy ve formátu služby MSMQ|  
|----------------------------------|-----------------------------------|--------------------------------------|---------------------------------|  
|NET.MSMQ://\<název počítače >/privátní/abc|NEPRAVDA (výchozí)|Nativní (výchozí)|DIRECT = OS:machine-name\private$ \abc|  
|NET.MSMQ://\<název počítače >/privátní/abc|False|SRMP|DIRECT = http://machine/msmq/private$ / abc|  
|NET.MSMQ://\<název počítače >/privátní/abc|Hodnota TRUE|Nativní|VEŘEJNÉ = některá guid (identifikátor GUID fronty)|  
  
### <a name="reading-messages-from-the-dead-letter-queue-or-the-poison-message-queue"></a>Čtení zpráv z fronty nedoručených zpráv nebo Poison zprávy fronty  
 Chcete-li čtení zpráv z fronty poison zpráva, která je dílčí fronta cílové fronty, otevřete `ServiceHost` s adresou dílčí fronta.  
  
 Příklad: Net.msmq://localhost/private/PurchaseOrders;poison by adres služby, který čte z fronty zpráv poison soukromé fronty PurchaseOrders z místního počítače.  
  
 Ke čtení zpráv z fronty nedoručených zpráv transakcí systému, musí být identifikátor URI ve tvaru: net.msmq://localhost/system$; DeadXact.  
  
 Ke čtení zpráv z fronty nedoručených zpráv netransakční systému, musí být identifikátor URI ve tvaru: net.msmq://localhost/system$; nedoručených zpráv.  
  
 Pokud používáte vlastní frontu nedoručených zpráv, Všimněte si, že frontu nedoručených zpráv musí nacházet na místním počítači. Identifikátor URI pro frontu nedoručených zpráv jako takový je omezen na formulář:  
  
 NET.MSMQ: //localhost/ [privátní /] \< *vlastní zpráv písmeno fronty name*>.  
  
 A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby ověřuje, že všechny zprávy obdrží byla provedena do konkrétní fronty naslouchá na. Pokud cílovou frontu zprávy fronty, kterou je ve službě neodpovídá, službu nezpracovává zprávy. Jedná se o problém, který služby naslouchání do fronty nedoručených zpráv musí řešit, protože jakékoli zprávy do fronty nedoručených zpráv byl určen pro doručena jinde. Ke čtení zpráv z fronty nedoručených zpráv nebo z poškozených fronty, `ServiceBehavior` s <xref:System.ServiceModel.AddressFilterMode.Any> parametr je nutné použít. Příklad, naleznete v části [fronty nedoručených zpráv](../../../../docs/framework/wcf/samples/dead-letter-queues.md).  
  
## <a name="msmqintegrationbinding-and-service-addressing"></a>MsmqIntegrationBinding a adresování služeb  
 `MsmqIntegrationBinding` Se používá ke komunikaci s tradiční aplikacím služby MSMQ. K usnadnění vzájemná spolupráce pomocí stávající aplikaci služby MSMQ, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podporuje pouze formátu název adresy. Proto musí odpovídat zprávy odeslané používá tuto vazbu schéma identifikátoru URI:  
  
 MSMQ.formatname:\<*název formátu MSMQ*>>  
  
 Název formátu MSMQ je ve formátu zadaný službou MSMQ v [o služby Řízení front zpráv](http://go.microsoft.com/fwlink/?LinkId=94837).  
  
 Všimněte si, že můžete použít pouze formátované názvy a názvy ve formátu veřejné a privátní (vyžaduje integrace služby Active Directory) při přijímání zpráv z fronty pomocí `MsmqIntegrationBinding`. Doporučujeme však používat názvy v přímém formátu. Například na [!INCLUDE[wv](../../../../includes/wv-md.md)], pomocí jiných názvu formátu způsobuje chybu, protože se systém pokusí otevřít dílčí fronta, který lze otevřít pouze pomocí přímého názvu formátu.  
  
 Při zadávání adresy pomocí SRMP `MsmqIntegrationBinding`, není potřeba, chcete-li přidat /msmq/ v přímém formátu názvu usnadní odeslání Internetové informační služby (IIS). Příklad: při adresování fronty abc pomocí SRMP protokolu místo přímé = http://adatum.com/msmq/private$ / abc, měli byste použít přímo = http://adatum.com/private$ / abc.  
  
 Všimněte si, že nemůžete použít net.msmq:// adresování s `MsmqIntegrationBinding`. Protože `MsmqIntegrationBinding` podporuje vlastní MSMQ formát název adresy, můžete použít [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] službu, která používá tuto vazbu funkce vícesměrového vysílání a distribučního seznamu používat služby MSMQ. Jedinou výjimkou je zadání `CustomDeadLetterQueue` při použití `MsmqIntegrationBinding`. Musí být typu net.msmq:// formuláře, podobně jako na to, jak je zadán pomocí `NetMsmqBinding`.  
  
## <a name="see-also"></a>Viz také  
 [Webhosting Frontové aplikace](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
