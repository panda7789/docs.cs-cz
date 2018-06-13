---
title: 'Postupy: Hostování služby pracovního procesu pomocí Windows Server App Fabric'
ms.date: 03/30/2017
ms.assetid: 83b62cce-5fc2-4c6d-b27c-5742ba3bac73
ms.openlocfilehash: a1e2312beed61b340e034a48c36f739e799b1bf8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495837"
---
# <a name="how-to-host-a-workflow-service-with-windows-server-app-fabric"></a>Postupy: Hostování služby pracovního procesu pomocí Windows Server App Fabric
Hostování služeb pracovních postupů v App Fabric je podobná hostování v rámci služby IIS / byla. Jediným rozdílem je, nástroje, které poskytuje App Fabric pro nasazení, monitorování a správu služeb pracovních postupů. Toto téma používá služby pracovního postupu, které jsou vytvořené v [vytvoření dlouhodobé služby pracovního postupu](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md). Toto téma vás procesem vytvoření služby pracovních postupů. Toto téma vysvětluje, jak hostitele služby pracovního postupu pomocí App Fabric. Další informace o systému Windows Server App Fabric najdete v tématu [dokumentaci systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=193037&clcid=0x409). Před dokončením následujících kroků zkontrolujte, zda že máte nainstalovaný Windows Server App Fabric.  Pokud chcete provést tuto, otevřete si Internetová informační služba (inetmgr.exe), klikněte na název serveru v **připojení** zobrazení, klikněte na tlačítko weby a klikněte na **Default Web Site**. Na pravé straně obrazovky byste měli vidět části s názvem **App Fabric**. Pokud nevidíte v této části (je nahoře v pravém podokně) nemáte App Fabric nainstalována. Další informace o instalaci systému Windows Server App Fabric najdete v části [instalace systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=193136).  
  
### <a name="creating-a-simple-workflow-service"></a>Vytvoření jednoduchého pracovního postupu služby  
  
1.  Otevřete [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] a načtení OrderProcessing řešení, kterou jste vytvořili v [vytvoření dlouhodobé služby pracovního postupu](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md) tématu.  
  
2.  Klikněte pravým tlačítkem **OrderService** projektu a vyberte **vlastnosti** a vyberte **webové** kartě.  
  
3.  V **spustit akci** část na stránku vlastností vyberte **konkrétní stránky** a do textového pole zadejte Service1.xamlx.  
  
4.  V **servery** část na stránku vlastností vyberte **použití místního webového serveru IIS** a zadejte následující adresu URL: `http://localhost/OrderService`.  
  
5.  Klikněte **vytvořit virtuální adresář** tlačítko. To se vytvořit nový virtuální adresář a nastavení projektu při sestavení projektu zkopírovat potřebné soubory do virtuálního adresáře.  Případně může ručně zkopírujete .xamlx, soubor web.config a všechny potřebné knihovny DLL do virtuálního adresáře.  
  
### <a name="configuring-a-workflow-service-hosted-in-windows-server-app-fabric"></a>Konfigurace pracovního postupu služby hostované v systému Windows Server App Fabric  
  
1.  Otevřete Správce Internetové informační služby (inetmgr.exe).  
  
2.  Přejděte do virtuálního adresáře OrderService v **připojení** podokně.  
  
3.  Klikněte pravým tlačítkem na OrderService a vyberte **spravovat WCF a WF služby**, **konfigurace...** . **Konfigurace WCF a WF pro aplikaci** se zobrazí dialogové okno.  
  
4.  Vyberte **Obecné** kartě chcete zobrazit obecné informace o aplikaci, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Karta Obecné, dialogové okno Konfigurace prostředků infrastruktury aplikace](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-general.gif "AppFabricConfiguration – obecné")  
  
5.  Vyberte **monitorování** kartě. Ukazuje to různá nastavení monitorování, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Aplikace monitorování konfigurace infrastruktury karta](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-monitoring.gif "AppFabricConfiguration monitorování")  
  
     Další informace o konfiguraci služby pracovního postupu v tématu monitorování v nástroji App Fabric [konfiguraci monitorování pomocí App Fabric](http://go.microsoft.com/fwlink/?LinkId=193153).  
  
6.  Vyberte **pracovního postupu trvalost** kartě. To umožňuje konfiguraci aplikace na použití App Fabric výchozí trvalost poskytovatele, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Konfigurace infrastruktury aplikace &#45; trvalost](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-persistence.gif "AppFabricConfiguration trvalost")  
  
     Další informace o konfigurování trvalosti pracovního postupu v systému Windows Server App Fabric najdete v části [konfigurace trvalosti pracovního postupu v App Fabric](http://go.microsoft.com/fwlink/?LinkId=193148).  
  
7.  Vyberte **správu hostitele pracovního postupu** kartě. Můžete určit, když instance služby nečinnosti pracovního postupu by měla být uvolněna a jako trvalý, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Správa hostitele pracovního postupu konfigurace App Fabric](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-management.gif "AppFabricConfiguration-Management")  
  
     Další informace o konfiguraci správy hostitele pracovního postupu v tématu [konfigurace správy hostitele pracovního postupu v App Fabric](http://go.microsoft.com/fwlink/?LinkId=193151).  
  
8.  Vyberte **automatického spuštění** kartě. To umožňuje určit nastavení automatického spouštění služby pracovních postupů v aplikaci, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Aplikace Fabric automaticky&#45;spustit konfigurování](../../../../docs/framework/wcf/feature-details/media/appfabricconfigurationautostart.gif "AppFabricConfigurationAutostart")  
  
     Další informace o konfiguraci automatického spouštění naleznete v části [konfigurace automatického – spuštění pomocí App Fabric](http://go.microsoft.com/fwlink/?LinkId=193150).  
  
9. Vyberte **omezování** kartě. To umožňuje konfigurovat nastavení omezení pro službu pracovní postup, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Omezení configuration App Fabric](../../../../docs/framework/wcf/feature-details/media/appfabricconfigurationthrottling.gif "AppFabricConfigurationThrottling")  
  
     Další informace o konfiguraci omezování najdete v části [konfigurace omezování pomocí App Fabric](http://go.microsoft.com/fwlink/?LinkId=193149).  
  
10. Vyberte **zabezpečení** kartě. To umožňuje konfigurovat nastavení zabezpečení pro aplikace, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Konfigurace zabezpečení aplikace infrastruktury](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-security.gif "AppFabricConfiguration zabezpečení")  
  
     Další informace o konfiguraci zabezpečení pomocí systému Windows Server App Fabric najdete v části [konfigurace zabezpečení s App Fabric](http://go.microsoft.com/fwlink/?LinkId=193152).  
  
### <a name="using-windows-server-app-fabric"></a>Pomocí Windows Server App Fabric  
  
1.  Sestavte řešení zkopírovat potřebné soubory do virtuálního adresáře.  
  
2.  Klikněte pravým tlačítkem na projekt OrderClient a vyberte **ladění**, **spustit novou instanci** spustit klientskou aplikaci.  
  
3.  Klient spustí a Visual Studio se zobrazí **připojit upozornění zabezpečení** dialogové okno, klikněte na tlačítko **nemáte připojení** tlačítko. Tato hodnota informuje Visual Studio není připojit k procesu služby IIS pro ladění.  
  
4.  Klientská aplikace bude okamžitě volání služby pracovního postupu a potom počkejte, než. Služby pracovních postupů přejde nečinnosti a nastavit jako trvalý. Můžete to ověřit spuštěním Internetová informační služba (inetmgr.exe), nejde přejít ke OrderService v podokně připojení a ho vyberete. Potom klikněte na ikonu řídicí panel infrastruktury aplikace v pravém podokně. V rámci instance pracovního postupu jako trvalý, uvidíte, že existuje jedna instance služby pracovního postupu trvalou jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Řídicí panel infrastruktury aplikace](../../../../docs/framework/wcf/feature-details/media/appfabricdashboard.gif "AppFabricDashboard")  
  
     **WF Instance historie** uvádí informace týkající se služby pracovního postupu, například počet aktivací služby pracovního postupu, počet dokončených instance služby pracovního postupu a počet instancí pracovního postupu s chybami. Pod aktivní a nečinnosti instance, které se zobrazí odkaz kliknutím na odkaz zobrazíte další informace o instancích nečinnosti pracovní postup, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Trvalé podrobnosti Instance pracovního postupu](../../../../docs/framework/wcf/feature-details/media/persisteddetail.gif "PersistedDetail")  
  
     Další informace o systému Windows Server App Fabric funkcí a jejich použití najdete v části [hostování funkce systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=193143&clcid=0x409)  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření dlouhodobé služby pracovního postupu](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)  
 [Hostování funkcí systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=193143)  
 [Instalace systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=193136)  
 [Dokumentaci k systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=193037&clcid=0x409)
