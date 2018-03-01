---
title: "Představení aplikací spouštěných jako služby systému Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 613107a13820ad71b854dcba93f21c41f2a5fa5f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="introduction-to-windows-service-applications"></a>Představení aplikací spouštěných jako služby systému Windows
Služby Microsoft Windows, dříve označovaná jako služba NT umožňují vytvářet dlouho běžící spustitelný soubor aplikace, které běží ve vlastní relací v systému Windows. Tyto služby můžete být automaticky spustí při spuštění počítače, můžete pozastavit a restartování a nezobrazuje žádné uživatelské rozhraní. Tyto funkce usnadnění služby ideální pro použití na serveru nebo kdykoli budete potřebovat dlouhodobé funkce, které nebudou v konfliktu s jinými uživateli, kteří pracují na stejném počítači. Služby můžete také spustit v kontextu zabezpečení konkrétní uživatelský účet, který se liší od přihlášeného uživatele nebo výchozího účtu. Další informace o službách a relace systému Windows naleznete v dokumentaci k Windows SDK.  
  
 Služby můžete snadno vytvořit tak, že vytvoříte aplikaci, která je nainstalován jako služba. Předpokládejme například, že chcete monitorovat data čítače výkonu a reagovat na prahové hodnoty. Můžete psát aplikace služby systému Windows, která naslouchá na data čítače výkonu, nasaďte aplikaci a zahájit shromažďování a analýza dat.  
  
 Vytvoření služby jako projekt sady Microsoft Visual Studio, definování kód v něm, který určuje, jaké příkazy lze odesílat a jaké akce by měla být provedena při přijetí těchto příkazů. Příkazy, které lze odeslat buď do služby zahrnují spuštění, pozastavení, obnovení a ukončení služby; Můžete také provést vlastní příkazy.  
  
 Po vytvoření a sestavení aplikace, můžete ho nainstalovat spuštěním nástroje příkazového řádku InstallUtil.exe a předání cesta ke spustitelnému souboru služby. Pak můžete použít **správci řízení služeb** pro spuštění, zastavení, pozastavení, obnovení a konfiguraci služby. Mohou také provádět mnoho z těchto úloh v **služby** uzlu v **Průzkumníka serveru** nebo pomocí <xref:System.ServiceProcess.ServiceController> – třída.  
  
## <a name="service-applications-vs-other-visual-studio-applications"></a>Aplikace služby vs. Ostatní aplikace Visual Studio  
 Funkce aplikace služby jinak než mnoho dalších typů projektu několika způsoby:  
  
-   Kompilované spustitelný soubor, který vytvoří projekt aplikace služby musí na serveru nainstalovány, před projektu, můžou fungovat smysluplný způsobem. Nelze ladění a spusťte aplikaci služby stisknutím klávesy F5 nebo F11; nelze spustit okamžitě služby nebo krok do jeho kódu. Místo toho musíte nainstalovat a spustit služby a pak připojit ladicí program k procesu služby. Další informace najdete v tématu [postupy: ladění aplikace služby systému Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md).  
  
-   Na rozdíl od některé typy projektů musíte vytvořit instalace součásti pro aplikace služby. Součásti instalace nainstalujte a zaregistrujte službu na serveru a vytvořit položku pro vaši službu pomocí ovládacího prvku Windows **správci řízení služeb**. Další informace najdete v tématu [postupy: Přidání instalačních programů pro vaše aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
-   `Main` Metoda pro aplikaci služby musíte vydat příkaz spustit pro služby projektu obsahuje. `Run` Metoda načte služby do **správci řízení služeb** na příslušném serveru. Pokud použijete **služby systému Windows** šablony projektu, tato metoda je napsán pro můžete automaticky. Všimněte si, že načítání služby není totéž jako službu spustit. Najdete v části "Service doba trvání" následující další informace.  
  
-   Aplikace služby systému Windows spustit v jiné časové období stanice než interaktivní stanice přihlášeného uživatele. Okno stanice je objekt zabezpečení, který obsahuje schránky, sadu globální atomů a skupiny klientů objektů. Protože stanice služby systému Windows není interaktivní stanice, dialogová okna vyvolané z v rámci Windows aplikace služby nedostupné a může způsobit, že váš program přestal reagovat. Podobně chybové zprávy by měl být zaznamenají do protokolu událostí systému Windows a nikoli vyvolána v uživatelském rozhraní.  
  
     Třídy služeb systému Windows nepodporuje rozhraní .NET Framework nepodporují interakci s interaktivní stanice, který je uživatel přihlášen. Rozhraní .NET Framework také nezahrnuje tříd, které představují stanic a stolní počítače. Pokud vaše služba systému Windows musí spolupracovat s ostatních stanic, potřebujete pro přístup k nespravovaného rozhraní API systému Windows. Další informace najdete v dokumentaci k Windows SDK.  
  
     Interakce služby s uživateli nebo jiné stanice musí být navrženy pečlivě zahrnout scénáře takové protože neexistuje žádný přihlášený uživatel nebo uživatel s neočekávanou sadu objektů plochy Windows. V některých případech může být vhodnější pro zápis aplikace systému Windows, který spouští pod kontrolou uživatele.  
  
-   Aplikace služby systému Windows spusťte v jejich vlastním kontextu zabezpečení a jsou spuštěny před se uživatel přihlásí do Windows počítače, na kterém jsou nainstalované. Měli pečlivě naplánovat jaké uživatelský účet, ke spouštění služby v rámci; služby spuštěné pod účtem system má další oprávnění a oprávnění než uživatelský účet.  
  
## <a name="service-lifetime"></a>Doba platnosti služby  
 Služba projde několik interní stavy v celé jeho životnosti. Nejprve je služba nainstalována systému, na kterém se spustí. Tento proces se spustí instalační služby pro projekt služby a načte službu do **správci řízení služeb** pro tento počítač. **Správci řízení služeb** je centrální nástroj obsažené v systému Windows ke správě služeb.  
  
 Po zavedení služby je nutné spustit. Spouštění služby umožňuje, aby začal fungovat. Můžete spustit služby z **správci řízení služeb**, z **Průzkumníka serveru**, nebo z kódu voláním <xref:System.ServiceProcess.ServiceController.Start%2A> metoda. <xref:System.ServiceProcess.ServiceController.Start%2A> Metoda předá zpracování aplikace <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda a zpracuje žádný kód, který jste definovali existuje.  
  
 Spuštěná služba může existovat v tomto stavu, bez omezení, dokud nebude buď zastavena nebo pozastavena, nebo dokud se počítač vypne. Služba může existovat v jednom ze tří stavů základní: <xref:System.ServiceProcess.ServiceControllerStatus.Running>, <xref:System.ServiceProcess.ServiceControllerStatus.Paused>, nebo <xref:System.ServiceProcess.ServiceControllerStatus.Stopped>. Službu můžete také sestavy stavu čekající příkazu: <xref:System.ServiceProcess.ServiceControllerStatus.ContinuePending>, <xref:System.ServiceProcess.ServiceControllerStatus.PausePending>, <xref:System.ServiceProcess.ServiceControllerStatus.StartPending>, nebo <xref:System.ServiceProcess.ServiceControllerStatus.StopPending>. Tyto stavy znamenat, že příkaz byl vydán, třeba příkaz pozastaví spuštěné služby, ale nebyla ještě provádějí. Můžete zadat dotaz <xref:System.ServiceProcess.ServiceController.Status%2A> k určení, co stav služby je v nebo pomocí <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A> proveďte akci, pokud některý z těchto stavů dojde k.  
  
 Můžete pozastavit, zastavit nebo obnovit služby z **správci řízení služeb**, z **Průzkumníka serveru**, nebo voláním metod v kódu. Každý z těchto akcí můžete volat s příslušným postupem v rámci služby (<xref:System.ServiceProcess.ServiceBase.OnStop%2A>, <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, nebo <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>), ve kterém můžete definovat další zpracování, které mají být provedeny, když se změní stav služby.  
  
## <a name="types-of-services"></a>Typy služeb  
 Existují dva typy služeb, které lze vytvořit v sadě Visual Studio pomocí rozhraní .NET Framework. Služby, které jsou pouze služby v procesu přiřazené typ <xref:System.ServiceProcess.ServiceType.Win32OwnProcess>. Služby, které proces sdílet s jinou službu přiřazené typ <xref:System.ServiceProcess.ServiceType.Win32ShareProcess>. Typ služby můžete načíst pomocí dotazu <xref:System.ServiceProcess.ServiceController.ServiceType%2A> vlastnost.  
  
 Jiné typy služeb může občas zobrazit, je-li dotaz stávající služby, které nebyly vytvořeny v sadě Visual Studio. Další informace naleznete v tématu <xref:System.ServiceProcess.ServiceType>.  
  
## <a name="services-and-the-servicecontroller-component"></a>Služby a součást ServiceController  
 <xref:System.ServiceProcess.ServiceController> Součást je použité pro připojení k instalované služby a pracovat s její stav; pomocí <xref:System.ServiceProcess.ServiceController> součásti, můžete spustit a zastavit službu, pozastavit a pokračovat v jeho fungování a odeslat vlastní příkazy ke službě. Však není potřeba použít <xref:System.ServiceProcess.ServiceController> součást při vytváření aplikace služby. Ve skutečnosti ve většině případů vaší <xref:System.ServiceProcess.ServiceController> komponenty by měly existovat v samostatných aplikací z aplikace služby systému Windows, která definuje služby.  
  
 Další informace naleznete v tématu <xref:System.ServiceProcess.ServiceController>.  
  
## <a name="requirements"></a>Požadavky  
  
-   Služby musí být vytvořen v **služba systému Windows** projekt aplikace nebo jiného projektu podporující rozhraní .NET Framework, který vytvoří soubor .exe při sestavení a dědí z <xref:System.ServiceProcess.ServiceBase> třídy.  
  
-   Projekty obsahující služby systému Windows musí být instalace součásti pro projekt a jeho služeb. To se dá snadno udělat z **vlastnosti** okno. Další informace najdete v tématu [postupy: Přidání instalačních programů pro vaše aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
## <a name="see-also"></a>Viz také  
 [Aplikace služby systému Windows](../../../docs/framework/windows-services/index.md)  
 [Architektura programování aplikace služby](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 [Postupy: Vytváření služeb systému Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Postupy: Instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [Postupy: Spuštění služeb](../../../docs/framework/windows-services/how-to-start-services.md)  
 [Postupy: Ladění aplikací služby systému Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Návod: Vytvoření aplikace služby systému Windows v návrháři součástí](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 [Postupy: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
