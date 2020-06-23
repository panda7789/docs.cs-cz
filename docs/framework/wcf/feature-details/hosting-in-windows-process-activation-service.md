---
title: Hostování v Aktivační službě procesů systému Windows
description: Přečtěte si o tom, jak byla spravována aktivace a životního cyklu pracovních procesů obsahujících aplikace, které hostují služby WCF.
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], WAS
ms.assetid: d2b9d226-15b7-41fc-8c9a-cb651ac20ecd
ms.openlocfilehash: 6b0b23c21762009341fd62c029431824dd26d6c3
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247257"
---
# <a name="hosting-in-windows-process-activation-service"></a>Hostování v Aktivační službě procesů systému Windows
Aktivační služba procesů systému Windows (WAS) spravuje aktivaci a životnost pracovních procesů, které obsahují aplikace, které hostují služby Windows Communication Foundation (WCF). Model procesu WAS generalizuje model procesu IIS 6,0 pro server HTTP tím, že odebere závislost na HTTP. To umožňuje službám WCF používat protokoly HTTP i non-HTTP, jako je NET. TCP, v hostitelském prostředí, které podporuje aktivaci prostřednictvím zpráv, a nabízí možnost hostovat v daném počítači velký počet aplikací.  
  
 Další informace o vytváření služby WCF, která běží v prostředí hostování, najdete v tématu [How to: Host a WCF Service in was](how-to-host-a-wcf-service-in-was.md).  
  
 Model procesu WAS obsahuje několik funkcí, které umožní hostování aplikací způsobem, který je robustnější, více spravovatelnější a používá prostředky efektivně:  
  
- Aktivace aplikací a aplikací pracovních procesů, které jsou založeny na zprávách, se spouští a zastavují dynamicky v reakci na příchozí pracovní položky, které přicházejí pomocí síťových protokolů HTTP a non-HTTP.  
  
- Robustní recyklace aplikací a pracovních procesů pro udržení stavu spuštěných aplikací.  
  
- Centralizovaná konfigurace a Správa aplikací.  
  
- Umožňuje aplikacím využívat model procesu služby IIS, aniž by vyžadoval nasazení úplné instalace služby IIS.  
[Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10)) spolupracuje se službou IIS 7,0 a službou WAS (Windows Process Activation Service) k poskytování bohatých hostujících prostředí aplikací pro NET4 WCF a služby WF. Mezi tyto výhody patří Správa životního cyklu procesu, recyklace procesů, sdílené hostování, rychlá ochrana při selhání, osamocení procesu, aktivace na vyžádání a sledování stavu. Podrobné informace najdete v tématu [funkce hostování technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10)) a [koncepce hostování technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677371(v=azure.10)).  
  
## <a name="elements-of-the-was-addressing-model"></a>Prvky modelu adresování  
 Aplikace mají adresy identifikátoru URI (Uniform Resource Identifier), které jsou jednotky kódu, jejichž životní prostředí a spouštěcí prostředí jsou spravovány serverem. Jedna instance serveru může být Domovská Server k mnoha různým aplikacím. Servery organizují aplikace do skupin označovaných jako *weby*. V rámci lokality jsou aplikace uspořádány hierarchicky způsobem, který odráží strukturu identifikátorů URI, které slouží jako jejich externí adresy.  
  
 Adresy aplikací mají dvě části: základní předponu identifikátoru URI a relativní adresu (cestu) specifickou pro aplikaci, která poskytuje externí adresu pro aplikaci, když se spojí dohromady. Základní předpona identifikátoru URI je vytvořená z vazby webu a používá se pro všechny aplikace v rámci lokality. Adresy aplikací jsou poté vytvořeny pomocí fragmentů cesty specifické pro aplikaci (například "/applicationOne") a jejich připojením k základní předponě identifikátoru URI (například "NET. TCP://localhost") pro doručení do úplného identifikátoru URI aplikace.  
  
 Následující tabulka ilustruje několik možných scénářů adresování pro weby s vazbami lokalit HTTP i bez HTTP.  
  
|Scénář|Vazby webu|Cesta k aplikaci|Identifikátory URI základních aplikací|  
|--------------|-------------------|----------------------|---------------------------|  
|Jenom HTTP|http: 80:\*|/appTwo|`http://localhost/appTwo/`|  
|HTTP i non-HTTP|http: 80:\*<br /><br /> NET. TCP: 808:\*|/appTwo|`http://localhost/appTwo/`<br />`net.tcp://localhost/appTwo/`|  
|Pouze bez protokolu HTTP|NET. pipe: *|/appThree|`net.pipe://appThree/`|  
  
 Je také možné řešit služby a prostředky v rámci aplikace. V rámci aplikace jsou prostředky aplikace adresovány relativně k základní cestě aplikace. Předpokládejme například, že lokalita na počítači s názvem contoso.com má vazby lokality pro protokoly HTTP a NET. TCP. Předpokládejme také, že lokalita obsahuje jednu aplikaci umístěnou na adrese/Billing, která zpřístupňuje službu v GetOrders. svc. Pokud potom služba GetOrders. svc vystavila koncový bod s relativní adresou SecureEndpoint, koncový bod služby by měl být vystaven následujícímu dvěma identifikátorům URI:  
  
- `http://contoso.com/Billing/GetOrders.svc/SecureEndpoint`
- `net.tcp://contoso.com/Billing/GetOrders.svc/SecureEndpoint`
  
## <a name="the-was-runtime"></a>BYL za běhu  
 Aplikace jsou uspořádány do webů pro účely adresování a správy. V době běhu jsou aplikace seskupeny také dohromady do fondů aplikací. Fond aplikací může obsahovat mnoho různých aplikací z mnoha různých lokalit. Všechny aplikace v rámci fondu aplikací sdílejí společnou sadu charakteristik běhu. Všechny mají například všechny spuštěné pod stejnou verzí modulu CLR (Common Language Runtime) a všechny sdílejí společnou identitu procesu. Každý fond aplikací odpovídá instanci pracovního procesu (w3wp.exe). Každá spravovaná aplikace spuštěná ve sdíleném fondu aplikací je izolovaná od ostatních aplikací prostřednictvím třídy AppDomain CLR.  
  
## <a name="see-also"></a>Viz také

- [Architektura aktivace WAS](was-activation-architecture.md)
- [Konfigurace WAS pro použití s WCF](configuring-the-wpa--service-for-use-with-wcf.md)
- [Postupy: Instalace a konfigurace aktivačních komponent WCF](how-to-install-and-configure-wcf-activation-components.md)
- [Postupy: Hostování služby WCF ve WAS](how-to-host-a-wcf-service-in-was.md)
- [Funkce hostování technologie Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
