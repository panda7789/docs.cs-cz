---
title: Konfigurace podpory protokolu WS-AT (WS-Atomic Transactions)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS-AT protocol [WCF], configuring WS-Atomic Transaction
ms.assetid: cb9f1c9c-1439-4172-b9bc-b01c3e09ac48
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 922b2048a262e722a11ee77c41e96dddec411326
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-ws-atomic-transaction-support"></a>Konfigurace podpory protokolu WS-AT (WS-Atomic Transactions)
Toto téma popisuje, jak můžete nakonfigurovat podporu protokolu WS-AtomicTransaction (WS-AT) pomocí nástroje Konfigurace služby WS-AT.  
  
## <a name="using-the-ws-at-configuration-utility"></a>Pomocí nástroje pro konfiguraci služby WS-AT  
 Nástroj WS-AT Configuration Utility (wsatConfig.exe) se používá ke konfiguraci nastavení služby WS-AT. Chcete-li povolit službu protokolu WS-AT, musíte použít nástroj pro konfiguraci ke konfiguraci HTTPS port pro WS-AT, vazbu certifikátu X.509. certifikát na HTTPS port a konfigurace certifikátů autorizovaný partner zadáním názvy předmětu certifikátu nebo kryptografické otisky certifikátů. Nástroj pro konfiguraci můžete také vybrat režimu trasování a odchozí výchozí sadu a maximální časový limit příchozí transakce.  
  
 Tento nástroj funkce dostanete pomocí modul snap-in konzoly Microsoft Management Console (MMC) vlastnost stránky v konzole pro správu služby komponent nebo z okna příkazového řádku. Konfigurace podpory protokolu WS-AT v místním počítači pomocí okna příkazového řádku; Nakonfigurujte nastavení na místních i vzdálených počítačů pomocí modulu snap-in konzoly MMC.  
  
 Okno příkazového řádku jsou přístupné z umístění instalace sady Windows SDK "%WINDIR%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation".  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Nástroj příkazového řádku najdete v části [WS-AtomicTransaction Configuration Utility (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md).  
  
 Pokud používáte [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nebo [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], můžete přístup k modulu snap-in konzoly MMC přechodem na **ovládacích panelech nástroje/Component Services**, klikněte pravým tlačítkem na **Můj počítač**, a Výběr **vlastnosti**. Toto je stejné umístění, kde můžete nakonfigurovat Microsoft distribuované transakce koordinátora služba MSDTC (). Možnosti, které jsou k dispozici ke konfiguraci jsou seskupené v rámci **WS-AT** kartě. Pokud používáte systém Windows Vista nebo [!INCLUDE[lserver](../../../../includes/lserver-md.md)], modul snap-in konzoly MMC naleznete kliknutím **spustit** tlačítko a zadáním `dcomcnfg.exe` v **vyhledávání** pole. Po otevření konzoly MMC, přejděte na **Moje Computer\Distributed transakce Coordinator\Local DTC** uzel, klikněte pravým tlačítkem a vyberte **vlastnosti**. Možnosti, které jsou k dispozici ke konfiguraci jsou seskupené v rámci **WS-AT** kartě.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]modul snap-in najdete [modul Snap-in konzoly MMC WS-AtomicTransaction Configuration](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md).  
  
 Pokud chcete povolit uživatelské rozhraní nástroje, nejprve je nutné zaregistrovat soubor WsatUI.dll, který je umístěný v následující cestě  
  
 %ProgramFiles%\Microsoft SDKs\Windows\v6.0\Bin  
  
 K registraci, spusťte následující příkaz z okna příkazového řádku:  
  
 `regasm.exe /codebase WsatUI.dll`  
  
## <a name="enabling-ws-at"></a>Povolení služby WS-AT  
 Chcete-li povolit služby protokolu WS-AT uvnitř služby MSDTC pomocí portu 443 a certifikátu X.509. certifikát s privátním klíčem, která byla nainstalována v úložišti místního počítače, použijte nástroj wsatConfig.exe pomocí následujícího příkazu.  
  
 `WsatConfig.exe –network:enable –port:8443 –endpointCert:<machine|"Issuer\SubjectName"> -accountsCerts:<thumbprint|"Issuer\SubjectName"> -restart`  
  
 Nahraďte příslušnými parametry s hodnotami, které jsou relevantní pro vaše prostředí.  
  
 Chcete-li zakázat službu protokolu WS-AT uvnitř služby MSDTC, použijte nástroj wsatConfig.exe pomocí následujícího příkazu.  
  
 `WsatConfig.exe –network:disable -restart`  
  
## <a name="configuring-trust-between-two-machines"></a>Konfigurace vztahu důvěryhodnosti mezi dva počítače  
 Služba protokolu WS-AT vyžaduje správce explicitně autorizovat jednotlivých účtů k účastnit v distribuovaných transakcích. Pokud jste správce pro dva počítače, můžete nakonfigurovat oba počítače k navázání vztahu důvěryhodnosti vzájemné výměna správnou sadu certifikátů mezi počítači, nainstalujete je do úložiště příslušné certifikátů a pomocí Nástroj wsatConfig.exe přidání certifikátu pro každý počítač do jiného seznam autorizovaných účastnické certifikátů. Tento krok je nutný k provedení distribuované transakce mezi dvěma počítači pomocí protokolu WS-AT.  
  
 Následující příklad popisuje kroky k vybudování důvěry mezi dva počítače, A a B.  
  
### <a name="creating-and-exporting-certificates"></a>Vytváření a exportování certifikátů  
 Tento postup vyžaduje modulu snap-in Certifikáty konzoly MMC. Modul snap-in přístupná otevření nabídky Start nebo spustit, zadejte text "konzoly mmc" do vstupního pole a kliknutím na tlačítko OK. Potom v **Konzola1** okno, přejděte na **soubor nebo přidat nebo odebrat** modul Snap-in klikněte na tlačítko Přidat a vyberte **certifikáty** z **k dispozici samostatná Moduly snap-in** seznamu. Nakonec vyberte **účet počítače** Správa a klikněte na tlačítko **OK**. **Certifikáty** uzel se objeví v modulu snap-in konzoly.  
  
 Musíte již mít požadované certifikáty k navázání vztahu důvěryhodnosti. Informace o vytvoření a nové certifikáty před následující kroky instalace najdete v tématu [postupy: vytvoření a nainstalovat dočasné klientské certifikáty ve WCF během vývoj](http://go.microsoft.com/fwlink/?LinkId=158925).  
  
1.  Na počítač A pomocí importu modulu snap-in Certifikáty konzoly MMC existující certifikát (certA) do LocalMachine\MY (osobní uzel) a úložiště LocalMachine\ROOT (důvěryhodné kořenové certifikační autority uzel). Chcete-li importovat certifikát na konkrétním uzlu, klikněte pravým tlačítkem na uzel a zvolte **všechny úlohy nebo importovat**.  
  
2.  Na počítači B, pomocí modulu snap-in Certifikáty konzoly MMC vytvořit nebo získat certB certifikátu s privátním klíčem a importujte ho do LocalMachine\MY (osobní uzel) a úložiště LocalMachine\ROOT (důvěryhodné kořenové certifikační autority uzel).  
  
3.  Pokud to dosud neučinili, exportujte do souboru na certA veřejný klíč.  
  
4.  Pokud to dosud neučinili, exportujte do souboru na certB veřejný klíč.  
  
### <a name="establishing-mutual-trust-between-machines"></a>Navázání vzájemného vztahu důvěryhodnosti mezi počítači  
  
1.  Na počítači A naimportujte do úložiště LocalMachine\MY a LocalMachine\ROOT reprezentace souboru certB. To deklaruje, že počítač certB vztahy důvěryhodnosti pro komunikaci s ním.  
  
2.  Na počítači B certA na soubor importujte do úložiště LocalMachine\MY a LocalMachine\ROOT. To znamená, že počítač B certA vztahy důvěryhodnosti pro komunikaci s ním.  
  
 Po dokončení těchto kroků, je navázán vztah důvěryhodnosti mezi dvěma počítači a dá se nakonfigurovat navzájem komunikují pomocí protokolu WS-AT.  
  
### <a name="configuring-msdtc-to-use-certificates"></a>Konfigurace služby MS DTC používat certifikáty  
 Vzhledem k tomu, že služba protokolu WS-AT funguje jako klient a server, musí oba přijímat příchozí připojení a zahájit odchozí připojení. Proto musíte nakonfigurovat služby MSDTC tak, aby věděl, že může který certifikát má použít při komunikaci s externími uživateli a které certifikáty k autorizaci při přijetí příchozí komunikaci.  
  
 To můžete nakonfigurovat pomocí modulu snap-in konzoly MMC WS-AT. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Tento nástroj najdete [modul Snap-in konzoly MMC WS-AtomicTransaction Configuration](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md) tématu. Následující kroky popisují, jak k navázání vztahu důvěryhodnosti mezi dvěma počítači spuštěna služba MSDTC.  
  
1.  Nakonfigurujte nastavení počítače na. "Certifikát koncového bodu" Vyberte certA. Pro "Oprávnění certifikáty" Vyberte certB.  
  
2.  Nakonfigurujte počítač B. "Certifikát koncového bodu" Vyberte certB. Pro "Oprávnění certifikáty" Vyberte certA.  
  
> [!NOTE]
>  Když jeden počítač odešle zprávu do jiných počítačů, pokusí se odesílatel ověřte, jestli název předmětu certifikátu příjemce a název počítače příjemce odpovídají. Pokud se neshodují, certifikát ověření selže a dva počítače nemohou komunikovat.  
>   
>  Pro počítač připojený k doméně je název s plně kvalifikovaným názvem domény. Ve výchozím nastavení je název počítače v pracovní skupině název pro rozhraní NetBIOS počítače. Název může také mohou obsahovat příponu systému DNS (Domain Name)-Pokud je k dispozici pro připojení používá mezi dvěma počítači.  
>   
>  Pokud se změní název počítače, například při připojení k doméně, počítač pracovní skupiny musí obnášet opětovné vystavení certifikátů nebo ručně nakonfigurovat přípony DNS.  
  
## <a name="security"></a>Zabezpečení  
 Vzhledem k tomu, že některá nastavení týkající se služby MS DTC a WS-AT jsou uložené v registru v HKLM\Software\Microsoft\MSDTC a HKLM\Software\Microsoft\WSAT, v uvedeném pořadí, ujistěte se, že jsou tyto klíče registru zabezpečené tak, aby k nim lze zapisovat pouze správci. V nástroji Editor registru, klikněte pravým tlačítkem na klíč, který chcete zabezpečit a vyberte **oprávnění** o nastavení ovládacího prvku odpovídající přístup. Je velmi důležité pro zabezpečení a integrity systému, který důležité klíče jsou jen pro čtení pro uživatele s nízkými oprávněními.  
  
 Při nasazování služby MSDTC, Správce musí zajistěte, aby byl žádné výměnu dat služby MSDTC zabezpečené. V pracovní skupině nasazení izolovat transakční infrastruktury z uživatelé se zlými úmysly; v nasazení clusteru Zabezpečte registru clusteru.  
  
## <a name="tracing"></a>Trasování  
 Integrovaná služba podporuje protokol WS-AT, transakce konkrétní trasování, která můžete povolit a spravovat prostřednictvím [modul Snap-in konzoly MMC WS-AtomicTransaction Configuration](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md) nástroj.  Trasování může obsahovat data oznamující, že byl přijat v době zařazení se provádí pro konkrétní transakci, čas transakce dosáhne stavu terminálu, výsledek každé zařazení transakce. Všechny trasování lze zobrazit pomocí [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) nástroj.  
  
 Služba protokolu WS-AT také podporuje integrované sledování ServiceModel v relaci trasování ETW. To poskytuje podrobnější, specifické pro komunikaci trasování kromě existujícím trasování transakce.  Pokud chcete povolit tyto další trasování, postupujte podle těchto kroků  
  
1.  Otevřete **spuštění a spuštění** nabídce do vstupního pole zadejte "regedit" a vyberte **OK**.  
  
2.  V **Editor registru**, přejděte do následující složky, v levém podokně, Hkey_Local_Machine\SOFTWARE\Microsoft\WSAT\3.0\  
  
3.  Klikněte pravým tlačítkem `ServiceModelDiagnosticTracing` hodnotu v pravém podokně a vyberte **upravit**.  
  
4.  V **údaj hodnoty** vstupní pole, zadejte jednu z následujících hodnot platný k určení úrovně trasování, které chcete povolit.  
  
-   0: vypnuto  
  
-   1: kritické  
  
-   3: Chyba. Toto je výchozí hodnota  
  
-   7: upozornění  
  
-   15: informace  
  
-   31: verbose  
  
## <a name="see-also"></a>Viz také  
 [Nástroj pro konfiguraci WS-AtomicTransaction (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)  
 [Modul snap-in konzoly MMC pro konfiguraci WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md)
