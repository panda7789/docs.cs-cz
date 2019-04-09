---
title: Hostování v Aktivační službě procesů systému Windows
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], WAS
ms.assetid: d2b9d226-15b7-41fc-8c9a-cb651ac20ecd
ms.openlocfilehash: 5b234a00f3194fcf40a33d25302cff16d5999b05
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082981"
---
# <a name="hosting-in-windows-process-activation-service"></a>Hostování v Aktivační službě procesů systému Windows
Služby Aktivace procesu Windows (WAS) spravuje aktivace a dobu života pracovních procesů, které obsahují tento hostitel služby Windows Communication Foundation (WCF) aplikace. Model zpracování služby WAS zobecňuje [!INCLUDE[iis601](../../../../includes/iis601-md.md)] model procesu pro server HTTP odebráním závislosti na protokolu HTTP. To umožňuje službám WCF pomocí protokolu HTTP a jiných protokolů než HTTP, jako je například Net.TCP v hostitelském prostředí, který podporuje aktivaci založenou na zprávách a nabízí schopnost hostovat velký počet aplikací na daném počítači.  
  
 Další informace o vytvoření služby WCF, který běží v hostitelském prostředí WAS, najdete v části [jak: Hostování služby WCF ve WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
 Model zpracování služby WAS poskytuje několik funkcí, které umožňují aplikacím zajistit také jejich hostování způsobem, který je robustnější, snáze spravovatelné a, který efektivně využívá prostředky:  
  
-   Aktivace založená na zprávách aplikacím a aplikacím pracovní proces spuštění a zastavení dynamicky v reakci na příchozí pracovních položek, které přicházejí pomocí protokolu HTTP a jiným protokolem než HTTP síťových protokolů.  
  
-   Robustní aplikace a pracovní proces recykluje k údržbě stavu spuštěných aplikací.  
  
-   Centralizované aplikace konfigurace a správa.  
  
-   Umožňuje aplikacím využívat výhod procesní model IIS bez nutnosti nasazení nároky úplnou instalaci služby IIS.  
  
 Další informace o funkcích WAS najdete v tématu [IIS 7.0 Beta: Správu služby IIS 7.0 webu](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
 [Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=196496) funguje s [!INCLUDE[iisver](../../../../includes/iisver-md.md)] a Windows WAS Process Activation Service () k poskytování bohatých aplikací hostitelské prostředí služby NET4 WCF a WF. Mezi tyto výhody patří správa životního cyklu procesu, proces recykluje, sdílené hostování, rychlou ochranu, osamocení procesu, na vyžádání aktivace a sledování stavu. Podrobné informace najdete v tématu [funkce hostování AppFabric](https://go.microsoft.com/fwlink/?LinkId=196494) a [AppFabric hostování koncepty](https://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="elements-of-the-was-addressing-model"></a>Prvky WAS adresování modelu  
 Aplikace mají adres identifikátor URI (Uniform Resource), které jsou jednotky kódu, jejichž životní cyklus a spuštění prostředí jsou spravovány serverem. Může být jedna instance serveru WAS domácí pro spoustu různých aplikací. Servery uspořádání aplikací do skupin nazývaných *lokality*. V rámci lokality jsou hierarchické způsobem, který odráží strukturu identifikátorů URI, který bude sloužit jako jejich externí adresy uspořádané aplikací.  
  
 Aplikace adresy mít dvě části: základní identifikátor URI předponu a specifické pro aplikaci, relativní adresa (cesta), které poskytují externí adresu aplikace, když propojeny. Základní identifikátor URI předponu je vytvořen z vazby webu a používá se pro všechny aplikace v rámci lokality. Aplikace adresy jsou pak vytvořeny pomocí fragmentů cesty specifické pro aplikaci (například "/ applicationOne") a připojením k základní předpony identifikátoru URI (například "NET.TCP://localhost") můžete přejít na úplný identifikátor URI aplikace.  
  
 Následující tabulka ukazuje několik možných scénářů adresování WAS lokalit přes protokol HTTP a vazby webu jiným protokolem než HTTP.  
  
|Scénář|Vazby webu|Cesta k aplikaci|Základní aplikace identifikátorů URI|  
|--------------|-------------------|----------------------|---------------------------|  
|Jenom HTTP|http: *: 80:\*|/appTwo|http://localhost/appTwo/|  
|HTTP a jiným protokolem než HTTP|http: *: 80:\*<br /><br /> net.tcp: 808:\*|/appTwo|http://localhost/appTwo/<br />net.tcp://localhost/appTwo/|  
|Jiným protokolem než HTTP pouze|net.pipe: *|/appThree|NET.pipe://appThree/|  
  
 Služby a prostředky v rámci aplikace lze také řešit. V rámci aplikace prostředků aplikace se tak vyřeší, relativní k cestě základní aplikace. Předpokládejme například, že společnosti na contoso.com název počítače má vazby webu pro protokoly HTTP i protokol Net.TCP. Také Předpokládejme, že lokality obsahuje jednu aplikaci v /Billing, která poskytuje službu na GetOrders.svc. Potom Pokud služba GetOrders.svc vystavena koncového bodu s relativní adresu SecureEndpoint, koncový bod služby by vystavit na následující dva identifikátory URI:  
  
- `http://contoso.com/Billing/GetOrders.svc/SecureEndpoint`
- `net.tcp://contoso.com/Billing/GetOrders.svc/SecureEndpoint`
  
## <a name="the-was-runtime"></a>WAS modulu Runtime  
 Aplikace jsou uspořádány do lokality pro účely řešení a správy. V době běhu aplikace jsou také seskupeny do fondů aplikací. Fond aplikací může zastřešovat i různým aplikacím z mnoha různých lokalit. Všechny aplikace ve fondu aplikací sdílejí společnou sadu vlastností za běhu. Například všechny jsou spouštěny pod stejnou verzi modulu common language runtime (CLR) a všechny sdílejí společnou identitu procesu. Každý fond aplikací odpovídá instance pracovního procesu (w3wp.exe). Každé spravované aplikace běžících v rámci fondu sdílených aplikací je izolovaná od jiných aplikací prostřednictvím CLR AppDomain.  
  
## <a name="see-also"></a>Viz také:

- [Architektura aktivace WAS](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)
- [Konfigurace WAS pro použití s WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [Postupy: Instalace a konfigurace aktivačních komponent WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)
- [Postupy: Hostování služby WCF ve WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)
- [Hostování funkcí systému Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)
