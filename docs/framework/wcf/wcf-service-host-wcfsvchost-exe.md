---
title: Hostitel služby WCF (WcfSvcHost.exe)
ms.date: 03/30/2017
ms.assetid: 8643a63d-a357-4c39-bd6c-cdfdf71e370e
ms.openlocfilehash: b8fb32111a80178f5eb92411eb4990decb645bb6
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837737"
---
# <a name="wcf-service-host-wcfsvchostexe"></a>Hostitel služby WCF (WcfSvcHost.exe)

Hostitel služby Windows Communication Foundation (WCF) (WcfSvcHost. exe) umožňuje spustit ladicí program sady Visual Studio (F5) pro automatické hostování a testování služby, kterou jste implementovali. Pak můžete službu otestovat pomocí testovacího klienta WCF (WcfTestClient. exe) nebo svého vlastního klienta, abyste našli a opravili případné chyby.

## <a name="wcf-service-host"></a>Hostitel služby WCF

Hostitel služby WCF vytvoří výčet služby v projektu služby WCF, načte konfiguraci projektu a vytvoří instanci hostitele pro každou službu, kterou zjistí. Nástroj je integrován do sady Visual Studio prostřednictvím šablony služby WCF a je vyvolána při zahájení ladění projektu.

Pomocí hostitele služby WCF můžete hostovat službu WCF (v projektu knihovny služby WCF), aniž byste museli psát další kód nebo potvrzování konkrétního hostitele během vývoje.

> [!NOTE]
> Hostitel služby WCF nepodporuje částečnou důvěryhodnost. Pokud chcete používat službu WCF v částečném vztahu důvěryhodnosti, nepoužívejte k sestavení vaší služby šablonu projektu knihovny služby WCF v aplikaci Visual Studio. Místo toho vytvořte nový web v aplikaci Visual Studio tak, že vyberete šablonu webu služby WCF, která může hostovat službu na webovém serveru, na kterém je podporována částečná důvěryhodnost WCF.

## <a name="project-types-hosted-by-wcf-service-host"></a>Typy projektů hostované hostitelem služby WCF

Hostitel služby WCF může hostovat následující typy projektů knihovny služby WCF: knihovna služeb WCF, Knihovna služby sekvenčního pracovního postupu, Knihovna služby pracovního postupu stavového stroje a Knihovna služby syndikace. Hostitel služby WCF může také hostovat tyto služby, které lze přidat do projektu knihovny služeb pomocí funkce **Přidat položku** . Patří sem služba WCF, služba stavu WF, služba WF pro stavové služby a sekvenční služba XAML WF.

Nezapomeňte však, že nástroj vám nepomůže nakonfigurovat hostitele. Pro tuto úlohu musíte ručně upravit soubor App. config. Nástroj také neověřuje uživatelsky definované konfigurační soubory.

> [!CAUTION]
> Hostitel služby WCF byste neměli používat k hostování služeb v produkčním prostředí, protože pro tento účel nebyl navržen.  Hostitel služby WCF nepodporuje požadavky na spolehlivost, zabezpečení a spravovatelnost takového prostředí. Místo toho použijte službu IIS, protože poskytuje špičkové funkce pro spolehlivost a monitorování a je upřednostňovaným řešením pro hostování služeb. Po dokončení vývoje služeb byste měli migrovat služby z hostitele služby WCF do služby IIS.

## <a name="scenarios-for-using-wcf-service-host-inside-visual-studio"></a>Scénáře použití hostitele služby WCF v rámci sady Visual Studio

V následující tabulce jsou uvedeny všechny parametry v dialogovém okně **argumenty příkazového řádku** , které lze najít kliknutím pravým tlačítkem myši na projekt v **Průzkumníku řešení** v aplikaci Visual Studio, výběrem **vlastností**a výběrem karty **ladění** a kliknutím na položku **spustit projekt**. Tyto parametry jsou užitečné při konfiguraci hostitele služby WCF.

|Parametr|Význam|
|---------------|-------------|
|`/client`|Volitelný parametr, který určuje cestu ke spustitelnému souboru, který má být spuštěn po hostování služeb. Tím se spustí test klienta WCF po hostování.|
|`/clientArg`|Zadejte řetězec jako argument, který se předává vlastní klientské aplikaci.|
|`/?`|Zobrazí text v nápovědě.|

#### <a name="using-wcf-test-client"></a>Použití testovacího klienta WCF

Po vytvoření nového projektu služby WCF a stisknutím klávesy F5 ke spuštění ladicího programu začne hostitel služby WCF hostovat všechny služby, které najde ve vašem projektu. Testovací klient WCF se automaticky otevře a zobrazí seznam koncových bodů služby, které jsou definovány v konfiguračním souboru. Z hlavního okna můžete testovat parametry a vyvolat službu.

Chcete-li se ujistit, že se používá klient testu WCF, klikněte pravým tlačítkem myši na projekt v **Průzkumníku řešení** v aplikaci Visual Studio, vyberte možnost **vlastnosti**a pak vyberte kartu **ladění** . klikněte na tlačítko **spustit projekt** a ověřte, zda se v dialogovém okně **argumenty příkazového řádku** zobrazí následující.

`/client:WcfTestClient.exe`

#### <a name="using-a-custom-client"></a>Použití vlastního klienta

Chcete-li použít vlastního klienta, klikněte pravým tlačítkem myši na projekt v **Průzkumníku řešení** v aplikaci Visual Studio, vyberte možnost **vlastnosti**a pak vyberte kartu **ladění** . klikněte na tlačítko **spustit projekt** a v dialogovém okně **argumenty příkazového řádku** upravte parametr `/client` tak, aby odkazoval na vlastního klienta, jak je uvedeno v následujícím příkladu.

`/client:"path/CustomClient.exe"`

Když stisknete klávesu F5 ke spuštění služby znovu, hostitel služby WCF automaticky spustí vlastního klienta při spuštění ladicího programu.

Můžete také použít parametr `/clientArg:` a zadat řetězec jako argument, který je předán vlastní klientské aplikaci, jak je uvedeno v následujícím příkladu.

`/client:"path/CustomClient.exe" /clientArg:"arguments that are passed to Client"`

Pokud například používáte šablonu knihovny syndikace Service, můžete použít následující argumenty příkazového řádku:

`/client:iexplore.exe /clientArgs:http://localhost:8731/Design_Time_Addresses/Feed1/`

#### <a name="specifying-no-client"></a>Bez zadání klienta

Chcete-li určit, že po hostování služby WCF nebude použit žádný klient, klikněte pravým tlačítkem myši na projekt v **Průzkumníku řešení** v aplikaci Visual Studio, vyberte možnost **vlastnosti**a poté vyberte kartu **ladit** . klikněte na tlačítko **spustit projekt** a nechejte dialogové okno **argumenty příkazového řádku** prázdné.

#### <a name="using-a-custom-host"></a>Použití vlastního hostitele

Chcete-li použít vlastního hostitele, klikněte pravým tlačítkem myši na projekt v **Průzkumníku řešení** v aplikaci Visual Studio, vyberte možnost **vlastnosti**a pak vyberte kartu **ladění** . klikněte na **spustit externí program** a zadejte úplnou cestu k vlastnímu hostiteli. Pomocí dialogového okna **argumenty příkazového řádku** můžete také určit argumenty, které mají být předány hostiteli.

## <a name="wcf-service-host-user-interface"></a>Uživatelské rozhraní hostitele služby WCF

Při prvotním vyvolání hostitele služby WCF (stisknutím klávesy F5 uvnitř sady Visual Studio) se automaticky otevře okno **Hostitel služby WCF** . Když je hostitel služby WCF spuštěný, zobrazí se v oznamovací oblasti ikona programu. Dvojitým kliknutím na ikonu otevřete okno **Hostitel služby WCF** .

Pokud dojde k chybám během hostování služby, otevře se dialogové okno hostitel služby WCF, ve kterém se zobrazí relevantní informace.

Hlavní okno **hostitele služby WCF** obsahuje dvě nabídky:

- **Soubor**: obsahuje příkazy pro **zavření** a **ukončení** . Po kliknutí na **Zavřít**se dialogové okno **Hostitel služby WCF** zavře, ale služby se budou dál hostovat. Po kliknutí na tlačítko **ukončit**se taky ukončí hostitel služby WCF. Tím se také zastaví všechny hostované služby.

- **Help**: obsahuje příkaz **o** příkazu, který obsahuje informace o verzi. Obsahuje také příkaz **help** , který může otevřít soubor s nápovědě.

Hlavní okno **hostitele služby WCF** obsahuje dvě oblasti:

- První oblast je **Služba**. Obsahuje seznam, který zobrazuje základní informace o všech službách. Mezi tyto informace patří:

  - **Služba**: vypíše všechny služby.

  - **Stav**: zobrazuje stav služby. Platné hodnoty jsou "Start", "zastaveno" a "Error".

  - **Adresa metadat**: zobrazuje adresu metadat služeb.

- Druhá oblast je **Další informace**. Zobrazí podrobné vysvětlení stavu služby, když je v oblasti **služby** vybrán konkrétní řádek služby. Pokud je stav Chyba, můžete zobrazit úplnou chybovou zprávu na obrazovce.

## <a name="stopping-wcf-service-host"></a>Zastavuje se hostitel služby WCF.

Hostitele služby WCF můžete vypnout následujícími čtyřmi způsoby:

- Zastavte ladicí relaci v aplikaci Visual Studio.

- V okně **Hostitel služby WCF** vyberte možnost **ukončit** v nabídce **soubor** .

- V místní nabídce ikony hostitele služby WCF v oznamovací oblasti systému vyberte možnost **ukončit** .

- Ukončete klienta služby WCF test, pokud je používán.

## <a name="using-service-host-without-administrator-privilege"></a>Použití hostitele služby bez oprávnění správce

Aby uživatelé bez oprávnění správce mohli vyvíjet služby WCF, vytvoří se seznam ACL (Access Control) pro obor názvů "http://+:8731/Design_Time_Addresses" při instalaci sady Visual Studio. Seznam řízení přístupu (ACL) je nastavený na (uživatelské rozhraní), které zahrnuje všechny interaktivní uživatele přihlášené k počítači. Správci mohou přidat nebo odebrat uživatele z tohoto seznamu ACL nebo otevřít další porty. Tento seznam řízení přístupu umožňuje uživatelům používat automatické hostování služby WCF (wcfSvcHost. exe) bez udělení oprávnění správce.

Přístup můžete upravit pomocí nástroje Netsh. exe v systému Windows Vista pod účtem správce se zvýšenými oprávněními. Následuje příklad použití nástroje Netsh. exe.

```console
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>
```

Další informace o nástroji Netsh. exe najdete v části "[použití nástroje Netsh. exe a přepínačů příkazového řádku](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10))".

## <a name="see-also"></a>Viz také:

- [Testovací klient WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
