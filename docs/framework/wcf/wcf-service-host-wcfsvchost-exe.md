---
title: Hostitel služby WCF (WcfSvcHost.exe)
ms.date: 03/30/2017
ms.assetid: 8643a63d-a357-4c39-bd6c-cdfdf71e370e
ms.openlocfilehash: c000ad3ba53f103cb1a24a9a7fbc71049ba707c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="wcf-service-host-wcfsvchostexe"></a>Hostitel služby WCF (WcfSvcHost.exe)
Hostitel služby Windows Communication Foundation (WCF) (WcfSvcHost.exe) umožňuje spuštění ladicího programu sady Visual Studio (F5) automaticky hostování a testovat službu, kterou jste implementovali. Potom můžete otestovat pomocí služby [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] testovacího klienta (WcfTestClient.exe) nebo vlastního klienta najít a opravit všechny potenciální chyby.  
  
## <a name="wcf-service-host"></a>Hostitel služby WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hostitel služby zobrazí služeb v [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projekt služby, načte konfiguraci projektu a pro každou službu, kterou najde hostitele, který se vytvoří instance. Nástroj je integrován do sady Visual Studio prostřednictvím [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Šablona služby a je volána, když začnete spusťte ladění svého projektu.  
  
 Pomocí [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hostitele služby, můžete hostovat [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby (v [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projektu knihovny service) bez psaní dalšího kódu nebo potvrzení k určitému hostiteli během vývoje.  
  
> [!NOTE]
>  [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hostitel služby nepodporuje částečné důvěryhodnosti. Pokud chcete použít [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby v částečné důvěryhodnosti, nepoužívejte [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] šablona projektu knihovny služby v sadě Visual Studio k vytvoření služby. Místo toho vytvořte nový web v sadě Visual Studio tak, že zvolíte [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] šablony Web Service, která může být hostitelem služby webovém serveru, na kterém [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] částečné důvěryhodnosti je podporována.  
  
## <a name="project-types-hosted-by-wcf-service-host"></a>Typy projektů hostované hostitel služby WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hostitel služby může hostovat následující [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby typy projektů knihovny: [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] knihovny služby, knihovny služby sekvenčního pracovního postupu, stavu počítače pracovního postupu služby knihovnu a knihovna syndikace Service. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hostitel služby můžou hostovat taky těchto služeb, které mohou být přidány do projektu knihovny službu pomocí **přidat položku** funkce. To zahrnuje [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby, Služba Machine stavu WF, WF sekvenční služby XAML WF stav počítače a XAML WF sekvenční služby.  
  
 Upozorňujeme ale, ale, že nástroj nebude vám pomohou při konfiguraci hostitele. Pro tuto úlohu je nutné ručně upravit soubor App.config. Nástroj také neověřuje vlastní konfigurační soubory.  
  
> [!CAUTION]
>  Neměli byste používat [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hostitele služby na hostitele služby v produkčním prostředí, protože nebyla vytvořena pro tento účel.  [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hostitel služby nepodporuje spolehlivost, zabezpečení a možnosti správy požadavky na takové prostředí. Místo toho používají službu IIS, protože poskytuje vyšší spolehlivost a monitorovací funkce a je nejlepší řešení pro hostování služeb. Po dokončení vývoj vašich služeb by bylo nutné migrovat služeb z [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hostitele služby IIS.  
  
## <a name="scenarios-for-using-wcf-service-host-inside-visual-studio"></a>Scénáře použití hostitel služby WCF v sadě Visual Studio  
 Následující tabulka obsahuje seznam všech parametrů v **argumenty příkazového řádku** dialogové okno, které lze najít kliknutím pravým tlačítkem na projekt v **Průzkumníka řešení** v sadě Visual Studio, výběr **Vlastnosti**, pak výběrem **ladění** kartě a kliknutím na **spustit projekt**. Tyto parametry jsou užitečné při konfiguraci [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hostitele služby.  
  
|Parametr|Význam|  
|---------------|-------------|  
|`/client`|Volitelný parametr, který určuje cestu k spustitelný soubor spustit po hostovaných služeb. Spustí se [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] testovacího klienta následující hostování.|  
|`/clientArg`|Zadejte řetězec, jako argument, který je předán do vlastní klientské aplikace.|  
|`/?`|Zobrazí text nápovědy.|  
  
#### <a name="using-wcf-test-client"></a>Použití testovacího klienta WCF  
 Po vytvoření nové [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby projektu a stisknutím klávesy F5 spusťte ladicí program, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hostitele služby spustí hostování všechny služby, které najde v projektu. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Testovacího klienta automaticky otevře a zobrazí seznam koncových bodů služby definována v konfiguračním souboru. V hlavním okně můžete si otestovat parametry a vyvolání služby.  
  
 K Ujistěte se, že [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] testovacího klienta se používá, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** v sadě Visual Studio, vyberte **vlastnosti**, vyberte **ladění**kartě. Klikněte na tlačítko **spuštění projektu** a ujistěte se, že se zobrazí následující v **argumenty příkazového řádku** dialogové okno.  
  
 `/client:WcfTestClient.exe`  
  
#### <a name="using-a-custom-client"></a>Pomocí vlastního klienta  
 Pokud chcete používat vlastní klienta, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** v sadě Visual Studio, vyberte **vlastnosti**, vyberte **ladění** karta. Klikněte na tlačítko **spuštění projektu** a upravit `/client` parametr ve **argumenty příkazového řádku** dialogové okno tak, aby odkazovaly do vlastního klienta, jak je uvedeno v následujícím příkladu.  
  
 `/client:"path/CustomClient.exe"`  
  
 Po stisknutí klávesy F5 spusťte službu znovu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hostitele služby se automaticky spustí vlastní klienta při spuštění ladicího programu.  
  
 Můžete také `/clientArg:` parametr k určení řetězec jako argument, který je předán vlastní klientské aplikace, jak je uvedeno v následujícím příkladu.  
  
 `/client:"path/CustomClient.exe" /clientArg:"arguments that are passed to Client"`  
  
 Například pokud používáte šablonu knihovny služby syndikace, můžete použít následující argumenty příkazového řádku  
  
 `/client:iexplore.exe /clientArgs:http://localhost:8731/Design_Time_Addresses/Feed1/`  
  
#### <a name="specifying-no-client"></a>Určení žádné klienta  
 Chcete-li určit, že žádné klienta se použije po [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby hostování, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** v sadě Visual Studio, vyberte **vlastnosti**, pak vyberte  **Ladění** kartě. Klikněte na tlačítko **spuštění projektu** a nechat **argumenty příkazového řádku** dialogové okno prázdné.  
  
#### <a name="using-a-custom-host"></a>Pomocí vlastního hostitele  
 Pokud chcete použít vlastní hostitele, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** v sadě Visual Studio, vyberte **vlastnosti**, vyberte **ladění** kartě. Klikněte na tlačítko **spustit externí Program** a zadejte úplnou cestu k vlastní hostitel. Můžete také **argumenty příkazového řádku** dialogové okno zadat argumenty předávané do hostitele.  
  
## <a name="wcf-service-host-user-interface"></a>Uživatelského rozhraní hostitele služby WCF  
 Když jste původně vyvolání [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hostitele služby (stisknutím klávesy F5 v sadě Visual Studio), **hostitel služby WCF** automaticky otevře se okno. Když [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hostitele služby běží, se zobrazí v oznamovací oblasti ikonu programu. Dvakrát klikněte na ikonu Otevřít **hostitel služby WCF** okna  
  
 Pokud dojde k chybám při hostování služeb [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] otevře se dialogové okno hostitele služby zobrazíte příslušné informace.  
  
 **Hostitel služby WCF** hlavní okno obsahuje dvě nabídky:  
  
-   **Soubor**: obsahuje **Zavřít** a **ukončení** příkazy. Když kliknete na tlačítko **Zavřít**, **hostitel služby WCF** zavře dialogové okno, ale nadále být hostované služby. Když kliknete na tlačítko **ukončení**, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hostitele služby se vypne taky. To také zastaví všechny hostované služby.  
  
-   **Pomůže**: obsahuje **o** příkaz, který obsahuje informace o verzi. Obsahuje taky **pomoci** příkaz, který můžete otevřít soubor nápovědy.  
  
 Hlavní **hostitel služby WCF** okno obsahuje dvě oblasti:  
  
-   První oblast je **služby**. Obsahuje seznam, který zobrazuje základní informace o všech služeb. Informace, zahrnují:  
  
    -   **Služba**: Zobrazí seznam všech služeb.  
  
    -   **Stav**: Zobrazí stav služby. Platné hodnoty jsou "Začínáme", "Stopped" a "Chyba".  
  
    -   **Metadata adresu**: Zobrazí adresu metadat služeb.  
  
-   Druhý oblast je **Další informace o**. Zobrazí podrobné vysvětlení stav služby, pokud je vybrána konkrétní služby řádku v **služby** oblasti. Pokud je ve stavu chyby, můžete zobrazit celý text chybové zprávy na obrazovce.  
  
## <a name="stopping-wcf-service-host"></a>Zastavení hostitel služby WCF  
 Můžete vypnout [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hostitele služby následující čtyři způsoby:  
  
-   Ukončit relaci ladění v sadě Visual Studio.  
  
-   Vyberte **ukončení** z **soubor** v nabídce **hostitel služby WCF** okno.  
  
-   Vyberte **ukončení** kontextové nabídce [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hostitele služby panelu ikonu v oznamovací oblasti systému.  
  
-   Ukončení [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] testovacího klienta, pokud se používá.  
  
## <a name="using-service-host-without-administrator-privilege"></a>Pomocí hostitele služby bez oprávnění správce  
 Aby mohli uživatelé bez oprávnění správce k vývoji [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby, je vytvořit ACL (seznam řízení přístupu) pro obor názvů "http://+:8731/Design_Time_Addresses" při instalaci sady Visual Studio. Seznam řízení přístupu je nastavené na (UI), který zahrnuje všechny interaktivní uživatelé přihlášení k počítači. Správci mohou přidat nebo odebrat uživatele z tohoto seznamu ACL nebo otevřít další porty. Tento seznam ACL umožňuje uživatelům používat [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] automatického hostitele služby (wcfSvcHost.exe) bez je udělení oprávnění správce.  
  
 Můžete upravit přístup pomocí nástroje netsh.exe v [!INCLUDE[wv](../../../includes/wv-md.md)] pod účtem zvýšenými na úroveň správce. Následuje příklad použití netsh.exe.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Další informace o netsh.exe, najdete v části "[jak pomocí nástroje Netsh.exe a přepínače příkazového řádku](http://go.microsoft.com/fwlink/?LinkId=97877)".  
  
## <a name="see-also"></a>Viz také  
 [Testovací klient WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
