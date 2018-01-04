---
title: "Hostování v Internetové informační službě"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 988216447e47345b6d863de6e46d0de9a025f068
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-in-internet-information-services"></a>Hostování v Internetové informační službě
Jednou z možností pro hostování [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby je v rámci Internetové informační služby (IIS) aplikace. Tento model hostování je podobný modelu používaný [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] a webových služeb ASP.NET (ASMX) webové služby.  
  
## <a name="versions-of-iis"></a>Verze služby IIS  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]může být hostitelem následující verze služby IIS na následující operační systémy:  
  
-   Služba IIS 5.1 na [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]. Toto prostředí je užitečné pro návrh a vývoj hostované službou IIS nasazených aplikací později v operačním systému serveru, jako [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
-   [!INCLUDE[iis601](../../../../includes/iis601-md.md)]na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. [!INCLUDE[iis601](../../../../includes/iis601-md.md)]poskytuje pokročilé proces model, který nabízí lepší škálovatelnost, spolehlivost a izolace aplikací. Toto prostředí je vhodná pro produkční nasazení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, které používají výhradně komunikaci pomocí protokolu HTTP.  
  
-   Služba IIS 7.0 na [!INCLUDE[wv](../../../../includes/wv-md.md)] a [!INCLUDE[lserver](../../../../includes/lserver-md.md)]. Služba IIS 7.0 obsahuje stejný model pokročilé proces jako [!INCLUDE[iis601](../../../../includes/iis601-md.md)], ale používá služba aktivace procesů systému Windows (WAS) k povolení aktivace a síťovou komunikaci v jiné protokoly než HTTP. Toto prostředí je vhodný pro vývoj [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, které komunikují přes všechny sítě nepodporuje protokol [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (včetně protokolů HTTP, net.tcp, net.pipe a net.msmq). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]BYL, najdete v části [hostování v aktivační službě procesů systému Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
-   [Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496) pracuje s [!INCLUDE[iisver](../../../../includes/iisver-md.md)] a proces aktivace služby WAS (Windows) k poskytování hostování prostředí služeb NET4 WCF a WF bohaté aplikace. Tyto výhody patří správa životního cyklu procesu, recyklace procesů, sdílené hostování, rychlou ochranu před chybami, osamocení proces, na vyžádání aktivace a sledování stavu. Podrobné informace najdete v tématu [funkce hostování AppFabric](http://go.microsoft.com/fwlink/?LinkId=196494) a [AppFabric hostování koncepty](http://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="benefits-of-iis-hosting"></a>Výhody hostování služby IIS  
 Hostování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby ve službě IIS má několik výhod:  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]služby hostované ve službě IIS se nasadit a spravovat jako jiný typ aplikace služby IIS, včetně [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace a ASMX.  
  
-   Služba IIS poskytuje aktivace procesů, správy stavu a recyklaci možnosti zvýšit spolehlivost hostovaných aplikací.  
  
-   Jako [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby hostovány v [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] můžete využít výhod [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] sdílený model hostování, kde jsou umístěny v běžné pracovní proces pro hustotu lepší využití serverových a škálovatelnost více aplikací.  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]služby hostované ve službě IIS použít stejný model dynamická kompilace jako [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)], což usnadňuje vývoj a nasazení hostovaných služeb.  
  
 Při rozhodování o hostitele [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby ve službě IIS, je důležité si pamatovat této služby IIS 5.1 a [!INCLUDE[iis601](../../../../includes/iis601-md.md)] omezeny pouze komunikaci pomocí protokolu HTTP. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]výběr do hostitelského prostředí, najdete v části [hostování služeb](../../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="deploying-an-iis-hosted-wcf-service"></a>Nasazení služby WCF hostované IIS  
 Vývoj a nasazení hostované službou IIS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby se skládá z následujících úloh:  
  
-   Ujistěte se, zda služba IIS, ASP.NET, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] součásti aktivace protokolu HTTP jsou správně nainstalováno a zaregistrován.  
  
-   Vytvoření nové aplikace služby IIS, nebo znovu použijte existující [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace.  
  
-   Vytvořte soubor .svc pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.  
  
-   Implementace služby nasaďte do aplikace služby IIS.  
  
-   Konfigurace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.  
  
 Informace o každé z těchto úloh, najdete v části [nasazení služby WCF Internet Information Services-Hosted](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="wcf-services-and-aspnet"></a>Služby WCF a ASP.NET  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]služby mohou být hostované buď-souběžného s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] nebo v [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] režimu kompatibility, ve kterém služby můžete využít všech výhod funkcí poskytovaných [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] platformy pro webové aplikace. Informace o těchto funkcích, najdete v části [služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření hostování pomocí ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 [Nasazení služby WCF hostované Internetovou informační službou](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)  
 [Služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [Osvědčené postupy hostování Internetové informační služby](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Konfigurace Internetové informační služby 7.0 pro Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)  
 [Hostování funkcí systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
