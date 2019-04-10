---
title: Konfigurace podpory protokolu WS-AT (WS-Atomic Transactions)
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF], configuring WS-Atomic Transaction
ms.assetid: cb9f1c9c-1439-4172-b9bc-b01c3e09ac48
ms.openlocfilehash: 987d6c12262fd6530c6ef6f14cedeec269d3f2f8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315176"
---
# <a name="configuring-ws-atomic-transaction-support"></a>Konfigurace podpory protokolu WS-AT (WS-Atomic Transactions)
Toto téma popisuje, jak můžete nakonfigurovat podporu WS-AtomicTransaction (WS-AT) pomocí nástroje Konfigurace WS-AT.  
  
## <a name="using-the-ws-at-configuration-utility"></a>Pomocí nástroje pro konfiguraci WS-AT  
 Nástroj WS-AT Configuration Utility (wsatConfig.exe) se používá ke konfiguraci nastavení WS-AT. Chcete-li povolit službu protokolu WS-AT, musíte použít nástroj pro konfiguraci nakonfigurovat HTTPS port pro WS-AT navázat certifikát X.509 na HTTPS port a konfigurace certifikátů autorizovaný partner tak, že zadáte názvy předmětu certifikátů nebo kryptografické otisky. Nástroj pro konfiguraci můžete také vybrat režimu trasování a odchozí výchozí sadu a maximální příchozí časový limit transakce.  
  
 Tento nástroj funkce se zpřístupní v konzole pro správu služby Component Services nebo z okna příkazového řádku pomocí modul snap-in konzoly Microsoft Management Console (MMC) vlastnosti stránky. Konfigurace podpory WS-AT na místním počítači pomocí okna příkazového řádku. Konfigurace nastavení na místních i vzdálených počítačích pomocí modulu snap-in konzoly MMC.  
  
 Okno příkazového řádku je možný v umístění instalace sady Windows SDK "%WINDIR%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation".  
  
 Další informace o nástroj příkazového řádku najdete v tématu [WS-AtomicTransaction Configuration Utility (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md).  
  
 Pokud používáte [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nebo [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], můžete přístup k modulu snap-in konzoly MMC tak, že přejdete do **ovládací panely/pro správu nástroje/Component Services**, pravým tlačítkem myši **tento počítač**, a Výběr **vlastnosti**. Toto je na stejném umístění, kde můžete nakonfigurovat Microsoft distribuované transakce koordinátor (MSDTC). Možnosti pro konfiguraci k dispozici jsou seskupené podle **WS-AT** kartu. Pokud používáte systém Windows Vista nebo [!INCLUDE[lserver](../../../../includes/lserver-md.md)], modul snap-in konzoly MMC najdete po kliknutí **Start** tlačítko a zadáním `dcomcnfg.exe` v **hledání** pole. Při otevření konzoly MMC, přejděte **Moje Computer\Distributed transakce Coordinator\Local DTC** uzel, klikněte pravým tlačítkem myši a vyberte **vlastnosti**. Možnosti pro konfiguraci k dispozici jsou seskupené podle **WS-AT** kartu.  
  
 Další informace o modulu snap-in, najdete v článku [modul Snap-in konzoly MMC konfigurace WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md).  
  
 Pokud chcete povolit uživatelské rozhraní nástroje, musíte se nejprve zaregistrovat soubor WsatUI.dll umístěný v následující cestě  
  
 %PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin  
  
 K registraci, spusťte následující příkaz z okna příkazového řádku:  
  
 `regasm.exe /codebase WsatUI.dll`  
  
## <a name="enabling-ws-at"></a>Povolení WS-AT  
 Povolit službu protokolu WS-AT uvnitř nástroje MSDTC pomocí portu 443 a certifikát X.509 s privátním klíčem, který je nainstalovaný v úložišti místního počítače, použijte nástroj wsatConfig.exe pomocí následujícího příkazu.  
  
 `WsatConfig.exe –network:enable –port:8443 –endpointCert:<machine|"Issuer\SubjectName"> -accountsCerts:<thumbprint|"Issuer\SubjectName"> -restart`  
  
 Nahrazení odpovídajících parametrů s hodnotami, které se vztahují k vašemu prostředí.  
  
 Zakázat službu protokolu WS-AT uvnitř MSDTC, nástrojem wsatConfig.exe pomocí následujícího příkazu.  
  
 `WsatConfig.exe –network:disable -restart`  
  
## <a name="configuring-trust-between-two-machines"></a>Konfigurace vztahu důvěryhodnosti mezi dvěma počítači  
 Služba protokolu WS-AT vyžaduje, aby správce explicitně povolit jednotlivé účty účastnit v distribuovaných transakcích. Pokud jste správce pro dva počítače, můžete nakonfigurovat oba počítače, na navázání vztahu důvěryhodnosti obousměrnou výměnu správnou sadu certifikáty mezi počítači, instalace do úložišť příslušný certifikát a použitím Nástroj wsatConfig.exe přidání certifikátu každý počítač do druhé strany seznamu autorizovaných účastníka certifikátů. Tento krok je nezbytný k provádění distribuované transakce mezi dvěma počítači pomocí WS-AT.  
  
 Následující příklad popisuje kroky k navázání vztahu důvěryhodnosti mezi dvěma počítači, A a B.  
  
### <a name="creating-and-exporting-certificates"></a>Vytvoření a export certifikátů  
 Tento postup vyžaduje modul snap-in Certifikáty konzoly MMC. Modul snap-in můžete přístup otevřením nabídky Start nebo spuštění, do vstupního pole zadáním "konzoly mmc" a kliknutím na tlačítko OK. Potom v **Konzola1** okno, přejděte na **soubor a přidat nebo odebrat** modul Snap-in klikněte na tlačítko Přidat a vybrat **certifikáty** z **k dispozici samostatná Moduly snap-in** seznamu. Nakonec vyberte **účet počítače** pro správu a klikněte na tlačítko **OK**. **Certifikáty** uzel se zobrazí v modulu snap-in konzoly.  
  
 Musíte již vlastnit požadované certifikáty k navázání vztahu důvěryhodnosti. Zjistěte, jak vytvořit a nainstalovat nové certifikáty před následující kroky, najdete v článku [jak: Vytvoření a instalace dočasné klientských certifikátů ve službě WCF při vývoji](https://go.microsoft.com/fwlink/?LinkId=158925).  
  
1. Na počítač A pomocí importu modulu snap-in Certifikáty konzoly MMC existujícího certifikátu (certA) do LocalMachine\MY (osobní uzlu) a úložiště LocalMachine\ROOT (důvěryhodné kořenové certifikační autority uzlu). Chcete-li importovat certifikát na konkrétním uzlu, klikněte pravým tlačítkem na uzel a zvolte **všechny úlohy/Import**.  
  
2. V počítači B, pomocí modulu snap-in Certifikáty konzoly MMC vytvořit nebo získat certB certifikátu s privátním klíčem a naimportujete do LocalMachine\MY (osobní uzlu) a úložiště LocalMachine\ROOT (důvěryhodné kořenové certifikační autority uzlu).  
  
3. Exportujte veřejného klíče pro certA do souboru, pokud to není již bylo provedeno.  
  
4. Exportujte veřejného klíče pro certB do souboru, pokud to není již bylo provedeno.  
  
### <a name="establishing-mutual-trust-between-machines"></a>Vytvoření vzájemném vztahu důvěryhodnosti mezi počítači  
  
1. Na počítači A naimportujte soubor reprezentace certB LocalMachine\MY a LocalMachine\ROOT úložiště. To deklaruje tento počítač vztahy důvěryhodnosti certB komunikovat s ním.  
  
2. V počítači B od certA soubor importujte do úložiště LocalMachine\MY a LocalMachine\ROOT. To znamená tento počítač B certA vztahy důvěryhodnosti pro komunikaci s ním.  
  
 Po dokončení těchto kroků, důvěru lze navázat mezi dvěma počítači a se dají konfigurovat pro komunikaci mezi sebou pomocí WS-AT.  
  
### <a name="configuring-msdtc-to-use-certificates"></a>Konfigurace služby MSDTC používat certifikáty  
 Protože služba WS-AT protokolu funguje jako klient a server, musí i přijímat příchozí připojení a iniciovat odchozí připojení. Proto budete muset nakonfigurovat MSDTC tak, aby věděl, který certifikát se má použít při komunikaci s externími stranami a které certifikáty k ověření při přijetí příchozí komunikaci.  
  
 To můžete nakonfigurovat pomocí modulu snap-in konzoly MMC WS-AT. Další informace o tomto nástroji najdete v tématu [modul Snap-in konzoly MMC konfigurace WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md) tématu. Následující kroky popisují, jak vytvořit vztah důvěryhodnosti mezi dva počítače se systémem MSDTC.  
  
1. Konfigurace počítačů A nastavení. "Certifikát koncového bodu" Vyberte certA. "Autorizované certifikáty" Vyberte certB.  
  
2. Konfigurace nastavení počítače B. "Certifikát koncového bodu" Vyberte certB. "Autorizované certifikáty" Vyberte certA.  
  
> [!NOTE]
>  Pokud jeden počítač odešle zprávu do dalších počítačů, odesílatel se pokusí ověřte, že odpovídají názvu předmětu certifikátu příjemce a název počítače příjemce. Pokud shodné nejsou, se nezdaří ověření certifikátů a dva počítače nemohou komunikovat.  
>   
>  Pro počítač připojený k doméně je název plně kvalifikovaný název domény. Ve výchozím nastavení je název počítače v pracovní skupině název NetBIOS počítače. Název může také mohou obsahovat příponu systému DNS (Domain Name)-Pokud je k dispozici připojení mezi dvěma počítači používán.  
>   
>  Pokud se změní název počítače, například když počítači pracovní skupiny připojí k doméně, musíte znovu vystavit certifikáty nebo ručně konfigurovat přípony DNS.  
  
## <a name="security"></a>Zabezpečení  
 Vzhledem k tomu, že některá nastavení týkající se služby MSDTC a WS-AT uložené v registru v HKLM\Software\Microsoft\MSDTC a HKLM\Software\Microsoft\WSAT, respektive, ujistěte se, že jsou tyto klíče registru zabezpečen tak, aby k nim můžete napsat jenom správci. V nástroji editoru registru klikněte pravým tlačítkem na klíč, který chcete zabezpečit a vyberte **oprávnění** nastavení správy odpovídající přístup. Je důležité pro zabezpečení a integrity systému, který důležité klíče jsou jen pro čtení pro uživatele s nízkými oprávněními.  
  
 Při nasazování služby MSDTC, správce musíte zajistit, že všechny výměny dat MSDTC je zabezpečené. V pracovní skupině nasazení izolovat transakční infrastruktury z uživateli se zlými úmysly; v nasazení clusteru secure registru clusteru.  
  
## <a name="tracing"></a>Trasování  
 Tato služba podporuje protokol WS-AT obslužných rutin integrated, transakce konkrétní trasování můžete povolit a spravovat prostřednictvím [modul Snap-in konzoly MMC konfigurace WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md) nástroj.  Trasování může zahrnovat údaje, které indikují, že se čas zařazení se provádí pro určitou transakci, čas transakce dosáhne stavu terminálu, výsledek každou zařazení transakce byl přijat. Všechna trasování můžete zobrazit pomocí [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) nástroj.  
  
 Službě protokolu WS-AT podporuje také integrovaného ServiceModel trasováním relaci sledování ETW. To poskytuje podrobnější, specifické pro komunikaci trasování kromě existující transakce trasování.  Povolit další trasování, postupujte podle těchto kroků  
  
1. Otevřít **spuštění nebo spuštění** nabídky, do vstupního pole zadejte "regedit" a vyberte **OK**.  
  
2. V **Editor registru**, přejděte do následující složky v levém podokně Hkey_Local_Machine\SOFTWARE\Microsoft\WSAT\3.0\  
  
3. Klikněte pravým tlačítkem myši `ServiceModelDiagnosticTracing` hodnotu v pravém podokně a vyberte **změnit**.  
  
4. V **údaj hodnoty** vstupní pole, zadejte jednu z následujících platné hodnoty k určení úrovně trasování, které chcete povolit.  
  
-   0: vypnuto  
  
-   1: kritické  
  
-   3: Chyba. Toto je výchozí hodnota  
  
-   7: upozornění  
  
-   15: informace  
  
-   do 31: podrobné  
  
## <a name="see-also"></a>Viz také:

- [Nástroj WS-AtomicTransaction Configuration Utility (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
- [Modul snap-in konzoly MMC WS-AtomicTransaction Configuration](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md)
