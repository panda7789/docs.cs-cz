---
title: "Služby hostování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: hosting services [WCF]
ms.assetid: 192be927-6be2-4fda-98f0-e513c4881acc
caps.latest.revision: "31"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c0d3cd2f53b81ae6114baa3c7eedd899126ed579
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="hosting-services"></a>Služby hostování
Stane aktivní, musí být hostované služby v rámci běhové prostředí, která ji vytvoří a určuje jeho kontextu a doba platnosti. [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]služby jsou určený ke spouštění v jakýkoli proces systému Windows, že podporuje spravovaného kódu.  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]poskytuje jednotný programovací model pro vytváření aplikací orientovaných na služby. Tento programovací model konzistentní a je nezávislý běhové prostředí nasazení služby. V praxi to znamená, že kód pro vaše služby vypadá mnohem stejný bez ohledu možnosti hostování.  
  
 Tyto hostování rozsah možnosti z běžících v rámci aplikace konzoly do prostředí serveru, jako je Windows služba spuštěná, a to v rámci pracovní proces spravované pomocí Internetové informační služby (IIS) nebo pomocí procesu aktivace služby WAS (Windows). Vývojáři zvolte hostitelské prostředí, který splňuje požadavky na nasazení služby. Tyto požadavky může být odvozen z platformy, na kterém je aplikace nasazená, přenos se musí odesílat a přijímat zprávy, nebo na typ recyklace procesů a další proces správy, vyžaduje se pro zajištění odpovídající dostupnosti nebo u některých Další požadavky na správu nebo spolehlivost. Následující část obsahuje informace a pokyny na hostování možnosti.  
  
## <a name="hosting-options"></a>Možnosti hostování  
  
#### <a name="self-hosting-in-a-managed-application"></a>Vlastní hostování ve spravované aplikaci  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]služby může být hostovaný ve všech spravovaných aplikací. Toto je možnost nejpružnější, protože vyžaduje minimálně infrastrukturu pro nasazování. Vložení kódu pro službu uvnitř kódu spravované aplikace a pak vytvořte a otevřete instanci <xref:System.ServiceModel.ServiceHost> chcete zpřístupnit službu. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Postupy: hostování služby WCF ve spravované aplikaci](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Tato možnost umožňuje dvě běžné scénáře: [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] na základě služeb běžících v rámci konzolové aplikace a plně funkčního klienta s aplikací, jako jsou [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] nebo Windows Forms (WinForms). Hostování [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] službu v konzolové aplikaci je obvykle užitečné v průběhu fáze vývoje aplikace. Díky tomu je usnadňuje ladění, lze snadno získávat informace trasování z a zjistěte, co se děje v rámci aplikace a usnadňuje pohyb zkopírováním do nového umístění. Tato možnost hostování také usnadňuje plně funkčního klienta s aplikací, například [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] a WinForms aplikace komunikovat s vnějším světem. Například peer-to-peer spolupráce klienta, který používá [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] jeho uživatelské rozhraní a také hostitelů [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] službu, která umožňuje dalším klientům připojit se k němu a sdílet informace.  
  
#### <a name="managed-windows-services"></a>Spravované služby  
 Tato možnost hostování se skládá z registraci domény aplikace (AppDomain), který je hostitelem [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby jako spravovanou službu systému Windows (dříve označované jako služba NT) tak, aby se doba platnosti procesu služby řídí správce řízení služeb (SCM) pro služby systému Windows. Jako možnost samoobslužné hostování tento typ hostování prostředí vyžaduje, že některé hostování kódu je zapsána jako součást aplikace. Služba se implementuje jako obě služby systému Windows a jako [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby tak, že ho dědění z <xref:System.ServiceProcess.ServiceBase> třída také jako z [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] rozhraní kontraktu služby. <xref:System.ServiceModel.ServiceHost> Se potom vytvoří a otevřít v rámci překryté <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> metoda a ukončeny během překryté <xref:System.ServiceProcess.ServiceBase.OnStop> metoda. Instalační třída, která dědí z <xref:System.Configuration.Install.Installer> musí zprostředkovatel taky implementovat povolit program, který chcete nainstalovat nástroj Installutil.exe jako služby systému Windows. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Postupy: hostování služby WCF ve spravované službě Windows](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md). Scénář ve spravované služby systému Windows, hostování možnost povolená, je dlouho běžící [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby hostované v zabezpečeném prostředí, která není aktivované mimo služby IIS. Doba platnosti služby místo toho řídí operační systém. Tento hostitelský možnost je dostupná ve všech verzích systému Windows.  
  
#### <a name="internet-information-services-iis"></a>Internet Information Services (IIS)  
 Možností hostování služby IIS je integrovaná s [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] a používá funkce nabízí tyto technologie, jako je například recyklace, nečinnosti ukončení procesu, monitorování stavu procesu a aktivaci na základě zpráv. Na [!INCLUDE[wxp](../../../includes/wxp-md.md)] a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] operační systémy, toto je upřednostňovaný řešení pro hostování aplikací webové služby, které musí být vysoce dostupné a vysoce škálovatelné. Služba IIS také nabízí integrované možnosti správy, které zákazníci očekávají o podnikových serveru produkt. Tato možnost hostování vyžaduje, aby se služba IIS správně nakonfigurovaná, ale nevyžaduje, aby všechny hostování kódu zapsání jako součást aplikace. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Postup konfigurace služby IIS pro hostování [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] najdete v tématu [postupy: hostování služby WCF ve službě IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
 Všimněte si, hostovaná IIS služby lze použít pouze přenos HTTP. Jeho implementace ve službě IIS 5.1 obsahuje zavedla určitá omezení v [!INCLUDE[wxp](../../../includes/wxp-md.md)]. Aktivace na základě zpráv poskytuje pro [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby IIS 5.1 na [!INCLUDE[wxp](../../../includes/wxp-md.md)] blokuje všechny ostatní vlastním hostováním [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby ve stejném počítači pomocí portu 80 pro komunikaci. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]služby mohou být spuštěny ve stejném fondu nebo pracovní procesu domény aplikace nebo aplikace jako ostatní aplikace, pokud je hostováno pomocí [!INCLUDE[iis601](../../../includes/iis601-md.md)] na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]. Ale protože [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] a [!INCLUDE[iis601](../../../includes/iis601-md.md)] používejte zásobníku režimu jádra protokolu HTTP (HTTP.sys), [!INCLUDE[iis601](../../../includes/iis601-md.md)] port 80 můžete sdílet s jinými hostovanou na vlastním [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby spuštěné na stejném počítači, na rozdíl od služby IIS 5.1.  
  
#### <a name="windows-process-activation-service-was"></a>Aktivační služba procesů systému Windows (WAS)  
 Aktivační služba procesů systému Windows (WAS) je nový mechanismus aktivace procesů pro [!INCLUDE[lserver](../../../includes/lserver-md.md)] , je také k dispozici na [!INCLUDE[wv](../../../includes/wv-md.md)]. Uchovává známé [!INCLUDE[iis601](../../../includes/iis601-md.md)] model procesu (fondů aplikací a na základě zpráv proces aktivace) a ve hostování funkce (například rychlou ochranu před chybami, sledování stavu a recyklaci), ale odebere závislost na protokolu HTTP z aktivace Architektura. [!INCLUDE[iisver](../../../includes/iisver-md.md)]využívá WAS k dosažení aktivace na základě zpráv přes protokol HTTP. Další [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] součásti také připojte WAS zajistit aktivace na základě zpráv z nich protokoly, které [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] podporuje, například TCP, služby MSMQ a pojmenované kanály. Díky tomu, že aplikace, které používají komunikační protokoly používat funkce služby IIS například recyklace procesů, rychlé nezdaří ochrany a systém společné konfigurace, které byly dostupné pro aplikace založené na protokolu HTTP.  
  
 Tato možnost hostování vyžaduje, který se musí být správně nakonfigurovaná, ale nevyžaduje k psaní jakéhokoli kódu hostování jako součást aplikace. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Postup konfigurace byla hostování najdete v tématu [postupy: hostování služby WCF ve WAS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
## <a name="choosing-a-hosting-environment"></a>Výběr do hostitelského prostředí  
 Následující tabulka shrnuje některé klíčové výhody a scénáře související s jednotlivými možnosti hostování.  
  
|Hostování prostředí|Běžné scénáře|Klíčové výhody a omezení|  
|-------------------------|----------------------|----------------------------------|  
|Spravované aplikace ("samoobslužně hostovaná")|-Konzolové aplikace používá během vývoje.<br />-Bohaté WinForm a [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] klientské aplikace přístup ke službám.|-Flexibilní.<br />-Snadno nasadit.<br />-Není podnikové řešení pro služby.|  
|Služby systému Windows (dříve označovaná jako služba NT)|-A dlouhodobé [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby hostované mimo služby IIS.|-Doba platnosti procesu Service řídí operační systém, není aktivována zpráva.<br />– Podporuje všechny verze systému Windows.<br />-Zabezpečeném prostředí.|  
|SLUŽBA IIS 5.1,[!INCLUDE[iis601](../../../includes/iis601-md.md)]|-Spuštěná [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby souběžného s [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] obsahu na Internetu pomocí protokolu HTTP.|-Recyklace procesu.<br />-Nečinnosti vypnutí.<br />-Zpracování sledování stavu.<br />– Na základě zpráv aktivace.<br />-Pouze HTTP.|  
|Aktivační služba procesů systému Windows (WAS)|-Spuštěná [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby bez instalace služby IIS na Internetu pomocí různých protokolů přenosu.|-Služba IIS není vyžadován.<br />-Recyklace procesu.<br />-Nečinnosti vypnutí.<br />-Zpracování sledování stavu.<br />– Na základě zpráv aktivace.<br />-Funguje přes protokol HTTP, TCP, pojmenované kanály a služby MSMQ.|  
|Internetová informační služba 7,0|-Spuštěná [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby s [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] obsah.<br />-Spuštěná [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby v síti Internet pomocí různých protokolů přenosu.|-BYL výhody.<br />– Integrované s [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] a obsahu služby IIS.|  
  
 Volba do hostitelského prostředí závisí na verzi Windows, na kterém je nasazený, přenosy vyžaduje k odesílání zpráv a typ procesu a recyklace domény aplikací, která vyžaduje. Následující tabulka shrnuje data týkající se těchto požadavků.  
  
|Hostování prostředí|Platforma dostupnosti|Přenosy podporováno|Proces a recyklace domény aplikace|  
|-------------------------|---------------------------|--------------------------|-------------------------------------|  
|Spravované aplikace ("samoobslužně hostovaná")|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|PROTOKOLU HTTP,<br /><br /> NET.TCP,<br /><br /> NET.pipe,<br /><br /> NET.MSMQ|Ne|  
|Služby systému Windows (dříve označovaná jako služba NT)|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|PROTOKOLU HTTP,<br /><br /> NET.TCP,<br /><br /> NET.pipe,<br /><br /> NET.MSMQ|Ne|  
|SLUŽBA IIS 5.1|[!INCLUDE[wxp](../../../includes/wxp-md.md)]|HTTP|Ano|  
|[!INCLUDE[iis601](../../../includes/iis601-md.md)]|[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]|HTTP|Ano|  
|Aktivační služba procesů systému Windows (WAS)|[!INCLUDE[wv](../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../includes/lserver-md.md)]|PROTOKOLU HTTP,<br /><br /> NET.TCP,<br /><br /> NET.pipe,<br /><br /> NET.MSMQ|Ano|  
  
 Je důležité si uvědomit, že spuštění služby nebo jakoukoli příponu z ohrožení zabezpečení služby nedůvěryhodné hostitele. Rovněž Pamatujte, že při otevírání <xref:System.ServiceModel.ServiceHost> v zosobnění, aplikace musí zajistit, že uživatel není odhlášením, například pomocí ukládání do mezipaměti <xref:System.Security.Principal.WindowsIdentity> uživatele.  
  
## <a name="see-also"></a>Viz také  
 [Požadavky na systém](../../../docs/framework/wcf/wcf-system-requirements.md)  
 [Základní programovací životní cyklus](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
 [Implementace kontraktů služeb](../../../docs/framework/wcf/implementing-service-contracts.md)  
 [Postupy: hostování služby WCF ve službě IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)  
 [Postupy: hostování služby WCF ve WAS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)  
 [Postupy: hostování služby WCF ve spravované službě Windows](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)  
 [Postupy: hostování služby WCF ve spravované aplikaci](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
