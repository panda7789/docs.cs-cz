---
title: Hostování v Aktivační službě procesů systému Windows
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], WAS
ms.assetid: d2b9d226-15b7-41fc-8c9a-cb651ac20ecd
ms.openlocfilehash: 5cd2244c4b44592e436dfd983985dca3c1a50144
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492444"
---
# <a name="hosting-in-windows-process-activation-service"></a>Hostování v Aktivační službě procesů systému Windows
Služba aktivace procesů systému Windows (WAS) spravuje aktivace a dobu života pracovních procesů, které obsahují aplikace služby Windows Communication Foundation (WCF) tohoto hostitele. Model procesu WAS umožňuje zobecnit [!INCLUDE[iis601](../../../../includes/iis601-md.md)] model procesu pro server HTTP odebráním závislosti na protokolu HTTP. To umožňuje službám WCF pomocí protokolu HTTP a jiných protokolů než HTTP, jako je například Net.TCP v hostitelské prostředí, které podporuje aktivaci na základě zpráv a nabízí schopnost hostovat velký počet aplikací v daném počítači.  
  
 Další informace o vytvoření služby WCF, který běží v hostitelském prostředí WAS, najdete v části [postupy: hostování služby WCF ve WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
 Model procesu WAS poskytuje několik funkcí, které umožňují aplikacím pro hostování způsobem, který je robustnější, lepší správu bitlockeru a efektivně používající prostředky:  
  
-   Aktivace na základě zpráv a pracovní proces aplikace spustit a zastavit dynamicky v reakci na příchozí pracovních položek, které přicházejí pomocí protokolu HTTP a jiných protokolů než HTTP sítě.  
  
-   Robustní aplikace a recyklace pracovního procesu zachování stavu spuštěných aplikací.  
  
-   Centralizované aplikace konfigurace a správy.  
  
-   Umožňuje aplikacím využívat výhod procesní model IIS bez nutnosti nasazení otisk úplné instalace služby IIS.  
  
 Další informace o funkcích WAS najdete v tématu [IIS 7.0 Beta: správu webu služby IIS 7.0](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
 [Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496) pracuje s [!INCLUDE[iisver](../../../../includes/iisver-md.md)] a proces aktivace služby WAS (Windows) k poskytování hostování prostředí služeb NET4 WCF a WF bohaté aplikace. Tyto výhody patří správa životního cyklu procesu, recyklace procesů, sdílené hostování, rychlou ochranu před chybami, osamocení proces, na vyžádání aktivace a sledování stavu. Podrobné informace najdete v tématu [funkce hostování AppFabric](http://go.microsoft.com/fwlink/?LinkId=196494) a [AppFabric hostování koncepty](http://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="elements-of-the-was-addressing-model"></a>Elementy WAS adresování modelu  
 Aplikací mít identifikátor URI (Uniform Resource) adresy, které jsou kód jednotky, jejichž doba platnosti a spouštění prostředí jsou spravované serverem. Může být jedna instance serveru WAS domácí na mnoha různých aplikací. Servery uspořádání aplikací do skupin nazývaných *lokality*. V rámci lokality jsou uspořádány aplikace hierarchické uspořádání, který odráží strukturu identifikátory URI, který slouží jako jejich externí adresy.  
  
 Adresy aplikací mít dvě části: základní předpony identifikátoru URI a specifické pro aplikaci, relativní adresa (cesta), které poskytují externí adresu pro aplikaci, když propojeny. Základní předpony identifikátoru URI je vytvořený z vazby webu a používá se pro všechny aplikace v rámci lokality. Aplikace adresy se pak vytvářejí provedením fragmenty cesta specifické pro aplikaci (například "/ applicationOne") a jejich připojením k základní identifikátor URI předponu (například "net.tcp://localhost") tak, aby přicházejí na úplný identifikátor URI aplikace.  
  
 Následující tabulka znázorňuje několika možných scénářích adresování pro weby WAS přes protokol HTTP a vazby webu jiným protokolem než HTTP.  
  
|Scénář|Vazby webu|Cesta k aplikaci|Základní aplikace identifikátory URI|  
|--------------|-------------------|----------------------|---------------------------|  
|Pouze HTTP|http: *: 80:\*|/appTwo|http://localhost/appTwo/|  
|HTTP a jiným protokolem než HTTP|http: *: 80:\*<br /><br /> NET.TCP: 808:\*|/appTwo|http://localhost/appTwo/<br />NET.TCP://localhost/appTwo/|  
|Jiným protokolem než HTTP pouze|NET.pipe: *|/appThree|NET.pipe://appThree/|  
  
 Služby a prostředky v rámci aplikace lze také řešit. V rámci aplikace jsou prostředky aplikace řešit relativní k cestě základní aplikace. Předpokládejme například, že lokalita na contoso.com název počítače má vazby webu pro HTTP i Net.TCP protokoly. Také předpokládají, že lokalita obsahuje jednu aplikaci, které jsou umístěné v /Billing, která poskytuje služby v GetOrders.svc. Poté Pokud služba GetOrders.svc vystavený koncový bod s relativní adresu SecureEndpoint, koncový bod služby by vystavit na následující dva identifikátory URI:  
  
 http://contoso.com/Billing/GetOrders.svc/SecureEndpoint  
NET.TCP://contoso.com/Billing/GetOrders.svc/SecureEndpoint  
  
## <a name="the-was-runtime"></a>WAS modulu Runtime  
 Aplikace jsou uspořádány do lokality pro účely správy a adresování. V době běhu aplikace jsou také seskupeny do fondů aplikací. Fond aplikací může obsahovat mnoho různých aplikací z mnoha různých lokalit. Všechny aplikace ve fondu aplikací sdílejí společnou sadu vlastností běhu. Například všechny poběží pod stejnou verzi common language runtime (CLR) a všechny sdílejí společnou identitu procesu. Každý fond aplikací odpovídá instance pracovního procesu (w3wp.exe). Každé spravované aplikace běžící v rámci fondu sdílených aplikací je izolovaný od ostatních aplikací prostřednictvím CLR AppDomain.  
  
## <a name="see-also"></a>Viz také  
 [Architektura aktivace WAS](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)  
 [Konfigurace WAS pro použití s WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [Postupy: Instalace a konfigurace aktivačních komponent WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)  
 [Postupy: Hostování služby WCF ve WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)  
 [Hostování funkcí systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
