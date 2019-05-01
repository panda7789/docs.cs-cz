---
title: 'Postupy: Hostování služby pracovního procesu pomocí Windows Server App Fabric'
ms.date: 03/30/2017
ms.assetid: 83b62cce-5fc2-4c6d-b27c-5742ba3bac73
ms.openlocfilehash: d1042aca7e4127c39e59bf0bf400974f0cecb1e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62039495"
---
# <a name="how-to-host-a-workflow-service-with-windows-server-app-fabric"></a>Postupy: Hostování služby pracovního procesu pomocí Windows Server App Fabric
Hostování služeb pracovních postupů v prostředcích infrastruktury aplikace je podobný hostování v rámci služby IIS nebo WAS. Jediným rozdílem je, nástroje, které poskytuje App Fabric pro nasazení, monitorování a správu služeb pracovních postupů. Toto téma používá služby pracovních postupů v vytvoří [vytvoření dlouhodobé služby pracovního postupu](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md). Toto téma vás provede procesem vytvoření služby pracovních postupů. Toto téma vysvětluje, jak hostování služby pracovního postupu pomocí App Fabric. Další informace o systému Windows Server App Fabric najdete v tématu [dokumentaci k systému Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=193037&clcid=0x409). Před provedením následujících kroků zkontrolujte, že máte nainstalovaný Windows Server App Fabric.  Provedete tuto otevřete Internetová informační služba (inetmgr.exe), klikněte na název serveru v **připojení** zobrazení, klikněte na tlačítko weby a klikněte na tlačítko **výchozí webový server**. V pravém okraji obrazovky byste měli vidět část s názvem **App Fabric**. Pokud se nezobrazí v této části (bude uvedená nahoře v pravém podokně) nemáte nainstalované App Fabric. Další informace o instalaci systému Windows Server App Fabric najdete v části [instalace systému Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=193136).  
  
### <a name="creating-a-simple-workflow-service"></a>Vytvoření služby jednoduchý pracovní postup  
  
1. Otevřít Visual Studio 2012 a načtení řešení OrderProcessing, kterou jste vytvořili v [vytvoření dlouhodobé služby pracovního postupu](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md) tématu.  
  
2. Klikněte pravým tlačítkem myši **OrderService** projektu a vyberte **vlastnosti** a vyberte **webové** kartu.  
  
3. V **spustit akci** části na stránce vlastností **konkrétní stránka** a do textového pole zadejte Service1.xamlx.  
  
4. V **servery** části na stránce vlastností **použití místní webový Server IIS** a zadejte následující adresu URL: `http://localhost/OrderService`.  
  
5. Klikněte na tlačítko **vytvořit virtuální adresář** tlačítko. Tím se vytvoří nový virtuální adresář a nastavení projektu při sestavení projektu zkopírovat potřebné soubory do virtuálního adresáře.  Další možností je může ručně zkopírovat .xamlx, soubor web.config a všechny potřebné knihovny DLL do virtuálního adresáře.  
  
### <a name="configuring-a-workflow-service-hosted-in-windows-server-app-fabric"></a>Konfigurace pracovního postupu služby hostované v systému Windows Server App Fabric  
  
1. Otevřete Správce Internetové informační služby (inetmgr.exe).  
  
2. Přejděte do virtuálního adresáře OrderService v **připojení** podokně.  
  
3. OrderService klikněte pravým tlačítkem a vyberte **spravovat WCF a WF služby**, **konfigurace...** . **Konfigurace WCF a WF pro aplikaci** se zobrazí dialogové okno.  
  
4. Vyberte **Obecné** karet zobrazit obecné informace o aplikaci, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Karta Obecné, dialogové okno Konfigurace prostředků infrastruktury aplikace](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-general.gif "AppFabricConfiguration – obecné")  
  
5. Vyberte **monitorování** kartu. To ukazuje různé nastavení monitorování, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Karta monitorování infrastruktury konfigurace aplikace](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-monitoring.gif "AppFabricConfiguration monitorování")  
  
     Další informace o konfiguraci služby pracovních postupů monitorování v prostředcích infrastruktury aplikace naleznete v tématu [konfigurace sledování pomocí App Fabric](https://go.microsoft.com/fwlink/?LinkId=193153).  
  
6. Vyberte **trvalost pracovního postupu** kartu. To umožňuje nakonfigurovat aplikace použijte poskytovatele trvalého chování výchozí App Fabric jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Konfigurace aplikace Fabric &#45; trvalost](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-persistence.gif "AppFabricConfiguration trvalosti")  
  
     Další informace o konfiguraci trvalosti pracovního postupu v systému Windows Server App Fabric najdete v části [konfigurace trvalost pracovního postupu v aplikaci Fabric](https://go.microsoft.com/fwlink/?LinkId=193148).  
  
7. Vyberte **správu hostitele pracovního postupu** kartu. To umožňuje zadat při instance nečinných pracovních postupů služby by mělo být odpojeno a zachována, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Správa hostitele pracovního postupu konfigurace App Fabric](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-management.gif "AppFabricConfiguration-Management")  
  
     Další informace o konfiguraci správy hostitele pracovního postupu v tématu [konfigurace správy hostitele pracovního postupu v aplikaci Fabric](https://go.microsoft.com/fwlink/?LinkId=193151).  
  
8. Vyberte **automatického spuštění** kartu. To umožňuje určit nastavení automatického spouštění služby pracovního postupu v aplikaci, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Snímek obrazovky s App Fabric automaticky&#45;spustit konfiguraci.](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-auto-start-configuration.gif)  
  
     Další informace o konfiguraci automatického spuštění najdete v části [konfiguraci automatického spuštění pomocí App Fabric](https://go.microsoft.com/fwlink/?LinkId=193150).  
  
9. Vyberte **omezování** kartu. To umožňuje nakonfigurovat nastavení omezení pro službu pracovního postupu, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Snímek obrazovky zobrazující konfigurace omezení App Fabric.](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-throttling-configuration.gif)  
  
     Další informace o konfiguraci omezování naleznete v tématu [konfigurace omezování pomocí App Fabric](https://go.microsoft.com/fwlink/?LinkId=193149).  
  
10. Vyberte **zabezpečení** kartu. To umožňuje konfigurovat nastavení zabezpečení pro aplikaci, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Konfigurace zabezpečení aplikace Fabric](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-security.gif "AppFabricConfiguration zabezpečení")  
  
     Další informace o konfiguraci zabezpečení pomocí systému Windows Server App Fabric najdete v části [konfigurace zabezpečení v aplikaci Fabric](https://go.microsoft.com/fwlink/?LinkId=193152).  
  
### <a name="using-windows-server-app-fabric"></a>Pomocí systému Windows Server App Fabric  
  
1. Sestavte řešení, zkopírujte soubory potřebné k virtuálnímu adresáři.  
  
2. Klikněte pravým tlačítkem na projekt OrderClient a vyberte **ladění**, **spustit novou instanci** spuštění klientské aplikace.  
  
3. Klient se spustí a zobrazí Visual Studio **připojit upozornění zabezpečení** dialogové okno, klikněte na tlačítko **Nepřipojovat** tlačítko. Znamená to Visual Studio se nelze připojit k procesu služby IIS pro ladění.  
  
4. Klientská aplikace bude okamžitě volání služby pracovního postupu a potom počkejte. Služba pracovního postupu přejde za nečinné a trvalé. Můžete to ověřit spuštěním Internetová informační služba (inetmgr.exe), přejdete na OrderService v podokně připojení a že ji vyberete. Klikněte na ikonu aplikace řídicí panel prostředků infrastruktury v pravém podokně. V rámci trvalé instance pracovního postupu uvidíte, že jeden trvalými instancemi pracovního postupu služby jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Snímek obrazovky zobrazující řídicí panel infrastruktury aplikace.](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-dashboard.gif)  
  
     **Historie Instance pracovního postupu** uvádí informace o službě pracovního postupu, jako je například počet aktivací služby pracovního postupu, počet dokončení instance služby pracovního postupu a počet instancí pracovních postupů s chybami. V rámci aktivní nebo neaktivní instance, které se zobrazí odkaz kliknutím na odkaz zobrazíte další informace o instance nečinných pracovních postupů, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Snímek obrazovky zobrazující podrobnosti o trvalé instanci pracovního postupu.](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/persisted-workflow-instance-detail.gif)  
  
     Další informace o systému Windows Server App Fabric funkcí a jejich použití naleznete v tématu [hostování funkce systému Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=193143&clcid=0x409)  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření dlouhodobé služby pracovního postupu](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)
- [Hostování funkcí systému Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=193143)
- [Instalace systému Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=193136)
- [Dokumentaci k systému Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=193037&clcid=0x409)
