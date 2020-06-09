---
title: Doporučené postupy pro komunikaci ve frontě
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], best practices
- best practices [WCF], queued communication
ms.assetid: 446a6383-cae3-4338-b193-a33c14a49948
ms.openlocfilehash: af9ed7d64a60042297e071262be7610c4d791a51
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601345"
---
# <a name="best-practices-for-queued-communication"></a>Doporučené postupy pro komunikaci ve frontě
Toto téma popisuje doporučené postupy pro komunikaci ve frontě v Windows Communication Foundation (WCF). Následující části popisují doporučené postupy z perspektivy scénáře.  
  
## <a name="fast-best-effort-queued-messaging"></a>Rychlé a nejlepší úsilí pro zasílání zpráv ve frontě  
 Pro scénáře, které vyžadují oddělení zasílání zpráv ve frontě, poskytuje kvalitní a vysoce výkonné zasílání zpráv s osvědčenými zárukami, použijte netransakční frontu a nastavte <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> vlastnost na `false` .  
  
 Kromě toho se můžete rozhodnout neúčtovat náklady na zápisy na disk nastavením <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> vlastnosti na `false` .  
  
 Zabezpečení má vliv na výkon. Další informace najdete v tématu věnovaném [důležitým informacím o výkonu](performance-considerations.md).  
  
## <a name="reliable-end-to-end-queued-messaging"></a>Spolehlivě kompletní zasílání zpráv ve frontě  
 Následující části popisují doporučené postupy pro scénáře, které vyžadují komplexní spolehlivé zasílání zpráv.  
  
### <a name="basic-reliable-transfer"></a>Základní spolehlivý přenos  
 Pro komplexní spolehlivost nastavte <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> vlastnost na, aby `true` se zajistil přenos. <xref:System.ServiceModel.MsmqBindingBase.Durable%2A>Vlastnost může být nastavena na `true` nebo `false` v závislosti na vašich požadavcích (výchozí nastavení je `true` ). Obecně se tato <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> vlastnost nastavuje `true` jako součást komplexní spolehlivosti. Ohrožení zabezpečení je náklady na výkon, ale zpráva je odolná, takže pokud správce fronty selže, zpráva nebude ztracena.  
  
### <a name="use-of-transactions"></a>Použití transakcí  
 Aby byla zajištěna komplexní spolehlivost, je nutné použít transakce. `ExactlyOnce`záruky zajišťují, že se zprávy doručí do cílové fronty. Chcete-li zajistit, aby byla zpráva přijata, použijte transakce. Bez transakcí, pokud dojde k chybě služby, ztratíte zprávu, která se doručuje, ale ve skutečnosti se doručí do aplikace.  
  
### <a name="use-of-dead-letter-queues"></a>Použití front nedoručených zpráv  
 Fronty nedoručených zpráv zajišťují, že budete upozorněni na to, jestli se zpráva nepovede doručit do cílové fronty. Můžete použít frontu nedoručených zpráv poskytnutou systémem nebo vlastní frontu nedoručených zpráv. Obecně platí, že použití vlastní fronty nedoručených zpráv je nejlepší, protože umožňuje posílání nedoručených zpráv z jedné aplikace do jediné fronty nedoručených zpráv. Jinak budou všechny nedoručené zprávy, ke kterým dochází pro všechny aplikace běžící v systému, doručovány do jediné fronty. Každá aplikace musí potom vyhledat zprávy nedoručených zpráv, které jsou relevantní pro danou aplikaci, ve frontě nedoručených zpráv. V některých případech není možné používat vlastní frontu nedoručených zpráv, například při použití služby MSMQ 3,0.  
  
 Vypnutí front nedoručených zpráv pro ucelenou spolehlivou komunikaci se nedoporučuje.  
  
 Další informace najdete v tématu [použití front nedoručených zpráv pro zpracování selhání přenosu zpráv](using-dead-letter-queues-to-handle-message-transfer-failures.md).  
  
### <a name="use-of-poison-message-handling"></a>Použití zpracování nepoškozených zpráv  
 Manipulace s neoprávněnými zprávami poskytuje možnost zotavení po selhání zpracování zpráv.  
  
 Při použití funkce pro zpracování nezpracovatelných zpráv se ujistěte, že <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> je vlastnost nastavena na odpovídající hodnotu. Nastavením této možnosti <xref:System.ServiceModel.ReceiveErrorHandling.Drop> znamená, že dojde ke ztrátě dat. Na druhé straně nastavíte tak, aby <xref:System.ServiceModel.ReceiveErrorHandling.Fault> při zjištění poškozené zprávy nedošlo k chybě hostitele služby. Při použití služby MSMQ 3,0 <xref:System.ServiceModel.ReceiveErrorHandling.Fault> je nejlepší volbou, jak zabránit ztrátě dat a přesunout neškodnou zprávu ze způsobů. <xref:System.ServiceModel.ReceiveErrorHandling.Move>Doporučený postup je použití služby MSMQ 4,0. <xref:System.ServiceModel.ReceiveErrorHandling.Move>Přesune nepoškozenou zprávu z fronty, aby mohla služba nadále zpracovávat nové zprávy. Služba nezpracovatelná zpráva pak může zpracovat nezpracovatelovou zprávu samostatně.  
  
 Další informace naleznete v tématu [manipulace s Nezpracovatelovou zprávou](poison-message-handling.md).  
  
## <a name="achieving-high-throughput"></a>Dosažení vysoké propustnosti  
 K dosažení vysoké propustnosti jednoho koncového bodu použijte následující:  
  
- Vytransakční dávkování. Transakční dávkování zajišťuje, aby bylo možné číst mnoho zpráv v rámci jedné transakce. Tato operace optimalizuje potvrzení transakcí a zvyšuje celkový výkon. Náklady na dávkování znamená, že pokud dojde k selhání v jedné zprávě v rámci dávky, pak se celá dávka vrátí zpátky a zprávy se musí zpracovat po jednom, dokud nebude možné znovu spustit dávku. Ve většině případů jsou nefunkční zprávy zřídka, takže dávkování je preferovaným způsobem, jak zvýšit výkon systému, zejména v případě, že máte jiné správce prostředků, kteří se účastní transakce. Další informace najdete v tématu [dávkové zpracování zpráv v transakci](batching-messages-in-a-transaction.md).  
  
- Concurrency. Souběžnost zvyšuje propustnost, ale souběžnost ovlivňuje také obsah sdílených prostředků. Další informace najdete v tématu [souběžnost](../samples/concurrency.md).  
  
- Omezování. Pro zajištění optimálního výkonu omezte počet zpráv v kanálu dispečera. Příklad toho, jak to udělat, najdete v tématu [omezování](../samples/throttling.md).  
  
 Při použití dávkového zpracování Pamatujte na to, že převod souběžnosti a omezování omezuje na souběžné dávky.  
  
 Abyste dosáhli vyšší propustnosti a dostupnosti, použijte farmu služeb WCF, které se čtou z fronty. To vyžaduje, aby všechny tyto služby zveřejnily stejný kontrakt na stejném koncovém bodu. Přístup k farmě funguje nejlépe pro aplikace s vysokými provozními sazbami zpráv, protože umožňuje několika službám čtení ze stejné fronty.  
  
 Při použití farmy mějte na paměti, že MSMQ 3,0 nepodporuje vzdálené čtení v transakčním režimu. Služba MSMQ 4,0 podporuje vzdálené čtení v transakčním režimu.  
  
 Další informace najdete v tématu [dávkové zpracování zpráv v transakcích](batching-messages-in-a-transaction.md) a [rozdílech ve funkcích služby Řízení front v systému Windows Vista, Windows Server 2003 a Windows XP](diff-in-queue-in-vista-server-2003-windows-xp.md).  
  
## <a name="queuing-with-unit-of-work-semantics"></a>Zařazení do fronty s sémantikou pracovní jednotky  
 V některých scénářích může být skupina zpráv ve frontě spojená a proto je pořadí těchto zpráv významné. V takových scénářích zpracujte skupinu souvisejících zpráv jako jednu jednotku: obě zprávy se úspěšně zpracovávají nebo žádné nejsou. K implementaci takového chování použijte relace s frontami.  
  
 Další informace najdete v tématu [seskupování zpráv zařazených do fronty v relaci](grouping-queued-messages-in-a-session.md).  
  
## <a name="correlating-request-reply-messages"></a>Korelace zpráv požadavku a odpovědi  
 I když jsou fronty obvykle jednosměrné, v některých případech můžete chtít korelovat odpověď přijatou k žádosti odeslané dříve. Pokud požadujete takovou korelaci, doporučujeme, abyste použili vlastní hlavičku zprávy SOAP, která obsahuje informace o korelaci se zprávou. Odesílatel obvykle připojí tuto hlavičku k této zprávě a příjemcem při zpracování zprávy a odpovědi zpět na novou zprávu ve frontě odpovědí připojí hlavičku zprávy odesílatele, která obsahuje informace o korelaci, aby odesilatel mohl identifikovat zprávu odpovědi s požadavkem na zprávu.  
  
## <a name="integrating-with-non-wcf-applications"></a>Integrace s aplikacemi nepodporujícími technologii WCF  
 Použijte `MsmqIntegrationBinding` při integraci služeb WCF nebo klientů se službami nebo klienty, kteří nejsou WCF. Aplikace jiného typu než WCF může být aplikace služby MSMQ napsaná pomocí System. Messaging, COM+, Visual Basic nebo C++.  
  
 Při použití nástroje `MsmqIntegrationBinding` mějte na paměti následující skutečnosti:  
  
- Tělo zprávy WCF není stejné jako tělo zprávy služby MSMQ. Při odesílání zprávy WCF pomocí vazby zařazené do fronty je text zprávy WCF umístěný uvnitř zprávy služby MSMQ. Infrastruktura služby MSMQ se oblivious na tyto dodatečné informace; uvidí jenom zprávu služby MSMQ.  
  
- `MsmqIntegrationBinding`podporuje oblíbené typy serializace. Na základě typu serializace typ textu obecné zprávy, <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> , používá jiné parametry typu. Například <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.ByteArray> vyžaduje `MsmqMessage\<byte[]>` a <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.Stream> vyžaduje `MsmqMessage<Stream>` .  
  
- Pomocí serializace XML lze určit známý typ pomocí `KnownTypes` atributu u [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) prvku, který je poté použit k určení, jak se má zpráva XML deserializovat.  
  
## <a name="see-also"></a>Viz také

- [Fronty ve WCF](queuing-in-wcf.md)
- [Postupy: Výměna zpráv zařazených do fronty s koncovými body WCF](how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Postupy: Výměna zpráv s koncovými body WCF a aplikací pro řazení zpráv do front](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [Seskupování zpráv zařazených do fronty v relaci](grouping-queued-messages-in-a-session.md)
- [Dávkování zpráv v transakci](batching-messages-in-a-transaction.md)
- [Zpracování chyb přenosu zpráv pomocí front nedoručených zpráv](using-dead-letter-queues-to-handle-message-transfer-failures.md)
- [Zpracování škodlivých zpráv](poison-message-handling.md)
- [Rozdíly ve funkcích zařazování do front ve Windows Vista, Windows Serveru 2003 a Windows XP](diff-in-queue-in-vista-server-2003-windows-xp.md)
- [Zabezpečení zpráv pomocí zabezpečení přenosu](securing-messages-using-transport-security.md)
- [Zabezpečení zpráv](securing-messages-using-message-security.md)
- [Řešení potíží se zasíláním zpráv zařazovaných do front](troubleshooting-queued-messaging.md)
