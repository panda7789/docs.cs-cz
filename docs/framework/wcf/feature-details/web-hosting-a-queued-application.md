---
title: Webhosting frontové aplikace
ms.date: 03/30/2017
ms.assetid: c7a539fa-e442-4c08-a7f1-17b7f5a03e88
ms.openlocfilehash: 36c35fe0590ad9fc728641313d4175a432d7ccaa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951579"
---
# <a name="web-hosting-a-queued-application"></a>Webhosting frontové aplikace
Aktivační služba procesů systému Windows (WAS) spravuje aktivaci a životnost pracovních procesů, které obsahují aplikace, které hostují služby Windows Communication Foundation (WCF). Model procesu WAS generalizuje model procesu IIS 6,0 pro server HTTP tím, že odebere závislost na HTTP. To umožňuje službám WCF používat protokoly HTTP i non-HTTP, jako je NET. MSMQ a MSMQ. FormatName, v hostitelském prostředí, které podporuje aktivaci založené na zprávách, a nabízí možnost hostovat v daném počítači velký počet aplikací.  
  
 Služba WAS obsahuje aktivační službu Řízení front zpráv (MSMQ), která aktivuje aplikaci ve frontě, pokud je jedna nebo více zpráv umístěných v jedné z front používaných aplikací. Aktivační služba MSMQ je služba NT, která se ve výchozím nastavení automaticky spustí.  
  
 Další informace o a jeho výhodách najdete v tématu [hostování v aktivační službě procesů systému Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md). Další informace o službě MSMQ najdete v tématu [Queue Overview](../../../../docs/framework/wcf/feature-details/queues-overview.md).
  
## <a name="queue-addressing-in-was"></a>Zařazení do fronty v nástroji bylo  
 Měly by aplikace adresy identifikátoru URI (Uniform Resource Identifier). Adresy aplikací mají dvě části: základní předponu identifikátoru URI a relativní adresu (cestu) specifickou pro aplikaci. Tyto dvě části poskytují externí adresu aplikace, když se spojí dohromady. Základní předpona identifikátoru URI je vytvořená z vazby webu a používá se pro všechny aplikace v lokalitě, například "NET. MSMQ://localhost", "MSMQ. FormatName://localhost" nebo "NET. TCP://localhost". Adresy aplikací se pak vytvoří pomocí fragmentů cesty specifické pro aplikaci (například "/applicationOne") a jejich připojením k základní předponě identifikátoru URI, aby bylo možné dorazit na úplný identifikátor URI aplikace, například "NET. MSMQ://localhost/applicationOne".  
  
 Aktivační služba MSMQ používá identifikátor URI aplikace, aby odpovídala frontě, kterou musí služba Aktivace služby MSMQ monitorovat pro zprávy. Jakmile se služba Aktivace služby MSMQ spustí, vytvoří výčet všech veřejných a privátních front v počítači, na kterých je nakonfigurovaný příjem, a monitoruje je pro zprávy. Aktivační služba MSMQ každých 10 minut aktualizuje seznam front, které se mají monitorovat. Když se ve frontě najde zpráva, aktivační služba se shoduje s názvem fronty a výsledkem je nejdelší odpovídající identifikátor URI aplikace pro vazbu NET. MSMQ a aplikaci aktivuje.  
  
> [!NOTE]
> Aplikace, která se aktivuje, se musí shodovat s předponou názvu fronty (nejdelší shoda).  
  
 Název fronty je například: msmqWebHost/orderProcessing/service. svc. Pokud má aplikace 1 virtuální adresář/msmqWebHost/orderProcessing se službou. svc pod ní a aplikace 2 má virtuální adresář/msmqWebHost s orderProcessing. svc, je aktivována aplikace 1. Pokud je aplikace 1 odstraněna, je aktivována aplikace 2.  
  
> [!NOTE]
> Když se vytvoří fronta, všechny zprávy, které do ní odešlou, neaktivují aplikaci, dokud aktivační služba MSMQ neaktualizuje seznam front, což je většinou 10 minut od okamžiku, kdy se fronta vytvořila. Restartování aktivační služby aktualizuje i seznam front.  
  
### <a name="the-effect-of-private-and-public-queues-on-addressing"></a>Vliv privátních a veřejných front na adresování  
 Aktivační služba MSMQ nerozlišuje mezi monitorováním privátních a veřejných front. V takovém případě nemůžete mít veřejné a soukromé fronty se stejným názvem. V případě, že aplikace hostovaná na webu, může dojít k aktivaci čtení z obou front.  
  
### <a name="queue-configuration-for-activation"></a>Konfigurace fronty pro aktivaci  
 Aktivační služba MSMQ je spuštěna jako síťová služba. Jedná se o službu, která monitoruje fronty pro aktivaci aplikací. Aby mohla fronta aktivovat aplikace z fronty, musí pro přístup k síti v seznamu řízení přístupu (ACL) pro síťovou službu použít přístup.  
  
### <a name="poison-messaging"></a>Nezpracovatelná zpráva  
 Zpracování škodlivých zpráv v technologii WCF je zpracováváno kanálem, který nejen detekuje, že zpráva je poškozena, ale vybírá dispozice na základě konfigurace uživatele. V důsledku toho je ve frontě jediná zpráva. Aplikace, která je hostována v rámci webu, se postupně přerušuje a zpráva se přesune do fronty opakovaných pokusů. V bodě vydaném zpožděním při opakování cyklu se zpráva přesune z fronty opakování do hlavní fronty a zkusí to znovu. To ale vyžaduje, aby byl kanál zařazený do fronty aktivní. Pokud byla aplikace recyklována nástrojem WAS, zpráva zůstane ve frontě opakování, dokud do hlavní fronty nepřijde jiná zpráva k aktivaci aplikace zařazené do fronty. Alternativním řešením v tomto případě je přesunout zprávu ručně z fronty opakování zpět do hlavní fronty a znovu aktivovat aplikaci.  
  
### <a name="subqueue-and-system-queue-caveat"></a>Omezení podfronty a fronty systému  
 Hostovaná aplikace se nedá aktivovat na základě zpráv ve frontě systému, jako je například fronta nedoručených zpráv v rámci systému, nebo podfronty, jako je například otravové podfronty. Toto je omezení pro tuto verzi produktu.  
  
## <a name="see-also"></a>Viz také:

- [Zpracování škodlivých zpráv](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
- [Koncové body služby a adresování front](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)
