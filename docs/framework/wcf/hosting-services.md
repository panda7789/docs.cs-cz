---
title: Služby hostování
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF]
ms.assetid: 192be927-6be2-4fda-98f0-e513c4881acc
ms.openlocfilehash: b914d5d9f578c5ce13dfc1c520f1b26f8af1fa76
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837919"
---
# <a name="hosting-services"></a>Hostingové služby

Aby bylo možné stát aktivní, musí být služba hostována v prostředí runtime, které je vytvoří a řídí její kontext a dobu života. Služba Windows Communication Foundation (WCF) je navržena tak, aby běžela v jakémkoli procesu systému Windows, který podporuje spravovaný kód.

WCF nabízí jednotný programovací model pro vytváření aplikací orientovaných na služby. Tento programovací model zůstává konzistentní a je nezávislý na běhovém prostředí, ve kterém je služba nasazená. V praxi to znamená, že kód pro vaše služby vypadá stejně jako možnost hostování.

Tyto možnosti hostování se spouštějí v rámci konzolové aplikace na serverová prostředí, jako je například služba systému Windows spuštěná v pracovním procesu spravovaném pomocí Internetová informační služba (IIS) nebo aktivační služby procesů systému Windows (WAS). Vývojáři si vyberou hostující prostředí, které splňuje požadavky na nasazení služby. Tyto požadavky mohou být odvozeny z platformy, na které je aplikace nasazena, přenosu, na kterém je nutné odesílat a přijímat zprávy, nebo na základě typu recyklace procesu a jiné správy procesů, která je nutná k zajištění náležité dostupnosti nebo na některých jiné požadavky na správu nebo spolehlivost. V další části najdete informace a pokyny k možnostem hostování.

## <a name="hosting-options"></a>Možnosti hostování

### <a name="self-host-in-a-managed-application"></a>Samoobslužné hostování ve spravované aplikaci
 Služby WCF je možné hostovat v jakékoli spravované aplikaci. Tato možnost je nejpružnější, protože vyžaduje, aby se nasadila minimální infrastruktura. Kód pro službu vložíte do spravovaného kódu aplikace a pak vytvoříte a otevřete instanci <xref:System.ServiceModel.ServiceHost>, aby služba byla k dispozici. Další informace najdete v tématu [Postup: hostování služby WCF ve spravované aplikaci](how-to-host-a-wcf-service-in-a-managed-application.md).

 Tato možnost umožňuje dva běžné scénáře: služby WCF běžící uvnitř konzolových aplikací a bohatých klientských aplikací, jako jsou například na základě Windows Presentation Foundation (WPF) nebo model Windows Forms (WinForms). Hostování služby WCF v konzolové aplikaci je obvykle užitečné během fáze vývoje aplikace. Díky tomu se dají snadno ladit, snadno získat trasovací informace a zjistit, co se děje uvnitř aplikace, a snadno se pohybovat, když je zkopírujete do nových umístění. Tato možnost hostování také usnadňuje použití bohatých klientských aplikací, jako jsou WPF a WinForms, ke komunikaci s vnějším světem. Například klient pro spolupráci Peer-to-peer, který používá WPF pro své uživatelské rozhraní a také hostuje službu WCF, která umožňuje ostatním klientům připojit se k němu a sdílet informace.

### <a name="managed-windows-services"></a>Spravované služby systému Windows
 Tato možnost hostování se skládá z registrace domény aplikace (AppDomain), která je hostitelem služby WCF, jako spravované služby systému Windows (dříve označované jako služba NT), aby byla doba života této služby řízena správcem řízení služeb (SCM) pro Služby systému Windows. Podobně jako u možnosti samoobslužné hostování tento typ hostitelského prostředí vyžaduje, aby byl jako součást aplikace napsán nějaký hostitelský kód. Služba je implementována jako služba systému Windows a jako služba WCF tím, že by dědila z třídy <xref:System.ServiceProcess.ServiceBase> a také z rozhraní kontraktu služby WCF. <xref:System.ServiceModel.ServiceHost> je pak vytvořen a otevřen v přepsané <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> metodě a uzavřen v rámci přepsané <xref:System.ServiceProcess.ServiceBase.OnStop> metody. Aby bylo možné program nainstalovat jako službu systému Windows pomocí nástroje Installutil. exe, musí být také implementována Instalační třída, která dědí z <xref:System.Configuration.Install.Installer>. Další informace najdete v tématu [Postup: hostování služby WCF ve spravované službě systému Windows](./feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md). Scénář povolený možností hostování spravované služby systému Windows je to, že dlouhodobě běžící služba WCF hostovaná mimo službu IIS v zabezpečeném prostředí, které není aktivované zprávou. Doba života služby se místo toho řídí operačním systémem. Tato možnost hostování je k dispozici ve všech verzích Windows.

### <a name="internet-information-services-iis"></a>Internet Information Services (IIS)
 Možnost hostování služby IIS je integrovaná s ASP.NET a používá funkce, které nabízejí tyto technologie, jako je recyklace procesů, nečinné vypnutí, monitorování stavu procesu a aktivace na základě zpráv. V operačních systémech [!INCLUDE[wxp](../../../includes/wxp-md.md)] a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] je toto preferované řešení pro hostování aplikací webové služby, které musí být vysoce dostupné a vysoce škálovatelné. Služba IIS také nabízí integrovanou spravovatelnost, kterou zákazníci očekávají od produktového serveru podnikové třídy. Tato možnost hostování vyžaduje, aby služba IIS byla správně nakonfigurovaná, ale nevyžaduje, aby se veškerý hostitelský kód napsal jako součást aplikace. Další informace o tom, jak nakonfigurovat hostování služby IIS pro službu WCF, najdete v tématu [How to: Host a WCF Service in IIS](./feature-details/how-to-host-a-wcf-service-in-iis.md).

 Služby hostované službou IIS můžou používat jenom přenos HTTP. Jeho implementace ve službě IIS 5,1 zavedla určitá omezení [!INCLUDE[wxp](../../../includes/wxp-md.md)]. Aktivace založená na zprávách poskytovaná službou WCF 5,1 na [!INCLUDE[wxp](../../../includes/wxp-md.md)] blokuje všechny ostatní samoobslužné služby WCF ve stejném počítači, aby komunikovaly pomocí portu 80. Služby WCF lze spustit ve stejné doméně nebo fondu aplikací nebo pracovním procesu jako jiné aplikace, pokud jsou hostovány službou IIS 6,0 na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]. Vzhledem k tomu, že WCF a IIS 6,0 obě používají zásobník HTTP v režimu jádra (HTTP. sys), služba IIS 6,0 může sdílet port 80 s ostatními místně hostovanými službami WCF běžícími na stejném počítači, na rozdíl od služby IIS 5,1.

### <a name="windows-process-activation-service-was"></a>Aktivační služba procesů systému Windows (WAS)
 Aktivační služba procesů systému Windows (WAS) je nový mechanismus aktivace procesu pro [!INCLUDE[lserver](../../../includes/lserver-md.md)], která je také k dispozici v systému Windows Vista. Zachovává známý model procesu služby IIS 6,0 (fondy aplikací a aktivace procesů založené na zprávách) a funkce hostování (například rychlá ochrana při selhání, monitorování stavu a recyklace), ale odstraní závislost na HTTP z aktivace. Architektura. Služba IIS 7,0 používala k provedení aktivace založené na zprávách přes HTTP. K dalším součástem WCF se taky připojíte tak, aby poskytovaly aktivaci na základě zpráv přes jiné protokoly, které podporuje WCF, jako je například TCP, MSMQ a pojmenované kanály. To umožňuje aplikacím, které používají komunikační protokoly, používat funkce služby IIS, jako je recyklace procesů, rychlá ochrana proti selhání a společný konfigurační systém, který byl dostupný jenom pro aplikace založené na protokolu HTTP.

 Tato možnost hostování vyžaduje, aby byla správně nakonfigurovaná, ale nevyžaduje, abyste v rámci aplikace napsali žádný hostující kód. Další informace o tom, jak nakonfigurovat hostování, najdete v tématu [How to: Host a WCF Service in was](./feature-details/how-to-host-a-wcf-service-in-was.md).

## <a name="choose-a-hosting-environment"></a>Zvolit hostitelské prostředí
 Následující tabulka shrnuje některé klíčové výhody a scénáře spojené s jednotlivými možnostmi hostování.

|Hostitelské prostředí|Typické scénáře|Klíčové výhody a omezení|
|-------------------------|----------------------|----------------------------------|
|Spravovaná aplikace (místní hostování)|-Konzolové aplikace používané během vývoje.<br />– Rich DataGridView a klientské aplikace WPF přistupující ke službám.|Disket.<br />– Snadné nasazení.<br />– Nejedná se o podnikové řešení pro služby.|
|Služby systému Windows (dřív označované jako služby NT)|– Dlouhodobě běžící služba WCF hostovaná mimo službu IIS.|– Služba neaktivuje dobu života procesu řízenou operačním systémem, nikoli zprávou.<br />– Podporováno všemi verzemi systému Windows.<br />– Zabezpečení prostředí.|
|IIS 5.1, IIS 6.0|– Souběžně běžící služba WCF s ASP.NET obsahem na internetu pomocí protokolu HTTP.|– Zpracování recyklace.<br />-Nečinné vypnutí.<br />– Monitorování stavu procesu.<br />– Aktivace založená na zprávách.<br />– Jenom HTTP.|
|Aktivační služba procesů systému Windows (WAS)|– Spuštění služby WCF bez instalace IIS na internetu s použitím různých přenosových protokolů.|– Služba IIS se nevyžaduje.<br />– Zpracování recyklace.<br />-Nečinné vypnutí.<br />– Monitorování stavu procesu.<br />– Aktivace založená na zprávách.<br />– Funguje s HTTP, TCP, Named Pipes a MSMQ.|
|Internetová informační služba 7,0|– Spuštění služby WCF s obsahem ASP.NET<br />– Spuštění služby WCF na internetu s použitím různých přenosových protokolů.|– WAS výhody.<br />– Integrováno s obsahem ASP.NET a IIS.|

 Volba hostitelského prostředí závisí na verzi systému Windows, ve které je nasazena, přesměruje, že vyžaduje odeslání zprávy a typ recyklace domény aplikace, kterou vyžaduje. Následující tabulka shrnuje data týkající se těchto požadavků.

|Hostitelské prostředí|Dostupnost platformy|Podporované přenosy|Recyklace procesů a AppDomain|
|-------------------------|---------------------------|--------------------------|-------------------------------------|
|Spravované aplikace (místní hostování)|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], Windows Vista,<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> NET. TCP,<br /><br /> NET. pipe,<br /><br /> NET. MSMQ|Ne|
|Služby systému Windows (dřív označované jako služby NT)|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], Windows Vista,<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> NET. TCP,<br /><br /> NET. pipe,<br /><br /> NET. MSMQ|Ne|
|IIS 5.1|[!INCLUDE[wxp](../../../includes/wxp-md.md)]|HTTP|Ano|
|Internetová informační služba 6.0|[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]|HTTP|Ano|
|Aktivační služba procesů systému Windows (WAS)|Windows Vista, [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> NET. TCP,<br /><br /> NET. pipe,<br /><br /> NET. MSMQ|Ano|

 Je důležité si uvědomit, že při používání služby nebo jakéhokoli rozšíření z nedůvěryhodného hostitele dojde k ohrožení zabezpečení. Všimněte si také, že při otevření <xref:System.ServiceModel.ServiceHost> v oblasti zosobnění musí aplikace zajišťovat, že uživatel není odhlášený, například ukládáním <xref:System.Security.Principal.WindowsIdentity> uživatele do mezipaměti.

## <a name="see-also"></a>Viz také:

- [Základní programovací životní cyklus](basic-programming-lifecycle.md)
- [Implementace kontraktů služeb](implementing-service-contracts.md)
- [Postupy: Hostování služby WCF v IIS](./feature-details/how-to-host-a-wcf-service-in-iis.md)
- [Postupy: Hostování služby WCF ve WAS](./feature-details/how-to-host-a-wcf-service-in-was.md)
- [Postupy: Hostování služby WCF ve spravované službě Windows](./feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)
- [Postupy: Hostování služby WCF ve spravované aplikaci](how-to-host-a-wcf-service-in-a-managed-application.md)
