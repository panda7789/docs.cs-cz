---
title: "Webhosting frontové aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7a539fa-e442-4c08-a7f1-17b7f5a03e88
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 38edfcb1363e538295e1fb1a8b8fe0c5b2d34691
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="web-hosting-a-queued-application"></a>Webhosting frontové aplikace
Aktivační služba procesů systému Windows (WAS) spravuje aktivace a dobu života pracovních procesů, které obsahují aplikace, které hostují [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby. Model procesu WAS umožňuje zobecnit [!INCLUDE[iis601](../../../../includes/iis601-md.md)] model procesu pro server HTTP odebráním závislosti na protokolu HTTP. To umožňuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby využívají protokoly HTTP a jiných protokolů než HTTP, jako je například net.msmq a msmq.formatname v hostitelské prostředí, které podporuje aktivaci na základě zpráv a nabízí schopnost hostovat velký počet aplikací v daném počítači.  
  
 BYL zahrnuje služba Aktivace řízení front zpráv (MSMQ), která aktivuje aplikace ve frontě, když jeden nebo více zpráv ukládány v jednom z fronty používá aplikace. Aktivace služby MSMQ je služby NT, který se automaticky spustí ve výchozím nastavení.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]WAS a jeho výhody, najdete v části [hostování v aktivační službě procesů systému Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]MSMQ, najdete v části [fronty – přehled](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
  
## <a name="queue-addressing-in-was"></a>Fronty adresování ve WAS  
 BYLA aplikací mít adresy identifikátor URI (Uniform Resource). Adresy aplikací mít dvě části: základní předpony identifikátoru URI a specifické pro aplikaci, relativní adresu (cesta). Tyto dvě části zadejte externí adresu pro aplikaci, když propojeny. Základní předpony identifikátoru URI je vytvořený z vazby webu a používá se pro všechny aplikace v rámci lokality, například "net.msmq://localhost", "msmq.formatname://localhost" nebo "net.tcp://localhost". Aplikace adresy se pak vytvářejí provedením fragmenty cesta specifické pro aplikaci (například "/ applicationOne") a jejich připojení k základní identifikátor URI předpona, která přicházejí na úplný identifikátor URI aplikace, například "net.msmq://localhost/applicationOne".  
  
 Aktivace služby MSMQ používá identifikátor URI aplikace tak, aby odpovídaly fronta, kterou je třeba sledovat aktivace služby MSMQ pro zprávy. Při spuštění aktivační služby MSMQ, zobrazí všechny veřejné a soukromé fronty v počítači je nakonfigurovaný pro příjem z a monitoruje jejich pro zprávy. Každých 10 minut, aktivace služby MSMQ aktualizuje seznam fronty pro monitorování. Když se najde zprávu ve frontě, službu Aktivace odpovídá názvu fronty do aplikace nejdéle odpovídající identifikátor URI pro vazbu net.msmq a aktivuje aplikaci.  
  
> [!NOTE]
>  Aplikace aktivované musí odpovídat (nejdelší shody) předponu názvu fronty.  
  
 Je třeba název fronty: msmqWebHost/orderProcessing/service.svc. Pokud /msmqWebHost/orderProcessing virtuálního adresáře s service.svc v něm má aplikace 1 a 2 aplikace má /msmqWebHost virtuálního adresáře s orderProcessing.svc v něm, je aktivovaná aplikace 1. Pokud se odstraní aplikaci 1, 2 aplikace je aktivována.  
  
> [!NOTE]
>  Při vytvoření fronty, všechny zprávy do něj odeslané Neaktivujte aplikace dokud aktivace služby MSMQ aktualizuje seznam fronty, který je maximálně 10 minut od okamžiku, kdy fronta byla vytvořena. Restartování služby Aktivace aktualizuje seznamu fronty.  
  
### <a name="the-effect-of-private-and-public-queues-on-addressing"></a>Účinek privátní a veřejné fronty na adresování  
 Aktivace služby MSMQ nerozlišuje mezi monitorování privátní a veřejné fronty. Jako takový nemůže mít veřejné a soukromé fronty se stejným názvem. Pokud tak učiníte, může získat k hostované webové aplikaci aktivovat čtení pomocí kteréhokoli z fronty.  
  
### <a name="queue-configuration-for-activation"></a>Konfigurace fronty pro aktivaci  
 Aktivace služby MSMQ spouští jako síťová služba. Je služba, která monitoruje fronty k aktivaci aplikace. Pro něj k aktivaci aplikací z fronty musíte zadat fronty pro SÍŤOVOU službu přístup k prohlížení zpráv ve svém seznamu řízení přístupu (ACL).  
  
### <a name="poison-messaging"></a>Zacházení s nezpracovatelnými zasílání zpráv  
 Zpracování v poškozených zpráv [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá kanál, který není pouze zjistí, že zprávy je poškozen, ale vybírá dispozice, v závislosti na konfiguraci uživatele. Ve frontě v důsledku toho není do jedné zprávy. Aplikace hostované webové zruší následných časy a zpráva bude přesunuta do fronty opakování. V okamžiku, závisí na zpoždění opakování cyklus zpráva se přesune ze fronty opakování hlavní fronty a zkuste to znovu. Ale vyžaduje zařazených do fronty kanálu jako aktivní. Pokud je aplikace recyklované službou WAS, pak zpráva zůstane v fronty opakování dokud dorazí další zprávu ve frontě hlavní aktivovat aplikaci ve frontě. Alternativní řešení v tomto případě je přesunout zprávu ručně z fronty opakování zpět do hlavní fronty se znovu aktivovat aplikaci.  
  
### <a name="subqueue-and-system-queue-caveat"></a>Dílčí fronta a přímý přístup fronty paměti systému  
 Aplikace hostované WAS nelze aktivovat, na základě zpráv ve frontě systému, jako jsou systémové fronty nedoručených zpráv nebo dílčí fronty, jako je například poškozených dílčí fronty. Jedná se o omezení pro tuto verzi produktu.  
  
## <a name="see-also"></a>Viz také  
 [Zpracování škodlivých zpráv](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 [Koncové body služby a adresování front](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)
