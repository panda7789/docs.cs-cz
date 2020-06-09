---
title: Hostování v Internetové informační službě
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
ms.openlocfilehash: baf13af39fe575a75f1304b21f3b4ad70dd370ab
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597316"
---
# <a name="host-in-internet-information-services"></a>Hostitel v Internetová informační služba

Jedna možnost pro hostování služby Windows Communication Foundation (WCF) je uvnitř aplikace Internetová informační služba (IIS). Tento model hostování je podobný modelu používanému webovými službami ASP.NET a ASP.NET Web Services (ASMX).

## <a name="versions-of-iis"></a>Verze služby IIS

Služba WCF může být hostována v následujících verzích služby IIS v následujících operačních systémech:

- Služba IIS 5,1 v systému Windows XP SP2. Toto prostředí je užitečné pro návrh a vývoj aplikací hostovaných službou IIS, které jsou později nasazené na serverovém operačním systému, jako je Windows Server 2003.

- Služba IIS 6,0 v systému Windows Server 2003. Služba IIS 6,0 poskytuje pokročilý model procesu, který nabízí vylepšenou škálovatelnost, spolehlivost a izolaci aplikací. Toto prostředí je vhodné pro produkční nasazení služeb WCF, které používají výhradně komunikaci pomocí protokolu HTTP.

- Služba IIS 7,0 v systému Windows Vista a Windows Server 2008. Služba IIS 7,0 poskytuje stejný pokročilý model procesu jako IIS 6,0, ale používá aktivační službu procesů systému Windows (WAS) k povolení aktivace a síťové komunikace přes jiné protokoly než HTTP. Toto prostředí je vhodné pro vývoj služeb WCF, které komunikují přes jakýkoli síťový protokol podporovaný službou WCF (včetně HTTP, NET. TCP, NET. pipe a NET. MSMQ). Další informace o nástroji najdete v tématu [hostování v aktivační službě procesů systému Windows](hosting-in-windows-process-activation-service.md).

- [Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10)) spolupracuje se službou IIS 7,0 a službou WAS (Windows Process Activation Service) k poskytování bohatých hostujících prostředí aplikací pro NET4 WCF a služby WF. Mezi tyto výhody patří Správa životního cyklu procesu, recyklace procesů, sdílené hostování, rychlá ochrana při selhání, osamocení procesu, aktivace na vyžádání a sledování stavu. Podrobné informace najdete v tématu [funkce hostování technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10)) a [koncepce hostování technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677371(v=azure.10)).

## <a name="benefits-of-iis-hosting"></a>Výhody hostování služby IIS

Hostování služeb WCF ve službě IIS má několik výhod:

- Služby WCF hostované ve službě IIS se nasazují a spravují jako jakýkoli jiný typ aplikace IIS, včetně aplikací ASP.NET a ASMX.

- Služba IIS poskytuje aktivaci procesů, správu stavu a možnosti recyklace a zvyšuje tak spolehlivost hostovaných aplikací.

- Podobně jako ASP.NET mohou služby WCF hostované v ASP.NET využít výhod modelu sdíleného hostování ASP.NET, kde se více aplikací nachází v běžném pracovním procesu pro zlepšení hustoty serveru a škálovatelnosti.

- Služby WCF hostované v IIS používají stejný model dynamické kompilace jako ASP.NET 2,0, což zjednodušuje vývoj a nasazování hostovaných služeb.

Při rozhodování o hostování služeb WCF ve službě IIS je důležité si uvědomit, že služba IIS 5,1 a služba IIS 6,0 jsou omezené jenom na komunikaci HTTP. Další informace o volbě hostitelského prostředí naleznete v tématu [hostingové služby](../hosting-services.md).

## <a name="deploy-an-iis-hosted-wcf-service"></a>Nasazení služby WCF hostované v IIS

Vývoj a nasazení služby WCF hostované v IIS se skládá z následujících úloh:

- Ujistěte se, že je správně nainstalovaná a registrovaná součást IIS, ASP.NET, WCF a aktivace služby WCF HTTP.

- Vytvořte novou aplikaci služby IIS nebo znovu použijte existující aplikaci ASP.NET.

- Vytvořte soubor. svc pro službu WCF.

- Nasaďte implementaci služby do aplikace IIS.

- Nakonfigurujte službu WCF.

Diskuzi o jednotlivých úlohách najdete v tématu [nasazení služby WCF hostované Internetová informační služba](deploying-an-internet-information-services-hosted-wcf-service.md).

## <a name="wcf-services-and-aspnet"></a>Služby WCF a ASP.NET

Služby WCF je možné hostovat buď souběžně s ASP.NET, nebo v režimu kompatibility ASP.NET, ve kterém můžou služby plně využít funkcí poskytovaných platformou webové aplikace ASP.NET. Diskuzi o těchto funkcích najdete v tématu [WCF Services a ASP.NET](wcf-services-and-aspnet.md).

## <a name="see-also"></a>Viz také

- [Rozšíření hostování pomocí třídy ServiceHostFactory](../extending/extending-hosting-using-servicehostfactory.md)
- [Nasazení služby WCF hostované Internetovou informační službou](deploying-an-internet-information-services-hosted-wcf-service.md)
- [Služby WCF a ASP.NET](wcf-services-and-aspnet.md)
- [Doporučené postupy hostování Internetové informační služby](internet-information-services-hosting-best-practices.md)
- [Konfigurace Internetové informační služby 7.0 pro službu Windows Communication Foundation](configuring-iis-for-wcf.md)
- [Funkce hostování technologie Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
