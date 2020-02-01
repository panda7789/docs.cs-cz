---
title: Konfigurace podpory protokolu WS-AT (WS-Atomic Transactions)
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF], configuring WS-Atomic Transaction
ms.assetid: cb9f1c9c-1439-4172-b9bc-b01c3e09ac48
ms.openlocfilehash: 6399d64746db158ba0569eaf0137127603973513
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76919348"
---
# <a name="configure-ws-atomic-transaction-support"></a>Konfigurace podpory transakcí WS-Atomic

Toto téma popisuje, jak můžete nakonfigurovat podporu WS-AtomicTransaction (WS-AT) pomocí konfiguračního nástroje WS-AT.

## <a name="use-the-ws-at-configuration-utility"></a>Použijte konfigurační nástroj WS-AT.

Konfigurační nástroj WS-AT (wsatConfig. exe) se používá ke konfiguraci nastavení WS-AT. Aby bylo možné povolit službu protokolu WS-AT, je nutné pomocí konfiguračního nástroje nakonfigurovat port HTTPS pro WS-AT, vytvořit z něj certifikát X. 509 a nakonfigurovat autorizované partnerské certifikáty zadáním názvů subjektů certifikátů nebo kryptografické otisky. Nástroj pro konfiguraci také umožňuje vybrat režim trasování a nastavit výchozí odchozí a maximální počet příchozích transakcí.

Přístup k funkcím tohoto nástroje můžete získat pomocí modulu snap-in stránky vlastností konzoly Microsoft Management Console (MMC) v konzole pro správu služby Component Services nebo z okna příkazového řádku. Nakonfigurujte podporu WS-AT na místním počítači prostřednictvím okna příkazového řádku. Nakonfigurujte nastavení na místních i vzdálených počítačích pomocí modulu snap-in konzoly MMC.

Okno příkazového řádku je k dispozici v umístění instalace Windows SDK "%WINDIR%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation".

Další informace o nástroji příkazového řádku najdete v tématu [konfigurační nástroj WS-AtomicTransaction (WsatConfig. exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md).

Pokud používáte systém Windows XP nebo Windows Server 2003, získáte přístup k modulu snap-in konzoly MMC tak, že přejdete na **Ovládací panely nebo nástroje pro správu/služby komponent**, kliknete pravým tlačítkem na položku **Tento počítač**a vyberete **vlastnosti**. Toto je stejné umístění, kde můžete nakonfigurovat Microsoft DTC (Distributed Transaction Coordinator) (MSDTC). Možnosti, které jsou k dispozici pro konfiguraci, jsou seskupeny na kartě **WS-AT** . Pokud používáte systém Windows Vista nebo Windows Server 2008, modul snap-in konzoly MMC lze najít kliknutím na tlačítko **Start** a zadáním `dcomcnfg.exe` do **vyhledávacího** pole. Po otevření konzoly MMC přejděte do uzlu **Computer\Distributed Transaction COORDINATOR\LOCAL DTC** , klikněte pravým tlačítkem a vyberte **vlastnosti**. Možnosti, které jsou k dispozici pro konfiguraci, jsou seskupeny na kartě **WS-AT** .

Další informace o modulu snap-in najdete v [modulu snap-in konzoly MMC pro konfiguraci WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md).

Chcete-li povolit uživatelské rozhraní nástroje, je třeba nejprve zaregistrovat soubor WsatUI. dll, který je umístěn v následující cestě.

%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin

Chcete-li zaregistrovat produkt, spusťte následující příkaz z okna příkazového řádku:

`regasm.exe /codebase WsatUI.dll`

## <a name="enable-ws-at"></a>Povolit WS-AT

Pokud chcete povolit službu protokolu WS-AT v nástroji MSDTC pomocí portu 443 a certifikátu X. 509 s privátním klíčem, který byl nainstalován v úložišti místního počítače, použijte nástroj wsatConfig. exe s následujícím příkazem.

`WsatConfig.exe –network:enable –port:8443 –endpointCert:<machine|"Issuer\SubjectName"> -accountsCerts:<thumbprint|"Issuer\SubjectName"> -restart`

Příslušné parametry nahraďte hodnotami, které jsou relevantní pro vaše prostředí.

Chcete-li zakázat službu protokolu WS-AT ve službě MSDTC, použijte nástroj wsatConfig. exe s následujícím příkazem.

`WsatConfig.exe –network:disable -restart`

## <a name="configure-trust-between-two-machines"></a>Konfigurace vztahu důvěryhodnosti mezi dvěma počítači

Služba protokolu WS-AT vyžaduje, aby správce explicitně schvaloval jednotlivé účty k účasti v distribuovaných transakcích. Pokud jste správcem dvou počítačů, můžete nakonfigurovat oba počítače tak, aby navázaly vzájemný vztah důvěryhodnosti tím, že si vyměňujete správnou sadu certifikátů mezi počítači, nainstalujete je do příslušných úložišť certifikátů a použijete Nástroj wsatConfig. exe, který přidá certifikát každého počítače do seznamu autorizovaných certifikátů účastníků. Tento krok je nezbytný k provádění distribuovaných transakcí mezi dvěma počítači pomocí WS-AT.

V následujícím příkladu je popsán postup navázání vztahu důvěryhodnosti mezi dvěma počítači, a a B.

### <a name="create-and-export-certificates"></a>Vytvoření a export certifikátů

Tento postup vyžaduje modul snap-in Certifikáty konzoly MMC. K modulu snap-in lze přistupovat otevřením nabídky Start/Run, zadáním příkazu MMC do vstupního pole a stisknutím tlačítka OK. Pak v okně **Konzola1** přejděte do modulu snap-in **soubor/přidat-odstranit** , klikněte na tlačítko Přidat a vyberte možnost **certifikáty** ze seznamu **Dostupné samostatné Snapins** . Nakonec vyberte **účet počítače** , který chcete spravovat, a klikněte na **OK**. Uzel **certifikáty** se zobrazí v konzole modulu snap-in.

K navázání vztahu důvěryhodnosti už musíte mít požadované certifikáty. Informace o tom, jak vytvořit a nainstalovat nové certifikáty před následujícím postupem, najdete v tématu [Postupy: vytváření a instalace dočasných klientských certifikátů ve službě WCF během vývoje](https://docs.microsoft.com/previous-versions/msp-n-p/ff650751(v=pandp.10)).

1. V počítači A pomocí modulu snap-in Certifikáty konzoly MMC importujte stávající certifikát (CERT) do úložišti LocalMachine\MY (osobní uzel) a úložiště LocalMachine\ROOT (uzel důvěryhodných kořenových certifikačních autorit). Chcete-li importovat certifikát do konkrétního uzlu, klikněte na něj pravým tlačítkem myši a vyberte možnost **všechny úlohy a importovat**.

2. V počítači B použijte modul snap-in Certifikáty konzoly MMC, vytvořte nebo Získejte certifikát certB s privátním klíčem a naimportujte ho do úložišti LocalMachine\MY (osobní uzel) a do úložiště LocalMachine\ROOT (důvěryhodné kořenové certifikační autority).

3. Exportujte veřejný klíč certifikátu CERT do souboru, pokud již nebyl proveden.

4. Exportujte veřejný klíč certB do souboru, pokud jste to ještě neudělali.

### <a name="establish-mutual-trust-between-machines"></a>Navázání vzájemné důvěry mezi počítači

1. V počítači a importujte soubor certB do úložišť úložišti LocalMachine\MY a LocalMachine\ROOT. Tato deklarace deklaruje, že počítač, kterému důvěřují certB, komunikuje.

2. V počítači B importujte soubor CERT. do úložišť úložišti LocalMachine\MY a LocalMachine\ROOT. To znamená, že počítač B důvěřuje certifikačnímu programu, aby s ním komunikoval.

Po dokončení těchto kroků se mezi těmito dvěma počítači vytvoří vztah důvěryhodnosti a můžete je nakonfigurovat tak, aby se navzájem komunikovaly pomocí WS-AT.

### <a name="configure-msdtc-to-use-certificates"></a>Konfigurace služby MSDTC pro použití certifikátů

Vzhledem k tomu, že služba protokolu WS-AT funguje jako klient i server, musí naslouchat příchozím připojením a iniciovat odchozí připojení. Proto je nutné nakonfigurovat MSDTC tak, aby znal, který certifikát se má použít při komunikaci s externími stranami a které certifikáty se mají autorizovat při přijímání příchozí komunikace.

Tuto konfiguraci můžete provést pomocí modulu snap-in konzoly MMC WS. Další informace o tomto nástroji naleznete v tématu [modul snap-in konzoly MMC konfigurace WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md) . Následující postup popisuje, jak vytvořit vztah důvěryhodnosti mezi dvěma počítači se spuštěným koordinátorem MSDTC.

1. Nakonfigurujte nastavení počítače A. V části certifikát koncového bodu vyberte CERT. V případě "autorizovaných certifikátů" vyberte certB.

2. Nakonfigurujte nastavení počítače B. U možnosti "certifikát koncového bodu" vyberte certB. V části autorizované certifikáty vyberte CERT.

> [!NOTE]
> Když jeden počítač pošle zprávu druhému počítači, odesilatel se pokusí ověřit, že název předmětu certifikátu příjemce a název počítače příjemce se shodují. Pokud se neshodují, ověření certifikátu se nezdařilo a dva počítače nemohou komunikovat.
>
> Pro počítač připojený k doméně je název plně kvalifikovaný název domény. Ve výchozím nastavení je název počítače v pracovní skupině název NetBIOS počítače. Název může ale také zahrnovat příponu DNS (Domain Name System), pokud je k dispozici připojení mezi dvěma počítači.
>
> Pokud se název počítače změní, například když se počítač pracovní skupiny připojí k doméně, je nutné vystavit certifikáty nebo ručně nakonfigurovat přípony serveru DNS.

## <a name="security"></a>Zabezpečení –

Vzhledem k tomu, že některá nastavení týkající se MSDTC a WS-AT se ukládají v registru na adrese HKLM\Software\Microsoft\MSDTC a v HKLM\Software\Microsoft\WSAT, zajistěte, aby byly tyto klíče registru zabezpečené, aby do nich mohli zapisovat jenom správci. V nástroji Editor registru klikněte pravým tlačítkem na klíč, který chcete zabezpečit, a vyberte **oprávnění** k nastavení příslušného řízení přístupu. Je zásadní pro zabezpečení a integritu systému, že jsou důležité klíče jen pro čtení pro uživatele s nízkými oprávněními.

Při nasazování služby MSDTC musí správce zajistit zabezpečení výměny dat MSDTC. V nasazení pracovní skupiny izolujte transakční infrastrukturu od uživatelů se zlými úmysly. v nasazení clusteru Zabezpečte registr clusteru.

## <a name="tracing"></a>Trasování

Služba protokolu WS-AT podporuje integrované trasování specifické pro transakce, které lze povolit a spravovat prostřednictvím použití nástroje pro [modul snap-in konzoly MMC pro konfiguraci WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md) . Trasování mohou zahrnovat data indikující dobu, po kterou je zařazení pro konkrétní transakci, čas, kdy transakce dosáhne svého stavu terminálu, výsledek přijetí každého zařazení transakce. Všechna trasování lze zobrazit pomocí nástroje pro [Prohlížeč trasování služby (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) .

Služba protokolu WS-AT podporuje také integrované trasování ServiceModel prostřednictvím relace trasování ETW. To poskytuje podrobnější informace o trasování specifických pro komunikaci spolu s existujícími trasováními transakcí.  Pokud chcete povolit tato další trasování, postupujte podle těchto kroků.

1. Otevřete nabídku **Start/Run** , do pole vstup zadejte "regedit" a vyberte **OK**.

2. V **Editoru registru**přejděte do následující složky v levém podokně HKEY_LOCAL_MACHINE \software\microsoft\wsat\3.0\

3. V pravém podokně klikněte pravým tlačítkem na hodnotu `ServiceModelDiagnosticTracing` a vyberte **změnit**.

4. Do pole vstup **dat hodnoty** zadejte jednu z následujících platných hodnot a určete úroveň trasování, kterou chcete povolit.

- 0: vypnuto

- 1: kritická

- 3: Chyba. Toto je výchozí hodnota.

- 7: upozornění

- 15: informace

- 31: verbose

## <a name="see-also"></a>Viz také:

- [Nástroj pro konfiguraci WS-AtomicTransaction (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
- [Modul snap-in konzoly MMC pro konfiguraci WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md)
