---
title: Služby hostování
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF]
ms.assetid: 192be927-6be2-4fda-98f0-e513c4881acc
ms.openlocfilehash: 2d926fb3f630d2a1af00242f94ddcb3c2dc284df
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170058"
---
# <a name="hosting-services"></a>Služby hostování
Přejít do aktivního stavu, musí být služba hostovaný v rámci prostředí za běhu, která ho vytvoří a řídí jeho kontextu a životnosti. Služby Windows Communication Foundation (WCF) slouží ke spouštění v jakýkoli proces Windows, že podporuje spravovaného kódu.  
  
 WCF poskytuje jednotný programovací model pro vytváření aplikací orientovaných na služby. Tento model programování konzistentní a je nezávislý na běhové prostředí, ve kterém je služba nasazená. V praxi to znamená, že kód pro vaše služby vypadá podobně stejný bez ohledu možnost hostování.  
  
 Tyto možnosti v rozsahu od běží uvnitř konzolovou aplikaci pro prostředí serveru jako službu Windows v rámci pracovní proces spravované Internetové informační služby (IIS) nebo pomocí Windows WAS Process Activation Service () pro hostování. Vývojáři zvolit hostitelské prostředí, která splňuje požadavky na nasazení služby. Tyto požadavky může být odvozen z platformy, na kterém je aplikace nasazená, přenosu, na kterém musí odesílat a přijímat zprávy, nebo na typ recyklace procesů a další správa procesů, vyžaduje se pro zajištění adekvátní dostupnosti nebo u některých Další požadavky pro správu a spolehlivosti. Další část obsahuje informace a pokyny k možnosti hostování.  
  
## <a name="hosting-options"></a>Možnosti hostování  
  
#### <a name="self-hosting-in-a-managed-application"></a>Samoobslužné hostování ve spravované aplikaci  
 Služby WCF je možné hostovat v žádné spravované aplikace. To je nejflexibilnější možností, protože vyžaduje minimálně infrastrukturu pro nasazení. Kód služby do spravované aplikace kódu pro vložení a pak vytvořte a spusťte instanci <xref:System.ServiceModel.ServiceHost> aby tato služba k dispozici. Další informace najdete v tématu [jak: Hostování služby WCF ve spravované aplikaci](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Tato možnost povolí dvě běžné scénáře: WCF služby spuštěné v konzolových aplikací a aplikacemi rich client například algoritmů založených na Windows Presentation Foundation (WPF) nebo Windows Forms (WinForms). Hostování služby WCF v konzolové aplikaci je obvykle vhodné v průběhu fáze vývoje aplikace. Díky tomu je snadné ladění, snadno získat informace o trasování z a zjistěte, co se děje v rámci aplikace a snadno přesouvat jejich zkopírováním do nového umístění. Tato možnost hostování také usnadňuje aplikacemi rich client, jako jsou třeba aplikace WPF a WinForms komunikovat s vnějším světem. Například nastavení spolupráci peer-to-peer klienta, který používá pro jeho uživatelské rozhraní WPF a také hostuje službu WCF, která umožňuje dalším klientům připojit se k němu a sdílení informací.  
  
#### <a name="managed-windows-services"></a>Služby spravované Windows  
 Tato možnost hostování se skládá z registraci domény aplikace (AppDomain), který je hostitelem služby WCF je spravovaná služba Windows (dříve označované jako služby NT) tak, že doba platnosti procesu služby se řídí správce řízení služeb (SCM) Služby Windows. Jako možnost samoobslužné hostování tento typ hostitelské prostředí vyžaduje, aby hostování kódu je zapsán jako součást aplikace. Služba je implementováno jako služby Windows a služby WCF by ji zdědit <xref:System.ServiceProcess.ServiceBase> třídy a také ze WCF služby rozhraní kontraktu. <xref:System.ServiceModel.ServiceHost> Se pak vytvoří a otevře v rámci překryté <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> metoda a zavření v rámci překryté <xref:System.ServiceProcess.ServiceBase.OnStop> metoda. Instalační třída, která dědí z <xref:System.Configuration.Install.Installer> musí zprostředkovatel také implementovat umožníte aplikaci nainstalovat jako službu Windows pomocí nástroje Installutil.exe. Další informace najdete v tématu [jak: Hostování služby WCF ve spravované Windows Service](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md). Scénář umožněné spravované služby Windows možnost hostování je dlouho běžící služby WCF hostované mimo službu IIS v zabezpečeném prostředí, která aktivuje zpráva není. Doba platnosti služby je místo toho řídí operační systém. Tato možnost hostování je k dispozici ve všech verzích Windows.  
  
#### <a name="internet-information-services-iis"></a>Internet Information Services (IIS)  
 Možnost hostování služby IIS je integrovaná s technologií ASP.NET a používá funkce, které nabízí tyto technologie, jako je například recyklace, nečinnosti ukončení procesu, proces monitorování stavu a aktivaci založenou na zprávách. Na [!INCLUDE[wxp](../../../includes/wxp-md.md)] a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] operačních systémů, toto je preferovaným řešením pro hostování webových aplikací služby, které musí být vysoce dostupné a vysoce škálovatelné. Služba IIS také nabízí integrované možnosti správy, které zákazníci očekávat od o produkt poskytovaný jako server podnikové úrovně. Tato možnost hostování vyžaduje, aby byly správně konfigurovány služby IIS, ale nevyžaduje, že libovolný kód hostování se zapisují jako součást aplikace. Další informace o tom, jak nakonfigurovat službu IIS hostování služby WCF, naleznete v tématu [jak: Hostování služby WCF v IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
 Všimněte si, že služby hostované v IIS lze použít pouze přenos pomocí protokolu HTTP. Jeho implementace v IIS 5.1 přináší určitá omezení v [!INCLUDE[wxp](../../../includes/wxp-md.md)]. Poskytuje pro služby WCF, služba IIS 5.1 na aktivaci založenou na zprávách [!INCLUDE[wxp](../../../includes/wxp-md.md)] blokuje jakékoli jiné v místním prostředí služby WCF ve stejném počítači z přes port 80 pro komunikaci. Služby WCF můžete spustit ve stejném procesu fondu/pracovního procesu domény aplikace/aplikace jako ostatní aplikace, když jsou hostované ve [!INCLUDE[iis601](../../../includes/iis601-md.md)] na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]. Ale protože WCF a [!INCLUDE[iis601](../../../includes/iis601-md.md)] používají zásobník v režimu jádra HTTP (HTTP.sys), [!INCLUDE[iis601](../../../includes/iis601-md.md)] můžete nasdílet další v místním prostředí služby WCF, které jsou spuštěné ve stejném počítači, na rozdíl od služba IIS 5.1 port 80.  
  
#### <a name="windows-process-activation-service-was"></a>Aktivační služba procesů Windows (WAS)  
 Aktivační služba procesů Windows (WAS) je nový mechanismus procesu aktivace pro [!INCLUDE[lserver](../../../includes/lserver-md.md)] , který je k dispozici také na [!INCLUDE[wv](../../../includes/wv-md.md)]. Zachová známé [!INCLUDE[iis601](../../../includes/iis601-md.md)] model procesu (fondy aplikací a aktivaci založenou na zprávách procesu) a ve hostování funkcí (třeba rychlou ochranu, monitorování stavu a recyklaci), ale eliminuje závislost na HTTP z aktivace Architektura. [!INCLUDE[iisver](../../../includes/iisver-md.md)] používá WAS provést aktivaci na základě zpráv přes protokol HTTP. Další součásti WCF také pružný WAS k poskytování aktivaci založenou na zprávách přes protokoly, které podporuje WCF, jako je například TCP, MSMQ a pojmenované kanály. Díky tomu, že aplikace, které používají komunikační protokoly používat funkce služby IIS jako je například recyklace procesů, rychlé selhání ochrany a společné konfigurační systém, které byly k dispozici pro aplikace založené na protokolu HTTP.  
  
 Vyžaduje tato možnost hostování, který byl být správně nakonfigurovaný, ale nevyžaduje psaní jakéhokoli hostování kódu jako součást aplikace. Hostování se další informace o tom, jak konfigurovat, najdete v části [jak: Hostování služby WCF ve WAS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
## <a name="choosing-a-hosting-environment"></a>Výběr hostitelské prostředí  
 Následující tabulka shrnuje některé z klíčových výhod a scénářů, které jsou spojené s každou z možností hostování.  
  
|Hostitelské prostředí|Obvyklé scénáře|Mezi klíčové výhody a omezení|  
|-------------------------|----------------------|----------------------------------|  
|Spravované aplikace ("v místním prostředí")|-Konzolové aplikace použít během vývoje.<br />– Formuláře Windows bohaté a klientské aplikace WPF přístup ke službám.|-Flexibilní.<br />-Snadné nasazení.<br />-Není podnikové řešení pro služby.|  
|Služby Windows (dříve známé jako služby NT)|– Dlouhodobé služby WCF hostované mimo službu IIS.|– Doba platnosti procesu služba řídí operační systém není aktivována zpráva.<br />-Podporovány všemi verzemi Windows.<br />– Zabezpečené prostředí.|  
|IIS 5.1, [!INCLUDE[iis601](../../../includes/iis601-md.md)]|– Spouštění služby WCF vedle sebe s obsahem ASP.NET na Internetu pomocí protokolu HTTP.|– Recyklace procesu.<br />-Nečinnosti vypnutí.<br />-Zpracování monitorování stavu.<br />-Založenou na zprávách aktivace.<br />-Pouze protokolu HTTP.|  
|Aktivační služba procesů Windows (WAS)|– Spouštění služby WCF bez instalace služby IIS na Internetu s použitím různé přenosové protokoly.|-Služby IIS se nevyžaduje.<br />– Recyklace procesu.<br />-Nečinnosti vypnutí.<br />-Zpracování monitorování stavu.<br />-Založenou na zprávách aktivace.<br />-Funguje přes protokol HTTP, TCP, pojmenované kanály a služby MSMQ.|  
|Internetová informační služba 7,0|– Spouštění služby WCF s obsahem technologie ASP.NET.<br />– Spouštění služby WCF na Internetu s použitím různé přenosové protokoly.|-BYLO výhody.<br />– Integrované s ASP.NET a IIS obsahem.|  
  
 Volba hostitelské prostředí závisí na verzi Windows, na kterém je nasazený, přenosy vyžaduje k odesílání zpráv a typ procesu a recyklace domény aplikací, které vyžaduje. Následující tabulka shrnuje data související s těmito požadavky.  
  
|Hostitelské prostředí|Dostupnost platformy|Přenosy podporována|Proces a recyklace domény aplikace|  
|-------------------------|---------------------------|--------------------------|-------------------------------------|  
|Spravované aplikace ("v místním prostředí")|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> NET.TCP,<br /><br /> NET.pipe,<br /><br /> net.msmq|Ne|  
|Služby Windows (dříve známé jako služby NT)|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> NET.TCP,<br /><br /> NET.pipe,<br /><br /> net.msmq|Ne|  
|IIS 5.1|[!INCLUDE[wxp](../../../includes/wxp-md.md)]|HTTP|Ano|  
|[!INCLUDE[iis601](../../../includes/iis601-md.md)]|[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]|HTTP|Ano|  
|Aktivační služba procesů Windows (WAS)|[!INCLUDE[wv](../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> NET.TCP,<br /><br /> NET.pipe,<br /><br /> net.msmq|Ano|  
  
 Je důležité si uvědomit, že spuštěné služby nebo žádné rozšíření z ohrožení zabezpečení nedůvěryhodného hostitele. Mějte také na paměti, která při otevírání <xref:System.ServiceModel.ServiceHost> v zosobnění, musí aplikace zajistit, že uživatel není odhlášen, například díky ukládání do mezipaměti <xref:System.Security.Principal.WindowsIdentity> uživatele.  
  
## <a name="see-also"></a>Viz také:

- [Požadavky na systém](../../../docs/framework/wcf/wcf-system-requirements.md)
- [Základní programovací životní cyklus](../../../docs/framework/wcf/basic-programming-lifecycle.md)
- [Implementace kontraktů služeb](../../../docs/framework/wcf/implementing-service-contracts.md)
- [Postupy: Hostování služby WCF v IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
- [Postupy: Hostování služby WCF ve WAS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)
- [Postupy: Hostování služby WCF ve spravované Windows Service](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)
- [Postupy: Hostování služby WCF ve spravované aplikaci](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
