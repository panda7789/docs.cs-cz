---
title: Zpracování chyb přenosu zpráv pomocí front nedoručených zpráv
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9e891c6a-d960-45ea-904f-1a00e202d61a
ms.openlocfilehash: 0be22fa1e81c85d82494bc4b93468a18f05d6423
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345562"
---
# <a name="using-dead-letter-queues-to-handle-message-transfer-failures"></a>Zpracování chyb přenosu zpráv pomocí front nedoručených zpráv
Zprávy ve frontě můžou neúspěšné doručení. Tyto neúspěšné zprávy se zaznamenávají do fronty nedoručených zpráv. Neúspěšné doručení může být způsobeno důvody, například selhání sítě, odstraněnou frontou, úplnou frontou, selháním ověřování nebo selháním doručení včas.  
  
 Zprávy zařazené do fronty mohou zůstat ve frontě delší dobu, pokud přijímající aplikace je nečte z fronty včas. Toto chování nemusí být vhodné pro zprávy citlivé na čas. Zprávy s časovým rozlišením mají nastavenou vlastnost TTL (Time to Live) ve frontě, která určuje, jak dlouho mohou být zprávy ve frontě, než musí vypršet jejich platnost. Zprávy s vypršenou platností se odesílají do speciální fronty označované jako fronta nedoručených zpráv. Zprávy je také možné umístit do fronty nedoručených zpráv z jiných důvodů, jako je například překročení kvóty fronty nebo selhání ověřování.  
  
 Obecně platí, že aplikace zapisuje kompenzační logiku ke čtení zpráv z front nedoručených zpráv a z důvodů selhání. Logika kompenzace závisí na příčině selhání. V případě selhání ověřování můžete například opravit certifikát připojený ke zprávě a znovu odeslat zprávu. Pokud se doručení nepovedlo, protože byla dosažena kvóta cílové fronty, můžete se pokusit o doručení znovu při vyřešení problému s kvótou.  
  
 Většina systémů pro zařazování do fronty má frontu nedoručených zpráv v celém systému, kde jsou uložené všechny neúspěšné zprávy z tohoto systému. Služba Řízení front zpráv (MSMQ) poskytuje dvě fronty nedoručených zpráv v rámci systému: transakční fronta nedoručených zpráv v systému, která ukládá zprávy, které selhaly při doručování do transakční fronty, a netransakční fronta nedoručených zpráv v systému, která ukládá zprávy, které selhaly při doručování do netransakční fronty. Pokud dva klienti odesílají zprávy do dvou různých služeb, a proto různé fronty ve službě WCF sdílejí stejnou službu MSMQ, aby se odesílaly, pak je možné mít kombinaci zpráv ve frontě nedoručených písmen systému. To není vždy optimální. V několika případech (například zabezpečení) možná nebudete chtít, aby jeden klient načetl zprávy jiného klienta z fronty nedoručených zpráv. Sdílená fronta nedoručených zpráv také vyžaduje, aby klienti procházeli frontu a našli zprávu, kterou odeslali, což může být zakazovatelné na základě počtu zpráv ve frontě nedoručených zpráv. Proto ve službě WCF`NetMsmqBinding``MsmqIntegrationBinding,` a MSMQ v systému Windows Vista zadejte vlastní frontu nedoručených zpráv (někdy označovanou jako fronta nedoručených zpráv specifické pro aplikaci).  
  
 Vlastní fronta nedoručených zpráv poskytuje izolaci mezi klienty, kteří sdílejí stejnou službu MSMQ a odesílají zprávy.  
  
 V systému Windows Server 2003 a [!INCLUDE[wxp](../../../../includes/wxp-md.md)]Windows Communication Foundation (WCF) poskytuje frontu nedoručených zpráv v celém systému pro všechny klientské aplikace ve frontě. V systému Windows Vista nabízí služba WCF nedoručenou frontu pro každou klientskou aplikaci ve frontě.  
  
## <a name="specifying-use-of-the-dead-letter-queue"></a>Určení použití fronty nedoručených zpráv  
 Fronta nedoručených zpráv je ve Správci fronty odesílající aplikace. Ukládá zprávy, jejichž platnost vypršela, nebo se nezdařil přenos nebo doručení.  
  
 Vazba má následující vlastnosti fronty nedoručených zpráv:  
  
- <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>  
  
- <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>  
  
## <a name="reading-messages-from-the-dead-letter-queue"></a>Načítají se zprávy z fronty nedoručených zpráv.  
 Aplikace, která čte zprávy z fronty nedoručených zpráv, je podobná službě WCF, která čte z fronty aplikace, s výjimkou následujících menších rozdílů:  
  
- Chcete-li číst zprávy z fronty nedoručených zpráv transakčního systému, musí být identifikátor URI (Uniform Resource Identifier) ve tvaru: NET. MSMQ://localhost/System $;D eadXact.  
  
- Chcete-li číst zprávy z netransakční fronty nedoručených zpráv, identifikátor URI musí být ve tvaru: NET. MSMQ://localhost/System $;D eadLetter.  
  
- Chcete-li číst zprávy z vlastní fronty nedoručených zpráv, identifikátor URI musí být ve tvaru: NET. MSMQ://localhost/Private/\<*Custom-DLQ-name*>, kde *Custom-DLQ-Name* je název vlastní fronty nedoručených zpráv.  
  
 Další informace o tom, jak adresovat fronty, najdete v tématu [koncové body služby a adresování front](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
 Zásobník WCF na přijímači odpovídá adresám, na kterých služba naslouchá, pomocí adresy ve zprávě. Pokud se adresy shodují, zpráva se odešle. v takovém případě není zpráva odeslána. To může způsobit problémy při čtení z fronty nedoručených zpráv, protože zprávy ve frontě nedoručených zpráv jsou obvykle adresovány službě a nikoli službě fronty nedoručených zpráv. Proto služba, která je čtena z fronty nedoručených zpráv, musí nainstalovat filtr adres `ServiceBehavior`, který nastaví zásobník tak, aby odpovídal všem zprávám ve frontě nezávisle na adresátovi. Konkrétně je potřeba přidat `ServiceBehavior` s parametrem <xref:System.ServiceModel.AddressFilterMode.Any> ke službě, která čte zprávy z fronty nedoručených zpráv.  
  
## <a name="poison-message-handling-from-the-dead-letter-queue"></a>Zpracování nezpracovatelných zpráv z fronty nedoručených zpráv  
 Zpracování poškozených zpráv je k dispozici ve frontách nedoručených zpráv s některými podmínkami. Vzhledem k tomu, že při čtení z fronty nedoručených zpráv systému nelze vytvořit podfronty ze systémových front, `ReceiveErrorHandling` nelze nastavit na `Move`. Všimněte si, že pokud čtete z vlastní fronty nedoručených zpráv, můžete mít podfronty, a proto je `Move` platnou dispozici pro nezpracovatelnou zprávu.  
  
 Když je `ReceiveErrorHandling` nastavená na `Reject`, při čtení z vlastní fronty nedoručených zpráv se nezpracovatelná zpráva vloží do fronty nedoručených zpráv systému. Při čtení z fronty nedoručených zpráv systému je zpráva vyřazena (vyprázdněna). Odmítnutí z fronty nedoručených zpráv systému v MSMQ vyřazuje (vyprázdní) zprávu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit frontu nedoručených zpráv a jak ji použít ke zpracování zpráv s vypršenou platností. Příklad je založen na příkladu v tématu [Postupy: Výměna zpráv zařazených do fronty pomocí koncových bodů WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md). Následující příklad ukazuje, jak napsat kód klienta do služby zpracování objednávek, která používá frontu nedoručených zpráv pro každou aplikaci. Tento příklad také ukazuje, jak zpracovávat zprávy z fronty nedoručených zpráv.  
  
 Následuje kód pro klienta, který určuje frontu nedoručených zpráv pro každou aplikaci.  
  
 [!code-csharp[S_DeadLetter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/client.cs#1)]
 [!code-vb[S_DeadLetter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/client.vb#1)]  
  
 Následuje kód pro konfigurační soubor klienta.  

 Následuje kód pro zprávy zpracovávající služby z fronty nedoručených zpráv.  
  
 [!code-csharp[S_DeadLetter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/dlservice.cs#3)]
 [!code-vb[S_DeadLetter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/dlservice.vb#3)]  
  
 Následuje kód pro konfigurační soubor služby fronta nedoručených zpráv.  

## <a name="see-also"></a>Viz také:

- [Přehled front](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Postupy: Výměna zpráv zařazených do fronty s koncovými body WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Zpracování škodlivých zpráv](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
