---
title: Zpracování chyb přenosu zpráv pomocí front nedoručených zpráv
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9e891c6a-d960-45ea-904f-1a00e202d61a
ms.openlocfilehash: c83d48994c6038dfde67867a1766777c479c2169
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64637736"
---
# <a name="using-dead-letter-queues-to-handle-message-transfer-failures"></a>Zpracování chyb přenosu zpráv pomocí front nedoručených zpráv
Zprávy ve frontě může selhat doručování. Tyto zprávy se nezdařilo se zaznamenávají do fronty nedoručených zpráv. Selhání doručení může být způsobeno důvodů, jako je například selhání sítě, frontu odstranil, plné frontě, ověřování se nezdařilo nebo selhání na včasném poskytnutí výsledků.  
  
 Zprávy ve frontě může zůstat ve frontě po dlouhou dobu, pokud přijímající aplikace nenačítá je z fronty včas. Toto chování nemusí být vhodný pro zprávy s časovým počitadlem. Časově zprávy dostatek času k Live (TTL) nastavenou ve vazbě zařazených do fronty, který ukazuje, jak dlouho zprávy může být ve frontě předtím, než vyprší. Zprávy s vypršenou platností se odesílají do speciální fronty s názvem fronty nedoručených zpráv. Zprávy mohou také vložit do fronty nedoručených zpráv z jiných důvodů, jako je například překročení kvóty fronty nebo kvůli chybě ověřování.  
  
 Obecně platí aplikace zapisovat kompenzační logiky ke čtení zpráv z fronty nedoručených zpráv a důvody selhání. Kompenzační logika závisí na příčinu selhání. Například v případě selhání ověření můžete opravit certifikát připojený se zprávou a znovu odeslat zprávu. Pokud doručení se nezdařilo, protože bylo dosaženo kvóty cílové fronty, zkuste znovu provést přenos v naději, že byl vyřešen problém kvóty.  
  
 Většina zařazování do fronty systémy mají fronty nedoručených zpráv systémová ukládat všechny neúspěšné zprávy z tohoto systému. Řízení front zpráv (MSMQ) poskytuje dvě fronty nedoručených zpráv systémová: transakční frontu nedoručených zpráv celý systém, který ukládá zprávy, které se nepodařilo doručování transakční fronty a netransakční fronta nedoručených celý systém, který ukládá zprávy, které se nepodařilo doručování netransakční fronta. Pokud jsou dva klienti odesílání zpráv do dvou různých služeb, a proto různé fronty ve WCF sdílejí stejnou službu MSMQ pro odeslání, je možné mít kombinaci zprávy ve frontě nedoručených zpráv systému. To není vždycky optimální. V několika případech (například zabezpečení) možná nebudete chtít jednoho klienta číst jiného klienta zprávy z fronty nedoručených zpráv. Sdílené fronty nedoručených zpráv také vyžaduje, aby klienti procházením najít zprávu, která se odesílá, což může být nepřekonatelně drahé na základě počtu zpráv ve frontě nedoručených zpráv do fronty. Proto se ve službě WCF`NetMsmqBinding`, `MsmqIntegrationBinding,` a MSMQ na [!INCLUDE[wv](../../../../includes/wv-md.md)] poskytnout vlastní frontu nedoručených zpráv (někdy označované jako do fronty nedoručených zpráv specifické pro aplikaci).  
  
 Vlastní frontu nedoručených zpráv zajišťuje izolaci mezi klienty, které sdílejí stejné služby MSMQ pro odesílání zpráv.  
  
 Na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)], Windows Communication Foundation (WCF) poskytuje frontu nedoručených zpráv systémová pro všechny ve frontě klientské aplikace. Na [!INCLUDE[wv](../../../../includes/wv-md.md)], WCF poskytuje fronty nedoručených zpráv pro každou aplikaci ve frontě klienta.  
  
## <a name="specifying-use-of-the-dead-letter-queue"></a>Určení použití fronty nedoručených zpráv  
 Fronty nedoručených zpráv je ve správci fronty odesílací aplikace. Ukládá zprávy, jejichž platnost vypršela nebo které selhaly, přenos nebo doručení.  
  
 Vazba má následující vlastnosti fronty nedoručených zpráv:  
  
- <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>  
  
- <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>  
  
## <a name="reading-messages-from-the-dead-letter-queue"></a>Přečte zprávy z fronty nedoručených zpráv  
 Aplikace, která čte zprávy z fronty nedoručených zpráv je podobný služby WCF, která čte z fronty služby aplikace, s výjimkou následujících drobné rozdíly:  
  
- Ke čtení zpráv z fronty nedoručených zpráv transakcí systému, identifikátor URI (Uniform Resource) musí být ve tvaru: net.msmq://localhost/system$; DeadXact.  
  
- Ke čtení zpráv ze systému netransakční fronta nedoručených zpráv, identifikátor URI musí být ve tvaru: net.msmq://localhost/system$; nedoručených zpráv.  
  
- Ke čtení zpráv z vlastní frontu nedoručených zpráv, musí být identifikátor URI formuláře: net.msmq://localhost/private/\<*Vlastní DLQ se názvy*> kde *Vlastní DLQ se názvy* je název nástroje custom fronty nedoručených zpráv.  
  
 Další informace o tom, jak adresa fronty, naleznete v tématu [koncové body služby a adresování front](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
 Zásobník WCF na straně příjmu odpovídá adresy, které služba naslouchá na adresu ve zprávě. Pokud se adresy shodují, je zpráva odeslána; v opačném případě není zpráva odeslána. To může způsobovat problémy při čtení z fronty nedoručených zpráv, protože zprávy ve frontě nedoručených zpráv se obvykle tak vyřeší, služby a nikoli služba fronty nedoručených zpráv. Proto se čtením z fronty nedoručených zpráv služby musíte nainstalovat filtr adresy `ServiceBehavior` , který dává pokyn zásobníku tak, aby odpovídaly všechny zprávy ve frontě bez ohledu na jejich příjemce. Konkrétně je nutné přidat `ServiceBehavior` s <xref:System.ServiceModel.AddressFilterMode.Any> parametr ke službě přečte zprávy z fronty nedoručených zpráv.  
  
## <a name="poison-message-handling-from-the-dead-letter-queue"></a>Zacházení s nezpracovatelnými zprávami z fronty nedoručených zpráv  
 Je k dispozici ve frontách nedoručených zpráv, se některé podmínky manipulaci s nezpracovatelnými zprávami. Protože nelze vytvořit dílčí fronty ze systémové fronty, při čtení z fronty nedoručených zpráv systému `ReceiveErrorHandling` nelze nastavit na `Move`. Všimněte si, že při čtení z vlastní frontu nedoručených zpráv, může mít dílčí fronty a tedy `Move` je platný dispozice pro nezpracovatelných zpráv.  
  
 Když `ReceiveErrorHandling` je nastavena na `Reject`, při čtení z fronty nedoručených zpráv vlastní nezpracovatelná zpráva je umístit do fronty nedoručených zpráv systému. Pokud se čtení z fronty nedoručených zpráv systému, se zahodí zprávy (odstraněný). Odmítnout z fronty nedoručených zpráv systému v drops služby MSMQ (odstraní) zprávy.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit frontu nedoručených zpráv a jak ji používat ke zpracování zprávy s vypršenou platností. V příkladu je založena na příkladu v [jak: Výměna zpráv pomocí koncových bodů WCF zařazených do fronty](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md). Následující příklad ukazuje, jak psát kód klienta pro službu, která používá fronty nedoručených zpráv pro každou aplikaci zpracování objednávek. Tento příklad také ukazuje, jak zpracovávat zprávy z fronty nedoručených zpráv.  
  
 Níže je kód pro klienta, který určuje fronty nedoručených zpráv pro každou aplikaci.  
  
 [!code-csharp[S_DeadLetter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/client.cs#1)]
 [!code-vb[S_DeadLetter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/client.vb#1)]  
  
 Níže je kód pro soubor konfigurace klienta.  

 Níže je kód služby zpracování zprávy z fronty nedoručených zpráv.  
  
 [!code-csharp[S_DeadLetter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/dlservice.cs#3)]
 [!code-vb[S_DeadLetter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/dlservice.vb#3)]  
  
 Níže je kód pro konfigurační soubor služby fronty nedoručených zpráv.  

## <a name="see-also"></a>Viz také:

- [Přehled front](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Postupy: Výměna zpráv zařazených do fronty pomocí koncových bodů WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Zpracování škodlivých zpráv](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
