---
title: Představení aplikací spouštěných jako služby systému Windows
ms.date: 03/30/2017
f1_keywords:
- ServiceController
helpviewer_keywords:
- Windows Service applications, deploying
- OnStop method
- OnPause method
- services, about services
- Service class, Windows Service applications
- framework services, creating services
- ServiceController components, about Windows services
- Win32OwnProcess service type
- services, lifetime
- OnContinue method
- Windows Service applications, about Windows Service applications
- services, states
- service states
- WaitForStatus method
- Win32ShareProcess service type
- Windows Service applications, lifetime
ms.assetid: 1b1b5e67-3ff3-40c0-8154-322cfd6ef0ae
author: ghogen
ms.openlocfilehash: 8ff1adaa025dc11417c3dcfdaf42ea203828be57
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053525"
---
# <a name="introduction-to-windows-service-applications"></a>Představení aplikací spouštěných jako služby systému Windows
Služby Microsoft Windows, dříve označované jako služby NT, umožňují vytvářet dlouhotrvající spustitelné aplikace, které běží ve vlastních relacích systému Windows. Tyto služby mohou být automaticky spuštěny při spuštění počítače, lze pozastavit a restartovat a Nezobrazovat žádné uživatelské rozhraní. Tyto funkce umožňují služby, které jsou ideální pro použití na serveru, nebo kdykoli potřebujete dlouhodobě běžící funkce, které nebrání jiným uživatelům, kteří pracují na stejném počítači. Služby můžete také spustit v kontextu zabezpečení konkrétního uživatelského účtu, který se liší od přihlášeného uživatele nebo z výchozího účtu počítače. Další informace o službách a relacích systému Windows naleznete v dokumentaci k Windows SDK.  
  
 Služby můžete snadno vytvořit tak, že vytvoříte aplikaci, která je nainstalovaná jako služba. Předpokládejme například, že chcete monitorovat data čítače výkonu a reagovat na prahové hodnoty. Můžete napsat aplikaci služby systému Windows, která přijímá data čítače výkonu, nasadí aplikaci a začne shromažďovat a analyzovat data.  
  
 Vytvoříte službu jako projekt Microsoft Visual Studio, definujete kód v rámci něj, který určuje, jaké příkazy lze odeslat do služby a jaké akce by měly být provedeny při přijetí těchto příkazů. Mezi příkazy, které je možné odeslat do služby, patří spuštění, pozastavení, obnovení a zastavení služby. Můžete také provádět vlastní příkazy.  
  
 Po vytvoření a sestavení aplikace ji můžete nainstalovat spuštěním nástroje příkazového řádku InstallUtil. exe a předáním cesty ke spustitelnému souboru služby. Potom můžete pomocí **správce řízení služeb** spustit, zastavit, pozastavit, obnovit a nakonfigurovat službu. Mnohé z těchto stejných úloh můžete také provést v uzlu **služby** v **Průzkumník serveru** nebo pomocí <xref:System.ServiceProcess.ServiceController> třídy.  
  
## <a name="service-applications-vs-other-visual-studio-applications"></a>Aplikace služby vs. Ostatní aplikace sady Visual Studio  
 Aplikace služeb fungují jinak než mnoho dalších typů projektů v několika ohledech:  
  
- Kompilovaný spustitelný soubor, který vytvoří projekt aplikace služby, musí být nainstalován na serveru, aby mohl projekt fungovat smysluplným způsobem. Aplikaci služby nelze ladit nebo spustit stisknutím klávesy F5 nebo F11; službu nebo krok nelze okamžitě spustit do kódu. Místo toho musíte nainstalovat a spustit službu a potom připojit ladicí program k procesu služby. Další informace najdete v tématu [jak: Ladit aplikace](how-to-debug-windows-service-applications.md)služby systému Windows.  
  
- Na rozdíl od některých typů projektů je nutné vytvořit instalační součásti pro aplikace služeb. Součásti instalace nainstalujte a zaregistrujte službu na serveru a vytvořte záznam pro vaši službu pomocí **správce řízení služeb**systému Windows. Další informace najdete v tématu [jak: Přidejte instalační programy do aplikace](how-to-add-installers-to-your-service-application.md)služby.  
  
- `Main` Metoda aplikace služby musí vystavit příkaz run pro služby, které projekt obsahuje. Metoda načte služby do **správce řízení služeb** na příslušném serveru. `Run` Použijete-li šablonu projektu **služby systému Windows** , bude tato metoda vytvořena automaticky. Všimněte si, že načtení služby není stejné jako spuštění služby. Další informace najdete v části "doba platnosti služby" níže.  
  
- Aplikace služby systému Windows běží v jiné stanici okna než interaktivní stanice přihlášeného uživatele. Stanice okna je zabezpečený objekt, který obsahuje schránku, sadu globálních atomů a skupinu objektů plochy. Vzhledem k tomu, že stanice služby Windows není interaktivní stanicí, nezobrazí se dialogová okna vyvolaná v rámci aplikace služby systému Windows a může dojít k tomu, že program přestane reagovat. Podobně by se chybové zprávy měly protokolovat v protokolu událostí systému Windows, nikoli v uživatelském rozhraní.  
  
     Třídy služby systému Windows podporované .NET Framework nepodporují interakci s interaktivními stanicemi, tedy s přihlášeným uživatelem. .NET Framework ani nezahrnuje třídy, které reprezentují stanice a desktopy. Pokud vaše služba systému Windows musí spolupracovat s jinými stanicemi, budete potřebovat přístup k nespravovanému rozhraní API systému Windows. Další informace najdete v dokumentaci k Windows SDK.  
  
     Interakce služby systému Windows s uživatelem nebo jinými stanicemi musí být pečlivě navržena tak, aby zahrnovala scénáře, jako například není přihlášený uživatel nebo uživatel s neočekávanou sadou objektů plochy. V některých případech může být vhodnější napsat aplikaci pro Windows, která běží pod kontrolou uživatele.  
  
- Aplikace služby systému Windows běží ve vlastním kontextu zabezpečení a jsou spuštěny před přihlášením uživatele do počítače se systémem Windows, ve kterém jsou nainstalovány. Měli byste pečlivě naplánovat, na jaký uživatelský účet se má služba spustit; služba spuštěná v účtu System má více oprávnění a oprávnění než uživatelský účet.  
  
## <a name="service-lifetime"></a>Doba života služby  
 Služba prochází několika interními stavy během své životnosti. Nejdřív se služba nainstaluje do systému, na kterém se spustí. Tento proces spustí instalační programy pro projekt služby a načte službu do **správce řízení služeb** pro tento počítač. **Správce řízení služeb** je centrální nástroj poskytovaný systémem Windows ke správě služeb.  
  
 Po načtení služby je nutné ji spustit. Spuštění služby umožňuje její zprovoznění začít pracovat. Službu můžete spustit ze **správce řízení služeb**, z **Průzkumník serveru**nebo z kódu voláním <xref:System.ServiceProcess.ServiceController.Start%2A> metody. Metoda předá zpracování do <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody aplikace a zpracovává jakýkoli kód, který jste tam definovali. <xref:System.ServiceProcess.ServiceController.Start%2A>  
  
 Běžící služba může existovat v tomto stavu po dobu neurčitou, dokud nebude zastavena nebo pozastavena nebo dokud se počítač nevypne. Služba může existovat v jednom ze tří základních stavů: <xref:System.ServiceProcess.ServiceControllerStatus.Running>, <xref:System.ServiceProcess.ServiceControllerStatus.Paused>nebo <xref:System.ServiceProcess.ServiceControllerStatus.Stopped>. Služba může také ohlásit stav příkazu, který čeká na vyřízení <xref:System.ServiceProcess.ServiceControllerStatus.ContinuePending>: <xref:System.ServiceProcess.ServiceControllerStatus.PausePending>, <xref:System.ServiceProcess.ServiceControllerStatus.StartPending>, nebo <xref:System.ServiceProcess.ServiceControllerStatus.StopPending>. Tyto stavy označují, že byl vydán příkaz, například příkaz pro pozastavení spuštěné služby, ale ještě nebyl proveden. Můžete zadat dotaz <xref:System.ServiceProcess.ServiceController.Status%2A> na, abyste zjistili, jaký stav služby je služba, nebo můžete <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A> použít k provedení akce, když dojde k jakémukoli z těchto stavů.  
  
 Službu můžete pozastavit, zastavit nebo obnovit ze **správce řízení služeb**, z **Průzkumník serveru**nebo voláním metod v kódu. Každá z těchto akcí může volat přidruženou proceduru ve službě (<xref:System.ServiceProcess.ServiceBase.OnStop%2A>, <xref:System.ServiceProcess.ServiceBase.OnPause%2A>nebo <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>), ve které můžete definovat další zpracování, které má být provedeno při změně stavu služby.  
  
## <a name="types-of-services"></a>Typy služeb  
 Existují dva typy služeb, které můžete vytvořit v aplikaci Visual Studio pomocí .NET Framework. Služby, které jsou jedinou službou v procesu, jsou přiřazeny typu <xref:System.ServiceProcess.ServiceType.Win32OwnProcess>. Typ <xref:System.ServiceProcess.ServiceType.Win32ShareProcess>se přiřadí službám, které sdílejí proces s jinou službou. Můžete načíst typ služby dotazem na <xref:System.ServiceProcess.ServiceController.ServiceType%2A> vlastnost.  
  
 Pokud se dotazovat na existující služby, které nebyly vytvořeny v aplikaci Visual Studio, můžete občas zobrazit další typy služeb. Další informace najdete v tématu <xref:System.ServiceProcess.ServiceType>.  
  
## <a name="services-and-the-servicecontroller-component"></a>Služby a Komponenta ServiceController  
 Komponenta se používá pro připojení k instalované službě a manipulaci se svým stavem. <xref:System.ServiceProcess.ServiceController> pomocí komponenty můžete spustit a zastavit službu, pozastavit a pokračovat v jejím fungování a odesílat do služby vlastní příkazy. <xref:System.ServiceProcess.ServiceController> Při vytváření aplikace služby ale nemusíte používat <xref:System.ServiceProcess.ServiceController> komponentu. Ve většině případů by vaše <xref:System.ServiceProcess.ServiceController> komponenta měla existovat v samostatné aplikaci od aplikace služby systému Windows, která definuje vaši službu.  
  
 Další informace naleznete v tématu <xref:System.ServiceProcess.ServiceController>.  
  
## <a name="requirements"></a>Požadavky  
  
- Služby musí být vytvořeny v projektu aplikace **služby systému Windows** nebo jiném projektu s podporou .NET Framework, který vytvoří soubor. exe při sestavení a dědění z <xref:System.ServiceProcess.ServiceBase> třídy.  
  
- Projekty, které obsahují služby systému Windows, musí mít součásti instalace pro projekt a jeho služby. To lze snadno provést z okna **vlastnosti** . Další informace najdete v tématu [jak: Přidejte instalační programy do aplikace](how-to-add-installers-to-your-service-application.md)služby.  
  
## <a name="see-also"></a>Viz také:

- [Aplikace služby systému Windows](index.md)
- [Architektura programování aplikace služby](service-application-programming-architecture.md)
- [Postupy: Vytvořit služby systému Windows](how-to-create-windows-services.md)
- [Postupy: Instalace a odinstalace služeb](how-to-install-and-uninstall-services.md)
- [Postupy: Spustit služby](how-to-start-services.md)
- [Postupy: Ladění aplikací služby systému Windows](how-to-debug-windows-service-applications.md)
- [Návod: Vytvoření aplikace služby systému Windows v Návrháři součástí](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
- [Postupy: Přidání instalačních programů do aplikace služby](how-to-add-installers-to-your-service-application.md)
