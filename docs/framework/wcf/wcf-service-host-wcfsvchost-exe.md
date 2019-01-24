---
title: Hostitel služby WCF (WcfSvcHost.exe)
ms.date: 03/30/2017
ms.assetid: 8643a63d-a357-4c39-bd6c-cdfdf71e370e
ms.openlocfilehash: 6a8ed677ceaf9b86b67ec2558eb4e31c23d4c57e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505637"
---
# <a name="wcf-service-host-wcfsvchostexe"></a>Hostitel služby WCF (WcfSvcHost.exe)
Hostitel služby Windows Communication Foundation (WCF) (WcfSvcHost.exe) umožňuje spustit ladicí program sady Visual Studio (F5) automaticky hostovat a testovat službu, kterou jste implementovali. Potom můžete otestovat pomocí testovacího klienta WCF (WcfTestClient.exe) nebo vlastního klienta, můžete najít a opravit všechny potenciální chyby.  
  
## <a name="wcf-service-host"></a>Hostitel služby WCF  
 Hostitel služby WCF vytvoří výčet služby v projektu služby WCF, načte konfiguraci projektu a vytvoří instanci hostitele pro každou službu, kterou zjistí. Nástroj je integrován do sady Visual Studio pomocí šablony služby WCF a je vyvolána při spuštění ladění projektu.  
  
 Pomocí hostitele služby WCF můžete hostovat služby WCF (v projektu knihovny WCF service) bez psaní kódu navíc nebo potvrzení pouze určitého hostitele během vývoje.  
  
> [!NOTE]
>  Hostitel služby WCF nepodporuje částečném vztahu důvěryhodnosti. Pokud chcete použít službu WCF v částečném vztahu důvěryhodnosti, nepoužívejte šablony projektu Knihovna služby WCF v sadě Visual Studio k vytvoření vaší služby. Místo toho vytvořte nový web v sadě Visual Studio výběrem šablony WCF Web Service, které můžete hostovat službu v webového serveru, na kterém je WCF částečném vztahu důvěryhodnosti podporována.  
  
## <a name="project-types-hosted-by-wcf-service-host"></a>Typy projektů, které jsou hostovány hostitel služby WCF  
 Hostitel služby WCF můžete hostovat typ s projektu knihovny služby WCF: Knihovna služby WCF, knihovna služby sekvenčního pracovního postupu, knihovna služby pracovního postupu stavového stroje a knihovna služby syndikace. Hostitel služby WCF mohli hostovat i tyto služby, které mohou být přidány do projektu knihovny služby pomocí **přidat položku** funkce. To zahrnuje služby WCF, WF stavu počítače služby sekvenční Služba pracovního postupu, XAML WF stavu počítače a sekvenční Služba pracovního postupu XAML.  
  
 Nezapomeňte přitom, ale, že nástroj nebude vám pomohou při konfiguraci hostitele. Pro tuto úlohu musíte ručně upravit soubor App.config. Nástroj také nelze ověřit uživatelský konfigurační soubory.  
  
> [!CAUTION]
>  Hostitel služby WCF pro hostování služeb byste neměli používat v produkčním prostředí, protože nebyl analyzován pro tento účel.  Hostitel služby WCF nepodporuje spolehlivost, zabezpečení a možnosti správy požadavky těchto prostředí. Místo toho pomocí služby IIS, protože poskytuje spolehlivost a monitorovací funkce a je preferovaným řešením pro hostování služby. Jakmile je dokončen vývoj služeb, by měl migrovat služby od hostitele služby WCF na službu IIS.  
  
## <a name="scenarios-for-using-wcf-service-host-inside-visual-studio"></a>Scénáře použití hostitel služby WCF v sadě Visual Studio  
 V následující tabulce jsou uvedeny všechny parametry v **argumenty příkazového řádku** dialogové okno, které najdete tak, že kliknete pravým tlačítkem projekt v **Průzkumníka řešení** v sadě Visual Studio, že vyberete **Vlastnosti**, vyberete **ladění** kartu a kliknutím na **spustit projekt**. Tyto parametry jsou užitečné při konfiguraci hostitele služeb WCF.  
  
|Parametr|Význam|  
|---------------|-------------|  
|`/client`|Volitelný parametr, který určuje cestu ke spuštění po jsou hostovány službami spustitelného souboru. Tím se spustí testovací klient WCF po hostování.|  
|`/clientArg`|Zadejte řetězec jako argument, který je předán do vlastní klientské aplikace.|  
|`/?`|Zobrazí text nápovědy.|  
  
#### <a name="using-wcf-test-client"></a>Použití testovacího klienta WCF  
 Po vytvoření nového projektu služby WCF a stisknutím klávesy F5 spusťte ladicí program, hostitel služby WCF spustí hostování všechny služby, které najde ve vašem projektu. Testovací klient WCF automaticky otevře a zobrazí seznam koncových bodů služby, které jsou definovány v konfiguračním souboru. V hlavním okně můžete otestovat parametry a vyvolání služby.  
  
 Pokud chcete mít jistotu, že se používá testovací klient WCF, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** v sadě Visual Studio, vyberte **vlastnosti**a pak **ladění** kartu. Klikněte na tlačítko **spustit projekt** a ujistěte se, že se zobrazí následující v **argumenty příkazového řádku** dialogové okno.  
  
 `/client:WcfTestClient.exe`  
  
#### <a name="using-a-custom-client"></a>Pomocí vlastního klienta  
 Pokud chcete použít vlastní klienta, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** v sadě Visual Studio, vyberte **vlastnosti**a pak vyberte **ladění** kartu. Klikněte na tlačítko **spustit projekt** a upravit `/client` parametr **argumenty příkazového řádku** dialogové okno tak, aby odkazoval do vlastního klienta, jak je uvedeno v následujícím příkladu.  
  
 `/client:"path/CustomClient.exe"`  
  
 Po stisknutí klávesy F5 spusťte službu znovu, hostitel služby WCF se automaticky spustí vlastního klienta při spuštění ladicího programu.  
  
 Můžete také použít `/clientArg:` parametr zadat řetězec jako argument, který je předán do vlastní klientské aplikace, jak je uvedeno v následujícím příkladu.  
  
 `/client:"path/CustomClient.exe" /clientArg:"arguments that are passed to Client"`  
  
 Například pokud používáte šablonu Knihovna syndikační služby, můžete použít následující argumenty příkazového řádku  
  
 `/client:iexplore.exe /clientArgs:http://localhost:8731/Design_Time_Addresses/Feed1/`  
  
#### <a name="specifying-no-client"></a>Určení žádní klienti  
 Chcete-li určit, že žádní klienti nebudou použity po hostování služby WCF, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** v sadě Visual Studio, vyberte **vlastnosti**a pak vyberte **ladění** kartu. Klikněte na tlačítko **spustit projekt** a nechat **argumenty příkazového řádku** dialogové okno prázdné.  
  
#### <a name="using-a-custom-host"></a>Pomocí vlastního hostitele  
 Pokud chcete použít vlastního hostitele, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** v sadě Visual Studio, vyberte **vlastnosti**a pak vyberte **ladění** kartu. Klikněte na tlačítko **spustit externí Program** a zadejte úplnou cestu do vlastního hostitele. Můžete také použít **argumenty příkazového řádku** dialogové okno zadat argumenty předávané do hostitele.  
  
## <a name="wcf-service-host-user-interface"></a>WCF Service Host User Interface  
 Při počáteční vyvolání hostitel služby WCF (stisknutím klávesy F5 v sadě Visual Studio), **hostitel služby WCF** automaticky otevře okno. Při spuštění hostitele služby WCF, se zobrazí v oznamovací oblasti ikonu programu. Poklepejte na ikonu Otevřít **hostitel služby WCF** okna  
  
 Když dojde k chybám při hostování služeb, otevře se dialogové okno hostitele služeb WCF zobrazíte příslušné informace.  
  
 **Hostitel služby WCF** hlavní okno obsahuje dvě nabídky:  
  
-   **Soubor**: Obsahuje **Zavřít** a **ukončovací** příkazy. Po kliknutí na **Zavřít**, **hostitel služby WCF** zavře dialogové okno, ale nadále možné hostovat služby. Po kliknutí na **ukončovací**, je také vypnout hostitele služeb WCF. Tím se zastaví také všechny hostované služby.  
  
-   **Nápověda**: Obsahuje **o** příkaz, který obsahuje informace o verzi. Obsahuje taky **pomáhají** příkaz, který můžete otevřít soubor nápovědy.  
  
 Hlavní **hostitel služby WCF** okno obsahuje dvě oblasti:  
  
-   V první oblasti je **služby**. Obsahuje seznam, který zobrazuje základní informace o všech službách. Tyto informace zahrnují:  
  
    -   **Služba**: Zobrazí seznam všech služeb.  
  
    -   **Stav**: Zobrazí stav služby. Platné hodnoty jsou "Spuštěno", "Stopped" a "Chyba".  
  
    -   **Adresa metadat**: Zobrazí adresu metadat služby.  
  
-   Druhá oblast je **Další informace o**. Zobrazí se při výběru řádku konkrétní služby v podrobné vysvětlení stav služby **služby** oblasti. Pokud je ve stavu chyby, můžete zobrazit celé chybové zprávy na obrazovce.  
  
## <a name="stopping-wcf-service-host"></a>Stopping WCF Service Host  
 Hostitel služby WCF můžete vypnout následující čtyři způsoby:  
  
-   Zastavte relaci ladění v sadě Visual Studio.  
  
-   Vyberte **ukončovací** z **souboru** v nabídce **hostitel služby WCF** okna.  
  
-   Vyberte **ukončovací** z místní nabídky hostitel služby WCF na hlavním panelu ikonu v oznamovací oblasti systému.  
  
-   Testovací klient WCF ukončete, pokud se používá.  
  
## <a name="using-service-host-without-administrator-privilege"></a>Pomocí hostitele služby bez oprávnění správce  
 Pokud chcete povolit uživatelům bez oprávnění správce k vývoji služeb WCF, je vytvořen seznamu ACL portu (seznam řízení přístupu) pro obor názvů "http://+:8731/Design_Time_Addresses" během instalace sady Visual Studio. Seznam ACL je nastavena na (UI), což zahrnuje všechny interaktivní uživatelé přihlášení k počítači. Správci mohou přidat nebo odebrat uživatele z tohoto seznamu ACL nebo otevřít další porty. Tento seznam ACL umožňuje uživatelům používat automaticky hostitel služby WCF (wcfSvcHost.exe) bez nutnosti přidělení oprávnění správce.  
  
 Můžete upravit přístupu pomocí nástroje netsh.exe v [!INCLUDE[wv](../../../includes/wv-md.md)] pod účtem se zvýšenými oprávněními správce. Následuje příklad použití netsh.exe.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Další informace o netsh.exe, najdete v části "[použití pomocí nástroje Netsh.exe a přepínače příkazového řádku](https://go.microsoft.com/fwlink/?LinkId=97877)".  
  
## <a name="see-also"></a>Viz také:
- [Testovací klient WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
