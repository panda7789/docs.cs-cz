---
title: Doporučené postupy pro komunikaci ve frontě
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], best practices
- best practices [WCF], queued communication
ms.assetid: 446a6383-cae3-4338-b193-a33c14a49948
ms.openlocfilehash: 03b2366f531c0a7f8fd296ee2a685c38fd62ca82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54719817"
---
# <a name="best-practices-for-queued-communication"></a>Doporučené postupy pro komunikaci ve frontě
Toto téma obsahuje doporučené postupy pro komunikaci ve frontě ve Windows Communication Foundation (WCF). Následující části popisují doporučené postupy z hlediska scénář.  
  
## <a name="fast-best-effort-queued-messaging"></a>Rychlé a Best Effort zařazených do fronty zasílání zpráv  
 Pro scénáře, které vyžadují poskytuje oddělení, který zařazených do fronty zasílání zpráv a rychlé, vysoce výkonné zasílání zpráv s záruky best effort, použijte netransakční fronta a nastavte <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> vlastnost `false`.  
  
 Kromě toho můžete rozhodnete vám být naúčtovány náklady zápisu disku tak, že nastavíte <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> vlastnost `false`.  
  
 Zabezpečení má vliv na výkon. Další informace najdete v tématu [faktory ovlivňující výkon](../../../../docs/framework/wcf/feature-details/performance-considerations.md).  
  
## <a name="reliable-end-to-end-queued-messaging"></a>Spolehlivé začátku do konce zasílání zpráv zařazených do fronty.  
 Následující části popisují doporučené postupy pro scénáře, které vyžadují začátku do konce spolehlivé zasílání zpráv.  
  
### <a name="basic-reliable-transfer"></a>Základní spolehlivé přenosu  
 Spolehlivost začátku do konce, nastavte <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> vlastnost `true` k zajištění přenosu. <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> Nastavenou na `true` nebo `false` v závislosti na vašich požadavcích (výchozí hodnota je `true`). Obecně platí <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> je nastavena na `true` jako součást spolehlivost začátku do konce. Ohrožení snížení výkonu, ale umožňuje trvalý zprávu tak, aby zpráva nedojde ke ztrátě, pokud dojde k chybě správce fronty.  
  
### <a name="use-of-transactions"></a>Použití transakcí  
 Transakce je nutné použít k zajištění spolehlivosti začátku do konce. `ExactlyOnce` záruky pouze ujistěte se, že se zprávy doručovaly do cílové fronty. Aby bylo zajištěno, že doručení zprávy, použijte transakce. Bez transakcí Pokud dojde k chybě služby, ztratíte zprávu, která je distribuována, ale ve skutečnosti se doručí do aplikace.  
  
### <a name="use-of-dead-letter-queues"></a>Použití fronty nedoručených zpráv  
 Fronty nedoručených zpráv – Ujistěte se, že budete upozorněni, pokud se nepodaří doručit do cílové fronty zprávu. Můžete použít fronty nedoručených zpráv poskytované systémem nebo vlastní frontu nedoručených zpráv. Obecně platí používat vlastní frontu nedoručených zpráv je nejvhodnější vzhledem k tomu, že se vám umožní odesílat nedoručené zprávy z jedné aplikace do jediné fronty nedoručených zpráv. V opačném případě jsou všechny nedoručených zpráv, ke kterým dochází pro všechny aplikace spuštěné v systému poskytována do jediné fronty. Každá aplikace musí vyhledejte ale fronty nedoručených zpráv nedoručených zpráv, které jsou relevantní pro danou aplikaci najít. V některých případech použití vlastní frontu nedoručených zpráv není vhodná, například při použití služby MSMQ 3.0.  
  
 Vypnutí fronty nedoručených zpráv pro komunikaci spolehlivé začátku do konce se nedoporučuje.  
  
 Další informace najdete v tématu [pomocí fronty nedoručených zpráv pro zpracování selhání přenosu zpráv](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).  
  
### <a name="use-of-poison-message-handling"></a>Používání zpracování Poison – zpráva  
 Zpracování zpráv Poison poskytuje možnost obnovení po selhání zpracování zpráv.  
  
 Pokud používáte funkci zpracování zpráv poison, ujistěte se, že <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> je nastavena na odpovídající hodnotu. Nastavení na <xref:System.ServiceModel.ReceiveErrorHandling.Drop> znamená, že data budou ztracena. Na druhé straně ji nastavíte na <xref:System.ServiceModel.ReceiveErrorHandling.Fault> chyb stránkování hostitele služby, když zjistí počet nezpracovatelných zpráv. Použití služby MSMQ 3.0 <xref:System.ServiceModel.ReceiveErrorHandling.Fault> je nejlepší možnost nedošlo ke ztrátě dat a eliminuje přesunout nezpracovatelných zpráv. Pomocí služby MSMQ 4.0 <xref:System.ServiceModel.ReceiveErrorHandling.Move> je doporučený postup. <xref:System.ServiceModel.ReceiveErrorHandling.Move> Přesune poškozená po zprávy z fronty tak, aby služba můžou dál zpracovávat nové zprávy. Služba poison zpráv můžete následně zpracovat nezpracovatelná zpráva samostatně.  
  
 Další informace najdete v tématu [zpracování škodlivých zpráv](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
## <a name="achieving-high-throughput"></a>Dosahuje vysoké propustnosti  
 K dosažení vysoké propustnosti na jeden koncový bod, použijte následující:  
  
-   Transakční dávkování. Provedené dávkování zajistí, že počet zpráv najdete v rámci jedné transakce. Tím se optimalizují potvrzení transakcí, zvýšit celkový výkon. Náklady na dávkování je, že pokud dojde k selhání jedné zprávy v rámci služby batch, pak celý batch se vrátí zpět a zprávy musí být zpracované jeden po druhém, dokud je bezpečné batch znovu. Ve většině případů jsou vzácné, počet nezpracovatelných zpráv, takže dávkování je preferovaný způsob, jak zvýšit výkon systému, zejména v případě, že máte ostatní správci prostředků, které jsou součástí transakce. Další informace najdete v tématu [dávkování zpráv v transakci](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md).  
  
-   Souběžnost. Souběžnost zvyšuje propustnost, ale souběžnost ovlivňuje také kolize ke sdíleným prostředkům. Další informace najdete v tématu [souběžnosti](../../../../docs/framework/wcf/samples/concurrency.md).  
  
-   Omezení šířky pásma. Pro zajištění optimálního výkonu omezte počet zpráv v dispečeru kanálu. Příklad toho, jak to provést, najdete v části [omezování](../../../../docs/framework/wcf/samples/throttling.md).  
  
 Při použití dávkování, mějte na paměti, že omezování a souběžnosti přeložit do souběžných listů.  
  
 K dosažení vyšší propustnost a dostupnost, použijte farmu služby WCF, které načítají z fronty. To vyžaduje, aby všechny tyto služby vystavit stejný kontrakt na stejný koncový bod. Farma přístup je nejvhodnější pro aplikace, které mají vysokou produkční sazby zpráv, protože umožňuje použít řadu služeb pro všechny číst ze stejné fronty.  
  
 Při použití farmy, mějte na paměti, že služba MSMQ 3.0 nepodporuje vzdálené transakční operace čtení. MSMQ 4.0 podporuje vzdálené transakční operace čtení.  
  
 Další informace najdete v tématu [dávkování zpráv v transakci](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md) a [rozdíly ve funkcích služby Řízení front ve Windows Vista, Windows Server 2003 a Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).  
  
## <a name="queuing-with-unit-of-work-semantics"></a>S jednotkou práce sémantiku řízení front  
 V některých scénářích může souviset skupinu zpráv do fronty, a proto je důležité pořadí těchto zpráv. V takových scénářích zpracovat skupinu související zprávy společně jako jednu jednotku: všechny zprávy úspěšně zpracovat nebo žádný není. K implementaci takové chování, použijte relace s frontami.  
  
 Další informace najdete v tématu [seskupování zpráv zařazených do fronty v relaci](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md).  
  
## <a name="correlating-request-reply-messages"></a>Korelace zprávy požadavek odpověď  
 I když fronty jsou obvykle jednosměrné, v některých scénářích možná budete chtít korelaci odpovědi přijaté žádosti zaslané dříve. Pokud budete potřebovat tato korelace, doporučuje se, že použijete vlastní záhlaví zprávy protokolu SOAP, která obsahuje informace pro korelaci s touto zprávou. Obvykle odesílatel připojí tato hlavička se zprávou a příjemce při zpracování zprávy a odpověď zpět s novou zprávu do fronty odpovědí připojí odesílatele hlavičky, který obsahuje informace pro korelaci, mohli odesílatele Identifikujte zprávy s odpovědí se zprávy s požadavkem.  
  
## <a name="integrating-with-non-wcf-applications"></a>Integrace s aplikacemi bez WCF  
 Použití `MsmqIntegrationBinding` při integraci služby WCF nebo klienty pomocí jiných WCF služby nebo klientů. Aplikace bez WCF může být MSMQ aplikace napsané s využitím System.Messaging, modelu COM +, Visual Basic nebo C++.  
  
 Při použití `MsmqIntegrationBinding`, mějte na paměti z následujících akcí:  
  
-   Tělo zprávy WCF není stejný jako text zprávy služby MSMQ. Při odesílání zprávy WCF pomocí vazbu s frontou, text zprávy WCF je umístěn uvnitř zprávy služby MSMQ. Infrastruktura služby MSMQ je oblivious tyto dodatečné informace, ji uvidí jen zprávy služby MSMQ.  
  
-   `MsmqIntegrationBinding` podporuje typy oblíbených serializace. Na základě serializace typu, typ těla obecná zpráva <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, parametry jiného typu. Například <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.ByteArray> vyžaduje `MsmqMessage\<byte[]>` a <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.Stream> vyžaduje `MsmqMessage<Stream>`.  
  
-   K serializaci kódu XML, můžete zadat pomocí známého typu `KnownTypes` atribut na [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element, který se pak použije k určení, jak zrušit serializaci zpráv XML.  
  
## <a name="see-also"></a>Viz také:
- [Zařazování do front ve WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [Postupy: Výměna zpráv zařazených do fronty pomocí koncových bodů WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Postupy: Výměna zpráv pomocí koncových bodů WCF a aplikací služby Řízení front zpráv](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [Seskupování zpráv zařazených do fronty v relaci](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)
- [Dávkování zpráv v transakci](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)
- [Zpracování chyb přenosu zpráv pomocí front nedoručených zpráv](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)
- [Zpracování škodlivých zpráv](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
- [Rozdíly ve funkcích zařazování do front ve Windows Vista, Windows Serveru 2003 a Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)
- [Zabezpečení zpráv pomocí zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)
- [Zabezpečení zpráv](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)
- [Řešení problémů se zasíláním zpráv zařazovaných do front](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)
