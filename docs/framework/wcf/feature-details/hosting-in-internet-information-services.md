---
title: Hostování v Internetové informační službě
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
ms.openlocfilehash: 588e069280afc369256fdbee0132f732348ffc37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494111"
---
# <a name="hosting-in-internet-information-services"></a>Hostování v Internetové informační službě
Jednou z možností pro hostování služby Windows Communication Foundation (WCF) je v rámci Internetové informační služby (IIS) aplikace. Tento model hostování je podobný modelu používaný [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] a webových služeb ASP.NET (ASMX) webové služby.  
  
## <a name="versions-of-iis"></a>Verze služby IIS  
 WCF může být hostitelem následující verze služby IIS na následující operační systémy:  
  
-   Služba IIS 5.1 na [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]. Toto prostředí je užitečné pro návrh a vývoj hostované službou IIS nasazených aplikací později v operačním systému serveru, jako [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
-   [!INCLUDE[iis601](../../../../includes/iis601-md.md)] na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. [!INCLUDE[iis601](../../../../includes/iis601-md.md)] poskytuje pokročilé proces model, který nabízí lepší škálovatelnost, spolehlivost a izolace aplikací. Toto prostředí je vhodná pro produkční nasazení služby WCF, které používají výhradně komunikaci pomocí protokolu HTTP.  
  
-   Služba IIS 7.0 na [!INCLUDE[wv](../../../../includes/wv-md.md)] a [!INCLUDE[lserver](../../../../includes/lserver-md.md)]. Služba IIS 7.0 obsahuje stejný model pokročilé proces jako [!INCLUDE[iis601](../../../../includes/iis601-md.md)], ale používá služba aktivace procesů systému Windows (WAS) k povolení aktivace a síťovou komunikaci v jiné protokoly než HTTP. Toto prostředí je vhodný pro vývoj služby WCF, které komunikují přes všechny síťové protokoly podporované službou WCF (včetně protokolů HTTP, net.tcp, net.pipe a net.msmq). Další informace o WAS najdete v tématu [hostování v aktivační službě procesů systému Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
-   [Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496) pracuje s [!INCLUDE[iisver](../../../../includes/iisver-md.md)] a proces aktivace služby WAS (Windows) k poskytování hostování prostředí služeb NET4 WCF a WF bohaté aplikace. Tyto výhody patří správa životního cyklu procesu, recyklace procesů, sdílené hostování, rychlou ochranu před chybami, osamocení proces, na vyžádání aktivace a sledování stavu. Podrobné informace najdete v tématu [funkce hostování AppFabric](http://go.microsoft.com/fwlink/?LinkId=196494) a [AppFabric hostování koncepty](http://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="benefits-of-iis-hosting"></a>Výhody hostování služby IIS  
 Hostování služby WCF ve službě IIS má několik výhod:  
  
-   Služby WCF hostované ve službě IIS se nasadit a spravovat jako jiný typ aplikace služby IIS, včetně [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace a ASMX.  
  
-   Služba IIS poskytuje aktivace procesů, správy stavu a recyklaci možnosti zvýšit spolehlivost hostovaných aplikací.  
  
-   Jako [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], služby WCF hostované v [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] můžete využít výhod [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] sdílený model hostování, kde jsou umístěny v běžné pracovní proces pro hustotu lepší využití serverových a škálovatelnost více aplikací.  
  
-   Služby WCF hostované ve službě IIS použít stejný model dynamická kompilace jako [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)], což usnadňuje vývoj a nasazení hostovaných služeb.  
  
 Při rozhodování o hostování služeb WCF v IIS, je důležité nezapomenout, že služba IIS 5.1 a [!INCLUDE[iis601](../../../../includes/iis601-md.md)] omezeny pouze komunikaci pomocí protokolu HTTP. Další informace o výběru do hostitelského prostředí najdete v tématu [hostování služeb](../../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="deploying-an-iis-hosted-wcf-service"></a>Nasazení služby WCF hostované IIS  
 Vývoj a nasazení služby WCF hostované IIS se skládá z následujících úloh:  
  
-   Zajistěte, aby služby IIS, ASP.NET, WCF a součásti aktivace WCF HTTP jsou správně nainstalovaný a zaregistrovaný.  
  
-   Vytvoření nové aplikace služby IIS, nebo znovu použijte existující [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace.  
  
-   Vytvořte soubor .svc pro službu WCF.  
  
-   Implementace služby nasaďte do aplikace služby IIS.  
  
-   Konfigurace služby WCF.  
  
 Informace o každé z těchto úloh, najdete v části [nasazení služby WCF Internet Information Services-Hosted](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="wcf-services-and-aspnet"></a>Služby WCF a ASP.NET  
 Může být služby WCF hostované buď-souběžného s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] nebo v [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] režimu kompatibility, ve kterém služby můžete využít všech výhod funkcí poskytovaných [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] platformy pro webové aplikace. Informace o těchto funkcích, najdete v části [služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření hostování pomocí ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 [Nasazení služby WCF hostované Internetovou informační službou](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)  
 [Služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [Osvědčené postupy hostování Internetové informační služby](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Konfigurace Internetové informační služby 7.0 pro Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)  
 [Hostování funkcí systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
