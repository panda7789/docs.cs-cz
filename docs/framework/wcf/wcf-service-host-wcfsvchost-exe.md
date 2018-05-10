---
title: Hostitel služby WCF (WcfSvcHost.exe)
ms.date: 03/30/2017
ms.assetid: 8643a63d-a357-4c39-bd6c-cdfdf71e370e
ms.openlocfilehash: e1e258015adc34edd4a109f3bc5a32b4bf6f0296
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="wcf-service-host-wcfsvchostexe"></a>Hostitel služby WCF (WcfSvcHost.exe)
Hostitel služby Windows Communication Foundation (WCF) (WcfSvcHost.exe) umožňuje spuštění ladicího programu sady Visual Studio (F5) automaticky hostování a testovat službu, kterou jste implementovali. Potom můžete otestovat pomocí testovacího klienta WCF (WcfTestClient.exe) nebo vlastního klienta najít a opravit všechny potenciální chyby.  
  
## <a name="wcf-service-host"></a>Hostitel služby WCF  
 Hostitel služby WCF vytvoří výčet služeb v projektu služby WCF, načte konfiguraci projektu a vytvoří instanci hostitele pro každou službu, kterou najde. Nástroj je integrován do sady Visual Studio pomocí šablony služby WCF a je volána, když začnete spusťte ladění svého projektu.  
  
 Pomocí hostitele služby WCF můžete hostovat služby WCF (v projektu knihovny služby WCF) bez psaní dalšího kódu nebo potvrzení k určitému hostiteli během vývoje.  
  
> [!NOTE]
>  Hostitel služby WCF nepodporuje částečné důvěryhodnosti. Pokud chcete použít částečný vztah důvěryhodnosti ve služby WCF, nepoužívejte šablona projektu knihovny služby WCF v sadě Visual Studio k vytvoření služby. Místo toho vytvořte nový web v sadě Visual Studio výběrem šablony webu služby WCF, která může být hostitelem služby webovém serveru, na kterém se podporuje částečné důvěryhodnosti WCF.  
  
## <a name="project-types-hosted-by-wcf-service-host"></a>Typy projektů hostované hostitel služby WCF  
 Hostitel služby WCF můžete hostovat typy s projektu knihovny služby WCF: knihovny služby WCF, sekvenční knihovny služby pracovního postupu, stav počítače pracovního postupu služby knihovnu a knihovna syndikace Service. Hostitel služby WCF můžete hostovat těchto služeb, které mohou být přidány do projektu knihovny službu pomocí **přidat položku** funkce. To zahrnuje služby WCF, WF stavu počítač služby, WF sekvenční služby, Služba Machine stavu WF XAML a XAML WF sekvenční služby.  
  
 Upozorňujeme ale, ale, že nástroj nebude vám pomohou při konfiguraci hostitele. Pro tuto úlohu je nutné ručně upravit soubor App.config. Nástroj také neověřuje vlastní konfigurační soubory.  
  
> [!CAUTION]
>  Hostitel služby WCF pro hostování služeb byste neměli používat v provozním prostředí, protože nebyla vytvořena pro tento účel.  Hostitel služby WCF nepodporuje spolehlivost, zabezpečení a možnosti správy požadavky na takové prostředí. Místo toho používají službu IIS, protože poskytuje vyšší spolehlivost a monitorovací funkce a je nejlepší řešení pro hostování služeb. Po dokončení vývoj vašich služeb, měli byste migrovat služby z hostitele služeb WCF pro službu IIS.  
  
## <a name="scenarios-for-using-wcf-service-host-inside-visual-studio"></a>Scénáře použití hostitel služby WCF v sadě Visual Studio  
 Následující tabulka obsahuje seznam všech parametrů v **argumenty příkazového řádku** dialogové okno, které lze najít kliknutím pravým tlačítkem na projekt v **Průzkumníka řešení** v sadě Visual Studio, výběr **Vlastnosti**, pak výběrem **ladění** kartě a kliknutím na **spustit projekt**. Tyto parametry jsou užitečné při konfiguraci hostitele služeb WCF.  
  
|Parametr|Význam|  
|---------------|-------------|  
|`/client`|Volitelný parametr, který určuje cestu k spustitelný soubor spustit po hostovaných služeb. Spustí se testovacího klienta WCF následující hostování.|  
|`/clientArg`|Zadejte řetězec, jako argument, který je předán do vlastní klientské aplikace.|  
|`/?`|Zobrazí text nápovědy.|  
  
#### <a name="using-wcf-test-client"></a>Použití testovacího klienta WCF  
 Po vytvoření nového projektu služby WCF a stisknutím klávesy F5 spusťte ladicí program, hostitel služby WCF spustí hostování všechny služby, které najde v projektu. WCF testovacího klienta automaticky otevře a zobrazí seznam koncových bodů služby definována v konfiguračním souboru. V hlavním okně můžete si otestovat parametry a vyvolání služby.  
  
 Abyste měli jistotu, že se používá testovacího klienta WCF, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** v sadě Visual Studio, vyberte **vlastnosti**, vyberte **ladění** kartě. Klikněte na tlačítko **spuštění projektu** a ujistěte se, že se zobrazí následující v **argumenty příkazového řádku** dialogové okno.  
  
 `/client:WcfTestClient.exe`  
  
#### <a name="using-a-custom-client"></a>Pomocí vlastního klienta  
 Pokud chcete používat vlastní klienta, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** v sadě Visual Studio, vyberte **vlastnosti**, vyberte **ladění** karta. Klikněte na tlačítko **spuštění projektu** a upravit `/client` parametr ve **argumenty příkazového řádku** dialogové okno tak, aby odkazovaly do vlastního klienta, jak je uvedeno v následujícím příkladu.  
  
 `/client:"path/CustomClient.exe"`  
  
 Po stisknutí klávesy F5 spusťte službu znovu hostitel služby WCF se automaticky spustí vlastní klienta při spuštění ladicího programu.  
  
 Můžete také `/clientArg:` parametr k určení řetězec jako argument, který je předán vlastní klientské aplikace, jak je uvedeno v následujícím příkladu.  
  
 `/client:"path/CustomClient.exe" /clientArg:"arguments that are passed to Client"`  
  
 Například pokud používáte šablonu knihovny služby syndikace, můžete použít následující argumenty příkazového řádku  
  
 `/client:iexplore.exe /clientArgs:http://localhost:8731/Design_Time_Addresses/Feed1/`  
  
#### <a name="specifying-no-client"></a>Určení žádné klienta  
 Chcete-li určit, že žádné klienta se použije po hostování služby WCF, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** v sadě Visual Studio, vyberte **vlastnosti**, vyberte **ladění** kartě. Klikněte na tlačítko **spuštění projektu** a nechat **argumenty příkazového řádku** dialogové okno prázdné.  
  
#### <a name="using-a-custom-host"></a>Pomocí vlastního hostitele  
 Pokud chcete použít vlastní hostitele, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** v sadě Visual Studio, vyberte **vlastnosti**, vyberte **ladění** kartě. Klikněte na tlačítko **spustit externí Program** a zadejte úplnou cestu k vlastní hostitel. Můžete také **argumenty příkazového řádku** dialogové okno zadat argumenty předávané do hostitele.  
  
## <a name="wcf-service-host-user-interface"></a>Uživatelského rozhraní hostitele služby WCF  
 Pokud jste původně vyvolání hostitel služby WCF (stisknutím klávesy F5 v sadě Visual Studio), **hostitel služby WCF** automaticky otevře se okno. Když hostitel služby WCF běží, zobrazí se v oznamovací oblasti ikonu programu. Dvakrát klikněte na ikonu Otevřít **hostitel služby WCF** okna  
  
 Pokud dojde k chybám při hostování služeb, otevře se dialogové okno hostitel služby WCF a zobrazte příslušné informace.  
  
 **Hostitel služby WCF** hlavní okno obsahuje dvě nabídky:  
  
-   **Soubor**: obsahuje **Zavřít** a **ukončení** příkazy. Když kliknete na tlačítko **Zavřít**, **hostitel služby WCF** zavře dialogové okno, ale nadále být hostované služby. Když kliknete na tlačítko **ukončení**, hostitel služby WCF se vypne taky. To také zastaví všechny hostované služby.  
  
-   **Pomůže**: obsahuje **o** příkaz, který obsahuje informace o verzi. Obsahuje taky **pomoci** příkaz, který můžete otevřít soubor nápovědy.  
  
 Hlavní **hostitel služby WCF** okno obsahuje dvě oblasti:  
  
-   První oblast je **služby**. Obsahuje seznam, který zobrazuje základní informace o všech služeb. Informace, zahrnují:  
  
    -   **Služba**: Zobrazí seznam všech služeb.  
  
    -   **Stav**: Zobrazí stav služby. Platné hodnoty jsou "Začínáme", "Stopped" a "Chyba".  
  
    -   **Metadata adresu**: Zobrazí adresu metadat služeb.  
  
-   Druhý oblast je **Další informace o**. Zobrazí podrobné vysvětlení stav služby, pokud je vybrána konkrétní služby řádku v **služby** oblasti. Pokud je ve stavu chyby, můžete zobrazit celý text chybové zprávy na obrazovce.  
  
## <a name="stopping-wcf-service-host"></a>Zastavení hostitel služby WCF  
 Hostitel služby WCF můžete vypnout následující čtyři způsoby:  
  
-   Ukončit relaci ladění v sadě Visual Studio.  
  
-   Vyberte **ukončení** z **soubor** v nabídce **hostitel služby WCF** okno.  
  
-   Vyberte **ukončení** z kontextové nabídky hostitel služby WCF panelu ikonu v oznamovací oblasti systému.  
  
-   Pokud se používá, ukončete testovacího klienta WCF.  
  
## <a name="using-service-host-without-administrator-privilege"></a>Pomocí hostitele služby bez oprávnění správce  
 Pokud chcete povolit uživatelům bez oprávnění správce k vývoji služeb WCF, se vytvoří ACL (seznam řízení přístupu) pro obor názvů "http://+:8731/Design_Time_Addresses" při instalaci sady Visual Studio. Seznam řízení přístupu je nastavené na (UI), který zahrnuje všechny interaktivní uživatelé přihlášení k počítači. Správci mohou přidat nebo odebrat uživatele z tohoto seznamu ACL nebo otevřít další porty. Tento seznam ACL umožňuje uživatelům používat automatické hostitel služby WCF (wcfSvcHost.exe) bez je udělení oprávnění správce.  
  
 Můžete upravit přístup pomocí nástroje netsh.exe v [!INCLUDE[wv](../../../includes/wv-md.md)] pod účtem zvýšenými na úroveň správce. Následuje příklad použití netsh.exe.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Další informace o netsh.exe, najdete v části "[jak pomocí nástroje Netsh.exe a přepínače příkazového řádku](http://go.microsoft.com/fwlink/?LinkId=97877)".  
  
## <a name="see-also"></a>Viz také  
 [Testovací klient WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
