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
ms.openlocfilehash: a98528a4bae1a22352096958cfec2350b21ddf8e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103412"
---
# <a name="introduction-to-windows-service-applications"></a>Představení aplikací spouštěných jako služby systému Windows
Služby Microsoft Windows, dřív označované jako služby NT, umožňují vytvářet dlouhodobé spustitelné aplikace spouštěné ve vlastních relacích Windows. Tyto služby mohou být automaticky spuštěny při spuštění počítače, mohou být pozastaveny a restartovány a nezobrazují žádné uživatelské rozhraní. Tyto funkce jsou služby ideální pro použití na serveru nebo kdykoliv potřebujete dlouhodobé funkčnosti, která nebude v konfliktu s jinými uživateli, kteří pracují na stejném počítači. Služby můžete také spustit v kontextu zabezpečení konkrétního uživatelského účtu, který se liší od přihlášeného uživatele nebo výchozího účtu počítače. Další informace o službách a relacích Windows najdete v dokumentaci Windows SDK.  
  
 Můžete snadno vytvářet služby tak, že vytvoříte aplikaci, která je nainstalována jako služba. Předpokládejme například, že chcete sledovat data čítače výkonu a reagovat na prahové hodnoty. Můžete psát aplikace služby Windows, které naslouchají datům čítačů výkonu, nasaďte aplikaci a začít vybírat a analyzovat data.  
  
 Vytvořte službu jako projekt aplikace Microsoft Visual Studio, definujte kód v, který určuje, jaké příkazy lze odesílat do služby a jaké akce je třeba provést při přijetí těchto příkazů. Příkazy, odeslané do služby zahrnují spuštění, pozastavení, pokračování a ukončení služby; Můžete také spustit vlastní příkazy.  
  
 Po vytvoření a sestavení aplikace, můžete ho nainstalovat spuštěním nástroje příkazového řádku InstallUtil.exe a předáním cesty do spustitelného souboru služby. Pak můžete použít **správce řízení služeb** pro spuštění, zastavení, pozastavení, pokračování a konfigurace služby. Můžete také provést mnohé z těchto úloh v **služby** uzel v **Průzkumníka serveru** nebo s použitím <xref:System.ServiceProcess.ServiceController> třídy.  
  
## <a name="service-applications-vs-other-visual-studio-applications"></a>Aplikace služeb vs. Jiné aplikace Visual Studio  
 Aplikace služeb fungují jinak než mnoho jiných typů projektů v několika ohledech:  
  
-   Kompilovaný spustitelný soubor, který vytvoří projekt aplikace služby musí nainstalovat na serveru, než projekt může fungovat srozumitelným způsobem. Nelze ladit nebo spustit aplikaci služby stisknutím klávesy F5 nebo F11; nelze spustit okamžitě službu nebo přejít do jejího kódu. Místo toho musíte nainstalovat a spusťte svoji službu a potom připojit ladicí program k procesu služby. Další informace najdete v tématu [jak: Ladění aplikace služby Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md).  
  
-   Na rozdíl od některých typů projektů je třeba vytvořit instalační komponenty pro aplikace služby. Součásti instalace nainstalujte a zaregistrují službu na serveru a vytvořte záznam pro vaši službu s Windows **správce řízení služeb**. Další informace najdete v tématu [jak: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
-   `Main` Metoda pro aplikaci služby musí vydat příkaz spustit pro služby, váš projekt obsahuje. `Run` Metoda načte služby do **správce řízení služeb** na příslušném serveru. Pokud používáte **služby Windows** šablony projektu, tato metoda je zapsána automaticky. Všimněte si, že načtení služby není totéž jako spuštění služby. Viz "Doba platnosti služby" níže pro další informace.  
  
-   Aplikace služby Windows běží v jiné stanici oken stanici než interaktivní stanice přihlášeného uživatele. Objekt window station je zabezpečený objekt, který obsahuje schránku, sadu globálních atomů a skupinu objektů plochy. Protože stanice služby Windows není interaktivní stanice, dialogová okna vyvolaná z v rámci Windows nebudou zobrazena aplikace služby a může způsobit, že program přestane reagovat. Podobně chybové zprávy by měl být zaznamenají do protokolu událostí Windows namísto vyvolání v uživatelském rozhraní.  
  
     Třídy služby Windows podporované rozhraním .NET Framework nepodporují interakci s interaktivními stanicemi, to znamená, přihlášeného uživatele. Rozhraní .NET Framework také nezahrnuje třídy, které představují stanice a plochy. Pokud vaše služba Windows musí spolupracovat s jinými stanicemi, je potřeba přístup k nespravované rozhraní API Windows. Další informace najdete v dokumentaci Windows SDK.  
  
     Interakce Windows service s uživatelem nebo jinými stanicemi musí být pečlivě navržena pro zahrnutí těchto scénářů, protože neexistuje žádný přihlášený uživatel nebo uživatel s neočekávanou množinou objektů plochy. V některých případech může být vhodnější vytvořit aplikace Windows, na kterém běží pod kontrolou uživatele.  
  
-   Aplikace služby Windows běží v jejich vlastním kontextu zabezpečení a jsou spuštěny před přihlášením uživatele do počítače Windows, na kterém je nainstalováno. Měli byste pečlivě naplánovat který uživatelský účet použít ke spuštění služby; služby spuštěné pod účtem systému má více oprávnění a pověření než uživatelský účet.  
  
## <a name="service-lifetime"></a>Doba platnosti služby  
 Služby prochází několika interními stavy v průběhu své životnosti. Nejprve je služba nainstalována do systému, na kterém se spustí. Tento postup spustí instalační programy pro projekt služby a načte službu do **správce řízení služeb** pro daný počítač. **Správce řízení služeb** je ústřední nástroj poskytovaný v systémem Windows ke správě služeb.  
  
 Po načtení služby musí být spuštěna. Spuštění služby umožňuje začít fungovat. Můžete spustit z **správce řízení služeb**, z **Průzkumníka serveru**, nebo z kódu voláním <xref:System.ServiceProcess.ServiceController.Start%2A> metody. <xref:System.ServiceProcess.ServiceController.Start%2A> Metoda předává do aplikace zpracování <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda a zpracuje veškerý kód, který jste definovali.  
  
 Spuštěná služba může existovat v tomto stavu, po neomezenou dobu, dokud se buď zastavena nebo pozastavena nebo vypnutí počítače. Služba může existovat v jednom ze tří základních stavů: <xref:System.ServiceProcess.ServiceControllerStatus.Running>, <xref:System.ServiceProcess.ServiceControllerStatus.Paused>, nebo <xref:System.ServiceProcess.ServiceControllerStatus.Stopped>. Služba může také nahlásit Stav čekajícího příkazu: <xref:System.ServiceProcess.ServiceControllerStatus.ContinuePending>, <xref:System.ServiceProcess.ServiceControllerStatus.PausePending>, <xref:System.ServiceProcess.ServiceControllerStatus.StartPending>, nebo <xref:System.ServiceProcess.ServiceControllerStatus.StopPending>. Tyto stavy ukazují, že příkaz byl vystaven, například příkaz pozastavit spuštěnou službu, ale nebyl dosud proveden. Můžete zadávat dotazy <xref:System.ServiceProcess.ServiceController.Status%2A> k určení stavu, ve kterém je služba, nebo použít <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A> dochází k provedení akce při některém z těchto stavů.  
  
 Můžete pozastavit, zastavit nebo obnovit službu ze **správce řízení služeb**, z **Průzkumníka serveru**, nebo pomocí volání metody v kódu. Všechny tyto akce mohou volat přidružené procedury ve službě (<xref:System.ServiceProcess.ServiceBase.OnStop%2A>, <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, nebo <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>), v níž je možné definovat další zpracování, které mají být provedeny, když služba změní stav.  
  
## <a name="types-of-services"></a>Typy služeb  
 Existují dva typy služeb, které můžete vytvořit v sadě Visual Studio pomocí rozhraní .NET Framework. Služby, které jsou jedinou službou v procesu, mají přiřazen typ <xref:System.ServiceProcess.ServiceType.Win32OwnProcess>. Služby, které sdílejí procesu s jinou službou, mají přiřazen typ <xref:System.ServiceProcess.ServiceType.Win32ShareProcess>. Typ služby můžete načíst pomocí dotazu <xref:System.ServiceProcess.ServiceController.ServiceType%2A> vlastnost.  
  
 Někdy může vidět jiné typy služeb, když odešlete dotaz na existující služby, které nebyly vytvořené v sadě Visual Studio. Další informace naleznete v tématu <xref:System.ServiceProcess.ServiceType>.  
  
## <a name="services-and-the-servicecontroller-component"></a>Služby a součást ServiceController  
 <xref:System.ServiceProcess.ServiceController> Komponenta je použité pro připojení k nainstalované služby a manipulaci s jejím stavem; using <xref:System.ServiceProcess.ServiceController> komponentu, můžete spustit a zastavit službu, pozastavit a pokračovat v jeho fungování a vlastní příkazy odesílat službě. Ale není potřeba použít <xref:System.ServiceProcess.ServiceController> komponenty při vytváření aplikace služby. Ve skutečnosti ve většině případů vaše <xref:System.ServiceProcess.ServiceController> komponenty by měly existovat v samostatné aplikaci mimo aplikaci služby Windows, který definuje vaši službu.  
  
 Další informace naleznete v tématu <xref:System.ServiceProcess.ServiceController>.  
  
## <a name="requirements"></a>Požadavky  
  
-   Služby musí být vytvořeny v **Windows Service** projektu aplikace nebo jiný projekt podporující rozhraní .NET Framework, který vytvoří soubor s příponou .exe při sestavení a dědí z <xref:System.ServiceProcess.ServiceBase> třídy.  
  
-   Projekty obsahující služby Windows musí mít instalační komponenty pro projekt a jeho služeb. Můžete to snadno provést z **vlastnosti** okna. Další informace najdete v tématu [jak: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
## <a name="see-also"></a>Viz také:

- [Aplikace služby systému Windows](../../../docs/framework/windows-services/index.md)
- [Architektura programování aplikace služby](../../../docs/framework/windows-services/service-application-programming-architecture.md)
- [Postupy: Vytváření služeb systému Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [Postupy: Instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)
- [Postupy: Spuštění služby](../../../docs/framework/windows-services/how-to-start-services.md)
- [Postupy: Ladění aplikací spouštěných jako služby systému Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)
- [Návod: Vytvoření aplikace služby Windows v Návrháři součástí](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
- [Postupy: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
