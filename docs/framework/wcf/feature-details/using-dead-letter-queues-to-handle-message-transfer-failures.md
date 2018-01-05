---
title: "Zpracování chyb přenosu zpráv pomocí front nedoručených zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9e891c6a-d960-45ea-904f-1a00e202d61a
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9f10b3895fcdea0c3ab80617acd9874953b7665e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-dead-letter-queues-to-handle-message-transfer-failures"></a>Zpracování chyb přenosu zpráv pomocí front nedoručených zpráv
Zprávy ve frontě může selhat doručení. Tyto zprávy se nezdařila se zaznamenávají do fronty nedoručených zpráv. Selhání doručení může být způsobeno z důvodů, například selhání sítě, odstraněné fronty, plné frontě, selhání ověřování nebo selhání při doručení na času.  
  
 Zprávy ve frontě může zůstat ve frontě delší dobu, pokud přijímající aplikace nenačte je z fronty včas. Toto chování nemusí být vhodný pro citlivé na čas zprávy. Zprávy dobou mít dobu a vlastnost Live (TTL) nastavit vazba zařazených do fronty, který ukazuje, jak dlouho zprávy může být ve frontě než vyprší. Zprávy s vypršenou platností jsou odesílány speciální fronty s názvem frontu nedoručených zpráv. Zprávy můžete také vložit do fronty nedoručených zpráv z jiných důvodů, například překročení kvóty fronty nebo z důvodu selhání ověřování.  
  
 Obecně platí aplikace zapisovat kompenzace logiku pro čtení zpráv z fronty nedoručených zpráv a důvodech selhání. Kompenzace logiku závisí na příčinu selhání. Například můžete v případě selhání ověřování, opravte certifikát přiložený se zprávou a znovu odešlete zprávu. Pokud doručení se nezdařila, protože bylo dosaženo kvóty cílové fronty, zkuste znovu provést doručení v naděje, že kvóta problém byl vyřešen.  
  
 Většina služby Řízení front systémy mají systémové fronty nedoručených zpráv, kde jsou uložené všechny neúspěšné zprávy z tohoto systému. Poskytuje dvě systémové fronty nedoručených zpráv služby Řízení front zpráv (MSMQ): transakční frontu nedoručených zpráv systémové ukládá zprávy, které se nezdařilo doručení a netransakční frontu nedoručených zpráv systémové ukládá transakční fronty zprávy, které doručení do netransakční fronty se nezdařilo. Pokud jsou dva klientů zasílání zpráv dvě různé služby a proto různých front v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sdílejí stejné služby MSMQ k odeslání, pak je možné, že směs zprávy do fronty nedoručených zpráv systému. Toto není vždy optimální. V několika případech (například zabezpečení) nemusí chcete jednoho klienta ke čtení jiného klienta zpráv z fronty nedoručených zpráv. Sdílené frontu nedoručených zpráv taky vyžaduje klientům procházet fronty najít zprávu, která budou odeslána, může být výtažkovými na základě počtu zpráv do fronty nedoručených zpráv. Proto v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `NetMsmqBinding`, `MsmqIntegrationBinding,` a MSMQ na [!INCLUDE[wv](../../../../includes/wv-md.md)] zadejte vlastní frontu nedoručených zpráv (někdy označované jako frontu nedoručených zpráv specifické pro aplikaci).  
  
 Vlastní frontu nedoručených zpráv poskytuje izolaci mezi klienty, které sdílejí stejné služby MSMQ pro odesílání zpráv.  
  
 Na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)], [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] poskytuje systémové fronty nedoručených zpráv pro všechny aplikace ve frontě klienta. Na [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje frontu nedoručených zpráv pro každou aplikaci ve frontě klienta.  
  
## <a name="specifying-use-of-the-dead-letter-queue"></a>Zadání použití fronty nedoručených zpráv  
 Ve správci fronty odesílání aplikace je frontu nedoručených zpráv. Ukládá zprávy, jejichž platnost vypršela nebo které selhaly přenos nebo doručení.  
  
 Vazba má následující vlastnosti fronty nedoručených zpráv:  
  
-   <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>  
  
-   <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>  
  
## <a name="reading-messages-from-the-dead-letter-queue"></a>Čtení zpráv z fronty nedoručených zpráv  
 Aplikace, která čte zprávy z fronty nedoručených zpráv je podobná [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, který čte z fronty zpráv aplikace, s výjimkou následujících drobné rozdíly:  
  
-   Ke čtení zpráv z fronty nedoručených zpráv transakcí systému, identifikátor URI (Uniform Resource) musí být ve tvaru: net.msmq://localhost/system$; DeadXact.  
  
-   Ke čtení zpráv z fronty nedoručených zpráv netransakční systému, musí být identifikátor URI ve tvaru: net.msmq://localhost/system$; nedoručených zpráv.  
  
-   Ke čtení zpráv z fronty nedoručených zpráv vlastní, musí být identifikátor URI formuláře: net.msmq://localhost/private/\<*Vlastní-DLQ se name*> kde *Vlastní-DLQ se name* je název vlastní frontu nedoručených zpráv.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Adresa front najdete v tématu [koncové body služby a adresování front](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Zásobníku na odpovídá adresy příjemce, které služba naslouchá na s adresou na zprávu. Pokud se adresy shodují, je zpráva odeslána; Pokud ne, není-li odeslat zprávu. To může způsobit problémy při čtení z fronty nedoručených zpráv, protože zprávy do fronty nedoručených zpráv jsou obvykle adresovaných službu a ne službu frontu nedoručených zpráv. Proto služba čtení z fronty nedoručených zpráv musí nainstalovat filtr adres `ServiceBehavior` , dá pokyn zásobníku tak, aby odpovídaly všechny zprávy ve frontě nezávisle na adresát. Konkrétně je nutné přidat `ServiceBehavior` s <xref:System.ServiceModel.AddressFilterMode.Any> parametr ke službě čtení zpráv z fronty nedoručených zpráv.  
  
## <a name="poison-message-handling-from-the-dead-letter-queue"></a>Zacházení s nezpracovatelnými zprávami z fronty nedoručených zpráv  
 Zpracování poškozených zpráv je k dispozici ve frontách nedoručených zpráv s některé podmínky. Protože dílčí fronty nelze vytvořit z fronty systému při čtení z fronty nedoručených zpráv systému `ReceiveErrorHandling` nelze nastavit na `Move`. Všimněte si, že při čtení z vlastní frontu nedoručených zpráv, může mít dílčí fronty a tedy `Move` je platný dispozice pro poškozená zpráva.  
  
 Když `ReceiveErrorHandling` je nastaven na `Reject`, že při čtení z fronty zpráv nedoručených zpráv vlastní nezpracovatelná zpráva je umístěna do fronty nedoručených zpráv systému. Když čtení z fronty nedoručených zpráv systému, zpráva se zahodí (vymazány). Odmítnutí z fronty nedoručených zpráv systému v vyřazuje služby MSMQ (odstraní) zprávy.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit frontu nedoručených zpráv a způsobu jeho použití ke zpracování zprávy s vypršenou platností. V příkladu je založena na příkladu v [postup: Exchange zprávy zařazené do fronty pomocí koncových bodů WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md). Následující příklad ukazuje, jak napsat kód klienta pořadí zpracování službu, která používá frontu nedoručených zpráv pro každou aplikaci. Tento příklad také ukazuje, jak ke zpracování zpráv z fronty zpráv nedoručených zpráv.  
  
 Zde je kód pro klienta, který určuje frontu nedoručených zpráv pro každou aplikaci.  
  
 [!code-csharp[S_DeadLetter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/client.cs#1)]
 [!code-vb[S_DeadLetter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/client.vb#1)]  
  
 Zde je kód pro soubor konfigurace klienta.  
  
  
  
 Zde je kód služby zpracování zpráv z fronty nedoručených zpráv.  
  
 [!code-csharp[S_DeadLetter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/dlservice.cs#3)]
 [!code-vb[S_DeadLetter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/dlservice.vb#3)]  
  
 Zde je kód pro konfigurační soubor služby frontu nedoručených zpráv.  
  
  
  
## <a name="see-also"></a>Viz také  
 [Přehled front](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [Postupy: Výměna zpráv zařazených do fronty s koncovými body WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [Zpracování škodlivých zpráv](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
